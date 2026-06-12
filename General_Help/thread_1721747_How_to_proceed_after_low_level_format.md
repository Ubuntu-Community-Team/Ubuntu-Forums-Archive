---
title: "How to proceed after low level format?"
date: 2011-04-04
forum: General Help
---

### Post by ricaltman on 2011-04-04
I've been trying to install 10.04 on a pc. The hard drive seems  reluctant to let anything be written. I am wiping the drive with Acronis  Drive Cleanser. After the wipe, should I have Acronis format or should I  open the 10.04 iso and have the installer do the formatting? Any  details steps would be appreciated.

---

### Post by lindsay7 on 2011-04-04
I have used Acronis before and I would let it set up and format the drive so that you are sure that you have a viable drive. I would then install Ubuntu and let it set up the formatting for linux. I would use the ext4 format.

---

### Post by wolfen69 on 2011-04-04
> **lindsay7 said:**
> I would then install Ubuntu and let it set up the formatting for linux. I would use the ext4 format.

Ext4 is the default, so no need to worry about that if you choose "use whole drive to install ubuntu".

---

### Post by srs5694 on 2011-04-05
> **ricaltman said:**
> The hard drive seems  reluctant to let anything be written.

That's an extremely vague description. Taken very literally -- that is, that it's the hard disk itself that's refusing commands to write data -- it would mean that the hard disk has failed, probably with bad sectors or perhaps with an electronics failure. Of course, you've provided no hard data about what's actually happening, so this diagnosis is premature. It is a possibility, though.

You could run some SMART tests on the drive to determine if it's physically failing. Something like GSmartControl in Linux can do this, and disk manufacturers usually have SMART utilities on their Web sites that you can run from DOS or Windows.

> After the wipe, should I have Acronis format or should I  open the 10.04 iso and have the installer do the formatting? Any  details steps would be appreciated.

The Ubuntu installer can handle a completely blank disk. Since Acronis is Windows software, it's likely to try to set up FAT or NTFS partitions, which you won't use for installing Linux, so there's no point to trying to use Acronis to set up the disk. (That said, I'm not familiar with Acronis; perhaps it has options to help set up Linux partitions. Even if it does, though, I see no advantage to using it over the Ubuntu installer for creating Linux partitions.)

Incidentally, your message title is incorrect. A low-level format involves redefining the tracks and sectors on a disk. Users can do this type of format on floppy disks (using fdformat in Linux) and on *very* old hard disks (from the 1980s and perhaps slightly into the 1990s), but modern hard disks are low-level formatted at the factory and cannot be low-level formatted by end users.

What you *can* do is to write 0 values to every byte on the hard disk. This operation does not redefine sectors or tracks, so it's not a low-level format; but it does erase all the data on the disk.

---

### Post by glene77is on 2011-04-05
Ricalt,

(1) I would use the Live-CD from Partition Magic, based on the gPartEd program. 
Delete any existing partition.
Define a partition as ext2 or ext3. , and preferably the whole HD, as that makes the choices simpler. .
(You can re-size a partition later, to make room for more partitions if you need). 

(2) boot your Live-CD Ubuntu to Ram, and check to see that you can mount the HD. 
That was your safety check to make certain everything is working. 
Then Install to HD, taking the whole disk, standard default settings. 

(3) If you boot from the Partition Magic Live-CD, then you are running in RAM only, 
and the HD is not being required.  
So then,   you can resize the partitions on the HD, to allow more partitions as required. 

I've done this a dozen times on several computers.
Live-CD are available by internet, $3. each, shipped by mail, from OSDisk.com . 
So, that is my general advice. 
Hope that helps.  
And I hope you ask some more questions.  !      :)

---

### Post by ricaltman on 2011-04-05
> **srs5694 said:**
> That's an extremely vague description. Taken very literally -- that is, that it's the hard disk itself that's refusing commands to write data -- it would mean that the hard disk has failed, probably with bad sectors or perhaps with an electronics failure. Of course, you've provided no hard data about what's actually happening, so this diagnosis is premature. It is a possibility, though.

