---
title: "Most compatible fs for pendrives?"
date: 2011-01-27
forum: General Help
---

### Post by outofsync on 2011-01-27
I'm going to buy a new pendrive (32GB or 64GB), and I'd like to use it with Ubuntu 10.10, Mac OSX, and Vista, but most of the times I'll use it with the Ubuntu box.

What would be the best filessystem for formatting it, so that it supports as much features as possible from my ubuntu ext4 filesystem, while still being compatible with OSX and Windows?

Is FAT32 still the best option? Aren't there better options, with support for files bigger than 4GB?

Btw, are there some limitations in modern pendrives regarding the filesystem you can format them in?

Thanks!!

---

### Post by TeoBigusGeekus on 2011-01-27
I'd go with ntfs.

---

### Post by timgood on 2011-01-27
Ubuntu will always offer to format a USB pen drive as FAT32 because it is compatible with most Operating Systems. Although Ubuntu will read NTFS partitions, it will not write to them without additional software and the same is the case with OSX. So I would stick with FAT32, although the file size limitation is a pain.

---

### Post by mikewhatever on 2011-01-27
Fat32 or Ntfs should suite you. Guess since ntfs doesn't have the 4GB size limit, it's better then the other.

---

### Post by Grenage on 2011-01-27
NTFS, absolutely; FAT32 is only a consideration when dealing with legacy kit, or modern units like BR players which might only support FAT32.

---

### Post by cek on 2011-01-27
For cross platform use with Windows (assuming you don't want any user space utilities for communicating with the drive) will be FAT32 or NTFS.

Either way, you will lose functionality when copying files over (certain permissions, etc.) from ext4.

---

### Post by srs5694 on 2011-01-27
I'd go with FAT-32. Although both Windows and Ubuntu can read and write NTFS (contrary to what timgood claimed), there are two reasons why FAT-32 is more compatible for your needs:


[list]
[*]Only Windows has NTFS check features. In practice, this means that if you remove the drive without first selecting the option to unmount (or "safely remove") it in the OS, or if the computer crashes or the power fails and you just pull it out, you won't be able to do anything with the drive until it's been checked in Windows. This could be a serious problem in certain scenarios, particularly if you're sneakernetting it around to different locations, some of which don't have Windows computers handy.
[*]OS X doesn't have NTFS write support. I know of two add-on software packages (NTFS-3g and a commercial driver, I believe from Paragon) that provide NTFS write support. There's also a way to add it to OS X 10.6 by modifying a configuration file, but that option is reported to be dangerously buggy, so I wouldn't try it. In any event, if you need to write to the drive in OS X, NTFS is a poor option. It might be acceptable if you've got a limited number of OS X machines and you're willing to install the third-party NTFS drivers, though.
[/list]


The biggest drawback to FAT-32 is, as you seem to be aware, its 4 GiB limit on file sizes. If this will be a serious problem, using NTFS and dealing with its limitations might be acceptable; but otherwise, FAT-32 is superior in its cross-platform support, which seems to be the biggest issue here.

Surprisingly, although there are Windows and OS X drivers for ext2fs and ext3fs, they seem to get poor reviews. I guess they just aren't being very well maintained. You'd also have to install them on all your Windows and OS X machines.

---

### Post by coffeecat on 2011-01-27
Just to add a couple of comments about NTFS. Ubuntu has had (reliable) NTFS write support for a few years now - let's be sure of that, despite what an earlier poster said.

I've installed the ntfs-3g driver on my Mac Mini running Snow Leopard. It works, but it's slow. If you're having to use NTFS instead of FAT32 because you want to store files larger than 4GB, that's a real issue.

Your question comes up a lot: which filesystem to use that supports files > 4GB and which you can use in Windows, Linux and OSX? There's no easy answer. My solution is to use more than one external drive: NTFS for Windows/Linux and HFS+ (you must use non-journalled) for OSX/Linux.

---

### Post by srs5694 on 2011-01-27
> **coffeecat said:**
> Your question comes up a lot: which filesystem to use that supports files > 4GB and which you can use in Windows, Linux and OSX? There's no easy answer. My solution is to use more than one external drive: NTFS for Windows/Linux and HFS+ (you must use non-journalled) for OSX/Linux.

Your solution would even work on just one drive, but with two partitions. That would reduce the storage capacity for any given OS transfer pair, of course; but it might be better to have one higher-capacity USB flash drive than two smaller-capacity drives. Also, if you do it this way, make sure the NTFS partition comes *first*; Windows insists on treating USB flash drives as "superfloppies," meaning that it will mount only the first partition on the drive. Neither Linux nor OS X is so limited, so the HFS+ partition can come second and both OSes will be able to read it.

---

### Post by coffeecat on 2011-01-27
> **coffeecat said:**
> My solution is to use more than one external drive: NTFS for Windows/Linux and HFS+ (you must use non-journalled) for OSX/Linux.

> **srs5694 said:**
> Your solution would even work on just one drive, but with two partitions. That would reduce the storage capacity for any given OS transfer pair, of course; but it might be better to have one higher-capacity USB flash drive than two smaller-capacity drives. Also, if you do it this way, make sure the NTFS partition comes *first*; Windows insists on treating USB flash drives as "superfloppies," meaning that it will mount only the first partition on the drive. Neither Linux nor OS X is so limited, so the HFS+ partition can come second and both OSes will be able to read it.

Now there's an interesting idea. I hadn't though of that: NTFS and HFS+ partitions on the same drive. It could be a reasonably flexible option considering that the read-only support for NTFS in MacOS is not that bad. But a question: which partition table type would you choose for this, MBR or GUID?

---

### Post by srs5694 on 2011-01-27
Either Master Boot Record (MBR) or GUID Partition Table (GPT) would work, provided you only care about Windows Vista or 7. If you want Windows XP or earlier to be able to read the drive, you'd need to use MBR. Likewise for some other older OSes, including older versions of Linux or even a modern Linux if somebody's recompiled the kernel and omitted GPT support from it. Overall, MBR is probably the safer choice.

---

### Post by uRock on 2011-01-27
Fat32 has none of those problems, so it will always be used on my media.

---

