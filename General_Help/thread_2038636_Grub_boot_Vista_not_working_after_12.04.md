---
title: "Grub boot Vista not working after 12.04"
date: 2012-08-07
forum: General Help
---

### Post by iwatts on 2012-08-07
I had Ubuntu 11 running, dual-booting with Vista. I decided to upgrade to 12.04. The upgrade failed and left me with a non-booting Linux, and I decided to just start over and install 12.04 fresh on the partition.

I did that, and when Grub booted, none of the options would work, just kept getting a disk error. So I booted to the Ubuntu DVD and installed and ran boot-repair. This more or less fixed things, but still faced with some issues.

At the boot menu, I have a few options.

- Boot Ubuntu
- Boot Ubuntu with rescue
- Boot previous Linux
- Memtest
- Memtest with Serial
- Windows Vista (loader) on /dev/sda1
- Windows Vista (loader) on /dev/sda2

Before I would still get the two Vista listings, but the first one booted to Windows no problem. Now, the first option just throws me back to the boot screen. The second option presents me a recovery screen with two options, boot OEM Recovery Manager, or boot Windows Vista (recovered). Second option seems to boot fine, but I still think I need to fix this.

Ideally, I'd like to get to a situation, where there is only one option for Vista, for it to work without a prompt, and for it to be the default boot. Any help appreciated.

sda1, should be the actual boot device.
sda2 is the OEM recovery partition.

When I look at the disk utility in Ubuntu, several partitions are now misaligned.

Boot info..

[http://paste.ubuntu.com/1133797/](http://paste.ubuntu.com/1133797/)

This seems to be the problematic part.

menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 9ED0F826D0F805F5
chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" --class windows --class os {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set=root 2C88743C8874071C
chainloader +1

Second one boots (and lets me pick Vista (recovered)), first does not.

Any help appreciated.

---

### Post by decrepit on 2012-08-07
Have you tried just updating grub?

something like, (I'm not 100% sure)
```
sudo grub update
```

---

### Post by krytorii on 2012-08-07
> **decrepit said:**
> Have you tried just updating grub?

something like, (I'm not 100% sure)
```
sudo grub update
```

It's

```
sudo update-grub
```

OP, try a boot repair livecd maybe.
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by oldfred on 2012-08-07
From Boot Repair post the link it creates for BootInfo (Other Options).

Your Windows in sda1 may need repair?


Once you get Windows working, then you may want to hide the recovery, so you do not accidentally boot it.
HOWTO: Grub Customizer Updated for grub 1.99
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html)
The Grub 2 Guide - drs305 also link to grub customizer
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by iwatts on 2012-08-07
> **oldfred said:**
> From Boot Repair post the link it creates for BootInfo (Other Options).

Your Windows in sda1 may need repair?


Bootinfo pasted into url.

[http://paste.ubuntu.com/1134640/](http://paste.ubuntu.com/1134640/)

The windows Vista boot info. Should the Identifiers be different?

C:\>bcdedit /enum all /v

Windows Boot Manager
--------------------
identifier {9dea862c-5cdd-4e70-acc1-f32b344d4795}
device partition=C:
default {78eeebc1-e0ce-11e1-8e44-c035fd19712c}
displayorder {78eeebc1-e0ce-11e1-8e44-c035fd19712c}
timeout 30
resume No

Windows Boot Loader
-------------------
identifier {78eeebc1-e0ce-11e1-8e44-c035fd19712c}
device partition=C:
path \WINDOWS\system32\winload.exe
description Windows Vista (TM) Home Premium
osdevice partition=C:
systemroot \WINDOWS

Windows Memory Tester
---------------------
identifier {b2721d73-1db4-4c62-bf78-c548a880142d}
device partition=C:
path \boot\memtest.exe
description Windows Memory Diagnostic

---

### Post by oldfred on 2012-08-07
I do not know details of BCDs, it looks like their identifiers are not the partition UUIDs. You probably have two, one for your install and the other for the recovery. Or is that only in the recovery partition sda2?

But you have a left over boot.ini from XP and script did not find you main install.

Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

Script did not find this:
/Windows/System32/winload.exe 

Are those folders & files for Windows & System32 in your sda1 and script missed them?

---

### Post by iwatts on 2012-08-07
> **oldfred said:**
> Or is that only in the recovery partition sda2?

But you have a left over boot.ini from XP and script did not find you main install.

Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

Script did not find this:
/Windows/System32/winload.exe 

Are those folders & files for Windows & System32 in your sda1 and script missed them?

Not sure if I understood about the NTDETECT.COM. Don't seem to actually have that file.

I do have the /Windows/System32/winload.exe file though. So any ideas on how I go about fixing it? Thanks.

The recovery partition has it's own boot info, I think.

---

### Post by oldfred on 2012-08-07
How to fix XP  also link to Vista/7 when the boot files are missing & info on windows in logical partitions-  meierfra.
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)

oldfred's Windows Vista/Win7 repair links posts #7:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

---

### Post by iwatts on 2012-08-08
I more or less gave up after trying a ton of things from the links provided to no avail. Restored my drive(s) to an earlier image.

---

### Post by oldfred on 2012-08-08
Always  best to have something to restore from. :)

---

