---
title: "Permissions problems with External Hardrive"
date: 2009-12-21
forum: General Help
---

### Post by emilthomasg on 2009-12-21
Hi
Im having big issues with my ex hdd, I can't  remove any files off it due to permissions issues. I keep getting told that I'm not the owner. I been reading the forum for a few days now and nothing seems to be helping. It is HFS+ formatted with a 32gb FAT32 partition.
Anyone got any ideas?
Cheers
ps The FAT32 partition is owned by me and is working perfectly :)

---

### Post by prem1er on 2009-12-21
What command did you use to mount it? Or was it mounted automatically?

---

### Post by emilthomasg on 2009-12-21
It was mounted automatically,forgot to add (sorry) that this all started after a friend (mac user) dragged and drop a lot of music,movies etc on to the ex hdd.
Cheers

---

### Post by emilthomasg on 2010-01-05
Hi
Anyone out there with some ideas? This problems is driving me NUTS! After checking the properties tab of the ex hdd, I see the owener is set as :99- user #99. I've tries gksudo nautilus but still no help. I keep getting told I am not the owner.
Any ideas??
Thanks

---

### Post by nothingspecial on 2010-01-05
Hfs+ drives are mounted read only by default in linux.

I don`t have any experience with them (except with a mac formatted iPod, but I just restored that on my brothers windows pc).

Try ```
sudo mkdir /media/drive
```

```
sudo mount -w -t hfsplus /dev/sd[COLOR="Red"]??[/COLOR] /media/drive
```

change the red question marks for the correct partition.

---

### Post by amac777 on 2010-01-20
From my research, it appears that HFS+ write support is implemented but not guaranteed to work properly yet in Linux. That is why by default HFS+ drives will be mounted read-only. It's a protection mechanism to prevent data corruption that might occur if you write to that drive from Linux.

For the above reason, my first advice would be to not use HFS+ at all. If you need to share your drive between linux and mac (and/or windows), I would recommend using the NTFS file system. That way, read/write support will be automatic and reliable no matter which computer you use to access the drive. To convert your drive, you would simply copy all the files onto your internal drive (or some other temporary location), then repartition the HFS+ partition to use NTFS (you can use gparted or another similar utility), and then copy all the files back into the NTFS partition.

But if you really want to try enabling write support, it seems that you could use the "force" option with mount to force write support even for HFS+. So you would need to modify the above command from nothingspecial to the following:

```
sudo mount -w -t hfsplus -o force /dev/sd?? /media/drive
```

But as quoted on this page ([http://www.mjmwired.net/kernel/Documentation/filesystems/hfsplus.txt):](http://www.mjmwired.net/kernel/Documentation/filesystems/hfsplus.txt):) 
[COLOR="Red"]Use 'force' at your own risk.[/COLOR]

---

### Post by emilthomasg on 2010-01-20
Thanks for the advice will proberley create a new partition from the HFS+ partition,I would like to keep some space for any mac files or users. HFS+ is problematic although some people swear by it. This whole permissions thing with linux can be difficult. 
Thanks again.
ps Will keep you posted on my progresse :)

---