You could run some SMART tests on the drive to determine if it's physically failing. Something like GSmartControl in Linux can do this, and disk manufacturers usually have SMART utilities on their Web sites that you can run from DOS or Windows.



The Ubuntu installer can handle a completely blank disk. Since Acronis is Windows software, it's likely to try to set up FAT or NTFS partitions, which you won't use for installing Linux, so there's no point to trying to use Acronis to set up the disk. (That said, I'm not familiar with Acronis; perhaps it has options to help set up Linux partitions. Even if it does, though, I see no advantage to using it over the Ubuntu installer for creating Linux partitions.)

Incidentally, your message title is incorrect. A low-level format involves redefining the tracks and sectors on a disk. Users can do this type of format on floppy disks (using fdformat in Linux) and on *very* old hard disks (from the 1980s and perhaps slightly into the 1990s), but modern hard disks are low-level formatted at the factory and cannot be low-level formatted by end users.

What you *can* do is to write 0 values to every byte on the hard disk. This operation does not redefine sectors or tracks, so it's not a low-level format; but it does erase all the data on the disk.Thanks for the input. Acronis 11 is what Western Digital refers me to when looking for disc repair. They no longer provide any WD support for these discs. Acronis has as part of the bootable disc a program called Disc Cleanser which they describe as a low level formatter where it writes zeros. I launched this and after a while it said the format would take 353 days to complete so I aborted. I can view this disc from Windows and Acronis and create partitions, but after formatting to either ext2,3 or 4 or NTFS, writing anything is either not happening or so slow that it appears that nothing is happening. I'm 95% sure the drive was fine until I tried to install Ubuntu on the disc and the install failed for some reason. The disc has been great with no bad sectors until the Ubuntu install. It could be a coincidental failure, but I'm reluctant to believe that.

---

### Post by ricaltman on 2011-04-05
> **glene77is said:**
> Ricalt,

(1) I would use the Live-CD from Partition Magic, based on the gPartEd program. 
Delete any existing partition.
Define a partition as ext2 or ext3. , and preferably the whole HD, as that makes the choices simpler. .
(You can re-size a partition later, to make room for more partitions if you need). 

(2) boot your Live-CD Ubuntu to Ram, and check to see that you can mount the HD. 
That was your safety check to make certain everything is working. 
Then Install to HD, taking the whole disk, standard default settings. 

(3) If you boot from the Partition Magic Live-CD, then you are running in RAM only, 
and the HD is not being required.  
So then,   you can resize the partitions on the HD, to allow more partitions as required. 

I've done this a dozen times on several computers.
Live-CD are available by internet, $3. each, shipped by mail, from OSDisk.com . 
So, that is my general advice. 
Hope that helps.  
And I hope you ask some more questions.  !      :)I've booted Ubuntu repeatedly from a cd and tried Gparted many times and only have the install freeze after seemingly successfully setting up the partitions and formatting. Either the install is going so slowly that after eight hours there seems to be no progress or my hard drive isn't accepting the data.

---

### Post by srs5694 on 2011-04-05
> **ricaltman said:**
> Thanks for the input. Acronis 11 is what Western Digital refers me to when looking for disc repair. They no longer provide any WD support for these discs. Acronis has as part of the bootable disc a program called Disc Cleanser which they describe as a low level formatter where it writes zeros.

Another case of sloppy/incorrect terminology working its way into computer programs....

> I launched this and after a while it said the format would take 353 days to complete so I aborted.

This observation suggests one of three things:


[list]
[*]The Acronis software's time estimate is *way* off.
[*]The software was set to do a multi-pass wipe of the hard disk, with the number of passes set in the hundreds, or maybe over a thousand. A single-pass wipe of a hard disk should normally take a few hours.
[*]The disk has errors that are slowing down the wipe operation, and so the time estimate shows the wipe as taking much longer than it ordinarily would.
[/list]


