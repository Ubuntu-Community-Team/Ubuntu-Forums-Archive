---
title: "Is RAID 1 Possible after install?"
date: 2006-05-09
forum: General Help
---

### Post by JCorrea920 on 2006-05-09
I installed Ubuntu 5.10 Breezy Badger similar to the [Ubuntu Perfect Setup]("http://howtoforge.com/perfect_setup_ubuntu_5.10") except I ran installer without the server option so X windows was installed. I partitioned slightly different with a 2 GB swap I then I installed VMWare Server e.x.p and Windows 2k3 Enterprise SP1 on top of that. I have a Dell PowerEdge 1420 Single Intel Xeon and two 160GB SATA Hardrive which I would like to setup RAID 1 on. Is this possible after install?

I found a newbie who posted a how to on RAID at: [http://www.humandoing.net/blog/33/raid-on-linux-ubuntu-510 ]("http://www.humandoing.net/blog/33/raid-on-linux-ubuntu-510")

Would this work without lossing my configuration already? The code from this how to listed above basically looks like this:

```

sudo cfdisk /dev/sda
sudo cfdisk /dev/sdb

sudo modprobe raid1

sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sda1 /dev/sdb1

sudo cat /proc/mdstat

sudo mdadm --misc --detail /dev/md0

sudo mkfs.ext3 /dev/md0

sudo mkdir /backup

sudo mount /dev/md0 /backup

df -k

sudo vi /etc/fstab

# Add this line to /etc/fstab
# /dev/md0        /backup         ext3   defaults,errors=remount-ro      0       2
```

I am new to Ubuntu, but have been working with Fedora Core 4 for about 8 months. Any help would be greatly appreciated.

Jorge

---

### Post by fake123 on 2006-05-09
im pretty sure it has to be done before you install the OS
seeing how it installs the data on two drives at once

---

### Post by JCorrea920 on 2006-05-09
fake123,

So even though the configuration is done after base system install by choosing RAID1 partitions it will write on both disks at install? I didn't know that. Which way would you recommend?

1) [https://wiki.ubuntu.com/Installation/RAID1?highlight=%28RAID%29%7C%281%29]("https://wiki.ubuntu.com/Installation/RAID1?highlight=%28RAID%29%7C%281%29")

2) [http://www.humandoing.net/blog/33/raid-on-linux-ubuntu-510 ]("http://www.humandoing.net/blog/33/raid-on-linux-ubuntu-510")

or

3)  (a) [ http://www.howtoforge.com/perfect_setup_ubuntu_5.10]("http://www.howtoforge.com/perfect_setup_ubuntu_5.10")

with

    (b) [http://www.howtoforge.com/linux_software_raid]("http://www.howtoforge.com/linux_software_raid")

And to top it off would you recommend:

1) [http://www.howtoforums.net/viewtopic.php?t=5]("http://www.howtoforums.net/viewtopic.php?t=5")

2) [http://www.ubuntuforums.org/showthread.php?t=154022]("http://www.ubuntuforums.org/showthread.php?t=154022")

or

3) [https://wiki.ubuntu.com/VmWare?action=show&redirect=VmWareWorkstation]("https://wiki.ubuntu.com/VmWare?action=show&redirect=VmWareWorkstation")

Jorge](*,)

---

### Post by lha on 2006-05-10
You _can_ set up raid after install, I've done it myself, too. Do you wish to 
a) convert your system to a root-on-raid system or 
b) add two new drives that will be set up as a raid1 device?

a) See /usr/share/doc/mdadm/rootraiddoc.97.html. (I found it amusing that people ask for good raid-how to when they already have it in their hands. :))
b) Those instructions look ok.

---

### Post by JCorrea920 on 2006-05-10
> You _can_ set up raid after install, I've done it myself, too. Do you wish to
a) convert your system to a root-on-raid system or
b) add two new drives that will be set up as a raid1 device?

I already have the OS on sda and currently have a sdb that hasn't even been formated. All this hardware came with the server. I would like to create RAID1 mirror without loosing my data and software I have currently installed on the system: ie. VMWAre, Windows2k3 Enterprise SP1 on top of that.

> a) See /usr/share/doc/mdadm/rootraiddoc.97.html. (I found it amusing that people ask for good raid-how to when they already have it in their hands. )

I will take a look at those instructions. My dilemma is that the filesystem I chose for my OS install on all three partitions (/boot, /  , /var) is ext3 and of course the /swap is linux-swap. All documentations that I have read so far suggests that it should be RAID, Linux-RAID Autodetect (FD), or something similar in order for mdadm to detect and link to each other. Please tell me I am greatly mistaken. Otherwise before I create the partitions and format the second hard drive ext3. If there is no way around this I will need a tool to convert ext3 to FD without loosing data. See my dilemma? :-|

