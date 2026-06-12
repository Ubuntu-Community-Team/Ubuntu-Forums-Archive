---
title: "GNOME ERROR: dual boot WIN-7 and Ubuntu 9.10"
date: 2009-12-12
forum: General Help
---

### Post by jpjm132003 on 2009-12-12
Hello all,
It hurts me to say that I am new to Ubuntu, hopefully you experts can offer me some advice.
Here is my problem:

I had Windows 7 installed and running on my system.
The OS was installed to a solid state with two conventional hard drives for storage.
I decided to consolidate my data to one disk and install Ubuntu 9.10 on the spare.
The install went well, but now Windows WILL NOT BOOT.
I enter GRUB, where Ubuntu will boot fine.[COLOR=Black]
When I select Windows(loader) I receive[/COLOR][COLOR=Red][COLOR=Black]:[/COLOR]
[/COLOR][INDENT][COLOR=Red]GRUB Error 13 "Invalid or unsupported executable format[/COLOR]
[/INDENT]I have 3 hard disks in my system
SATA 1: Kingston 64gb solid state  (Windows 7)
SATA 2: Western Digital 320gb      (DATA)
SATA 3: Western Digital 320gb      (UBUNTU)

Device.map: reads....
(Hd0) /DEV/sda
(Hd1) /DEV/sdb
(Hd2) /DEV/sdc

Thanks in advance for any advice

---

### Post by jpjm132003 on 2009-12-12
SORRY the title should be GRUB ERROR: dual boot WIN-7 and Ubuntu 9.10

---

### Post by ubhi on 2009-12-12
generally people corrupt grub boot loader after installing windows over ubuntu... your case is reverse..

so
1. first check you still have windows partition alive on your system, open ubuntu goto terminal (Application->Accessories->Terminal), check partitions type & size

#df -h

if you can see your windows NTFS partition which is stored at (ATA 1: Kingston 64gb solid state (Windows 7)), then its okay.

2. first of all repair your windows 7 MBR by windows 7 bootable disk,

goto the reparing option from windows 7 installation disk then either of following commands

fixmbr 
fdisk /mbr (etc or you can find repair MBR from any windows forumn site)

or 

you can repair windows

3. then at last you have to fix out ur ubuntu boot loader by below mentioned document (because windows 7 MBR overwrite the grub)  

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

good luck lots of work to do....

---

### Post by jpjm132003 on 2009-12-17
Thank you very much for your help ubhi,

Solution:
1. Boot to Windows 7 install CD,
2. Repair Windows Startup,
3. Restart

GRUB now has no problems loading Windows 7 or UBUNTU 9.10.

Thanks again.

---

