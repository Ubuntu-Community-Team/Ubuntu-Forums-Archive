---
title: "Am i right in saying that...."
date: 2012-01-10
forum: General Help
---

### Post by L33tsco on 2012-01-10
My old desktop has suddenly stopped booting,i tried out ubuntu and are highly considering installing it,am i right in saying that i can install all 4.4gb of ubuntu goodness onto my flash drive and transport my entire ubuntu o.s to another pc via flash drive?

---

### Post by Basher101 on 2012-01-10
> **L33tsco said:**
> My old desktop has suddenly stopped booting,i tried out ubuntu and are highly considering installing it,am i right in saying that i can install all 4.4gb of ubuntu goodness onto my flash drive and transport my entire ubuntu o.s to another pc via flash drive?

But you cannot simply copy it over. That will not work (trust me i tried it myself and learned the hard way). So if you want a system image that you can install on multiple PCs check out Remastersys. It is a backup program that compresses your entire install into a bootable .iso (note that it cannot compress more than ~ 18 GB total) You can then make a Live USB using your self-made iso and install that everywhere else you want. There is a new application in your dash called "RELEASE Install" which will start the installation process. If you do not find it, you can start the installation process manually with the command ```
gksu ubiquity --desktop %k gtk_ui
```


regards

---

### Post by BC59 on 2012-01-10
You could try @Basher101 solution or trying to copy the system with Remastersys or Clonezilla, but for best results you should do a fresh installation of the system in your new computer.
You are going to spend many hours to clone your system and a new installation needs no more than an hour.

---

### Post by Basher101 on 2012-01-10
sureley, if he has no programs installed yet and hasn't done hours of configuration, he should go for fresh installs. But if he has changed alot already, remastersys will take care. Also, a remastersys install only took me 10 minutes more than a fresh one (for 6 GB backed up)

---

### Post by BC59 on 2012-01-10
The best way to avoid the hours of tweaking is to keep record of the changes you make. I have a .txt file in which I paste all the commands, installed PPAs, applications etc I used to better my system. In a fresh installation, I just copy-paste the commands and that's it.

---

