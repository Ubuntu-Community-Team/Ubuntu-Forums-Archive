---
title: "Ubuntu Server with postfix and RT"
date: 2011-03-14
forum: General Help
---

### Post by abducted47 on 2011-03-14
Hello all,
I do apologise if this is not in the appropriate section. 
I have a few questions concerning Ubuntu Server, postfix and request tracker.

After many hours and attempts I have managed to install postfix and request tracker on my ubuntu server.

My problems/questions are:
Does postfix send and receive email? Because I can send and email via postfix to RT but I dont get the auto reply message from RT.
If it does do both (send/receive) how can I know that the problem is a postfix configuration or a RT one?

If does not do both should I install something like sendmail?Because when I tried to install it through the Synaptic Package manager it wanted to uninstall postfix.

It's an ubuntu server 10.04 with apache mysql and gnome desktop. RT is version 3.8.

Thank you very much and any help on this matter will be much appreciated.
Kind Regards :D

---

### Post by abducted47 on 2011-03-15
Anyone got any ideas ?
Thank you

---

### Post by rbishop on 2011-03-15
How did you initially setup your server?  What were the base packages you setup? 

LAMP
SSH Server
Mail Server

Sometimes when you install Mail Server it doesn't want to work right, at least in my experience.  I have always started with a default install with the only thing installed was the SSH Server.  After that I updated the system, rebooted, and then went on to install all of my additional packages that I needed.

---

### Post by abducted47 on 2011-03-15
Thank you for the reply.
I certainly installed LAMP.
Is there a way finding out which other packages i have installed?

Cheers

---

