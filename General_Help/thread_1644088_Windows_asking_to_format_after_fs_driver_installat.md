---
title: "Windows asking to format after fs driver installation"
date: 2010-12-12
forum: General Help
---

### Post by caspian915 on 2010-12-12
Hi all,

I just installed the driver from fs-driver.org to allow my Windows XP partition to read/write my linux mint partition. It seemingly worked as advertised, I labeled the linux partition as L and pressed finished. When I went into Windows Explorer and clicked on the L drive, though, a dialog box came up asking if I wanted to format the drive. 

What exactly am I missing here?

thanks,
sps

---

### Post by Quackers on 2010-12-12
I'm not sure what's happening, but I definitely wouldn't format it.

---

### Post by caspian915 on 2010-12-12
I have no intention of formatting it. But I'm confused. I've been googling and looking all over trying to determine the best way to setup a dual boot XP/Linux Mint with shared data. I discovered the ext2 driver solution, ran it, it set up the way it said it would, but it doesn't work at all. So there's something I'm missing, but I can't track the problem down anywhere.

any ideas?

---

### Post by Quackers on 2010-12-12
Forgive me, but I'm not familiar with Linux Mint. Does it use ext2 or ext3?

---

### Post by efflandt on 2010-12-12
Mint is based on Ubuntu, so default in recent Mint versions would likely be ext4 unless you specifically did manual partitioning and selected something else.  What format is the partition you are trying to read?

Ext3 is ext2 with journaling, so ext2 programs for Windows should be able to read that, but not sure if any can read ext4 yet, which may be the problem.

---

### Post by Quackers on 2010-12-12
Ah, well that enlightens me, to a degree :-)  Thanks efflandt

---

### Post by oldfred on 2010-12-12
I would just create a shared NTFS partition for any data that you want to share. Using a foreign system to write into another can lead to problems. 

I do not write into my windows system partition unless I have to, to make repairs. I have a NTFS partition for all the data I may want. Some programs in windows do not want to save to a different locations and for those I made a .bat file just to copy data to the shared partition.

---

### Post by caspian915 on 2010-12-14
By the way, just wanted to jump back in here - thanks to everyone. I wanted to mention that I loaded GParted and discovered that indeed it was the Ext4 issue, so instead I created a NTFS partition for everything. I've heard there can be some issues with that and Linux though - any thoughts? The searches I did for it kept contradicting each other about whether it should be FAT32 or NTFS.

---

