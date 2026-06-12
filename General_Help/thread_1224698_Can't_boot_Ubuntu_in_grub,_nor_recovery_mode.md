---
title: "Can't boot Ubuntu in grub, nor recovery mode"
date: 2009-07-27
forum: General Help
---

### Post by tesseract1 on 2009-07-27
Hi,

I just restarted my computer after making some changes to xorg.conf file and I cannot get back into Ubuntu, the screen freezes.

I tried restarting and trying the recovery mode but then I get a Error 11: Unrecongizes device string.

I don't know what to do.  I can't get into Ubuntu or its recovery to try to restore the changes I made.

---

### Post by pastalavista on 2009-07-27
Boot the computer from the live CD. Navigate to the HDD to /etc/X11/xorg.conf and delete the file. Then rename the backup file (you did create one I hope) to xorg.conf and then try booting again.

---

### Post by tesseract1 on 2009-07-27
I booted from the Ubuntu 9.04 cd, however I don't see an option to navigate to the HDD.  Am I missing something?

---

### Post by tesseract1 on 2009-07-27
Ah I see, I loaded ubuntu from the CD.  I'm in the trial version sort of thing.

It won't let me make changes to the file because I don't have permission.  How do I navigate to this drive in the terminal with permissions?

---

### Post by pastalavista on 2009-07-27
It's easier to just do it in Nautilus. To obtain admin permissions, type Alt-f2 to open a command prompt and enter ```
gksu nautilus
```
Be careful you don't delete or change anything else except xorg.conf

the 'gksu' or 'gksudo' command grants root permissions in graphical applications while 'sudo' elevates the command line to admin (root)

---

### Post by tesseract1 on 2009-07-27
Thank you that worked

---

