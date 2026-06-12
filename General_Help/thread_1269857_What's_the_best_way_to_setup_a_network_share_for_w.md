---
title: "What's the best way to setup a network share for windows and ubuntu?"
date: 2009-09-18
forum: General Help
---

### Post by knottshawk on 2009-09-18
I have a small home network with 2 Vista machines and 1 Ubuntu 8.10 machine. I'd like to centrally locate all my files so all the systems can access them without the expense of a NAS. I was thinking of attaching a large external HDD to my Ubuntu box and sharing it with the Vista machines. Is this even possible? In my preliminary tests (using a simple flash drive) Vista was unable to connect.

Is there a better way? I can get an external HDD cheap, but I'm open to other options.

---

### Post by UndeniablyRexer on 2009-09-18
Samba server
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by knottshawk on 2009-09-18
I've got samba setup... that's how I shared out my flash drive, but Vista won't connect to it...I've got a separate thread going regarding Vista connection issues, but are you implying that it IS possible to share a USB attached hard drive via Samba to a Vista box?

---

### Post by UndeniablyRexer on 2009-09-18
Yea, you just have to add it as a shared folder, or I believe you might be able to mount it in an already shared folder.

The only experience I have with samba is through Webmin.  It provides a good GUI to set up samba, as well as a lot of other sever monitoring/configuring tools.

---

### Post by knottshawk on 2009-09-19
Well, I've currently got it all setup that way and my other systems can't seem to connect. Anything specific in the Samba server settings I should be changing (not on the specific share)...

---

