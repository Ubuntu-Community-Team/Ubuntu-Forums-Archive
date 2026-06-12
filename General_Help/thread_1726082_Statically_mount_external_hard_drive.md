---
title: "Statically mount external hard drive?"
date: 2011-04-10
forum: General Help
---

### Post by hogfan on 2011-04-10
I have USB External HDD attach to my Ubuntu Maverick server that I plan to use for backups.  However, everytime the server is rebooted the External drive gets mounted as a different device.  I want to mount this every time at /media/backup.  I have been following this guide:

[http://ubuntu-tutorials.com/2006/12/06/how-to-always-mount-removable-drives-in-the-same-place-ubuntu-6061-610/](http://ubuntu-tutorials.com/2006/12/06/how-to-always-mount-removable-drives-in-the-same-place-ubuntu-6061-610/)

but when I get to the part where I try to get my drive information using:

```

udevinfo -a -p $(udevinfo -q path -n /dev/sda) | grep SYSFS{serial}
```I get a udevinfo  not found message.  What do I need to do to get this backup hdd to mount in the same location every time?  Thanks for any help.

-hogfan

---

### Post by seawolf167 on 2011-04-11
You'll want to add an entry to /etc/fstab for the drive to be mounted upon boot. You can click the fstab link in my signature if you'd like to work through it yourself, else, post the output of

```
blkid
sudo fdisk -l
mount
```

so we can help you add the correct entry.

---

### Post by hogfan on 2011-04-11
Thanks.  I'm going to try and work through it.

-hogfan

---

### Post by buntolith on 2011-04-26
Hi,

I have the same problem and when I read through the fstab link I still can not find a solution.

I have edited my fstab like this to always mount my external hdd by UUID on /mnt/laketria on my server:

# automount of laketria
UUID=e3300722-ceb9-43d3-868b-33a8c58f6d95 /mnt/laketria	ext4	defaults	0	0 

This have always worked out fine for me, but recently I installed smartmontools to keep an eye on my hdd I have in my server. (I have 6 hdd in a raid5 with LVM on top plus the external HDD). With smartmontools I want to set up the smartd daemon to email me when there are hdd errors. Smartmontools doesn't work well with external hdd so I want to exclude the external hdd in the configuration file for the smartd daemon. But since the external hdd sometimes is named /dev/sde1 and sometimes something else I have a problem. Ideally I want to automount the external hdd at /mnt/laketria and always also mount it at /dev/sdg1. Is this possible?

Thanks a lot for any help because I am stuck for now...(and then I have to setup postfix also but this is another problem...)

---

### Post by seawolf167 on 2011-04-26
For future problems/questions please start a new thread.

As for adding as two mount points is pretty easy, you'll use the *bind* command. 

The basic example to add in /etc/fstab (edit it to fit your needs) is:

```
/mount/path/one /mount/path/two bind defaults,bind 0 0
```

---

### Post by buntolith on 2011-04-26
OK, I'll do that for the next time...but thanks for the incredibly quick answer.

In vi when I type 

UUID=e3300722-ceb9-43d3-868b-33a8c58f6d95 /dev/sdg1 /mnt/laketria       ext4    bind defaults bind 0 0

..."bind defaults bind 0 0" becomes red. Is this the way to do it?

---

### Post by seawolf167 on 2011-04-26
Add the *bind* command as a separate line after you have already defined your two mount points

---

