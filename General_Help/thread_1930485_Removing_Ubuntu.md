---
title: "Removing Ubuntu"
date: 2012-02-23
forum: General Help
---

### Post by K-Sub on 2012-02-23
Well, after three years, I have decided to remove Ubuntu from my computer and install Windows 7.  There are two reasons for this:

1.  Despite following all the various and sundry instructions in these forums, I cannot reliably establish a Wireless connection.

2.  The new Unity desktop just does not work for me on my Dell Mini, and, quite frankly, I really dislike it.

So, my question is, what steps do I need to follow to totally remove Ubuntu so that I can do a clean install of Windows.

Thanx!

---

### Post by K-Sub on 2012-02-23
Well, after three years, I have decided to remove Ubuntu from my computer and install Windows 7.  There are two reasons for this:

1.  Despite following all the various and sundry instructions in these forums, I cannot reliably establish a Wireless connection.

2.  The new Unity desktop just does not work for me on my Dell Mini, and, quite frankly, I really dislike it.

So, my question is, what steps do I need to follow to totally remove Ubuntu so that I can do a clean install of Windows.

Thanx!

---

### Post by CharlesA on 2012-02-23
Delete partitions. Install Win7. Profit. :)

---

### Post by oldfred on 2012-02-23
Just use gparted from LiveCD to erase all partitions. Unless you have any Windows recovery partitions that you do not want to erase.

Windows will only install to unallocated or NTFS primary partitions with the boot flag. It does not see Linux formated partitions and gets confused if you do not have NTFS or unallocated space.

Grub's boot loader will be in the MBR so the hard drive will not work until you have Windows boot loader installed.

Some of what you have to look forward to:

Contrast - Installing Windows and Ubuntu side-by-side
[http://ubuntuforums.org/showthread.php?t=1930318](http://ubuntuforums.org/showthread.php?t=1930318)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

More for repair:
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)

---

### Post by drawkcab on 2012-02-23
Ya just install Win7 over Ubuntu.

If you have one of those nasty broadcom cards, there is a way to get them to work reliably.  Also Unity is only one of a number of desktop environments that you can use with 'buntu.

---

### Post by forrestcupp on 2012-02-23
Removing Ubuntu and keeping a current installation of Windows is a different story. But if you're doing a clean install, that's a piece of cake.

---

### Post by click4851 on 2012-02-23
yup...."Install Win7. Profit."

---

### Post by K-Sub on 2012-02-23
> **oldfred said:**
> Just use gparted from LiveCD to erase all partitions. Unless you have any Windows recovery partitions that you do not want to erase.

Windows will only install to unallocated or NTFS primary partitions with the boot flag. It does not see Linux formated partitions and gets confused if you do not have NTFS or unallocated space.

Grub's boot loader will be in the MBR so the hard drive will not work until you have Windows boot loader installed.

Some of what you have to look forward to:

Contrast - Installing Windows and Ubuntu side-by-side
[http://ubuntuforums.org/showthread.php?t=1930318](http://ubuntuforums.org/showthread.php?t=1930318)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

More for repair:
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)
OK, I'm not familiar with this.  I just created a bootable USB drive.  Is that the same as a LiveCD.  I don't see gparted on the drive, do I need to boot the computer from the drive to see and use it?  Thanks.

---

### Post by alexfish on 2012-02-23
1. you have not tried.simple solution  by a card that works
2. you have a choice

3. Good Bye

---

### Post by sffvba[e0rt on 2012-02-23
Threads merged.


404

---

### Post by K-Sub on 2012-02-23
> **drawkcab said:**
> Ya just install Win7 over Ubuntu.

If you have one of those nasty broadcom cards, there is a way to get them to work reliably.  Also Unity is only one of a number of desktop environments that you can use with 'buntu.
Well, I have followed every hint I could find on the forums, and that nasty broadcome card will not work reliably.

---

### Post by K-Sub on 2012-02-23
> **forrestcupp said:**
> Removing Ubuntu and keeping a current installation of Windows is a different story. But if you're doing a clean install, that's a piece of cake.
OK, how?  I try gparted and it says I need root priveleges.  I'm clueless...

---

### Post by forrestcupp on 2012-02-23
If you're doing a clean install of Windows 7, you don't even need to use GParted at all. You can do the partitioning from within the Windows 7 installation. [Here is a good tutorial](http://www.sevenforums.com/tutorials/52291-partition-hard-drive-windows-7-install.html) explaining how the installation works with partitioning.

---

### Post by K-Sub on 2012-02-24
> **forrestcupp said:**
> If you're doing a clean install of Windows 7, you don't even need to use GParted at all. You can do the partitioning from within the Windows 7 installation. [Here is a good tutorial](http://www.sevenforums.com/tutorials/52291-partition-hard-drive-windows-7-install.html) explaining how the installation works with partitioning.
Thanx, that is exactly what I needed!

---

### Post by K-Sub on 2012-02-27
> **K-Sub said:**
> Well, after three years, I have decided to remove Ubuntu from my computer and install Windows 7.  There are two reasons for this:

1.  Despite following all the various and sundry instructions in these forums, I cannot reliably establish a Wireless connection.

2.  The new Unity desktop just does not work for me on my Dell Mini, and, quite frankly, I really dislike it.

So, my question is, what steps do I need to follow to totally remove Ubuntu so that I can do a clean install of Windows.

Thanx!
Thanks to everyone who helped me out here.  I now have Win 7 up and running on my netbook, and, I hate to say it here, but it is a much more pleasant experience than when I was running Ubuntu.  Now, when I turn on the computer, things just work the way they should.  Ubuntu is a nice system, but it was just not a good match for this computer.

---

