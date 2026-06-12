---
title: "mdadm RAID configuration : failed boot on restart"
date: 2009-06-30
forum: General Help
---

### Post by sjalloq on 2009-06-30
Hi there,

I'm new to Ubuntu and Linux admin in general.  I've used Unix/Linux systems for a long time but never had to get down and dirty if you know what I mean.

I have an old machine which consists of an AMD Sempron 1.1GHz and an Abit NF7 mobo.  I have a single HDD as my boot drive and have just configured two 500GB Samsung drives in a RAID-1 setup.

The OS was previously 8.10 and I upgraded to 9.04 at the weekend.  I have since been working out how to set up software RAID and ended up following the guide at [http://linux-raid.osdl.org/](http://linux-raid.osdl.org/) using mdadm.

The drives I was using for my data partition were from an old FreeNAS or ReadyNAS that used GPT.  I managed to create a single partition on each drive and then use mdadm to create a single mirrored RAID array which I called /dev/md0.

All was well until I restarted my machine (which I am trying to run as a headless server).  The boot stopped with the following on the screen:


> 
* Checking file systems...
fsck 1.41.4 (27-jan-2009)
fsck.ext3: No such file or directory while trying to open /dev/md0
/dev/md0:
The superblock could not be rad or does not describe a correct ext2 filesystem.  If the device is valid and it readlly contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternative superblock
    e2fsck -b 8193 <device>

fsck dies with exit status 8

* File system check failed.
A log is being saved in /var/log/fsck/checkfs if that location is witeable.
Please repair the file system manually.
* A maintenance shell will now be started.
CONTROL-D will terminate this shell and resume system boot.
bash: no job control in this shell
root@ubuntu-server:~#So what did I do wrong and what is my next move?  I remember getting lots of warnings that fsck can't read GPT partition tables so is that what has gone wrong.

Thanks, Shareef.

---

### Post by ronparent on 2009-06-30
There appears to be a bug in 9.04 affecting both 'fakeraid' and software raid that in certains instance will not allow you to boot to a raid or, for that matter, allow automounting. The bug is probably hardware related and doesn't affect everyone or in the same way. You might find a work around for the software raid in the server section of this forum. This could account for your problem as the raid is not recognized at boot.

---

