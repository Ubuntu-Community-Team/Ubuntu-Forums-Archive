---
title: "Hard drive imaging and cloning"
date: 2011-05-14
forum: General Help
---

### Post by EngDrewman on 2011-05-14
What is the best way to image and clone hard drives in Ubuntu?

I work for a small company that maintains computers for charter schools. Students return their computers to us, we repair and test the hardware, re-image the hard drive, and then issue it to another student. We currently use Norton Ghost on an XP machine to do the re-imaging.

I don't like Norton Ghost because it splits the image into multiple files and has to restart the computer and boot into dos to restore the image. Additionally, I've discovered that if the hard drive has a corrupted partition on it, Windows will freeze as it tries to mount the bad partition, making it such that I have to boot Ubuntu and use Gparted to nuke the bad partition before I can restore the image (which wastes no small amount of time). Since I frequently have to boot Ubuntu for this reason, is there a way to perform this task in Linux and completely ditch Windows and Ghost?

---

### Post by 5149.5 on 2011-05-14
Check[ clonezilla]("http://goo.gl/VqGk") and see if it meets your requirements.

---

### Post by EngDrewman on 2011-05-15
Looks promising... have yet to play with it.

If anyone else knows of any other tools or methods, pls post them!

Thanks!

---

### Post by wilee-nilee on 2011-05-15
> **EngDrewman said:**
> Looks promising... have yet to play with it.

If anyone else knows of any other tools or methods, pls post them!

Thanks!

Honestly if your not wiping the drive anyway your leaving recoverable stuff on the disc from the former user. I would not image that unless I new it was clean, in the circumstances you describe. Maybe Norton has some way of really cleaning and imaging but I doubt it.

There is a non profit in my town that refurbishes used computers for resale they wipe every HD 3 times, before installing a Ubuntu OS.

---

### Post by Bucic on 2011-06-26
I've been looking for a zero-zero backup solution for ubuntu and clonezilla worked perfectly. It was surprisingly easy to use* and lightning-fast! The only drawback of Clonezilla seems to be (for now) the lack of incremental or differential backup methods to choose.

**A serious issue with Clonezilla**:
The actual backup image file when viewed under Ubuntu has 0 bytes file size and file name with incorrect encoding (some weird symbols). A showstopper. Any thoughts? **EDIT:** [http://ubuntuforums.org/showthread.php?p=11198173#post11198173](http://ubuntuforums.org/showthread.php?p=11198173#post11198173)

* given that you preview your partition setup in GParted BEFORE you start with Clonezilla. I've made a screenshot of the partition layout in Ubuntu and I kept the screenshot handy while proceeding with Clonezilla.

---

