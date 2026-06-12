---
title: "Add more Space? Help!"
date: 2011-01-18
forum: General Help
---

### Post by NissanSkylineN1 on 2011-01-18
Hey guys,
I have just installed Xubuntu and suprisingly it did not ask me to create a partition within its installer like Ubuntu does. So now, I am left with 150mb of free space. I want to expand that amount. The problem is, I do not know where it has been installed on. I have a C and an E drive. Currently, the C drive is mounted and the E drive will not mount even if i press the mount button. Does anyone have a solution?

---

### Post by sum1nil on 2011-01-18
Are you saying that you have only 150 mb of free space on the partion or there is 150 mb unallocated?

Try installing gparted and while being careful see what is available.

Can you mount the E drive manually? Would be something like:
Create a file called Edrive in your home directory.
"sudo mount -t ext3 /dev/sda2 ./Edrive'

If you can mount it manually but not in the gui desktop, it may not be in your fstab
file.

Good luck.

---

### Post by NissanSkylineN1 on 2011-01-18
No, there is a good 5.5 gb that i want to use left on the drive where Ubuntu is installed. The E drive is full and I don't need it because it cant be mounted anyways. All I want to do is steal 5gb from Windows and donate it to Ubuntu.

---

### Post by NissanSkylineN1 on 2011-01-19
Hey,
I have finally got the drive mounted, just needed patience. For the C drive, what I am proposing is to remove the redundant XFCE packages (sine I am running LXDE) and use the E drive (I've cleared up room) for my documents. But I need two things to know:
1: How to I get rid of XFCE (other than deleting packages one by one
2: Is there a macro I can make to mount that drive every time i log on?

---

### Post by sum1nil on 2011-01-19
XFCE: [http://ubuntuforums.org/showthread.php?t=1354248](http://ubuntuforums.org/showthread.php?t=1354248)  had some interesting info but no mention of how he deleted it all (probably in the package manager he higlighted it and choose complete removal). This posting has warnings too.

As far as mounting the drive everytime I would use fstab and add a line:
'/dev/sda2     /               ext4    auto, errors=remount-ro    0       1'
if ext3 worked on a manual mount I would use that.
If it is not root(/) you want to mount exchange that for something like '/home' etc

Be careful when fiddling with fstab not to change any other line(s).

---

### Post by NissanSkylineN1 on 2011-01-19
Hey,
Thanks for your help first of all.
Ok, so here we go again:
1: Is there a command line to remove XFCE? 
2: As for the E drive, I'll manually do it. All I need to do is press enter anyways.

---

### Post by NissanSkylineN1 on 2011-01-19
Hey guys,
I need to add more space to Xubuntu as it only has 380 mb of space left. The problem is, I don't know if it partitioned the C drive. How do I expand it?

---

### Post by NissanSkylineN1 on 2011-01-19
Double post

---

### Post by NissanSkylineN1 on 2011-01-19
Hey guys,
Nevermind, I NEED space, and expand the space that Ubuntu has. The problem is, Xubuntu didn't create a partition. So I don't know how to expand its space.

---

### Post by NissanSkylineN1 on 2011-01-19
Sorry, DOUBLE POST. Mods, Delete

---

### Post by NissanSkylineN1 on 2011-01-19
Hey guys,
I need to add more space to Xubuntu as it only has 380 mb of space left. The problem is, I don't know if it partitioned the C drive. How do I expand it?

---

### Post by NissanSkylineN1 on 2011-01-19
Hey guys,
I need to add more space to Xubuntu as it only has 380 mb of space left. The problem is, I don't know if it partitioned the C drive. How do I expand it?

---

### Post by NissanSkylineN1 on 2011-01-19
Hey guys,
I need to add more space to Xubuntu as it only has 380 mb of space left. The problem is, I don't know if it partitioned the C drive. How do I expand it?

---

