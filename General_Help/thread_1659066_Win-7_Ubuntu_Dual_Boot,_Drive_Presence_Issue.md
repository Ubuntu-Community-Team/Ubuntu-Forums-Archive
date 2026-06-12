---
title: "Win-7 Ubuntu Dual Boot, Drive Presence Issue"
date: 2011-01-03
forum: General Help
---

### Post by HomerD on 2011-01-03
[FONT=Times New Roman][SIZE=3]Win-7 Ubuntu Dual Boot, Drive Presence Issue[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I recently built up a new computer and set it up for dual-boot with Win7 and Ubuntu. Initially I had some issues with the boot management but I discovered that GRUB works well and Paragon’s Partition Manager does not. I reloaded Ubuntu using GRUB and got the system working exactly as I would like it to. [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Several weeks later I volunteered to assist my brother-in-law’s family with getting their Unbutu system working properly with a new Brother MFC295CN printer. I brought the printer home so that I could work with it on my system. I did get the printer to work correctly (thank you Ubuntu forums!) but in the process I had to reload Ubuntu because I made a few mistakes on my way to success. [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]When I reloaded Ubuntu, I accidentally loaded it onto my system’s second drive, drive F. Before, I had Ubuntu in a partition on drive C. Ubuntu works from the F drive and GRUB allows me to boot either Win 7 or Ubuntu, as desired. I will note that the earlier version of Ubuntu on drive C has been removed although the partition is still there. GRUB shows entries for this second copy of Ubuntu along with Win 7 and the entry for the functioning Ubuntu OS. [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Here’s where I’m getting into trouble. Initially, everything looked fine. Win 7 worked, Ubuntu worked. Then, after a reboot to Win7, I noticed that my F drive was missing. I searched all around the system controls, tried loading new hardware, etc, etc, but the drive did not show up anywhere. Rebooting into Ubuntu showed that the drive was in fact still there and all the date in the large data partition was still there. Using Ubuntu’s partition manager I discovered that the data partition was not enabled. I enabled the partition and rebooted back into Win7. No go. The F drive was not present. [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]My next step was to try Paragon’s Partition Manager software, which I have a paid-for copy of. It would not see the F drive either. Using the Paragon recovery disk I had made earlier with the Paragon software, I restarted the system. The recovery software saw both drives correctly and the partitions were set up correctly. I ran the boot corrector software but I did not mess around too much as earlier experience had indicated that some of the Paragon features do not work well with Ubuntu. [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I shut down and rebooted into Win7. Success! The F drive was there. But later, when I restarted the system the F drive was gone again. I tried a few things then rebooted using the recovery disk again. As before, on the next restart the F drive was present. I didn’t take the time to reboot the system twenty times, but it seems apparent that something in the boot records is preventing Win7 from seeing the F drive correctly unless I boot from the Paragon recovery disk and then boot Win7. [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]No knowing a lot about what goes into a boot record and how either GRUB or boot.ini manage things, I’m at a loss as to why I’m seeing this inconsistency with the F drive. A probable solution would be to remove both the second (old Ubuntu) partition on the C drive and the Ubuntu partion on the F drive and reload Unbutu all over. This would put me back to where I was in the beginning. However, this seems a bit inelegant as all the other attributes of the system are working well, is there a better way to address the problem?[/SIZE][/FONT]

---

### Post by Verbeck on 2011-01-03
is this a wubi installation?

right click my computer>manage>disk management/utility and see if it is listed
if so, try to assign a letter to it from there

---

### Post by HomerD on 2011-01-05
Not sure. How would I know?

---

### Post by Mark Phelps on 2011-01-06
> **HomerD said:**
> Not sure. How would I know?

One way is, when you are in Ubuntu, open a terminal and enter "sudo fdisk -lu" (that's a lowercase L, not a one). That will list out the partitions on the drives.

If you see only FAT/NTFS partitions, then it was a Wubi install -- which creates a large file inside an MS Windows partition but treats it as if it were a Linux partition.

---

