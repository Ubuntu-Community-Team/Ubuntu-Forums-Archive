---
title: "Help with cloning"
date: 2010-01-23
forum: General Help
---

### Post by clayman1000x on 2010-01-23
I currently dual boot windows XP Pro with Ubuntu 9.10. I made a mistake last night playing with gparted and lost my E drive, which had all of my music, games and movies plus is where my Ubuntu install was. I then ended up reformatting the drive with windows and reinstalling Ubuntu 9.10. 
My question is how can I put my windows files on my E drive without going through the hassle of reinstalling windows. 
I have a 20g IDE drive where my windows install is, windows and Ubuntu both tell me this drive is failing, (I have used it for booting since 2002, so I am not that concerned with it), another 40g IDE drive for more storage and a 160g SATA drive where Ubuntu is again installed. I want the SATA drive to be my main boot drive now, so how can I clone my windows boot to the other drive. I tried gparted but could not figure it out. I have gparted burnt to cd, booted with it and just don't understand how to use it.
Also, if I clone this boot drive to the SATA drive, do I need to change jumper settings on my 40g to master when I take out the 20g drive.
20g master and 40g slave on first IDE channel and 2 CD devices on second IDE channel and SATA drive on first SATA connection. I read somewhere that it is better to keep the cd devices on another channel than the disk drives.
Can anyone give some advice?
:popcorn:

---

### Post by dcstar on 2010-01-24
> **clayman1000x said:**
> I currently dual boot windows XP Pro with Ubuntu 9.10. I made a mistake last night playing with gparted and lost my E drive, which had all of my music, games and movies plus is where my Ubuntu install was. I then ended up reformatting the drive with windows and reinstalling Ubuntu 9.10. 
My question is how can I put my windows files on my E drive without going through the hassle of reinstalling windows. 
I have a 20g IDE drive where my windows install is, windows and Ubuntu both tell me this drive is failing, (I have used it for booting since 2002, so I am not that concerned with it), another 40g IDE drive for more storage and a 160g SATA drive where Ubuntu is again installed. I want the SATA drive to be my main boot drive now, so how can I clone my windows boot to the other drive. I tried gparted but could not figure it out. I have gparted burnt to cd, booted with it and just don't understand how to use it.
Also, if I clone this boot drive to the SATA drive, do I need to change jumper settings on my 40g to master when I take out the 20g drive.
20g master and 40g slave on first IDE channel and 2 CD devices on second IDE channel and SATA drive on first SATA connection. I read somewhere that it is better to keep the cd devices on another channel than the disk drives.
Can anyone give some advice?
:popcorn:

Just boot off a Live CD and use the Partition Editor Cut and Paste function.

---

