---
title: "Creating an image of an ubuntu server"
date: 2010-09-28
forum: General Help
---

### Post by mrwooster on 2010-09-28
I want to move development from my existing VPS provider to EC2.  My VPS provider does not have any current facility to create a disk image, therefore I was wondering if it was possible to do so using linux software.  The main purpose of the disk image would be to restore my existing VPS if EC2 doesnt work out.

Thanks

---

### Post by linux-hack on 2010-09-28
did you try clonezila ?

---

### Post by mrwooster on 2010-09-28
Ah, that looks just like what I need.

Many thanks

---

### Post by linux-hack on 2010-09-28
Your welcome ;)

---

### Post by JedMeister on 2010-09-28
Depending on your usage scenario, I've found [RemasterSys]("http://www.geekconnection.org/remastersys/") useful too. 

It's not really an imaging tool but I've found in some circumstance its actually more useful than Clonezilla (like migration of OS to new hardware). In that situation Clonzilla can be a bit temperamental if you don't create same partition layout.

---

### Post by linux-hack on 2010-09-28
RemasterSys is making a live distro from you installed system . Or you can do a full backup. Not the same thing but can do ALMOST the same job :D

---

