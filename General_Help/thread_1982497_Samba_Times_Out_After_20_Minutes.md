---
title: "Samba Times Out After 20 Minutes"
date: 2012-05-18
forum: General Help
---

### Post by Mighty_Joe on 2012-05-18
I have a new PC that I've set aside to act as a home file/media server.  I installed 12.04 and shared my home directory out with Samba so I could access it from my MacBook Pro via wireless.  The problem is that after around 20 minutes, I get an error on my laptop that the Samba connection has been "interrupted".  I can't access the connection with Finder for a minute or so, but it comes back up and I can browse the remote directory again.  
I don't think this is a problem with my wireless or client as I have an [older home server running 8.04]("http://ubuntuforums.org/showthread.php?t=1244304") that does not exhibit this problem.  I can copy large files to it (taking more than 20 minutes) and do not get a timeout.  I also tried booting into Windows 7 and was not successful with the new server but was successful with the older one, so it doesn't appear to be OSX
As far as I can tell I've turned off all the power-saving features of the BIOS and Ubuntu. I would assume that if it were power saving, it would not fail in the middle of a file transfer. Does anyone have any other ideas?
Thanks!

---

### Post by Mighty_Joe on 2012-06-07
The mystery gets deeper.  I installed 12.04 and Samba on an HP EliteBook that I borrowed from work and file transfers work fine. I'm beginning to think there's a hardware problem with the desktop.  It's an HP Elite 8000 Elite SFF that I added a 2TB Western Digital Green hard drive to.

---

### Post by Mighty_Joe on 2012-06-08
I was suspicious of the Western Digital Green drive, so I ripped it out and reinstalled 12.04. No problem after that, so I reinstalled the drive and reinstalled 12.04, thinking that maybe the hdparm's Ubuntu chose for the secondary drive had a spindown value configured.  Lo and behold, everything works.  I'm thinking I may have a wonky SATA cable, but I'm puzzled that it would be that consistent, to time out around 20 minutes each time, and only with Samba. SFTP and USB file transfers worked fine. 
*shrug*

---

