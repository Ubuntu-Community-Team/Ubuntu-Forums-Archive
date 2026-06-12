---
title: "disk usage - drive is filling up"
date: 2010-11-22
forum: General Help
---

### Post by smeggs on 2010-11-22
I've just noticed, via the system monitor, that my drive is being filled up when there aren't any programs running (that I'm aware of). /dev/sda1 is filling at a rate of .1 GB every 3-5 seconds or so. I've got about 640 GB left. another weird thing, it's showing this increase over three locations - /dev/sda1, /home/user/.Private, and /var/lib/ureadahead/debugfs.


There were a couple external drives mounted on another user, I unmounted them and logged the user out and the usage went back down to about 205 GB but the data amount is counting back up again, and the system is running sluggishly. I can't tell what's running that is doing that. Is there a way to check which application is using the disk?

---

### Post by paulsarmiento on 2010-11-22
Hi smeggs,

In ubuntu, you could try 'iotop' utility program to get the program that hogs your disk i/o resource. After getting all your information then you can assess if you really need that program. 

I'm quite of a linux oldie, if you really wanted to get it the linux way, then you have to do basic linux utils, vmstat and iostat.


Paul

---

### Post by smeggs on 2010-11-22
> **paulsarmiento said:**
> Hi smeggs,

In ubuntu, you could try 'iotop' utility program to get the program that hogs your disk i/o resource. After getting all your information then you can assess if you really need that program. 

I'm quite of a linux oldie, if you really wanted to get it the linux way, then you have to do basic linux utils, vmstat and iostat.


Paul

Hey, Paul,

iotop is showing a user with the process gnome-set-ngs-daemon as using around 17 mb/sec, and root as running jbd2/sda1-8 as using 171.55MB/sec. I did a search on google for these and can't really find much about my problem.

---

### Post by oldfred on 2010-11-22
iotop does not look like it is installed by default. Must be an oldie.:)

You may be able to use top.

But I would assume it is your log files filling up from some sort of error. I would check log files in System, Administration, log file viewer.

---

### Post by smeggs on 2010-11-22
> **oldfred said:**
> iotop does not look like it is installed by default. Must be an oldie.:)

You may be able to use top.

But I would assume it is your log files filling up from some sort of error. I would check log files in System, Administration, log file viewer.


I checked earlier, it's not generating enough errors to account for 180 and some odd megabites per second being written to disk. The error I was receiving was 

Nov 22 17:56:02 klendathu kernel: [96295.464115] VFS: busy inodes on changed media or resized disk sr0


I just found a post about jdb2/sda1-8, it explained a little bit. Also flush. Apparently the driver for the external my girlfriend was using was going crazy. The drive was plugged in, but not mounted under my user. I forced the logout of her user but the driver was still generating errors under her user name. Weird. File system is ext4 and I'm using Maverick. It's still writing periodically, due to some misconfigured apparmor profiles, but the usage is in the KB's and not the GB's. (I generated over 100GB of errors to cache in less than 30 minutes.) Is this like some super mega ultra polling or something? :P 

Also, hal-disable-polling --device /dev/sda1 would not work. kept reporting that the device was not found. However, a reboot with the device unplugged has fixed the drive use. Now to figure out how to get it to work like it's supposed to. 

Thanks for the replies.

---

### Post by richtl on 2010-11-28
Same problem here. gnome-set-ngs-daemon is beating the heck out of my hard drive. Often, when I try to print a pdf my system will completely lock with gnome-set-ngs-daemon bottlenecking the drive on iotop.

Very irritating.

Going to try reinstalling Maverick when I have a few minutes. If that doesn't work, it's back to Lucid for me!

Rich

---

