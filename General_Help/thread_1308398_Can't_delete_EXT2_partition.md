---
title: "Can't delete EXT2 partition"
date: 2009-10-31
forum: General Help
---

### Post by modmidget on 2009-10-31
I had to install a new disk drive in my PC a week ago because the old drive died.  The new drive is a 160 gig drive.  First I installed Win XP with S/P 3 and everything was fine.  Then I installed Ubuntu 8.04 and the troubles began.  Ubuntu resized the Windows partition down to 8.81 gig and used the other 137.44 gig for Ubuntu.  When I booted into Windows I started getting nasty little messages about "not enough disk space".  SOOoooo....... I booted using the Ubuntu install CD and ran "sudo gparted" in a terminal window.  I tried to resize the ext2 partition but got an unknown error.  Then I ran fixmbr in Windows to get rid of grub.  Then I tried running gparted again to delete the ext2 partition.  Got an error that said "can't delete the partition because it's mounted".  So I tried to unmount the partition but got a message that the command "unmount" could not be found.  After that I installed Partition Magic in Windows and tried that.  It sees the ext2 partition but says it's unsupported when I try to delete or resize it.  I ran fdisk but it doesn't see the Linux partitions either, so I can't delete them in that program.  I finally tried to format the disk but now I have a 9 gig drive with nothing on it.

How do I get those Linux partitions off the drive so I will have a 160 gig drive that I can start over with?  I've spent 6 days this week reinstalling XP and all of my programs, and now everything is gone because Ubuntu decided to be a disk hog.  I plan to reinstall XP and Ubuntu but will need some help with Ubuntu so it doesn't take over the whole disk.

---

