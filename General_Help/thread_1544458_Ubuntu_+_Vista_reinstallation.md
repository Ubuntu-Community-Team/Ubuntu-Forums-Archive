---
title: "Ubuntu + Vista reinstallation"
date: 2010-08-02
forum: General Help
---

### Post by pg1192 on 2010-08-02
Allrighty, so I'm fixing my friend's computer for him, and it's just been one problem after another.  The computer dual boots vista and ubuntu 10.04. Both operating systems are installed at this point.  However, the vista reinstallation made the main hard drive partition the active one, as expected. That means that grub isn't loaded.  I'm having some issues with the partitioning.  His hard drive is having problems, so I had to do a really funky install on vista's recovery partition. Now, I'm not sure which partition to set active with gparted. I've tried / and /ext4, as well as the whole ubuntu partition, and each time I try to boot, it didn't work. At least, when I tried /, it didn't give a boot error; it was just the blinking cursor hanging.  How do I figure out which partition needs to be active? Is there anything else I need to do to get grub working again?

Thanks!

---

### Post by pg1192 on 2010-08-02
I ran grub-install as instructed on [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows).  That made the disk boot, but it didn't go to the normal grub menu, but a grub terminal prompt.  Not what I was hoping for.

---

### Post by MasterGamerJK on 2010-08-02
Problem: It has the Vista
Solution: Remove the Vista, and add Windows 7 for or maby a second Ubuntu partition :D

---

### Post by pg1192 on 2010-08-02
I suggested that to him, but he likes vista.  I have NO idea why, but I'm sticking with it.

---

### Post by Mark Phelps on 2010-08-02
> **pg1192 said:**
> ...His hard drive is having problems...

Perhaps the problems have NOTHING to do with Vista or Ubuntu, but simply due to the hard drive failing??

Post the results of "sudo fdisk -lu" (that's a lowercase L, not a one), so we can at least see the current partition setup you're using.

---

### Post by oldtraveler on 2010-08-02
You might take a look at my post # 17 in this thread for a possible solution - or at least a work around.
[http://ubuntuforums.org/showthread.php?t=1543969&page=2](http://ubuntuforums.org/showthread.php?t=1543969&page=2)

---

### Post by TheNerdAL on 2010-08-02
> **Mark Phelps said:**
> Perhaps the problems have NOTHING to do with Vista or Ubuntu, but simply due to the hard drive failing??

Post the results of "sudo fdisk -lu" (that's a lowercase L, not a one), so we can at least see the current partition setup you're using.

Or you can test your hard drive using Disk Utility.

---

### Post by oldfred on 2010-08-02
The boot flag (active partition) should be on the NTFS partition and only the windows boot partition. Grub does not use a boot flag to boot.

To see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

