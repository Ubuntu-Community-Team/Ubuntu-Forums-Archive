---
title: "Copied mp3 files corrupted"
date: 2011-08-18
forum: General Help
---

### Post by wagnebr1 on 2011-08-18
I have all of my music in mp3 form on an external HD.  When I copy it to my home folder for use in Banshee 2.0, some of the music files become corrupted.

When these copied mp3s are played, they have annoying, intermittent distortion throughout some of the songs.  

In an effort to try and isolate the problem, played one of the distorted songs directly from the file on the external HD, and it played flawlessly.  I then downloaded Clementine and had the exact same distortion on the playback from the copied file, and then no distortion from the external HD file.

So at this point, it seems like the mp3 are getting messed up when they are being copied from the external HD to the computer.  I am using a USB 2.0 port for the file copying.

Any thoughts or things to try?

---

### Post by tredegar on 2011-08-18
See if the files are really different, by comparing their **md5sum** 
```
md5sum /path/to/original
md5sum /path/to/copy
```
If the files are identical, the md5sums should be the same.

---

### Post by wagnebr1 on 2011-08-19
I was not able to get md5sum to work.  I kept getting a bunch of errors related to the file path (for both files).

---

### Post by tredegar on 2011-08-21
If you told us what the errors were, we might be able to help you better.

If your path or file names have spaces, or other special characters in them, try putting them in quotes:
md5sum [COLOR="Red"]'[/COLOR]/path/to/original file.mp3[COLOR="Red"]'[/COLOR]

---

### Post by wagnebr1 on 2011-09-03
Hi,

Their md5sum values are different.  

I experimented a bit more and found that if copied one file at a time, then the files don't have the errors and interruptions and their md5sum values are the same.  If I copy the entire library (~25 MB) at once, then the files get the errors (and different md5sum values).

How can I copy the whole library without getting the errors?

---

### Post by tredegar on 2011-09-03
> I was not able to get md5sum to work. I kept getting a bunch of errors related to the file path (for both files).
Looks like you solved this problem (but you did not tell us *how*)....> Their md5sum values are different. 
Ok.
This means that the files are indeed different.

If files are being copied from one device to another, they should be copied correctly, byte-for-byte, and the failure of the md5sum to correlate means that this is not happening.

It would be helpful if you told us what the filesystems (ext2, ext3, ext4, ntfs, fat, fat32 Etc.) you are copying _from_ and _to_ are.

Please confirm that you did remember to unmount or "safely remove" the drive after you had finished the copy operation.

---

### Post by wagnebr1 on 2011-09-05
> **tredegar said:**
> Looks like you solved this problem (but you did not tell us *how*)....
Ok.
This means that the files are indeed different.

If files are being copied from one device to another, they should be copied correctly, byte-for-byte, and the failure of the md5sum to correlate means that this is not happening.

It would be helpful if you told us what the filesystems (ext2, ext3, ext4, ntfs, fat, fat32 Etc.) you are copying _from_ and _to_ are.

Please confirm that you did remember to unmount or "safely remove" the drive after you had finished the copy operation.


So, it appears that the destination hard drive has an ext4 filesystem, and the source (external) hard drive is an ntfs filesystem.  Gparted gave me a warning message with the nfts source partition.

It says:
Unable to find mount point
Unable to read the contents of this file system!
Because of this some operation might not be available.

From Gparted, I have screen shots of the destination hard drive (internal, ext4) and its partitions, the source hard drive and its partitions (external, ntfs), and the information box detailing the error mentioned above for the main partition of the external hard drive.

And to answer your other question on how I got the md5sum to work, the quote marks on the source and destinations (') fixed it.  Thanks for the suggestion.

Also, thank you very much for all of your help.  This is all very frustrating.

---

### Post by wagnebr1 on 2011-09-05
Oh, and to answer your last question, I always unmount the external drive.

---

### Post by tredegar on 2011-09-06
Thanks for the additional information.

I think you should plug the NTFS drive into a windows computer, and have windows check / repair it.

Then try again.

---

### Post by wagnebr1 on 2011-10-10
> **tredegar said:**
> Thanks for the additional information.

I think you should plug the NTFS drive into a windows computer, and have windows check / repair it.

Then try again.

Up front, I apologize for the late  reply, but I want to get this thread wrapped up since it could be helpful to others.

So I booted my computer into Windows7 and tried to repair the external hard drive per your suggestion.  Windows could find no errors with the drive to repair, so nothing was fixed.  I booted back into Ubuntu and gParted still listed an error with the drive.

Moving along, I got another external HD, did the whole mp3 file transfer thing with the new HD, and everything worked fine.  

So now I need to figure out what is wrong with the old drive before I toss it.  It's only a year old and it's 1TB, so I want to try and fix it.  

Thanks for all of your help!

---

