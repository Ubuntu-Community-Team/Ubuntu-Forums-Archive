---
title: "fstab file contains strange data"
date: 2012-02-27
forum: General Help
---

### Post by danielbbuchanan on 2012-02-27
I just did another fresh install of Ubuntu 11.10 32bit and immediately my /etc/fstab file contains data I understand should not be there. Here is my file:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=6a5fbd89-6c03-4603-ad79-de3983fff9c5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1a141333-4893-4bd7-98cc-d580edfa17f2 none            swap    sw              0       0
 
This is actually my 3rd install and each time my fstab file starts out like this right out of the gate. Can I get some help with this before I go any further? Is something wrong with my partitioning. This has happened on two different Ubuntu downloads and installs from both CD and USB stick. What do I need to do to fix this?

---

### Post by Paqman on 2012-02-27
Looks alright to me. What bit are you concerned about?

---

### Post by papibe on 2012-02-27
The file does not look wrong. You have 2 partitions: the root partition (home will be living there to), and the swap partition.

What do you mean with strange data? Are you missing partitions, or it shows different partitions from the ones you designed?

Regards.

---

### Post by danielbbuchanan on 2012-02-27
I was told that the file should not contain any of the "swap" info; that everything below the line:

proc            /proc           proc    nodev,noexec,nosuid 0       0

was not suppose to be there and could possibly be the source of many of my problems that I experience as I begin to customize my desktop and start adding programs to my new install. Has somebody given me bad information?

---

### Post by ajgreeny on 2012-02-27
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=6a5fbd89-6c03-4603-ad79-de3983fff9c5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1a141333-4893-4bd7-98cc-d580edfa17f2 none            swap    sw              0       0
```That is totally normal and correct.  Perhaps you are getting confused by the use of UUIDs to denote partitions, and by all the lines starting #.

Any line starting with # is "commented out" and is there for information only.  The lines that start in the pattern "UUID=6a5fbd89-6c03-4603-ad79-de3983fff9c5" etc are the only two lines read by the system when executing fstab.

If your system runs properly then all is OK.

---

### Post by danielbbuchanan on 2012-02-27
For the most part, all of my installs my system has run properly with a few consistent exceptions. With each install I seem to have problems doing a file search while in gedit, while in gedit my system will never show me the contents of the /proc directory and i get multiple GTK Bug errors when in gedit. Now being a new user to Ubuntu, I do not know if this is normal or not.

---

### Post by danielbbuchanan on 2012-02-27
I dont want to take this thread off its stated subject matter; it is good to know that I am starting my install off right. I really appreciate the feedback as I have been concerned that I have been starting off with some corruption that does not show its ugly side till I have spent weeks customizing my OS. Thank you again for your time and assistance.

---

### Post by oldos2er on 2012-02-27
> **danielbbuchanan said:**
>  Has somebody given me bad information?

Short answer, yes.

/proc is a virtual directory that is recreated at each boot. Normally you wouldn't need to edit files in /proc. See [http://it.toolbox.com/blogs/locutus/what-does-this-proc-directory-do-17379](http://it.toolbox.com/blogs/locutus/what-does-this-proc-directory-do-17379)

/proc has little or nothing to do with customizations you make to your home user's graphical desktop environment.

---

