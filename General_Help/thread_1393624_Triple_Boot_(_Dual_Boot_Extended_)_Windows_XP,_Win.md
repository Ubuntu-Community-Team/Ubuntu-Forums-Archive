---
title: "Triple Boot ( Dual Boot Extended ) Windows XP, Windows 7, &amp; Ubuntu"
date: 2010-01-29
forum: General Help
---

### Post by jjrjr1 on 2010-01-29
Hi
 
Just wanted to share how to create a triple boot situation if you need it (sort of Dual Boot on Steroids)
 
First lay out the partitions as your requirements for disk space may dictate for each operating system.
 
My installation for triple boot of Windows 7, Windows XP, & Ubnuntu started with Windows XP installed.
 
I can give you steps if any version of Windows is installed first. I have not tried this with Ubuntu installed first. But with a little wiggling of these steps, I suppose that could be done as well.
 
If XP is installed first:
 
Install Windows 7 to it's partition.
If on reboot Win7 has not created the dual boot for both OSs you will need to get a tool (or use command line 'bcdedit') to edit the boot manager database and set up dual boot.
 
Now install Ubuntu to it's partition.
When done and rebooted, GRUB will be your boot manager now and it will have a entry for Win 7.
When you select that you will be re-directed to the Win7 boot manager and be able to select which Windows to boot.
 
If Win7 is installed first:
Install XP to it's partition
When you reboot you will notice that Win7 is no longer available.
Dont Fret... Put the Win7 dvd into a drive, cancel installation, and enter cmd on XP
Navigate to the /boot folder of your Win7 dvd and type this command:
 
bootsect /nt60 all
 
On re-boot you will now be at Win7. If Win7 does not have a dual boot configuration, you will have to use the tool or command line editor to create dual boot in Win7 pointing to your XP partition.
 
Now install Ubuntu and the situation is the same as above for XP first.
 
Note on Ubuntu 9.10 grub does not have a file called menu.lst any more.
 
If you want to edit the GRUB display choices, default boot, etc., you need to edit /boot/grub/grub.cfg.
 
This file is just like menu.lst except it is re-genetated when ever you re-configire grub.
 
Hope this helps anyone trying to do this.
 
Take Care

---

### Post by MichealH on 2010-01-29
In a nutshell: Install Windows First or Ubuntu will be took over

---

### Post by rnerwein on 2010-01-29
> **jjrjr1 said:**
> Hi
 
Just wanted to share how to create a triple boot situation if you need it (sort of Dual Boot on Steroids)
 
First lay out the partitions as your requirements for disk space may dictate for each operating system.
 
My installation for triple boot of Windows 7, Windows XP, & Ubnuntu started with Windows XP installed.
 
I can give you steps if any version of Windows is installed first. I have not tried this with Ubuntu installed first. But with a little wiggling of these steps, I suppose that could be done as well.
 
If XP is installed first:
 
Install Windows 7 to it's partition.
If on reboot Win7 has not created the dual boot for both OSs you will need to get a tool (or use command line 'bcdedit') to edit the boot manager database and set up dual boot.
 
Now install Ubuntu to it's partition.
When done and rebooted, GRUB will be your boot manager now and it will have a entry for Win 7.
When you select that you will be re-directed to the Win7 boot manager and be able to select which Windows to boot.
 
If Win7 is installed first:
Install XP to it's partition
When you reboot you will notice that Win7 is no longer available.
Dont Fret... Put the Win7 dvd into a drive, cancel installation, and enter cmd on XP
Navigate to the /boot folder of your Win7 dvd and type this command:
 
bootsect /nt60 all
 
On re-boot you will now be at Win7. If Win7 does not have a dual boot configuration, you will have to use the tool or command line editor to create dual boot in Win7 pointing to your XP partition.
 
Now install Ubuntu and the situation is the same as above for XP first.
 
Note on Ubuntu 9.10 grub does not have a file called menu.lst any more.
 
If you want to edit the GRUB display choices, default boot, etc., you need to edit /boot/grub/grub.cfg.
 
This file is just like menu.lst except it is re-genetated when ever you re-configire grub.
 
Hope this helps anyone trying to do this.
 
Take Care

hi jjrjr1
 read this: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

before grub2 will drive you crazy
ciao
:P

---

### Post by jjrjr1 on 2010-01-31
Hi
 
That is not exactly true.
 
Yes Grub will take over your bootsector but to fix that simply run the command from your win7 disk in the boot folder
 
bootsect /nt60 all
 
This will put the win7 boot sector back for you.
 
Have not researched this for XP.
 
If you do, Let me know
 
Thanks
 
John

---

### Post by Jose Catre-Vandis on 2010-01-31
> If you want to edit the GRUB display choices, default boot, etc., you need to edit /boot/grub/grub.cfg.

This is not correct.

You edit files in /etc/grub.d folder. Grub2/Ubuntu documentation specifically tells you NOT to edit grub.cfg. I folks do, and are prepared to redit it once you have a kernel upgrade, but a sudo update-grub2 will wuipe out any changes you make as well.

I prefer to remove the executable bits from the 10_ and 30_ files and create custom entries in 40_

---

### Post by jjrjr1 on 2010-02-01
Thanks for the correction.

---

