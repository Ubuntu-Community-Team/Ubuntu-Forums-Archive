---
title: "Won't boot after update, No Such Device"
date: 2010-11-10
forum: General Help
---

### Post by nonexistentera on 2010-11-10
Ok I installed Xubuntu 10.04, and it was working somewhat smoothly(little drivers, but I could see and hear). 

Ran the update(as of 3 hours ago), and started up the machine.

Here is what greeted me.

Insyde ACPI BIOS Version 1.50.00 Date: 11/01/02
Copyright (c) 2002 Insyde Software, Inc. All Rights Reserved
Attempting to boot a Hard Drive...
error: no such device: 6a7820b6-708d-4c44-a057-a2aff1467203
grub rescue>

I am not too sure how this happened, or what to do.

The machine is a Kohjinsha SA1F00B AMD Geode LX 512mb and 80gb Hitachi HD.

Thanks,
Tyler

---

### Post by oldfred on 2010-11-10
Is this a wubi install inside the windows NTFS partition or a full install?

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

this will tell us where everything is installed. You can run from Ubuntu liveCD.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

