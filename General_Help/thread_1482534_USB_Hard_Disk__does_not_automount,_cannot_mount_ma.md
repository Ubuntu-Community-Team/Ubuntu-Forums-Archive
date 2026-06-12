---
title: "USB Hard Disk : does not automount, cannot mount manually, is detected incorrectly"
date: 2010-05-13
forum: General Help
---

### Post by theimpossible on 2010-05-13
Hello Everybody,
I am a noob and I will be grateful for eternity if someone helped me access my "Seagate FreeAgent Go" 500 GiB external hard disk. It has 160 GiB of invaluable personal data with no backup elsewhere.

==============================

<BEGIN>

PART I : DOES NOT AUTOMOUNT

I think no elaboration is needed here. :-)

----------

PART II : CANNOT MOUNT MANUALLY

Here are the details of my effort at manual mount and the results:

My external hard disk is listed as 'sda' in Disk Utility in my Ubuntu 10.04 'Lucid'.

sudo mkdir /mnt/usbhdd
sudo mount -t vfat /dev/sda /mnt/usbhdd
**mount: /dev/sda: can't read superblock**

----------

I don't know what's the purpose of 'fdisk', but ubuntu users with automount problem were asked to do this, so I did it too and I think it is indicating a (serious?) problem with sdb1 and sdb2:

sudo fdisk -l

Disk /dev/sdb: 8024 MB, 8024752128 bytes
247 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 15314 * 512 = 7840768 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         973     7447552   83  Linux
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 32, 33) logical=(0, 33, 3)
Partition 1 has different physical/logical endings:
     phys=(927, 77, 46) logical=(972, 192, 40)
Partition 1 does not end on cylinder boundary.
/dev/sdb2             973        1024      386049    5  Extended
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(927, 110, 14) logical=(972, 225, 41)
Partition 2 has different physical/logical endings:
     phys=(975, 125, 46) logical=(1023, 81, 52)
Partition 2 does not end on cylinder boundary.
/dev/sdb5             973        1024      386048   82  Linux swap / Solaris

----------

Again, I don't know anything about 'fstab' and 'mtab', but here are the contents. Is 'mtab' indicating an error with sdb1 :

FSTAB

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=bb85c867-4f3c-4a3f-8f3d-04e091c99b79 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=65b743ba-4fc4-4b5c-8490-ff59fd5074de none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

MTAB

**/dev/sdb1 / ext4 rw,errors=remount-ro 0 0**
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/impossible/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=impossible 0 0

----------

PART III : DETECTED INCORRECTLY

Disk Utility is listing my 'Seagate FreeAgent Go' 500 GiB External Hard Disk, but strangely it is reporting a size of 2.2 TeraBytes!

Also, my " /media " directory is listing a "floppy" and a "floppy0", even though I have no Floppy Drives. This might be totally irrelevant, but I think one or neither of these used to be there when my USB Hard Disk would automount and be listed in that directory.

----------

HISTORY & A FUN FACT:

My Seagate 320 GiB Internal Hard Disk Crashed a month ago. I bought this Seagate FreeAgent Go 500 Gib External Hard Disk, installed Ubuntu 10.04 'Lucid' on it and started using it via USB Boot. No Internal Hard Disk, that is to say. It worked fine for a few days, but then my system mysteriously got hung up on three occasions - unusual for Linux. In order to get things working again, I pulled of the USB HDD and/or switched off the power supply without taking out USB HDD. I had to do that because the reboot button won't work. I'm afraid that that could've caused some damage to the USB HDD, but I'm hoping that they are more robust than that. But in any case, the USB HDD stopped getting automounted after the third occasion.

Now that I have no Internal HDD nor External HDD, I'm using 'Kingston Data Traveler G2' 8 GiB PenDrive with Ubuntu 10.04 'Lucid'! :-)

<END>

==============================

Now, if you have read all of this far I am already grateful to you and would readily be your slave if you could help me salvage my 160 GiB data.

Cheers,
The Impossible.

---

### Post by blazemore on 2010-05-13
If you're in Firefox, [click here]("apt:gparted") to install gParted.
Once the installation has completed, run it from System->Administration
Select your external drive from the drop-down menu in the top-right corner.

If it says you need to "initialise" don't let it, and quit gparted.

Can you see your partitions? If so, try right-clicking them all and selecting "unmount", then right-clicking the one(s) with the data on and click "mount". What happens then?

---

### Post by -humanaut- on 2010-05-13
You can try pmount sudo apt-get pmount I didn't see any entry for it in the Fstab maybe I overlooked it? What filesystem is it formatted with?

---

### Post by blazemore on 2010-05-13
> **-humanaut- said:**
> You can try pmount sudo apt-get pmount I didn't see any entry for it in the Fstab maybe I overlooked it? What filesystem is it formatted with?

If you can't access the disk, and there is important data, I would attempt to mount the partitions first using standard utilities, as this is unlikely to cause any problems (no offense humanaut, I'm sure pmount is an excellent utility. Just try this first)

---

### Post by theimpossible on 2010-05-14
blazemore and -humanaut-, thanks reading all the way through and for your replies.

----------

@ **blazemore**:

Installed gParted. (Thanks for the ready link.)
It is not showing my external hard disk.

