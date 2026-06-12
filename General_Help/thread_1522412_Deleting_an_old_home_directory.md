---
title: "Deleting an old /home directory?"
date: 2010-07-02
forum: General Help
---

### Post by djmccormick on 2010-07-02
I've followed some instructions on installing a new hard drive on Ubuntu ("[Installing a New Hard Drive]("https://help.ubuntu.com/community/InstallingANewHardDrive")" and "[HOWTO move /home to a new hard drive]("http://ubuntuforums.org/showthread.php?t=250104")") and I've now successfully got my new drive working with /home. Everything looks to be in perfect working order.

Now I'm wondering how to delete my original /home folder. Running "df -h" still shows 97% usage on my / partition and I'd like to clear out the old /home to free up all that space. I just don't know where these files are now is all.

---

### Post by dino99 on 2010-07-02
if you have installed a new hdd, you still have used a formatting tool like gparted or partedmagic, dont you ?

---

### Post by djmccormick on 2010-07-02
I used fdisk for the formatting (this is a CLI-only installation by the way). I believe my /home wasn't partitioned on its own, and thus the / mount still showing as being 97% full.

---

### Post by philinux on 2010-07-02
> **djmccormick said:**
> I used fdisk for the formatting (this is a CLI-only installation by the way). I believe my /home wasn't partitioned on its own, and thus the / mount still showing as being 97% full.

Then just use nautilus to navigate to you old home and delete anything you no longer need. Then empty trash.

---

### Post by djmccormick on 2010-07-02
This is a command-line only installation of Ubuntu 9.10. I don't have nautilus or a trash, but I'm comfortable using the command line tools to delete the directory.

My problem is that I don't know where my old /home is. I have mounted a new hard drive as /home so when I navigation to /home I'm seeing the new hard drive, not the old one. The data from my old /home is still taking up all my space on / where it was mounted before. I don't know "where" these files are, if that makes sense.

I figure I can unmount my new drive from /home and I'd be back to my original setup, where I could delete /home and give it a reboot (which should automatically mount the new drive as /home since i've updated my /etc/fstab to do this) but I'm worried something might get borked trying to unmount a live /home, delete the old one, and rebooting.

Hope that made more sense :P

---

### Post by indytim on 2010-07-02
Just launch your LiveCD.  Once booted, kickoff GParted and look at the partitions.  Your offending partition will be nearly full.


Remember, your boot /home is dictated by the contents of /etc/fsab.

-DataMan

---

### Post by djmccormick on 2010-07-02
I have two hard drives, one is the old drive (/dev/sda) and is 160GB. The new one (/dev/sdb) is 1TB.

My old drive (/dev/sda) is partitioned 3 ways. The first partition is the boot partition and it's about 146GB. The second and third partitions are both around 240 megabytes and I assume these are swap or something.

My new drive (/dev/sdb) is partitioned into one single partition. I've mounted this partition over /home now.

My problem is that I need to delete my old /home directory, but it wasn't on it's own partition. It was on the same partition as / so using a partitioning tool wouldn't help me here I don't believe.

> **indytim said:**
> Your offending partition will be nearly full.

The nearly full partition is also the partition that has my root filesystem. If I deleted the nearly full partition I'd delete my entire Ubuntu installation.

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0d43063f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19426   156039313+  8e  Linux LVM
/dev/sda2           19427       19457      249007+   5  Extended
/dev/sda5           19427       19457      248976   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4e6eb965

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux
```

---

### Post by philinux on 2010-07-02
> **djmccormick said:**
> This is a command-line only installation of Ubuntu 9.10. I don't have nautilus or a trash, but I'm comfortable using the command line tools to delete the directory.

My problem is that I don't know where my old /home is. I have mounted a new hard drive as /home so when I navigation to /home I'm seeing the new hard drive, not the old one. The data from my old /home is still taking up all my space on / where it was mounted before. I don't know "where" these files are, if that makes sense.

I figure I can unmount my new drive from /home and I'd be back to my original setup, where I could delete /home and give it a reboot (which should automatically mount the new drive as /home since i've updated my /etc/fstab to do this) but I'm worried something might get borked trying to unmount a live /home, delete the old one, and rebooting.

Hope that made more sense :P

Ah sorry.

Just use cd to get to your old home. Then you can use rm.

---

### Post by djmccormick on 2010-07-02
> **philinux said:**
> Just use cd to get to your old home. Then you can use rm.

Where exactly is my old home? For instance, complete this command...

```
cd _________
```

If I cd to /home I'm looking at my new home partition.

---

### Post by artemyv on 2010-07-02
> **djmccormick said:**
> Where exactly is my old home? For instance, complete this command...

```
cd _________
```If I cd to /home I'm looking at my new home partition.

You need to mount the root partiotion without mounting home - to do such - boot from live cd

mount  your "regular" root partition somewhere like /mnt/rootprt

and go to /mnt/rootprt/home

you should be able to see your old home dir and clean it...

---

### Post by djmccormick on 2010-07-03
> **artemyv said:**
> You need to mount the root partiotion without mounting home - to do such - boot from live cd

Thanks for the advice -- I wound up unplugging the new hard drive from the SATA to ensure I wouldn't get confused and delete anything, then I booted into the recovery mode and moved /home to /home2. Once I hooked the new drive back up and booted normally to confirm everything worked I went ahead and deleted /home2.

I appreciate you guys offering up your tips.

---

