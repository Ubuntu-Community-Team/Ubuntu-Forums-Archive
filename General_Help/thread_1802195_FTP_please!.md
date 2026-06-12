---
title: "FTP please!"
date: 2011-07-11
forum: General Help
---

### Post by unbuntunewb on 2011-07-11
Hello,

I would like to set up an FTP server that I can remotely connect to when needed. I have tried vsftpd and proftpd but cannot figure them out. Can anyone give me the blow by blow for a complete ftp newb? I would ideally like to have it be secure but I think baby steps are in order. I just want to be able to connect to my home computer from my laptop (or anyones computer I guess) when I am away from home.

Please help this has been bothering me for some time. I have a dyndns account, I dont know if that helps.

Thanks.

edit: I thought I should mention I plan on using filezilla to connect to my server. I would prefer a graphical approach.

---

### Post by wildmanne39 on 2011-07-11
> **unbuntunewb said:**
> Hello,

I would like to set up an FTP server that I can remotely connect to when needed. I have tried vsftpd and proftpd but cannot figure them out. Can anyone give me the blow by blow for a complete ftp newb? I would ideally like to have it be secure but I think baby steps are in order. I just want to be able to connect to my home computer from my laptop (or anyones computer I guess) when I am away from home.

Please help this has been bothering me for some time. I have a dyndns account, I dont know if that helps.

Thanks.

edit: I thought I should mention I plan on using filezilla to connect to my server. I would prefer a graphical approach.
Hi, here is a link with step by step instructions.
[https://help.ubuntu.com/11.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/11.04/serverguide/C/ftp-server.html)

---

### Post by unbuntunewb on 2011-07-11
I read that earlier, unless I am reading it wrong it does not say how to connect to the server remotely using filezilla or something similar, I dont know what port to use, or is default, or what the server name is etc.

---

### Post by mikejonesey on 2011-07-11
ssh is easyer to setup, faster and you can connect using the sftp protocol with it...

to connect to your laptop at home from anywhere though there is more to think about ie networking solutions...

the easiest and fastest way for you to do this is using some 3rd party service, (some are free and cross platform compatible...)

Iv'e used various solutions like these and they are ok for the job when you are away... i'd just prefer ssh...

you can find some free ones here;

[http://en.wikipedia.org/wiki/Comparison_of_remote_desktop_software](http://en.wikipedia.org/wiki/Comparison_of_remote_desktop_software)

---

### Post by Dangertux on 2011-07-11
SSH is also considerably more secure, you really should consider it.

---

