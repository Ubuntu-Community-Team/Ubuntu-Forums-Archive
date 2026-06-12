---
title: "vsftpd question?"
date: 2009-07-16
forum: General Help
---

### Post by note32 on 2009-07-16
ok so heres the story:

                my brother: aw man i hate coming all the way downstairs to get stuff from you i wish there was a way i could just download it.

                        me: THERE IS A WAY!

                my brother: REALLY!?!?!?!?:o
 
                        me: YES! with an FTP server! Running on ubuntu 9.04 with vsftpd:biggrin:


 anyway so i set it up and everything and it works just fine. BUT! when you login to the server it shows everything of mine my photos music movies ect.... pretty much everything in my home folder i just want there to be one "shareing folder" for me and my bro

---

### Post by note32 on 2009-07-16
so i set it up and everything and it works just fine. BUT! when you login to the server it shows everything of mine my photos music movies ect.... pretty much everything in my home folder i just want there to be one "shareing folder" for me and my bro

---

### Post by RealG187 on 2009-07-17
[http://ubuntuforums.org/showthread.php?p=7628656#post7628656](http://ubuntuforums.org/showthread.php?p=7628656#post7628656)

I am having FTP Server trouble...

---

### Post by Vishal Agarwal on 2009-07-17
Changing the access permission for the desired folder may work ?

---

### Post by Vishal Agarwal on 2009-07-17
in fact I am also searching the solution for vsFtpd, as it gives the access to view all the / folder and most of the files while somebody log in to the system using the FTP server.  I want to restrict them to their home folder only.

---

### Post by bodhi.zazen on 2009-07-17
Edit /etc/vsftpd.conf

Add/edit these lines 

```
local_enable=YES[FONT=monospace]
[/FONT]chroot_local_user=YES
```Restarte vsftp

```
sudo /etc/init.d/vsftpd restart
```

Note: I suggest you comment out anonymous_enable=YES

---

