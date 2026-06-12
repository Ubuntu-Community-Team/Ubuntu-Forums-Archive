---
title: "New boot problem"
date: 2010-06-05
forum: General Help
---

### Post by xchecker on 2010-06-05
This just started today.  I upgraded to 10.04 weeks ago and have been running it fine.  Now when I start up my computer it gets to the GRUB loading stage (counts down to 0), then the monitor goes blank for a moment and then several thin scratchy lines about an inch wide in total appear across the top of the monitor and it just freezes there.  The boot process just stops.  I've had these lines appear ever since I upgraded, but they were always momentary and the boot process just continued.  Where do I start in diagnosing and fixing this?

Thanks.

---

### Post by happyhamster on 2010-06-05
First thing you could try is: boot into the grub menu, select the kernel you want to boot, and press 'e'. Now find a line beginning with "linux /boot/vmlinuz........." At the end of that huge line will be the kernelparameters used to boot that kernel, usually "quiet splash". Get rid of "splash" and optionally "quiet" as well. Then boot by pressing ctrl-x. (Note: there should also be a parameter "ro", never remove that one.)

The boot will now happen without loading a graphical splashscreen (and it will give a lot of feedback if you chose to remove the "quiet" parameter as well).

If that doesn't work, you could try adding the parameter "nomodeset" after "quiet splash". For a bit more info, see:
```

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working around bugs in the new kernel video architecture](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working around bugs in the new kernel video architecture)
```

BTW: what type of videocard is your system using? (ATI, Nvidia, Intel...)

Good luck.

---

### Post by xchecker on 2010-06-05
So, a bit more patience on my part may have helped.  I forgot that after so many boots it will run a disk test of some sort; apparently that's what it was doing.  I waited a few minutes this time and it eventually booted up on its own.

The thin scratchy lines must actually be text displayed on the monitor.  I'm not sure why it is so tiny at that point.  I checked the kernel boot instructions as suggested but saw nothing about 'splash' there, nor do I have a splash screen activated through Start-Up Manager.

It's not a huge problem, but any ideas how to get the text at that stage of the boot process to display properly?  If there was an important message I'd sure like to be able to read it.

I have an nVidia GeForce 8400 GS gpu.

---

