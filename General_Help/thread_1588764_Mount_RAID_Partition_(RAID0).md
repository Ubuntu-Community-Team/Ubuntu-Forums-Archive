---
title: "Mount RAID Partition (RAID0)"
date: 2010-10-05
forum: General Help
---

### Post by p2bc on 2010-10-05
Seems my system was no shutdown properly. :confused:
Not by me, or by power outage, but I digress.


So when I go to boot the system it say can't boot. So I proceed to boot from a LiveCD to do diagnostic of the system.

Before I continue I illustrate the system:

1x 32gig USB Thumb Drive as Root  (/)
2x 500gig in a RAID0 as Home Directory (/home)
1x 4gig USB Thumb Drive as Swap (/swap)

So in theory I should be able to pullout the root usb key and put in another and point to the /home director (md0, the software RAID drive), or re-install on the root usb , and be good to go.

Before doing that I want to try and boot the system from the LiveCD, and recover the system if I can. ([https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)) At the very least check to see if the data on the home directory is unaffected, but I cannot mount to RAID0 partition by the LiveCD. All I see of the /home partition is the 2 individual drives, not the RAID drive, and therefore cannot access the 2 individual drives either.

Any help would be appreciated.
[SIZE=1]
**For the record, I looked to see if there was a appropriate thread for the subject, and could not find one. Please feel free to move as you feel fit**[/SIZE]

---

### Post by ronparent on 2010-10-05
Which release are you using? In releases before 9.10 you would have to install dmraid to a live cd session and activate and mount your raid partitions before you could look at them. 9.10 and 10.04 live cd's should mount them automatically on boot.

---

### Post by p2bc on 2010-10-06
To be honest wasn't sure which which LiveCD I used originally so I tried Kubuntu 9.10 and Ubuntu 10.4 last night and neither found / detected the RAID drive.

Both LiveCDs found the same two partitions. Seem as though I created a /boot and / (root) partition on the USB drive, how responsible of me, go figure. Anyways both of them mounted no problem, but there was no trace of the RAID partition. If I use GParted it does find the separate drives just says it is an unknown file format. I am assuming that is because it is a RAID format.

I also checked the fstab, and it is pointing to MD0 for my /home directory.

So I can chroot into the partition and probably fix it which is a good thing, but at this point I would like to check that the RAID/2 drives are functioning and/or not corrupted. 

Any suggestions.

---

### Post by p2bc on 2010-10-07
Where I am at today:

Well decided to try the fall back method, Google, and found some interesting results. So that help, some that confused, and some that increased the problem. 

Using these to pages together I tried to dig deeper.
[https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

So I proceed to mount the root disk:
```

sudo mount /dev/sdc2 /mnt
sudo ls -la /mnt
sudo chroot /mnt
/bin/bash/: 3: Syntax error:  "(" unexpected

```"Syntax error" :confused: First question is the syntax error on the LiveCD, don't think so, must be on the /mnt which I have to admit I have modifies on other system but never on this one.

Strike 1, lets try something else...

[quote=LiveCDRecovery]
If you are not using a software raid setup or have  setup your partitions using LVM/2 or EVMS your IDE/SATA/SCSI devices  should be accessible through the files /dev/hd[a-z] and /dev/sd[a-z].  /dev/hda corresponds to the primary master device on your IDE bus, while  /dev/sda is your first SCSI/SATA device. If you are using software  raid, LVM, LVM2 or EVMS, your devices may be listed in the following  directories: 

/dev/evms/dm     if you are using software raid 
/dev/evms/lvm    if you are using LVM
/dev/evms/lvm2   if you are using LVM2 
/dev/evms        if you are using EVMS
[/quote]

So I decide to check
```

ls -la /mnt/dev/evns/dm
No file or folder found
ls -la /mnt/dev/evns
No file or folder found 
```I do a "ls" command instead of "fdisk" like it was discribed on the other page because I can't mount /mnt

Strike 2, we go on...

[quote=SoftwareRAID]
**Checking the status of your RAID**

 Two useful commands to check the status are: 
* cat /proc/mdstat  
This will show output something similar to 
Personalities : [raid1] [raid6] [raid5] [raid4] 
[/quote]

```

ls -la /mnt/proc/mdstat
No file or folder found
ls -la /mnt/proc/
.
..

```Again can't mount the partition so I at lease check to files are there, nope empty.

Now, I also came across these:
[http://ubuntuforums.org/showthread.php?t=2557&pp=10](http://ubuntuforums.org/showthread.php?t=2557&pp=10) (outdated)
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)  (section 7 most relevant in this case)

The next step I am going to try is installing mdadm onto the LiveCD since it is not already installed, and try that.

[SIZE=1]
On a side note, this post has taken me 3 hours to write since as I am writing I think of something else to try so I go off and come back. At this moment in time I am trying to get the LiveCD configure to work on my network so I can browse the web from there. To find I can't access the web, I ping no good, I change hostname, I do everything, to find out I am connected to the router, actually log into the router from the LiveCD machine, so that connection is good, but can't get through the router to the outside web on the LiveCD machine, but I can on my laptop. All that to say yet another problem to over come. I am sorry for the little rant, it help though, now to find the solution.[/SIZE]

---

### Post by p2bc on 2010-10-07
SO... after a few more gray hairs, not to mention less hair from all the pulling.

I finally using Knoppix, because it has "mdadm" included, I do:
```

sudo mdadm --assemble --scan
mdadm: /dev/md/0_0 has been started with 2 drives
sudo mount /dev/md/0_0 /mnt
sudo ls -la /mnt

```

And low and behold everything seems to be there!!! :P
[B]

Now the question is how do I fix all this?[/B]

Can't "chroot" into the root partition because of an unexpected "("

And then to tie the raid drive into the installation if I choose to format and re-install root.

---

