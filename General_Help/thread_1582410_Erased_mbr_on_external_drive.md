---
title: "Erased mbr on external drive"
date: 2010-09-26
forum: General Help
---

### Post by jcolyn on 2010-09-26
I have an 80GB external USB2 hard drive that has 4 files on it that I  would like to access/recover. The only problem is the mbr was  inadvertently deleted. This drive was only used for data storage and was  formatted originally NTFS. I have not formatted it or written any data  to it in the hope that I can recover.

Short of having to spend  money is there an easy way to undelete mbr and restore the files? I  tried one downloaded program but since it was a demo it would not  undelete. Have to buy to get that feature.

I will be working from a KDE desktop.

---

### Post by prshah on 2010-09-26
> **jcolyn said:**
> Short of having to spend  money is there an easy way to undelete mbr and restore the files?

Use testdisk (it's in the repos), and if it fails (unlikely), use the companion program photorec to recover files (loses filenames, though, and will also undelete previously deleted files, so not very convenient).

And when you say "erased MBR", I assume you mean erased MBR+Partition record (MBR=446 bytes, MBR+partition record=512 bytes)

If you have lost ONLY your MBR (ie, files are accessible) then you don't need to do this (testdisk).

---

### Post by jcolyn on 2010-09-26
> **prshah said:**
> Use testdisk (it's in the repos)

Testdisk did the trick. It was already installed when I checked the repo..

> **prshah said:**
> And when you say "erased MBR", I assume you mean erased MBR+Partition record (MBR=446 bytes, MBR+partition record=512 bytes)

I was attempting to reformat another backup drive connected to the system but selected this one instead.

> **prshah said:**
> If you have lost ONLY your MBR (ie, files are accessible) then you don't need to do this (testdisk).

The drive was showing unallocated space so nothing was accessible. Most of the photos were backed up in another drive but I had 4 of my Nikon raw images on this one that I did not want to loose. They are now backed up to other drives.

Thanks for the help

---

