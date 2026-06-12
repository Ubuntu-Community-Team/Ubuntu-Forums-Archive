---
title: "uninstalling  ubuntu"
date: 2010-05-27
forum: General Help
---

### Post by saakeman on 2010-05-27
How to uninstall   ubuntu 

please help !

---

### Post by Guitar John on 2010-05-27
Is it the only OS on your computer, or did you set up as a dual boot, with another Operating System?

---

### Post by saakeman on 2010-05-27
> **Guitar John said:**
> Is it the only OS on your computer, or did you set up as a dual boot, with another Operating System?

dual boot , runing windows 7 and ubuntu 9.10

---

### Post by saakeman on 2010-05-27
uninstalling ubuntu 
help!

---

### Post by ownaginatious on 2010-05-27
You're going to have to give more information than that if you want any help.

Did you install Ubuntu in Windows(Wubi)? If so, it should be as simple as uninstalling it as if it were a program on your windows side.

---

### Post by Guitar John on 2010-05-27
I found this [HowTo]("http://computersight.com/operating-systems/ubuntu/ubuntu-how-to-remove-ubuntu-windows-vista/") for Vista.  Should work the same for Windows7.

Ignore the advertisment at the top of the page requesting that you "Run a Free Scan for Errors."

---

### Post by dustinmarlowe56 on 2010-05-27
boot to the liveCD, open the partition editor, select the ubuntu partition, right click, delete, apply, done.

---

### Post by goinglinux on 2010-05-27
> **dustinmarlowe56 said:**
> boot to the liveCD, open the partition editor, select the ubuntu partition, right click, delete, apply, done.

This works *if* you don't have Ubuntu installed in a dual-boot configuration with Windows. If you are dual booting and your installation is using GRUB as the boot manager, then using dustinmarlowe56's suggestion will cause you to need to use the Windows recovery console to fix the MBR (master boot record) so you can boot Windows again.

See this thread: [http://ubuntuforums.org/showthread.php?t=271459&highlight=remove+ubuntu]("http://ubuntuforums.org/showthread.php?t=271459&highlight=remove+ubuntu")

---

### Post by dustinmarlowe56 on 2010-05-27
> **goinglinux said:**
> This works *if* you don't have Ubuntu installed in a dual-boot configuration with Windows. If you are dual booting and your installation is using GRUB as the boot manager, then using dustinmarlowe56's suggestion will cause you to need to use the Windows recovery console to fix the MBR (master boot record) so you can boot Windows again.

See this thread: [http://ubuntuforums.org/showthread.php?t=271459&highlight=remove+ubuntu]("http://ubuntuforums.org/showthread.php?t=271459&highlight=remove+ubuntu")


ah, thank you for the correction. I have not had to remove linux from a system and worry about keeping the dual boot windows system running at the same time.

---

### Post by lisati on 2010-05-29
Threads merged. Please do not start multiple threads on the same question.

---

