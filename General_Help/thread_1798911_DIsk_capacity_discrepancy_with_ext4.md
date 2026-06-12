---
title: "DIsk capacity discrepancy with ext4"
date: 2011-07-06
forum: General Help
---

### Post by jcd29 on 2011-07-06
I've been seeing this with every single ext4 or ext3 disk/partition I work with, but I decided to make a post about it now since I got a bigger hard drive.

I formatted a 1TB external HDD as ext4 last night. 

This is what I got:

[IMG]http://img146.imageshack.us/img146/2259/71163295.png[/IMG]

[IMG]http://img69.imageshack.us/img69/7180/70755142.png[/IMG]

The first imaage is from GParted, and the second one from Nautilus, when you right click the disk and click on Properties. **Notice how GParted says the disk is 931 GiB while the Properties window says it's 917 GB**. This happens to every single ext4 or ext3 drive I've worked with, and every other Linux computer with ext4 or ext3 I've seen. I know about the 5% reserved space in ext4, but it's not that. The 5% would be that 45.8 GB you see as used (the disk in actually empty) in the Properties image.

Now, I know about how HDD manufacturers will tell you it's 1000TB when in reality it's not, etc. The thing is, according to this converter: [http://wintelguy.com/gb2gib.html](http://wintelguy.com/gb2gib.html)

1000 GB would be 931 GiB. So far so good! The GParted image shows the disk as 931 GiB. **The thing is, as you can see, it also shows 14.81 GiB used right out of the gate, which leaves that 917 GiB that the Properties image takes as the "total capacity". **

So what's going on here? Is it just that ext4 takes that much off the actual disk capacity? Because I compared with a friends 1TB external, and it showed its total capacity as 931 in both GParted AND the disk properties, but of course his disk was NTFS. 

It'd be weird if ext4 takes off 14 GiB while NTFS takes nothing, so I'm wondering what exactly is that and if it can be changed/fixed somehow?

Like I said, this applies to every single ext4 and ext3 drive I've worked with.

---

### Post by dFlyer on 2011-07-06
Is it's system space reserved for journaling, this is only a guess on my part.

---

### Post by haqking on 2011-07-06
I would say journalling overhead too

---

### Post by jcd29 on 2011-07-07
Is that something you could safely remove/disable for external drives or internal data drives? (as in, not the one with the OS). What could the consequences be?

---

### Post by Frogs Hair on 2011-07-07
Reported capacity can vary depending on the file system because of the method of measurement used . I don't  if you could recover space that does not show up as a partition .

---

### Post by Topsiho on 2011-07-07
The 1 TB is measured in decimal (1000 bytes in a KB).
The reported amount of memory is measured in binary (1024 bytes in a KB).

If you divide 10^12 (which is a TB) bytes repeatedly a number of times by 1024, you get exactly the 931 GB :)

So everything is clear and normal ...

Topsiho

---

### Post by jcd29 on 2011-07-07
> **Topsiho said:**
> The 1 TB is measured in decimal (1000 bytes in a KB).
The reported amount of memory is measured in binary (1024 bytes in a KB).

If you divide 10^12 (which is a TB) bytes repeatedly a number of times by 1024, you get exactly the 931 GB :)

So everything is clear and normal ...

Topsiho

931 GB would be normal, yes. But not 917 GB which is what you see under disk properties. If you check disk properties on a 1TB NTFS drive, you'll see 931GB. 

But yeah now I see it's the journaling, so no big deal.

---

### Post by Topsiho on 2011-07-07
:)

I did not look at the second graph, only the GParted one. That one says 931 GB, which is the correct binary number for the available disk space in binary, if it is 1 TB in decimal.

The second graph says 917 GB, as you stated, and probably correctly  explain as the available amount after journaling, which would then use 931 - 917 = (oops, where is the calculator) 14 GB (binary), if both are in binary.

Topsiho

---

### Post by psusi on 2011-07-07
The total reported by the kernel, and thus nautilus, is reduced by the filesystem inode tables and allocation bitmaps, which is about 15 gb.  The journal uses 128 mb, and the resize inode uses a little bit more.  There is a bug in nautilus that causes it to report the reserved space as used, which accounts for about 45 gb, or most of what it says is used.  By default, ext[234] reserve 5% of the disk for use by root only, to prevent the disk from filling up and causing high levels of fragmentation, and the system to be unable to log any errors.  You can adjust the reservation with tune2fs.

---

### Post by Topsiho on 2011-07-07
The 15 GB mentioned tallies well with the 14 GB (rounded) discrepancy, so it's not journaling after all :)

Topsiho

---

### Post by jcd29 on 2011-07-07
> **Topsiho said:**
> The 15 GB mentioned tallies well with the 14 GB (rounded) discrepancy, so it's not journaling after all :)

Topsiho

I don't know, check the GParted image, it says 14GB used, which would make the 931GB to 917GB. If it was just a Nautilus bug, this wouldn't appear there.

---

### Post by psusi on 2011-07-07
> **jcd29 said:**
> I don't know, check the GParted image, it says 14GB used, which would make the 931GB to 917GB. If it was just a Nautilus bug, this wouldn't appear there.

The nautilus bug is why it says 46 instead of 14 used.  The 14 is the inode table and allocation bitmaps, and then the extra 32 that nautilus reports is the emergency reserve.

---

### Post by jcd29 on 2011-07-07
> **psusi said:**
> The nautilus bug is why it says 46 instead of 14 used.  The 14 is the inode table and allocation bitmaps, and then the extra 32 that nautilus reports is the emergency reserve.

I don't get it. The reserved space right now is 5%. I still haven't changed that. 

But still, the total capacity Properties reflect is 917 GB. With 46.8 GB used and 870 GB free. Those 46.8 are I'm guessing that 5% reserved space. If we add those to the 870GB free, that's about the 917GB. Since the disk is still empty.

However, in Gparted we see that apart from those 46.8 GB that are for the reserved space, there's 14 GB in use. Since it shows the capacity as 931 and the "free space" as 917 GB.

So are you saying that the 14GB are all filesystem inode tables and allocation bitmaps?

---

### Post by psusi on 2011-07-07
> **jcd29 said:**
> 
So are you saying that the 14GB are all filesystem inode tables and allocation bitmaps?

Yes.

---

### Post by jcd29 on 2011-07-07
> **psusi said:**
> Yes.

Damn. Why does that take up so much space? With a 248GB partition it seemed to only take 4GB.

---

### Post by psusi on 2011-07-07
> **jcd29 said:**
> Damn. Why does that take up so much space? With a 248GB partition it seemed to only take 4GB.

Because each block group is 128 mb and uses 2mb for the inode table.  You can lower the inode ratio when you format if getting 1% more space is that important to you.

---

### Post by jcd29 on 2011-07-07
> **psusi said:**
> Because each block group is 128 mb and uses 2mb for the inode table.  You can lower the inode ratio when you format if getting 1% more space is that important to you.

I admit I know almsot nothing about inode tables, so that's why I'm a little lost :)

But thanks a lot for the info!

---

