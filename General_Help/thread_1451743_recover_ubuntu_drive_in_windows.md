---
title: "recover ubuntu drive in windows"
date: 2010-04-10
forum: General Help
---

### Post by dant321 on 2010-04-10
Hi All,
I was using ubuntu for 18 months on my laptop however it died last night.
I cannot remember what format I had the drive in.
It was probably ntfs but i have no idea.

I have bought a new laptop that is not compatible at the moment with ubuntu so  am running windows 7.

I am trying to recover the drive but cannot, its not being seen in windows. I am using various file recovery programs, nothing is being found.

It might be the drive totally dead but i think it has somethign to do with recovering a ubuntu drive in windows?

Is it all gone?

The only tools I have at my disposal are windows machines and programs, or an ubuntu live cd which wont find the hdd either.

The hdd is being inserted via a usb external caddy I have. It behaves as an external drive.

Thanks

---

### Post by darolu on 2010-04-11
I don't think your hard drive or info is gone (well I hope is not). What -most likely- is happening is Windows not being able to read your Linux Partition, by default Windows can't read Unix and Unix-like filesystems like Ext2, Ext3 or Ext4, your Ubuntu partition is probably formatted with one of these filesystems; what you have to do is to install a program (in Windows) to read these partitions.

Read this links for more info about it: [http://www.linuxjournal.com/article/9449](http://www.linuxjournal.com/article/9449)

[http://icsbd.co.cc/linux/57-utility/57-access-your-linux-partition-ext2-ext3-and-ext4-from-windows-in-a-duel-boot.html](http://icsbd.co.cc/linux/57-utility/57-access-your-linux-partition-ext2-ext3-and-ext4-from-windows-in-a-duel-boot.html)

Another solution would be to use the LiveCD on your new Laptop to read your old hard drive.

BTW; what laptop did you get? are you sure it is not compatible with Ubuntu at all?

---

### Post by Mark Phelps on 2010-04-11
> **darolu said:**
> Another solution would be to use the LiveCD on your new Laptop to read your old hard drive.

Guess you didn't see the part where the OP said:  > or an ubuntu live cd which wont find the hdd either.

If you can't even see the drive with the Ubuntu LiveCD, I would suggest you download a burn a GParted LiveCD from distrowatch.com and see if you can see the drive using that.

---

