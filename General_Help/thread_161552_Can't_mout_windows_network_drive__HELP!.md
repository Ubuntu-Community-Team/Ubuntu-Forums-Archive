---
title: "Can't mout windows network drive  HELP!"
date: 2006-04-17
forum: General Help
---

### Post by Magiczero on 2006-04-17
Hey

I am unable to get into my windows network to mount the drive.  I was messing around the other day and I must have installed a samba network thing and now when I click on the windows network it asks me for my Samba Username & password & I dont even use samba I use windows network but i cant get into it to remount the drive.  Can anyone tell what I did & how I can fix it? 

thanks

---

### Post by Qrk on 2006-04-17
I am confused by your question. How exactly did you connect to a windows network without samba? I could be wrong, but I am not aware of any method to connect to a windows machine besides Samba except CUPS (limited to printing.) 

Also, by "the drive," what exactly do you mean? I'll assume this is a windows machine and/or an external hardrive accessible through a windows machine. 

I think you already had Samba installed. Your problem is that its now asking you for a password. This is probably due to the machine you are connecting to. All you should need to do is use a user name and password that are valid on that machine.

---

### Post by Magiczero on 2006-04-17
hi

the computer I am trying to access is a MCE PC with file and print sharing turned on.  How do I make samba work so I can access my network?  

Thanks

---

### Post by krismatth3 on 2006-04-17
Qrk: you are correct. samba is an implementation of windows file sharing, SMB/CIFS.

---

### Post by Qrk on 2006-04-17
If its asking you for a password, it may already be working. You should be able to use your MCE user account and password. For more information, try the wiki:

[https://wiki.ubuntu.com/SettingUpSamba](https://wiki.ubuntu.com/SettingUpSamba)

---

### Post by Magiczero on 2006-04-17
it works now!

---

