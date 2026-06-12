---
title: "How to use smtp authentication for php mail form?"
date: 2010-10-28
forum: General Help
---

### Post by karthick87 on 2010-10-28
The php mail form is designed using post function,normally the mails are not getting delivered without smtp authentication.So can someone say me on adding smtp authentication to php email form.

---

### Post by babur on 2010-10-28
You can use PEAR's Mail::Factory to create the mailer instance with SMTP host,port,username,pass for SMTP authentication. 

Also you can use Swiftmailer php library to create the mailer instance with SMTP authentication.

---

### Post by karthick87 on 2010-10-28
I am not so familiar with php can you pls provide me the php script for smpt authentication?

This is my php script to send mails without authentication,i want to use smtp authentication for sending mails..How to modify this script..?

[PHP]<?php

session_start();

if ($_POST['Submit'] == 'Send')

{


$to = $_POST['toemail'];

$subject = $_POST['subject'];

$message = $_POST['message'];

$fromemail = $_POST['fromemail'];

$fromname = $_POST['fromname'];

$lt= '<';

$gt= '>';

$sp= ' ';

$from= 'From:';

$headers = $from.$fromname.$sp.$lt.$fromemail.$gt;

mail($to,$subject,$message,$headers);

header("Location: sendmail.php?msg= Mail Sent!");

exit();

}

?>

<html>

<head>

<title>Email </title>

</head>

<body bgcolor="#ffffcc">

<h2 align="center">

Email
</h2>

<h3 align="center">

Please do not misuse this script.
</h3><br>

<p style="margin-left:15px">

<form action="sendmail.php" method="POST">

<b>From Name:</b><br>

<input type="text" name="fromname" size="50"><br>

<br><b>From Email:</b><br>

<input type="text" name="fromemail" size="50"><br>

<br><b>To Email:</b><br>

<input type="text" name="toemail" size="50"><br>

<br><b>Subject:</b><br>

<input type="text" name="subject" size="74"><br>

<br><b>Your Message:</b><br>

<textarea name="message" rows="5" cols="50">

</textarea><br>

<input type="submit" name="Submit" value="Send">

<input type="reset" value="Reset">

</form>

</p>

<?php if (isset($_GET['msg'])) { echo "<font color=\"red\"><h3 align=\"center\"> $_GET[msg] </h3></font>"; } ?>

</body>

</html>[/PHP]

---

### Post by babur on 2010-10-29
First download swiftmailer from "http://swiftmailer.org/download" and extract in a location. ie: /opt/ or in your current dev location. 

Then replace the below code with your mailing snippet and change the SMTP host credentials. Since the mailer will throw exceptions for using null values/email address, you have to implement the form validation to avoid using null values.

[PHP]
<?php

// include swift mailer library
require_once 'Swift/lib/swift_required.php';

if($_POST['Submit'] == "Send")
  {

    // mailer smtp auth
    $smtpauth = Swift_SmtpTransport::newInstance('smtp.localhost',25)
      ->setUsername('user')
      ->setPassword('pass');

    // mailer intance
    $mailer = Swift_Mailer::newInstance($smtpauth);
    
    $to = $_POST['toemail'];
    $subject = $_POST['subject'];
    $message = $_POST['message'];
    $fromemail = $_POST['fromemail'];
    $fromname = $_POST['fromname'];
    
    // composing message
    $compose = Swift_Message::newInstance($subject)
      ->setFrom(array($fromemail => $fromname))
      ->setTo(array($to => 'Friends'))
      ->setBody($message);
    
    // sending mail
    $mail_status = $mailer->send($compose);
    
    $location = $PHP_SELF."?msg=Mail Sent!";
    header("Location: $location");
    
    exit();
       
  }

?>

<html>

<head>

<title>Email </title>

</head>

<body bgcolor="#ffffcc">

<h2 align="center">

Email
</h2>

<h3 align="center">

Please do not misuse this script.
</h3><br>

<p style="margin-left:15px">

<form action="<?php echo $PHP_SELF; ?>" method="POST">

