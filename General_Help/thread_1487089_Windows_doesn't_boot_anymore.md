---
title: "Windows doesn't boot anymore"
date: 2010-05-18
forum: General Help
---

### Post by maes on 2010-05-18
Hi,
 
I have dual boot Windows XP pro SP3 / Ubuntu 9.04 and I only use the Windows to download torrents because the download speed on Ubuntu is terrible...
But by accident I pressed the power button when I was downloading in Windows and since then Windows won't boot anymore. Is this a Windows problem or is it maybe that it srewed up my grub? Because I can still select Windows in the grub menu but it stops at "Starting up".
suggestions?

---

### Post by johngreth on 2010-05-18
I had a similar problem and I was able to fix it with a windows boot cd running "fixboot". It takes a while, though, so I would try running "sudo update-grub" first, just to be sure it isn't grub.

---

### Post by maes on 2010-05-19
I updated the grub but that didn't work, so what's that fixboot you're talking about? I still have my installation disk, I think I have some kind of limited version (MSDNAA) because i already ran the system repair but nothing happened...

---

### Post by derande on 2010-05-19
> **maes said:**
> Hi,
 
I have dual boot Windows XP pro SP3 / Ubuntu 9.04 and I only use the Windows to download torrents because the download speed on Ubuntu is terrible...

i don't think Ubuntu is the cause of a slow torrent download speed. what client were you using? maybe try another client.
i know of some hosts who don't allow certain clients they don't know well because they think they are used for cheating ratios.

---

### Post by bcbc on 2010-05-19
you might have corrupted ntfs when you shut down hard. boot from windows repair and run chkdsk  on it.

---

### Post by johngreth on 2010-05-19
You need to get to a command prompt from the boot disk to run any commands.

---

### Post by maes on 2010-05-20
I'm not really a computer genius so what commands do I have to do?

---

### Post by bcbc on 2010-05-21
> **maes said:**
> I'm not really a computer genius so what commands do I have to do?

> To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1. Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer. 

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2. When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3. If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4. When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5. At the command prompt, type the appropriate commands to diagnose and repair your Windows XP installation. 

e.g. 
```
chkdsk c: /r
```
Here's a link with a bit more [http://support.microsoft.com/kb/307654](http://support.microsoft.com/kb/307654)

---

### Post by Sef on 2010-05-21
> Quote:
 	 	 		 			 				 					Originally Posted by **maes** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9321601#post9321601") 				
 				[I]Hi,
 
I have dual boot Windows XP pro SP3 / Ubuntu 9.04 and I only use the  Windows to download torrents because the download speed on Ubuntu is  terrible...[/I]
 			 		 	 	 
i don't think Ubuntu is the cause of a slow torrent download  speed. what client were you using? maybe try another client.
i know of some hosts who don't allow certain clients they don't know  well because they think they are used for cheating ratios. 	

+1.  When I download a torrent, it is often very fast.   I just use Transmission which is the default, but more clients are available in the Ubuntu Software Center.

---

### Post by maes on 2010-05-23
I also use the Transmission but when I download a torrent with Transmission, the speed is about 35 - 50 kB/s and when I tried the same torrent in windows the download speed was between 250 - 300 kB/s, maybe it's something that I have to change in the settings, I don't know..

---

