---
title: "Will resizing XP's partition or reinstalling XP affect it's GRUB entry?"
date: 2006-02-22
forum: General Help
---

### Post by nrwilk on 2006-02-22
Before I get started here, I'd like to apologize.  Because I know I've seen this spoken of in other threads.  Even so, I've searched for a while on this subject, and I could not find any mentions now.  I also didn't see any dedicated threads.  I figure even if it is mentioned elsewhere, this way if someone searches they'll be able to find it more easily.

I'd like to create more room for Linux, and several new partitions for testing Dapper and other distros which I am curious about ( just to let you know, I'm curious about Mepis, Debian, SuSE, gentoo and Slackware.  Mostly because I want to expand my knowledge of Linux in general, and I gather that each distro has a different feel.  I probably won't be replacing ubuntu. ).  In order to do this, I need to free up some room which is being hogged by Windows XP.  I never Use XP, so I only need to give it around 30GB.  That frees up around 90GB for me to use for Linux testing.

If I use a utility under XP to resize it, will it mess with it's entry in GRUB's boot list?  Is there a specific way to do it in order to ensure GRUB will continue to recognize the partition?  If I reinstall XP, will it be lost to GRUB?

What's my best bet for getting this done with the least amount of trouble?

Any and all info on these different scenarios is well appreciated.

Thank you! :grin:

---

### Post by RAOF on 2006-02-22
GRUB's XP entry should remain valid - you'll be removing space from the end of the partition, so it's partition number shouldn't change.

If you reinstall XP it will overwrite GRUB because Microsoft knows that no one ever wants to dual-boot Windows.  If you reinstall XP you'll need to re-install GRUB to the MBR.

Your best bet would be, I reckon, to use whatever partitioner comes with the distro's installer.  I've used Ubuntu's to resize my NTFS XP partition & that worked just fine.  Then just install distros to your heart's content.  The only problem I can see is that you'll need to make sure that all the relevant boot lines get put into your GRUB's menu.lst.

---

### Post by nrwilk on 2006-02-22
[QUOTE=RAOF]Your best bet would be, I reckon, to use whatever partitioner comes with the distro's installer.  I've used Ubuntu's to resize my NTFS XP partition & that worked just fine.[/QUOTE]

I was wondering about this as well.  I figured, though, that since Linux cannot write to NTFS with stability yet, it probably couldn't do this.  It's good that it can.  That makes it easier, for now I don't need to search for a Windows utility to do it.

---

### Post by nrwilk on 2006-02-22
If I add new partitions to the end of /dev/hda1 (where Windows is installed), won't that rename /dev/hda2 ( / ), /dev/hda4 ( /home ), etc... Therefore, they won't be in the same places when I startup, and their entries in fstab will be pointing to the wrong places. Or, am I just trying to create problems now? When partitions are created, are they named in the order that they go on the disk, or in the order of their creation? If the latter is true, then I'll be fine, right?

---

### Post by RAOF on 2006-02-22
[QUOTE=nrwilk]If I add new partitions to the end of /dev/hda1 (where Windows is installed), won't that rename /dev/hda2 ( / ), /dev/hda4 ( /home ), etc... Therefore, they won't be in the same places when I startup, and their entries in fstab will be pointing to the wrong places. Or, am I just trying to create problems now? When partitions are created, are they named in the order that they go on the disk, or in the order of their creation? If the latter is true, then I'll be fine, right?[/QUOTE]
Mmm, I'm not sure.  That's a good point.  You may need to edit your /boot/grub/menu.lst if it doesn't boot properly.

You'll still be able to boot if it doesn't work, just manually edit the bootline (press 'e' on the boot option to do that) and change the harddrive it's trying to boot from :)

---

### Post by nrwilk on 2006-02-23
I'll try it tomorrow morning, and let you know if it works. ;)

---

### Post by nrwilk on 2006-02-24
Well, my friend gave me a really nice disk which you can boot from, and it has hundreds of utilities to fix boot managers, partition drives and do partition rescues, and a whole LOT more stuff.  It has utilities for Linux and Windows.  Anyway, NONE of the partition tools on that disk could resize my NTFS partition.

But, the Breezy install disk could!

I'm sure that disk (called "The Techie Toolkit") is still a nice tool to have around.


Anyway, I had to backup my /home partition and reinstall because I never knew that one could only have 4 primary partitions on a disk.  I didn't know the difference between primary and logical before, so I always chose primary.  I never had any problems, but after resizing Windows' partition It called the free space "unallocated" instead of "free space."  Then it told me that I couldn't have more than 4 primary partitions.  But, I researched it, and each primary partition can have infinite logical partitions.  So, I had to reinstall with a single Linux primary partition and the rest logical.

What's the difference, anyway?

---

### Post by RAOF on 2006-02-25
I believe that the difference is that you can only have 4 primary partitions :)

You might not be able to boot from an extended partition, I'm not sure.

---

### Post by cotcot on 2006-02-25
Do not forget to defragment your XP partition before youy shrink it.
The other partitions will be renumbered when you put a new distro before your actual /hda2. There is a nice case study about this in the GNU parted manual : [http://www.gnu.org/software/parted/manual/html_chapter/parted_2.html#SEC31](http://www.gnu.org/software/parted/manual/html_chapter/parted_2.html#SEC31)
Fstab is to be revised too. Good luck.

---

### Post by nrwilk on 2006-02-25
[QUOTE=cotcot]Do not forget to defragment your XP partition before youy shrink it.[/QUOTE]
Yup, I've never defragmented a drive in my life, but I did remember to do it before resizing.

[QUOTE=cotcot]The other partitions will be renumbered when you put a new distro before your actual /hda2.  Fstab is to be revised too.[/QUOTE]
That's what I thought would happen.  I had to reinstall Breezy anyway, because the reason for making more space was to be able to test Dapper and other distros.  I had already used up my four primary partitions, though.  I had to reinstall, making some partitions logical.  So, this wasn't a problem this time.

[QUOTE=cotcot]Good luck.[/QUOTE]
thanks! :D 


[QUOTE=RAOF]You might not be able to boot from an extended partition, I'm not sure.[/QUOTE]
Yes, you can.  I was worried about that too.  That's what I thought the difference was at first.  But, you can.

---

### Post by dcstar on 2006-02-25
[QUOTE=nrwilk]I was wondering about this as well.  I figured, though, that since Linux cannot write to NTFS with stability yet, it probably couldn't do this.  It's good that it can.  That makes it easier, for now I don't need to search for a Windows utility to do it.[/QUOTE]
Working with a disk's Partition Table and then the file system while it is off-line is not the same as mounting a disk and using it as a "normal" resource, so by all reports the Linux resizing tools seem to perform fine in this regard.

If you downsize a NTFS partition, AFAIK all that happens is any files that need to be relocated to the remaining space are moved, and then the Directory structure and sector boundaries are adjusted to reflect the new settings (Defragmenting may remove the need for the move step).

Upsizing should be even simpler (and less risky), as no files need to be moved, the filesystem just needs to be given the new sector boundaries and any root directory restructuring performed.

---

