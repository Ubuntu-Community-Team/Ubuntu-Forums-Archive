---
title: "I think I messed up my partition table"
date: 2011-03-08
forum: General Help
---

### Post by willhurley82 on 2011-03-08
I used testdisk last night, to undelete some files on my ntfs partition.  I booted to vista before that (first time since I've installed Ubuntu 10.10) and uninstalled/deleted some unused software and personal files.  Upon booting up today, I was taken straight to the grub recovery prompt.  I used my cell phone to see what to do.  

I booted from Ubuntu 10.10 64bit recovery disk and I think I fixed my grub.  Now I can boot, but Conky is not reading my swap partition.  I checked with gparted gui and my swap partition is now sda3.  It was sda5.  How do I fix this?  I don't want to muck things up worse and am not sure if it's the lua file my Conky is hooked to (which wasn't changed) or if my swap partition is useless now.  

I'm putting the red triangle beside this because I do not know the ramifications of potentially losing a swap partition, on a laptop, with Linux.  

Let me know what additional information I need to provide, if any.

---

### Post by Hedgehog1 on 2011-03-08
> **willhurley82 said:**
> 

Let me know what additional information I need to provide, if any.

We need 2 things - and then we can solve this.  Honest!

In the Terminal (Menu to: Applications >> Accessories >> Terminal),  please run this command: (the -'l' is a lower case 'L')
```
sudo fdisk -l
```
Then copy the text from the output and paste it into your next post.

Also, please copy the text from your **/etc/fstab **file into your next post, too.

***The Hedge***

:KS

---

### Post by willhurley82 on 2011-03-08
From fdisk:


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x32d8b890

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8429    67700704+   7  HPFS/NTFS
/dev/sda2            8429       13260    38807552   83  Linux
/dev/sda3           13260       13372      893944   82  Linux swap / Solaris






From fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=af920f37-9cf2-48ec-8656-ebf1172faa4f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=8d74440b-b9d8-4c57-aebf-affd2cc4c4c8 none            swap    sw              0       0

---

### Post by Hedgehog1 on 2011-03-08
Your system has changed over time.  Thankfully, you used UUIDs in fstab, and that is a very good thing.

It looks like your swap parition has a new UUID when it got moved to sda3.  No biggie.

We will follow the text in the comment in fstab:

```
# Use 'blkid -o value -s UUID' to print the universally unique identifier
```

So, lets have you do this, please:

```
sudo blkid -o value -s UUID
```

You will see a UUID that does not match the ones in the fstab file.

The new UUID is your new swap partition's UUID.

Let hve you edit the fstab file:
```
gksudo gedit /etc/fstab
```

Now you will change your fstab ile to reflect the new swap space UUID ([COLOR="Red"]xxx-xxx-xxx-xxx-xxx[/COLOR] represents the new UUID)
```
# / was on /dev/sda5 during installation
UUID=af920f37-9cf2-48ec-8656-ebf1172faa4f / ext4 errors=remount-ro 0 1
# swap was on /dev/sda6 during installation
[COLOR="Red"]#[/COLOR]UUID=8d74440b-b9d8-4c57-aebf-affd2cc4c4c8 none swap sw 0 0
[COLOR="Red"]UUID=xxx-xxx-xxx-xxx-xxx none swap sw 0 0[/COLOR]

```

Save the fstab file, reboot and you have swap!

***The Hedge***

:KS

p.s. Lack of defined swap space would mean 'sleep' and 'hibernate' would not work/crash.

---

### Post by willhurley82 on 2011-03-08
Just to make sure, it's the first line of this blkid?


8A3207C43207B3EB
af920f37-9cf2-48ec-8656-ebf1172faa4f
8d74440b-b9d8-4c57-aebf-affd2cc4c4c8



EDIT:  I ask this because the other two match

---

### Post by Hedgehog1 on 2011-03-08
> **willhurley82 said:**
> Just to make sure, it's the first line of this blkid?

8A3207C43207B3EB
af920f37-9cf2-48ec-8656-ebf1172faa4f
8d74440b-b9d8-4c57-aebf-affd2cc4c4c8

EDIT:  I ask this because the other two match

I am glad you asked. The shorter number is from your NTFS partition.

So please **DO NOT** change your fstab file after all.  It is fine.

Looks like you will have to tell conky to use /dev/sda3 as swap.

***The Hedge***

---

### Post by willhurley82 on 2011-03-08
Cool, thanks!  Now to learn Conky/lua, to an extent!  :D

---

### Post by Hedgehog1 on 2011-03-08
You also learned why using the UUIDs are so great.  You moved the partitions around, and Ubuntu ran happily (after that little grub thingy).

Is it possible to get conky to use the UUID as well?  I don't know.

***The Quandering Hedge***

---

### Post by willhurley82 on 2011-03-08
Hedgehog1, you are a genius!  :D   I'll see if it can.  That would be THE trick!  Give me a week or so though.  Having to learn lua from scratch with very little coding experience.

EDIT:  I didn't really mean to move the partitions around.  I know how they work, somewhat and moved them by accident.  :(

---

### Post by willhurley82 on 2011-03-09
I still think something is wrong.  I went to put computer in Hibernate mode and the option isn't there since I rearranged the partitions.

---

### Post by Hedgehog1 on 2011-03-09
OK - this means you need to turn 'swap on'

To do this, you need to run gparted, right click on the swap parition and select the 'swapon' option.

It toggles between 'swapon' and 'swapoff'.  This might solve the conky issue (but no promises on that).

***The Hedge***

> Hedgehog1, you are a genius!*...and yet so few people realize this...*

---

### Post by willhurley82 on 2011-03-09
I'm getting this.  So . . . my swap isn't big enough, or do I need to resize something?

swapon: /dev/sda3: found swap signature: version 1, page-size 4, same byte order
swapon: /dev/sda3: pagesize=4096, swapsize=915406848, devsize=915398656
swapon: /dev/sda3: last_page 0x36900000 is larger than actual size of swapspace
swapon: /dev/sda3: swapon failed: Invalid argument

EDIT:  And gparted is telling me that swap is off

My other thread is also attempting to address this:  [http://ubuntuforums.org/showthread.php?p=10541833#post10541833](http://ubuntuforums.org/showthread.php?p=10541833#post10541833)

---

### Post by willhurley82 on 2011-03-09
Solved, but hibernate function is still gone from shutdown menu.  I'm leaving the other link open for that.  Turns out there was a "-" left out of my uuid in fstab.  Thanks again, Hedgehog1  :D

Dave

---

