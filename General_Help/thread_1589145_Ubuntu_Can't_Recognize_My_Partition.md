---
title: "Ubuntu Can't Recognize My Partition"
date: 2010-10-06
forum: General Help
---

### Post by Zalebi on 2010-10-06
(If this is in the wrong place, would a Moderator please move it?)

Hi! Thank you for taking the time to look at my post. I have installed Ubuntu on my netbook, an early Eee PC, and the battery ran out of charge. I didn't know that however and turned on my netbook. It started booting up traditionally, but then it just spit out a whole bunch of code:

 > Killed
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

I learned that this is a slightly common problem and that I should boot from a Live USB and run some code in terminal. But when I try and boot into a Live USB it just stays at the Ubuntu loading screen and when I hit escape it tell me:

> (process:303): GLiB-WARNING **: getpwuid_r(): failed due to unknown id (0)
Killed
stdin: error 0
unable to open '/dev/sda'

Here is where I get stuck, I haven't found anything on how to fix this. So, that is why I am here, is there anyway for me to be able to use this computer again without changing the Hard Drive, I don't really care about keeping the data I had on it already. Please HELP!

---

### Post by SeijiSensei on 2010-10-06
Did the battery die during installation?  If so, you need to reinstall again.

---

### Post by Zalebi on 2010-10-06
No, I had working Ubuntu for over a three months. But then the battery died. I didn't know this so I turned it on, and it immediately shut off. Then I charged it and it gave me the code once turned on again.

---

### Post by Zalebi on 2010-10-08
Bump.

Any ideas?

---

