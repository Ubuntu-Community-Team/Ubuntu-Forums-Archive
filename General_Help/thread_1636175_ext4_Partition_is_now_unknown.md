---
title: "ext4 Partition is now unknown"
date: 2010-12-02
forum: General Help
---

### Post by hedggie on 2010-12-02
I attempted to shrink my ext4 storage partition with KDE partition manager. Because it was taking so long with out any progress I hit cancel, and then it said finishing current task or something like that. I left it like that for a good 20 minutes, so I force quit. Now I have an "Unknown" partition and 20gb of unallocated space. I attempted to use testdisk to recover it, but I am a serious ubuntu n00b and don't know what I'm doing. What should I do in testdisk to recover my files?
Thanks a bunch!!

---

### Post by ivan-wells on 2010-12-05
I attempted to shrink my /dev/sda1 ext4 partition with KDE partition manager (using MEPIS live CD) yesterday. I have only used GParted before. I waited hours and it was clearly stuck. I came across your post while Googling for help!

Using GParted I can still see /dev/sda1 but with an unknown file system. Using testdisk [Intel] [Analyse] [Quick Search] I could see the /dev/sda1 partition with an ext4 filesystem but when using P to list files testdisk reported that the filesystem appeared damaged. I pressed Enter to continue followed by a [Deeper Search]. This listed a lot of old partition information but after a little time searching I found the files and successfully copied them to another partition. Hope this helps.

I guess there may be a way to recover the partition itself.  I may try another day as I have a multiple Linux boot system and do not need the space yet.

Update: recovering the partition was harder than I expected and resulted in a system that would not boot. At one stage loss of my other working partition used for the backup!

About to do a clean install as I have recovered all the files that I need to an external hard drive. First time I had used testdisk so helpful links below in case of help to others:

For GParted Live CD/USB/PXE/HD (which includes testdisk)

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

For instructions on testdisk

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

