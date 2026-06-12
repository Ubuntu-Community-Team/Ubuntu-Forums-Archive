---
title: "erratic drive behavior -- CD-RW/DVD±RW mounting issue"
date: 2009-07-22
forum: General Help
---

### Post by ecmatter on 2009-07-22
My CD-RW/DVD±RW drive only works every now and again in Ubuntu (works perfectly in Windows).

When I boot up, there is a CD-RW/DVD±RW Drive listed in Nautilus (computer:///)
When I insert an audio cd, it will either a) change the icon in nautilus from CD-RW/DVD±RW Drive to AudioCD, and place an AudioCD icon on the desktop; or  b) do nothing.

If the AudioCD is recognized, I can view the tracks and either a) play/rip/etc... the tracks without problem; b) play/rip/etc... the tracks for a while before the CD quits and is no longer available; or c) not be able to play any of the tracks (Rhythmbox, soundjuicer, VLC all spit out errors).

DVD's seem to work fine, though data cd-r's usually read as blank discs.

I've tried a little bit of everything to fix this.  I've changed options in fstab for hdc, I've tried different installs (currently on a week old Ubuntu Hardy install -- fully updated, but had the same erratic behavior in Xubuntu Jaunty.  I've tried different audio cd's.  I've pulled the drive and stuck it in a Windows laptop (where it worked flawlessly).  My Bios is up to date

**My question is: is there anything I've overlooked?  Looking at bug reports, there's been a lot of problems with erratic cd drive behavior dating back to Dapper, but never any resolution.  What should I do next to try to get this thing working?  The behavior is so erratic that it's been incredibly difficult to pin anything down.**

Here's the relevant output from mtab, fstab, dmesg, etc...
(note that mtab doesn't change at all, no matter if a cd is loaded and playable or not.)

```

**from dmesg:**
[   38.050735] hdc: MATSHITADVD-RAM UJ-850S, ATAPI CD/DVD-ROM drive
[   38.050801] hdc: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[   38.051110] hdc: UDMA/33 mode selected
[   38.051551] ide1 at 0x170-0x177,0x376 on irq 15
[   38.056098] ACPI: PCI Interrupt 0000:09:06.0[A] -> GSI 22 (level, low) -> IRQ

**~$ cat /etc/fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4ac0e0ae-170e-45f0-82d1-56e1c728c442 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=caf570be-6a33-4abd-8033-b47b733ae951 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


**~$ cat /etc/mtab**
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-24-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
gvfs-fuse-daemon /home/********/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=******** 0 0

**~$ dmesg | tail**
[ 5094.855326] hdc: drive not ready for command
[ 5099.851679] hdc: status timeout: status=0xa0 { Busy }
[ 5099.851687] ide: failed opcode was: unknown
[ 5099.851692] hdc: drive not ready for command
[ 5164.261268] hdc: lost interrupt
[ 5164.261334] hdc: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
[ 5164.261347] hdc: status error: error=0x00 { }
[ 5164.261351] ide: failed opcode was: unknown
[ 5164.261358] hdc: drive not ready for command

**$ sudo mount -t /dev/hdc /media/cdrom0**
[sudo] password for ********: 
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

```

---

### Post by ecmatter on 2009-07-22
Hmmm...

It looks like I'll either need to buy a different drive (not that there's anything wrong with the one I have) or gather enough Linux skills to fix the kernel myself (and by the time that happens DVD's and CD's will be relics and this laptop will be long dead).  So are there any CD-RW/DVD±RW drives that work in linux?  What brands?  Or, if you have a Matshita UJ-850S drive, and it works in Linux, what distro and kernel are you using and how did you get it to work?

---

### Post by Braytok on 2009-07-22
I've been searching for months for a solution to this exact same problem. Ironically the drive I'm using (TSSTcorp CD/DVDW SH-S182D) works find in windows, Solaris, and Fedora but fails with Ubuntu. I've had this problem since Hardy.

Here are my relevant outputs as well.

