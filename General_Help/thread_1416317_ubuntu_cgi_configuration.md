---
title: "ubuntu cgi configuration"
date: 2010-02-25
forum: General Help
---

### Post by casperdaghost on 2010-02-25
I installed apache2 on ubuntu to test webpages offline. 
When I try to browse this page on firefox   - I get an internal server error.

[http://127.0.0.1/cgi-bin/form1.cgi](http://127.0.0.1/cgi-bin/form1.cgi)

Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.
Please contact the server administrator, webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.
More information about this error may be available in the server error log.


But when I browse to the local file to the page with this 

file:///home/casper/public_html/cgi-bin/form1.cgi

The file looks fine. 

However, when I try to post to the form, after hitting enter, the same internal server error comes up:

Internal Server Error

Here is the header to form1.cgi. 

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.or
g/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="content-type" content="text/html; charset=iso-8859-1" />
<title>HTML Form Elements</title>
</head>
<body>
print "Content-type: text/html\n\n";

<form action="http://127.0.0.1/cgi-bin/form1.cgi" method="post">

---

### Post by casperdaghost on 2010-02-25
In the sites-available directory I created a new site - baremetalhost and here is the config file for it:

casper@casper-laptop:/etc/apache2/sites-available$ pwd
/etc/apache2/sites-available

casper@casper-laptop:/etc/apache2/sites-available$ ls
baremetalhost  default  default-ssl

casper@casper-laptop:/etc/apache2/sites-available$ more baremetalhost
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    
    DocumentRoot /home/casper/public_html
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /home/casper/public_html>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>

    ScriptAlias /cgi-bin/ "/home/casper/public_html/cgi-bin/"
    <Directory "/home/casper/public_html/cgi-bin/">
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
casper@casper-laptop:/etc/apache2/sites-available$

---

### Post by casperdaghost on 2010-02-26
casper@casper-laptop:/var/log/apache2$ pwd
/var/log/apache2

[Fri Feb 26 00:14:28 2010] [error] [client 127.0.0.1] Premature end of script headers: form1.cgi
[Fri Feb 26 00:14:42 2010] [error] (8)Exec format error: exec of '/home/casper/public_html/cgi-bin/form3.cgi' failed
[Fri Feb 26 00:14:42 2010] [error] [client 127.0.0.1] Premature end of script headers: form1.cgi
[Fri Feb 26 00:22:02 2010] [error] (8)Exec format error: exec of '/home/casper/public_html/cgi-bin/form3.cgi' failed
[Fri Feb 26 00:22:02 2010] [error] [client 127.0.0.1] Premature end of script headers: form1.cgi
[Fri Feb 26 00:22:33 2010] [error] (8)Exec format error: exec of '/home/casper/public_html/cgi-bin/form3.cgi' failed
[Fri Feb 26 00:22:33 2010] [error] [client 127.0.0.1] Premature end of script headers: form1.cgi
[Fri Feb 26 00:22:36 2010] [error] (8)Exec format error: exec of '/home/casper/public_html/cgi-bin/form1.cgi' failed
[Fri Feb 26 00:22:36 2010] [error] [client 127.0.0.1] Premature end of script headers: form1.cgi

---

### Post by gmargo on 2010-02-26
> **casperdaghost said:**
> 
Here is the header to form1.cgi. 

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.or
g/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="content-type" content="text/html; charset=iso-8859-1" />
<title>HTML Form Elements</title>
</head>
<body>
print "Content-type: text/html\n\n";

<form action="http://127.0.0.1/cgi-bin/form1.cgi" method="post">

What content is that?  You say it's "the header to form1.cgi" but that's unclear.  Is this the content of the form1.cgi file or is it the output from the execution of form1.cgi?  It is obviously not a valid cgi nor valid html in either case.

---

### Post by casperdaghost on 2010-02-26
the above is the first ten lines of code from the cgi script that i am trying to open

---

### Post by gmargo on 2010-02-26
> **casperdaghost said:**
> the above is the first ten lines of code from the cgi script that i am trying to open

It is not a valid cgi script.  It seems to be perl based, so debug it by running it from the command line.  Edit - test - repeat.

---

