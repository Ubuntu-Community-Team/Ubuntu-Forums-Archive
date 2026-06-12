---
title: "PHP5 installation problem"
date: 2011-06-05
forum: General Help
---

### Post by hatalar205 on 2011-06-05
Hi.
I installed Apache 2 server and Php5 on my netbook. I created a HTML and PHP page on the folder /war/www. When I try to browse the pages on the Chromium Browser I can see the HTML page but I can't see the PHP page. Browser gives this error message;
```
The website encountered an error while retrieving http://localhost/test.php. It may be down for maintenance or configured incorrectly.
```
I think I did something wrong during the installation process of PHP5. Help please.
Thanks in advance.

---

### Post by pqwoerituytrueiwoq on 2011-06-05
does a html file work?
if not 
sudo service apache2 start

---

### Post by hatalar205 on 2011-06-05
> **pqwoerituytrueiwoq said:**
> does a html file work?
if not 
sudo service apache2 start

Html file work well. But, php file doesn't work.:(

---

### Post by pqwoerituytrueiwoq on 2011-06-05
post the content of the php file here
i will find the typo

---

### Post by hatalar205 on 2011-06-05
> **pqwoerituytrueiwoq said:**
> post the content of the php file here
i will find the typo

Here it is. A test page;
> <html>
<head>
<title>PHP Test</title>
</head>
<body>
<p>This is an HTML line
<?php
echo “<p>This is a PHP line</p>”;
phpinfo();
?>
</body>
</html>

---

### Post by SeijiSensei on 2011-06-05
As always, logs should be your first resource for troubleshooting.  What does /var/log/apache2/error.log show when you try and open the PHP file?

---

### Post by hatalar205 on 2011-06-05
> **SeijiSensei said:**
> As always, logs should be your first resource for troubleshooting.  What does /var/log/apache2/error.log show when you try and open the PHP file?

It is here. 
```
[Sun Jun 05 17:24:32 2011] [error] [client 127.0.0.1] PHP Warning:  Unknown: failed to open stream: Permission denied in Unknown on line 0
[Sun Jun 05 17:24:32 2011] [error] [client 127.0.0.1] PHP Fatal error:  Unknown: Failed opening required '/var/www/test.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

```

---

### Post by pqwoerituytrueiwoq on 2011-06-05
Parse error: syntax error, unexpected '>' in /var/www/test.php on line 8 
seems the lines yuo pasted had the wrong double quote character

[FONT=Courier New]gksudo gedit /etc/php5/apache2/php.ini[/FONT]
go down to line 531
this line should be at or near it
[FONT=Courier New]display_errors = Off[/FONT]
turn [FONT=Courier New]Off[/FONT] to [FONT=Courier New]On
[/FONT]
that will make it show errors in the browser

---

### Post by hatalar205 on 2011-06-05
I did what you said.

Here is what browser says;
> Server error
The website encountered an error while retrieving [http://localhost/test.php](http://localhost/test.php). It may be down for maintenance or configured incorrectly.
Here are some suggestions:
Reload this web page later.
**HTTP Error 500 (Internal Server Error): An unexpected condition was encountered while the server was attempting to fulfill the request.**

---

### Post by pqwoerituytrueiwoq on 2011-06-05
make sure the user [FONT=Courier New]www-data[/FONT] has permission to read the php script

---

### Post by hatalar205 on 2011-06-05
> **pqwoerituytrueiwoq said:**
> make sure the user [FONT=Courier New]www-data[/FONT] has permission to read the php script

Yes, it is. I changed the permissions and it works well now. Wow! It works. 
Thanks.
Thanks.
Thanks.
Thanks. :guitar:

---

### Post by cpetercarter on 2011-06-05
[PHP]echo “<p>This is a PHP line</p>”;[/PHP] is wrong. It should be [PHP]echo "<p>This is a PHP line</p>";[/PHP] Notice the different types of quotation marks. My guess is that you used a word processor to compose the script - these often replace plain quotation marks with opening and closing quotes, which is very clever but a complete disaster if you are trying to write code. Always use a text editor like gedit for tasks like this.

---

