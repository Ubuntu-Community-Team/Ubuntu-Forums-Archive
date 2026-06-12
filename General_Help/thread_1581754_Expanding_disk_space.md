---
title: "Expanding disk space"
date: 2010-09-25
forum: General Help
---

### Post by varunit on 2010-09-25
Hello friends,I have installed ubuntu 10.04 using wubi installer..
I am dual booting ubuntu with windows 7.
I have alloted 8 gb of disk space while installing ubuntu.

My first question is how can i know where the installed applications are stored and how much memory they occupy and how much free space is available out of the alloted 8gb.?


My second one is now i have to install RAD 7.5 which requires 3.5 gb of free space..How can i expand the disk space without the need of reinstalling ubuntu..

Please help me in this issue guys...

---

### Post by Lateralis on 2010-09-25
Hi Varunit. 

There are several ways of determining how much space has been used.  If you click on System -> Administration -> System Monitor then look under the "File System" tab.  At the top of the list you should see a device with '**/**' listed in the second column ("Directory").  This is your main file system and in your case should be 8 GB in total size.  You will see the amount of spare space you have.  

Another way is to fire up a terminal (Applications -> Accessories -> Terminal) and type in 

```

df -lh

```

The first line (pertaining to mount point '**/**') will say how much of the drive has been used up as  percentage.  

Secondly, expanding a Wubi installation is difficult.  It is possible, but tricky.  There is a link to the Wubi installation guide in my signature.  On the linked page are instructions on how to expand the Wubi virtual disk, or migrate it to a standalone partition.  

I would also say that if you are now comfortable with Ubuntu and like what you see, I'd suggest installing Ubuntu to a dedicated partition.  Wubi installations are great for trying out Ubuntu - check that you like it, that the hardware works OK etc... - but doesn't compare to having it installed properly.  Aside from anything else a proper installation will run quicker, and it is easier to do system upgrades.    

Hope this helps. :)

---

### Post by varunit on 2010-09-25
Thanks a lot [Lateralis ]("http://ubuntuforums.org/member.php?u=481237"):)..
I will try installing ubuntu with much more free space like 25 gb..:)

---

### Post by Lateralis on 2010-09-26
Cool.  Good luck!

Of course I should mention all of the usual boring (but important!) stuff like make sure you have backups of all of your important data saved to some external medium such as USB flash drive, external hard drive, CDs or DVDs.  :)

---

