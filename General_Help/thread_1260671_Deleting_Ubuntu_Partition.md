---
title: "Deleting Ubuntu Partition"
date: 2009-09-07
forum: General Help
---

### Post by Omnicron on 2009-09-07
I am currently trying to install Windows XP on to my computer, but I keep running into an issue with the filesystem that Ubuntu made my hardrive use. Basically, I insert the Windows Xp install disc and boot from it and then I get through loading all the xp drivers and such, but when the message "Starting Up Windows" appears, I get a BSOD. If anyone knows how I can delete my Ubuntu partition off of my hardrive it would be greatly appreciated. Thanks a bunch!

---

### Post by egalvan on 2009-09-07
Seriously doubt that Ubuntu left-overs are the reason for the BSD....

but anyhooo...

Tell the XP installer that you want to use the entire drive.

If, in fact, you have nothing that needs saving, and you want to use the entire drive for XP.

---

### Post by Efwis on 2009-09-07
you need to remove the partitions with a program like gparted. Once this is done your windows install will do it's job.

---

### Post by Omnicron on 2009-09-07
Perhaps I explained my problem unclearly, you see, I can't even make it to the windows partition manager, or whatever it is called, it crashes right before it gets to that part. I am almost 100% sure that the reason for this is that my entire hardrive is partitioned for ubuntu right now, which caused it to change the filesystem on my hardrive to whatever Ubuntu uses, and Windows can only strictly write to NTFS. So, basically I just need to know how to wipe out everything on my hardrive so that I can reformat the filesystem to NTFS.

---

### Post by Omnicron on 2009-09-07
Thanks Efwis I'll check that out.

---

### Post by fluffman86 on 2009-09-07
weird, I didn't have a problem with this, but I only did it once.  The Windows installer just showed that I had a couple of unrecognized partitions.

---

### Post by alejaaandro on 2009-09-07
if you want to keep your ubuntu partition, boot into ubuntu, install gparted and change the size of that partition.. in the place left, create an NTFS partition..

if you don't care about saving your ubuntu share, download patred-magic, a small linux distro very good for maintenance stuff.. burn it on a disk, boot from it and use gpated to format your whole disk to a ntfs partition...

then you can try installing windows again..

---

### Post by Omnicron on 2009-09-07
I resized my dev/sda2 to about 5 gigs smaller, but when I Click on the oartition to the right of my ubuntu part, it wont let me partition it to NTFS, and only ext 2, 3, and 4,  ext, fat16, and 32, reiserfs and linux swap. Any suggestions?

---

### Post by fluffman86 on 2009-09-07
I think a base windows XP install requires about 1.5 gigs of free space.  That's with pretty much no extra apps available.  So yeah, you should be fine, but I have trouble with 10 gigs. :(

---

### Post by alejaaandro on 2009-09-07
strange, i have support for ntfs.. 

after i quick search i got here...

[http://ubuntuforums.org/archive/index.php/t-656443.html](http://ubuntuforums.org/archive/index.php/t-656443.html)

check if you have ntfsprogs installed from synaptic

---

### Post by Omnicron on 2009-09-07
I'll check out ntfsprogs. Thanks for all your help guys!

---

### Post by Omnicron on 2009-09-07
Do you think that formatted my 11 gigs of unallocated space as fat32 and setting it as my primary partition to boot from will allow windows to be installed?

---

### Post by Omnicron on 2009-09-07
Yea! I installed ntfsprogs and it allowed me to format my unallocated space to ntfs! Thanks so much! Now I just have to figure out if it will really let me install xp! Thanks guys!

---

### Post by alejaaandro on 2009-09-07
wish you luck..

just a tip: I THINK (it's been a while since i moved to linux permanently, so don't remember 4 sure) that, in order to install windows, the target partition must be the first on the disk.. so make sure you allocate accordingly your partitions..

'night from me...

---

### Post by Omnicron on 2009-09-07
Darn. Even know I was able to format it to ntfs, it still crashes on startup, I am really lost here. Is there a specific way I can set the ntfs space as the first partition on my hardrive like you advised?

Here is a screenshot of what I have right now [http://www.brickshelf.com/gallery/klbrickmations/BIM/screenshot.png](http://www.brickshelf.com/gallery/klbrickmations/BIM/screenshot.png)

---

### Post by alejaaandro on 2009-09-07
gparted again.. assuming you only have these 2 paritions, delete the ntfs one.. then move your ubuntu one to the end of the disk and create a new ntfs at the beginning of the disk.. 

i really don't know much about installing win, but apart from that, the only possible problem i can think is that the disk has a problem (apart from having win in it :twisted: sorry, just being mean). It might be corrupted so maybe you can google for an md5sum of windows and see if it's ok.. or else you ll have to wait for someone with better experience to help you, sorry..

---

### Post by Omnicron on 2009-09-07
.

---

### Post by c0mput3r_n3rD on 2009-09-07
It has to be the boot cd.  What ever the format of the HDD has nothing to do with the cd booting.  When you boot from the cd, the cd acts as the HDD, and just uses ram, cpu, cd, video card, sound card, system speaker; every thing but the HDD.  That's why windows has a partitioning program in the install cd... so that you can format the disk to NTFS or FAT16 (you're also wrong about windows strictly working on NTFS, it works on fat16 totally fine).  Get a new windows cd and try it again.

---

### Post by Omnicron on 2009-09-07
Sorry about the strictly NTFS thing, but the problem is that Ubuntu is working on a different fielsystem is all. I have tried using a windows cd several times. I think all I need to do now is be able to move my unallocated space before my ubuntu partition.

How do go about moving the partition after I have deleted the ntfs one and am left with 11 gigs of unalloacted space again?

---

### Post by alejaaandro on 2009-09-07
to move your ubuntu partition you'll have to use a live distro, because you can't manage mounted partitions, and you can't unmount this one since it's your root (the one you're working on)

i already mentioned parted magic

---

### Post by Omnicron on 2009-09-07
Oh, that's right, I forgot you mentioned that. Sorry for being such a nuisance.

---

### Post by alejaaandro on 2009-09-07
btw, c0mput3r_n3rD might be right.. i just went over your first post, and since you can't event boot to windows, it is probably a faulty disk.. (at first i thought you just had trouble partitioning the drive)

after trying moving your ntfs to the front (which now i doubt it will work), if you still have no luck you should check your disk, or maybe try getting some help from a windows forum.. they'll probably know better..

---

### Post by egalvan on 2009-09-08
> **Omnicron said:**
> it crashes right before it gets to that part. 
I am almost 100% sure that the reason for this is that my entire hardrive is partitioned for ubuntu right now, which caused it to change the filesystem on my hardrive to whatever Ubuntu uses, and Windows can only strictly write to NTFS.

No, the Install CD DOES NOT TOUCH THE DRIVE until AFTER THE PARTITION OPTION.
So, NOT IT IS NOT THE UBUNTU FORMAT CAUSING THIS PROBLEM.

sorry about yelling, but folks don't seem to be paying attention.

> 
So, basically I just need to know how to wipe out everything on my hardrive so that I can reformat the filesystem to NTFS.

to FULLY WIPE  a hard drive, download Darik's Boot And Nuke

dban.org

burn the iso to a cd, then boot from it.
This will FULLY WIPE  the drive.

Or download PartedMagicd LiveCD, and use it to remove all partitions.

Or use Disk Partitioner on the Ubuntu LiveCD (gparted) to remove all partitions. (you need to unmount all partitions, including the swap)

ErnestG

---

