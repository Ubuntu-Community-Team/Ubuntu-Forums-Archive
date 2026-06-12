---
title: "install vista"
date: 2010-06-19
forum: General Help
---

### Post by soluckytouselinux on 2010-06-19
Hi everyone. can i install windows vista on a pc that has ubuntu 10.04 on it already. ubuntu takes up the whole disk. do i need to do a partion and then install windows on that? what would be a good program to do the partion, and are there any tricks to doing it. thanx in advance.

---

### Post by elliotn on 2010-06-19
Open gparted and partition the drive giving the new partition a enough space for your vista needs

---

### Post by elliotn on 2010-06-19
Oh i forgot to say after you install vista you wont access your ubuntu, u will have to recover grub as windows would overide

---

### Post by Mark Phelps on 2010-06-20
> **soluckytouselinux said:**
> Hi everyone. can i install windows vista on a pc that has ubuntu 10.04 on it already. ubuntu takes up the whole disk. do i need to do a partion and then install windows on that? what would be a good program to do the partion, and are there any tricks to doing it. thanx in advance.

Don't make a partition with GParted, just make some available space.  Vista is very finicky about its NTFS partitions.  Let it partition the space when you boot from the DVD and do the installation.

---

### Post by TechnoGeek95 on 2010-06-20
After installing Vista, to reinstall Grub, you can use the LiveCD. Check out this article in section 13: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275). If for some reason, Grub doesn't recognize your new Windows installation, you can run "sudo update-grub" and it should search for other boot options.

---

