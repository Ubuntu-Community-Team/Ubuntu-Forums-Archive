---
title: "Delete XP but leave the files ?"
date: 2010-07-15
forum: General Help
---

### Post by MooPi on 2010-07-15
Okay I've got a computer with numerous media files,(video and music). It's a dual boot Windows XP , Ubuntu 10.04 install.I use it as a media box for my large LCD TV. I was wondering if anyone else has deleted the Windows system files and program folders and left the media files. Edit grub deleting Windows XP and leaving the large number of media files alone. I don't want to spend the time to backup and transfer, as it would be to time consuming. I don't want to bork the system just to clean out XP. Any suggestions or similar attempts ?

---

### Post by oOarthurOo on 2010-07-15
So basically, you want to turn your Windows XP partition, which I assume also has all your files, into a NTFS data partition, with Ubuntu as the sole OS. Is that about right?

This doesn't sound too hard. Not really ideal, I mean, with no windows why use an inferior file system like NTFS to serve files? 

In any event, your basic plan is fine. Mount the NTFS partition, using 3G tools delete all the system folders and non-media folders. Then using the ntfs-tools or progs, defragment.

Then run update-grub, but you should probably manually confirm that windows has been removed from the bootloader. This isn't essential, just a cleanliness issue. You'll also want to use something like gparted or cfdisk to remove the bootable flag from the partition.

This is all just in theory. I'm afraid I'm more of a backup restore kinda guy. BUt I can't foresee any problems.

---

### Post by MooPi on 2010-07-15
I know it's a sloppy plan but so many media files to backup and transfer would probably require an entire day of tedious work. Deleting Windows and hour maybe.

---

### Post by elliotn on 2010-07-15
Simply delete the Windows folders, leave only the folders with the media files. i have done that before and just removed the xp entry in grub

---

### Post by oOarthurOo on 2010-07-15
Sure. Well, to be safe you should probably degfragment from within windows first, then delete it. If you're gonna use linux tools to degragment, check for bugs against your current package. I notice in your sig your not on the latest Ubuntu.

---

### Post by MooPi on 2010-07-17
Okay Windows is gone and without much trouble either. Deleted all system files and kept just media files. Updated grub and wallah I was finished. Thanks for the reassurances that my task was easy.

---

