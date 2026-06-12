---
title: "Min Limits on Filesystems"
date: 2009-11-04
forum: General Help
---

### Post by NvrBst on 2009-11-04
Hope I'm not way off the ball asking about file systems on the ubuntu forums ;)

So I have a nvram chip that has 128KB space.  The driver currently treats this almost like a file (I'm able to write to /dev/nvram and read).  I only use a max of ~4KB of the nvram space currently.

I was thinking maybe I'd be able to mount "/dev/nvram" to a folder and setup a filesystem on it.  This way it would be easier for others to use the extra space of the nvram.  I was unsure about the overhead of the various filesystems though (thinking ext2).  Wiki has max limits but nothing on min limits.

Is 128KB too small for a filesystem?  What type of usable space would be possible if say I went with ext2 or ext3?  Also would attempting to convert the /dev/nvram driver I have to work with the "mount /dev/nvram ..." be a fair bit of work?

Thanks.  More of a curiosity right now.  When I googled I found people asking about mounting 32KB nvram chips, and that 32KB is too small for filesystem, but, my 128KB chip is a fair bit bigger that 32KB.  Still too small?

---

### Post by kidders on 2009-11-05
Hi there,

> **NvrBst said:**
> I was thinking maybe I'd be able to mount "/dev/nvram" to a folder and setup a filesystem on it.Personally, I've never tried to do it, but it *ought* to be possible, I suppose.

> **NvrBst said:**
> Is 128KB too small for a filesystem?Only in some cases ... for example, the smallest possible JFS filesystem is 16MB. In general, 128k is too small for any journalised filesystem, so the only reasonable "conventional" choice is Ext2, imo.

I don't have an nvram chip I can write to safely, but I made do with a small file for a quick test, to get you some figures...```
# Create a 128k file to simulate your chip
dd if=/dev/zero of=small_filesystem bs=1024 count=128 

# Write an Ext2 filesystem into it, with no reserved blocks
# and a reduced number of superblock backups, to save space.
mkfs.ext2 -O sparse_super -m0 small_filesystem 

# Mount the filesystem & cd into it
mkdir loop
mount -o loop small_filesystem loop/
cd !$

# Create 10 empty files on the filesystem
for f in `seq 1 10`; do touch $f; done
touch: cannot touch `6': No space left on device
touch: cannot touch `7': No space left on device
touch: cannot touch `8': No space left on device
touch: cannot touch `9': No space left on device
touch: cannot touch `10': No space left on device
```

Yuck! Thankfully, you *can* squash more files into the available space by increasing the number of inodes (at the cost of usable disk space). With a bit of messing, I managed to create around 90 x 7-byte files (I just wrote the word "foobar" into lots of files). In another test, I got around 20 x 4k files out of it, before I ran out of space. In both cases, that equates to about 106/107k of actual disk usage ... something in the ballpark of 20% overhead, which isn't half bad, really. At filesystem sizes in the kilobyte range, I was expecting the worst!

Anyhow, I hope that answers your question ... or at least gets you *some* of the way. By the way, most Linux forums will happily deal with filesystem-related issues, in my experience. :-)

---

