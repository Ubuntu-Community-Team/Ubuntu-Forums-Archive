---
title: "FTP hanging on LS command"
date: 2011-01-01
forum: General Help
---

### Post by griffen on 2011-01-01
Hi there,

Using the latest version of Ubuntu. Trying to ftp to an ftp server. Able to successfully login through terminal but when I try and list the contents of a folder I get "200 PORT command successful" and then it just hangs. I thought it might be the server but I've tried it on different Mac and Windows machines and was successful. I can only assume there's something in Ubuntu which is blocking it. Does anyone know what the cause might be?

Thanks and of course Happy New Year!

---

### Post by perspectoff on 2011-01-01
I'm using FileZilla from (K)Ubuntu routinely and have no problems, as long as my firewall allows port 21.

Naturally, all the other settings must be correct.

---

### Post by dcstar on 2011-01-02
> **griffen said:**
> Hi there,

Using the latest version of Ubuntu. Trying to ftp to an ftp server. Able to successfully login through terminal but when I try and list the contents of a folder I get "200 PORT command successful" and then it just hangs. I thought it might be the server but I've tried it on different Mac and Windows machines and was successful. I can only assume there's something in Ubuntu which is blocking it. Does anyone know what the cause might be?

Thanks and of course Happy New Year!

Maybe, try PASV mode:

[http://slacksite.com/other/ftp.html](http://slacksite.com/other/ftp.html)

---

### Post by griffen on 2011-01-04
dcstar right on the money. Thanks for your help. It's quite frustrating that it was something so small and at the same time a relief :) Oh well :guitar:

---