dmesg-
```


[    0.408146] ACPI: Interpreter enabled
[    0.408149] ACPI: (supports S0 S1 S3 S4 S5)
[    0.408169] ACPI: Using IOAPIC for interrupt routing
[    0.408227] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.415839] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.428682] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.439001] ACPI: No dock devices found.
[    0.439064] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.439124] pci 0000:00:00.0: reg 10 32bit mmio: [0xd0000000-0xdfffffff]
[    0.439422] pci 0000:00:01.0: supports D1
[    0.439454] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.439458] pci 0000:00:02.0: PME# disabled
[    0.439501] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.439505] pci 0000:00:03.0: PME# disabled
[    0.439548] pci 0000:00:0c.0: reg 10 io port: [0xec00-0xec3f]
[    0.439578] pci 0000:00:0c.0: supports D2
[    0.439607] pci 0000:00:0e.0: reg 10 io port: [0xe800-0xe8ff]
[    0.439613] pci 0000:00:0e.0: reg 14 32bit mmio: [0xfebffc00-0xfebffcff]
[    0.439639] pci 0000:00:0e.0: supports D1 D2
[    0.439641] pci 0000:00:0e.0: PME# supported from D1 D2 D3hot D3cold
[    0.439644] pci 0000:00:0e.0: PME# disabled
[    0.439673] pci 0000:00:0f.0: reg 10 io port: [0xe400-0xe407]
[    0.439678] pci 0000:00:0f.0: reg 14 io port: [0xe000-0xe003]
[    0.439684] pci 0000:00:0f.0: reg 18 io port: [0xdc00-0xdc07]
[    0.439690] pci 0000:00:0f.0: reg 1c io port: [0xd800-0xd803]
[    0.439695] pci 0000:00:0f.0: reg 20 io port: [0xd400-0xd40f]
[    0.439701] pci 0000:00:0f.0: reg 24 io port: [0xd000-0xd0ff]
[    0.439757] pci 0000:00:0f.1: reg 20 io port: [0xfc00-0xfc0f]
[    0.439823] pci 0000:00:10.0: reg 20 io port: [0xcc00-0xcc1f]
[    0.439838] pci 0000:00:10.0: supports D1 D2
[    0.439839] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.439843] pci 0000:00:10.0: PME# disabled
[    0.439884] pci 0000:00:10.1: reg 20 io port: [0xc800-0xc81f]
[    0.439899] pci 0000:00:10.1: supports D1 D2
[    0.439900] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.439904] pci 0000:00:10.1: PME# disabled
[    0.439946] pci 0000:00:10.2: reg 20 io port: [0xc400-0xc41f]
[    0.439960] pci 0000:00:10.2: supports D1 D2
[    0.439962] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.439965] pci 0000:00:10.2: PME# disabled
[    0.440014] pci 0000:00:10.3: reg 20 io port: [0xc000-0xc01f]

```

fstab-
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9617977e-e553-4869-b78d-891ddce8133e /               ext3    relatime,erro$
# /dev/sda5
UUID=fc43e0da-6553-4b57-a3c3-360cf4bc6c20 none            swap    sw           $
/dev/scd0       /media/cdrom   udf,iso9660 user,noauto,exec,utf8 0       0

```

mtab-
```

/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.28-13-generic/volatile tmpfs rw,mode=755 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/cameron/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user$

```

---

### Post by ecmatter on 2009-07-22
<bumpity-bump>

---

### Post by ecmatter on 2009-07-23
<sigh>

---

### Post by ecmatter on 2009-07-24
I give up.

I like Ubuntu, but Ubuntu doesn't like me.  If I can manage to get Ubuntu to recognize my drive long enough to burn an iso, I'll install Fedora and report back with the results.

---

### Post by Raffles10 on 2009-07-24
I suspect that won't make any difference. I've had lots of cd/dvd mounting/burning problems with different linux distributions, currently using Arch, still have problems.

I have two Lite-on dvd-rw drives that work flawlessly in vista but not in linux, it's just something I've come to accept, linux has problems with optical drives. :(

If I want to burn/mount a cd I place it in the drive then reboot, it's the only way that linux will read the disc.

---

### Post by ecmatter on 2009-07-25
Yeah, rebooting is the only way I can access a disk in Ubuntu.  The problem is, the disk doesn't remain available long enough to do much of anything with it.

I played around with the acpi/apic/irq options in /boot/grub/menu.list last night and got nowhere.  I don't have my notes with me, but one combination of options gave me what appeared to be a functioning cd drive, but left me with no sound and idle cpu temps of around 90C.

I couldn't keep the drive up long enough to burn a Fedora Live CD, but I did manage to burn a Puppy Live CD, and following a full install, the drive works flawlessly.

So I guess that that's my solution for now -- boot into Puppy whenever I need to burn a disc.

---

