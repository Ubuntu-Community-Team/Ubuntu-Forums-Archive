---
title: "Partioning Question, dual boot, shared data?"
date: 2011-07-10
forum: General Help
---

### Post by Lumsdoni on 2011-07-10
I hope someone can either help me, or point out that what I want to do is ill advised etc.

I have recently switched to Linux from Windows and am more than happy to experiment and play around with settings before I start using my netbook full time for work.

What i wanted was...

A dual boot system, so I can experiment with various distros, but to keep all my data on a third partition so I can format the other distro partitions in the future without losing data.

Currently, I have set up:

Ubuntu 11.04 Unity on sda1 - 250GB
then I dual booted with Linux Mint 11 to test - sda6. This took 50GB so Ubuntu was on 200GB

I then shrunk the Ubuntu partition to 50GB and created an ext4 partition sda3 out of the unallocated space.

ALl is fine so far. 

My question is, can I set the home folder documents,video, music,pictures folders etc to be stored on the sda3 partition  and have it so that both DISTROS default to that location or will that cause issues? So I suppose I'm saying can I move the home directory?

AM I better off just creating new folders on the data partition and simply not using the folders in my home directory.

---

### Post by macaholic on 2011-07-11
The problem with sharing the /home/(username) directory is that there are many hidden configuration directories in there that will not mix well with the two distros. If you just want to share media files and such, I would recommend either creating a /home partition and using two different user names on the two distros, and then keeping a /home/media directory they both can access for all the folders you mentioned. Doing so would avoid the conflicting configuration files while still allowing you to access your media files on both distros.

---

### Post by decrepit on 2011-07-11
I have a seperate "data" partition, that all OSs can access.
Then the home directories only contain stuff for that OS.

Means you can mess around with different OSs without worrying about data.

---

