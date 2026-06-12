---
title: "strip lucid Desktop installation to minimalCD"
date: 2010-09-06
forum: General Help
---

### Post by 13east on 2010-09-06
I'm trying to get a minimalCD installation on a flashdrive but the installation never finishes... (i've left the installation runnin overnight for over 12hrs and only 90 percent got completed; whenever trying to retrive packages from the internet the process slows down to a crawl; i've tried ext4, ext3, ext2 and resierfs)

normal Desktop insatallation works fine; so I was wondering if there is anyway to strip all the packages off a normal installation to get it to minimal installation, and than start installing the pacakges i need?

---

### Post by Revolutionary101 on 2010-09-06
Are you trying to create a LiveUSB flash drive with Ubuntu on it? If you are trying to do a normal install of Ubuntu to a flash drive I know there would be problems with it.

If you are doing the install some other way, try to go to System>Administration>Startup Disk Creator. With that program just take an .iso file and you will be able to run Ubuntu off of your flash drive just like a LiveCD, but you will be able to install programs on it. One last thing to note is that Startup Disk Creator will only install Ubuntu on a flash drive formated with FAT32. (Sorry if all this sounds obvious, but I just want to cover all the bases)

---

### Post by 13east on 2010-09-07
> **Revolutionary101 said:**
> Are you trying to create a LiveUSB flash drive with Ubuntu on it? If you are trying to do a normal install of Ubuntu to a flash drive I know there would be problems with it.

If you are doing the install some other way, try to go to System>Administration>Startup Disk Creator. With that program just take an .iso file and you will be able to run Ubuntu off of your flash drive just like a LiveCD, but you will be able to install programs on it. One last thing to note is that Startup Disk Creator will only install Ubuntu on a flash drive formated with FAT32. (Sorry if all this sounds obvious, but I just want to cover all the bases)

thx for your response...

- i can run a live presistant usb drive, but that doesnt let me update the system and reinstalling every time with a new release every 6months is too tedious.
- i am able to get a full desktop installtion running on a 9gb usb drive partation but wanna strip the installation of all the extra packages that i dont need.  but trying to run a [MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD") takes forever.

- So I was wondering if there is anyway to delete all packages from the installation drive to get a mirror of a Minimal installation, and than work my way forwards by adding only the packages I need/want?

---

### Post by dcstar on 2010-09-08
> **13east said:**
> I'm trying to get a minimalCD installation on a flashdrive but the installation never finishes... (i've left the installation runnin overnight for over 12hrs and only 90 percent got completed; whenever trying to retrive packages from the internet the process slows down to a crawl; i've tried ext4, ext3, ext2 and resierfs)

normal Desktop insatallation works fine; so I was wondering if there is anyway to strip all the packages off a normal installation to get it to minimal installation, and than start installing the pacakges i need?

[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

---

### Post by 13east on 2010-09-08
> **dcstar said:**
> [http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

-thx for your response but not what i was looking for
-i had planned on using remastersys to backup my installation after i had gotten it to my liking
-my problem is that i cannot get MinimalCD installation (or the "cli" installation) to install itself onto a flash drive; the times i have tried this process the installation took unbearably long (over 12hrs for only 90% completion) and i do not have a spare hard-drive to install into and create a remastersys iso right now.
  i am able to run a normal desktop installation off of a flash drive and would like to be able to remove all packages off of it to get it to a minimal terminal only setting.  And than add back basic packages like "gnome-core" and "xorg" etc.

---

