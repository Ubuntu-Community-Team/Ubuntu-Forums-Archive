---
title: "dual boot"
date: 2012-09-15
forum: General Help
---

### Post by debiauser on 2012-09-15
hello!

I want to install ubuntu 10.10 in my winxp machine and dual boot

the problem is that wubi seems not to offer an option to install my ubuntu 10.10 iso, and it only installs the one that it downloads from the server (which is the latest 12.04)

any hint for an easy wubi-like installation of 10.10?

thanks!

---

### Post by offgridguy on 2012-09-15
Is 10.10 iso available on CD?

---

### Post by debiauser on 2012-09-15
> **offgridguy said:**
> Is 10.10 iso available on CD?

I have it in a 4GB iso in my HD

cant I install it from that iso?

I can mount it in a virtual DVD player, but I cant burn it on an actual dvd

---

### Post by Karlchen on 2012-09-15
Hello, debiauser.

Each Ubuntu version brings along its own Wubi installer. I.e. the Wubi installer wubi.exe must match the Ubuntu version which you are trying to install via Wubi.
The latest wubi.exe will install the latest Ubuntu release, i.e. 12.04.1.

Provided you have got the Maverick Meerkat ISO image at hand, you can extract the appropriate wubi.exe from the root folder of the ISO image.
In case you do not have the image at hand, well, you can download the image and the matching wubi.exe here e.g.: 
[http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu-release/10.10/](http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu-release/10.10/)

But:
I wonder whether installing Ubuntu 10.10 is really a wise idea, because its lifecycle is over. It is not longer maintained and supported.

Kind regards,
Karl

---

### Post by Karlchen on 2012-09-15
> **debiauser said:**
> I have it in a 4GB iso in my HD
cant I install it from that iso?Hm. I doubt this will work. The Wubi installer has got some built-in size limit. The size limit is something below 1000 MB. So I doubt wubi.exe will be willing to process an ISO image of 4 GB.

Karl

---

### Post by debiauser on 2012-09-15
okay, I installed it via wubi, but I reboot and get this error:

invalid boot.ini
booting from c:\windows\

any hint?

---

### Post by debiauser on 2012-09-15
maybe you can help me build from scratch the correct boot.ini?

 partition C: win xp pro 64bit
 partition E: ubuntu 10.10 64bit

 thanks!

---

### Post by oldfred on 2012-09-16
The wubi entry should look like this. In your case the c: may be e:

boot.ini entry:
c:\wubildr.mbr="Ubuntu-Linux"

Post your entire boot.ini.

If editing from Linux you have to be careful to save with Windows line endings. 

If editing windows files like boot.ini
(Use nano instead of gedit, it's better for dos-style linebreaks)
Linux, of course, uses only LF as newline and DOS is expecting CR/LF so text files look wrong in DOS.
New versions of gedit have an combo box under save as to cchoose windows format.

---

### Post by debiauser on 2012-09-16
my boot.ini is invalid

these are its contents:


```
c:\grldr="Start Puppy Linux"
[boot loader]
timeout=30
[operating systems]
c:\grldr="Ubuntu 6.06 installer"
```

whenever I boot my pc, I get the msg "invalid boot.ini, booting from C:\windows

---

### Post by oldfred on 2012-09-16
grldr is grub4dos.

There is no Windows entry in your boot.ini? Is this from c: or e:?

This is a typical boot.ini for the first disk - rdisk(0)  and first partition - partition(1).

```
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

```

But again becareful of line endings.

---

### Post by debiauser on 2012-09-16
so how must my boot.ini be in order to dual boot?

how do I specify the exact values in the parentheses for each OS entry in boot.ini?

multi(x)disk(x)rdisk(x)partition(x)

I have two physical disks, the one with two partitions and the other with a single partition

---

### Post by oldfred on 2012-09-16
I do not know details.

How to edit the Boot.ini file in Windows XP
[http://support.microsoft.com/kb/289022/](http://support.microsoft.com/kb/289022/)

If you run the bootcfg then it creates a new boot.ini.

[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
[http://support.microsoft.com/kb/307654](http://support.microsoft.com/kb/307654)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

---

