---
title: "format for data partition"
date: 2011-07-02
forum: General Help
---

### Post by rng on 2011-07-02
I am planning to have a separate data partition to share files between ubuntu and windows. What is the best format to have- fat32 or ntfs? Please help.

---

### Post by wildmanne39 on 2011-07-02
> **rng said:**
> I am planning to have a separate data partition to share files between ubuntu and windows. What is the best format to have- fat32 or ntfs? Please help.Hi, nfts.

---

### Post by nzjethro on 2011-07-03
> Hi, nfts.

Haha, nice, to the point.

And I'd recommend ntfs too. The main reason being that you can't put files or size greater than 4GB on a fat32 drive. This means if you want to share a 1080p HD movie between the two, or a large game .iso, you'll run into issues. I found this out the hard way, and had to re-format my fat32 external to ntfs.

---

### Post by rng on 2011-07-03
Thanks for your replies. Is large file limitation the only issue? I am unlikely to need files of such size, at least in near future. Is there any issue regarding data corruption or loss in fat32? How real is this problem?

---

### Post by dino99 on 2011-07-03
ubuntu directly deal with windoz, no need headaches :)

---

### Post by rng on 2011-07-03
> **dino99 said:**
> ubuntu directly deal with windoz, no need headaches :)

I want to have a separate partition for data and I do not want to keep data on windoz partition.

---

### Post by dino99 on 2011-07-03
> **rng said:**
> I want to have a separate partition for data and I do not want to keep data on windoz partition.

so ext4 is your choice

---

### Post by rng on 2011-07-03
> **dino99 said:**
> so ext4 is your choice

Thanks for your replies. You suggest that I keep data on ext4 partition and access it thru windows using some utilities. Are these utilities reliable, safe and easy to use? How about ext3, since some old linux programs/distros may have problems accessing ext4. 

Also which particular utility would you recommend for reading ext3/4 partition from windoz.

---

### Post by steevven1 on 2011-07-03
In my experience, FAT32 is the most reliable, safe, and easily accessible from ANY operating system. There is a 4 GB file size limit.

If you need files 4 GB and larger, go with NTFS. It is about as reliable, and easily accessible from both Windows and Linux without any special utilities.

Ext4 or ext3 would be the very best if you ONLY needed to access the files from Linux, but if you plan to access them from Windows, it is a HUGE PAIN (or sometimes impossible) to set this up. Don't do it.

---

### Post by nzjethro on 2011-07-03
> **dino99 said:**
> so ext4 is your choice

If the choice is ext4 (or ext3) the files will be only readable by your Linux partition (well, you can find ways around this, but it can be very difficult). If you want shared data, it has to be ntfs or fat32.

I suggested ntfs because in my experience with it I have had no issues (no corruption, no data loss), plus if you ever need to exceed 4GB you don't have to go through the pain of having to reformat. But if you think that the 4GB limit won't affect you (e.g. if it will just be pictures, documents, or music files etcetera to be shared), then either will work.

---

### Post by wildmanne39 on 2011-07-03
Hi, also ntfs is faster then fat 32.

---