<b>From Name:</b><br>

<input type="text" name="fromname" size="50"><br>

<br><b>From Email:</b><br>

<input type="text" name="fromemail" size="50"><br>

<br><b>To Email:</b><br>

<input type="text" name="toemail" size="50"><br>

<br><b>Subject:</b><br>

<input type="text" name="subject" size="74"><br>

<br><b>Your Message:</b><br>

<textarea name="message" rows="5" cols="50">

</textarea><br>

<input type="submit" name="Submit" value="Send">

<input type="reset" value="Reset">

</form>

</p>

<?php if (isset($_GET['msg'])) { echo "<font color=\"red\"><h3 align=\"center\"> $_GET[msg] </h3></font>"; } ?>

</body>

</html>
[/PHP]


Refer the documentation section of swiftmailer for more info.

---

### Post by karthick87 on 2010-10-29
[PHP]
<?php

// include swift mailer library
require_once 'Swift/lib/swift_required.php';

if($_POST['Submit'] == "Send")
  {

    // mailer smtp auth
    $smtpauth = Swift_SmtpTransport::newInstance('smtp.gmail.com',587)
      ->setUsername('gmailusername')
      ->setPassword('gmailpassword');

    // mailer intance
    $mailer = Swift_Mailer::newInstance($smtpauth);
    
    $to = $_POST['toemail'];
    $subject = $_POST['subject'];
    $message = $_POST['message'];
    $fromemail = $_POST['fromemail'];
    $fromname = $_POST['fromname'];
    
    // composing message
    $compose = Swift_Message::newInstance($subject)
      ->setFrom(array($fromemail => $fromname))
      ->setTo(array($to => 'Friends'))
      ->setBody($message);
    
    // sending mail
    $mail_status = $mailer->send($compose);
    
    $location = $PHP_SELF."?msg=Mail Sent!";
    header("Location: $location");
    
    exit();
       
  }

?>

<html>

<head>

<title>Email </title>

</head>

<body bgcolor="#ffffcc">

<h2 align="center">

Email
</h2>

<h3 align="center">

Please do not misuse this script.
</h3><br>

<p style="margin-left:15px">

<form action="<?php echo $PHP_SELF; ?>" method="POST">

<b>From Name:</b><br>

<input type="text" name="fromname" size="50"><br>

<br><b>From Email:</b><br>

<input type="text" name="fromemail" size="50"><br>

<br><b>To Email:</b><br>

<input type="text" name="toemail" size="50"><br>

<br><b>Subject:</b><br>

<input type="text" name="subject" size="74"><br>

<br><b>Your Message:</b><br>

<textarea name="message" rows="5" cols="50">

</textarea><br>

<input type="submit" name="Submit" value="Send">

<input type="reset" value="Reset">

</form>

</p>

<?php if (isset($_GET['msg'])) { echo "<font color=\"red\"><h3 align=\"center\"> $_GET[msg] </h3></font>"; } ?>

</body>

</html>
[/PHP]I have changed the smtp settings in the script..But still i dont get the mail...Did you checked..?

---

### Post by babur on 2010-10-29
Yes, I checked it was and it is working.  Moreover I have used the same SMTP authentication for my dev purpose.

Do you get any exception? Check in your apache error log, if you use apache.

---

### Post by karthick87 on 2010-10-29
I am using postfix..How to check the logs..?

---

### Post by babur on 2010-11-02
Postfix log file "mail.log" is stored in "/var/log/".

However Postfix is a MTA and not web server.

Hope you are using web server (apache) to host/access the PHP files. By default the logs of apache web server will be in "/var/log/apache2/". So you have to check the "error" logs in this location.  

Type the command "tail -f /var/log/apache2/error.log" in a terminal to view the errors of apache web server in append mode.

Also make sure with the below items:-

- Check the Postfix, Apache web server services
- Check the swift mailer integration and the path
- Are you getting any "mailer daemon errors"

If nothings works out, let me understand how you are accessing the php mailer form and the swift mailer integrations.

---

