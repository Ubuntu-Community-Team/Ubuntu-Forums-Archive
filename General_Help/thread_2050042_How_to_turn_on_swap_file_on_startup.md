---
title: "How to turn on swap file on startup?"
date: 2012-08-29
forum: General Help
---

### Post by chkneater on 2012-08-29
I am using Ubuntu Studio with AV Linux dual install.  At startup I have to manually turn on the swap file with Gparted.  Does anyone know a script or command to automatically turn the swap file on at start up?

---

### Post by 2F4U on 2012-08-30
Is that a swap file or a swap partition? You would usually create a swap partition during setup and it will be added to /etc/fstab and mounted automatically during the boot sequence. Seems to be different for you, so how exactly is your setup?

---

### Post by chkneater on 2012-08-31
Well, it's a swap partition, and I have to manually turn it on with Gparted.  During setup I don't recall setting up the swap file at all.  I forgot that I am actually using AV linux, not Ubuntu.  I had been using Ubuntu Studio 10.10, which didn't have a swap file either?  AV and Ubuntu are so similar I forgot which one I was using, but the kernel is 2.6.39.1  The weird thing is even tho the swap partition is on, it doesn't seem to be writing anything to it regardless of load?

---

### Post by TheFu on 2012-08-31
Look inside the /etc/fstab file. There should be a line that has "swap" in it.  It needs to be a partition, not a file.  I suppose there's a way to use a swap file, but a swap partition is historically how all UNIX/Linux systems work.

Gparted should show the swap partition device.  Something like /dev/sda6 ... be certain you actually check which device your system uses or it will be terrible - wipe all your data terrible with the wrong device.  Here's the line in my fstab.  
Your uuid will be different or you can use the specific device.
```

UUID=42370193-074c-479c-87aa-35616a853dfb none    swap    sw     0       0
```

---

### Post by chkneater on 2012-08-31
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# /dev/sda3
/dev/sda3 / ext4 relatime,errors=remount-ro 0 1
# /dev/sda7
/dev/sda7 none swap sw 0 0
# cdrom
/dev/cdrom /media/cdrom udf,iso9660 user,noauto,exec,utf8 0 0
/swapfile1 swap swap defaults 0 0


This is my fstab.  The very last line I added after going through a guide on mkswap.  I did format a swap partition manually, which is also the swap I turn on manually with Gparted-swapon.  After I added that last line, I no longer get an error at startup, however the same problem exists with it not actually USING the swap.  I know that it will only use swap when necessary, but I've load tested and it still doesn't work.  

So to summarize, I started out with a swap partition that I have to start with Gparted and it still didn't work.  So I then used mkswap to make a swap file instead, and still doesn't work.  

For some reason tho, my fstab points to sda7, when the swap partition is actually sda5.  I'm tempted to go ahead and change that out and see what happens.  Also, the fstab doesn't list a UUID for sda7?

Does it look like I should change out sda7 for sda5 since that is the partition formatted for swap (just over 2Gigs)

Also, fdisk -l does display sda5 and 7 as Linux swap/ Solaris, but Gparted only shows sda5 as a partition, and sda7 as not formatted.  Thanks for the help BTW

---

### Post by TheFu on 2012-08-31
There isn't any "format" for a swap partition. Might that be the issue with /dev/sda7?  
Using the **swapon -s** command, see if that device is used. If not, open gparted, delete the partition, then add it back and mark it as "swap" or "linux swap" and leave it alone.

You can add the **swapon** command to a startup script if you like ... perhaps /etc/rc.local would work, but really, you should figure out the root cause for why sda7 isn't used already.

I hate to say this now, but I specifically do not have swap partitions on many of my machines. They aren't needed when the necessary RAM is available.  For a desktop, it is a good idea to have a 1G-4G swap partition.  Forget the old rules of thumb - 2x physical RAM. Those do not apply anymore without a very good reason.

To see which device goes with which UUID, use the **blkid** command.  If that only works with mounted partitions, you can do a **ls -al /dev/disk/by-uuid/**  to see the mapping between device and uuid.  Simple.

Once you get sda7 working as your swap, be certain to remove the swapfile.  Urg. ugly.  Plus it is nice on a dual, tri, quad, .... boot system to only have 1 swap partition.

---

### Post by chkneater on 2012-08-31
As far as partitioning goes, you can partition a linux swap by using gparted-right click.

Now I have sda2 as the extended partition you mentioned, then sda3 is the partition with AV, and sda6 as US10.10.  And I DO remember that when I initially installed 10.10, I DID lose everything like you said.  I just remembered that...:confused:

sda5 is linux-swap and sda7 is unknown or unformatted according to gparted, but sda7 is what fstab was pointing too.  Now to confuse things a bit more, fdisk shows BOTH sda5 and sda7 as linux swap/solaris.  Now I have two options I can see, which would be go ahead and format sda7 to linux swap OR just change fstab to point to sda5?  That's all I can come up with so far.

When you said get rid of the swap file, were you referring to that last line I added in the fstab?

ls -al /dev/disk/by-uuid/ shows my file system partitions along with sda5 linux-swap which is correct.  

Swapon -s yielded both /swapfile1 and sda5. sda7 is unused by anything according to gparted, that is the partition that fstab was pointing too.

---

### Post by NikTh on 2012-09-01
Hello 

can you please give the results of 

```
sudo blkid
``` 

Thanks

---

### Post by TheFu on 2012-09-01
I made a mistake about sda5 - and corrected it, but it seems you'd already read it. Sorry.

When it comes to disk partitions, it is really easier for us to help if you copy/paste the output from the programs we ask to be run.  Also, if you can avoid the GUIs, that is helpful too ... I can't copy/paste text from a GUI/image file. ;)
Text descriptions are harder to gain a clear understanding from.

* blkid
* fdisk -l
* swapon -s
* contents of your /etc/fstab

Please.

---

### Post by chkneater on 2012-09-08
Ok, I seem to get what's going on now.  I have both a swap partition and a swap file that I created with the guide below:

[http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/](http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/)


For some reason the swap partition is not being started at startup, so to avoid having to use Gparted every time to start the partition, I commented out the relevant line in the /etc/fstab leaving only the swap file active.  The guide above was really useful and easy and now I don't have any startup errors.

---

### Post by sadeqzadeh on 2013-07-06
I had the same problem, I had to turn my swap partition on manually each time (using swapon command). The problem was that the UUID for swap partition in /etc/fstab file was totally different from my real swap partition's UUID (you can check your swap partition's UUID with Gparted). I have no idea of how that UUID had came into the fstab file, but it was there. Thanks to TheFu for giving a clue for double checking those UUIDs. Again, the UUID mentioned in /etc/fstab (that for swap purpose) should be the same as the UUID of your swap partition.

---

