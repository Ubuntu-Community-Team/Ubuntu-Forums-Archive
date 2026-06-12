---
title: "Need help setting up hard drive partition with advanced settings"
date: 2010-11-27
forum: General Help
---

### Post by TheOnlyMrK on 2010-11-27
Basically I got Windows 7 installed on my laptop and it's been doing nothing but slowing down more and more even though it isn't used for much more than basic internet use and I realized the hard drive was the cause, I did a bunch of stuff to try to fix it that I won't get into here, and in basic I'm to the point I'm just going to reinstall Windows 7, but this time with the help of Ubuntu's partitioning utilities.

I've already had the first ~5GB of the drive overwritten with zero's (thanks to DBAN) and now I'm booted on the Ubuntu LiveCD and trying to learn the command line stuff for formatting a drive. What I want to achieve is use the smallest amount of space possible for the MBR and that's also a point I don't quite understand.
After some research on Google I read that the MBR is on one sector only the very first one, yet the first partition on a hard drive starts anywhere from 63 to 4096. Why are they so far apart? And can I force the partition to be moved closer? I know I know their is pretty much no purpose to this but it bugs me knowing that their might be 31MB (64 512byte sectors minus 1 (MBR) and 64 (beginning of partition)) just going to waste when I could put the NTFS MFT there.
Then the second and last part I want to understand is I want to make the NTFS partition have a 512byte allocation unit size and have it lined with the 512sectors on the hard drive so it can have the max performance. Does anyone know how to do this stuff or could find better info than I have on the internet?

---

### Post by TheOnlyMrK on 2010-11-27
Nevermind about aligning the partition, I got the info on how that is done here: [http://manpages.ubuntu.com/manpages/lucid/man8/parted.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/parted.8.html)

---

### Post by planetofdeviants on 2010-11-27
I wouldn't worry about this space either.  Why not just get things up and going.  The command line stuff can teach you a few things, but gparted can get the job done fast for you.

Boot your live cd.  Open gparted.  Choose create new partition table.  Apply all operations.  Then create a new partions the size you want and format it to NTFS.

---

### Post by TheOnlyMrK on 2010-11-27
> **planetofdeviants said:**
> I wouldn't worry about this space either.  Why not just get things up and going.  The command line stuff can teach you a few things, but gparted can get the job done fast for you.

Boot your live cd.  Open gparted.  Choose create new partition table.  Apply all operations.  Then create a new partions the size you want and format it to NTFS.

I'd rather learn how to do all this. Windows's retarded-ness when it comes to formatting a drive bugs the hell out of me, I'd rather do it the hard and slow but proper way, not to mention I hate GParted.

Plus I'm in no rush, the laptop is what I'm working on while I talk here and look around Google on my desktop. Just annoying that I have to keep putting the laptop in sleep mode because Ubuntu kills the laptop's hard drive, already had it destroy the first one, thank goodness for warranties.

---

### Post by dcstar on 2010-11-27
> **TheOnlyMrK said:**
> 
...........
Then the second and last part I want to understand is I want to make the NTFS partition have a 512byte allocation unit size and have it lined with the 512sectors on the hard drive so it can have the max performance. Does anyone know how to do this stuff or could find better info than I have on the internet?

You are deluding yourself because "512 byte sectors" are just a leftover from the old days and have little relation to what the actual hard drive does internally. **Larger** Allocation Units provide **better** performance, smaller ones waste less drive space. All filesystems are a compromise between these two opposing settings.

Let the provided formatting and partitioning tools do the job they are designed to do because it is almost guaranteed that they will do a better job than people who read a few things on the Internet.

---

### Post by TheOnlyMrK on 2010-11-27
> **dcstar said:**
> You are deluding yourself because "512 byte sectors" are just a leftover from the old days and have little relation to what the actual hard drive does internally. **Larger** Allocation Units provide **better** performance, smaller ones waste less drive space. All filesystems are a compromise between these two opposing settings.

Let the provided formatting and partitioning tools do the job they are designed to do because it is almost guaranteed that they will do a better job than people who read a few things on the Internet.

I prefer to not live by the saying "those who never try, never fail" xP I got my desktop to do important stuff and not be messed with, then my laptop and various old desktops from the 90's to mess with.

EDIT: Also the drive got a speed increase in the Disk Utility from Max Read: 94.6MB/s to 112.6MB/s, Min Read: 42.1MB/s to 44.0MB\s
If you manage to get the filesystem aligned to the sectors that is a big enough speed increase alone to be noticeable. True having a larger cluster size can make the drive even faster but I want to leave it at this trade-off since it will still be faster than before, while wasting less space.

---

### Post by TheOnlyMrK on 2010-11-27
Finally found out how to do it!
```
sudo mkntfs -f -C -I -c 512 -s 512 -p 1 /dev/sda 625137345
```
mkntfs [options] device [number-of-sectors]
-f
Perform quick (fast) format. This will skip both zeroing of the volume and bad sector checking.

-C
Enable compression on the volume.

-I
Disable content indexing on the volume. (This is only meaningful on Windows 2000 and later. Windows NT 4.0 and earlier ignore this as they do not implement content indexing at all.)

-c BYTES
Specify the size of clusters in bytes. Valid cluster size values are powers of two, with at least 256, and at most 65536 bytes per cluster. If omitted, mkntfs uses 4096 bytes as the default cluster size.
Note that the default cluster size is set to be at least equal to the sector size as a cluster cannot be smaller than a sector. Also, note that values greater than 4096 have the side effect that compression is disabled on the volume (due to limitations in the NTFS compression algorithm currently in use by Windows).

-s BYTES
Specify the size of sectors in bytes. Valid sector size values are 256, 512, 1024, 2048 and 4096 bytes per sector. If omitted, mkntfs attempts to determine the sector-size automatically and if that fails a default of 512 bytes per sector is used.

-p SECTOR
Specify the partition start sector. The maximum is 4294967295 (2^32-1). If omitted, mkntfs attempts to determine part-start-sect automatically and if that fails a default of 0 is used. Note that part-start-sect is required for Windows to be able to boot from the created volume.

Now I just need to test and see if Windows will be able to install and boot from the partition with the modified start sector.

---

