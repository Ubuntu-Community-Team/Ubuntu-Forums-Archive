---
title: "My file system seems to have disappeared"
date: 2010-06-13
forum: General Help
---

### Post by erajsri on 2010-06-13
Hi all,

I use a nettop PC which runs Ubuntu 24x7 connected to the internet. This has a 60 GB 2.5" hard drive and I remember letting Ubuntu partition it the way it wants. This netop has been operational for the past few months.

When I started up this nettop today (i send it offline once in awhile) the system wouldn't boot to the login screen. I get the boot loader options and the ubunut boot image. But halfway through the bootup the screen goes blank and shows me a terminal with the prompt **initramfs**. Before that on the terminal **I see several error messages saying failed to mount** /sys /dev etc which indicates to me there is a file system error. At the initramfs prompt I can run limited commands such as 'ls' and I see several folders such as /root /libs etc intact. But there arent many files inside these folders.

I am wondering if somebody hacked into my system or if it is a hardware fault such as a bad sector on the HDD. **In any case would I be able to recover my data and how would it be possible** ? Cos this data is precious, even salvaging some of it would be ok. 

Thanx all,
Hoping help is on the way.

---

### Post by erajsri on 2010-06-13
Pls help :(

---

### Post by WorMzy on 2010-06-13
Boot from a Live CD or USB stick, then run: ```
sudo fdisk -l
``` to get a list of all the partitions on your hard disks. Then check the status of your ext partitions with:


```
sudo e2fsck /dev/sda1
```

Replacing sda1 with whichever ext# partition you want to check. 

NOTE: Don't use this on a non-ext partition.

---

### Post by bodhi.zazen on 2010-06-13
can you boot a live CD and try to mount the partition ?

Next would be to try testdisk

---

### Post by erajsri on 2010-06-14
Thanx, I think they were ext partitions. Not sure if it was 2, 3 or 4. I really want to salvage my data. Will run the tests and let u know if i need further help.

---

### Post by erajsri on 2010-06-18
> **WorMzy said:**
> Boot from a Live CD or USB stick, then run: ```
sudo fdisk -l
``` to get a list of all the partitions on your hard disks. Then check the status of your ext partitions with:


```
sudo e2fsck /dev/sda1
```

Replacing sda1 with whichever ext# partition you want to check. 

NOTE: Don't use this on a non-ext partition.


Just a question. I dint try running on a Live CD yet. I will do that soon.

What is there are bad sectors on my hard drive. Will fdisk fail on that ? If fdisk fails, without being able to read the partition infor, would that stop from **e2fsck**ing ?

thanx.

---

### Post by WorMzy on 2010-06-18
fdisk shouldn't fail, it might report the partition as "unknown", rather than ext#, but it should at least recognise that there's a partition there. If it doesn't, then e2fsck won't be able to run, in which case you're best off using a data recovery application like TestDisk, as bodhi.zazen suggested. Recover your data, and reformat your hard disk.

---

### Post by bodhi.zazen on 2010-06-18
> **erajsri said:**
> Just a question. I dint try running on a Live CD yet. I will do that soon.

What is there are bad sectors on my hard drive. Will fdisk fail on that ? If fdisk fails, without being able to read the partition infor, would that stop from **e2fsck**ing ?

thanx.

Bad sectors = wear and tear on your hard drive. fsck is a check of the software (file system). Sometimes it can be reparied, sometimes not.

If the file system can not be repaired, reformat the HD and restore your data from backup.

See also:

[http://www.linux.com/feature/32026](http://www.linux.com/feature/32026)

[http://blog.shadypixel.com/monitoring-hard-drive-health-on-linux-with-smartmontools/](http://blog.shadypixel.com/monitoring-hard-drive-health-on-linux-with-smartmontools/)

You can read more technical articles if you are interested, but all hard ware fails eventually, which is why you should back up your data off the hard drive.

---

### Post by erajsri on 2010-06-20
> **WorMzy said:**
> Boot from a Live CD or USB stick, then run: ```
sudo fdisk -l
``` to get a list of all the partitions on your hard disks. Then check the status of your ext partitions with:
```
sudo e2fsck /dev/sda1
```


This worked! I'm thankful for your input. I'm now back online without a reformat or reinstallation of the OS nor any data loss. Seems like the problem was with a file system inconsistency (?) (the filesystem was actually set up with journalin and e2fsck used it to repair it.)

But there's a hitch. When I got to e2fscking the hard drive it reported an error and asked me if I wanted to ignore it. I replied with a no hoping that it would try to fix that and get back to me with a status. But e2fsck didnt fix it and aborted the file system check. After that I rebooted to the OS. The OS seems to be working fine except for the login screen on the first attempt, which reported some errors of missing files of GNOME. I checked my data and they were there in my folders. I havent been to testing ALL those files for their consistency, but the few I checked randomly were ALL good.

Now I want to get rid of the idea that file system could be in any form of inconsistency. How can I make sure of this ? If there are any bad sectors or not ? Any better tools other than e2fsck that you can suggest, or any parameters that I should add ? Im currently running this system and it seems fine so far, but I jus want to clear my doubts.

thanx all,
you jus saved 6 months worth of work for me.

---

### Post by leorolla on 2010-06-21
If your files are that valuable, my naive advise is that you stop all the fixes and make a good backup of your important files right now.

Actually... make 2 backups, and avoid making both on identical devices that you bought all together.

I have a general rule that important data should be saved in at least 3 different devices, and these devices should never be at the same place at the same time. By doing so, you only loose your data if two unrelated, very rare events happen at the same time.

If your computer is not that reliable at this moment, so loosing the data there right now wouldn't count as a rare event.

---

