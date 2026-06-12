---
title: "PHP Error logging in Ubuntu 10.10"
date: 2010-11-19
forum: General Help
---

### Post by cearlp on 2010-11-19
I need help to turn on error logging for PHP errors in Ubuntu 10.10 with PHP5 installed.
I modified php.ini to turn on all error logging that seems appropriate for my purposes but I can't find any of the specified log files.
What am I doing wrong?

---

### Post by mellis95 on 2010-11-19
Look for the following in php.ini:

```
; Log errors to specified file. PHP's default behavior is to leave this value
; empty.
; http://php.net/error-log
; Example:
;error_log = php_errors.log
; Log errors to syslog (Event Log on NT, not valid in Windows 95).
;error_log = syslog

```

I have not used this, but it seems that you just uncomment the error_log directive and set that to the path you would like your logs to go to.

matt

---

### Post by SeijiSensei on 2010-11-19
By default, PHP logs to /var/log/apache2/error.log.  Did you look there?

---

### Post by cearlp on 2010-11-20
Already changed the ini file to specify a specific location. I specified /var/log/php_errors.log but nothing was generated. SeijiSensei's suggestion to look in the error.log in /var/log/apache2 did show somethings but I need help in interpreting them. They are:

[Sat Nov 20 12:36:25 2010] [error] [client 192.168.1.115] PHP Warning:  mail(/var/log/mail.log) [<a href='function.mail'>function.mail</a>]: failed to open stream: Permission denied in /var/www/mail-comments.php on line 27, referer: [http://192.168.1.115/comments.html](http://192.168.1.115/comments.html) 
sh: /usr/sbin/sendmail: not found 
[Sat Nov 20 12:36:25 2010] [error] [client 192.168.1.115] File does not exist: /var/www/favicon.ico 

/var/log/mail.log is empty. Is this because permission was denied to open a stream to it?
Line 27 of mail-comments.php is simply a call to mail as follows:

if (maIl($to, $subject, $message, $header)) {
  header( "Location: reply-comments.html" );
} else {
  echo "sending of Email Failed";
}

What is file favicon.ico and what is trying to access it?

---

### Post by SeijiSensei on 2010-11-22
> **cearlp said:**
> [Sat Nov 20 12:36:25 2010] [error] [client 192.168.1.115] PHP Warning:  mail(/var/log/mail.log) [<a href='function.mail'>function.mail</a>]: failed to open stream: Permission denied in /var/www/mail-comments.php on line 27, referer: [http://192.168.1.115/comments.html](http://192.168.1.115/comments.html) 
sh: /usr/sbin/sendmail: not found 

You probably don't have a "mail transfer agent" like Postfix or sendmail installed.  Use "sudo apt-get install postfix".

> [Sat Nov 20 12:36:25 2010] [error] [client 192.168.1.115] File does not exist: /var/www/favicon.ico 

favicon.ico is the little icon that appears next to a website address in the browser.  It's automatically requested by default by most modern browsers.  If you want to get rid of the errors, you can just create an empty file in the website directory like this:

```
sudo touch /var/www/favicon.ico
```

That will create an empty file that will satisfy the browsers and stop the errors from appearing in the logs.

If you want to create an icon for your site, a little searching will bring up some methods to do this in Linux.

---

### Post by sprosty on 2011-03-02
If you want php error logs showing up in a separate file from:

/var/log/apache2/error.log

You can set error_log to a directory that www-data has access to OR change permissions/ownership in /var/log so that it can write to the file there. 

So if you want to call this file "php.log" then you can set error log as 

[PHP]error_log = /var/www/php.log[/PHP]This will have the file show up in your web root folder (you shouldn't need to change any permissions or ownerships this way).

If you'd rather have the log file show up in your /var/log directory then change error_log to: 

[PHP]error_log = /var/log/php.log[/PHP]I had to create an empty /var/log/php.log file first (use vi or emacs). Then I had to set the owner of the file to www-data. 

I prefer log files in /var/log since they do not share the same partition as /var/www (under my partition scheme). 

For full disclosure, if having www-data rw access to the /var/log/php.log file creates some kind of security threat, I don't know about it.  

As an additional note, apache apparently has the permissions to write to /var/log/apache2 files, but for some reason if you want php to write to a specific file inside /var/log/apache2 or /var/log via apache, it can not write to it (so probably using www-data thread as oppposed to root thread?). 

So there may be a better way to do it than I did, but there you go.

---

### Post by chupnik on 2012-09-07
This workaround may help you
[http://ubuntuforums.org/showthread.php?p=12224765#post12224765](http://ubuntuforums.org/showthread.php?p=12224765#post12224765)

---

### Post by overdrank on 2012-09-07
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

