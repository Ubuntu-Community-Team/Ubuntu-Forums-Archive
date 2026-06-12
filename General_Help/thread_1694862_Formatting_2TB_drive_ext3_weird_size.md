---
title: "Formatting 2TB drive ext3 weird size"
date: 2011-02-25
forum: General Help
---

### Post by randumnumber on 2011-02-25
Hello all I just bought and installed a western digital 2tb harddrive I used Gparted GUI to format it to ext3, after i format it however Gparted reports the File System as UNKNOWN. I dont like the looks of this already. Then after it was all done i mounted it and looked at the size info of the disk, it says total capacity is 1.8TB this is to be expected because of the manufacture calculation scam. BUT it says that 93.3GB of the file system are already used and i have 1.7TB free. 

My questions to you guys are.

1. Why doesn't Gparted see the File System as ext3
2. Why are 93.3GB already used on a fresh drive?

NOTES
harddrive mode is WDC WD20EARS-00M

---

### Post by mr_luksom on 2011-02-25
Do you get different results with different filesystems? What if you format to ext4, ntfs or xfs?

---

### Post by An Sanct on 2011-02-25
EXT3 has journaling, thats where those 93Gb went. The benefit is that you can recover from a  crash better.

I would use EXT4 in your situation, unless there is some specific reason no to...

---

### Post by kelvin spratt on 2011-02-25
> **randumnumber said:**
> Hello all I just bought and installed a western digital 2tb harddrive I used Gparted GUI to format it to ext3, after i format it however Gparted reports the File System as UNKNOWN. I dont like the looks of this already. Then after it was all done i mounted it and looked at the size info of the disk, it says total capacity is 1.8TB this is to be expected because of the manufacture calculation scam. BUT it says that 93.3GB of the file system are already used and i have 1.7TB free. 

My questions to you guys are.

1. Why doesn't Gparted see the File System as ext3
2. Why are 93.3GB already used on a fresh drive?

NOTES
harddrive mode is WDC WD20EARS-00M
  I use that drive  I formatted mine with no problems I don't use ext3 way to bloated and slow try JFS its very fast and takes a lot less space.

---

### Post by randumnumber on 2011-02-25
Like to add, solved it myself, main issue is the sector size problem with the new WDxxEARS harddrives...I had to do a manual config with parted, and set the start of the partition to 4096, now the drive is recognized and FLYS!! transfering @ 30.0 MB/s from my old IDE drives to this drive. 

Here is the guide i used to set the drive up correctly:
http://community.wdc.com/t5/Desktop/Problem-with-WD-Advanced-Format-drive-in-LINUX-WD15EARS/td-p/6395;jsessionid=B95EF9635BF46BC4698ECB5AC0EC6C5D"]http://community.wdc.com/t5/Desktop/Problem-with-WD-Advanced-Format-drive-in-LINUX-WD15EARS/td-p/6395;jsessionid=B95EF9635BF46BC4698ECB5AC0EC6C5D

I actually set it up with EXT4(ext3 was mistype) because i didnt want file fragmentation, im using it for media storage and playback.

Thank you all for the advice. I love this forum, always a quick response and suggestions.

---

### Post by srs5694 on 2011-02-25
I'm not sure why GParted wasn't recognizing your partition's filesystem type, but it seems unlikely to me that it's related to the drive's Advanced Format (4096-byte sector) technology, since to software, these drives look just like drives with conventional 512-byte sectors. It's possible this is a bug in some versions of GParted related to the way partition alignment has been changing recently, though, and by changing the alignment, you worked around this bug. That's sheer speculation on my part, though.

Issues with disk size discrepancies usually boil down to one or more of three factors:


[list]
[*]**[SI units](http://physics.nist.gov/cuu/Units/prefixes.html) vs. [IEEE-1541 units](http://en.wikipedia.org/wiki/IEEE_1541)** -- You referred to this as a "scam," but it's not; it's a matter of gross misuse of SI units by most of the computer industry in the early years, followed by standardization on new units being slowly (and incompletely, as of yet) adopted. In brief, the SI prefixes (kilo, mega, giga, and so on) should be used in reference to power-of-10 measures, while IEEE-1541 units (kibi, mebi, gibi, and so on) should be used in reference to power-of-2 measures. Once everybody uses these units correctly and understands the rules, there'll be much less confusion. Until then, confusion will continue. I'm belaboring this point because I think it's important that people understand it.
[*]**The journal** -- As An Sanct said, the journal on a journaling filesystem consumes some space. The precise amount depends on the filesystem type and the size of the filesystem. You can learn how much space an ext3/4 journal is consuming with dumpe2fs, as in "sudo dumpe2fs /dev/sdc2 | grep Journal" to find the size of the journal on /dev/sdc2. The "Journal size" line tells you the size of the journal.
[*]**Reserved space** -- By default, ext2/3/4 filesystems reserve 5% of their capacity for use by root, so that root may create files in the process of recovering the computer should ordinary users fill up the filesystem. Depending on the utility, this amount might or might not be subtracted out in capacity estimates. In most cases, 5% reserved space is excessive on modern drives, so you might want to reduce it with tune2fs, as in "sudo tune2fs -m 1 /dev/sdc2". This example reduces the reserved space to 1% on /dev/sdc2. On some drives, you might even want to reduce it to 0%.
[/list]


FWIW, 5% of 1.8 TiB is 92 GiB. That's the vast majority of the discrepancy you've reported, so chances are most of what you're seeing (after correcting for SI vs. IEEE-1541 units) is that 5% reserved space. The rest is probably the journal.

Also, keep in mind that different filesystems allocate space in different ways. Thus, you might be able to store more files on a disk that seems to have less free space than on a disk that seems to have more free space. ReiserFS is noteworthy in this respect; when storing small files (a few KiB in size) it does a better job of cramming them in together than do most other filesystems. This effect is less likely to be important with big files than with small files.

---

### Post by randumnumber on 2011-03-03
Well, after doing it manually in parted, Gparted recognized the partition type with no problems. If you look up info on the WD20EARS it is a common problem. Gparted was starting the partition on a weird byte like 37 or something. It has to start on a number greater than 512 and divisible by 512, I did mine at 4096 and it works flawlessly.

Also the bug you are reffering to is not just in gparted.. it is in the OS itself, if you look up the info on the disk at command line it reports the page size as 512. There is a bug report filed but it has not been resolved.

---

