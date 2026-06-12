---
title: "User permissions"
date: 2009-11-25
forum: General Help
---

### Post by NaBzOr on 2009-11-25
Hey! I've installed Ubuntu for the first time today. Now i'm having trouble with with permissions. I wonder how i can set my userpermissions to "admin" or "full" or whatever Ubuntu uses.

Thanks

<3 NaBzOr

---

### Post by audiomick on 2009-11-25
What do you need that for?
If you try and do anything (with the onboard tools at least ) that needs root privileges ( that is what it is in Ubuntu ), you will get asked for your password. 
This is a good thing, it means you are heading into territory where you can break your system. 
The password is the one you use to log on. Think about it carefully, and if you aren't sure about what you are doing, bail out and go and do some research.

You do not want to have permanent root priviliges in Ubuntu. There is nothing that doesn't work right if you aren't the administrator, unlike windows. Not being root means you can't accidently break your system, and is one of the things that makes linux so virus resistant.

---

### Post by lyall on 2009-11-25
search the web for "linux permissions"
also check out the following link [http://www.psychocats.net/ubuntu/index]("http://www.psychocats.net/ubuntu/index")

have fun reading and learning:)

---

### Post by oldos2er on 2009-11-25
> **NaBzOr said:**
> Hey! I've installed Ubuntu for the first time today. Now i'm having trouble with with permissions. I wonder how i can set my userpermissions to "admin" or "full" or whatever Ubuntu uses.


 It's the policy on these forums not to give info that would subvert Ubuntu's security model. You might want to read [http://psychocats.net/ubuntu/security](http://psychocats.net/ubuntu/security)

---

### Post by NaBzOr on 2009-11-26
Thanks for the replies guys.

I'll be more specific: I need to activate my second monitor. I use nVIDIA X-server to configure all this. The problem is, when i try to save the settings, i get this message:
[IMG]http://www.nabzor.com/Bilder/x-server.png[/IMG]

I tried to create the file myself, but was denied, and i needed the right permissions.

---

### Post by akakingess on 2009-11-26
You should be able to just use "sudo" in order to accomplish those tasks, even if it's just gksudo nautilus so that you can create a folder within the filesystem (still not recommended unless you are sure you know what you are doing.

---

### Post by NaBzOr on 2009-11-26
> **akakingess said:**
> You should be able to just use "sudo" in order to accomplish those tasks, even if it's just gksudo nautilus so that you can create a folder within the filesystem (still not recommended unless you are sure you know what you are doing.
I did this just now, but then i got a new errormessage: Unable to remove old X config backup file.

---

### Post by oldos2er on 2009-11-26
If you already have a file /etc/X11/xorg.conf.backup, rename it to something else
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf.backup.1
``` then delete the first file ```
sudo rm /etc/X11/xorg.conf.backup
```
Now run ```
gksu nvidia-settings 
``` and you should be able to save your configuration.

---

### Post by NaBzOr on 2009-11-26
Worked perfectly! Thanks a lot:D

---

