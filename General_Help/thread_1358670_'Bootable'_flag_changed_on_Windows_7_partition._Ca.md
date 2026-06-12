---
title: "'Bootable' flag changed on Windows 7 partition. Can't be mounted now."
date: 2009-12-18
forum: General Help
---

### Post by Shne on 2009-12-18
Okay, making a new thread because old thread's title didn't match the problem anymore. Old thread detailing more (mostly last post): [http://ubuntuforums.org/showthread.php?p=8522265](http://ubuntuforums.org/showthread.php?p=8522265)

My problem, in short, is that I changed the bootable flag (and back again) of my windows 7 partition and now it can't be mounted or even recognized by the windows bootloader, ubuntu, gparted or disk utility.

I really don't want to reinstall windows 7 and GRUB2 to make it work because that means lots of lost saved games and lots of time spent on setting things up. Although I know it might be my last option.

---

### Post by oldfred on 2009-12-18
Windows uses the boot flag to know what partition to boot, but if you have more than one windows it then combines the boot of the second windows into the one with the boot flag. The second windows will not boot on its own (but can be repaired). 

Vista copies boot manager to one 
[http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing](http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing)
Moral of the story - look on other NTFS partitions for the missing bootmgr and Boot directory.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by Shne on 2009-12-18
I appreciate the reply, but I don't think you've really read what my problem is.

The problem is that I can't reach my Windows 7 partition by any means I know and I don't know how to correct this.
The problem started when I changed the boot flag in an attempt to see if I could boot it on it's own. I got an error message which I was too dumb not to save in any way.

I googled what I could remember from the error message and it's something like this I found: > Error modifying partition: helper exited with exit code 1: In part_change_partition: device_file=/dev/sda, start=190555094016, new_start=190555094016, new_size=8463780864, type=0x83
Entering MS-DOS parser (offset=0, size=200049647616)
MSDOS_MAGIC found
looking at part 0 (offset 32256, size 7649478144, type 0x0b)
new part entry
looking at part 1 (offset 7649510400, size 174894128640, type 0x07)
new part entry
looking at part 2 (offset 182543639040, size 8003197440, type 0x05)
Entering MS-DOS extended parser (offset=182543639040, size=8003197440)
readfrom = 182543639040
No MSDOS_MAGIC found
Exiting MS-DOS extended parser
looking at part 3 (offset 190546836480, size 9500198400, type 0x05)
Entering MS-DOS extended parser (offset=190546836480, size=9500198400)
readfrom = 190546836480
MSDOS_MAGIC found
readfrom = 190555061760
MSDOS_MAGIC found
readfrom = 199018874880
MSDOS_MAGIC found
Exiting MS-DOS extended parser
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 1
got it Note that this is **not** my exact error message, none of the numbers or amount of messages are applicable to my situation.
I remember there was at least two more "got xxx" messages in my error, and after that it said something like "ugh. offset or size changed"

---

### Post by oldfred on 2009-12-18
If you have or had XP or any other windows installed, your windows7 does not have a boot partition, all the boot info is in the other boot partition that had the boot flag. You can repair the win7 install with the windows install CD and then reinstall grub to get Ubuntu to boot again.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista Recovery Disc 
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

This works for Vista since it is just copying backup data in the windows partition. I do not know if it works for Win7

meierfra.
[http://ubuntuforums.org/showthread.php?t=1350824](http://ubuntuforums.org/showthread.php?t=1350824)   post 10 on repair of Vista
I agree. But I recommend to use testdisk to fix your boot sector. (Vista's "fixboot" usually only repairs the boot code in the boot sector, but not the boot parameters)

---

### Post by Shne on 2009-12-19
I tried tesdisk.

There was no Backup BS option, and it said that both Boot Sector and Back Boot Sector status was bad.
So I tried the Rebuild BS option instead. It used a long time to 'Search MFT' but at the end nothing happened. It just went back to the screen it was at before. and the Windows 7 partition remains unmountable and unrecognized.

Any other ideas? Or closer analysis of what the problem is? My own guess is that both the Boot Sector and MFT is screwed. Could a Windows 7 install dvd repair it then?

---

### Post by oldfred on 2009-12-19
Most of the suggestions say fixboot and fixmbr but there is a rebuild command also:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

