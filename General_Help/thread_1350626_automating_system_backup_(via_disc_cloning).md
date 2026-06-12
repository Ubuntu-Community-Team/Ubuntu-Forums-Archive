---
title: "automating system backup (via disc cloning)"
date: 2009-12-09
forum: General Help
---

### Post by Lukas666 on 2009-12-09
Hello!

My main hard drive is a 1TB class F1 Samsung boy. It has a twin brother which I use for full system backup. By backup I mean full system/all partitions cloning. No, I am not interested in RAID as the backup drive is being stored at a different location (and hooked up only for the time of the backup process).

Here is my ideal scenario:

1. System is off, I hook-up the drive via eSATA port
2. System starts, grub screen pops-up. I'd like to add an entry there, saying "boot-CD backup/cloning", which I select.
3. I get prompted to insert a CD disc (more about it below) and the system boots from the CD.
4. The CD is a special, tiny and and hand-crafted linux distro I would have to make. It knows my partition setup and starts the backup process (using "dd") with no questions asked.


Does my idea make sense? I want minimal user involvement:  just pop in a CD disc, press "enter" and go out have fun. The system should clone itself automatically, with no human interaction.

Now, how could I accomplish that? How difficult would it be to tweak GRUB and create a custom CD-based distro? "dd" part is easy and I can handle that. 

Or maybe a similar solution already exists?

I would appreciate all tips and hints how to make my dream work.

Thanks!!!

L.

---

### Post by audiomick on 2009-12-09
Hallo.
I haven't really looked into the topic, but you might be able get your backups done with clonezilla, or maybe rsync.

Update:
I just looked at this for the first time:
[http://en.wikipedia.org/wiki/Clonezilla](http://en.wikipedia.org/wiki/Clonezilla)

I think the live CD that is mentioned there is definitely what you want.

---

### Post by Lukas666 on 2009-12-14
> **audiomick said:**
> Hallo.
I haven't really looked into the topic, but you might be able get your backups done with clonezilla, or maybe rsync.

Update:
I just looked at this for the first time:
[http://en.wikipedia.org/wiki/Clonezilla](http://en.wikipedia.org/wiki/Clonezilla)

I think the live CD that is mentioned there is definitely what you want.

Thanks, you were absolutely right about clonezilla. With a few custom scripts I created a fully automated backup/cloning disc. The whole process starts without a single key hit and I even check the drives serial numbers, so it's not possible to do any damage on other machines.

If anyone is interested please send me a private message.

L.

---

### Post by Lukas666 on 2011-11-26
For those interested (I received many private messages) I am publishing my custom-ocs file. 

Enjoy.

---

