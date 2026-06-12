---
title: "How to automount Partitions in Karmic"
date: 2009-11-14
forum: General Help
---

### Post by harishgayatri on 2009-11-14
Hi guys/girls,

I got a new problem

How am I supposed to automount my partitions automatically during startup.

I tried NTFSconfig but didnot have any luck with that.

Please Help me out

---

### Post by Earwicker on 2009-11-14
Yes, I too would like to know the answer to this. There's a setting I think in user permissions for auto mounting... but it doesn't seem to make any difference.

---

### Post by Greenwidth on 2009-11-14
I like MountManager (in the repos):

sudo apt-get install mountmanager

be careful though :)

Option to mount at startup is halfway down the general tab.

---

### Post by quixotic-cynic on 2009-11-14
See if [http://ubuntuforums.org/showthread.php?t=57685](http://ubuntuforums.org/showthread.php?t=57685) helps.

---

### Post by kjohri on 2009-11-14
You can edit the /etc/fstab file. The following link tells how to automount Windows partitions under Linux.

[http://www.softprayog.in/troubleshooting/linux/win_partition_mount.shtml]("http://www.softprayog.in/troubleshooting/linux/win_partition_mount.shtml")

---

### Post by Elcid247 on 2009-11-21
well i've written 2 HowTos about this and there u go

[New Method]("http://o-saad.blogspot.com/2009/11/better-automount-rules-in-karmic.html")

[Old Method]("http://o-saad.blogspot.com/2009/10/automount-in-karmic.html")

both work like a charm for me, hope they help :D

---

### Post by oldfred on 2009-11-21
In my fstab to prevent everything from being executable I made this my entry:

UUID=44332FD360AA9657                      /home/fred/shared  ntfs-3g      defaults,rw,noexec,nosuid,locale=en_US.UTF-8,fmask=0111,dmask=0000          0  0

---

