---
title: "Live CD problem, help?"
date: 2009-11-18
forum: General Help
---

### Post by WatTwo on 2009-11-18
Okay, so i have a Ubuntu CD, burned the ISO, now i need a broadcom driver, so i found a way to get it off the disk, but when i do this, it says "please insert disk labeled....."

But i have it in the drive.

Any idea what i'm doing wrong? thanks.

Heres what im trying to do:

[http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)

---

### Post by sailthesea on 2009-11-18
Are you trying to do this whilst running the CD live session? 
If you've installed already it should work if not... well it won't;)

---

### Post by WatTwo on 2009-11-18
Err.. I put the CD in and tried doing what it says.

And just to be sure, the live CD is the one i unstalled ubuntu with right?

---

### Post by sailthesea on 2009-11-18
OK I'm sorry I wasn't clear
 Have you installed Karmic and are trying to get the wireless working from the LiveCD as suggested in your link? 
 There seems to be a problem with the Broadcom driver in Karmic I found but lost a thread you may want to look at. I will try and track back to it 
 I haven't tried Karmic myself yet, there seem too many problems
 Will post if I find the info

Good luck And google!;)

 If you have the windows disk with driver in you could try ndswrapper to install

[http://ubuntuforums.org/showthread.php?t=197102&page=196](http://ubuntuforums.org/showthread.php?t=197102&page=196)

---

### Post by WatTwo on 2009-11-18
Yep, that's what I'm trying to do, all i need for it to work is for it to "see" the live CD

Is there anything i have to do after putting the disk in?

---

### Post by sailthesea on 2009-11-18
> **WatTwo said:**
> Yep, that's what I'm trying to do, all i need for it to work is for it to "see" the live CD

Is there anything i have to do after putting the disk in?

 It should auto mount
 Does it apear on your desktop or My Computer?
 Open it from there and browse for the right drivers then install them 
 Hopefully job done (never been a fan of ndswrapper tbh)
 
 Otherwise you hit a bug and it would help if you filed a report and check Launchpad for a better solution
 Going beyond my experience now 
 Persist and good luck!! :p

---

### Post by mechro on 2009-11-18
> **WatTwo said:**
> Okay, so i have a Ubuntu CD, burned the ISO, now i need a broadcom driver, so i found a way to get it off the disk, but when i do this, it says "please insert disk labeled....."

But i have it in the drive.

Any idea what i'm doing wrong? thanks.

Heres what im trying to do:

[http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)

Are you trying to Add CD-Rom in Software Sources?

A workaround is to insert the disc, unmount it (right click disc icon on desktop and Unmount Volume) then start the Add CD-Rom procedure.

---

