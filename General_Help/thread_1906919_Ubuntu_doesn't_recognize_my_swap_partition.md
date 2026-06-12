---
title: "Ubuntu doesn't recognize my swap partition"
date: 2012-01-10
forum: General Help
---

### Post by bobman321123 on 2012-01-10
I did some work with my swap, and I found out that I had two swap partitions that were each 4gb, and only one was active.
The smart person would have deleted the inactive one, and resized the correct one, but folks, I am not a smart person :P
I deleted both, and followed the ubuntuhelp site for setting up new swap partition, but it didn't work. How do I get Ubuntu to recognise my new 8gb swap partition?

---

### Post by SlugSlug on 2012-01-10
have you edited /etc/fstab  to contain new swap?

---

### Post by bobman321123 on 2012-01-10
I tried, but I'm not sure I formatted it correctly, because that didn't work.

---

### Post by mcduck on 2012-01-10
> **bobman321123 said:**
> I tried, but I'm not sure I formatted it correctly, because that didn't work.

Then could you post your current fstab contents and output from *sudo blkid* and *sudo fdisk -l* here?

---

### Post by SlugSlug on 2012-01-10
> **bobman321123 said:**
> I tried, but I'm not sure I formatted it correctly, because that didn't work.

can you post output of 

cat /etc/fstab 


& 

sudo blkid

---

### Post by bobman321123 on 2012-01-10
cat /ect/fstab: 
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda7 during installation
UUID=e3c460e6-bdf1-44b6-b166-d60818813186 none            swap    sw              0       0

```

sudo blkid: 
```
/dev/sda1: UUID="F4B435D2B43597D6" TYPE="ntfs" 
/dev/sda5: UUID="7779a225-b8ba-4ed7-8dd7-ad1816c8c106" TYPE="ext4" 
/dev/sda6: LABEL="swap" UUID="dbd88d03-e9fc-4510-b55e-596130b24613" TYPE="swap" 
```

---

### Post by satanselbow on 2012-01-10
> **bobman321123 said:**
> 
/dev/sda6       /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda7 during installation
UUID=**e3c460e6-bdf1-44b6-b166-d60818813186** none            swap    sw              0       0
[/CODE]

sudo blkid: 
```
/dev/sda1: UUID="F4B435D2B43597D6" TYPE="ntfs" 
/dev/sda5: UUID="7779a225-b8ba-4ed7-8dd7-ad1816c8c106" TYPE="ext4" 
/dev/sda6: LABEL="swap" UUID="**dbd88d03-e9fc-4510-b55e-596130b24613**" TYPE="swap" 
```

Replace the top bold bit in your quoted post with the bottom bold bit ;)


Your fstab entry for swap should look like:

```
UUID=dbd88d03-e9fc-4510-b55e-596130b24613 none            swap    sw              0       0
```

---

### Post by bobman321123 on 2012-01-10
Thanks man, that did it :D

---

### Post by Buntumatic on 2012-01-10
Next time don't go thru all that trouble, Linux can use as many swap partitions as you want same time. You even can add swap files to overall swap space.

---

### Post by bobman321123 on 2012-01-10
Oh? How would you add another swap partition to the system?

---

### Post by Buntumatic on 2012-01-10
First run mkswap on it. Like this ```
mkswap /dev/sdX
```
Then let your Linux know you want to use it with swapon. Like this ```
swapon /dev/sdX
```
That's it, repeat it for every swap partition you have.
Of course, if you want them activated automatically next reboot add respective lines to your fstab.
You can also turn them off with swapoff. Like this ```
swapoff /dev/sdX
```
Note, activating and deactivating swap does not require reboot, as with everything else in Linux (except kernel upgrade).

---

### Post by Buntumatic on 2012-01-10
Just to illustrate the fun working with Linux. :)

Once upon time I was building Openoffice on Gentoo, the box had not much resources, I think it had 1 GiB of RAM and 512 MiB of swap. I had conky running on the desktop and I saw memory filled up and swap filling up, too. Compiling Openoffice is time consuming, I did not want it to be killed by OOM killer.
I quickly did ```
dd if=/dev/zero of=/swapfile bs=1024 count=1M
```this created 1 gigabyte file, then I made it swap space ```
mkswap /swapfile
``` and finally I activated it ```
swapon /swapfile
```and voila! My compilation process was saved.

---

### Post by bobman321123 on 2012-01-10
So if I were to want to add another partition to swap permanently, all I would do is to add another line that says the bellow to the fstab?

```
"name of partition" swap
```

---

### Post by Buntumatic on 2012-01-10
Look at existing line for swap in /etc/fstab. There are a few fields to be filled.

1. device
2. mount point
3. type
4. mount options

See **man fstab** for more.

---

### Post by bobman321123 on 2012-01-11
Ok, :) Thanks man.

---

### Post by bobman321123 on 2012-01-11
Thanks for the help everyone, I don't know how I would survive without you guys.

---

