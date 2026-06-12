---
title: "How to backup dual boot files"
date: 2009-11-27
forum: General Help
---

### Post by hardyfan on 2009-11-27
I have just upgraded my Windoz partition from XP to Win 7, I lost my dual boot functionality (couldn't access my Ubuntu partition).  I have since re installed and restored all my files (a lot of work).

What files on my primary (Windows) partition do I need to backup to restore this functionality ?  Or is there an easy way to just install or restore the dual boot option ?

Thank you in advance.

---

### Post by carl.davis on 2009-11-27
You need to look into restoring the MBR. I think you can boot into a rescue environment and use grub to re-install your MBR, however I don't know if Windows 7 will be happy with that. There is a way you can create a floppy disk with a backup boot record if you still have a floppy drive on your computer.

---

### Post by hardyfan on 2009-11-27
I don't have a floppy, I was hopeful that there was just a few files that could be copied to CD that could then be written back in this situation.

---

### Post by mechro on 2009-11-27
When you had the dual boot did you have a boot menu screen like this?..

[IMG]http://i3.photobucket.com/albums/y71/Cocasoca/grub.jpg[/IMG]

If you did then that is Ubuntu's Grub boot system and Windows will have overwritten Grub's configuration in the MBR. You can restore your Grub boot but the method depends on which version you are running. If you have Ubuntu 9.10 then it's probably Grub2. If it's older version Ubuntu then it's plain old Grub.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by hardyfan on 2009-11-27
Thank you, that is exactly what I was looking for.  I will bookmark all that info for future reference. I'm enjoying the learning curve.

Noel

---

