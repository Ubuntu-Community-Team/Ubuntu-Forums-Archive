---
title: "wont shut down 10.04LTS"
date: 2010-05-18
forum: General Help
---

### Post by capo1949 on 2010-05-18
Hi All
I updated to the the new 10.04 this morning and find I cannot shut down or restart my machine using the software power off button, in the corner of the screen.

dell inspiron pentium 4, 3 GB mem
Any help would be appreciated 
Graham

---

### Post by utnubuuser on 2010-05-18
This is a recuring thread...

Google: i915.modeset=0 ubuntu
or i915.modeset=1 ubuntu
or nomodeset ubuntu
and you'll most likely find the solution

in brief:
at the grub menu selection screen (press esc at boot time if you've no grub menu) press e, use arrow keys to scroll to the line that begins with 'kernel', use arrow keys to get to end of line, add "nomodeset" (without quotation marks) after quiet splash, then control+x to boot
if that helps, you can make the change permanent... plenty of how-to's out there...

There is also a forum-sticky regarding known issues with Lucid Lynx, - very helpful

---

### Post by capo1949 on 2010-05-19
Hi
Found that there is a conflict with Open Office quick start. Disabling that and shuts down every time.
See [http://ubuntuforums.org/showthread.php?t=1466589](http://ubuntuforums.org/showthread.php?t=1466589)
Graham

---