As for partitions, it has none. (Disk Utility confirms it.)
Again, a bit of history: when my internal hard disk was about to crash, I took a backup on a friend's laptop. Then bought the external, copied back my data on it and started using it using Ubuntu Live CD. When I realized the performance was too slow, I tried to install Ubuntu on it, but for unknown reasons I couldn't. So I got it done with the help of the same friend. The IMPORTANT point in all of this is that **neither him nor me ever partitioned or even formatted it**. I think it was company formatted (it had Seagate installer etc. on it) though I don't know with what filesystem.

@ **-humanaut-**
Installed pmount, here are the results:

pmount
Printing mounted removable devices:
/dev/disk/by-uuid/bb85c867-4f3c-4a3f-8f3d-04e091c99b79 on / type ext4 (rw,relatime,errors=remount-ro,barrier=1,data=ordered)

This was the corresponding entry in FSTAB:
UUID=bb85c867-4f3c-4a3f-8f3d-04e091c99b79 / ext4 errors=remount-ro 0 1

As for formatting, I neither formatted nor partitioned it.
And noob that I am, I don't know and can't even figure out what filesystem it is formatted with.

----------

What to do now? :(

---

### Post by sedawk on 2010-05-14
Boot from your USB stick (or LiveCD).

When the system is ready open a terminal and type
"sudo dmesg -c" to view and clear the message buffer.

Now connect your external disk.
Wait ( 20 seconds).
run "dmesg" to view the message buffer (only containing
new messages).

The system should tell you that it detected the drive
and it will tell you the device it uses
(sda, or sdb, or sdc, or ...)
and it will show you the partitions if found
(e.g. sdd1,sdd2,sdd3,...).
Are there any warnings or error messages?

Next, if everything worked, you can check the partition table
with "sudo fdisk -l /dev/sdd" or similar.
Then you can try to mount the correct partition like
you already tried (but "/dev/sda" is wrong - that is
the whole disk! You want to mount a partition like
"/dev/sdd1" or "/dev/sdd2")

---

### Post by theimpossible on 2010-05-14
Hey Sedawk, thanks a lot for taking an interest in my problem.

I did the "dmesg" thing and sure there are endless error messages; there are so many of them that my terminal won't show the beginning. But they are all the same except for changing sector numbers. Here's a sample:

[  363.398487] sd 4:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  363.398493] sd 4:0:0:0: [sda] Sense Key : Aborted Command [current] 
[  363.398500] sd 4:0:0:0: [sda] Add. Sense: No additional sense information
[  363.398507] sd 4:0:0:0: [sda] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  363.398523] end_request: I/O error, dev sda, sector 0
[  363.405238] sd 4:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  363.405244] sd 4:0:0:0: [sda] Sense Key : Aborted Command [current] 
[  363.405251] sd 4:0:0:0: [sda] Add. Sense: No additional sense information
[  363.405258] sd 4:0:0:0: [sda] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[  363.405274] end_request: I/O error, dev sda, sector 8
[  363.412114] sd 4:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  363.412120] sd 4:0:0:0: [sda] Sense Key : Aborted Command [current] 
[  363.412127] sd 4:0:0:0: [sda] Add. Sense: No additional sense information
[  363.412134] sd 4:0:0:0: [sda] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[  363.412149] end_request: I/O error, dev sda, sector 128
[  363.418861] sd 4:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  363.418868] sd 4:0:0:0: [sda] Sense Key : Aborted Command [current] 
[  363.418874] sd 4:0:0:0: [sda] Add. Sense: No additional sense information
[  363.418881] sd 4:0:0:0: [sda] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  363.418897] end_request: I/O error, dev sda, sector 0
[  363.425739] sd 4:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  363.425745] sd 4:0:0:0: [sda] Sense Key : Aborted Command [current] 
[  363.425751] sd 4:0:0:0: [sda] Add. Sense: No additional sense information
[  363.425758] sd 4:0:0:0: [sda] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  363.425774] end_request: I/O error, dev sda, sector 0
[  363.432615] sd 4:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  363.432621] sd 4:0:0:0: [sda] Sense Key : Aborted Command [current] 
[  363.432628] sd 4:0:0:0: [sda] Add. Sense: No additional sense information
[  363.432635] sd 4:0:0:0: [sda] CDB: Read(10): 28 00 00 00 10 00 00 00 08 00
[  363.432651] end_request: I/O error, dev sda, sector 4096

----------

Now, I don't have the slightest clue what to understand from this, so will you please guide me further?

Thanks,
The Impossible

P.S. The external HD turned itself on exactly after 20 seconds! How did you know that? Standard Electronics stuff? Or lots of geek experience?

---

