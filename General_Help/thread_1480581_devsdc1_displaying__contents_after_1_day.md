---
title: "/dev/sdc1 displaying / contents after 1 day"
date: 2010-05-11
forum: General Help
---

### Post by Zizuph on 2010-05-11
I was running 9.10-64, upgraded from 9.04 on a 160GB separate boot drive with a 1TB drive for storage.  I had mdadm software RAID on 3 500GB drives.  I copied off the contents of the md0 RAID device, formatted from ext3 to ext4, then copied it all back.  I operated for several weeks this way with enhanced performance and no issues.

note: All drives are on MB SATA-II.

I wiped out everything and reloaded the 160GB drive with 10.04-64.  I removed dmraid and set up mdadm as before with no immediate problems.

The next day, when I pulled up the contents of the 1TB drive (mapped to /1000), it displayed the contents of the root instead.  Curious, I attempted to tunnel down to the /1000 folder from within its own listing of /, and saw no files listed.  I proceeded to delete the files in the /1000 folder, whereupon I found that my system became unstable.  I must have somehow been deleting files from the root itself.

I reloaded again.  To check if the SATA connector to the 1TB drive may be somehow suddenly faulty, I reordered the connectors and set up the boot priority in the BIOS to match the new configuration.  The next morning, I was once again able to see the contents of / when ls'ing /1000.  I carefully checked the entry in fstab, the fdisk -l output, and made sure that the directory wasn't somehow showing as a link.

For the next attempt I decided to take ext4 and mdadm completely out of the equation, hoping it was a bug with some combination of the two under the new kernel or something else which could be corrected by replacing the software RAID with a physical controller at a later date.  Instead of RAID, I simply formatted each of the 500's as ext3 and mapped them to /500-1 through /500-3 respectively.  However, after a day of normal operation, I am now able to see the contents of / when I ls /500-3.  The other 4 drives appear to continue operating normally.

I have been unable to pull up a similar post prior to creating this one.  Perhaps I don't know how to properly search for this issue.  If anyone has seen something similar, please link me to the solution.  I would love to understand what is causing this.  Could my motherboard SATA controller be starting to flake out on me?  I wish I could be sure.  Only one drive seems to be affected by this.

---

### Post by Zizuph on 2010-05-11
Update:  When I create a txt file inside the /500-3 folder, it creates it in the root folder.  Creating a similar file in other folders such as 500-2 works as intended.  When I examine the output of ls -la / and compare the folders, they have identical attributes, but the 500-3 folder indicates the same number of contents as the root...
drwxr-xr-x  27 root root  4096 2010-05-11 19:29 .
drwxr-xr-x  27 root root  4096 2010-05-11 19:29 ..
drwxr-xr-x   3 root root  4096 2010-05-11 19:29 500-2
drwxr-xr-x  27 root root  4096 2010-05-11 19:29 500-3

---

### Post by Zizuph on 2010-05-11
Update: I just compared the output of fdisk -l to my mount points in fstab, and found that three of the five differed from yesterday, including the one for swap, which was set up automatically by the install CD.  How they changed, I would love to understand.  So, I set them back, and after a reboot, everything is once again correct.  Now, to wait another day and see if it happens again.

Has anyone heard of anyone else experiencing seemingly random drive mounting changes without rebooting, just letting the system set over night?

---

