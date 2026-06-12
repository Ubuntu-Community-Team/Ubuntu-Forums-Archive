---
title: "Mounting a SAN to Ubuntu"
date: 2010-02-10
forum: General Help
---

### Post by gungadin on 2010-02-10
Hi,
 
I am a rather new user of Linux. I created a SAN using openfiler on another machine and I can mount that SAN in Windows. I would also like to mount the SAN in Ubuntu but I have no idea how to start? I have found some sites that try to do this but it fails. Can someone set me on the right path to go about this? I just want my Ubutu to have access to the data on the SAN, I don't want to boot from it or anything like that. The SAN was formatted in Windows 2003. Not sure if that matters.
 
Thanks
Jim

---

### Post by bogdan.veringioiu on 2010-02-10
Hi.
Not sure that I can help you, but please provide more info:
-what kind of volume did you export (iscsi lun, smb share)?
-how did you mount it under windows?
Cheers.
Bogdan

---

### Post by gungadin on 2010-02-10
I mounted it under windows using ISCSI as a lun. Using Microsofts ISCSI initiator, then under windows drive management I partioned the drive and formated it. I gave it a drive letter and I could copy and delete files off it. I did not use any special encryption or password protection on the SAN. 
 
From what I could find, I may have to edit a stab file with target info. I had problems with mounting it after many many clicks.

---

### Post by bogdan.veringioiu on 2010-02-11
Hi.
Did you try following these tutorials:
> [http://www.cyberciti.biz/faq/howto-setup-debian-ubuntu-linux-iscsi-initiator/](http://www.cyberciti.biz/faq/howto-setup-debian-ubuntu-linux-iscsi-initiator/)
[http://www.howtoforge.com/using-iscsi-on-ubuntu-9.04-initiator-and-target](http://www.howtoforge.com/using-iscsi-on-ubuntu-9.04-initiator-and-target)
Did you discover the lun?
Are there any errors?
Bogdan

---

