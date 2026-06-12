---
title: "Preparing my laptop harddrive for instilation"
date: 2009-08-05
forum: General Help
---

### Post by the lemming on 2009-08-05
Hello

I'm hoping to dual boot Ubuntu with Vista Basic on my laptop.

I am hoping to seperate my hard drive into three areas
Partition for Vista Operating System
Partition for shared data
Partition for Ubuntu.

So far I am going to have the first two partitions as NTFS however I do not know what to do with the third partition.

I understand that I am going to break it into three sections, a part for the /, a part for home and a part for the Swap.  The problem is that I do not know which file structure to use for / and Home.

Could somebody please tell me what file structure I need to format the relevant partitions of my drive?

I've tried to use the Ubuntu partition tool but I get confused so I am going to use gParted to do the task for me.

Cheers

---

### Post by t0p on 2009-08-05
I suggest you format your ubuntu partition(s) as ext3.

People are also using ext4 nowadays, and I believe  it is officially described as "stable".  But I've never used it, so I recommend ext3.

You're right in formatting both the Windows and the shared data partitions as NTFS.  Ubuntu can read and write to NTFS okay, but Windows can't deal with ext3/4 by default.

---

### Post by Scotty Bones on 2009-08-05
If you are going to break ubuntu into root and home partitions you are going to need to use a special setup, as you will end up more than 4 partitions. 4 primaries is the max.

I suggest: 1 primary partition for windows (this is a requirement for windows), a second primary for the swap partition (placed at the end of the disk), and an extended partition for root, home and share partitions.

It would be best to do this from a live environment using either the ubuntu live-cd or the [parted magic]("http://partedmagic.com/") live-cd.

---

### Post by the lemming on 2009-08-06
> **Scotty Bones said:**
> If you are going to break ubuntu into root and home partitions you are going to need to use a special setup, as you will end up more than 4 partitions. 4 primaries is the max.

I suggest: 1 primary partition for windows (this is a requirement for windows), a second primary for the swap partition (placed at the end of the disk), and an extended partition for root, home and share partitions.

It would be best to do this from a live environment using either the ubuntu live-cd or the [parted magic]("http://partedmagic.com/") live-cd.

I was intending on an extended partition for the Ubuntu setup which included the Swap file.  May I ask why you suggest a primary partition for the Swap file?

Cheers

---

