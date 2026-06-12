---
title: "RAID and Network?"
date: 2006-06-14
forum: General Help
---

### Post by ultralame on 2006-06-14
I installed Dapper for the first time- I did this when the disk I was running Debain Sarge off of died.

On the Debian system, I had a RAID 5 array with the /var and /home mounts.

After installing Dapper (which worked perfectly), I did the following:
  1) Booted into the Dapper Live CD.

  2) Mounted rw the Dapper disk and my two RAID partitions:
[INDENT] (Dapper /):   **mount /dev/hda1 /mnt/hda1**
 (Old /home): **mount /dev/md0 /mnt/md0**
 (Old /var):    **mount /dev/md1 /mnt/md1**[/INDENT]

  3) Moved the old data on the RAID /home and /var to subfolders, to avoid intereference with the new installation:
[INDENT]mkdir /mnt/md0/home.old; mv /mnt/md0/* /mnt/md0/home.old
mkdir /mnt/md1/var.old; mv /mnt/md1/* /mnt/md0/var.old[/INDENT]
       
  4) Copied the new /var and /home folder contents:
[INDENT]cp -a /hda1/home/* /mnt/md0
cp -a /hda1/var/* /mnt/md1[/INDENT]

 5) Updated /hda1/etc/fstab:
[INDENT]/dev/md1        /var            ext2    defaults,errors=remount-ro 0       1
/dev/md0        /home           ext2    defaults,errors=remount-ro 0       1[/INDENT]

 6) Rebooted into the new disk.

The system rebooted fine the first time, and the RAID volumes mounted.  But here's what happens:

FIRST PROBLEM:When I shudown or reboot, the system seems to hang after the processes shut down. After waiting several minutes with a blank screen I reset, and when it reboots it says that /dev/md0,md1 were not unmounted cleanly, and proceeds to run disk checks.  Then everything mounts cleanly.

SECOND PROBLEM: The network does not come up.  Running **/etc/init.d/networking start** causes an error.  I researched it and found that I needed to run:  **cp -r /etc/network /var/run**.  Then I needed to go to the Networking Admin panel (in Gnome) and activate the eth0 device, then run **/etc/init.d/network start**.

Now, I have not rebooted since (since I need this thing to work!) but I expect that both of these problems will continue.  I did not have the network problem before I moved /var to the raid system.

Any ideas?

---

### Post by ultralame on 2007-10-20
Just found something that seems to work:  vol_id

Can anyone confirm this is accurate?

Can I recreate my array using the UUIDs?

---

### Post by fjgaude on 2007-10-20
From my experience, vol_id and blkid produce the same UUIDs for devices.

Have never created an array using UUIDs but I will the next time around.

Good luck.

---

