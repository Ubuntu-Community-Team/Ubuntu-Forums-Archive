---
title: "netbook will not boot - filesystem error"
date: 2010-01-12
forum: General Help
---

### Post by marie-p on 2010-01-12
Hi,

I re-installed ubuntu netbook remix on my eeepc netbook last week and it was working just fine, until this morning it refused to boot.

When I turn it on, I get the eeepc screen as usual (and I can enter setup), then it starts loading ubuntu and it does a filesystem check. 
When it stops first I get a message saying
Filesystem check failed
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.

It then stops doing anything.
If I do control-D, it tries again and then gives me a long message. I wont type all of it here, but some of the things it lists are 'problem activating swap' (a few times), 'Duplicate of bad block in use!' 'UNEXPECTED INCONSISTENCY: RUN fsck MANUALLY' 'mountall: fsck /home (802) terminated with status 4'
'mountall: Filesystem has errors: /home'

What does it mean?
What should I do?

---

### Post by marie-p on 2010-01-12
I forgot to specify, I have ubuntu netbook remix 9.10
I originally installed the 9.04 then upgraded to 9.10

My eeepc has two flash memory drives, one of 4GB and one of 16GB. I think it was meant to have the 4GB for the system and 16GB for storage, but I was having a hard time with that during the installation, so I put the system on the 16GB section and formatted the 4GB. I was not able to figure out exactly where that 4GB was, but my available storage was over 16GB, so I figured that it was recognized as part of my storage.

Would re-installing ubuntu be a solution? (I would loose the work I've done this week, but I guess it could be worst)

---

### Post by marie-p on 2010-01-12
update: 

I tried to do fsck (before hitting control-D, since I could still type commands then) and it gave me a warning that running the fsck on a mounted file system could do some damage, so I opted not to continue. 
Then it said:

/dev/sda1 contains a file system with errors, check forced.
Pass1: Checking idodes, blocks, and sizes

Running additional passes to resolve blocks claimed by more than one inode...
Pass 1B: Rescanning for multiply-claimed blocks
Multiply-claimed block(s) in inode 48034: 1188414 334368
Multiply-claimed block(s) in inode 48063: 118814
Multiply-claimed block(s) in inode 64005: 334368
Pass 1C: Scanning directories for inodes with multiply-claimed blocks
Pass 1D: Reconcilin multiply-claimed blocks
(There are 3 inodes containing multiply-claimed block(s), shared with 2 file(s):
/marie/.cache/notify-osd.log (inode #64005, mod time Fri Jan 8 13:07:52 2010)
/marie/.pulse/2135c35ce2b4df22fdf66b54b457776-default-sink (inode #48063, mod time Fri Jan 8 12:54:52 2010)
Clone multiply-claimed blocks(y)?


What should I do now?

---

### Post by marie-p on 2010-01-12
update:

since the system was not really giving me an option regarding whether I wanted to proceed or not, I proceeded and it seems to have fixed the problem with the filesystem.
I reloaded and it booted normally.

But how did this happen?
Is there anything I can do to make sure it doesn't happen again?

---

