---
title: "Universal format for Externals ?"
date: 2011-01-14
forum: General Help
---

### Post by helios16v on 2011-01-14
I have a 500 GB external hard drive that is screwed up and wont let me copy any files to it on Ubuntu, I plugged it into my dads iMac and it works perfect so clearly this is just an OS 10 thing.

I bought a 320 GB external a few days ago to back up the 270GB of files on the 500 GB so I can format it to a Universal format that will work fine on Ubuntu, OSX, and Windows.

The problem I had was Ubuntu telling me I don't have permission to change anything even in terminal with the chown and chmod commands, nothing worked so I have everything backed up onto the 320 GB right now and I would just like to know what format I can put the 500 GB to that will work in all three operating systems.

Thanks :)

---

### Post by srs5694 on 2011-01-14
First, be aware of the fact that what most people mean by "formatting" a disk can involve one or more of several different operations. Two that are likely to be relevant for you are creating partitions and creating filesystems.

Second, if the disk is usable from OS X, chances are good that it uses the Apple Partition Map (APM) or GUID Partition Table (GPT) partitioning scheme. Linux understands both, but AFAIK Windows doesn't understand APM without special software, and you need Windows Vista or later (or some earlier versions on some platforms) to understand GPT. The best cross-OS compatibility for partition tables is with the old Master Boot Record (MBR) system, which is recognized by just about everything these days, including Linux, OS X, and Windows. Thus, you may need to change the partitioning system to MBR. If you don't care about pre-Vista Windows compatibility, GPT will also work, and has some minor advantages over MBR.

To actually perform both partitioning and filesystem creation, the easiest Linux tool is GParted. I believe there's a way to launch it from Ubuntu's menus, but I don't use the default Ubuntu menu system, so I'm not sure exactly where it is. You can type "gksudo gparted" in a Terminal window to launch it. This will produce its main window. You should select the disk you want to modify. You can then select Device -> Create Partition Table to create a fresh partition table. Use the default (MBR, which GParted refers to as "msdos") or change it by clicking the Advanced button. Be aware that creating a new partition table will make it hard to recover data from the disk, so be sure you're working on the correct disk!

With the new partition table in place, you can create a new partition (or more than one, if you like). The File Allocation Table (FAT) is the most cross-platform-friendly filesystem; however, it's old and it can't be used to store files bigger than 4 GiB, which is limiting if you want to store big multimedia files, backups, etc. If that's the case, your best bet for cross-platform use is probably the New Technology File System (NTFS). This is the default filesystem in Windows since XP (and the NT/200x line before that); Ubuntu supports it for read/write operations; and OS X supports it in read-only mode. To get read/write support in OS X, you'll need to add third-party software. There's a version of NTFS-3g (the same driver used in Linux) for OS X, but I'm not sure if it works with 64-bit kernels. Another filesystem option is Linux's ext2fs or ext3fs (but *not* ext4fs). There are Windows and OS X drivers for it, but I'm not sure how reliable they are. Certainly this option doesn't seem to be very popular. You could use Apple's HFS+, but you'd need to use it *without* a journal to get Linux read/write access, and IIRC the only way to get access from Windows is to use a commercial driver.

---

