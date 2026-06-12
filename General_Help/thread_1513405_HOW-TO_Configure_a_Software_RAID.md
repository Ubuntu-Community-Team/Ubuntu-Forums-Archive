---
title: "HOW-TO Configure a Software RAID"
date: 2010-06-19
forum: General Help
---

### Post by nineg50 on 2010-06-19
I thought I would pass on my experiences configuring a software raid in 10.04.  All of this information (of course) is available across the forums and in the wiki, but I thought I'd assemble them in one place.

[first, the wiki was by far the most help:]("https://wiki.ubuntu.com/Raid"), and it got me 95% of the way there.

Also these 2 threads helped me figure out how to solve the rest:

[http://ubuntuforums.org/showthread.php?t=1319215]("http://ubuntuforums.org/showthread.php?t=1319215")

[http://www.linuxforums.org/forum/debian-linux-help/90623-mdadm-array-disappears.html]("http://www.linuxforums.org/forum/debian-linux-help/90623-mdadm-array-disappears.html")

My setup is 4 1.5 TB SATA drives (I'm building a media jukebox, and for how long it's going to take to rip all my movies I want some redundancy!).  

From the wiki I found out that the RAID controller on my motherboard really isn't a hardware controller, so it's software raid for me.

The drives are /dev/sdb /dev/sdc /dev/sdd and /dev/sde and the RAID level I'm using is 5.  

**Create the RAID /dev/md0 using mdadm**

mdadm /dev/md0 --create --auto yes -l 5 -n 4 /dev/sdb /dev/sdc /dev/sdd /dev/sde

**Create a filesystem on the RAID **(I used ext3 after being scared away from ext4 by some bug reports)

mke2fs -t ext3 /dev/md0

**Make a directory and mount the RAID:**

mkdir /raid
mount /dev/md0 /raid

However, the RAID disappears upon reboot.
 
**to Fix:**

mdadm --assemble /dev/md0 /dev/sdb /dev/sdc /dev/sdd /dev/sde 

reassembles the drive and it can then be mounted

mdadm --detail --scan >> /etc/mdadm/mdadm.conf will make it so the RAID is assembled upon reboot.

**edit /etc/fstab so the the special device /dev/md0 is mounted at boot time:**

cat >> /etc/fstab
     /dev/md0        /raid          ext3    defaults        0       0

---

### Post by runesvend on 2010-06-20
Thank you very much for this short and concise thread on how to get a RAID array up and working. I've been reading threads for the past two hours, and this thread sorted out a lot of confusion.
It looks pretty simple, I must say! I will be trying this with RAID-1 soon, wish me luck :) (though, hopefully, that's not needed!).

---

### Post by runesvend on 2010-07-10
I have successfully gotten RAID-1 up and running using this guide, and [https://raid.wiki.kernel.org/index.php/RAID_setup#Create_RAID_device]("https://raid.wiki.kernel.org/index.php/RAID_setup#Create_RAID_device"), was quite helpful as well.

I used the *--metadata 1.2* option and a newer mdadm version available from here: [https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/495370/comments/12](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/495370/comments/12)
With this setup I don't need to add anything to /etc/mdadm/mdadm.conf, the RAID array is automatically detected and assembled at boot:

```
rune@runescomp:~$ dmesg | grep md
[    4.878559] md: bind<sdc1>
[    4.964741] md: bind<sdb1>
[    4.970658] md: raid1 personality registered for level 1
[    4.970798] md/raid1:md1: active with 2 out of 2 mirrors
[    4.970821] md1: detected capacity change from 0 to 999202443264
[    4.971881]  md1: unknown partition table
[    5.579426] EXT4-fs (md1): mounted filesystem with ordered data mode. Opts: (null)

```

Also, the "unknown partition table"-message shouldn't matter: [http://marc.info/?l=linux-raid&m=125797242110594&w=2]("http://marc.info/?l=linux-raid&m=125797242110594&w=2")

---

