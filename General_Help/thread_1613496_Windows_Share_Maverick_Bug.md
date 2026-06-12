---
title: "Windows Share Maverick Bug"
date: 2010-11-04
forum: General Help
---

### Post by jeruzzzzzzzz on 2010-11-04
Hello, 

I installed Maverick recently. I used to access a server with Windows Share, and be able to see and copy files onto this server (Windows 2003). I still can with older version of Ubuntu but can't copy large binary files anymore on the server...

Anybody with this bug?

---

### Post by CharlesA on 2010-11-04
You'd need to post more info if you want any help.

---

### Post by jeruzzzzzzzz on 2010-11-05
Well the point is that there is no much information. If I try to copy a text file, no problem. Now if I try, let's say jo.pdf, I get the following popup:
[B]
Error while copying "jo.pdf"

There was an error copying the file into smp://xxx.xxx.xx.x/folder/[/B] 

"**Show more details**" only yields "**Invalid argument**"


Note that the bug doesn't exist with later version of Windows Server (post 2003)...

That's all I have :-(

---

### Post by CharlesA on 2010-11-05
It doesn't look like it's a bug with Windows.

See here: [https://bugs.launchpad.net/autofs/+bug/393012](https://bugs.launchpad.net/autofs/+bug/393012)

---

### Post by jeruzzzzzzzz on 2010-11-05
Hum that seems really similar indeed. However, it does work with Lucid Lynx :-/

---

### Post by CharlesA on 2010-11-05
According to the bug report, it has something to do with smbclient in Maverick. *shrug*

I haven't experienced the problems, but my network is set up differently, since I don't have a box running Server 2K3.

---

### Post by jeruzzzzzzzz on 2010-11-05
alright at least I am not the only one. Hopefully it will get fixed fast. Thanks for the help.

---

