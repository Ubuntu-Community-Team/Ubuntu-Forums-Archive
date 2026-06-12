---
title: "sendmail, php"
date: 2010-09-14
forum: General Help
---

### Post by 1cookie on 2010-09-14
hi

OK, I just want to be able to send emails through my webserver, setup. I couldn't find a dev forum - so thought i'd post here.

I'd like to be able to send emails (form my localhost setup) to and from my global client, namely: ( ***@yahoo.com), using PHP and Apache. A snippet from my php.ini file looks like:

```
 
...
; For Unix only.  You may supply arguments as well (default: "sendmail -t -i").
; http://php.net/sendmail-path
sendmail_path = /usr/sbin/sendmail -i -t
sendmail_from = example@yahoo.com
...

```Now, I never could get this working in Windows, let alone Linux. I could do with it working though. Can anyone help with this please? 

:p

---

### Post by btindie on 2010-09-14
Try using google, I'm sure you'll find lots of [answers]("http://php.net/manual/en/function.mail.php").
 
As an alternative to the PHP mail function you could use the [XPertMailer]("http://www.xpertmailer.com/") PHP class
 
```
<?php
header('Content-Type: text/plain');
 
$emailToAddress = 'me@gmail.com';
$emailToName = 'My Name';
$emailFromAddress = 'root@localhost';
$emailFromName = 'root';
$emailSubject = 'Test Message';
$emailBody = 'This is a test mail';
 
error_reporting(E_ALL); // php errors
define('DISPLAY_XPM4_ERRORS', true); // display XPM4 errors
 
require_once('includes/xPertMailer/MAIL.php');
 
$m = new MAIL;
 
// explicitly set the Return-Path otherwise it comes out as anonymous
$m->Path($emailFromAddress);
$m->From($emailFromAddress, $emailFromName);
$m->AddTo($emailToAddress, $emailToName);
$m->Subject($emailSubject);
$m->Text($emailBody);
// attach a file to the email
$m->Attach(file_get_contents('/etc/postfix/main.cf'), 'text/plain', 'main.cf');
 
// send mail using /usr/bin/sendmail
echo ($m->Send('sendmail') ? 'Mail sent!' : 'Error!') . '\n';
 
print_r($m->History);
 
?>
```

---

### Post by JohDut on 2010-09-14
Or if you just want to send a mail through your/an existing smtp-server you could use php-mail.

First install:
sudo apt-get install php-mail php-net-smtp

And then your php code would look something like this:
```
<?php
require_once "Mail.php"; // this require is automatically fullfilled by the installed packages

$from = "Realname from <fromme@example.org>";
$to = "Sendto <sendto@example.org>";
$subject = "Test message ".date("d-m-Y / H:i");
$body = "Some text\n\n".date("d-m-Y / H:i");

$host = "192.168.1.100"; // Set IP or hostname of the smtp-server you want to use

$headers = array ('From' => $from,'To' => $to,'Subject' => $subject);
$smtp = Mail::factory('smtp',array ('host' => $host));
$mail = $smtp->send($to, $headers, $body);

if (PEAR::isError($mail)) {
echo("<p>" . $mail->getMessage() . "</p>");
} else {
echo("<p>Message sent succesfully ".date("d-m-Y / H:i")."</p>");
}
?>
```

If you want you can also use an secure connection.
And if you need, you can also use authentication to the smtp-server.
The code would like this (you can use either independently of eachother)

```
<?php
require_once "Mail.php";

$from = "Realname from <fromme@example.org>";
$to = "Sendto <sendto@example.org>";
$subject = "Test message ".date("d-m-Y / H:i");
$body = "Some text\n\n".date("d-m-Y / H:i");

$host = "ssl://192.168.1.100"; // again set IP or hostname of the smtp-server you want to use. If your smtp-server is on IP 192.168.1.100 it would look like this
$port = "465";
$username = "username on SMTP-server"; // smtp username needed tot authenticate
$password = "password on SMTP-server"; // smtp password needed tot authenticate

$headers = array ('From' => $from,
'To' => $to,
'Subject' => $subject);
$smtp = Mail::factory('smtp',
array ('host' => $host,
'port' => $port,
'auth' => true,
'username' => $username,
'password' => $password));

$mail = $smtp->send($to, $headers, $body);

if (PEAR::isError($mail)) {
echo("<p>" . $mail->getMessage() . "</p>");
} else {
echo("<p>Message successfully sent!</p>");
}
?>
```

---

### Post by 1cookie on 2010-09-15
hi

