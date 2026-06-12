---
title: "how to unlock internal hard drives"
date: 2012-03-03
forum: General Help
---

### Post by vapblack on 2012-03-03
Recently, both my extra internal hard drives have become locked. I'm unable to delete files from, and add files to the drive. It is just greyed out. How can I unlock the drive so I can use them.

When I go on my XP partition, I am able to access everything.

---

### Post by winh8r on 2012-03-03
Someone may be able to help if you are a bit more specific with regard to the following:

What release of Ubuntu are you running.
Your hardware specifications.
What is installed on the disks you are trying to access,and what are they formatted as (ext4, ntfs, ?)
Has this problem just started? Were you able to access them before?
How are you trying to access them?
Have you recently changed any of the configurations on your system or experienced any strange behaviour when using these hard disks?

---

### Post by vapblack on 2012-03-03
Thanks for the response.

I'm using ubuntu 11.10
its a 1tb internal drive that worked up until recently, I don't think I made any big changes, that would affect that...on the 1tb is just videos and pictures, its used as a  backup. On the other is just a partition of my main drive and it holds windows xp
I was able to access them. Just for some time, it's been locked. I don't know how long it's been, I noticed it and just ignored it for a while, expecting that it would be easy to fix if I just did a little research. I was of course sadly mistaken :(

I just mount the drive and try to delete or add, and I am not able to. The delete is greyed out, and if I try to add something it says "the destination is read-only"

---

### Post by winh8r on 2012-03-03
Can you open a terminal (press control + alt + T ) and enter this command:

```
sudo gedit /etc/fstab
```

It will open the file in a text editor, just copy and paste the entire file into your next post.Use the # (code tags) function when pasting the output into your next post to keep it tidy.

---

### Post by vapblack on 2012-03-03
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=9816a77a-eab8-495a-8b82-3173c2099dcd none            swap    sw              0       0
```

---

### Post by vapblack on 2012-03-06
any ideas...Im thinking about just reinstalling the OS...:-|

---

### Post by vapblack on 2012-03-17
Ok so I formatted the HD and reinstalled Ubuntu and for the first week or so it was fine, and now it's locked again. I didn't do anything but install different software from the software center.
this is getting annoying :/

---

### Post by oldfred on 2012-03-17
Normally you need to permanently mount them if fixed drives with your permissions & ownership.

But if you are having issues, are these NTFS partitions and are you hibernating in Windows? Or have you recently run chkdsk on the NTFS partitions. Windows does not seem to run chkdsk automatically. Ubuntu runs fsck on its partition every 40 or 60 reboots.

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

