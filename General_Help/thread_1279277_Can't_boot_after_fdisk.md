---
title: "Can't boot after fdisk"
date: 2009-09-30
forum: General Help
---

### Post by sargio on 2009-09-30
Ubuntu Server 9.04
sda - 1.5T
sdb - 250GB


I've just set up Ubuntu Server 9.04 on sdb(250GB). During installation process I've chosen "use LVM" option . After completion and rebooting to the new installed Ubuntu, I decided to add a new disk - sda(1.5T). I formatted it  with mkfs(ext3), successfully mounted it and then add an entry to fstab (mount by uuid) and reboot...
Now I'm facing a problem, I just can't load Ubuntu. 
I've got "Reboot and Select proper Boot device or Insert Boot Media in selected Boot device".

What have I done wrong?


I've just reinstalled Ubuntu and repeated all the steps and got the same result. 
Can't I just mkfs on entire disk with LVM?

---

### Post by sargio on 2009-10-01
???

---

### Post by MedianMajik on 2009-10-01
No need to double post as people should get around to your thread.  Have you checked your BIOS boot priority settings?  Is your primary drive set as the first device or is it something you used to install Ubuntu Server?  Are your drives set as IDE when they should be SATA?

Also, you can try selecting the device manually during boot with a hotkey defined by your BIOS/mobo (on my desktop it is F9).

Googling [Reboot and Select proper Boot device or Insert Boot Media in selected Boot device](http://www.google.com/search?q=Reboot+and+Select+proper+Boot+device+or+Insert+Boot+Media+in+selected+Boot+device&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a) yields lots of results.

---

### Post by sargio on 2009-10-01
Oops my bad. Ubuntu setup installed MBR on sda, but grub root and all stuff on sdb
Why??? It even didn't ask me where write MBR.

Anyway thanks.

---

