---
title: "OH MY SCIENCE! I formatted over 300+GB of data!"
date: 2010-03-30
forum: General Help
---

### Post by bumblestiltskin on 2010-03-30
Hey Forum --

I have formatted over 300 plus GB of data on my terabyte 'backup' hard drive. As you can probably guess, I got lazy and started using it for straight data storage not backed-up anywhere else. 

I formatted over it by attempting to make a Ubuntu boot drive from a flash USB stick using 'USB Startup Disk Creator' in the System>Administration menu. I went to format the flash drive (1,000 MB) and accidentally chose the backup hard drive (1,000 GB). Immediately after clicking format, I realized my mistake. Perhaps in a boneheaded move, I pulled the power cord on the USB backup hard drive. After quiting the program, I plugged the hard drive back in. 

Now it won't mount under Ubuntu 9.10 (or at least it doesn't show on the desktop). But it will show up under Windows XP. When I attempt to access it there, Windows XP wants me to format it. Of course, I didn't do that.

I've tried using TestDisk to recover the partition. Running under Ubuntu or Windows, it sees the hard drive and it attempts to find a missing partition, but it does not find any.

In TesDisk I'm using:

Partition Table Type: Intel
Analyze
Quick Search
Deeper Search (after no results from Quick Search)

In the screen before I start Quick Search, it shows me my partition structure. Here is what is shows:
 
```

Current partition structure:
     Partition                  Start        End    Size in sectors

Invalid FAT boot sector
 1 * FAT32 LBA                0   1  1 121600 254 63 1953520002
 1 * FAT32 LBA                0   1  1 121600 254 63 1953520002

```

Hopefully there is a way out of this. I will have a very, very upset wife if I can't recover some of this data.

Here's to hoping!

---

### Post by schumifer on 2010-03-30
Try through windows with file scavenger.pm if you need illegal help

---

### Post by NovaWasp on 2010-03-30
Try to use photorec.  It's installed with test disk.  It will find media files pretty good, but it's not great with newer office documents.
 
```

sudo photorec

```
 
once installed to launch.
 
Fairly self explanitory, but there are quite a few tutorials out there.
 
You're files will not have their original names.
 
You can run photos through AmoK Exif sorter to resort by date as that meta data will probably survive.  Rhythm Box should resort and rename the MP3s.
 
good luck.

---

### Post by bumblestiltskin on 2010-03-30
> **schumifer said:**
> Try through windows with file scavenger.pm if you need illegal help

Thanks schumifer for the recommendation. I'll download and see if it will at least find the files. Reviews seem promising. I'll report back in a bit.

> **NovaWasp said:**
> Try to use photorec.  It's installed with test disk.  It will find media files pretty good, but it's not great with newer office documents.

If File Scavenger doesn't work, I'll give photorec a try. Thanks!

---

### Post by Johnny B on 2010-03-30
the very first thing you should do is make a bit for bit copy of the partition with dd, that way any mistake you make will cost you time and not data.
since you cut the power so abruptly, you should run fsck on the copy. cutting power while the disk is being used is probably just as bad as formating it.
now you're ready for testdisk.

---

### Post by bumblestiltskin on 2010-03-30
> **Johnny B said:**
> the very first thing you should do is make a bit for bit copy of the partition with dd, that way any mistake you make will cost you time and not data.
since you cut the power so abruptly, you should run fsck on the copy. cutting power while the disk is being used is probably just as bad as formating it.
now you're ready for testdisk.

That's a good idea. I'll need to get a backup drive for my backup drive. ;) I realize now cutting the power wasn't the best idea, but I panicked.

---

### Post by jsriz on 2010-03-30
Well exactly same thing happened to me an year ago when i first tried to install ubuntu .my image was in 500GB trancend harddisk and started formatting the hdd instead of the pendrive but unplugged it as soon i got to know my mistake 
I used test disk:
After the deeper search it gave me an option of writing the partition table (or something like that) 
I did that and I got to access all my data 
so try looking for that option
If you dont get any  option I guess I was lucky
if you are in a worst case and have to format the disk dont do any data transfer on that 
there are many proprietory data recovery utilities for ntfs and fat32 on windows

---

### Post by bumblestiltskin on 2010-04-07
Quick follow up on this thread. 

Neither Testdisk or Photorec were able to recover anything from my drive. But...

File Scavenger was an absolute life saver. It found basically everything on the drive. To my knowledge (and from the log) only two files were not retrievable. Not bad for 300+ GB of data. 

So now I've got the files split between two 500gb drives and will be backing those up to the 1tb drive for true redundancy. 

Thanks to everyone who helped in this thread and especially schumifer for recommending File Scavenger. Without that program, all my files would be lost.

---

