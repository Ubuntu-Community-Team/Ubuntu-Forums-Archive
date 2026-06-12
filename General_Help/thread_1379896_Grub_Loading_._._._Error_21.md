---
title: "Grub Loading . . . Error 21"
date: 2010-01-13
forum: General Help
---

### Post by Epidemic on 2010-01-13
Hello everyone, I simply wanted to post a potential solution to this issue.  I had this problem directly after I created a bootable Ubuntu USB flash disk.  I would receive this error every time that my USB flash drive was not connected to my computer.

If anyone else encounters this problem in the future, you may feel free to follow these directions and you should be on your way to a trouble-free boot in no time =)

*Anything within '<>' symbols is what you would actually type.  DO NOT include the < or > symbols themselves*

1. Boot your computer with your flash drive plugged in.

2. Select the Hard Drive version of your Ubuntu from the boot menu (not the USB version -- this will usually be the one on the bottom rather than the top of the boot choices. It will also say something like /sda or /hda).

*Pay attention to the end of the boot choice you select.  It will say something like '/dev/sdx#'.  In this scenario, 'x' represents a letter and '#' represents a number.  Take note of what letter is there and ignore the number*

3. Open up a terminal and type <sudo su>    (you will more than likely be prompted for a password, simply type your password in, hit enter and continue)

4. type <grub-install /dev/sdx>    (Replace the 'x' with whatever letter was assigned within your boot choices -- Step 2)

5. Eject your USB disk then remove it from your computer.

*For those of you that do not know how to properly do this, select 'Places' in the top tab and scroll down until you find your USB; next, hit the eject button directly to the right of the USB drive*

6. Shut down your computer and reboot.

7. Your problem should be solved!  Enjoy a worry-free boot, and furthermore, enjoy Ubuntu!


***If you are dual-booting Windows and Ubuntu, do not follow this guide in its present form.  You may encounter a grub error when trying to boot Windows.  I will update this accordingly when I discover how exactly to avoid that potential error!***

---

