---
title: "Help with Btrfs snapshot please!"
date: 2011-05-04
forum: General Help
---

### Post by avongil on 2011-05-04
Hi everyone,

I formated a partition Btrfs and mounted it to the /home partition when installing. I wanted to make snapshots of /home in case I wanted to roll back some data.  It seems like I can only make snapshots of subvolumes. Is it possible to do what I want now?

Am I limited to doing this on a user level now? Should I have just made / the btrfs root and then made /home a sub volume???

Am I totally missing the boat? Sorry for the simple questions, but the documentation is a little lacking at this point in btrfs development!  Any help appreciated.

Label: none  uuid: 31fb6a1b-a822-4071-9c23-192e00d2a31d
    Total devices 1 FS bytes used 110.45GB
    devid    1 size 404.28GB used 113.04GB path /dev/sdb7

---

### Post by wilee-nilee on 2011-05-04
> **avongil said:**
> Hi everyone,

I formated a partition Btrfs and mounted it to the /home partition when installing. I wanted to make snapshots of /home in case I wanted to roll back some data.  It seems like I can only make snapshots of subvolumes. Is it possible to do what I want now?

Am I limited to doing this on a user level now? Should I have just made / the btrfs root and then made /home a sub volume???

Am I totally missing the boat? Sorry for the simple questions, but the documentation is a little lacking at this point in btrfs development!  Any help appreciated.

Label: none  uuid: 31fb6a1b-a822-4071-9c23-192e00d2a31d
    Total devices 1 FS bytes used 110.45GB
    devid    1 size 404.28GB used 113.04GB path /dev/sdb7

I have no experience with this partitioning schema, but with a quick look at google it looks as though clonezilla may work with this not sure which version though hopefully others will chime in.

---

### Post by avongil on 2011-05-05
Nope, I don't want to use a traditional backup utility. I want to make file system snapshots just like ZFS does. This is pretty awesome stuff, Google ZFS snapshot. 

Has anyone played with Btrfs yet?

---

### Post by avongil on 2011-05-05
Success!  A dream come true, entire file system snapshots have come to Linux!!! :D

Ok, so they must be a subvolume. The btrfs wiki describes it pretty well, I was just not executing it correctly.  I really wish I would have made my root partition btrfs, then I could have easily made /home a subvolume.  Not a huge deal,  not running a server here, I only have one user.

I will log in as root, rename the user folder, then create a sub volume with the original user name, change ownership then copy all the stuff back in it. Then I will make snapots with a script, on boot, hourly and shutdown. Will post results soon.  Thanks.  FreeBSD got me hooked on ZFS snapshot, they are so so sweet. Hopefully Btrfs will be able to export them one day over SSH.

---

