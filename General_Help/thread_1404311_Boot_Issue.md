---
title: "Boot Issue"
date: 2010-02-11
forum: General Help
---

### Post by cottfcfan on 2010-02-11
This is more of a niggle than an issue.
My Dell Inspiron 531 came preinstalled with Vista, to which i added Ubuntu 8.10 some 12 months ago, and everything played nicely.
 Since i installed 9.04 & now 9.10 though I have a 15-20 second hang after the Grub Menu, where the screen just goes black with the cursor flashing in the top left hand corner, the boot then resumes as normal and everything is OK.
 This didn`t happen though on 8.10.
Anyone have any ideas whats causing the hang or a possible cure?

---

### Post by oldfred on 2010-02-11
If you have two drives it can be this:


[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)
Slow boot, multi drives, known issue, move boot to same drive & adjust BIOS
sudo dpkg-reconfigure grub-pc

---

### Post by cottfcfan on 2010-02-11
Thanx for your reply oldfred.
I only have one drive though. This issue occurs after the boot menu screen, and has happened since before grub2.

---

### Post by oldfred on 2010-02-11
Have you checked your log files to see what may be slow or have errors?
system/administration/log file viewer

Look at kern and dmesg

but I do not know how to resolve specific issues. Look for large differences in timestamps and what task may be hanging or slow.

Someone with similar issues but no resolution.
[http://ubuntuforums.org/showthread.php?t=1322923](http://ubuntuforums.org/showthread.php?t=1322923)

---

### Post by cottfcfan on 2010-02-11
When I boot it seems to be hanging at this line:

..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1

I don`t know if this helps anyone?

---

### Post by Arenlor on 2010-02-11
Just a suggestion: Try to disable APIC and see if that helps, first do it through GRUB by pressing e and adding it to the end, if so: [http://ubuntuforums.org/showthread.php?t=148761](http://ubuntuforums.org/showthread.php?t=148761)

---

### Post by cottfcfan on 2010-02-11
acpi=off at the end of the boot line works, but then i lose power options like suspend & hibernate, and the system dosen`t feel right.
But i`m on the right lines.

---

### Post by Arenlor on 2010-02-11
Try the noapic option to see if that helps. Otherwise I have no idea what could be up.

---

