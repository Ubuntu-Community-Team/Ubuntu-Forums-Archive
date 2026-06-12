---
title: "Help! Missing OS!!"
date: 2010-05-19
forum: General Help
---

### Post by bigseb on 2010-05-19
Some time ago I ran Gparted off my Live CD and formatted the entire hard disc. Then I installed Karmic and lived a happy life. O:)

The past week I have been searching for a decent 3D CAD program and found that I will be needing to use Windows. So I create a 30Gb partition and try to install XP. So after it runs through file extraction process the machine reboots and SHOULD start install XP, only it doesn't. I get a message: "Missing NTLDR. Hit any key to reboot" :confused:

I wrote to Seven Forums and one chap suggested I boot up with command prompt using my Windows disc then type: bootrec /fixmbr [enter], bootrec /fixboot [enter], bootrec /rebuildbcd [enter]). The first command is successful. The second one gives me this message: "The volume does not contain a recognised file system. Please make sure that all the required drivers are loaded and the volume is not corrupted" :(

When reboot it shows the usual Acer screen (Prepare to boot OS, etc) then this: "Missing Operating System :cry:

I ran the Live CD and sure enough Karmic is still there it just won't boot. I really need to fix this ASAP as Linux is still my main OS. XP will need to running too but that's secondary. PLEASE HELP!!

---

### Post by amite on 2010-05-19
check these links it may help u.......
[http://www.tech-pro.net/howto-fix-ntldr-is-missing.html](http://www.tech-pro.net/howto-fix-ntldr-is-missing.html)

[http://www.quickonlinetips.com/archives/2005/12/ntldr-is-missing-press-any-key-to-restart/](http://www.quickonlinetips.com/archives/2005/12/ntldr-is-missing-press-any-key-to-restart/)

[http://support.microsoft.com/kb/318728](http://support.microsoft.com/kb/318728)

[http://support.microsoft.com/kb/314057](http://support.microsoft.com/kb/314057)

---

### Post by jbrown96 on 2010-05-19
1) Boot up the liveCD
2) Mount your Karmic partition. You can check your partition table with ```
sudo fdisk -l
``` then mount that partition with ```
sudo mkdir /media/mount && sudo mount /dev/sdXX /media/mount
``` replace XX with your partition. If you don't know what to do, then post the output of fdisk -l here.
3) Bind /dev/ into your mount point ```
sudo mount -bind /dev /media/mount
```
4) Chroot into your Karmic install. ```
sudo chroot /media/mount /bin/bash
```
5) Reinstall and update grub. ```
sudo grub-install && sudo update-grub
``` You should get some output that shows what Grub has found. XP should be listed there. If so, then you should be fine after you reboot. Karmic and XP will be accessible.

---

### Post by dcstar on 2010-05-19
> **bigseb said:**
> 
.........
I ran the Live CD and sure enough Karmic is still there it just won't boot. I really need to fix this ASAP as Linux is still my main OS. XP will need to running too but that's secondary. PLEASE HELP!!

Reinstall Grub:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by ryan858 on 2010-05-19
First of all, you wiped out grub by "fixing" the MBR. Basically, there's no bootloader anymore.

You'll have to use a Live cd to reinstall grub to the MBR. You can add Windows to the grub menu once you've got that fixed. That will solve the "Missing Operating System" issue.

---

### Post by elliotn on 2010-05-19
fixmbr,fixboot would erase grub thus u will need to reinstall it.

---

### Post by bigseb on 2010-05-19
Ok, questions....

1) Since the first command (bootrec /fixmbr) was successful does that mean XP will now install? Never got a chance to try...

2) Would it be better to install XP first, before repairing Grub?

3) @ DCSTAR: had a look at your link, that's a lot!! As a relative newcomer isn't there an easier-to-understand version. Would be a great help.

4) @ JBROWN96: Will following your method not interfere with the OS ie drivers, files, etc?

---

### Post by elliotn on 2010-05-19
MISSING NTDR means ur booting from a a wrong partition or drive, if u have more than 1 drive use the bios to point which drive to boot on.

---

### Post by jbrown96 on 2010-05-19
Installing Windows before Ubuntu is recommended. 

My method will allow you to boot your Ubuntu install and should also add a Grub entry for XP. There will be no damage to anything.

---

### Post by elliotn on 2010-05-19
> **bigseb said:**
> Ok, questions....

1) Since the first command (bootrec /fixmbr) was successful does that mean XP will now install? Never got a chance to try...

2) Would it be better to install XP first, before repairing Grub?

3) @ DCSTAR: had a look at your link, that's a lot!! As a relative newcomer isn't there an easier-to-understand version. Would be a great help.

4) @ JBROWN96: Will following your method not interfere with the OS ie drivers, files, etc?

yes install XP first then reinstall grua coz if u reinstall grub first then xp will erase it

---

### Post by bigseb on 2010-05-19
> **dcstar said:**
> Reinstall Grub:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

Did it and it worked!!

\\:D/

---

### Post by bigseb on 2010-05-19
> **dcstar said:**
> Reinstall Grub:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
It worked!

\\:D/

---

### Post by ryan858 on 2010-05-20
Please mark the thread solved. Thanks.

---

