---
title: "Ubuntu 10.04 Partition Expansion."
date: 2011-06-26
forum: General Help
---

### Post by Snowboi on 2011-06-26
Hey ubuntu community :)

I came to you guys with a problem :S
i have a duel boot desktop computer running ubuntu 10.04 Lucid Lynx (32 bit)
i have a 30gb partition for ubuntu on my DATA hard drive (drive d)
and i have a windows partition on my c drive (taking up the whole c drive)

problem is this is my first time using gparted and i running from a live cd right now i just wonder how can i expand the partition so that ubuntu is using the whole hard drive as apposed to only the 30gb

Here's the data for /dev/sda3 (ubuntu partition)

Used - 30.17gb
Unused - 82.68gb

i wanna resize my ubuntu partition so that i can use the whole drive 

basically i want it to look like this
Used - 112.85gb

Note : The unused 82.68 has nothing on it so its free to resize.

below i have a picture of what im talking about
[IMG]http://img155.imageshack.us/img155/8383/screenshotmet.png[/IMG]
What do i enter for free space preceding and free space following and new size if i wanted to do that.

also here is how the the entire partition chart looks like
[IMG]http://img864.imageshack.us/img864/442/screenshot1rh.png[/IMG]

---

### Post by Snowboi on 2011-06-26
bump :-\"

---

### Post by DawieS on 2011-06-26
Hi, it seems as if you have a Wubi installation, since the ntfs file system is native to Windows, and does not cater for the all of the file attribute requirements of Linux.

If it is only usable space you are after, you can probably adjust some settings from within Windows, since the /dev/sda3 (DATA) partition already runs to almost the end of the disk, as shown by your screenshot of GParted. (Sorry, I don't know Wubi, or the limitations thereof).

If you want to migrate your Wubi installation onto its own partition, I recommend the following steps:
1) Shrink the DATA partition to about 50 000 MiB.
2) Create a new primary ext4 partition in the unused space (Leave just enough unused space for Swap space at the rightmost end to be created later, the same size as your RAM).
3) Migrate your Wubi Ubuntu installation over to this new ext4 partition (Search for the many how-to threads on the forum).
4) Delete the remainder of the DATA partition, and expand the new Ubuntu ext4 partition to the left, into all of the unused space.
5) Create a Swap partition at the rightmost end.

If you have not yet put in a lot of time into customizing your Ubuntu installation, it will probably be quicker to delete the DATA partition (after backing up your data files in it), then create a new ext4 and Swap partition, then do a fresh install from a Live CD or USB stick.

---

### Post by oldfred on 2011-06-26
HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

There still are limits. If you are using Ubuntu a lot you should consider creating partitions.
Resize wubi - bcbc
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Even the designer of wubi expects you to convert to partitions:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

### Post by Snowboi on 2011-06-27
> **oldfred said:**
> HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

There still are limits. If you are using Ubuntu a lot you should consider creating partitions.
Resize wubi - bcbc
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Even the designer of wubi expects you to convert to partitions:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

Alright im trying this ill msg the results soon :) ty

I don't even use windows lol, i hate it so much i wanna delete it but sadly i only use it for photoshop and itunes >.<

---

