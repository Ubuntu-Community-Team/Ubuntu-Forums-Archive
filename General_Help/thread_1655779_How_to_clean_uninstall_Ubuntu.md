---
title: "How to clean uninstall Ubuntu?"
date: 2010-12-30
forum: General Help
---

### Post by deadpool15 on 2010-12-30
hi linux newb here.  I tried uninstalling a distro in the past by deleting the partition with the distro on it. And when I tried to restart my computer it had this error:  Error: no such device: (a bunch of numbers and letters)
Grub rescue>_


at the end I had to reinstall windows all over again. so so sad :-({|=



so now I tried Ubuntu 10.10 and decided again linux is not for me. :( 

So now how can I clean uninstall Ubuntu completely without the grub2 error?


cheers and farewell ubuntu community.):P

---

### Post by karthick87 on 2010-12-30
Is that dualboot??Do you have windows in your system??

---

### Post by deadpool15 on 2010-12-30
yes its dual booted by grub with windows xp professional and ubuntu 10.10 and I dont have the windows recovery disk thing. i do have windows xp pro cd, but i dont know how to go to the recover mode (no prompt to press R or anything), it just go straight to installing windows option.

any other way to remove grub and use the default windows bootloader?

---

### Post by matt_symes on 2010-12-30
Hi

When you uninstall Ubuntu you need to restore your MBR. This is the reason for the GRUB RESCUE> prompt on your previous attempt.

This can be done from the windows recovery console or the Ubuntu LIVECD using Lilo. What version of windows are you using?

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

[http://www.sevenforums.com/general-discussion/17521-how-fix-mbr-through-command-prompt.html](http://www.sevenforums.com/general-discussion/17521-how-fix-mbr-through-command-prompt.html).

or from the liveCD
[FONT=monospace]
[/FONT]```
sudo apt-get install lilo

sudo lilo -M /dev/sdX mbr
```

where X is the drive

Do this before removing Ubuntu.

Kind regards

---

### Post by aldee96 on 2011-01-01
> **matt_symes said:**
> Hi

When you uninstall Ubuntu you need to restore your MBR. This is the reason for the GRUB RESCUE> prompt on your previous attempt.

This can be done from the windows recovery console or the Ubuntu LIVECD using Lilo. What version of windows are you using?

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

[http://www.sevenforums.com/general-discussion/17521-how-fix-mbr-through-command-prompt.html](http://www.sevenforums.com/general-discussion/17521-how-fix-mbr-through-command-prompt.html).

or from the liveCD
[FONT=monospace]
[/FONT]```
sudo apt-get install lilo

sudo lilo -M /dev/sdX mbr
```where X is the drive

Do this before removing Ubuntu.

Kind regards

if the "X" is the drive, it means we have to enter the command for every partition?

---

### Post by karthick87 on 2011-01-01
**X** is harddrive and not partition no.For example **sda **but not **sda1**.

---

