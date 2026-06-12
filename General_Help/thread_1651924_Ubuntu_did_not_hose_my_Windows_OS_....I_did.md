---
title: "Ubuntu did not hose my Windows OS ....I did"
date: 2010-12-23
forum: General Help
---

### Post by SuperFreak on 2010-12-23
I have a dual boot with Win XP which I rarely use. I went into XP and used a program which became unresponsive, so I ALT CTRL DEL to get into Task manager and tried to end the process. Anyway the computer froze and I had to do a hard shutdown (with the power button). Now XP will only boot to Safe mode. If I try to go into normal mode it just goes to the XP screen before login and shows and endless bar timer. I am afraid to use my XP disc to repair XP as I might lose my Ubuntu partition. How do I safely fix XP?

---

### Post by djeikyb on 2010-12-23
FYI, I've never done this. But I've read about using the Windows XP disc in repair mode to fix ntldr. If it's just the Windows boot loader that is borked, you're home free (after you use a rescue* cd to reinstall grub). Google has a number of guides for this. Hope this points you in the right direction. If not..

Add an extra hard drive, boot with a linux livecd, copy your linux partition. Repair Windows, and whatever else you gotta do. Copy your linux stuff back over, and use a rescue* cd to reinstall grub.


* Your ubuntu install disc will work as a rescue cd. In the first boot option page, you can tell it to boot your system, you just need to tell it where the linux bits are.

---

### Post by oldfred on 2010-12-24
With XP you can fix everything from Ubuntu except you cannot run chkdsk. But if you have windows CD it may be easily to repair from that. You may not have to run all these commands, perhaps just chkdsk. If you want to prove it boots you have to run the fixMBR which will overwrite grub. So have an Ubuntu liveCD ready to reinstall grub.

XP CHKDSK
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r


[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
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

COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
Where [CDDrive] is location of cd or D: etc.
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

[http://support.microsoft.com/kb/291980](http://support.microsoft.com/kb/291980)
[http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Phanes on 2010-12-24
If you can boot into safe mode on xp then the issue is likely to be a driver within the program that is causing the issue. i dont know what was altered when you had to crash out of xp, but you could try a system restore from within xp and restore to just before you started having problems. i would guess that ntldr should be ok as you can boot to safe mode.

---

### Post by SuperFreak on 2010-12-24
Thanks everyone,

I tried copying the ntdetect.com file into the C directory and forgot the ntldr file so it didn't work. When I rebooted the second time after a hard power down I noticed that when I went to the safe mode screen it gave me the option of going back to the last known working configuration of Windows. I did that and presto it worked. 
I have just about given up on Windows and my next machine will probably be a single boot to Ubuntu; I had forgotten how unstable and unsecure windows is. I spent so many hours fixing Windows problems and installing & running security software. While Ubuntu has it's problems it is a much easier OS to work with.

---

