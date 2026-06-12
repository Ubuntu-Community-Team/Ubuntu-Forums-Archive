---
title: "XP Nod32 finding Ubuntu/GRUB as false positive?"
date: 2010-07-12
forum: General Help
---

### Post by Ninamori on 2010-07-12
Wasn't sure where to post this sorry. Here's my setup...

[B]sda = Ubuntu 10.4 (sda1)
sdb = Win XP Pro (sdb1)[/B]

Win XP is running ESET Nod32 AV and Comodo firewall, I'm having a big problem with Nod and Ubuntu, for some reason Nod is picking up the MBR on 0 physical disk (sda) as a virus **"Probably unknown TSR.Boot Virus"**, and says is unable to clean. Since I've just that second installed XP I'm pretty sure it's not a virus or trojan, but is picking up GRUB as a false positive.

I just wanted to hear other peoples opinions on this, am I right thinking its a false positive, or should I investigate further? Nod will keep spitting out the complaint over and over, about every 2 mins.

---

### Post by Andragorn on 2010-09-01
Hi, I have dual booting by grub Ubuntu and windows 7. Under windows 7  the same notification from Nod about TSR.Boot virus like You. It's start show, when I installed Ubuntu. So i thing it's false positive.

sorry for my english ;(

---

### Post by mamas6667 on 2011-07-14
sda1
First Hard rive and only partition has XP installed.

sdb2
I installed Ubuntu 11.04 using the ubuntu-11.04-alternate-i386.iso to a 2nd Hard drive's secondary partition.

I installed Grub2 to sdb2 partition not to sdb MBR

And as soon as I booted windows, ESET Smart Security antivirus finds "TSR.boot"

MBR sector of the 1. physical disk contains probably unknown TSR.BOOT virus

[B]SOLUTION
I removed this false positive simply by using a "partition manager" to change "boot flag" from the 2nd HD's  secondary partition to the  2nd HD's primary partition.[/B]

---------------------------------------------------------------------------------------------------
BTW im chainloading GRUB2 from XP using grub4dos.

copied "grldr" in C:\
-----------------------
Edited boot.ini 

```
[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\grldr="Linux"
```----------------------------
and created a menu.lst from a text file

C:\boot\grub\menu.lst

containing this

```
default 0
timeout 1
color green/black

#
title           Chainload into GRUB2
uuid            827d7140-3493-41f6-8ad7-29e7c5902da4
kernel          /boot/grub/core.img


```


---------------------

I hope it helps, took me many hours to figure it out, gtg sleep.

---

### Post by a.toraby on 2011-07-24
I have this problem too. After that I installed ubuntu eset smart security says that 0.physical disk has an unknown MBR sector virus.
I installed windows on sda1 and grub on sda boot sector.
Are you sure that this is a false positive?

---

