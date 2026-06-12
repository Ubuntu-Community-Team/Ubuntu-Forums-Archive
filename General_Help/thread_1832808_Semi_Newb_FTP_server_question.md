---
title: "Semi Newb FTP server question"
date: 2011-08-25
forum: General Help
---

### Post by The_Flaz on 2011-08-25
Hi,
 
I have a Ubuntu machine that I would like to set up as an FTP server.
 
I would like to be able to give my friends login details like web url, username and password and allow them to upload files over their internet browser to my machine. They are all windows users.
 
Is this possible and are there any useful guides that would help me? I have had a google and can see something called vsftp but it doesn't seem to talk about outside users connecting
 
Hope this question makes sense 
 
Cheer and thanks for any help

---

### Post by lmarmisa on 2011-08-25
Welcome to the forums.

Your friends will use ftp clients. The standard browsers (Firefox, Google Chrome, IE) support the ftp client function. So, I think that the user manual is not needed.

I recommend to you to use  [a dynamic DNS service]("http://en.wikipedia.org/wiki/Dynamic_DNS"). This service allows you to define a hostname for  your ftp server accessible from the internet. These two DynDNS providers offer free services:

[http://dyn.com/dns/dyndns-free/](http://dyn.com/dns/dyndns-free/)

[https://www.no-ip.com/](https://www.no-ip.com/)

So, the user manual is very simple:

URL: [ftp://yourftpserverhostname](ftp://yourftpserverhostname)

user: xxxxx

password: yyyyy

I hope that this information could help you.

Best regards,

Luis

---

