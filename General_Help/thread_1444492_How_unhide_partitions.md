---
title: "How unhide partitions"
date: 2010-04-01
forum: General Help
---

### Post by lotfipi on 2010-04-01
hi,

How can unhide my hiden partitions?

these are disk details when i invocate " sudo fdisk -l" command:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x411d411c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6161    49488201    7  HPFS/NTFS
/dev/sda2            6162       10614    35768722+  1c  Hidden W95 FAT32 (LBA)
/dev/sda3           10615       11977    10948266   1c  Hidden W95 FAT32 (LBA)
/dev/sda4           11978       19458    60085620+   f  W95 Ext'd (LBA)
/dev/sda5           11978       16108    33182226    7  HPFS/NTFS
/dev/sda6           16109       17446    10747453+  83  Linux
/dev/sda7           17447       17512      530113+  82  Linux swap / Solaris
/dev/sda8           17513       18486     7823623+   b  W95 FAT32
/dev/sda9           18487       19458     7802077+   b  W95 FAT32

sda2 and sda3 are hiden .

many thnaks
lotfipi

---

### Post by Jive Turkey on 2010-04-01
Hidden, is kind of an ambiguous word in this context.  Are those partitions mounted in /etc/fstab?  /etc/fstab is the file that tells the os which partitions/devices to mount and where to mount them, and with what properties.

You can see which partitions are mounted with the "mount" command.

exactly what the entry for fstab should look like depends on the type of filesystem and what version of linux you are running.  Google around and you are sure to find examples that will work.

You can also mount them temporarily with a command like ```
sudo mount /dev/sda2 ~/<some-empty-folder>
``` the part "~/<some-empty-folder>" should be an actual folder that exists in you home directory.  It could be anywhere you like actually, it is called the "mount point."

This thread should set you straight:
[http://swiss.ubuntuforums.org/showthread.php?p=9042210](http://swiss.ubuntuforums.org/showthread.php?p=9042210)

Note that in Lucid you don't need the UUID in fstab, you cna just use the /dev/sdaN instead.

---

### Post by srs5694 on 2010-04-01
In this context, the "hidden" description applies to certain MBR partition type codes (0x1c in this case). For the most part, Linux ignores partition type codes, so this will have no effect on Linux. Windows, however, does not ignore these type codes. Thus, if the problem is that Windows is not seeing the partitions, unhiding them makes sense; but if there are problems with Linux, a solution such as adjusting /etc/fstab entries makes sense.

To unhide the partitions, use Linux fdisk:


[list=1]
[*]Start a Terminal, Konsole, xterm, or other text-mode shell
[*]Type "sudo fdisk /dev/sda"
[*]Type "p" to verify that you're working on the correct disk.
[*]Type "t"
[*]Type the number of a partition whose type you want to change
[*]Type the new partition type code. To unhide a 0x1c partition, it should be changed to 0x0c. You can omit the "0x" part and just type "0c" or even just "c".
[*]Repeat steps 4-6 for any additional partitions whose codes you want to change.
[*]Type "p" to check that you've made the correct changes.
[*]Type "w" to save your changes.
[/list]


When you reboot, Windows should see the partitions again.

One caveat: It's possible to configure the GRUB or GRUB boot loader to hide and unhide partitions whenever you boot an OS. If GRUB is so configured on your system, it's possible that the partitions will end up hidden again. The solution is to modify the GRUB configuration to either stop it from hiding the partitions or to unhide the partitions when you boot Windows. So if the problem recurs, post back with information on what GRUB version you're using.

---

