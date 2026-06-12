---
title: "Order in which things start [SAMBA &amp; CUPS in particular]"
date: 2011-06-23
forum: General Help
---

### Post by Sorky on 2011-06-23
After many expletives and much hair pulling, I am now able to reliably get Ubuntu Server started [with a xubuntu desktop] that provides file and print sharing to a Windows XP client in a VM... With ONE CATCH!

Initially on a restart the VM will see the file shares but NOT the shared printer.

All I do then is run "sudo restart smbd" in a terminal window and the printer becomes visible! [Running "smbclient -L <server> -N" before and after the restart shows the difference without the need to launch the VM of Windows]

My guess is that the CUPS starts after SAMBA and hence the printer was not advertised - My assumption is that by getting CUPS to start before SAMBA, the problem will be solved.

So my questions are...

1) How do I make CUPS start sooner [note: I'm a noob!]

2) Who do I send this observation to so as to get it avoided by default so as to ave others some hair!

---

### Post by dragonfly41 on 2011-06-23
Not sure .. but try reading here for sequence of services ..  

[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

/etc/init.d/README

/etc/rc?.d/README

and ..

sudo man service

---

### Post by Sorky on 2011-06-23
> **dragonfly41 said:**
> ... try ... 
 
 
Thanks for the hints - I'll post an update once I've investigated ;-)

---

### Post by Sorky on 2011-06-25
Doesn't seem to be started in rc... looks like cups, nmbd and smbd are both in /etc/init

I'm going to take a stab at adding "and started cups" in the start condition for smbd - will advise on success/failure soon!

---

### Post by Sorky on 2011-06-30
Success!!! 

As I said previously, running "smbclient -L <server_name> -N" at startup did not show the printer and my guess regarding timing was correct. Making sure CUPS had started BEFORE the SNMB daemon ran was the key.

Such a simple solution in the end... 

edit /etc/init/smbd.conf
change "start on local-filesystems" -> "start on (local-filesystems and started cups)"

---

