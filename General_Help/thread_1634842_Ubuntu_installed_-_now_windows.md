---
title: "Ubuntu installed - now windows"
date: 2010-12-01
forum: General Help
---

### Post by damon118 on 2010-12-01
So i got ubuntu 10.10 installed on my c: on my laptop. Could I install windows 7 on my second hard drive without messing up the MBR and be able to duel boot everything?

Trying to avoid going through MBR hell like i did just a couple of days ago.

---

### Post by runeh76 on 2010-12-01
> **damon118 said:**
> So i got ubuntu 10.10 installed on my c: on my laptop. Could I install windows 7 on my second hard drive without messing up the MBR and be able to duel boot everything?

Trying to avoid going through MBR hell like i did just a couple of days ago.



Dont remember how did went BUT
its gonna work 100% if u FIRST install Win.
U find solution to that situation if u looking around (google)  ;)

---

### Post by damon118 on 2010-12-01
I don't really feel like reinstalling ubuntu all over again. Yes I know it will work IF Windows was installed first, but it wasn't.

Would it work if I swapped the secondary and primary hard drives in my laptop, then install windows 7, or is that going to make things worse?

Would be nice to be able to keep both without going through MBR hell.

---

### Post by COKEDUDE on 2010-12-01
> **damon118 said:**
> So i got ubuntu 10.10 installed on my c: on my laptop. Could I install windows 7 on my second hard drive without messing up the MBR and be able to duel boot everything?

Trying to avoid going through MBR hell like i did just a couple of days ago.

I assume with what you asked you are trying to dual boot. It makes life easier if you install windows and then ubuntu. The problem lies in the windows bootloader. The bootloader that windows uses doesn't know to boot Ubuntu. So you must use Ubuntu's bootloader which is called grub. If you would like more information on what grub is please google it. You now have 2 choices. Option 1 Reformat your computer and install Windows first then install Ubuntu. Option 2 install Windows 7, then you can fix grub with this guide. 

[http://ubuntuforums.org/showthread.php?t=1014708&highlight=grub](http://ubuntuforums.org/showthread.php?t=1014708&highlight=grub)

---

### Post by damon118 on 2010-12-01
> **COKEDUDE said:**
> I assume with what you asked you are trying to dual boot. It makes life easier if you install windows and then ubuntu. The problem lies in the windows bootloader. The bootloader that windows uses doesn't know to boot Ubuntu. So you must use Ubuntu's bootloader which is called grub. If you would like more information on what grub is please google it. You now have 2 choices. Option 1 Reformat your computer and install Windows first then install Ubuntu. Option 2 install Windows 7, then you can fix grub with this guide. 

[http://ubuntuforums.org/showthread.php?t=1014708&highlight=grub](http://ubuntuforums.org/showthread.php?t=1014708&highlight=grub)

yes basically I am trying to duel boot, I just haven't been able to find any info on trying to install windows after ubuntu on a completely separate hard drive then be able to duel boot the two different os's on two different hard drives. 

Just not to excited about doing MBR repairs. I originally tried to install ubuntu after windows, it completely f'd up my windows. Tried to repair my windows installation(which didn't work) which f'd up my ubuntu. Tried to recover windows with my recovery partition and it messed up my MBR. Fixed the MBR which completely f'd up my restored windows and completely corrupted/destroyed my recovery partition. A bid headache that in the end cost me $200(had to purchase windows)

So i'm good with messing with MBR crap :)

---

### Post by WorMzy on 2010-12-01
There is no way to prevent Windows installing it's bootloader to the MBR. However, it may be possible to get it to install it to the "wrong" MBR by switching the disk boot order in the bios before installing Windows, then switching it back afterwards. Not guaranteed, but could be worth a try.

---

### Post by mastablasta on 2010-12-01
obvuiously you didn't do something right.
 
Still if you have ubuntu already installed it is possible to add windows.
 
it will go liek this. when you will install windows you will overwrite grub with windows boot loader (nothing you can do about it). you will then have the windows installed, but won't see ubuntu to boot into (because windwos boot loader doesn't see it).
 
you will now need to reinstall grub (which can see both Ubuntu and Win) over the windows boot loader. that way when you start your computer grub will load first and let you choose your OS.
 
good luck.: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by COKEDUDE on 2010-12-01
> **damon118 said:**
> yes basically I am trying to duel boot, I just haven't been able to find any info on trying to install windows after ubuntu on a completely separate hard drive then be able to duel boot the two different os's on two different hard drives. 

Just not to excited about doing MBR repairs. I originally tried to install ubuntu after windows, it completely f'd up my windows. Tried to repair my windows installation(which didn't work) which f'd up my ubuntu. Tried to recover windows with my recovery partition and it messed up my MBR. Fixed the MBR which completely f'd up my restored windows and completely corrupted/destroyed my recovery partition. A bid headache that in the end cost me $200(had to purchase windows)

So i'm good with messing with MBR crap :)

Bootloaders and MBR are 2 different things. 

[http://en.wikipedia.org/wiki/Booting](http://en.wikipedia.org/wiki/Booting)
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

I have Ubuntu and Windows installed on my gaming desktop with no problems. It also has 2 HD's. 

Just follow this guide to repair grub after you install windows. I have used this guide many many times and it works great. 
[http://ubuntuforums.org/showthread.php?t=1014708&highlight=grub](http://ubuntuforums.org/showthread.php?t=1014708&highlight=grub)

---

### Post by Mark Phelps on 2010-12-01
If you actually have two separate physical drives, then do the following:
1) Disconnect the Ubuntu drive, leaving only the candidate Windows drive connected
2) Boot from the Win7 medium and install it on the candidate Windows drive
3) Reconnect the Ubuntu drive -- but choose to boot from it, not from the Windows drive
4) Boot into Ubuntu, open a terminal, and enter "sudo update-grub".  This will generate a GRUB menu with entries for Ubuntu and Win7.
5) Reboot.

---

### Post by damon118 on 2010-12-01
> **Mark Phelps said:**
> If you actually have two separate physical drives, then do the following:
1) Disconnect the Ubuntu drive, leaving only the candidate Windows drive connected
2) Boot from the Win7 medium and install it on the candidate Windows drive
3) Reconnect the Ubuntu drive -- but choose to boot from it, not from the Windows drive
4) Boot into Ubuntu, open a terminal, and enter "sudo update-grub".  This will generate a GRUB menu with entries for Ubuntu and Win7.
5) Reboot.
  
Was exactly the info I was looking for. Thank you very much.

---

