---
title: "Cant read extra partitions in Windows 7?"
date: 2010-07-23
forum: General Help
---

### Post by bburrito on 2010-07-23
I have Ubuntu Linux installed on a hard drive in a seperate computer.  I want to transfer some stuff so I pulled the drive and hooked it up to my main machine.  I then installed Ext2Explore so I could read the drive.  I am able to read it now and see all of the folders but it appears that I am only able to see the main partition.  With the other partitions, I see them listed in the Media folder but I click on them and they are all empty.    Does anybody know how I can retrieve the data in these partitions?  

Thanks!

---

### Post by WorMzy on 2010-07-23
Generally speaking, if you want to move files from a Linux partition to a Windows partition, you boot into a Linux OS, mount the Windows partition, and copy files over from there. Windows has very limited support for Linux file systems, there's  ext2explore for ext2 (and possibly ext3) partitions, but I'm not sure if there's support for ext4 yet.

---

### Post by Ocxic on 2010-07-23
Put your drive back, and use share some folders on your windows machine. thats the safest way/easiest.

---

### Post by bburrito on 2010-07-23
Well, for whatever reason it appears that my linux box is seriously hosed.  It wont load X any more and when it gets to the user prompt, the screen is flashing in such a way that might cause a seizure.  Half the time I type anything in,  the machine doesnt respond.  If I tried to type my username in it ends up looking like  buio instead of bburrito.  I dont know whats wrong with it and I just want to get my data off the drive. Was hoping to just be able to do that from windows.

---

### Post by WorMzy on 2010-07-24
A liveCD/USB should work fine.

---

### Post by Mark Phelps on 2010-07-24
> **bburrito said:**
> Well, for whatever reason it appears that my linux box is seriously hosed.  
If it was OK before, you most probably corrupted the filesystem messing around with Ext2 -- since that does NOT support Ext4 filesystems.

> Was hoping to just be able to do that from windows.
The BEST way to recover files from a Linux filesystem is to boot from a LiveCD of a Linux distro.  That way, you can be sure that you can read the filesystem without danger of corruption.

---

### Post by CharlesA on 2010-07-24
There is no driver that will read EXT4 partitions (yet), the best they can do is read EXT3 partitions.

Your best bet would be to boot into Linux and mount the Windows partition then copy the files over to it from there.

---

