---
title: "Problem with dual boot setup"
date: 2011-04-03
forum: General Help
---

### Post by kkelly77 on 2011-04-03
I've had Ubuntu running on my laptop for a good while now but recently I've needed to dual boot with XP. I'm having a problem that someone might be able to help me with.

Initially I booted off the live CD so I could use GParted to repartition my hard drive. That worked fine. I booted off my XP CD (genuine copy) and it started the automatic installation of windows files. Once that was complete, it has the message at the bottom of the blue screen 'Now installing windows'. Then I just get the blue screen of death (typical windoze :()

I tried the install a few times but I constantly get the blue screen. Tried booting back into Ubuntu and formatted the new partition to NTFS but same thing happens. Any ideas what could be causing this? Thanks for the help.

K
P.S. I know I can use WINE, and I do have it installed, but I need a copy of Windows on the laptop for what I want to use it for.

---

### Post by techunit on 2011-04-03
Not enough information. Please post more info.

---

### Post by kkelly77 on 2011-04-03
> **techunit said:**
> Not enough information. Please post more info.

Can you tell me what information you need? Thanks.

I'm running Ubuntu 10.04 and I've allocated 28Gb of space on the hard drive for XP.

---

### Post by techunit on 2011-04-03
Did you attempt to install windows after ubuntu? Doing so will cause many problems making Ubuntu temporarily unbootable is one of them. This however does not describe the problem you are having.

Have you installed windows on this computer in the past?

Are you installing an OEM edition of Windows

Are you installing Windows on hardware that is damaged or could have any underlying problems?

This is information that would be helpful.

Sincerely,
Tobias Mann

---

### Post by kkelly77 on 2011-04-03
> **techunit said:**
> Did you attempt to install windows after ubuntu? Doing so will cause many problems making Ubuntu temporarily unbootable is one of them. This however does not describe the problem you are having.

Have you installed windows on this computer in the past?

Are you installing an OEM edition of Windows

Are you installing Windows on hardware that is damaged or could have any underlying problems?

This is information that would be helpful.

Sincerely,
Tobias Mann

My laptop came with Vista on it when I bought it. However, I removed Vista straight away and put Ubuntu on it. So Ubuntu was on my laptop first and I tried the Windows install second. I have read threads relating to Windows changing the MBR and not allowing Ubuntu to boot.

My copy of XP is an OEM copy. I have not had any issues with the laptop relating to hardware prior to trying to set up the dual boot. Even now using Ubuntu there are no issues. Only with the attempted XP install. HTH.

---

### Post by LostFarmer on 2011-04-03
Along with '[ techunit ]("http://ubuntuforums.org/member.php?u=1045873")' questions, is the XP partition Primary ?  Is it flagged bootable/Active in the MBR ? If one answer is no, make both yes and try again.

---

### Post by techunit on 2011-04-03
Ok well if you have the Vista Disk you need to use that instead of the XP OEM. I assume when you say that its OEM you mean the disk came from another computer not that you bought the disk as OEM.

---

### Post by kkelly77 on 2011-04-03
> **LostFarmer said:**
> Along with '[ techunit ]("http://ubuntuforums.org/member.php?u=1045873")' questions, is the XP partition Primary ?  Is it flagged bootable/Active in the MBR ? If one answer is no, make both yes and try again.

Do you mean labeled Primary in GParted? Which directory is the MBR located? (Sorry, very newb)

> **techunit said:**
> Ok well if you have the Vista Disk you need to use that instead of the XP OEM. I assume when you say that its OEM you mean the disk came from another computer not that you bought the disk as OEM.

Correct. I have a Vista CD that came with the laptop. My XP disc is one I bought separately i.e. it did not come with a PC/laptop.

---

### Post by techunit on 2011-04-03
OEM disks must be used on new machines. I don't remember if that was a moral or physical rule but thats there intended purpose.

I would try the Vista disk instead.

---

### Post by kkelly77 on 2011-04-04
> **techunit said:**
> OEM disks must be used on new machines. I don't remember if that was a moral or physical rule but thats there intended purpose.

I would try the Vista disk instead.

Will try it and update. Thanks.

---

### Post by kkelly77 on 2011-04-04
I've had a bit of success.

I used the Vista CD that came with the laptop and installed ok. I have been using this ([http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=6](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=6)) guide and I am at the point on Page 6 where it tells you how to install GRUB.

However, when I am in Terminal and I type in the code 'setup (hd0)' I am being told '/boot/grub/stage1' and '/grub/stage1' don't exist. Also getting Error 15: File not found.

Can you help with this problem?

---

### Post by wilee-nilee on 2011-04-04
Post from a booted equal to the installed version; an Ubuntu live cd and post the output of 
sudo fdisk -lu

The link is not working for me.

---

### Post by kkelly77 on 2011-04-04
> **wilee-nilee said:**
> Post from a booted equal to the installed version; an Ubuntu live cd and post the output of 
sudo fdisk -lu

The link is not working for me.


```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x99ae8d6c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1          233472   553191423   276478976   83  Linux
/dev/sda2   *   553198275   613056464    29929095    7  HPFS/NTFS
/dev/sda3       613056465   625137344     6040440    5  Extended
/dev/sda5       613056528   625137344     6040408+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```

---

### Post by wilee-nilee on 2011-04-04
Okay got to the link it is for grub-legacy, I suspect you have grub2, follow this link to reload it from a live cd.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

If you're still in trouble after this click on the bootscript in my signature, run it and post the all the text from the generated file in code tags.

---

### Post by kkelly77 on 2011-04-04
> **wilee-nilee said:**
> Okay got to the link it is for grub-legacy, I suspect you have grub2, follow this link to reload it from a live cd.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

If you're still in trouble after this click on the bootscript in my signature, run it and post the all the text from the generated file in code tags.

SUCCESS!!!!!

Well done [wilee-nilee]("http://ubuntuforums.org/member.php?u=906928"). That worked 99.9% :D

I can now choose between Ubuntu and Vista. However, there are about 9 or 10 options of Ubuntu with different version numbers. For example:

Ubuntu 10.04 LTS, kernel 2.6.32-23-generic
Ubuntu 10.04 LTS, kernel 2.6.32-23-generic (recovery mode)
Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode) etc etc.......

They were listed in the menu.lst file which I deleted but they still appear when the laptop is loading.

---

### Post by wilee-nilee on 2011-04-04
Those Ubuntu notations are kernel sets, generally it is advise to keep two; one is an extra in case needed. I remove the extras using a nice utility called Ubuntu Tweak it does many things the easy way.
[http://ubuntu-tweak.com/downloads/](http://ubuntu-tweak.com/downloads/)

The easiest way to add it is with these commands from the link.
sudo add-apt-repository ppa:tualatrix/ppa
This added the ppa and the key, now
sudo apt-get update
then 
sudo apt-get install ubuntu-tweak
It is now in menu tools look in package cleaner.

---

### Post by kkelly77 on 2011-04-04
Cool. Got it. Nice little tool.

---

