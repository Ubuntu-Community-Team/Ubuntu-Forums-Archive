---
title: "ClamAV Does Not Scan All Files In A Pendrive"
date: 2009-09-11
forum: General Help
---

### Post by Nosophorus on 2009-09-11
Hi!

I've tried to scan my pendrive, since I have a dual boot system (Windows XP and Linux), in order to properly transfer its files to Windows. The pendrive is almost in its full capacity (1 GB), but when I scan it ClamAV only scans 210 MB! Despite using the recursive flag (-r). See below:

----------- SCAN SUMMARY -----------
Known viruses: 621734
Engine version: 0.94.2
Scanned directories: 34
Scanned files: 327
Infected files: 0
Data scanned: 207.14 MB
Time: 31.078 sec (0 m 31 s)

I scanned a pendrive's folder containing some 110 MB of songs but it seems ClamAV sees none of them:

----------- SCAN SUMMARY -----------
Known viruses: 621734
Engine version: 0.94.2
Scanned directories: 4
Scanned files: 38
Infected files: 0
Data scanned: 0.05 MB
Time: 2.481 sec (0 m 2 s)

I'm using Ubuntu Hardy Heron (8.04) and, yes, I got that annoying message concerning the outdated ClamAV engine, but I suppose, in this case, it has nothing to do with the engine itself, since ClamAV does not "see" some files.

So many thanks in advance!

---

### Post by ottosykora on 2009-09-11
I have tried too and have seen that this is so, but there might be reason. There are much more files read then scanned in my case. This is due to the fact that some files can not be scanned since they are somehow not accessible for th scanner, they are somehow encrypted, or otherwise protected so the scanner can not open them for scanning.

Can thins be the case on your flash drive?

---

### Post by Nosophorus on 2009-09-12
Hi!

I don't think so. ClamAV used to scan all my files and after I made a dual boot system in this computer, reinstalling Ubuntu and installing Windows XP, that problem has arisen. Maybe, an ill ClamAV install could have something to do with that (or not). All I did was follow the directions given on Ubuntu website to install ClamAV.

I'm a little worried about using this pendrive in Windows because there are some malwares that can run right away after mounting the device and I wouldn't like to harm my machine and, more important, my files.

Thank you so much for your reply!

Cheers!

---