### Post by karthick87 on 2010-11-02
I accessed my php page from localhost...

[http://127.0.0.1/sendmail.php](http://127.0.0.1/sendmail.php)

The form appeared..

Filled out everything..But when i click send a blank page is appearing..

This is my apache log:

```
karthick@Ubuntu-desktop:~$ tail -f /var/log/apache2/error.log
[Mon Nov 01 10:11:59 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Mon Nov 01 13:10:53 2010] [notice] caught SIGTERM, shutting down
[Mon Nov 01 19:47:32 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Tue Nov 02 01:57:11 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Tue Nov 02 02:04:59 2010] [notice] caught SIGTERM, shutting down
[Tue Nov 02 03:26:21 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Tue Nov 02 05:12:48 2010] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Tue Nov 02 05:12:53 2010] [error] [client 127.0.0.1] PHP Notice:  Undefined index: Submit in /var/www/sendmail.php on line 6, referer: http://127.0.0.1/
[Tue Nov 02 05:12:53 2010] [error] [client 127.0.0.1] PHP Notice:  Undefined variable: PHP_SELF in /var/www/sendmail.php on line 63, referer: http://127.0.0.1/
[Tue Nov 02 05:17:13 2010] [error] [client 127.0.0.1] PHP Fatal error:  Call to undefined method Swift_MailTransport::setUsername() in /var/www/sendmail.php on line 11, referer: http://127.0.0.1/sendmail.php

```

---

### Post by babur on 2010-11-02
Fine, check your code and clear the errors. ie:
[I]
[Tue Nov 02 05:17:13 2010] [error] [client 127.0.0.1] PHP Fatal error:  Call to undefined method Swift_MailTransport::setUsername() in /var/www/sendmail.php on line 11, referer: [http://127.0.0.1/sendmail.php](http://127.0.0.1/sendmail.php)[/I]


Refer this or the code i sent earlier to add username and password: 
[http://swiftmailer.org/docs/smtp-authentication](http://swiftmailer.org/docs/smtp-authentication)

Make the necessary changes and let me know if there is anything.

---

### Post by karthick87 on 2010-11-02
Edited codings

[PHP]<?php

// include swift mailer library
require_once 'Swift/lib/swift_required.php';

if($_POST['Submit'] == "Send")
  {

    // mailer smtp auth
    $smtpauth = Swift_SmtpTransport::newInstance('smtp.gmail.com',575)
      ->setUsername('name@gmail.com')
      ->setPassword('123456789');

    // mailer intance
    $mailer = Swift_Mailer::newInstance($smtpauth);
    
    $to = $_POST['toemail'];
    $subject = $_POST['subject'];
    $message = $_POST['message'];
    $fromemail = $_POST['fromemail'];
    $fromname = $_POST['fromname'];
    
    // composing message
    $compose = Swift_Message::newInstance($subject)
      ->setFrom(array($fromemail => $fromname))
      ->setTo(array($to => 'Friends'))
      ->setBody($message);
    
    // sending mail
    $mail_status = $mailer->send($compose);
    
    $location = $PHP_SELF."?msg=Mail Sent!";
    header("Location: $location");
    
    exit();
       
  }

?>

<html>

<head>

<title>Email </title>

</head>

<body bgcolor="#ffffcc">

<h2 align="center">

Email
</h2>

<h3 align="center">

Please do not misuse this script.
</h3><br>

<p style="margin-left:15px">

<form action="<?php echo $PHP_SELF; ?>" method="POST">

<b>From Name:</b><br>

<input type="text" name="fromname" size="50"><br>

<br><b>From Email:</b><br>

<input type="text" name="fromemail" size="50"><br>

<br><b>To Email:</b><br>

<input type="text" name="toemail" size="50"><br>

<br><b>Subject:</b><br>

<input type="text" name="subject" size="74"><br>

<br><b>Your Message:</b><br>

<textarea name="message" rows="5" cols="50">

</textarea><br>

<input type="submit" name="Submit" value="Send">

<input type="reset" value="Reset">

</form>

</p>

<?php if (isset($_GET['msg'])) { echo "<font color=\"red\"><h3 align=\"center\"> $_GET[msg] </h3></font>"; } ?>

</body>

</html>[/PHP]

[COLOR=Red]Apache log[/COLOR]

```
[Thu Oct 28 10:47:25 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Thu Oct 28 12:12:27 2010] [notice] caught SIGTERM, shutting down
[Thu Oct 28 16:02:49 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Thu Oct 28 16:07:10 2010] [notice] caught SIGTERM, shutting down
[Thu Oct 28 16:08:15 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Thu Oct 28 16:16:41 2010] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Thu Oct 28 16:16:51 2010] [error] [client 127.0.0.1] PHP Notice:  Undefined index: Submit in /var/www/sendmail.php on line 6, referer: http://127.0.0.1/
sendmail: fatal: www-data(33): No recipient addresses found in message header
[Thu Oct 28 16:17:24 2010] [error] [client 127.0.0.1] PHP Notice:  Undefined index: Submit in /var/www/sendmail.php on line 6, referer: http://127.0.0.1/sendmail.php
sendmail: fatal: www-data(33): No recipient addresses found in message header
[Thu Oct 28 16:17:27 2010] [error] [client 127.0.0.1] PHP Notice:  Undefined index: Submit in /var/www/sendmail.php on line 6, referer: http://127.0.0.1/sendmail.php?msg=%20Mail%20Sent!
sendmail: fatal: www-data(33): No recipient addresses found in message header
[Thu Oct 28 16:17:30 2010] [error] [client 127.0.0.1] PHP Notice:  Undefined index: Submit in /var/www/sendmail.php on line 6, referer: http://127.0.0.1/sendmail.php?msg=%20Mail%20Sent!
sendmail: fatal: www-data(33): No recipient addresses found in message header
[Thu Oct 28 16:17:35 2010] [error] [client 127.0.0.1] PHP Notice:  Undefined index: Submit in /var/www/sendmail.php on line 6, referer: http://127.0.0.1/sendmail.php?msg=%20Mail%20Sent!
[Thu Oct 28 16:46:05 2010] [notice] caught SIGTERM, shutting down
[Thu Oct 28 18:16:31 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Thu Oct 28 19:44:40 2010] [notice] caught SIGTERM, shutting down
[Thu Oct 28 19:53:49 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Thu Oct 28 20:11:39 2010] [notice] caught SIGTERM, shutting down
[Thu Oct 28 22:21:17 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Thu Oct 28 22:33:00 2010] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Thu Oct 28 22:38:44 2010] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Thu Oct 28 22:54:55 2010] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Fri Oct 29 02:24:36 2010] [notice] caught SIGTERM, shutting down
[Fri Oct 29 02:25:48 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Fri Oct 29 02:48:27 2010] [notice] caught SIGTERM, shutting down
[Fri Oct 29 09:20:07 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Fri Oct 29 10:46:49 2010] [notice] caught SIGTERM, shutting down
[Fri Oct 29 10:48:08 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Fri Oct 29 10:49:27 2010] [notice] caught SIGTERM, shutting down
[Fri Oct 29 14:13:11 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Fri Oct 29 14:21:13 2010] [notice] caught SIGTERM, shutting down
[Fri Oct 29 21:37:09 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Fri Oct 29 21:48:28 2010] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Fri Oct 29 21:48:30 2010] [error] [client 127.0.0.1] PHP Warning:  require_once(Swift/lib/swift_required.php): failed to open stream: No such file or directory in /var/www/sendmail.php on line 4, referer: http://127.0.0.1/
[Fri Oct 29 21:48:30 2010] [error] [client 127.0.0.1] PHP Fatal error:  require_once(): Failed opening required 'Swift/lib/swift_required.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/sendmail.php on line 4, referer: http://127.0.0.1/
[Fri Oct 29 21:48:36 2010] [error] [client 127.0.0.1] PHP Warning:  require_once(Swift/lib/swift_required.php): failed to open stream: No such file or directory in /var/www/sendmail.php on line 4, referer: http://127.0.0.1/
[Fri Oct 29 21:48:36 2010] [error] [client 127.0.0.1] PHP Fatal error:  require_once(): Failed opening required 'Swift/lib/swift_required.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/sendmail.php on line 4, referer: http://127.0.0.1/
[Fri Oct 29 21:48:37 2010] [error] [client 127.0.0.1] PHP Warning:  require_once(Swift/lib/swift_required.php): failed to open stream: No such file or directory in /var/www/sendmail.php on line 4, referer: http://127.0.0.1/
[Fri Oct 29 21:48:37 2010] [error] [client 127.0.0.1] PHP Fatal error:  require_once(): Failed opening required 'Swift/lib/swift_required.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/sendmail.php on line 4, referer: http://127.0.0.1/
[Fri Oct 29 21:48:38 2010] [error] [client 127.0.0.1] PHP Warning:  require_once(Swift/lib/swift_required.php): failed to open stream: No such file or directory in /var/www/sendmail.php on line 4, referer: http://127.0.0.1/
[Fri Oct 29 21:48:38 2010] [error] [client 127.0.0.1] PHP Fatal error:  require_once(): Failed opening required 'Swift/lib/swift_required.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/sendmail.php on line 4, referer: http://127.0.0.1/
[Fri Oct 29 21:49:04 2010] [error] [client 127.0.0.1] PHP Warning:  require_once(Swift/lib/swift_required.php): failed to open stream: No such file or directory in /var/www/sendmail.php on line 4, referer: http://127.0.0.1/
[Fri Oct 29 21:49:04 2010] [error] [client 127.0.0.1] PHP Fatal error:  require_once(): Failed opening required 'Swift/lib/swift_required.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/sendmail.php on line 4, referer: http://127.0.0.1/
[Fri Oct 29 21:49:05 2010] [error] [client 127.0.0.1] PHP Warning:  require_once(Swift/lib/swift_required.php): failed to open stream: No such file or directory in /var/www/sendmail.php on line 4, referer: http://127.0.0.1/
[Fri Oct 29 21:49:05 2010] [error] [client 127.0.0.1] PHP Fatal error:  require_once(): Failed opening required 'Swift/lib/swift_required.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/sendmail.php on line 4, referer: http://127.0.0.1/
[Fri Oct 29 21:53:02 2010] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Fri Oct 29 21:53:02 2010] [error] [client 127.0.0.1] PHP Notice:  Undefined index: Submit in /var/www/sendmail.php on line 6, referer: http://127.0.0.1/
[Fri Oct 29 21:53:02 2010] [error] [client 127.0.0.1] PHP Notice:  Undefined variable: PHP_SELF in /var/www/sendmail.php on line 63, referer: http://127.0.0.1/
[Fri Oct 29 21:53:39 2010] [error] [client 127.0.0.1] PHP Warning:  fsockopen(): php_network_getaddresses: getaddrinfo failed: No address associated with hostname in /var/www/Swift/lib/classes/Swift/Transport/StreamBuffer.php on line 233, referer: http://127.0.0.1/sendmail.php
[Fri Oct 29 21:53:39 2010] [error] [client 127.0.0.1] PHP Warning:  fsockopen(): unable to connect to smtp.localhost:25 (php_network_getaddresses: getaddrinfo failed: No address associated with hostname) in /var/www/Swift/lib/classes/Swift/Transport/StreamBuffer.php on line 233, referer: http://127.0.0.1/sendmail.php
[Fri Oct 29 21:53:39 2010] [error] [client 127.0.0.1] PHP Fatal error:  Uncaught exception 'Swift_TransportException' with message 'Connection could not be established with host smtp.localhost [php_network_getaddresses: getaddrinfo failed: No address associated with hostname #0]' in /var/www/Swift/lib/classes/Swift/Transport/StreamBuffer.php:235\nStack trace:\n#0 /var/www/Swift/lib/classes/Swift/Transport/StreamBuffer.php(70): Swift_Transport_StreamBuffer->_establishSocketConnection()\n#1 /var/www/Swift/lib/classes/Swift/Transport/AbstractSmtpTransport.php(101): Swift_Transport_StreamBuffer->initialize(Array)\n#2 /var/www/Swift/lib/classes/Swift/Mailer.php(74): Swift_Transport_AbstractSmtpTransport->start()\n#3 /var/www/sendmail.php(30): Swift_Mailer->send(Object(Swift_Message))\n#4 {main}\n  thrown in /var/www/Swift/lib/classes/Swift/Transport/StreamBuffer.php on line 235, referer: http://127.0.0.1/sendmail.php
[Fri Oct 29 21:53:39 2010] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Fri Oct 29 21:54:23 2010] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Fri Oct 29 21:54:26 2010] [error] [client 127.0.0.1] PHP Fatal error:  Uncaught exception 'Swift_TransportException' with message 'Expected response code 250 but got code "530", with message "530 5.7.0 Must issue a STARTTLS command first. d21sm536675ibg.15\r\n"' in /var/www/Swift/lib/classes/Swift/Transport/AbstractSmtpTransport.php:406\nStack trace:\n#0 /var/www/Swift/lib/classes/Swift/Transport/AbstractSmtpTransport.php(290): Swift_Transport_AbstractSmtpTransport->_assertResponseCode('530 5.7.0 Must ...', Array)\n#1 /var/www/Swift/lib/classes/Swift/Transport/EsmtpTransport.php(197): Swift_Transport_AbstractSmtpTransport->executeCommand('MAIL FROM: <kar...', Array, Array)\n#2 /var/www/Swift/lib/classes/Swift/Transport/EsmtpTransport.php(268): Swift_Transport_EsmtpTransport->executeCommand('MAIL FROM: <kar...', Array)\n#3 /var/www/Swift/lib/classes/Swift/Transport/AbstractSmtpTransport.php(441): Swift_Transport_EsmtpTransport->_doMailFromCommand('karthick@gmail....')\n#4 /var/www/Swift/lib/classes/Swift/Transport/AbstractSmtpTransport.php(477): Swift_Transport_AbstractSmtpTransport->_do in /var/www/Swift/lib/classes/Swift/Transport/AbstractSmtpTransport.php on line 406, referer: http://127.0.0.1/sendmail.php
[Fri Oct 29 21:54:52 2010] [error] [client 127.0.0.1] PHP Fatal error:  Uncaught exception 'Swift_TransportException' with message 'Expected response code 250 but got code "530", with message "530 5.7.0 Must issue a STARTTLS command first. gy41sm3769388ibb.11\r\n"' in /var/www/Swift/lib/classes/Swift/Transport/AbstractSmtpTransport.php:406\nStack trace:\n#0 /var/www/Swift/lib/classes/Swift/Transport/AbstractSmtpTransport.php(290): Swift_Transport_AbstractSmtpTransport->_assertResponseCode('530 5.7.0 Must ...', Array)\n#1 /var/www/Swift/lib/classes/Swift/Transport/EsmtpTransport.php(197): Swift_Transport_AbstractSmtpTransport->executeCommand('MAIL FROM: <kar...', Array, Array)\n#2 /var/www/Swift/lib/classes/Swift/Transport/EsmtpTransport.php(268): Swift_Transport_EsmtpTransport->executeCommand('MAIL FROM: <kar...', Array)\n#3 /var/www/Swift/lib/classes/Swift/Transport/AbstractSmtpTransport.php(441): Swift_Transport_EsmtpTransport->_doMailFromCommand('karthick@gmail....')\n#4 /var/www/Swift/lib/classes/Swift/Transport/AbstractSmtpTransport.php(477): Swift_Transport_AbstractSmtpTransport->_ in /var/www/Swift/lib/classes/Swift/Transport/AbstractSmtpTransport.php on line 406, referer: http://127.0.0.1/sendmail.php
[Fri Oct 29 21:54:57 2010] [error] [client 127.0.0.1] PHP Fatal error:  Uncaught exception 'Swift_TransportException' with message 'Expected response code 250 but got code "530", with message "530 5.7.0 Must issue a STARTTLS command first. u6sm3775473ibd.6\r\n"' in /var/www/Swift/lib/classes/Swift/Transport/AbstractSmtpTransport.php:406\nStack trace:\n#0 /var/www/Swift/lib/classes/Swift/Transport/AbstractSmtpTransport.php(290): Swift_Transport_AbstractSmtpTransport->_assertResponseCode('530 5.7.0 Must ...', Array)\n#1 /var/www/Swift/lib/classes/Swift/Transport/EsmtpTransport.php(197): Swift_Transport_AbstractSmtpTransport->executeCommand('MAIL FROM: <kar...', Array, Array)\n#2 /var/www/Swift/lib/classes/Swift/Transport/EsmtpTransport.php(268): Swift_Transport_EsmtpTransport->executeCommand('MAIL FROM: <kar...', Array)\n#3 /var/www/Swift/lib/classes/Swift/Transport/AbstractSmtpTransport.php(441): Swift_Transport_EsmtpTransport->_doMailFromCommand('karthick@gmail....')\n#4 /var/www/Swift/lib/classes/Swift/Transport/AbstractSmtpTransport.php(477): Swift_Transport_AbstractSmtpTransport->_doM in /var/www/Swift/lib/classes/Swift/Transport/AbstractSmtpTransport.php on line 406, referer: http://127.0.0.1/sendmail.php
[Fri Oct 29 22:02:55 2010] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Fri Oct 29 22:02:59 2010] [error] [client 127.0.0.1] PHP Fatal error:  Uncaught exception 'Swift_RfcComplianceException' with message 'Address in mailbox given [] does not comply with RFC 2822, 3.6.2.' in /var/www/Swift/lib/classes/Swift/Mime/Headers/MailboxHeader.php:309\nStack trace:\n#0 /var/www/Swift/lib/classes/Swift/Mime/Headers/MailboxHeader.php(239): Swift_Mime_Headers_MailboxHeader->_assertValidAddress('')\n#1 /var/www/Swift/lib/classes/Swift/Mime/Headers/MailboxHeader.php(97): Swift_Mime_Headers_MailboxHeader->normalizeMailboxes(Array)\n#2 /var/www/Swift/lib/classes/Swift/Mime/Headers/MailboxHeader.php(61): Swift_Mime_Headers_MailboxHeader->setNameAddresses(Array)\n#3 /var/www/Swift/lib/classes/Swift/Mime/SimpleMimeEntity.php(571): Swift_Mime_Headers_MailboxHeader->setFieldBodyModel(Array)\n#4 /var/www/Swift/lib/classes/Swift/Mime/SimpleMessage.php(199): Swift_Mime_SimpleMimeEntity->_setHeaderFieldModel('From', Array)\n#5 /var/www/sendmail.php(25): Swift_Mime_SimpleMessage->setFrom(Array)\n#6 {main}\n  thrown in /var/www/Swift/lib/classes/Swift/Mime/Headers/MailboxHeader.php on line 309, referer: http://127.0.0.1/sendmail.php
[Fri Oct 29 22:04:05 2010] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Fri Oct 29 22:04:31 2010] [error] [client 127.0.0.1] PHP Fatal error:  Uncaught exception 'Swift_TransportException' with message 'Expected response code 250 but got code "530", with message "530 5.7.0 Must issue a STARTTLS command first. d21sm546689ibg.3\r\n"' in /var/www/Swift/lib/classes/Swift/Transport/AbstractSmtpTransport.php:406\nStack trace:\n#0 /var/www/Swift/lib/classes/Swift/Transport/AbstractSmtpTransport.php(290): Swift_Transport_AbstractSmtpTransport->_assertResponseCode('530 5.7.0 Must ...', Array)\n#1 /var/www/Swift/lib/classes/Swift/Transport/EsmtpTransport.php(197): Swift_Transport_AbstractSmtpTransport->executeCommand('MAIL FROM: <kar...', Array, Array)\n#2 /var/www/Swift/lib/classes/Swift/Transport/EsmtpTransport.php(268): Swift_Transport_EsmtpTransport->executeCommand('MAIL FROM: <kar...', Array)\n#3 /var/www/Swift/lib/classes/Swift/Transport/AbstractSmtpTransport.php(441): Swift_Transport_EsmtpTransport->_doMailFromCommand('karthick@gmail....')\n#4 /var/www/Swift/lib/classes/Swift/Transport/AbstractSmtpTransport.php(477): Swift_Transport_AbstractSmtpTransport->_doM in /var/www/Swift/lib/classes/Swift/Transport/AbstractSmtpTransport.php on line 406, referer: http://127.0.0.1/sendmail.php
[Fri Oct 29 22:04:31 2010] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Fri Oct 29 22:09:03 2010] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Fri Oct 29 22:09:05 2010] [error] [client 127.0.0.1] PHP Fatal error:  Call to undefined method Swift_MailTransport::setUsername() in /var/www/sendmail.php on line 11, referer: http://127.0.0.1/sendmail.php
[Fri Oct 29 22:09:21 2010] [error] [client 127.0.0.1] PHP Fatal error:  Call to undefined method Swift_MailTransport::setUsername() in /var/www/sendmail.php on line 11, referer: http://127.0.0.1/sendmail.php
[Fri Oct 29 22:10:21 2010] [error] [client 127.0.0.1] PHP Fatal error:  Call to undefined method Swift_MailTransport::setUsername() in /var/www/sendmail.php on line 11, referer: http://127.0.0.1/sendmail.php
[Fri Oct 29 22:10:21 2010] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Fri Oct 29 22:10:49 2010] [error] [client 127.0.0.1] PHP Fatal error:  Call to undefined method Swift_MailTransport::setUsername() in /var/www/sendmail.php on line 11, referer: http://127.0.0.1/sendmail.php
[Fri Oct 29 22:14:21 2010] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Fri Oct 29 22:14:24 2010] [error] [client 127.0.0.1] PHP Fatal error:  Call to undefined method Swift_MailTransport::setUsername() in /var/www/sendmail.php on line 11, referer: http://127.0.0.1/sendmail.php
[Fri Oct 29 22:14:59 2010] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Fri Oct 29 22:20:08 2010] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Fri Oct 29 22:21:05 2010] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Fri Oct 29 23:34:25 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Sat Oct 30 04:09:29 2010] [notice] caught SIGTERM, shutting down
[Sat Oct 30 10:41:50 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Sat Oct 30 11:21:36 2010] [notice] caught SIGTERM, shutting down
[Sat Oct 30 11:30:19 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Sat Oct 30 11:56:22 2010] [notice] caught SIGTERM, shutting down
[Sat Oct 30 13:08:00 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Sat Oct 30 15:33:55 2010] [notice] caught SIGTERM, shutting down
[Sat Oct 30 21:22:47 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Sun Oct 31 01:51:17 2010] [notice] caught SIGTERM, shutting down
[Sun Oct 31 01:52:22 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Sun Oct 31 01:57:21 2010] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
```

Still i cant send mails :(

---

### Post by babur on 2010-11-03
Hope gmail uses STARTTLS communication protocol, so try to make the changes with the port as 465 and adding "tls" mode when you create the smtp transport.
ie:

[PHP]
$smtpauth = Swift_SmtpTransport::newInstance('smtp.gmail.com',465,'tls')
     	->setUsername('testuser')
      	->setPassword('testuser')
      	;[/PHP]


If you get any error when you submit the form, send me the dump.

---

### Post by karthick87 on 2010-11-03
Oops :) now i can send the mail..The problem gets solved.

---

### Post by techexpert on 2011-03-07
Thank you very much! I, too, was using port # 587 and couldn't figure out why it wouldn't work with Gmail when it worked with other SMTP servers. Setting port to 465 (my 'tls' option was already set) did the trick! Thanks a HUGE LOT!

---

