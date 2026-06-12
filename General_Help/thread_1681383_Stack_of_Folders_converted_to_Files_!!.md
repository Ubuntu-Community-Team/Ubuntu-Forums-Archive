---
title: "Stack of Folders converted to Files !?!?"
date: 2011-02-04
forum: General Help
---

### Post by Shadz0r on 2011-02-04
Hi

I hope someone can help me cause if not, this is going to be a major headache.

Basically i had a NAS/HTPC setup with Ubuntu 10.10 32Bit. That machine blew up, so i had to replace the hardware.

When i replaced the mobo/cpu/ram with new gear, the system ran just as before (using XBMC as my HTPC frontend and it listed all my media files and played them as before).

Then i started running into issues with the fact that i changed from a Intel Mobo/32bit CPU and Nvidia GFX card to AMD Mobo/CPU and integrated ATI card. So i firgured a reinstall would be the fastest way to fix my woe's

This time around i installed the 64Bit version of Ubuntu 10.10, plus i had previously partitioned my 1Tb HDD with about 40-50Gb's for the ' / ' area of linux, and the rest was partitioned and mounts as ' /home ' (which includes like 600Gb's of TV shows/Movies/Music/Etc).

I reinstalled to the small partition and had the installer load the big partition as /home, just like before.

This all worked fine as all my user directories are still there, and within them all their files.

EXCEPT! in my media folder, there are 2 main folders for movies and tvshows, (within them holding many sub directories and the video files them selves), these folders (atleast the top level which is all i can see) have been convered to "Files", specifically they come up as "Unknown FileType" files with no permissions or anything

i've checked my HDD space, there is only about 200Gb's free, so all the HTPC media has to still be there.

How can i convert these BACK to the files/folders they were before? !!! (its taken me a long time to rip all this content)

And also, can someone explain, how the hell this happened? how is it that the 5 or so user directories in the /home directory are there, and all their subfolders and files are completely untouched as i expected, but this one directory, which happens to be the one containing everything that this PC is basically used for, gets screwed over?

Any help or direction would be great !
Cheers

---

### Post by tredegar on 2011-02-04
> these folders (atleast the top level which is all i can see) have been convered to "Files", specifically they come up as "Unknown FileType" files with no permissions or anything
This can be a sign that the filesystem has become corrupted.

If you care about this data, remember "First, do no harm":

So, do not use the disk: You may corrupt the filesystem further.

Boot from a live CD.
Get another big, empty, disk. Format it as **ext3** or **ext4**

Make a backup of your old **/home** partition to the new disk with **dd**
eg ```
sudo dd  if=/dev/sda2  of=/media/bigdisk/brokenhome-dev-sda2.img
```
You'll need to change **sda2** to whatever is appropriate for you for your **/home** partition.

Unmount the backup disk, and put it somewhere safe.

Now _unmount_ the partition that seems to be broken (if it was ever mounted) and *then* run **fsck** on it. This may take some time.

Does **fsck** report any errors?

Reboot from your HDD. Do things look any better?

---

