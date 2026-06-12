---
title: "this is why im done with vista"
date: 2009-08-06
forum: General Help
---

### Post by Sylver06 on 2009-08-06
Alright, so its time for me to throw vista out the window (lol). After an unexpected 5 sec flood of very harmfull trojans that just about destroyed the OS, booting it, my recovery disc wont work and my restore points were all erased. But i do have some very crutial information and files id like to keep or restore that are still on my hardrive ( movies and pictures realy). Now before i compleatly wipe the disk and install ubuntu, is there a way that i can either mount the hard drive trying ubuntu, install a partition within windows through ubuntu or something along the that line?

and no i cant realy take it in to be fixed cause i live in the middle of no were and town is a ways away and im making the plan of changing to ubuntu for good:P

help please?

---

### Post by P4man on 2009-08-06
its much easier than that. If you download the ubuntu, burn it to a cd (or make a USB stick), you can just boot from the cd (/stick) to try it out. won't be as fast as when installed, and some things won't be available, but its lets you test  without changing anything to your computer.

---

### Post by Sylver06 on 2009-08-06
Thats just what i originaly did to see if that would be my solution, i am currently trying ubuntu on this laptop and ive had ubuntu put on my other systems, the only problem is that trying ubuntu will not let me acces my hardrive because it wont let me mount it, and so far no tutorials ive looked up have been sucessfull. I want to be able to open it and copy what files i need onto a portable hard disk and start fresh

---

### Post by Paddy Landau on 2009-08-06
> **Sylver06 said:**
> ... ubuntu will not let me acces my hardrive because it wont let me mount it
We need to know how you tried to mount it, and what error messages you received. Also tell us whether it was from a Live CD.

---

### Post by Sylver06 on 2009-08-06
Well to save myself the headache, i just came across my laptop hardrive addapter so i can plug it into another system, from there i can wipe it and install ubuntu, now i just have to figure to mount the second hardrive in ubuntu which i heard is simpler

---

### Post by burmanabhay88 on 2009-08-06
> **Sylver06 said:**
> Well to save myself the headache, i just came across my laptop hardrive addapter so i can plug it into another system, from there i can wipe it and install ubuntu, now i just have to figure to mount the second hardrive in ubuntu which i heard is simpler

Mounting is not a very tedious task.
you can use the mount command with the -o force option to mount any of your disks.
However if you're "installing" and not live booting ubuntu, i'd recommend you use "Disk Manager". You don't need to type a single command, It's got a gui. And in case it says cannot mount, just select 'ntfs-3g' as the driver, and use force mount option.
Do tell me if this works for you.

---

### Post by P4man on 2009-08-06
the reason it wont mount, is probably because the filesystem is "dirty". That happens when windows doesn't shut down properly or something messed it up. If windows isn't messed up too badly, the easiest is to boot it, and shut it down again (assuming it will still shut down properly). Won't hurt to run a chkdsk on it while you're at it.

If thats not possible, you can force the mount with the -o option, but its risky.

---

### Post by Sylver06 on 2009-08-06
Well what do you know, i changed CD for ubuntu to the original from the one i had downloaded, i got a message from a friend saying he had a similar problem and the reason was the disk he burnt had a fault in it, and after switching CD's with the original it enabled him to install and access his hardrive, strange i know but im relived to now find my files, well thanks for all of your support, your advice helped alot and i guess i just lucked out this time :P well its time to start a long slow transfer process of over 100gigs of vids pics and files i wanted and start fresh with ubuntu. thanks guys.

---

### Post by Sylver06 on 2009-08-06
but now that i think of it, it very well could be because it was ''dirty'' because ive had similar  problems with windows after the system crashes and i booted from the second hardisk with xp and i couldnt access the first hardrive,and the by doing the -o command it did nothing but freeze the system and it rebooted ohh well guess i wont know. thanks again tho

---

