---
title: "Creating Windows XP Partition"
date: 2009-12-14
forum: General Help
---

### Post by Uruz on 2009-12-14
Due to WINE's... short comings- I would like to create a partition of Windows XP for gaming. The question is: how?

I know how to create a partition for Ubuntu using a Live CD (Or Live ThumbDrive in my case), but when I put Ubuntu on, I foolishly deleted all of XP. No I see that I need at least as small portion of my Harddrive to be Windows.

Slightly more complicating is the fact that I'm using a Netbook and have no CD drive. I can mount ISOs as CDs and such, but I see how problems could arise anyway.

All the guides I've found related to the subject involve backing up important files and starting over with XP and then adding Ubuntu back to it, but many of my programmes and processes are complicated and I don't really know how I got everything working right.

Can anyone help me create a windows XP partition without wiping my harddrive?

NOTE: I have a 300g external harddrive that I could boot up on a computer with a CD drive, if that helps at all.

---

### Post by raymondh on 2009-12-14
> **Uruz said:**
> Due to WINE's... short comings- I would like to create a partition of Windows XP for gaming. The question is: how?

I know how to create a partition for Ubuntu using a Live CD (Or Live ThumbDrive in my case), but when I put Ubuntu on, I foolishly deleted all of XP. No I see that I need at least as small portion of my Harddrive to be Windows.

Slightly more complicating is the fact that I'm using a Netbook and have no CD drive. I can mount ISOs as CDs and such, but I see how problems could arise anyway.

All the guides I've found related to the subject involve backing up important files and starting over with XP and then adding Ubuntu back to it, but many of my programmes and processes are complicated and I don't really know how I got everything working right.

Can anyone help me create a windows XP partition without wiping my harddrive?

NOTE: I have a 300g external harddrive that I could boot up on a computer with a CD drive, if that helps at all.

Uruz,

1.  Using the liveUSB and in live session, you can access gparted and resize your existing ubuntu to create a space for XP.  You can also use gparted to make the unallocated (freed-up) space as a primary partition ... as needed by windows ... and format it to NTFS.

2.  Do you have an external CD-drive?  If yes, boot into the XP install disk and install windows TO THE APPROPRIATE partition.  If no external CD drive, you need to create a liveusb of windows using the XP iso.  Google search has tutorials on how to make a XP install USB drive.

3.  After installing windows,

a.  Boot into windows and update
b.  you need to re-install GRUB.  How to depends on which version Ubuntu you are using.  Pre-Karmic uses legacy whilst Karmic uses GRUB 2.  Here is a link for pre-Karmic (legacy) which I think you are using as your signature has 9.04.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)


Regards,

---

### Post by Uruz on 2009-12-14
<3 Thanks a lot! I've repartitioned and have a neat 30Gigs for XP. My Brother said he's got a External CD drive that he's hacked together and that I can use that and his XP CD. Thanks again! Everything should work out just fine.

---

### Post by raymondh on 2009-12-14
> **Uruz said:**
> <3 Thanks a lot! I've repartitioned and have a neat 30Gigs for XP. My Brother said he's got a External CD drive that he's hacked together and that I can use that and his XP CD. Thanks again! Everything should work out just fine.

glad to hear.

Remember :

1.  Format that space into NTFS 
2.  Install XP unto that partition
3.  XP will overwrite the MBR.  That's ok for now because once done, boot into XP and update.  Of course, that will take time.
4.  Once you're OK with XP, re-install GRUB.

Happy ubuntu-ing.

---

### Post by Uruz on 2009-12-15
Thanks, one last question though. Re-installing grub won't cause me to lose any data, right?

---

### Post by audiomick on 2009-12-15
> **Uruz said:**
> Thanks, one last question though. Re-installing grub won't cause me to lose any data, right?

No. It doesn't go anywhere near your data. It lives on the front of the drive somewhere, and just tells the computer where to boot from.

---

