---
title: "Ext4 Filesystem driver for windows?"
date: 2010-08-20
forum: General Help
---

### Post by szh on 2010-08-20
Is there an Ext4 filesystem driver for windows?

---

### Post by lukeiamyourfather on 2010-08-20
No, but there is for ext2 and ext3.

---

### Post by wirelessmonkey on 2010-08-20
Actually, there is kinda... it's not a full read/write driver, but this:
[http://ext2read.blogspot.com/2010/04/ext2read-22-released-now-with-lvm2-and.html](http://ext2read.blogspot.com/2010/04/ext2read-22-released-now-with-lvm2-and.html)

works great for me accessing my ext4 partitions from Win7 Pro x64. It is only read/copy though.

---

### Post by szh on 2010-08-22
Thanks for the answers.
Hopefully someone will release a full driver soon.

---

### Post by Bazirker on 2010-09-15
I am absolutely appaled that there is no ext4 read/write support for Win-doze yet.  While I dislike using Windows as much as the next Ubuntu user, there's simply a lot of software that I need XP to run and a dual-boot machine is a must, and I know several other linux users who are in the same situation.  Being unable to fully access my ext4 linux filesystems is a great way to keep Windows configured as my primary OS on my computers just because it's the only way I can make sure I always have access to all my files.

Is anyone working on this?  And a better question, why don't more people care about this?  Why is ext4 being pushed as the default filesystem choice for Ubuntu if it's harder to access (e.g. less open?) from other sources?

---

### Post by szh on 2010-09-15
I simply started using Ext3.

---

### Post by Bazirker on 2010-09-15
> **szh said:**
> I simply started using Ext3.

My point is that you shouldn't have to.  The code is all open, and a windows driver would certainly get used a lot...


Is there a way to convert an ext4 filesystem into an ext3 without doing a bunch of file swapping, etc?  I already set up my / as ext4.

---

### Post by Nythain on 2010-09-15
i cant even get any of the more popular ext2/3 drivers to recognize my current ext3 partitions created with gparted... first i thought it was the 256 inode factor, but i've tried numerous drivers and browsers that support 256 inode and still no luck :(

---

### Post by ouija on 2010-12-18
[http://www.ext2fsd.com/](http://www.ext2fsd.com/)

Works for Windows 7 / Vista and supports EXT2 / EXT3 and EXT4
(although I have write disabled, so I couldn't tell you if it actually supports writing to EXT4 but I wouldn't advise it)

It can be a little problematic getting the drive actually mapped, but if you choose to mount it like a USB drive using the program (it gives you different options) it works best I find.

---

### Post by ThorX89 on 2011-05-28
It's too bad there isn't one fully compatible with EXT4. EXT4 is extremely fast. I heard even Google started using it because of the speed as it significantly outperforms NTFS. An EXT4 windows driver would definitely get used and it's a pity nobody has made one yet given the specs for the system are open source.
I'd even pay for it if there was an EXT4 driver windows.

---

### Post by FrankTKO on 2012-03-01
Love to see this thread as SOLVED... but actually, there is no solution ;)

---

### Post by babygenius55 on 2012-07-17
I just found this [HTML]http://www.diskinternals.com/linux-reader/[/HTML].

Wonderful...better than ext2explore, and ext2fs.  Does ext4, and reiser fs as well.  I haven't tested the reiser fs though.

---