### Post by blazemore on 2010-05-14
[http://www.webupd8.org/2010/05/fix-usb-devices-automount-not-working.html](http://www.webupd8.org/2010/05/fix-usb-devices-automount-not-working.html)

---

### Post by cmcanulty on 2010-05-14
I have exact same drive and it is terrible for Linux. I even sent it back to factory and no difference. It has a power saving feature that causes it to constantly spin down even in the midst of a backup and unmount and then since it wasn't safely removed it won't remount without a giant pain. I have a western digital that does the same thing. On my netbook it stays mounted and even though they both run Lucid it has some difference I can never figure out. Gparted does help it to mount but even when I put an entry in fstab it didn't help.I try to use grsync for backups of my 70+GB of files but it takes forever due to the constant unmounts. I have never figured out how to correctly put an entry in fstab for devices that you don't want to boot but be able to use once a week or so and maybe that would help.
[http://www.mail-archive.com/linux-usb-devel@lists.sourceforge.net/msg52952.html](http://www.mail-archive.com/linux-usb-devel@lists.sourceforge.net/msg52952.html)
[http://www.nslu2-linux.org/wiki/FAQ/DealWithAutoSpinDownOnSeagateFreeAgent](http://www.nslu2-linux.org/wiki/FAQ/DealWithAutoSpinDownOnSeagateFreeAgent)
Unfortunately I am not skilled enough to understand exactly how to do the fix. If anyone can give us a fix for this that works and doesn't need reconfiguring each time the drive is mounted I would love it. This mounting business is the most irritating thing about Linux to me. Even my USB flash drives unmount if not accessed for several minutes. But for energy and sound issues I don't want to leave a ext HD attached all week for an hour or 2 of use a week.Let me know if you find a fix.And new with Lucid my USB mouse constantly disappears about once a day and only a restart fixes it though others have had luck with Ctrl+Alt+F2 or Fn+F7, also see
[http://www.mattcutts.com/blog/format-external-drive-for-linux/](http://www.mattcutts.com/blog/format-external-drive-for-linux/)
[http://www.linuxjournal.com/node/1005886](http://www.linuxjournal.com/node/1005886)

---

### Post by sedawk on 2010-05-17
That output from dmesg looks bad.

If the disk drive itself is not broken you can
try to use a different USB port, e.g. some
towers have bad connectors on the front but
the connectors on the back work fine (because
of cheap internal cables connecting the front connectors).

Or try a different cable to connect your drive
(make sure it is a USB 2.0 cable).

You can also try a different computer e.g. with an
Ubuntu LiveCD. The output you posted is not okay!

I have only seen stuff like that once here and that was
because of bad cabling!

---

### Post by cmcanulty on 2010-05-17
Drive and cables work fine on other systems. My USB ports work fine for other things.

---

### Post by cmcanulty on 2010-05-19
Here is my dmesg output. Can you please comment on it and if bad tell me how to repair.This is without any ext drives attached, thanks
```

[    0.089323] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.089329] pci 0000:00:13.2: PME# disabled
[    0.089384] pci 0000:00:14.0: reg 10 io port: [0x8400-0x840f]
[    0.089393] pci 0000:00:14.0: reg 14 32bit mmio: [0xc0503000-0xc05033ff]
[    0.089429] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.089494] pci 0000:00:14.1: reg 10 io port: [0x1f0-0x1f7]
[    0.089503] pci 0000:00:14.1: reg 14 io port: [0x3f4-0x3f7]
[    0.089511] pci 0000:00:14.1: reg 18 io port: [0x170-0x177]
[    0.089520] pci 0000:00:14.1: reg 1c io port: [0x374-0x377]
[    0.089529] pci 0000:00:14.1: reg 20 io port: [0x8410-0x841f]
[    0.089720] pci 0000:00:14.5: reg 10 32bit mmio: [0xc0503400-0xc05034ff]
[    0.089823] pci 0000:00:14.6: reg 10 32bit mmio: [0xc0503800-0xc05038ff]
[    0.089987] pci 0000:01:00.0: reg 10 32bit mmio pref: [0xc8000000-0xcfffffff]
[    0.089993] pci 0000:01:00.0: reg 14 io port: [0x9000-0x90ff]
[    0.089999] pci 0000:01:00.0: reg 18 32bit mmio: [0xc0000000-0xc000ffff]
[    0.090014] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.090031] pci 0000:01:00.0: supports D1 D2
[    0.090091] pci 0000:00:02.0: bridge io port: [0x9000-0x9fff]
[    0.090094] pci 0000:00:02.0: bridge 32bit mmio: [0xc0000000-0xc00fffff]
[    0.090098] pci 0000:00:02.0: bridge 32bit mmio pref: [0xc8000000-0xcfffffff]
[    0.090153] pci 0000:02:00.0: reg 10 64bit mmio: [0xc0100000-0xc0103fff]
[    0.090162] pci 0000:02:00.0: reg 18 io port: [0xa000-0xa0ff]
[    0.090222] pci 0000:02:00.0: supports D1 D2
[    0.090224] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.090229] pci 0000:02:00.0: PME# disabled
[    0.090291] pci 0000:00:06.0: bridge io port: [0xa000-0xafff]
[    0.090294] pci 0000:00:06.0: bridge 32bit mmio: [0xc0100000-0xc01fffff]
[    0.090361] pci 0000:03:05.0: reg 10 32bit mmio: [0xc0202000-0xc0202fff]
[    0.090393] pci 0000:03:05.0: supports D1 D2
[    0.090395] pci 0000:03:05.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.090401] pci 0000:03:05.0: PME# disabled
[    0.090440] pci 0000:03:07.0: reg 10 32bit mmio: [0xc0200000-0xc0201fff]
[    0.090558] pci 0000:03:0e.0: reg 10 32bit mmio: [0xc0203000-0xc02037ff]
[    0.090569] pci 0000:03:0e.0: reg 14 io port: [0xb000-0xb07f]
[    0.090641] pci 0000:03:0e.0: supports D2
[    0.090643] pci 0000:03:0e.0: PME# supported from D2 D3hot D3cold
[    0.090649] pci 0000:03:0e.0: PME# disabled
[    0.090693] pci 0000:00:14.4: transparent bridge
[    0.090702] pci 0000:00:14.4: bridge io port: [0xb000-0xbfff]
[    0.090707] pci 0000:00:14.4: bridge 32bit mmio: [0xc0200000-0xc02fffff]
[    0.090749] pci_bus 0000:00: on NUMA node 0
[    0.090752] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.090820] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB2_._PRT]
[    0.090877] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[    0.090947] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.093450] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    0.093538] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    0.093625] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    0.093711] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    0.093798] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.093885] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    0.093971] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.094058] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    0.094142] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.094146] vgaarb: loaded
[    0.094239] SCSI subsystem initialized
[    0.094276] libata version 3.00 loaded.
[    0.094332] usbcore: registered new interface driver usbfs
[    0.094342] usbcore: registered new interface driver hub
[    0.094363] usbcore: registered new device driver usb
[    0.094469] ACPI: WMI: Mapper loaded
[    0.094471] PCI: Using ACPI for IRQ routing
[    0.094615] NetLabel: Initializing
[    0.094617] NetLabel:  domain hash size = 128
[    0.094619] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.094631] NetLabel:  unlabeled traffic allowed by default
[    0.094654] Switching to clocksource tsc
[    0.095995] AppArmor: AppArmor Filesystem Enabled
[    0.095995] pnp: PnP ACPI init
[    0.095995] ACPI: bus type pnp registered
[    0.095995] pnp 00:09: mem resource (0x0-0xfff) overlaps 0000:01:00.0 BAR 6 (0x0-0x1ffff), disabling
[    0.095995] pnp: PnP ACPI: found 10 devices
[    0.095995] ACPI: ACPI bus type pnp unregistered
[    0.095995] PnPBIOS: Disabled by ACPI PNP
[    0.095995] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.095995] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.095995] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.095995] system 00:08: ioport range 0x1080-0x1080 has been reserved
[    0.095995] system 00:08: ioport range 0x200-0x20f has been reserved
[    0.095995] system 00:08: ioport range 0x87f-0x87f has been reserved
[    0.095995] system 00:08: ioport range 0x220-0x22f has been reserved
[    0.095995] system 00:08: ioport range 0x40b-0x40b has been reserved
[    0.095995] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.095995] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[    0.095995] system 00:08: ioport range 0x530-0x537 has been reserved
[    0.095995] system 00:08: ioport range 0xc00-0xc01 has been reserved
[    0.095995] system 00:08: ioport range 0xc14-0xc14 has been reserved
[    0.095995] system 00:08: ioport range 0xc50-0xc52 has been reserved
[    0.095995] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[    0.095995] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[    0.095995] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[    0.095995] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[    0.095995] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[    0.095995] system 00:08: ioport range 0x8000-0x805f has been reserved
[    0.095995] system 00:08: ioport range 0xf40-0xf47 has been reserved
[    0.095995] system 00:08: ioport range 0x87f-0x87f has been reserved
[    0.095995] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[    0.095995] system 00:09: iomem range 0xe0000000-0xe0ffffff has been reserved
[    0.095995] system 00:09: iomem range 0xfec00000-0xfeffffff could not be reserved
[    0.095995] system 00:09: iomem range 0xfff80000-0xffffffff has been reserved
[    0.130347] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.130350] pci 0000:00:02.0:   IO window: 0x9000-0x9fff
[    0.130354] pci 0000:00:02.0:   MEM window: 0xc0000000-0xc00fffff
[    0.130357] pci 0000:00:02.0:   PREFETCH window: 0xc8000000-0xcfffffff
[    0.130361] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
[    0.130363] pci 0000:00:06.0:   IO window: 0xa000-0xafff
[    0.130366] pci 0000:00:06.0:   MEM window: 0xc0100000-0xc01fffff
[    0.130369] pci 0000:00:06.0:   PREFETCH window: disabled
[    0.130374] pci 0000:03:05.0: CardBus bridge, secondary bus 0000:04
[    0.130377] pci 0000:03:05.0:   IO window: 0x00b400-0x00b4ff
[    0.130383] pci 0000:03:05.0:   IO window: 0x00b800-0x00b8ff
[    0.130389] pci 0000:03:05.0:   PREFETCH window: 0x40000000-0x43ffffff
[    0.130395] pci 0000:03:05.0:   MEM window: 0x44000000-0x47ffffff
[    0.130401] pci 0000:00:14.4: PCI bridge, secondary bus 0000:03
[    0.130405] pci 0000:00:14.4:   IO window: 0xb000-0xbfff
[    0.130412] pci 0000:00:14.4:   MEM window: 0xc0200000-0xc02fffff
[    0.130417] pci 0000:00:14.4:   PREFETCH window: 0x40000000-0x43ffffff
[    0.130431] pci 0000:00:02.0: setting latency timer to 64
[    0.130436] pci 0000:00:06.0: setting latency timer to 64
[    0.130455]   alloc irq_desc for 22 on node -1
[    0.130457]   alloc kstat_irqs on node -1
[    0.130461] pci 0000:03:05.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    0.130469] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.130471] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.130474] pci_bus 0000:01: resource 0 io:  [0x9000-0x9fff]
[    0.130476] pci_bus 0000:01: resource 1 mem: [0xc0000000-0xc00fffff]
[    0.130479] pci_bus 0000:01: resource 2 pref mem [0xc8000000-0xcfffffff]
[    0.130481] pci_bus 0000:02: resource 0 io:  [0xa000-0xafff]
[    0.130483] pci_bus 0000:02: resource 1 mem: [0xc0100000-0xc01fffff]
[    0.130486] pci_bus 0000:03: resource 0 io:  [0xb000-0xbfff]
[    0.130488] pci_bus 0000:03: resource 1 mem: [0xc0200000-0xc02fffff]
[    0.130491] pci_bus 0000:03: resource 2 pref mem [0x40000000-0x43ffffff]
[    0.130493] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.130495] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.130498] pci_bus 0000:04: resource 0 io:  [0xb400-0xb4ff]
[    0.130500] pci_bus 0000:04: resource 1 io:  [0xb800-0xb8ff]
[    0.130502] pci_bus 0000:04: resource 2 pref mem [0x40000000-0x43ffffff]
[    0.130504] pci_bus 0000:04: resource 3 mem: [0x44000000-0x47ffffff]
[    0.130534] NET: Registered protocol family 2
[    0.130618] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.130975] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.131944] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.132451] TCP: Hash tables configured (established 131072 bind 65536)
[    0.132454] TCP reno registered
[    0.132555] NET: Registered protocol family 1
[    0.132569] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.793439] pci 0000:01:00.0: Boot video device
[    0.793627] cpufreq-nforce2: No nForce2 chipset.
[    0.793652] Scanning for low memory corruption every 60 seconds
[    0.793761] audit: initializing netlink socket (disabled)
[    0.793776] type=2000 audit(1274271292.793:1): initialized
[    0.802228] Trying to unpack rootfs image as initramfs...
[    0.813599] highmem bounce pool size: 64 pages
[    0.813605] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.814853] VFS: Disk quotas dquot_6.5.2
[    0.814907] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.821690] fuse init (API version 7.13)
[    0.821793] msgmni has been set to 1716
[    0.822003] alg: No test for stdrng (krng)
[    0.822055] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.822058] io scheduler noop registered
[    0.822060] io scheduler anticipatory registered
[    0.822062] io scheduler deadline registered
[    0.822094] io scheduler cfq registered (default)
[    0.822231] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.822250] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.822869] ACPI: AC Adapter [AC] (on-line)
[    0.822920] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.822923] ACPI: Power Button [PWRB]
[    0.822960] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.822966] ACPI: Sleep Button [SLPB]
[    0.823005] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    0.824628] ACPI: Lid Switch [LID]
[    0.824672] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.824675] ACPI: Power Button [PWRF]
[    0.824812] Marking TSC unstable due to TSC halts in idle
[    0.824871] processor LNXCPU:00: registered as cooling_device0
[    0.827364] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.827627]   alloc irq_desc for 17 on node -1
[    0.827629]   alloc kstat_irqs on node -1
[    0.827636] serial 0000:00:14.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.827644] serial 0000:00:14.6: PCI INT B disabled
[    0.828449] brd: module loaded
[    0.833138] loop: module loaded
[    0.833235] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.833388]   alloc irq_desc for 16 on node -1
[    0.833390]   alloc kstat_irqs on node -1
[    0.833396] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.833449] pata_acpi 0000:00:14.1: setting latency timer to 64
[    0.833699] Fixed MDIO Bus: probed
[    0.833726] PPP generic driver version 2.4.2
[    0.833760] tun: Universal TUN/TAP device driver, 1.6
[    0.833762] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.833826] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.833842]   alloc irq_desc for 19 on node -1
[    0.833844]   alloc kstat_irqs on node -1
[    0.833847] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.833867] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.833894] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    0.833956] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0502000
[    0.833979] Switching to clocksource acpi_pm
[    0.834010] isapnp: Scanning for PnP cards...
[    0.886756] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.886878] usb usb1: configuration #1 chosen from 1 choice
[    0.886931] hub 1-0:1.0: USB hub found
[    0.886940] hub 1-0:1.0: 8 ports detected
[    0.887014] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.887028] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.887043] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.887073] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.887093] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0500000
[    0.914310] ACPI: Battery Slot [BAT0] (battery present)
[    0.979891] usb usb2: configuration #1 chosen from 1 choice
[    0.979925] hub 2-0:1.0: USB hub found
[    0.979940] hub 2-0:1.0: 4 ports detected
[    0.980023] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.980045] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.980084] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    0.980107] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0501000
[    1.067975] usb usb3: configuration #1 chosen from 1 choice
[    1.068027] hub 3-0:1.0: USB hub found
[    1.068043] hub 3-0:1.0: 4 ports detected
[    1.068107] uhci_hcd: USB Universal Host Controller Interface driver
[    1.068191] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.070457] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.070464] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.076284] mice: PS/2 mouse device common for all mice
[    1.076435] rtc_cmos 00:04: RTC can wake from S4
[    1.076472] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.076509] rtc0: alarms up to one month, 114 bytes nvram
[    1.076618] device-mapper: uevent: version 1.0.3
[    1.076718] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.076764] device-mapper: multipath: version 1.1.0 loaded
[    1.076767] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.076870] EISA: Probing bus 0 at eisa.0
[    1.076878] Cannot allocate resource for EISA slot 1
[    1.076906] Cannot allocate resource for EISA slot 8
[    1.076908] EISA: Detected 0 cards.
[    1.079553] cpuidle: using governor ladder
[    1.079600] cpuidle: using governor menu
[    1.079961] TCP cubic registered
[    1.080125] NET: Registered protocol family 10
[    1.080489] lo: Disabled Privacy Extensions
[    1.080742] NET: Registered protocol family 17
[    1.080772] powernow-k8: Found 1 Mobile AMD Athlon(tm) 64 Processor 3700+ processors (1 cpu cores) (version 2.20.00)
[    1.080816] powernow-k8:    0 : fid 0x10 (2400 MHz), vid 0x8
[    1.080818] powernow-k8:    1 : fid 0xe (2200 MHz), vid 0xa
[    1.080820] powernow-k8:    2 : fid 0xc (2000 MHz), vid 0xc
[    1.080822] powernow-k8:    3 : fid 0xa (1800 MHz), vid 0xe
[    1.080824] powernow-k8:    4 : fid 0x8 (1600 MHz), vid 0x10
[    1.080826] powernow-k8:    5 : fid 0x0 (800 MHz), vid 0x18
[    1.080861] Using IPI No-Shortcut mode
[    1.080933] PM: Resume from disk failed.
[    1.080944] registered taskstats version 1
[    1.081258]   Magic number: 10:859:228
[    1.081365] rtc_cmos 00:04: setting system clock to 2010-05-19 12:14:54 UTC (1274271294)
[    1.081368] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.081369] EDD information not available.
[    1.106238] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    1.188626] Freeing initrd memory: 7776k freed
[    1.370451] isapnp: No Plug & Play device found
[    1.370469] Freeing unused kernel memory: 656k freed
[    1.371226] Write protecting the kernel text: 4676k
[    1.371254] Write protecting the kernel read-only data: 1840k
[    1.385744] udev: starting version 151
[    1.496741] usb 2-1: new low speed USB device using ohci_hcd and address 2
[    1.553393] scsi0 : pata_atiixp
[    1.553531] scsi1 : pata_atiixp
[    1.554467] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8410 irq 14
[    1.554470] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8418 irq 15
[    1.564738] b43-pci-bridge 0000:03:07.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.567567] sky2 driver version 1.25
[    1.568570] sky2 0000:02:00.0: power state changed by ACPI to D0
[    1.568578]   alloc irq_desc for 18 on node -1
[    1.568580]   alloc kstat_irqs on node -1
[    1.568586] sky2 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.568596] sky2 0000:02:00.0: setting latency timer to 64
[    1.568628] sky2 0000:02:00.0: Yukon-2 FE chip revision 1
[    1.569193] sky2 eth0: addr 00:03:25:1b:f2:62
[    1.624075] ssb: Sonics Silicon Backplane found on PCI device 0000:03:07.0
[    1.707976] usb 2-1: configuration #1 chosen from 1 choice
[    1.909708] ata1.00: ATA-8: WDC WD3200BEVE-00A0HT0, 11.01A11, max UDMA/100
[    1.909712] ata1.00: 625142448 sectors, multi 16: LBA48 
[    1.925242] ata1.00: configured for UDMA/100
[    1.925346] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BEVE-0 11.0 PQ: 0 ANSI: 5
[    1.925478] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.925772] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.925808] sd 0:0:0:0: [sda] Write Protect is off
[    1.925810] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.925829] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.925935]  sda: sda1 sda2 < sda5 > sda3
[    1.962548] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.088603] ata2.00: ATAPI: HL-DT-ST DVD-RW GCA-4080N, 0G34, max UDMA/33
[    2.104557] ata2.00: configured for UDMA/33
[    2.110525] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-RW GCA-4080N 0G34 PQ: 0 ANSI: 5
[    2.122540] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.122542] Uniform CD-ROM driver Revision: 3.20
[    2.122609] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.122644] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.127964]   alloc irq_desc for 23 on node -1
[    2.127968]   alloc kstat_irqs on node -1
[    2.127975] ohci1394 0000:03:0e.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.135588] usbcore: registered new interface driver hiddev
[    2.140297] input: Logitech N48 as /devices/pci0000:00/0000:00:13.0/usb2/2-1/2-1:1.0/input/input6
[    2.140382] generic-usb 0003:046D:C001.0001: input,hidraw0: USB HID v1.00 Mouse [Logitech N48] on usb-0000:00:13.0-1/input0
[    2.140409] usbcore: registered new interface driver usbhid
[    2.140415] usbhid: v2.6:USB HID core driver
[    2.186066] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[23]  MMIO=[c0203000-c02037ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.390419] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    3.460134] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000325215000325b]
[   10.836943] udev: starting version 151
[   10.895374] Adding 3004112k swap on /dev/sda5.  Priority:-1 extents:1 across:3004112k 
[   10.945321] lp: driver loaded but no devices found
[   10.950702] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8400, revision 0
[   10.955310] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.172843] Linux agpgart interface v0.103
[   11.261507] cfg80211: Calling CRDA to update world regulatory domain
[   11.300863] cfg80211: World regulatory domain updated:
[   11.300867] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   11.300870] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.300873] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.300876] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.300878] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.300880] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.328409] type=1505 audit(1274271304.746:2):  operation="profile_load" pid=565 name="/sbin/dhclient3"
[   11.328655] type=1505 audit(1274271304.746:3):  operation="profile_load" pid=565 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   11.328791] type=1505 audit(1274271304.746:4):  operation="profile_load" pid=565 name="/usr/lib/connman/scripts/dhclient-script"
[   11.329383] [drm] Initialized drm 1.1.0 20060810
[   11.381388] yenta_cardbus 0000:03:05.0: CardBus bridge found [107b:0506]
[   11.381419] yenta_cardbus 0000:03:05.0: Using CSCINT to route CSC interrupts to PCI
[   11.381421] yenta_cardbus 0000:03:05.0: Routing CardBus interrupts to PCI
[   11.381428] yenta_cardbus 0000:03:05.0: TI: mfunc 0x01001002, devctl 0x44
[   11.430084] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   11.517173] [drm] radeon defaulting to kernel modesetting.
[   11.517177] [drm] radeon kernel modesetting enabled.
[   11.517239] radeon 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   11.517246] radeon 0000:01:00.0: setting latency timer to 64
[   11.532307] [drm] radeon: Initializing kernel modesetting.
[   11.534383] [drm] register mmio base: 0xC0000000
[   11.534386] [drm] register mmio size: 65536
[   11.534752] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   11.534772] [drm] Generation 2 PCI interface, using max accessible memory
[   11.534775] [drm] radeon: VRAM 128M
[   11.534777] [drm] radeon: VRAM from 0x00000000 to 0x07FFFFFF
[   11.534778] [drm] radeon: GTT 512M
[   11.534780] [drm] radeon: GTT from 0x20000000 to 0x3FFFFFFF
[   11.534808] [drm] radeon: irq initialized.
[   11.535032] [drm] Detected VRAM RAM=128M, BAR=128M
[   11.535036] [drm] RAM width 128bits DDR
[   11.535130] [TTM] Zone  kernel: Available graphics memory: 443650 kiB.
[   11.535132] [TTM] Zone highmem: Available graphics memory: 512550 kiB.
[   11.535149] [drm] radeon: 128M of VRAM memory ready
[   11.535151] [drm] radeon: 512M of GTT memory ready.
[   11.535172] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   11.535865] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
[   11.535910] [drm] PCIE GART of 512M enabled (table at 0x00040000).
[   11.535920] [drm] radeon: cp idle (0x10000C03)
[   11.536129] [drm] Loading R300 Microcode
[   11.536541] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
[   11.541809] [drm] radeon: ring at 0x0000000020000000
[   11.541831] [drm] ring test succeeded in 1 usecs
[   11.541952] [drm] radeon: ib pool ready.
[   11.542015] [drm] ib test succeeded in 0 usecs
[   11.542122] [drm] Panel ID String: SEC                     
[   11.542124] [drm] Panel Size 1280x800
[   11.542150] [drm] Default TV standard: NTSC-J
[   11.542152] [drm] 27.000000000 MHz TV ref clk
[   11.542155] [drm] Default TV standard: NTSC-J
[   11.542157] [drm] 27.000000000 MHz TV ref clk
[   11.542182] [drm] Radeon Display Connectors
[   11.542183] [drm] Connector 0:
[   11.542185] [drm]   VGA
[   11.542187] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   11.542189] [drm]   Encoders:
[   11.542191] [drm]     CRT1: INTERNAL_DAC1
[   11.542193] [drm] Connector 1:
[   11.542194] [drm]   LVDS
[   11.542195] [drm]   Encoders:
[   11.542197] [drm]     LCD1: INTERNAL_LVDS
[   11.542198] [drm] Connector 2:
[   11.542200] [drm]   S-video
[   11.542201] [drm]   Encoders:
[   11.542202] [drm]     TV1: INTERNAL_DAC2
[   11.574665] phy0: Selected rate control algorithm 'minstrel'
[   11.575291] Registered led device: b43-phy0::tx
[   11.575305] Registered led device: b43-phy0::rx
[   11.575320] Registered led device: b43-phy0::radio
[   11.575375] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   11.611125] [drm] fb mappable at 0xC80C0000
[   11.611129] [drm] vram apper at 0xC8000000
[   11.611130] [drm] size 4096000
[   11.611132] [drm] fb depth is 24
[   11.611133] [drm]    pitch is 5120
[   11.613150] yenta_cardbus 0000:03:05.0: ISA IRQ mask 0x0cf8, PCI irq 22
[   11.613154] yenta_cardbus 0000:03:05.0: Socket status: 30000006
[   11.613157] pci_bus 0000:03: Raising subordinate bus# of parent bus (#03) from #04 to #07
[   11.613165] yenta_cardbus 0000:03:05.0: pcmcia: parent PCI bridge I/O window: 0xb000 - 0xbfff
[   11.613169] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xb000-0xbfff: clean.
[   11.613328] yenta_cardbus 0000:03:05.0: pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc02fffff
[   11.613331] yenta_cardbus 0000:03:05.0: pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x43ffffff
[   11.623456] fb0: radeondrmfb frame buffer device
[   11.623458] registered panic notifier
[   11.623464] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
[   11.626413] vga16fb: initializing
[   11.626417] vga16fb: mapped to 0xc00a0000
[   11.626424] vga16fb: not registering due to another framebuffer present
[   11.714257] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   11.752675] Console: switching to colour frame buffer device 160x50
[   11.810457] ATI IXP MC97 controller 0000:00:14.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   11.886241] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x236eb3, caps: 0x904713/0x10008
[   11.908760] EXT4-fs (sda3): mounted filesystem with ordered data mode
[   11.920160] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   11.924174] MC'97 0 converters and GPIO not ready (0x1)
[   12.349284] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   12.351610] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   12.352606] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   12.353410] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   12.354256] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   14.628837] type=1505 audit(1274271308.046:5):  operation="profile_load" pid=776 name="/usr/share/gdm/guest-session/Xsession"
[   14.630275] type=1505 audit(1274271308.046:6):  operation="profile_replace" pid=777 name="/sbin/dhclient3"
[   14.630537] type=1505 audit(1274271308.046:7):  operation="profile_replace" pid=777 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   14.630682] type=1505 audit(1274271308.046:8):  operation="profile_replace" pid=777 name="/usr/lib/connman/scripts/dhclient-script"
[   14.634484] type=1505 audit(1274271308.050:9):  operation="profile_load" pid=778 name="/usr/bin/evince"
[   14.637913] type=1505 audit(1274271308.054:10):  operation="profile_load" pid=778 name="/usr/bin/evince-previewer"
[   14.639860] type=1505 audit(1274271308.054:11):  operation="profile_load" pid=778 name="/usr/bin/evince-thumbnailer"
[   14.682439] sky2 eth0: enabling interface
[   14.682625] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.732065] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   14.733814] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   14.736927] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   14.741651] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   14.860056] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
[   14.860063] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed soon (official deadline was July 2008).
[   14.860067] b43-phy0 warning: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   14.900885] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.387440] ppdev: user-space parallel port driver
[   17.660034] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   17.660223] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   23.388287] wlan0: deauthenticating from 00:1c:df:3a:de:f9 by local choice (reason=3)
[   23.389224] wlan0: direct probe to AP 00:1c:df:3a:de:f9 (try 1)
[   23.392244] wlan0: direct probe responded
[   23.392248] wlan0: authenticate with AP 00:1c:df:3a:de:f9 (try 1)
[   23.393974] wlan0: authenticated
[   23.393989] wlan0: associate with AP 00:1c:df:3a:de:f9 (try 1)
[   23.396572] wlan0: RX AssocResp from 00:1c:df:3a:de:f9 (capab=0x421 status=0 aid=1)
[   23.396574] wlan0: associated
[   23.397146] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   28.456035] eth0: no IPv6 routers present
[   33.736033] wlan0: no IPv6 routers present
cmcanulty@Gateway:~$ 
```

---

### Post by Andrew James Collett on 2010-05-19
Hey guys. I also have the same issue, my usb hard drive, newly bought, is not being recognized by ubuntu, but it mounts just fine on windows 7. When i plug it in to my ubuntu pc it sounds like its starting up and then dying, but it has an external power source. It is a 1 TB HD in an External enclosure, and it is a samsung. It also does the same thing on another Ubuntu PC

Here is the dmesg output i get after plugging it in

[FONT=monospace][ 1153.512040] usb 1-4: new high speed USB device using ehci_hcd and address 5
[ 1153.660283] hub 1-0:1.0: unable to enumerate USB

 device on port 4
[ 1154.116033] usb 2-4: new full speed USB device using ohci_hcd and address 85
[ 1154.316456] usb 2-4: not running at top speed; connect to a high speed hub
[ 1154.334593] usb 2-4: configuration #1 chosen from 1 choice
[ 1154.413415] Initializing USB Mass Storage driver...
[ 1154.413559] scsi6 : SCSI emulation for USB Mass Storage devices
[ 1154.413790] usbcore: registered new interface driver usb-storage
[ 1154.413796] USB Mass Storage support registered.
[ 1154.418170] usb-storage: device found at 85
[ 1154.418174] usb-storage: waiting for device to settle before scanning
[ 1154.444495] hub 2-0:1.0: port 4 disabled by hub (EMI?), re-enabling...
[ 1154.444503] usb 2-4: USB disconnect, address 85
[ 1155.480023] usb 2-4: new full speed USB device using ohci_hcd and address 86
[ 1155.668036] usb 2-4: device descriptor read/64, error -62
[ 1155.952030] usb 2-4: device descriptor read/64, error -62
[ 1156.232029] usb 2-4: new full speed USB device using ohci_hcd and address 87
[ 1156.356036] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 1159.772023] hub 2-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 1159.948030] usb 2-4: new full speed USB device using ohci_hcd and address 89
[ 1160.144024] usb 2-4: device descriptor read/64, error -62
[ 1163.188025] usb 2-4: device descriptor read/64, error -62
[ 1163.468042] usb 2-4: new full speed USB device using ohci_hcd and address 90
[ 1163.495585] usb 2-4: device descriptor read/8, error -62
[ 1163.619600] usb 2-4: device descriptor read/8, error -62
[ 1165.248041] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 1165.552027] usb 2-4: new full speed USB device using ohci_hcd and address 92
[ 1165.756065] usb 2-4: device descriptor read/64, error -62
[ 1167.448024] usb 2-4: device descriptor read/64, error -62
[ 1167.728024] usb 2-4: new full speed USB device using ohci_hcd and address 93
[ 1167.908030] usb 2-4: device descriptor read/64, error -62
[ 1168.924027] usb 2-4: device descriptor read/64, error -62
[ 1169.204033] usb 2-4: new full speed USB device using ohci_hcd and address 94
[ 1169.612023] usb 2-4: device not accepting address 94, error -62
[ 1169.788024] usb 2-4: new full speed USB device using ohci_hcd and address 95
[ 1169.827367] usb 2-4: device descriptor read/8, error -62
[ 1169.951384] usb 2-4: device descriptor read/8, error -62
[ 1170.052043] hub 2-0:1.0: unable to enumerate USB device on port 4




Pls help!

Andrew
[/FONT]

---