---

### Post by lha on 2006-05-10
The idea is to make those Linux raid autodetect partitions on sdb, create degraded md devices (raid1 devices with the other drive missing), duplicate your current install to new md devices and boot from raid.  Then go on by formatting sda in a similar way you formatted sdb, add partitions from sda into md devices and wait until your drives are synced. Finally, reboot and pray it worked. :) Remember to back up important stuff. Installing directly to raid is easier than converting a working system into raid, but if you have put a lot of time to get your current settings, it may be worth the hassle to the conversion.

---

### Post by mjziegle on 2006-05-10
To clarify the above posters comments.  Here are some rough instructions.  I have to do this myself in a couple days.  I'm switching from a single 160GB to a mirrored 400 GB setup.  If you have patience I can post more details with exact commands in a few days after I complete the project.

1.  Partition your new disk as a Raid autodetect making your partitions the same as you did on you original install disk.  DO NOT raid your swap partition, but make sure you raid / and /boot if applicate.

sudo fdisk /dev/(new disk)
use the menus it's easy enough

2.  Create a degraded array

mdadm --create /dev/md0 --level 1 --raid-devices=2 missing /dev/(newdisk)

3.  Make your filesystem (ext3 in this case)

sudo mke2fs -j /dev/md0

4.  Mount the filesystem and copy data over

sudo mkdir /raid_temp
sudo mount /dev/md0 /raid_temp
copy your entire directory structure over to /raid_temp

5.  Edit your fstab to include the new raid array

/dev/md0   /boot   ext3    errors=remount-ro       0       2

6.  Edit /boot/grub/menu.1st to boot off your raid

7.  Unplug your original drive and reboot and see if you system comes up.  If it comes up on the new drive your home free.  Otherwise check 1-6 again.

8.  Plug the original drive back in and reboot

9.  Partition the original drive as raid autodetect

10.  Add the original drive to the raid array

mdadm /dev/md0 -a /dev/(original drive)

11.  Watch your raid rebuild itself 

cat /proc/mdstat

12.  My healthy raid looks like this

cat /proc/mdstat
Personalities : [raid1]
md0 : active raid1 hda1[0] hdc1[1]
      117185984 blocks [2/2] [UU]

unused devices: <none>

The key here is the [UU]

Good luck.

-matt

---

### Post by lha on 2006-05-10
[QUOTE=mjziegle]1.  Partition your new disk as a Raid autodetect making your partitions the same as you did on you original install disk.  DO NOT raid your swap partition, but make sure you raid / and /boot if applicate.[/QUOTE]


I must disagree with that. If swap isn't on a raid1 device, system will crash if one drive fails. Of course, if one wants to only protect data on drives from disk failure, not putting swap on raid *may* be justified because swap performance will be a bit better. But I want my computer to keep going if I lose a drive, so I have my swap on raid.

---

### Post by JCorrea920 on 2006-05-11
So I tried the above broke my server and had to start from the beginning. So After many attempt at reinstalling Ubuntu I finally got the RAID1 Configuration from the install CD. Woo Hoo. Now All I have to do is test it by removing a hard disk and alternating the same effect. Thank a million all of you.

---

### Post by mjziegle on 2006-05-12
[QUOTE=lha]I must disagree with that. If swap isn't on a raid1 device, system will crash if one drive fails. Of course, if one wants to only protect data on drives from disk failure, not putting swap on raid *may* be justified because swap performance will be a bit better. But I want my computer to keep going if I lose a drive, so I have my swap on raid.[/QUOTE]

Swapping on a raid partition isn't always stable.  If it works for you then great.  The kernel automatically will stripe multiple swap partitions.  The pros of swapping are continuous uptime.  The cons being possible instability.  Disk failure requires downtime anyway, unless you have hot spares, but that's besides the point.  

-matt

---

### Post by Frank-Hamersley on 2006-10-27
G'day Matt,

Your post may be the answer to a problem I am suffering!

I have posted to a General forum thread about disk failure crashing a Dapper Server 6.01.1.  I am now wondering if the fact that I have mirrored the swap devices is the root cause of the crash rather than a weakness in md or the kernel!!!

Picking up on your comment "The kernel automatically will stripe multiple swap partitions" it seems maximum reliability would be achieved by having a discrete swap partition on each disk without having the md driver involved.

Is this then the best practice arrangement for the system disks?  Do I have to inform the kernel that there is multiple swap partitions on offer?

Cheers, Frank.

---