> I can view this disc from Windows and Acronis and create partitions, but after formatting to either ext2,3 or 4 or NTFS, writing anything is either not happening or so slow that it appears that nothing is happening. I'm 95% sure the drive was fine until I tried to install Ubuntu on the disc and the install failed for some reason. The disc has been great with no bad sectors until the Ubuntu install. It could be a coincidental failure, but I'm reluctant to believe that.

It's possible that the disk had errors all along but that they're concentrated in parts of the disk that you weren't using under Windows, so you saw no effects; but that your Linux installation happened to use problem sectors for some critical data structures, so you saw this performance problem.

It's also possible that there's a bug in the Linux drivers for your motherboard's disk controller. This could cause poor performance under Linux. If so, it's not a disk issue at all, or even a hardware issue.

In any event, I recommend you do two things for further diagnostics:


[list]
[*]Locate and use a SMART utility. GSmartControl is a GUI tool in Linux, and smartctl is a text-mode tool. You could post the output of smartctl here (between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags for legibility) if you need help interpreting the results.
[*]Post the output of "lspci" (again, between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags). This will tell us what your disk controller hardware is. I'm not aware of any specific bugs that would produce the results you describe, but perhaps somebody else is, and will know enough about your hardware to connect the two.
[/list]

---

### Post by ricaltman on 2011-04-05
Hey, thanks for taking the time for a detailed answer. At the moment, I'm trying to put the machine back to it's state just prior to attempting the Ubuntu install. I created a partition and formatted to NTFS which took about three hours, which I didn't think was out of the question time wise. I then started and restore from the backup I made just prior to doing anything. Acronis is predicting 4 days to finish. It does appear that Acronis is writing to the hard drive. It took two minutes to restore a 47 meg file, so at 23 meg per minute which seems very slow to me, it could take four days. I should throw the drive in the trash, but it's become a challenge, man vs. machine.

---

### Post by srs5694 on 2011-04-05
Your human willpower counts for nothing if the drive is bad. Don't take it personally. Instead, run a SMART utility to diagnose the drive. If the drive is bad, get a new one. A bad drive will almost certainly cause data loss.

---

### Post by lindsay7 on 2011-04-05
I have had a bad drive and tried to fix it with Acronis. It will be painfully slow and at the end you will get an error message anyway, with a restore. I new drive will restore in minutes from a back up. I think you are beating a dead horse.

---

### Post by jmore9 on 2011-04-05
When i install any linux distro i usually use gparted live cd 5-2-9.  I downloaded the iso and burned it to a cd.

It allows you to delete , create , resize partitions even if there is a NTFS partition on the same drive.

I will usually just delete the partition that i have windows installed on and create a new one as EXT3 or 4.  I also leave some space on the same partition for the swap file.  Example below

100 gig hard drive

orginal config

30 gig windows system
70 gig data storage NTFS

linux config

29 gig EXT 4
1 gig swap
70 gig data storage NTFS

I usually don't convert the NTFS to a linux file system as linux-es today handle NTFS pretty safely. I always leave the NTFS parts alone as they play nice with in my case ubuntu 10.04.

Gparted live cd is not very hard to work with it is similiar to partition magic for windows.  

Hope this helps .  Sometimes with older hardware you have to select different boot options for it to work properly.

---

### Post by ricaltman on 2011-04-27
> **srs5694 said:**
> Your human willpower counts for nothing if the drive is bad. Don't take it personally. Instead, run a SMART utility to diagnose the drive. If the drive is bad, get a new one. A bad drive will almost certainly cause data loss.I gave up and sent the drive back to WD. All is well with the replacement drive. Ubuntu is great.

---

### Post by ricaltman on 2011-04-27
> **lindsay7 said:**
>  I think you are beating a dead horse.Yes, I gave up.

---

### Post by ricaltman on 2011-04-27
> **ricaltman said:**
> Yes, I gave up.And thanks to all for their help.

---

