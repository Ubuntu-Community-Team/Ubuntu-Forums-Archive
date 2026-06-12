---
title: "Why does 9.10 change /dev/hda to to /dev/sda?"
date: 2009-12-03
forum: General Help
---

### Post by isee on 2009-12-03
I've read the difference between hda and sda has to do with the disk type, IDE etc., but of course I have not changed disk drives.  I've done two installs of 9.04 and 9.10 for a dual boot, and it changed both times.

I'm trying to configure partitions, and am going to delete the 9.10 partition.  Will the sda or hda designation matter with only 9.04 installed?

I've seen now that when I boot with GParted 4.4 the drive is labeled hda.  Using GParted when booted into 9.04 is still sda though.

---

### Post by gdonwallace on 2009-12-03
That does seem odd.  You are correct, hda refers to hard drives attached with the older ribbon cable and is considered an IDE (or EIDE) drive.  The sda designation is for hard drives connected through a sata cable.  Also, sda can be used for certain types of USB devices or cd-roms that use sata connections.  

I don't understand why the drive would change like that.  Since it sounds like you are doing a duel boot you might check the fstab file in /etc under both 9.04 and 9.10 and see how the hard drive is setup.  Also mtab in /etc shows the currently mounted hard drive as well.  Make sure both are reporting the same thing.

It sounds like with either hda or sda Ubuntu is running, so in theory it should not matter.  But as to the why it reports a different type of hard drive under each; that is not something I have heard of.

---

### Post by jocko on 2009-12-03
The reason (if I understand it correctly) is that most of the (p)ata drivers were switched to the same driver architecture as sata and scsi a few years ago, leading to the change from hdX to sdX. Some drivers were not migrated at the same time as the rest, so they stayed as hdX.
Apparently your ata driver was finally upgraded in the kernel sometime between the jaunty and karmic releases, which is why you don't notice it until now (I think mine changed between dapper and edgy or feisty...).

---

### Post by isee on 2009-12-03
Im sorry.  It's the version of GParted I was using.  I've got the 9.04 LiveCD in and it indicates my drive is sda.  When I wrote down my drive info, I was booted with GParted LiveCD 0.4.4 which I guess still uses the hda label, so only though the subsequent install of 9.10 changed it.

Good to know as I've buggered up my Grub2.

---

### Post by isee on 2009-12-03
Thanks very much for your help! ):P

Now I know why the labels are different.

---

