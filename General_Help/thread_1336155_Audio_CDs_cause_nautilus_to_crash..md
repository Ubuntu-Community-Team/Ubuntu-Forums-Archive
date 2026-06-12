---
title: "Audio CDs cause nautilus to crash."
date: 2009-11-24
forum: General Help
---

### Post by kircher on 2009-11-24
Yesterday I put together a brand new computer for myself and I installed 64-bit ubuntu 9.10. The installation went smoothly, all drivers worked right away, etc. All in all a very smooth installation.

Today I put in an audio CD that I wanted to rip onto the hard-drive, and it caused nautilus to crash. I verified it with other audio cds, and they all cause nautilus to crash. Attempting to open the CD with sound juicer causes Sound Juicer to crash. Even leaving the Audio CD in the cd drive causes nautilus to crash whenever I restart it. There are a few pages on the internet with similar problems, however all are dead-ends. This is the closest thing to my problem, but the bug report was closed: [https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/479044](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/479044)

Some more information on my new computer:

Gigabyte [GA-MA785GPM-UD2H]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=3139") motherboard
AMD Phenom II X4 3.0 GHz
4GB OCZ DDR3 RAM
NVidia 9800GT pcie 2.0 graphics card
Pioneer SATA DVD-RW optical drive
1TB Seagate Sata 2 3.5"

At first I thought it may have had something to do with the optical drive being a SATA device, so I changed it to run in IDE mode in the BIOS configuration, and nothing changed. I even tried 32-bit Ubuntu, and there is the same problem. I went back to 64-bit, which is where I am now. I double checked that it was just Audio CDs, by testing DVD videos, data DVDs, and data CDs, and all of them work flawlessly.

I guess it's a bug of some sort, but I wouldn't know where to begin in filing the report. /var/crash is empty. Does anyone know if there is an immediate solution to this problem or will I have to file a bug report?

Thank you for your time

Kircher

Edit: Can anyone with the same, or a similar problem who wishes to add to this thread please post a description of their problem, with hardware information in as much detail as possible. We might be able to find a trend here.

---

### Post by jorisjoris on 2009-11-24
same problem here

---

### Post by kircher on 2009-11-24
joris, can you post up some information about your hardware? perhaps we can find a trend here. There are others with the same problem as I have stated.

---

### Post by kircher on 2009-11-24
If I were to file a bug report about this information, what would be the best way to acquire information about nautilus crashing, and what is causing audio CDs not to work?

---

### Post by kircher on 2009-11-24
I just installed Fedora 12 to test whether it&#347; a problem with Ubuntu. I have the exact same problems with fedora. Fedora uses GNOME 2.28.0 and Linux kernel 2.6.31.5-127.fc12x86_64

---

### Post by kircher on 2009-11-25
I have narrowed it down to a possible hardware incompatibility problem. Another thread on this forum here: [http://ubuntuforums.org/showthread.php?p=8382208](http://ubuntuforums.org/showthread.php?p=8382208) identifies a similar if not identical problem, and that user has the exact same hardware as I do. Does anyone know how I'd go about reporting a hardware incompatibility issue? As I said before, the problem existed when I tried Fedora 12 as well, so it's not restricted to Ubuntu 9.10. The other user in the thread above uses 9.04. I'd prefer not to have to replace my brand new optical drive.

---

### Post by fouvolant on 2009-12-04
I, I'm the other user with same problem :wink:

I have brought my optical drive to a friend which tried it on a computer with Windows XP and everything was fine. So, I reconnected it to my PC with Ubuntu and... it worked fine :confused: So, I guessed I made a connection error, shame on me :oops: But, today, it doesn't work anymore. In fact, it could had worked just the time I reconnected it...

:(

---

### Post by OpSecShellshock on 2009-12-04
How recent are the audio CDs? Do they contain any multimedia content and/or DRM? If they have multimedia content on them, it would probably be in formats recognizable by Windows (and possibly Mac), or there could be some kind of autorun.inf file messing it all up.

If you could find an audio CD that's old enough that there couldn't be multimedia content or DRM, then you can try to put it in the drive and see if it works. Alternatively, you could try reading the disks from within a Wine session. It doesn't make sense to me that other types of disks work in the exact same drive without any issues. I'm more inclined to think it's the content on the disk that's causing the problem.

---

### Post by fouvolant on 2009-12-04
> **OpSecShellshock said:**
> How recent are the audio CDs?

I've tried with very old ones and brand news. Same result.

---

### Post by czege on 2009-12-22
I believe I have this same bug.

Ubuntu 9.04
Asus P6T Deluxe V2 (Intel X58 ATX) DDR3 motherboard
Intel Core i7 920 (2.66GHz) QUAD 130W CPU
Pioneer 22x DVD-RW SATA drive

I'm new to Ubuntu, but I'd be glad to provide additional information to help with resolution. Just tell me what to do.

[edit]
Device manager reports my DVD-RW drive as:

Model: DVD-RW  DVR-218L
Vendor: PIONEER
Device File: /dev/sr0
Firmware Version: 1.00
Connection Type: Internal
Removable Media: Yes (ejectable)
Media Compatibility: CD-ROM/CD-R/CD-RW/DVD-ROM/DVD+R/DVD+R DL/DVD+RW/DVD-R/DVD-RAM/DVD-RW
Maximum Read Speed: 47x (56.45 MBps)
Maximum Write Speed: 47x (56.45 MBps)

Paul

---

### Post by lifeform23 on 2010-01-02
I am also having this issue, but only on one of my machines so I think that would indicate a hardware incompatibility issue.  The machine that it does not happen on has the optical drive connected via IDE and the machine that crashes has the optical drive connected via SATA.

---

### Post by lifeform23 on 2010-01-02
I would also like to add that it had been working Dec 22 and the crashing started on Dec 23 (2009 that is)

---

### Post by lifeform23 on 2010-01-02
My drive is also a Pioneer SATA 22X

---

### Post by dcstar on 2010-01-02
> **kircher said:**
> If I were to file a bug report about this information, what would be the best way to acquire information about nautilus crashing, and what is causing audio CDs not to work?

```
ubuntubug nautilus
```

---

