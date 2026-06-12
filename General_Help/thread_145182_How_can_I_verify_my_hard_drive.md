---
title: "How can I verify my hard drive?"
date: 2006-03-15
forum: General Help
---

### Post by tony_st on 2006-03-15
This is a very general question.  If it has already been answered, please post a link because I couldn't find it.

I suspect my hard drive is having mechanical problems, but I'm not really sure.  Which utility / utilities should I use to check it?  Presumably I need to boot the live CD and run this?

I am not so concerned that the filesystem is corrupt.  Sometimes everything works, but sometimes not.  For example, a few times I booted and it hung on the hotplug section.  Then I booted in recovery mode no problem.  Then later I booted normally and gives an error "ata1: translated ATA stat/err 0x59/40 to SCSI SK/ASC/ASCQ 0x3/11/04" followed by "EXT3-fs error (device dm-1): ext3_get_inode_loc: unable to read inode block" "ata1: BUG: timeout without command".  The drive also has a WinXP partition which boots, though every now and put up a message saying there may be something wrong with the hard drive.

thx

---

### Post by o_fortuna on 2006-03-15
[QUOTE=tony_st]This is a very general question.  If it has already been answered, please post a link because I couldn't find it.

I suspect my hard drive is having mechanical problems, but I'm not really sure.  Which utility / utilities should I use to check it?  Presumably I need to boot the live CD and run this?

I am not so concerned that the filesystem is corrupt.  Sometimes everything works, but sometimes not.  For example, a few times I booted and it hung on the hotplug section.  Then I booted in recovery mode no problem.  Then later I booted normally and gives an error "ata1: translated ATA stat/err 0x59/40 to SCSI SK/ASC/ASCQ 0x3/11/04" followed by "EXT3-fs error (device dm-1): ext3_get_inode_loc: unable to read inode block" "ata1: BUG: timeout without command".  The drive also has a WinXP partition which boots, though every now and put up a message saying there may be something wrong with the hard drive.

thx[/QUOTE]
Download the ULTIMATE Boot CD: [http://www.ultimatebootcd.com]("http://www.ultimatebootcd.com") (Download: [http://www.softpedia.com/progDownload/Ultimate-Boot-CD-Download-5992.html]("http://www.softpedia.com/progDownload/Ultimate-Boot-CD-Download-5992.html"))

That CD includes tons of utilities, including manufacturer-specific hardware testing. Just put it in the CD drive and choose the right test.

---

### Post by tony_st on 2006-03-16
Thanks.  Very handy tool and glad to have that in my resources now.

---

