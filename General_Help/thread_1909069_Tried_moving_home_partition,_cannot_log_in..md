---
title: "Tried moving home partition, cannot log in."
date: 2012-01-14
forum: General Help
---

### Post by krytorii on 2012-01-14
I was following the instructions [here]("https://help.ubuntu.com/community/Partitioning/Home/Moving"), and I got to part 4 of Setup Fstab, where it asks you to reset the computer. I restarted my computer, but it came up with an error before the login screen appears (I'm afraid I do not remember quite what it said, something to do with mounting). 

I thought I must have done something wrong in editing the fstab file, so I loaded up a live cd and deleted my new file and replaced it with my backup. I tried restarting my computer again, but now I cannot log in. The login screen is different, with a black background and a blue and white box in the middle. Whenever I log in the screen goes blank then just goes back to the log in screen.

I am using an 11.04 installation, but the liveCD is 10.10.
The contents of my fstab are:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid      0  0  
# / was on /dev/sda5 during installation
UUID=28a851ce-8fc7-4750-afca-5ff2f04e0bae  /            ext3  errors=remount-ro        0  1  
# swap was on /dev/sda6 during installation
UUID=72557e3d-7335-45a1-b111-2a7e7da4476c  none         swap  sw                       0  0  
/dev/sdb1                                  /media/sdb1  ntfs  nls=iso8859-1,umask=000  0  0  
```

---

### Post by grahammechanical on 2012-01-14
Let us work out what has happened. Ubuntu looks for user settings, such as passwords in a folder called home. You have moved the home folder or /home partition (I am not sure which) to another partition on the hard disk.

This means that Ubuntu will not know where to find the user configuration files, so you edited the fstab file to tell it where to look. You got errors so you replaced the fstab file with a backup.

Was this a copy of the fstab file that was made before you moved the /home folder-partition? If so, then Ubuntu does not know where to look to find the /home folder. That information was never in the original fstab file. It only knows to look for a home folder on the same partition that Ubuntu is on.

That error message that you cannot now remember was important. It would have helped you rectify the problem that you first had.

I got into a situation like a few years ago. I did not have enough experience to know about editing the fstab file (I still do not have that knowledge). I solved my problem by re-installing. I could do this because I had created a /home partition that I moved my /home folder to.

But first I made copies of all my data (I had to create another partition to copy it to). And when I re-installed I told the installer to put Ubuntu into the / partition with a mount point of / I then told the partitioner that /home was on the partition I had created for it. I did this by giving this partition the mount point of /home but I did not mark the partition for being formatted. Do not do that or you will loose all your data for sure. To the existing swap partition I gave the mount point of /swap.

This is the brute-force way of fixing it. Others may be able to give you a more delicate method.

Regards.

---

### Post by krytorii on 2012-01-14
Thanks for the advice, I still have all my original files and such. I'm going to try and change the fstab to get the partitions right.

I do remember the error message saying "press s to continue", a  quick google search brought this up, which I think was the message:
"The disk drive for / is not ready yet or not present  Continue to wait; or Press S to skip mounting or M for manual recovery"

EDIT: I have reverted the fstab to the format shown in the guide, and I now get that error again. If anyone has any advice what to do from that stage, I would be grateful as well.

---

