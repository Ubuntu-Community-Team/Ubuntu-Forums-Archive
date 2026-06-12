---
title: "concatenating raid devices"
date: 2009-11-09
forum: General Help
---

### Post by Cr0n_J0b on 2009-11-09
I have what I think is an easy question.  I'm on 9.10 and have 2 devices:  /dev/sdb and /dev/sdc

These are both devices presented from my RAID controller.  They have 2TB each, but I would like to present them as one single file system.  How can I do this?

---

### Post by realzippy on 2009-11-09
Your raidcontroller seems to be a fakeraid.Hard to set up or nearly impossible (depending on controller).Unset bios controller  raid options,
if you need raid,set up a softwareraid,if not,you can create a LVM over both harddiscs...

---

### Post by Cr0n_J0b on 2009-11-09
It's definitely NOT a fakeraid device.  The controller creates a physical LUN out each drive set and presents them as standard devices.  I'm just trying to figure out how to join these together.

---

### Post by realzippy on 2009-11-09
Hm.Then ubuntu would not see separate discs.Which controller is it?

---

### Post by Cr0n_J0b on 2009-11-09
Sorry, let me explain further.

I have an AAC raid controller with 8 sata ports.  In the RAID setup screen at BIOS i have created 2 RAID volumes with 4 drives each.  Thus, the OS level sees two physical devices.

I know at the BIOS level I could likely restipe my set, but I was just thinking it would be easier to reformat and concatenate.

---

### Post by realzippy on 2009-11-10
Maybe you need to compile the driver to the kernel:

[http://manpages.ubuntu.com/manpages/hardy/man4/aac.4.html](http://manpages.ubuntu.com/manpages/hardy/man4/aac.4.html)

---

