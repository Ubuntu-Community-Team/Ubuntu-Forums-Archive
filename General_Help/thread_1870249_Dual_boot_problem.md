---
title: "Dual boot problem"
date: 2011-10-26
forum: General Help
---

### Post by Aviator_14 on 2011-10-26
I have an older compaq presario desktop that came with windows ME preinstalled. Anyway I put a second hard drive in the machine and installed ubuntu 10.4 on it. Anyway when I turn on the PC a list of options come up asking me to boot from ubuntu or windows 9x. If I select windows 9x an error comes up saying "invalid system disk, replace the disk, and then press any key." Before I installed ubuntu this did not occur and I was able to run Windows ME without any problems. It seems as if though Ubuntu wiped out the windows Me boot-loader even though the two different OS's are on separate hard drives. I tried reinstalling ME but then I lost the opportunity to boot into Ubuntu (the OS choices menu wasn't there anymore) and it just automatically booted into ME. Now I had to install ubuntu again and am stuck with the same issue where it will not boot into ME if I select it on the menu. Does Anyone know how I can dual boot ubuntu and windows ME? I do not really want to upgrade the machine to a newer windows because there are some old DOS programs that I have that will not run in windows XP and I want to be able to use the Windows ME computer so I can run those programs.

---

### Post by RaganN on 2011-10-26
I've never tried to dual boot ME and Ubuntu, but I know it's very different getting it to work than it is with XP, Vista, or 7.  When you install Ubuntu, there is an option to decide where to install grub.  If you don't set this, it will by default be installed on the first hard drive.  This overwrites the Windows loader.  If you install it on the second hard drive, you will not get the menu, however, unless you change the boot device.  

As for the DOS programs not working in Windows XP, have you tried using DOSbox?  I've found it very effective in running old DOS programs, especially considering that ME doesn't have the best DOS support.  With DOSbox you can run DOS programs on Windows XP or Ubuntu and it will run like it's actual DOS.

---

### Post by oldtimer7777 on 2011-10-26
Windows ME is relatively small. You can install it in Virtualbox and you won't have this problem. 

To install Virtuabox on Ubuntu 10.04:

[http://www.webupd8.org/2010/05/virtualbox-ubuntu-1004-lucid-lynx.html](http://www.webupd8.org/2010/05/virtualbox-ubuntu-1004-lucid-lynx.html)

Then create a new virtual disc in Virtualbox and install Windows ME the way as you would normally on your HP, but this time install it into Virtualbox.  That should fix this.

> **Aviator_14 said:**
> I have an older compaq presario desktop that came with windows ME preinstalled. Anyway I put a second hard drive in the machine and installed ubuntu 10.4 on it. Anyway when I turn on the PC a list of options come up asking me to boot from ubuntu or windows 9x. If I select windows 9x an error comes up saying "invalid system disk, replace the disk, and then press any key." Before I installed ubuntu this did not occur and I was able to run Windows ME without any problems. It seems as if though Ubuntu wiped out the windows Me boot-loader even though the two different OS's are on separate hard drives. I tried reinstalling ME but then I lost the opportunity to boot into Ubuntu (the OS choices menu wasn't there anymore) and it just automatically booted into ME. Now I had to install ubuntu again and am stuck with the same issue where it will not boot into ME if I select it on the menu. Does Anyone know how I can dual boot ubuntu and windows ME? I do not really want to upgrade the machine to a newer windows because there are some old DOS programs that I have that will not run in windows XP and I want to be able to use the Windows ME computer so I can run those programs.

---

### Post by wolfen69 on 2011-10-26
Unplugging the windows drive before installing ubuntu would have prevented any problems.

---

### Post by oldtimer7777 on 2011-10-26
> **wolfen69 said:**
> Unplugging the windows drive before installing ubuntu would have prevented any problems.

Taking the Windows Hard Drive apart and removing the platters to save for use as Wind Chimes would have prevented this from happening

---

### Post by oldfred on 2011-10-26
Old IDE drives can only boot from the primary master. You have to set jumpers on the Hard drive to set master & slave. Or you use the somewhat newer cable select and set jumpers to cable select and the location on the cable determines primary master. If using cable select make sure the cable is the newer 80 conductor, not a old 40 conductor or the same as comes with most CDs.

Windows boot has not changed. It only looks for boot flag (active partition in windows) and jumps to that partition boot sector to boot. Not sure about the older FAT partitions on how they were configured.

with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

---

