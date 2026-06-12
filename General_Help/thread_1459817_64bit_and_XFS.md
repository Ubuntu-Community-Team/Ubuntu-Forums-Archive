---
title: "64bit and XFS"
date: 2010-04-21
forum: General Help
---

### Post by -humanaut- on 2010-04-21
Tomorrow I'm going to clean install Kubuntu 10.04 R.C. 64bit and I'm thinking of changing my default file system to XFS because it was designed specifically for 64bit systems. I have been a big fan of ext4 but does anyone use XFS with a 64bit system? Is there a performance gain in using XFS with amd64?

---

### Post by dcstar on 2010-04-22
> **-humanaut- said:**
> Tomorrow I'm going to clean install Kubuntu 10.04 R.C. 64bit and I'm thinking of changing my default file system to XFS because it was designed specifically for 64bit systems. I have been a big fan of ext4 but does anyone use XFS with a 64bit system? Is there a performance gain in using XFS with amd64?

You have misunderstood things, XFS has a 64-bit filesystem structure, the only difference in using it on a 32-bit OS is that it "only" has a maximum limit of 16TB instead of 8EB on a 64-bit system.

Planning on archiving the Internet, are you?

---

### Post by srs5694 on 2010-04-22
Although XFS does use some 64-bit pointers, and those are handled more efficiently on a 64-bit CPU than on a 32-bit CPU, the time penalty for using these 64-bit pointers on a 32-bit CPU is minuscule, compared to everything else the filesystem does (including, of course, the time to access the physical disk). Thus, there's little reason to consider the bit-ness of your CPU when choosing a filesystem.

That said, XFS does have its advantages. IMHO, it's the best choice at the moment for handling large files (say, those with sizes in the high hundreds of megabytes or more). Ext2fs, ext3fs, and ReiserFS all bog down a bit with such big files, whether you're using a 32-bit or 64-bit kernel. JFS, XFS, ext4fs, and Btrfs all handle big files much better. Of these, Btrfs is brand-new and not yet as trustworthy as the others; JFS has always seemed a bit less stable than XFS to me, although not enough so that I'd say it should be avoided; and ext4fs, although not as new as Btrfs, is still fairly new and there have been problem reports in the not-too-distant past. Thus, XFS is, IMHO, at the top of the list for filesystems that work well with big files. I'd put ext4fs and JFS about on a level below XFS, followed by Btrfs. Others may have other opinions on the matter, and my own opinion is subject to change, particularly as ext4fs and Btrfs mature.

Depending on your needs, IMHO the best option is to use ext3fs or ReiserFS for your root (/) partition and other partitions that hold mostly small files (those smaller than a couple hundred megabytes, give or take). If you need to store many large files (virtual filesystems for emulators, whole-disk backups, CD or DVD image files, MPEG recordings, etc.), create one or more separate partitions and use XFS, or perhaps JFS or ext4fs, for those partitions only.

---

### Post by -humanaut- on 2010-04-22
Doesn't really matter now im Etc4 will Ubuntu 10.04 R.C.

---

### Post by Lepy on 2010-04-22
My mythtv backend has run 9.10 and 10.04 64bit with the video storage directories formatted to XFS. They are fast, and there was only one point where there were mounting errors related to XFS but that was during 9.10 testing, the install was 32 bit at the time, plus the errors were fixed. 

The only thing you might want to keep in mind is that XFS partitions can not be shrunk, only grown.

---

### Post by -humanaut- on 2010-04-23
> **srs5694 said:**
> Although XFS does use some 64-bit pointers, and those are handled more efficiently on a 64-bit CPU than on a 32-bit CPU, the time penalty for using these 64-bit pointers on a 32-bit CPU is minuscule, compared to everything else the filesystem does (including, of course, the time to access the physical disk). Thus, there's little reason to consider the bit-ness of your CPU when choosing a filesystem.

That said, XFS does have its advantages. IMHO, it's the best choice at the moment for handling large files (say, those with sizes in the high hundreds of megabytes or more). Ext2fs, ext3fs, and ReiserFS all bog down a bit with such big files, whether you're using a 32-bit or 64-bit kernel. JFS, XFS, ext4fs, and Btrfs all handle big files much better. Of these, Btrfs is brand-new and not yet as trustworthy as the others; JFS has always seemed a bit less stable than XFS to me, although not enough so that I'd say it should be avoided; and ext4fs, although not as new as Btrfs, is still fairly new and there have been problem reports in the not-too-distant past. Thus, XFS is, IMHO, at the top of the list for filesystems that work well with big files. I'd put ext4fs and JFS about on a level below XFS, followed by Btrfs. Others may have other opinions on the matter, and my own opinion is subject to change, particularly as ext4fs and Btrfs mature.

Depending on your needs, IMHO the best option is to use ext3fs or ReiserFS for your root (/) partition and other partitions that hold mostly small files (those smaller than a couple hundred megabytes, give or take). If you need to store many large files (virtual filesystems for emulators, whole-disk backups, CD or DVD image files, MPEG recordings, etc.), create one or more separate partitions and use XFS, or perhaps JFS or ext4fs, for those partitions only.

Thanks for your input I myself do not trust ext4 yet and XFS though just open sourced seems more mature and ready i'll be using it when I install Kubuntu in about 30 minutes I will let you know how it handles and any problems. I have never been a huge can of the 'ext' series of filesystems as I feel there slower then JFS,XFS,ZFS,etc... though on 32bit systems they are the better choice after much research I think XFS is the way to go until BTRFS is ready for 64bit users as it was designed for 64 bit IRIX. Thanks for your input.

---

### Post by iponeverything on 2010-04-23
> I myself do not trust ext4 yet

I don't ether. Pushing it out the door as the default is a very effective way to flush it out, but I see enough to think that there are still some serious -though relatively obscure - data corruption issues with ext4.

---

### Post by -humanaut- on 2010-04-24
I tried an Install with XFS and honestly it felt very sluggish moving small files was painfully slow So I'm using ext4 right now until the final version comes out i'll clean install again with ext3 as I trust it more then JFS and it's performance seems somewhat faster then ext4 to bad Reiser4 is dead that has some great benchmarks.

---

### Post by srs5694 on 2010-04-24
ReiserFS isn't seeing much development, but it still works. Personally, it's my preferred filesystem for root (/), /usr, and most other system directories. I use ext2fs for /boot and XFS for anything that holds mostly really big files (like my MythTV recordings partition).

---

### Post by dcstar on 2010-04-25
> **iponeverything said:**
> I don't ether. Pushing it out the door as the default is a very effective way to flush it out, but I see enough to think that there are still some serious -though relatively obscure - data corruption issues with ext4.

Considering EXT4 has been used in Ubuntu for about 12 months now by many (many) users, one can see by the **lack** of issues now that it has evolved to a stable filesystem.

---

