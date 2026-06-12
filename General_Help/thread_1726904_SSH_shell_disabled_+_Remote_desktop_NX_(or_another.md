---
title: "SSH shell disabled + Remote desktop NX (or another remote desktop software)"
date: 2011-04-11
forum: General Help
---

### Post by zoltan32 on 2011-04-11
Hi,

I'm French so excuse my English :)

I installed the remote desktop NX on ubuntu server 10.04 and for security reasons I disabled copy and paste from server to client.
The NX users are connecting with NX client perfectly and copy and paste restriction works also great.

NX works with accounts with ssh access so the users can also use their accounts to connect to server with ssh clients like putty or openssh.
The problem is copy and paste is enabled from server to client on these ssh shells.
I tried to disable the user shells like this : usermod -s /bin/false username
After that, the access with ssh clients is forbidden but the nx connection doesn't work anymore, I have this error message : "Authentication failed".
To retrieve nx connection, I did : usermod -s /bin/bash username
I also tried the same thing with another software : X2GO, and I have the same troubles.

So I'd like to know if it's possible to disable ssh shell and use nx remote desktop (or another remote desktop) at the same time.

Thanks, best regards.

---

### Post by bodhi.zazen on 2011-04-11
You can probably do this with what are called forced commands.

Edit the FreeNX keys (which I believe are ssh keys) and add options you with to disable (no-pty for example)

[http://binblog.info/2008/10/20/openssh-going-flexible-with-forced-commands/](http://binblog.info/2008/10/20/openssh-going-flexible-with-forced-commands/)

I use "no-port-forwarding,no-X11-forwarding,no-pty" with some regularity. Not sure how many of those options you can use, no-pty would be a good start.

---

### Post by zoltan32 on 2011-04-12
I'm going to test your solution. Thank you very much :)

---

