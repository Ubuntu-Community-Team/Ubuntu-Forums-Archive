---
title: "A question about restoring from Clonezilla backup"
date: 2009-11-01
forum: General Help
---

### Post by lgfish on 2009-11-01
Greetings, 

I was wondering if anyone out there could give me some general advice about restoring from a clonezilla backup I made of my machine about 6 months ago.  

Here's the situation:  I am pretty sure I had upgraded to Intrepid, which I was running on a Dell XPS-M1330 laptop.  I had to get rid of it in a hurry, so I backed it up using Clonezilla.   The details are fuzzy about any specific choices I might have made during that backup, but I have notes somewhere.  Now, I'd like to restore my backup.  I'm still a newbie, and here's what I need to know: can I only restore the backup to a machine with the exact same hardware (ie, another xps-m1330? ).. or, can i get away with restoring it on a similiar/comprable machine, but slightly more affordable machine (like a desktop)?  

I have a Pentium 4 acer desktop sitting around that I could try.. but, my *guess* is that that probably won't work, because P4 is a lot different than core 2 duo, right? 

Any advice much appreciated  :)  

kind regards, 
lauren

---

### Post by jerrrys on 2009-11-01
I also use clonezilla and if you want, you can download to another computer.  This should work, but never know till you try.  Also I use the HDD to HDD option and not the image backup so don't know about that...

---

### Post by seeker5528 on 2009-11-02
I have a hard drive that I some times put into other machines for troubleshooting types of things and normally it is able to boot in any computer I stick it in.

Also have upgraded motherboard/processors and what not many times with few issues.

Both of these things are similar to creating a clone from one system then restoring it to another.

One potential gotcha, which doesn't seem likely in your case is if the drive labeling scheme changes, hdX to sdX for example, which would require you to boot from a live disk to access the hard drive and change configurations to point to the correct places in some cases, theoretically the UUID stuff should save you from some of these types of issues.

If there is going to be a problem I would expect that most commonly it would be with video, if you had a customized xorg.conf on the old system that is incompatible with the new system or used a proprietary driver on the old system and have to change to a different driver on the new system. Some of these issues would not be different than you might get on a fresh install or if you changed video hardware in a desktop system.

Later, Seeker

---

