---
title: "slow data transfer to external drive in jaunty"
date: 2010-03-26
forum: General Help
---

### Post by davy jones on 2010-03-26
I'm getting a really low speed (2-3 mbps) while transferring data to my USB drive and external hard drive. I've heard this problem's there in Karmic but not in Jaunty but i have Jaunty and yet I'm facing this problem. Please help

---

### Post by Rasheeke on 2010-04-10
I'm having the same issues.  I thought I found a solution [here]("http://ubuntuforums.org/showthread.php?t=1330727&page=7") but that was just for USB sticks, suggesting a switch to the noop I/O scheduler which would only be good for flash drives, not hard disks.  

The problems are the same but the current solution only applies to flash.  

It has to do with ubuntu not dealing to swell with NTFS.  That's all I can gather.


Any help would be appreciated, maybe this will be better when Ubuntu 10 comes out...

edit: davy jones, it may have to do with the kernel you're using, apparently one of the more recent ones has caused this.

---

### Post by davy jones on 2010-04-12
Thank you but I'm actually fairly new to ubuntu and I don't really know all that about kernel settings etc. I tried this link and it led me to some post in which its shown how to change the kernel but that was for Linux Mint and its not the same as ubuntu so it was kind of a dead end. Can you please tell me in simpler terms how to change the kernel?

---

### Post by scifiskywatcher on 2010-04-12
Are you moving many files at the same time? I found that the more individual files that I transfer the slower it gets. This includes both esata & usb. I found that if I have a lot of individual files to move I place them in a single folder and transfer them. I get sustained top speeds.

---

