---
title: "Formating Drive"
date: 2011-04-24
forum: General Help
---

### Post by ron177 on 2011-04-24
Dear all,

I am trying to format an external hard drive and wanted to know the pros and cons of various different formats offered in Linux. 

I hear that ext4 is better (most stable) than anything else (better than ext3 or ext2) for Ubuntu. I wanted to know where I can obtain more info on these various formats.

I want a format that would be (1) as stable as it can get in formating a hard drive, and (2) readable and writable in both Windows and other versions of Linux (say Mandriva).

How is NTFS by the way? Has anyone had positive experience with it?

Appreciatively,

Ron

---

### Post by bryanl on 2011-04-24
For cross platform capability, NTFS is probably the way to go. In Linux, there may be some performance trade-offs but that usually isn't an issue - and this may be an old consideration. 

NTFS support in Linux is much much better than ext-4 support in Windows from anything I can tell. The Mac I don't know about but I'd think it'd handle NTFS well, too, as it is rather common on the large external drives.

For those drives I only access in Linux, I use ext-4 and make sure to eliminate the 5% reserved space with tune2fs.

For the flash drives at 16 GB or under, I tend to use FAT32.

---

### Post by Joe of loath on 2011-04-24
Macs can't handle anything other than HFS+ and FAT16/32/64, and can read NTFS drives. If you want interoperability with a mac, you're stuffed :lol:

For Windows/Linux compatibility, NTFS is your best bet. It can handle files larger than 4gb, unlike FAT32, and can be read and written reliably by Windows and Linux.

---

### Post by HermanAB on 2011-04-24
Howdy,

I have experienced weird issues with NTFS and some versions of Windows, where files become read only after being copied from Linux to Windows, due to an ownership issue, requiring Admin privileges to resolve.

So, if you want trouble free file movement between Linux and Windows, then you need to use FAT on the removable disk.

---

### Post by KegHead on 2011-04-24
Hi!

I've used fat 32/usb sticks...no problems.

KegHead

---

### Post by ron177 on 2011-04-24
If I want to work on the Linux platform only, what is the best format? So let's forget about Windows or any other non-Linux OS'es. Can you please tell me whether ext4 is better than ext3 or ext2? Is ext4 really the best? Can it be read and written to in all Linux distributions?

---

### Post by KegHead on 2011-04-24
Hi!

When you format, you have three (3) Linux options.

KegHead

---

### Post by ron177 on 2011-04-24
One last thing: if I choose ext4 for my external drive, do I also have to have a swap partition on it as well? If so, how can I calculate how much I need for the swap partition?

---

### Post by srs5694 on 2011-04-24
Ext4fs is the latest in the family that began with extfs (now extinct), moved on to ext2fs and then ext3fs. Other Linux-native filesystems include ReiserFS, JFS, XFS, and Btrfs.

Measuring a filesystem's "stability" is tricky at best, and I don't know of any studies that have attempted such measurements. Thus, we're left with anecdotal evidence, which you should take with a grain of salt. My own impression from reading various forums is that any of the above-mentioned filesystems, with the probable exception of Btrfs, should be stable enough for most uses. Each filesystem has its fans and its detractors, the latter group being made up mostly of people who've lost data on a particular filesystem. Beyond that, if you care to fund a scientific study of the question, I'm sure somebody will take your money. (It would take funding or serious devotion; filesystem stability is not an easy thing to measure.) One thing that's easier to measure is filesystem development and maintenance. My impression is that there's more effort going into ext2/3/4fs, XFS, and BtrFS than into JFS or ReiserFS.

I excluded Btrfs as being "stable enough" because it's still under development, and the last I heard, it still lacked a filesystem check tool, so if you were to run into a problem, you could easily lose all the data on the disk, even if it might be recoverable if there were a filesystem check tool.

I've never before heard the claim that ext4fs is more stable than ext3fs; in fact, until perhaps a year ago, the suspicion was that ext4fs was *less* stable than ext3fs. (Ext4fs is the newest in this series, and only became non-experimental about two years ago.) Ext4fs *does* include improvements over ext3fs, but they have to do with features and performance -- ext4fs is faster at certain operations and it supports larger files and filesystems, for instance. These aren't likely to be very important issues for the average desktop installation, but at this point, I know of no reason to recommend ext3fs over ext4fs for an all-Linux system. (Some Windows tools to access ext2/3fs don't support ext4fs, though, so for cross-platform support, ext3fs is probably better.)

Regarding non-Ubuntu Linux distributions, the choices are identical, provided we're talking about recent distributions. Support for Linux-native filesystems comes in the kernel, so filesystem support is identical for distributions that use the same kernel. There are a few important caveats to this rule, though. The first is that different distributions may compile different drivers in their standard kernels. I'm not aware of any significant omissions on this score in popular distributions, though, and you can always compile your own kernel if you need to. A second caveat is that a distribution's installer might support a subset of filesystems. This can be an annoying limitation, but it can be overcome if you know how. A final important caveat is that some non-Linux filesystems, including read-write NTFS support, are provided by non-kernel packages. This doesn't really change the support equation much, though; it's just that you need the same version of the filesystem support package to be the same to be able to say that support is identical. (There are some more obscure and minor caveats relating to kernel patches and whatnot.) The ext2/3/4fs family, in particular, is popular and is supported by all the major Linux distributions, AFAIK.

Regarding NTFS, that support is provided by a non-kernel package (FUSE with NTFS-3g). This imposes performance limitations. Anecdotally, the NTFS-3g support seems to be fairly reliable, but I find it hard to believe it would be as reliable as Microsoft's own NTFS implementation, since NTFS is a closed specification -- the NTFS-3g driver was written by reverse engineering. NTFS is unsuitable for use as a Linux root (/) filesystem, but you can use it for data exchange. I'd recommend FAT over NTFS for data exchange *if* you can live with FAT's 4 GiB file size limit, but that's a big *if* these days. Any way you do it, I recommend using a separate data-exchange partition rather than writing to the Windows C: drive from Linux; that's inherently risky.

Regarding Macs, Linux includes pretty good HFS+ support, so you can mount HFS+ volumes and use them for data exchange. If Linux is to write to HFS+, though, the HFS+ volume should *not* use a journal, which is an important limitation. It's probably reasonable to go journal-less on a small- to-midsize data-exchange partition, but not on a really big partition. Also, since both Mac OS X and Linux use Unix-style permissions and ownership, you should be sure your UID numbers match up between the two OSes, or you'll have permissions problems.

---

### Post by srs5694 on 2011-04-24
> **ron177 said:**
> One last thing: if I choose ext4 for my external drive, do I also have to have a swap partition on it as well?

No.

---

