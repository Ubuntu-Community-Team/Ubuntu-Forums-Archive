---
title: "600Gb - Partitioning advice needed"
date: 2006-04-02
forum: General Help
---

### Post by funkenstein on 2006-04-02
Hi all, I'm running Ubuntu on a gigabyte mobo that allows for hardware RAID. 
I'd like to get some opinions about whether I should or shouldn't RAID my two 300Gb maxtor disks to make a 600Gb RAID. 

I'd also like to know how I should be formatting them- in other words- what filesystem should I use- ext2/3? reiserfs? jfs? with or without LVM??


Thanks,
Jonathan.

---

### Post by hollywoodb on 2006-04-02
unless you actually need to *use* 600 GB, if you can get away with a measly 300 GB I would recommend RAID 1 (or 3 if your mobo supports it).

[RAID Definitions]("http://www.integratedsolutions.org/raid_ov.htm")

You don't realize how great mirroring is until a drive fails ;)

---

### Post by Iandefor on 2006-04-02
I'd use ext3 in a mirrored RAID array, unless you're a speed demon and don't mind the increased risk to your data, in which case you might like a striped RAID array better.

---

### Post by funkenstein on 2006-04-02
yea, well, the vital data gets regularly backed up onto several different mediums, but I do lots of video editing work - which is why the speed comes into question. 
I guess the real question has more got to do with the filesystem - which one performs best, while having a good balance of data integrity...
](*,) too many questions... NOOOOOO!! 

might just go for 2x300Gb ext partitions and deal with it... (but I don't wanna...)

---

### Post by Iandefor on 2006-04-02
Here are a few filesystem comparisons:
[URL="http://www.gurulabs.com/goodies/ext3_vs_reiserfs-1.php"]
ext3 vs. reiserfs[/URL]
[URL="http://www.as220.org/jb/linux/"]
Linux Filesystems Comparison[/URL]

[Which File System?]("http://faq.storagereview.com/tiki-index.php?page=WhichFileSystem")

---

### Post by pwrstick on 2006-04-04
Hello,

From the small amount of research that I've done, Reiser4 seems to be the fastest, latest and greatest (successor to ReiserFS), but requires some tinkering to get Ubuntu to mount it.

The webpage is here:  [http://www.namesys.com]("http://www.namesys.com") and has some benchmarks.  Maybe that will inspire you toward a specific file system.

---

### Post by Ian Maxwell on 2006-04-04
Actually, if I were in your position I wouldn't RAID at all. Rather, I would use one disk as a backup, and set up a cron job to sync them overnight. A mirrored RAID protects against hardware problems ("whoops, a head crash"), but not software problems ("whoops, I just typed 'sudo rm -R *' in the root directory").

---

### Post by funkenstein on 2006-04-05
Thanks for the input.

I'm afraid to say that i will not be heeding the warnings about data loss and will *attempt* to go for a fakeRAID0 reiser4 config. The logic behind it is that whatever I really do not want to lose I can back up onto dvd/dual layer/bluray when it comes out, or on my 160Gb SATA  drive. I just need the storage for, funnily enough, temporary stuff... here's a thought - Can I put my /tmp there? That way it's obvious to me as a usr that it's dangerous to put stuff there, but at the same time allowing any apps that use /tmp to run much faster... hmm... now I have to go and find out how to configure raid on my machine, but that's a separate topic entirely.....

What isn't a seperate topic is what is the fstab line to mount reiser filesystems? I'm pretty new to all this, and up to now I've just been mounting fat/ntfs using the easylinux.info guide, or I've copied the / line from my fstab and changed the mount point and drive to use.... I've got no idea what all the other details mean (well, a very rough idea, I suppose.... )

---

### Post by Ian Maxwell on 2006-04-05
When you say "puy my /tmp there," do you mean on a specific one of the striped disks? Whether you use a striped or mirrored RAID, you can't put specific things on specific disks. A striped RAID will break all data up across the two, while a mirrored RAID will put all data on both.

---

### Post by funkenstein on 2006-04-09
Yea, I got that much. and I meant to put /tmp on the RAID array. striped across both. making it slick and fast and stuff... either way, too much work writing my thesis, so the entire project's on hold.... :(

---

