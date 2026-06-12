---
title: "Backup Ubuntu installed with Wubi"
date: 2009-12-09
forum: General Help
---

### Post by kolaperumal on 2009-12-09
hi,
Although this question has been posted in several places i need some clarification about the files to be copied.I installed my ubuntu (using wubi ) in my D: drive so no problem about the loss of data when formatting windows.I need some help regarding the files to be copied from the C: drive where windows is installed.

As of now i know 
**boot.ini** has to be copied
Is there any others files to be copied to restore my ubuntu.

---

### Post by kolaperumal on 2009-12-10
Any Help friends!

---

### Post by kolaperumal on 2009-12-15
Bounce any help friends!

---

### Post by philinux on 2009-12-15
Not sure what your problem is.

Is wubi not booting or broken?

---

### Post by kolaperumal on 2009-12-15
@philinux

Let me explain the problem.I have installed ubuntu using wubi in my windows machine.The windows drive is installed in C: and ubuntu installation is in D: .Recently windows is behaving a bit differently showing a lot of errors and has become very slow so thought of formatting my windows for fresh install of the same.Now the problem is I dont know how to log into ubuntu again as fresh installation of windows will reset the MBR  and will not allow me to log into ubuntu again.

I would like to know the changes or the files which are in C: to be backed up so that i can copy them back after the new installation windows.

---

### Post by philinux on 2009-12-15
First of backup anything imprtant to usb or dvd.

If you reinstall windows you'll loose the wubi install as it installs as a windows program.

The best I can suggest os to follow the wubi guide to put your wubi install onto it own partition.

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

Or backup any important files and do a reinstall of windows and dual boot ubuntu without wubi.

---