> **JohDut said:**
> Or if you just want to send a mail through your/an existing smtp-server you could use php-mail.

First install:
sudo apt-get install php-mail php-net-smtp


I like the idea of using php-mail, so I've installed the package you mention above, thanks. :)  I have a broadband connection, so by default have email settings, smtp and pop3. Trouble is I'm having difficulty setting all this up locally on Lucid 10.04. Please see an earlier post: [http://ubuntuforums.org/showthread.php?t=1507060](http://ubuntuforums.org/showthread.php?t=1507060)

Using your code below (with my details appended):
 
> 

And then your php code would look something like this:
```
<?php
require_once "Mail.php"; // this require is automatically fullfilled by the installed packages

...

$host = "smtp.virginmedia.com:465"; // Set IP or hostname of the smtp-server you want to use
...

?>
```and running this script, I get the following response:

> 
Failed to connect to smtp.virginmedia.com:465:25 [SMTP: Invalid response code received from server (code: -1, response: ()]
Clearly my email is not set-up correctly, as the script seems to be executing this line: 

```

if (PEAR::isError($mail)) {
echo("<p>" . $mail->getMessage() . "</p>");

```I have all the correct information, smtp, pop3 and username/password are correct as ive checked with Virginmedia? I just don't get it?



;)

---

### Post by btindie on 2010-09-15
Take a look at JohDut's second example, it shows how to specify the port to connect to.
 
```
$host = "smtp.virginmedia.com";
$port = "465";
 
$smtp = Mail::factory('smtp',
    array ('host' => $host,
           'port' => $port));
```
 
> Failed to connect to smtp.virginmedia.com:465:25 [SMTP: Invalid response code received from server (code: -1, response: ()]
From your error response it shows that it tried to connect to the host *'smtp.virginmedia.com:465'* on the SMTP port, 25.

---

### Post by 1cookie on 2010-09-19
> **btindie said:**
> Take a look at JohDut's second example, it shows how to specify the port to connect to.
 

Yes, and now we're into ports, usb's, circuits, binary and electricity..:) lol. But that aside, where do i go about finding port (the host will be [EMAIL="myname@yahoo.com"]myname@yahoo.com[/EMAIL]?) numbers to connect to yahoo? I know what your gonna say now, 'the shell?'


:(:)

I'd love to try JonDut's example when i get some time..

---

### Post by btindie on 2010-09-19
> But that aside, where do i go about finding port (the host will be [EMAIL="myname@yahoo.com"][COLOR=#000000]myname@yahoo.com[/COLOR][/EMAIL]?) numbers to connect to yahoo?
That is your email address (user@domain) and not your host for relaying email to.
 
From your previous post where you had the problem connecting it looks like you tried JonDut's first example, the second one allows you to specify a non-standard port to use. You were trying to connect to *smtp.virginmedia.com:465* - 465 is the port number. You can test that it is correct by typing
```
telnet smtp.virginmedia.com 465
``` from the command line. It should display a welcome message if it worked. Once connected you can send a test email to see if it'll work
```
EHLO localhost
MAIL FROM: [EMAIL="myname@yahoo.com"]myname@yahoo.com[/EMAIL]
RCPT TO: [EMAIL="myname@yahoo.com"]myname@yahoo.com[/EMAIL]
DATA
Subject: Test message
wibble wibble
.

``` don't miss the full stop off at the end of the message as that by itself indicates the end of the email. Type QUIT, [example session]("http://www.hobgoblinconsulting.com/hints/smtp.html").
 
I've just noticed though it appears that you're trying to send email from your yahoo account through your virgin media SMTP server. This may or may not work, it depends how strict their servers are. Unless you have the paid for service with yahoo I don't think you can send email via their SMTP servers. Assuming you are using virginmedia as your ISP you may have better luck sending the email from your virginmedia email address when using their SMTP server.
 
Note: With [Google email ]("http://mail.google.com/support/bin/answer.py?hl=en&answer=13287")you can use SMTP authentication to send email from a google email address using their servers and they use SSL. Plus they don't charge you unlike yahoo.

---

### Post by 1cookie on 2010-09-26
> **btindie said:**
>  Assuming you are using virginmedia as your ISP you may have better luck sending the email from your virginmedia email address when using their SMTP server.
 

That's the problem though, setting up my virginmedia smtp account. I phoned virginmedia and they don't support Linux, only Microsoft. It should work though, I've had it working on Linux Karmic before. I only have trouble with Lucid?

---

### Post by dukkieduk on 2010-09-26
Hi 1Cookie,

I had it working on server 9.04,
I upgraded to LTS 10.04 and since then my simple setup is no longer working.

I will try out some things, and post it here, please help me to make a summary at the end.

Greetz
D

---

### Post by btindie on 2010-09-26
> **1cookie said:**
> That's the problem though, setting up my virginmedia smtp account. I phoned virginmedia and they don't support Linux, only Microsoft. It should work though, I've had it working on Linux Karmic before. I only have trouble with Lucid?
 
I don't know who at virgin media told you that but if that's the case then they are talking out of their a**e. They may say they only *support* Microsoft but that doesn't mean it won't work with others - SMTP is a standard protocol.
 
Take a look at the [Virgin Media email settings ]("http://help.virginmedia.com/system/selfservice.controller?CONFIGURATION=1002&PARTITION_ID=1&TIMEZONE_OFFSET=&USERTYPE=&VM_CUSTOMER_TYPE=Cable&CMD=VIEW_ARTICLE&ARTICLE_ID=37928")page for 'Email *settings for addresses ending in @virginmedia.com*'.
 
The key things there are you need to enable SSL, connect port 465 and use authentication. This is a *submission* service and not your normal *smtp* service so you will have to modify your code to take this into account.
 
So going back to JohDut's original example, the key part of your code would look like:
```
$host = "ssl://smtp.virginmedia.com";
$port = "465";
$username = [EMAIL="my.username@virginmedia.com"]my.username@virginmedia.com[/EMAIL];
$password = "mypassword";
 
$smtp = Mail::factory('smtp',
    array ('host' => $host,
           'port' => $port,
           'auth' => true,
           'username' => $username,
           'password' => $password));
 
$mail = $smtp->send($to, $headers, $body);
```

---

### Post by karthick87 on 2010-09-26
> **JohDut said:**
> Or if you just want to send a mail through your/an existing smtp-server you could use php-mail.

First install:
sudo apt-get install php-mail php-net-smtp

And then your php code would look something like this:
```
<?php
require_once "Mail.php"; // this require is automatically fullfilled by the installed packages

$from = "Realname from <fromme@example.org>";
$to = "Sendto <sendto@example.org>";
$subject = "Test message ".date("d-m-Y / H:i");
$body = "Some text\n\n".date("d-m-Y / H:i");

$host = "192.168.1.100"; // Set IP or hostname of the smtp-server you want to use

$headers = array ('From' => $from,'To' => $to,'Subject' => $subject);
$smtp = Mail::factory('smtp',array ('host' => $host));
$mail = $smtp->send($to, $headers, $body);

if (PEAR::isError($mail)) {
echo("<p>" . $mail->getMessage() . "</p>");
} else {
echo("<p>Message sent succesfully ".date("d-m-Y / H:i")."</p>");
}
?>
```If you want you can also use an secure connection.
And if you need, you can also use authentication to the smtp-server.
The code would like this (you can use either independently of eachother)

```
<?php
require_once "Mail.php";

$from = "Realname from <fromme@example.org>";
$to = "Sendto <sendto@example.org>";
$subject = "Test message ".date("d-m-Y / H:i");
$body = "Some text\n\n".date("d-m-Y / H:i");

$host = "ssl://192.168.1.100"; // again set IP or hostname of the smtp-server you want to use. If your smtp-server is on IP 192.168.1.100 it would look like this
$port = "465";
$username = "username on SMTP-server"; // smtp username needed tot authenticate
$password = "password on SMTP-server"; // smtp password needed tot authenticate

$headers = array ('From' => $from,
'To' => $to,
'Subject' => $subject);
$smtp = Mail::factory('smtp',
array ('host' => $host,
'port' => $port,
'auth' => true,
'username' => $username,
'password' => $password));

$mail = $smtp->send($to, $headers, $body);

if (PEAR::isError($mail)) {
echo("<p>" . $mail->getMessage() . "</p>");
} else {
echo("<p>Message successfully sent!</p>");
}
?>
```

I have tried your second code and got the following error..
```

karthick@Ubuntu-desktop:~/Desktop$ php -q test2.php
PHP Warning:  require_once(Mail.php): failed to open stream: No such file or directory in /home/karthick/Desktop/test2.php on line 2
PHP Fatal error:  require_once(): Failed opening required 'Mail.php' (include_path='.:/usr/share/php:/usr/share/pear') in /home/karthick/Desktop/test2.php on line 2
```

---

### Post by 1cookie on 2010-09-26
> **btindie said:**
> 
 
The key things there are you need to enable SSL, connect port 465 and use authentication. This is a *submission* service and not your normal *smtp* service so you will have to modify your code to take this into account.
I've done all of these things..:)
 
> 
So going back to JohDut's original exampleUsing JonhDut's second example (with my settings included) i get the following:

```
Failed to connect to ssl://virginmedia.com:465 [SMTP: Failed to connect socket: Connection timed out (code: -1, response: )]
```I'm using the password that opens my webmail account, which Virgin media inform me is my email password. Similarly, my username is: [EMAIL="myusername@virginmedia.com"]myusername@virginmedia.com[/EMAIL]. (withheld to protect me from spam bots)

:)

---

### Post by btindie on 2010-09-26
> **getyourkarthick said:**
> I have tried your second code and got the following error..
```

karthick@Ubuntu-desktop:~/Desktop$ php -q test2.php
PHP Warning:  require_once(Mail.php): failed to open stream: No such file or directory in /home/karthick/Desktop/test2.php on line 2
PHP Fatal error:  require_once(): Failed opening required 'Mail.php' (include_path='.:/usr/share/php:/usr/share/pear') in /home/karthick/Desktop/test2.php on line 2
```
 
That means your system is missing the header files required by php-mail
 
```
sudo apt-get install php-mail php-net-smtp
```

---

### Post by btindie on 2010-09-26
> **1cookie said:**
> ```
Failed to connect to ssl://virginmedia.com:465 [SMTP: Failed to connect socket: Connection timed out (code: -1, response: )]
```
 
From that error it appears that you're trying to connect to the wrong host. It should be **smtp.virginmedia.com**
 
There's a useful program for testing smtp connections called [Swaks]("http://jetmore.org/john/code/swaks/"). It's available in the [Universe repository]("http://packages.ubuntu.com/lucid/swaks") but that seems a little out of date. It's easy enough to get the latest one as it's just a perl script. Make sure you have the required perl libraries installed ```
sudo apt-get install libnet-dns-perl libnet-ssleay-perl
```
Then download Swaks ```
sudo wget -O /usr/local/bin/swaks [http://jetmore.org/john/code/swaks/latest/swaks](http://jetmore.org/john/code/swaks/latest/swaks)
sudo chmod +x /usr/local/bin/swaks
```
You can then test it with
```
swaks --to [EMAIL="me@yahoo.com"]me@yahoo.com[/EMAIL] --from [EMAIL="my.username@virginmedia.com"]my.username@virginmedia.com[/EMAIL] --auth-user [EMAIL="my.username@virginmedia.com"]my.username@virginmedia.com[/EMAIL] --protocol SSMTPA --server smtp.virginmedia.com
```
If the above works then we know the connection details to the virginmedia smtp are correct, it's just then a case of figuring out what's wrong with your PHP code...

---

### Post by karthick87 on 2010-09-26
> **btindie said:**
> That means your system is missing the header files required by php-mail
 
```
sudo apt-get install php-mail php-net-smtp
```


Thanks a lot now it works :)

---

### Post by 1cookie on 2010-10-09
> **btindie said:**
> 

```
swaks --to [EMAIL="me@yahoo.com"]me@yahoo.com[/EMAIL] --from [EMAIL="my.username@virginmedia.com"]my.username@virginmedia.com[/EMAIL] --auth-user [EMAIL="my.username@virginmedia.com"]my.username@virginmedia.com[/EMAIL] --protocol SSMTPA --server smtp.virginmedia.com
```If the above works then we know the connection details to the virginmedia smtp are correct, it's just then a case of figuring out what's wrong with your PHP code...


hi btindie, after trying the above, i get:

```

=== Trying smtp.virginmedia.com:465...
*** Error connecting 0.0.0.0 to smtp.virginmedia.com:465:
***     IO::Socket::INET: Bad hostname 'smtp.virginmedia.com'



```so i guess there is a problem with my virgin media connection? VM inform me that my connection details are the same as my login, username/password i use to access my webmail..:)

---

### Post by t4thfavor on 2010-10-09
I use a copy of this form on my site, and had it working in no time. I don't know if it's required, but I have a working mail server on the webserver. I do however know that it does send CC's to outside email addresses just fine.
 
[http://green-beast.com/gbcf-v3/](http://green-beast.com/gbcf-v3/)

It's all php, and the source is pretty easy to follow. I found it easier to use than creating my own which I have also done in the past.

---

