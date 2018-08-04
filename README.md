# digital-mailer-service

The Digital Mailer Service is an API that can send e-mails programmatically to e-mail addresses. 
The API can send plain-text, HTML, and HTML templates. HTML templates are very useful as you can 
upload an HTML template to the service, and then specify that template and provide actual data in 
later API calls. The service also allows for adding attachments to e-mail.
 

Features
Send plain-text or HTML e-mail programmatically
Upload and send HTML templates
Add attachments to e-mail

Attached is a NodeJS code example of how to call this API with an attachment.
 
    Content-Type: JSON
    
    Here are the JSON keys you need:
    
·         to: ­ this is who you want to send the e-mail to. You can also specify the keys: cc and bcc. Send the values as a comma delimited string. You must have one either to, cc, or bcc.
    
    Example: “foo@bar.com,foo2@bar.com,foo3@bar.com”
    
·         from:­ this is who you want the email to appear from, has to have a valid e-mail address format.
    
    Example: “foo@bar.com” but you can also be more descriptive by putting the e-mail address in angle brackets: "Siva Das <sivasankardas@gmail.com>" (you may have to escape the angle brackets)
    
·         subject: ­ Subject of the email
    
    Example: “Test Subject”
    
·         body: ­ This is the message body.
    
    Example: ³This is a test message body.²
    
    Those are all the required fields for the API call. For attachments, you need to specify the key “attachments” as an object 
    and then have each of your attachments in that object. The file name for the file will be the key for the data. It is very 
    important to provide the right extension. For example, “att2.ext” will be the name of the file created by the corresponding 
    base64 data, and if you creating a pdf file, make sure to name the file with a .pdf extenstion.
    
    Example:
    
    "attachments": {
    	"[filename here without brackets]": “[put base64 data here without the brackets]”,
    	“att2.ext”: “[put base64 data here without the brackets]”
    }
    
 
 
Example Call:
 
{ 	 debugId: 4, 
	uri: 'http://localhost:8080/digital/mailer-service/email',
     method: 'POST',
     headers:
      { 'Content-Type': 'application/json',
        authorization: 'Bearer QXLHgTXsKCfT4Ji0c6YVHsuN5lmB',
        host: 'localhost',
        accept: 'application/json',
        'content-length': 97 
      },
     body: '{"from":"sivasankardas@gmail.com","to":"sivasankardas@ge.com","subject":"subject","body":"body"}' 
     } 
     }