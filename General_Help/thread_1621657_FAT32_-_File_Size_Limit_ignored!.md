---
title: "FAT32 - File Size Limit ignored?!"
date: 2010-11-14
forum: General Help
---

### Post by andyzammy on 2010-11-14
I have ubuntu running in a VM on a tower, to which a usb HD is connected. I couldn't find a way to format it with extx so had to settle for FAT32 in order for the vista host to recognise it before it'd let me use it as a shared folder with the ubuntu VM. at least i *think* it's fat32.. i chose default + quick format in vista when i formatted it.

I wanted to empty out my HD on my laptop, and forgetting that the HD was FAT (and thus has a  theoretical 4GB file size limit), i scp'd 80Gigs of an iso box set dvd collection. It didn't click until later on and when i came back expecting to see an error on my term, i was surprised to see the copy was successful. I tried out one of the iso's (~7GB) and VLC read and played it fine no prob.

Am i to assume that these iso's are safe and won't be destroyed somehow because they're breaking some FAT law or should i not trust them? I'm asking because i've still not deleted the iso's from my HD as i don't want to recopy them over if they do decide to die on me - it's rather tedious work..

what do people think about this? i've seen windows disallow creation of >4GB files before, why did it allow these iso's to be created?

---

### Post by The Cog on 2010-11-14
This is really a windows question. But it sounds to me as though the disk must have been formatted with NTFS rather than FAT. I think it's unlikely that windows is somehow hiding the file size limit. 

Can't windows tell you which it is?

P.S.
Before you go deleting the original files, make **very** sure that the files on the USB disk are really not truncated. It occurs to me that there may have been some disk caching going on and you were playing back from a cache somewhere rather than from the actual disk. I know it sounds unlikely for so many gigs to be cached, but better safe than sorry. Maybe reboot and then make sure you can play right up to the end of the files on the external disk.

---

### Post by dcstar on 2010-11-15
> **andyzammy said:**
> I have ubuntu running in a VM on a tower, to which a usb HD is connected. I couldn't find a way to format it with extx so had to settle for FAT32 in order for the vista host to recognise it before it'd let me use it as a shared folder with the ubuntu VM. at least i *think* it's fat32.. i chose default + quick format in vista when i formatted it.
..........

And guess what Vista defaults to? (hint: It isn't some crappy old filesystem type from 20 years ago like FAT).

---

### Post by andyzammy on 2010-11-16
i was pretty sure it was a FAT format, after checking up on the windows pc it confirms exFAT which puts the file size limit up to 16EB. this HD is now incompatible with my ubuntu laptop, which is just great..

plugging the HD into windows is supposed to be a temp fix and if I move all my data onto it now it won't be an enjoyable experience moving it back to an ext FS. can someone confirm I can scp it back using cygwin?

is there no FS out there that is compatible with both OS's and allow pretty standard file sizes?

---

### Post by mcduck on 2010-11-16
There is a FUSE-based driver module to support exFAT on Linux. It's currently in Beta, and there's also a PPA repository with Ubuntu packages.

[http://code.google.com/p/exfat/]("http://code.google.com/p/exfat/")
[https://launchpad.net/~relan/+archive/exfat]("https://launchpad.net/~relan/+archive/exfat")

---

### Post by WorMzy on 2010-11-16
> **andyzammy said:**
> i was pretty sure it was a fat format, after checking up on the windows pc it confirms exfat which puts the file size limit up to 16eb. This hd is now incompatible with my ubuntu laptop, which is just great..

Plugging the hd into windows is supposed to be a temp fix and if i move all my data onto it now it won't be an enjoyable experience moving it back to an ext fs. Can someone confirm i can scp it back using cygwin?

Is there no fs out there that is compatible with both os's and allow pretty standard file sizes?

ntfs.

---

### Post by coldraven on 2010-11-16
Yes, go for NTFS.
I formatted my 1TB USB external drive NTFS, windows and Linux have no problems with it.
Use Gparted, just make sure to select the correct drive from the drop down menu in the top right-hand corner of the window.

---

### Post by andyzammy on 2010-11-18
hmm the HD actually came with NTFS and wouldn't work with ubuntu.. that's why i changed it to begin with.

i'm sure all i've read about NTFS with linux is that it's "incompatible", and though there are ways and means to get it working it's not 100% reliable by a long shot.. has this changed recently?

---

### Post by WorMzy on 2010-11-18
Define "recently". ;)

It's been fine for the past few years now, though permissions aren't really supported. Due to this, you will need to specify both ownership and permissions in an fstab entry for the NTFS partition, otherwise everything on it will be owned as root. This tutorial can help you with that: [[COLOR="DarkGreen"]HOWTO: Mount NTFS partitions with specific ownership/permissions[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1604251").

EDIT: You may need to install ntfsprogs and ntfs-3g, though it's my understanding that Ubuntu comes with these packages pre-installed.

---

### Post by mister_playboy on 2010-11-18
For a spinning disk drive you'll want journaling and you should just use NTFS.  For a USB stick, you can use UDF instead of FAT32 and it should work well on both Linux and Windows.  This lets you have a newer FS than FAT while not being stuck with the Windows-only exFAT.

---

