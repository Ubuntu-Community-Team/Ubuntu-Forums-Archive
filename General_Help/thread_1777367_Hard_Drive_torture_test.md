---
title: "Hard Drive torture test"
date: 2011-06-07
forum: General Help
---

### Post by bakegoodz on 2011-06-07
This question doesn't necessary have a Linux answer, but I'm impressed with the caliber of answers I get in this forum.

Do you know a really good way to torture test a hard drive?

 I have a drive that gets data errors some times when I copy files, I have confirmed it with multiple computers and installs of Windows and Ubuntu. Manufacturer tools, Badblocks (with zero wipe too), Smartmontools don't fix or find the problem. I want to "push this drive over the edge" without voiding the warranty. I know I could probably get it replaced under warranty now, but I don't like the idea of them reselling it as a refurb and I want to "put it out of its misery".

---

### Post by seawolf167 on 2011-06-07
Take a look at the [Phoronix Test Suite]("http://www.phoronix-test-suite.com/")

For RAM testing, use memtest which is a grub option available from the GRUB menu at boot

---

### Post by linuxinstalledfromhdd on 2011-06-07
> **bakegoodz said:**
> This question doesn't necessary have a Linux answer, but I'm impressed with the caliber of answers I get in this forum.

Do you know a really good way to torture test a hard drive?

 I have a drive that gets data errors some times when I copy files, I have confirmed it with multiple computers and installs of Windows and Ubuntu. Manufacturer tools, Badblocks (with zero wipe too), Smartmontools don't fix or find the problem. I want to "push this drive over the edge" without voiding the warranty. I know I could probably get it replaced under warranty now, but I don't like the idea of them reselling it as a refurb and I want to "put it out of its misery".



Ubuntu has plenty of testing tools..    Try using the default Disk Utility and SMART Status checks.   For data recovery I use: [http://cinderbox.net/2011/05/12/photorec-digital-picture-and-file-recovery/](http://cinderbox.net/2011/05/12/photorec-digital-picture-and-file-recovery/)

---

### Post by andyhe on 2011-06-07
using dd or ddrescue might be a nifty tool for that

---

### Post by dragonfly41 on 2011-06-07
[http://www.dban.org/about](http://www.dban.org/about)

---

### Post by bakegoodz on 2011-06-08
Those are all media scans that read and/or write in a sequential manner. Is there a test the drive to max, it would definitely need to include a random access test makes the heads dance all over place.

---

### Post by dFlyer on 2011-06-08
What does disk utility report as the status of your drive? If it's anything other than good, I'd back up what you want to keep and get a new drive. You might want to check you ram also.

---

### Post by bakegoodz on 2011-06-08
It is not the RAM. No Test says it has a problem now, though it has had bad sectors corrected 3 times before with the Manufacture's utility. Sometimes when I have a problem I find another bad sector, but sometimes it doesn't. Smartmontools is a linux command line too that gets the S.M.A.R.T information of the drive and Badblocks is a linux command line tool that checks all the sectors.

> **bakegoodz said:**
> 
 I have a drive that gets data errors some times when I copy files, I have confirmed it with multiple computers and installs of Windows and Ubuntu. Manufacturer tools, Badblocks (with zero wipe too), Smartmontools don't fix or find the problem . . . ".

---

### Post by Habitual on 2011-06-08
```
sudo /usr/bin/udisks --dump | grep -A 24 Updates
```

will show you what the OS "sees" as bad, etc...

dFlyer is spot-on. Flaky ram can cause file operation anomalies.
Could be a controller issue too...

---

### Post by bakegoodz on 2011-06-09
Nope. The drive has same issues in many other computers, it is a drive I use in an encloser to move large files around. I also been using it without the encloser lately and I get io errors once in a while too. Not a filesystem issue have reformatted several times. Don't care about about the data after it moved to another computers, just want it to reliably transfer multiple GB files from one location to another.
 I could try to get it RMA'd, but I would like to kill the drive. I would think a nice hyper active random access write for a few days would do it, but I have yet to find a random access write tool. All the dd variants are sequential.

---

### Post by larrypg on 2011-06-09
are you trying to break the drive so you can get a new one under warranty?

---

### Post by Jouke74 on 2011-06-10
Yes he is trying to break it to get warranty... Hmm.

Is it an external USB drive? In any case, if it starts to have bad sectors within the warranty period I think you can get a replacement if you call the manufacturer and explain things nicely.

---

### Post by Habitual on 2011-06-10
> **bakegoodz said:**
> ...Do you know a really good way to torture test a hard drive?

Install Windows. :)

P.S. If you call the Manufacturer for an RA, just tell them "Fdisk doesn't see the drive" and they happily send you a new one.

---

### Post by patmagee1024 on 2011-06-10
> **Habitual said:**
> Install Windows. :)


Yea, Vista will trash it rather quickly.

---

### Post by collisionystm on 2011-06-10
If only you could find  a tool that would let you spin the drive beyond its RPM capabilities.

---

### Post by bakegoodz on 2011-06-12
The drive is unreliable, but it passes all the test I can throw at it. It is quite a pain to get a drive replaced when their diag tool doesn't give a error code. I just got an another drive replaced in a HP workstation that would show up off an on in the BIOS (even applied both new Motherboard and drive firmware). I had to contact support 3 times and over all it took 4 hours with their technical support get them to send a new one. I was going to pull my hair out how many times I had to explain yes the drive was hooked up when it wouldn't detected and that there still was a problem when the bios did detected it and their diag tool returned no error. 3 other diag tools said it was fine when it detected and yes it did the same thing in a non-HP computer. I've had some interesting issues with drives lately.

---

