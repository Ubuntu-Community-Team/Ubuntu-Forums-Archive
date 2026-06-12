---
title: "is a proxy service what do I need?"
date: 2011-05-16
forum: General Help
---

### Post by ilpat on 2011-05-16
dear all,
I'm not sure this is the right place to post the following question.
I have two desktops: 
desktop O (ubuntu 10.10 64) at my office (static IP)
desktop H (ubuntu 10.10 64) at home (Internet connected via commercial ISP, dynamic IP)
desktop H connection to desktop O, runs out of the box, via ssh.

desktop O can accesses to some network services such as intranet, ftp, and restricted remote address. The question is:

how can I take advantage of network services from desktop H?

my first guess is to install a proxy service in desktop O. However, as you may understand, I'm not familiar with networking stuffs.

Any suggestion will be appreciated. Thanks in advance,

p

---

### Post by seawolf167 on 2011-05-16
What you are looking for is Tunneling via ssh.

A very quick google search gave [this example ]("http://www.revsys.com/writings/quicktips/ssh-tunnel.html")you can read.

---

### Post by Kidfork on 2011-05-16
[http://unixgeeks.org/security/newbie/unix/ftp.html](http://unixgeeks.org/security/newbie/unix/ftp.html)

---

### Post by ilpat on 2011-05-16
> **seawolf167 said:**
> What you are looking for is Tunneling via ssh.

A very quick google search gave [this example ]("http://www.revsys.com/writings/quicktips/ssh-tunnel.html")you can read.

thank [seawolf167]("http://ubuntuforums.org/member.php?u=1042634") for your quick reply.
ssh tunneling is probably what I need. I can use basic ssh connection of the type:

local-desk@user:~$ ssh my-remote-desk

suppose I wish to surf the web from my home machine but using the remote ip what should I do? 

my guess is something like

ssh -f user@my-remote-server -L portA:my-remote-server: portB -N

where portA[FONT=Verdana], and [/FONT]portB are specifics port of client and server respectively.
is that correct?

cheers,

P

---

