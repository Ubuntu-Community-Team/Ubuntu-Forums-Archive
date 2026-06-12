---
title: "contact form issues with LAMP installed on Ubuntu 11.10"
date: 2011-12-24
forum: General Help
---

### Post by KrisDeniseRiley1 on 2011-12-24
So I am a networking student that is working with designing and building  web pages. I installed LAMP on a home PC so that I can have a webserver  at home. So I am somewhat new to server side things. So I am building a  website and found the great idea of doing a contact form instead of  using the "mailto" idea. So I found a site that had a good and easy way  to install a contact form with a contact_form.html & contact.php  files. So I put them in my /var/www/ folder along with all of my other  website material. When I put localhost into the URL and the site comes  up, I click on the email contact link and the contact_form.html page  comes up. I fill in the info and click on send, but it comes up with a Message Failed  error, which would mean that it's doing the 'else'statement in the php file. I am new to this somewhat and would like someone to look through  the code from both files. When I installed LAMP, I was under the  assumption that it was PHP compatable when I have a .php file in the  /var/www/ folder. Any info would be great!

Kris

```
[COLOR=#000000][COLOR=#0000BB]<?php

$field_name [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000BB]$_POST[/COLOR][COLOR=#007700][[/COLOR][COLOR=#DD0000]'cf_name'[/COLOR][COLOR=#007700]];

[/COLOR][COLOR=#0000BB]$field_email [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000BB]$_POST[/COLOR][COLOR=#007700][[/COLOR][COLOR=#DD0000]'cf_email'[/COLOR][COLOR=#007700]];

[/COLOR][COLOR=#0000BB]$field_message [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000BB]$_POST[/COLOR][COLOR=#007700][[/COLOR][COLOR=#DD0000]'cf_message'[/COLOR][COLOR=#007700]];



[/COLOR][COLOR=#0000BB]$mail_to [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#DD0000]'hornerkris@gmail.com'[/COLOR][COLOR=#007700];

[/COLOR][COLOR=#0000BB]$subject [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#DD0000]'Message from a site visitor '[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]$field_name[/COLOR][COLOR=#007700];



[/COLOR][COLOR=#0000BB]$body_message [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#DD0000]'From: '[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]$field_name[/COLOR][COLOR=#007700].[/COLOR][COLOR=#DD0000]"\n"[/COLOR][COLOR=#007700];

[/COLOR][COLOR=#0000BB]$body_message [/COLOR][COLOR=#007700].= [/COLOR][COLOR=#DD0000]'E-mail: '[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]$field_email[/COLOR][COLOR=#007700].[/COLOR][COLOR=#DD0000]"\n"[/COLOR][COLOR=#007700];

[/COLOR][COLOR=#0000BB]$body_message [/COLOR][COLOR=#007700].= [/COLOR][COLOR=#DD0000]'Message: '[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]$field_message[/COLOR][COLOR=#007700];



[/COLOR][COLOR=#0000BB]$headers [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#DD0000]'From: '[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]$cf_email[/COLOR][COLOR=#007700].[/COLOR][COLOR=#DD0000]"\r\n"[/COLOR][COLOR=#007700];

[/COLOR][COLOR=#0000BB]$headers [/COLOR][COLOR=#007700].= [/COLOR][COLOR=#DD0000]'Reply-To: '[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]$cf_email[/COLOR][COLOR=#007700].[/COLOR][COLOR=#DD0000]"\r\n"[/COLOR][COLOR=#007700];



[/COLOR][COLOR=#0000BB]$mail_status [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000BB]mail[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000BB]$mail_to[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000BB]$subject[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000BB]$body_message[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000BB]$headers[/COLOR][COLOR=#007700]);



if ([/COLOR][COLOR=#0000BB]$mail_status[/COLOR][COLOR=#007700]) { [/COLOR][COLOR=#0000BB]?>[/COLOR][/COLOR]

    <script language="javascript" type="text/javascript">

        alert('Thank you for the message. We will contact you shortly.');

        window.location = 'contact_page.html';

    </script>

[COLOR=#000000][COLOR=#0000BB]<?php

[/COLOR][COLOR=#007700]}

else { [/COLOR][COLOR=#0000BB]?>[/COLOR][/COLOR]

    <script language="javascript" type="text/javascript">

        alert('Message failed. Please, send an email to hornerkris@gmail.com');

        window.location = 'contact_page.html';

    </script>

[COLOR=#000000][COLOR=#0000BB]<?php

[/COLOR][COLOR=#007700]}

[/COLOR][COLOR=#0000BB]?>[/COLOR][/COLOR]
``````
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

<html xmlns="http://www.w3.org/1999/xhtml">

<head>

<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />

<title>Contact Form</title>

</head>



<body>

<form action="contact.php" method="post">

    Your name<br>

    <input type="text" name="cf_name"><br>

    Your e-mail<br>

    <input type="text" name="cf_email"><br>

    Message<br>

    <textarea name="cf_message" Rows=20 Cols=100></textarea><br>

    <input type="submit" value="Send">

    <input type="reset" value="Clear">

</form>

</body>

</html>
```

---

