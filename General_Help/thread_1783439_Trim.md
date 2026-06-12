---
title: "Trim"
date: 2011-06-15
forum: General Help
---

### Post by Atrom on 2011-06-15
So, I'm curious is there any method of automatic trimming in ext2 file systems, or any way to set this up. I know the new Kernel and ext4 are being shipped with automatic trimming, but is there a way to make ext2's auto TRIM? I was assuming possibly setting up a cronjob to run wiper.sh?

---

### Post by Atrom on 2011-06-15
ANY help on the topic at all will be greatly appreciated :)

---

### Post by Herman on 2011-06-16
I use  [DiskTRIM]("http://disktrim.sourceforge.net/") to run wiper.sh in my OCZ Vertex.

Here's a link to an old thread which may be getting a little out of date by now, but contains a lot of links plus a few tips and tricks that I still think are interesting if you enjoy reading, [[ubuntu] ext4 without journaling]("http://ubuntuforums.org/showthread.php?t=1404664").

---

### Post by Atrom on 2011-06-17
Fun read, but that's for Ext4 no? I believe most SSD's run on EXT2.

---

### Post by pqwoerituytrueiwoq on 2011-06-17
you can put what ever partition you want on a ssd i have a ext4 partition on mine but i am using a kernel that does not support trim since it is uncommon for me to write to my ssd (i try to keep it as low as possible) i don't really see the need for trim

---

### Post by LowSky on 2011-06-17
My SSD is using EXT4... you can use any format you wish.
Where do these odd rumors come from?

---

### Post by pqwoerituytrueiwoq on 2011-06-17
> **LowSky said:**
> My SSD is using EXT4... you can use any format you wish.
Where do these odd rumors come from?
dont believe i can have a ext4 partition on a [ssd]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820139428")?
here are screen shots as proof
Edit:
i use a separate hdd for /var, /tmp, and /home
when i get more ram i will make /tmp a ram disk
also i use noatime and nodiratime on my / partition (my ssd only has / on it)

---

### Post by Herman on 2011-06-18
> Fun read, but that's for Ext4 no? I believe most SSD's run on EXT2. I use ext4 for my SSD (and other flash memory) and mount it noatime.

Don't take my word for it, read a few of [Theodore Tso's blogs]("http://www.linuxfoundation.org/blog/9"), in particular this one, **[SSD’s, Journaling, and noatime/relatime]("http://www.linuxfoundation.org/news-media/blogs/browse/2009/03/ssd%E2%80%99s-journaling-and-noatimerelatime")**
> On occasion, you will see the advice that the ext3 file system is not  suitable for Solid State Disks (SSD’s) due to the extra writes caused by  journaling — and so Linux users using SSD’s should use ext2 instead.    However, is this folk wisdom actually true?   This weekend, I decided to  measure exactly what the write overhead of journaling actually is in  actual practice.I'm not sure if it's important or not, but use this command to set the stripe width, (to try to align the file system),```
sudo tune2fs -E  stripe_width=128 /dev/sda1
```Where: the / is in /dev/sda1 - as  verfiied by the output from the blkid command.

---

### Post by Atrom on 2011-06-18
I wasn't saying you can't format it to Ext4 i'm just saying, most seem to run on Ext2.

---

### Post by WorMzy on 2011-06-18
Where are you pulling that statistic from?

---

### Post by Herman on 2011-06-18
I wouldn't bother concerning myself with what 'most people', or 'the majority' seem to think, say or do.

The sound logic and reasoning of someone like Mr Tso who actually knows what he's talking about backed up by experiments and testing is what I put my money on.

---

