---
title: "trying to send email from php"
date: 2010-06-12
forum: General Help
---

### Post by rhythmiccycle on 2010-06-12
I'm hosting a website from my pc.

LAMP is installed, and php and mysql is running fine.


i want the web site to send automated e-mails

i found the code

mail($to,$subject,$message,$headers);

but its not working.

I'm pretty sure i need to configure the php.ini file, but the problem is I have 2 php.ini files, and I dont know what one to change, or why I have 2

the two files with path are :


/etc/php5/apache2/php.ini
/etc/php5/cli/php.ini


why is there two?
what one do I need to change?

(i have other questions, but first things first)

---

### Post by rhythmiccycle on 2010-06-16
I had all kinds of issues with the mail() function,

But I found PEAR as a simpler way to achieve what I'm going for

I posted what I did here

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9468939#post9468939](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9468939#post9468939)

---

