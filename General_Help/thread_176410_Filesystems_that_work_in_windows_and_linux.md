---
title: "Filesystems that work in windows and linux"
date: 2006-05-14
forum: General Help
---

### Post by theswortz on 2006-05-14
I was wondering what filesystems work in both linux and windows. I want to format my external harddrive with a filesystem that will work on both. I know about fat32 but are there any others?

---

### Post by Sef on 2006-05-14
ext2 will work with both.

---

### Post by theswortz on 2006-05-14
Which one is better, fat32 or ext2?

---

### Post by shrimphead on 2006-05-14
ext2 is more stable, but requires a bit more effort to get set up (from the windows side)

personally I keep my usb key formatted as fat32 and it's never caused me any problems

---

### Post by theswortz on 2006-05-14
Aren't there size limitations for fat32 though. I want to setup my BitTorrent client to save to the external drive and some of the things I download, such as linux isos, tend to get pretty big.

---

### Post by dirwood on 2006-05-14
fat32 has a 4GB filesize limit.

---

### Post by minisori on 2006-05-14
[QUOTE=shrimphead]ext2 is more stable, but requires a bit more effort to get set up (from the windows side)[/QUOTE]

effort?

[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

Get those drivers and install on windows then you will be able to write/read ext2/ext3 from there.

---

### Post by shrimphead on 2006-05-14
[QUOTE=minisori]effort?

[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

Get those drivers and install on windows then you will be able to write/read ext2/ext3 from there.[/QUOTE]

more effort as in you actually have to dl and install something unlike fat32.

I totally forgot about the size limitations tho, my bad :(

---

### Post by dirwood on 2006-05-14
[QUOTE=shrimphead]I totally forgot about the size limitations tho, my bad :([/QUOTE]
yeah, but FAT32 is usually fine, as long as no DVD ISOs or other large files are downloaded.

---

