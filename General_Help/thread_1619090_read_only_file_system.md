---
title: "read only file system"
date: 2010-11-11
forum: General Help
---

### Post by ahmed shabayek on 2010-11-11
hey guy i was trying to fix my nvidia installtion when i upgraded from 10.04 10.10 the blank screen problem then after i mounted a cd containing the driver and installed it, restarted ,tried to edit the xorg to blacklist nouveau the system couldnt save saying its a read only file system

---

### Post by TeoBigusGeekus on 2010-11-11
The xorg file can only be accessed with root priviledges.
In order to make changes to it, you have to open it with
```
gksu gedit /etc/X11/xorg.conf
```

---

### Post by ahmed shabayek on 2010-11-11
thnx for the help but, icant use gk or gedit because i didnt blacklist nouveau yet so i am running command line with no gui // also i have tried as a root ( sudo bash) then (nano /etc/modprobe.d/blacklist.conf) but icant save : error read only file system

---

### Post by Vigh on 2010-11-11
sounds like a job for chmod, not sure which one is the most appropriate command to use, or if you should even use chmod on an important file like that but it will make the file save-able

could try sudo chmod 555 thereadonly.file

if you are doing a distribution upgrade, it is useful to keep in mind that proprietary drivers break when upgrading to a new distro, try booting into the recovery menu and restoring graphics to default settings

---

### Post by TeoBigusGeekus on 2010-11-11
```
sudo nano /etc/modprobe.d/blacklist.conf
```

---

### Post by ahmed shabayek on 2010-11-14
thnx vigh ill keep tryin, teo i told tht wont work but thnx anyway

---

### Post by TeoBigusGeekus on 2010-11-14
> **ahmed shabayek said:**
> thnx vigh ill keep tryin, teo i told tht wont work but thnx anyway

It will work if you put sudo in front of nano.

---

### Post by SeijiSensei on 2010-11-14
If it says you have a read-only file system, chances are that there are errors in the filesystem that must be fixed before it can be mounted read-write.  If you have only the one disk on the machine, you'll need to boot from a live CD version, then run the fsck program from a terminal and point it at the filesystem with errors.  Suppose, for instance, you're using /dev/sda1 as the root filesystem. Then you'd run "sudo fsck /dev/sda1" in the terminal to check and fix it as needed.

Usually problems like these arise when you've had a power outage or simply turned off the power on the machine rather than running the shutdown task.

---

### Post by ahmed shabayek on 2010-11-14
thnx teo  i tried but still, even super user and root cant change the files cause its a read only file system/ vigh how can i change it to default using recovery menu?

---

### Post by ahmed shabayek on 2010-11-14
thanks seiji ill try it right, and hopefully this will work thnx again :D

---

### Post by matt_symes on 2010-11-14
Hi

I would also suggest running fsck on the partition, but _dont_ run it when its mounted.

Kind regards

---

### Post by matt_symes on 2010-11-14
Hi 

I would also run fsck on the partition, but _dont_ run if mounted. Use the liveCD

Hmmm. Double post???

Kind regards

---

### Post by Vigh on 2010-11-16
hey mate, sorry i've been very busy haven't been able to get onto the forums recently, I think you can access the menu by holding ctrl-f2 down before the ubuntu logo comes up while booting, should give you the menu to select which kernel you want, select recovery kernel for your appropriate system if you are running more than one kernel, which is unlikely, you should have 4 options, you will want to enter the recovery kernel, then click run X fail safe or something like that, then it takes you into graphics recovery menu, click reconfigure X, restore to defaults, you should have normal open source graphics, you can then reinstall proprietary drivers if you wish from the new distribution, hope this works

regards
Ant

---

