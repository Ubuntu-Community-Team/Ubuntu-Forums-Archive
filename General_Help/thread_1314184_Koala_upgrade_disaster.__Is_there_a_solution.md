---
title: "Koala upgrade disaster.  Is there a solution?"
date: 2009-11-04
forum: General Help
---

### Post by SpotTheWonderDog on 2009-11-04
After banging my head against the wall for two+ solid days trying to recover from upgrading to Koala from Jaunty, I'm just about ready to throw in the towel.

For safety's sake, I was going to clone my hard disk at work but they didn't have a 320GB hard disk to clone to. I bought one on my own but it arrived after I had upgraded to Koala. Bad timing and big mistake on my part.

On Windows, I Ghost the OS partition before I make *any* changes but I don't know how to do that in Ubuntu. I don't know how to save a partition to another but that's for another day.

I'm a developer. I don't know the ins and outs of Ubuntu/Linux. I can drive a car and I know the basics of an automobile but I'm not qualified to rebuild the engine.

I need to know if there's a way I can get my system running again without having to wipe the system and reload.

I spent months configuring the system and being new to Linux/Ubuntu, when I set up the system I didn't make a separate home partition like I do for Windows (technically, it's not a home partition in Windows, but you get the idea).

I can't boot up in 2.6.31-14 without the system crashing ("General error mounting filesystems"). I can boot up in 2.6.28-15. The system starts off with the Jaunty back-and-forth loading window then jumps to the Koala loading window.

I've lost days of productivity and after reading many threads (after upgrading to Koala), I'm now a lot wiser. But the damage has already been done.

I desperately need to know if I can revert back to Jaunty without losing everything, or if I can get Koala to run. I think there's a problem with either fstab or menu.lst but I'm not sure.

The Ubuntu disk is on a separate hard disk. No dual boot.

Also,
Restore no longer works.
Audio no longer works.

I entered every command that someone mentioned in the forums and posted the results here.

```
$ fdisk -l

```Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91ca91ca

Device Boot Start End Blocks Id System
/dev/sdc1 * 1 1044 8385898+ 7 HPFS/NTFS
/dev/sdc2 1045 77826 616751415 f W95 Ext'd (LBA)
/dev/sdc5 ? 23062 45079 176851594+ 15 Unknown

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe5e5e5e5

Device Boot Start End Blocks Id System
/dev/sdd1 * 1 38157 306496071 83 Linux
/dev/sdd2 38158 38913 6072570 5 Extended
/dev/sdd5 38158 38913 6072538+ 82 Linux swap / Solaris

```
$ update-grub
```Searching for GRUB installation directory ... found: /boot/grub
findfs: unable to resolve 'UUID=31038fcb-b7d2-45e7-80fc-ebf9ee8b3bd2'
Cannot determine root device. Assuming /dev/hda1
This error is probably caused by an invalid /etc/fstab
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found kernel: /boot/vmlinuz-2.6.28-15-generic
Found kernel: /boot/vmlinuz-2.6.28-13-generic
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```
$ ls -l /dev/disk/by-uuid
```total 0
lrwxrwxrwx 1 root root 10 2009-11-03 16:57 4CD4E2E9D4E2D3EC -> ../../sda7
lrwxrwxrwx 1 root root 10 2009-11-03 16:57 54A4B449A4B42F7C -> ../../sda5
lrwxrwxrwx 1 root root 10 2009-11-03 16:57 80980CBF980CB5A6 -> ../../sda9
lrwxrwxrwx 1 root root 10 2009-11-03 16:57 A86C2B146C2ADD36 -> ../../sda6
lrwxrwxrwx 1 root root 10 2009-11-03 16:57 B4A000F8A000C2BA -> ../../sda8
lrwxrwxrwx 1 root root 10 2009-11-03 16:57 bb28d2a4-9763-4627-97dc-fe98a51b98c4 -> ../../sdd1
lrwxrwxrwx 1 root root 10 2009-11-03 16:57 d31384db-7522-4340-8fa3-819eaa6d758e -> ../../sdd5after changing uuid in fstab to bb28d2a4-9763-4627-97dc-fe98a51b98c4

```
$ update-grub
```Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found kernel: /boot/vmlinuz-2.6.28-15-generic
Found kernel: /boot/vmlinuz-2.6.28-13-generic
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done$

```
$ cat fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=bb28d2a4-9763-4627-97dc-fe98a51b98c4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d31384db-7522-4340-8fa3-819eaa6d758e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


```
$ cat /boot/grub/menu.lst
```# menu.lst - See: grub(), info grub, update-grub()
# grub-install(), grub-floppy(),
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=bb28d2a4-9763-4627-97dc-fe98a51b98c4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=bb28d2a4-9763-4627-97dc-fe98a51b98c4

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
## indomU=true
## indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##


### I had to manually move 2.6.28-15-generic to the top of the list or the system wouldn't boot
### ('file not found' error message)

title Ubuntu 9.04, kernel 2.6.28-15-generic
uuid bb28d2a4-9763-4627-97dc-fe98a51b98c4
kernel /boot/vmlinuz-2.6.28-15-generic root=UUID=bb28d2a4-9763-4627-97dc-fe98a51b98c4 ro quiet splash
initrd /boot/initrd.img-2.6.28-15-generic
quiet

title Ubuntu 9.04-new, kernel 2.6.28-15-generic (recovery mode)
uuid bb28d2a4-9763-4627-97dc-fe98a51b98c4
kernel /boot/vmlinuz-2.6.28-15-generic root=UUID=bb28d2a4-9763-4627-97dc-fe98a51b98c4 ro single
initrd /boot/initrd.img-2.6.28-15-generic

### 2.6.31-14 results in 'mountall General Error Mounting filesystems'
### and 'file not found' ( I think it's referring to: /boot/vvmlinuz-2.6.31-14 ??)


title Ubuntu 9.04new, kernel 2.6.31-14-generic
uuid bb28d2a4-9763-4627-97dc-fe98a51b98c4
kernel /boot/vvmlinuz-2.6.31-14-generic root=UUID=bb28d2a4-9763-4627-97dc-fe98a51b98c4 ro quiet splash
initrd /boot/initrd.img-2.6.31-14-generic
quiet

title Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid bb28d2a4-9763-4627-97dc-fe98a51b98c4
kernel /boot/vmlinuz-2.6.28-15-generic root=UUID=bb28d2a4-9763-4627-97dc-fe98a51b98c4 ro single
initrd /boot/initrd.img-2.6.28-15-generic

### memtest can't be found
title Ubuntu 9.04, memtest86+
uuid bb28d2a4-9763-4627-97dc-fe98a51b98c4
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```
$ ls -l /boot
```total 51352
-rw-r--r-- 1 root root 508385 2009-04-01 18:46 abi-2.6.27-11-generic
-rw-r--r-- 1 root root 528128 2009-06-30 17:56 abi-2.6.28-13-generic
-rw-r--r-- 1 root root 528310 2009-09-09 08:56 abi-2.6.28-15-generic
-rw-r--r-- 1 root root 629174 2009-10-16 14:03 abi-2.6.31-14-generic
-rw-r--r-- 1 root root 91358 2009-04-01 18:46 config-2.6.27-11-generic
-rw-r--r-- 1 root root 96768 2009-06-30 17:56 config-2.6.28-13-generic
-rw-r--r-- 1 root root 96804 2009-09-09 08:56 config-2.6.28-15-generic
-rw-r--r-- 1 root root 111371 2009-10-16 14:03 config-2.6.31-14-generic
drwxr-xr-x 2 root root 4096 2009-11-03 17:19 grub
-rw-r--r-- 1 root root 8227661 2009-05-03 12:25 initrd.img-2.6.27-11-generic
-rw-r--r-- 1 root root 7548196 2009-07-17 10:04 initrd.img-2.6.28-13-generic
-rw-r--r-- 1 root root 7549168 2009-09-29 10:15 initrd.img-2.6.28-15-generic
-rw-r--r-- 1 root root 7645225 2009-11-02 11:29 initrd.img-2.6.31-14-generic
-rw-r--r-- 1 root root 128796 2009-10-23 12:11 memtest86+.bin
-rw-r--r-- 1 root root 1031799 2009-04-01 18:46 System.map-2.6.27-11-generic
-rw-r--r-- 1 root root 1449810 2009-06-30 17:56 System.map-2.6.28-13-generic
-rw-r--r-- 1 root root 1450680 2009-09-09 08:56 System.map-2.6.28-15-generic
-rw-r--r-- 1 root root 1664737 2009-10-16 14:03 System.map-2.6.31-14-generic
-rw-r--r-- 1 root root 1074 2009-04-01 18:48 vmcoreinfo-2.6.27-11-generic
-rw-r--r-- 1 root root 1074 2009-06-30 17:58 vmcoreinfo-2.6.28-13-generic
-rw-r--r-- 1 root root 1074 2009-09-09 08:58 vmcoreinfo-2.6.28-15-generic
-rw-r--r-- 1 root root 1196 2009-10-16 14:06 vmcoreinfo-2.6.31-14-generic
-rw-r--r-- 1 root root 2249232 2009-04-01 18:46 vmlinuz-2.6.27-11-generic
-rw-r--r-- 1 root root 3488208 2009-06-30 17:56 vmlinuz-2.6.28-13-generic
-rw-r--r-- 1 root root 3491312 2009-09-09 08:56 vmlinuz-2.6.28-15-generic
-rw-r--r-- 1 root root 3890400 2009-10-16 14:03 vmlinuz-2.6.31-14-generic

```
# uname -a
```Linux joe-desktop 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686 GNU/Linux

I'm also having problems with sound which seems to be a common problem. I searched everywhere but so far I've been unable to come up with a solution. I have seen 'solved!' dozens of times but nothing has worked for me.

```
$ lspci | grep -i audio
```00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```
$ cat /proc/asound/cards
```0 [Intel ]: HDA-Intel - HDA Intel
HDA Intel at 0xfebf8000 irq 22

```
$ fuser -v /dev/dsp* /dev/snd/*
```(no output)

```
$ alsa force-reload
```Unloading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc

```
.$ aplay -l
```aplay: device_list:223: no soundcards found...

During bootup, I noticed this: 'PulseAudio configured for per-user sesssions' Is this good or bad or neither?

```
$ alsamixer
```alsamixer: function snd_ctl_open failed for default: No such file or directory

```
$ lspci -v | less
```00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
Subsystem: ASUSTeK Computer Inc. Device 81ec
Flags: bus master, fast devsel, latency 0, IRQ 22
Memory at febf8000 (64-bit, non-prefetchable) [size=16K]
Capabilities: [50] Power Management version 2
Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Sound preferences->Output->Choose a device for sound output:
"Dummy output"$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.18rc3```
.$ ls /etc/asound*
```ls: cannot access /etc/asound*: No such file or directory

```
$ strace -eopen alsamixer
```open("/etc/ld.so.cache", O_RDONLY) = 3
open("/lib/libncurses.so.5", O_RDONLY) = 3
open("/usr/lib/libasound.so.2", O_RDONLY) = 3
open("/lib/tls/i686/cmov/libm.so.6", O_RDONLY) = 3
open("/lib/tls/i686/cmov/libdl.so.2", O_RDONLY) = 3
open("/lib/tls/i686/cmov/libpthread.so.0", O_RDONLY) = 3
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
open("/lib/tls/i686/cmov/librt.so.1", O_RDONLY) = 3
open("/dev/urandom", O_RDONLY) = 3
open("/usr/share/alsa/alsa.conf", O_RDONLY) = 3
open("/usr/share/alsa/pulse.conf", O_RDONLY) = 3
open("/usr/share/alsa/bluetooth.conf", O_RDONLY) = 3
open("/etc/ld.so.cache", O_RDONLY) = 3
open("/usr/lib/alsa-lib/libasound_module_conf_pulse.so", O_RDONLY) = 3
open("/usr/lib/libpulse.so.0", O_RDONLY) = 3
open("/usr/lib/libpulsecommon-0.9.19.so", O_RDONLY) = 3
open("/usr/lib/libX11.so.6", O_RDONLY) = 3
open("/usr/lib/libICE.so.6", O_RDONLY) = 3
open("/usr/lib/libSM.so.6", O_RDONLY) = 3
open("/usr/lib/libXtst.so.6", O_RDONLY) = 3
open("/lib/libwrap.so.0", O_RDONLY) = 3
open("/usr/lib/libsndfile.so.1", O_RDONLY) = 3
open("/lib/libdbus-1.so.3", O_RDONLY) = 3
open("/usr/lib/libxcb.so.1", O_RDONLY) = 3
open("/lib/libuuid.so.1", O_RDONLY) = 3
open("/usr/lib/libXext.so.6", O_RDONLY) = 3
open("/lib/tls/i686/cmov/libnsl.so.1", O_RDONLY) = 3
open("/usr/lib/libFLAC.so.8", O_RDONLY) = 3
open("/usr/lib/libvorbisenc.so.2", O_RDONLY) = 3
open("/usr/lib/libvorbis.so.0", O_RDONLY) = 3
open("/usr/lib/libogg.so.0", O_RDONLY) = 3
open("/usr/lib/libXau.so.6", O_RDONLY) = 3
open("/usr/lib/libXdmcp.so.6", O_RDONLY) = 3
open("/dev/snd/controlC0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/dev/aloadC0", O_RDONLY) = -1 ENOENT (No such file or directory)
alsamixer: function snd_ctl_open failed for default: No such file or directory$ lsmod
Module Size Used by
snd_hda_intel 435252 0
snd_pcm_oss 46336 0
snd_mixer_oss 22656 1 snd_pcm_oss
snd_pcm 83076 2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy 10756 0
snd_seq_oss 37760 0
snd_seq_midi 14336 0
snd_rawmidi 29696 1 snd_seq_midi
snd_seq_midi_event 15104 2 snd_seq_oss,snd_seq_midi
snd_seq 56880 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer 29704 2 snd_pcm,snd_seq
snd_seq_device 14988 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd 62756 9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore 15200 1 snd
snd_page_alloc 16904 2 snd_hda_intel,snd_pcm
sha1_generic 10368 0
arc4 9856 0
ecb 10752 0
ppp_mppe 14724 0
ppp_async 16896 0
crc_ccitt 10112 1 ppp_async
binfmt_misc 16776 1
iptable_filter 10752 0
ip_tables 19600 1 iptable_filter
usblp 20224 0
x_tables 23044 1 ip_tables
nvidia 9594120 26
sbp2 30476 0
usbhid 42336 0
intel_agp 34108 0
ppdev 15620 0
parport_pc 40100 1
lp 17156 0
agpgart 42696 2 nvidia,intel_agp
parport 42220 3 ppdev,parport_pc,lp
ohci1394 38576 0
ieee1394 94660 2 sbp2,ohci1394
floppy 64324 0
atl1 40584 0
mii 13312 1 atl1
fbcon 46112 0
tileblit 10752 1 fbcon
font 16384 1 fbcon
bitblit 13824 1 fbcon
softcursor 9984 1 bitblit

```
$ asoundconf list
```Names of available sound cards:
Intel

```
$ cat /proc/interrupts
``` CPU0 CPU1
0: 165 0 IO-APIC-edge timer
1: 1449 0 IO-APIC-edge i8042
4: 6 0 IO-APIC-edge
6: 5 0 IO-APIC-edge floppy
7: 0 0 IO-APIC-edge parport0
8: 1 0 IO-APIC-edge rtc0
9: 0 0 IO-APIC-fasteoi acpi
16: 727510 0 IO-APIC-fasteoi ahci, uhci_hcd:usb3, nvidia
17: 293821 0 IO-APIC-fasteoi pata_jmicron, uhci_hcd:usb4
18: 0 0 IO-APIC-fasteoi ehci_hcd:usb1, uhci_hcd:usb7
19: 32 0 IO-APIC-fasteoi uhci_hcd:usb6
21: 3 0 IO-APIC-fasteoi ohci1394
22: 11445 0 IO-APIC-fasteoi HDA Intel
23: 35756 0 IO-APIC-fasteoi ehci_hcd:usb2, uhci_hcd:usb5, ohci1394
2298: 25728 0 PCI-MSI-edge eth0
2299: 41924 0 PCI-MSI-edge ahci
NMI: 0 0 Non-maskable interrupts
LOC: 387855 1037249 Local timer interrupts
RES: 3377 4995 Rescheduling interrupts
CAL: 166 607 Function call interrupts
TLB: 922 2323 TLB shootdowns
SPU: 0 0 Spurious interrupts
ERR: 0
MIS: 0

```
$ lspci -s 00:1b.0 -v
```00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
Subsystem: ASUSTeK Computer Inc. Device 81ec
Flags: bus master, fast devsel, latency 0, IRQ 22
Memory at febf8000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel
```


$ cat /etc/modprobe.d/alsa-base.conf
```# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N

---

### Post by m4tic on 2009-11-04
You haven't mentioned the problem, i won't read all the outputs you pasted

---

### Post by SpotTheWonderDog on 2009-11-04
The problem was stated in the beginning of my post:

**I can't boot up in 2.6.31-14 without the system crashing ("General error mounting filesystems"). I can boot up in 2.6.28-15. The system starts off with the Jaunty back-and-forth loading window then jumps to the Koala loading window.**

I've noticed that if a person posts too little information, then people say "how can we solve your problem when we don't know anything" or "have you tried ....?"

And when a person posts as much information as possible, then people complain that it's too much to read.

So, what are the correct number of words, sentences and paragraphs that one should write in a post so elicit a response?

---

### Post by Uncle Spellbinder on 2009-11-04
Clean install. 

Just because it is possible to 'upgrade' does not mean it is the best option. From one OS version to another, clean install is *always* the best option.

---

### Post by ST3ALTHPSYCH0 on 2009-11-04
> 
I can't boot up in 2.6.31-14 without the system crashing ("General error mounting filesystems"). I can boot up in 2.6.28-15. The system starts off with the Jaunty back-and-forth loading window then jumps to the Koala loading window.


I desperately need to know if I can revert back to Jaunty without losing everything, or if I can get Koala to run. I think there's a problem with either fstab or menu.lst but I'm not sure.

Also,
Restore no longer works.
Audio no longer works.
The op did list the problem, along with every attempted solution and the results of said solution.

There are a couple of things that you didn't tell us. First, were you completely updated prior to attempting the upgrade? Second, did you have any issues or get any error messages during upgrade?


For reference, I'd say next time, save all of your error messages in case the info is needed, but just post the commands you attempted.
EDIT----

To the OP, I understand your frustration, but please refrain from attacking someone. You are asking for free tech support. 
@ M4TIC, it seems as though you saw all the outputs and refused to even read any of the post, let's not just tell someone "I'm not gonna help you", posts like that are exactly the reason that people post on other forums about how rude the Ubuntu community is. [/rant]

---

### Post by HiImTye on 2009-11-04
for the record, posting as much info as possible is great. dont get discouraged about posting alot of information, ever.

```
 findfs: unable to resolve 'UUID=31038fcb-b7d2-45e7-80fc-ebf9ee8b3bd2'
```
this UUID isnt listed in your fstab. did you format your device again?

I would try using the live CD and going into GParted (either administration>gparted or administration>partition editor). select the drive (probably sda1). right click on a partition (the very big box on the screen. will display '/dev/sda1/'). select 'information'. there will be a heading 'UUID'. post that.

---

### Post by stderr on 2009-11-04
As HiImTye said, don't worry about posting "too much". There's quite a lot of info there that could conceivably put some people off reading through it, but that's up to them. I personally tend to post the most pertinent debugging output and leave the rest for other posters to request, but there's nothing wrong with sticking it all in.

I'm wondering about

> after changing uuid in fstab to bb28d2a4-9763-4627-97dc-fe98a51b98c4

When did you need to do that, and what was it in response to? Do you know which UUID you overwrote?

---

### Post by SpotTheWonderDog on 2009-11-04
I booted off of a LiveCD and that's where I am now.

GParted says /dev/sdd. When I click 'information' I get /dev/sdd1, filesystem ext3, path /dev/sdd1.

No UUID information.

~```
$ ls -l /dev/disk/by-uuid
```total 0
lrwxrwxrwx 1 root root 10 2009-11-04 15:49 4CD4E2E9D4E2D3EC -> ../../sda7
lrwxrwxrwx 1 root root 10 2009-11-04 15:49 54A4B449A4B42F7C -> ../../sda5
lrwxrwxrwx 1 root root 10 2009-11-04 15:49 80980CBF980CB5A6 -> ../../sda9
lrwxrwxrwx 1 root root 10 2009-11-04 15:49 A86C2B146C2ADD36 -> ../../sda6
lrwxrwxrwx 1 root root 10 2009-11-04 15:49 B4A000F8A000C2BA -> ../../sda8
lrwxrwxrwx 1 root root 10 2009-11-04 15:54 bb28d2a4-9763-4627-97dc-fe98a51b98c4 -> ../../sdd1
lrwxrwxrwx 1 root root 10 2009-11-04 15:49 d31384db-7522-4340-8fa3-819eaa6d758e -> ../../sdd5

sda5 -> sda9 are partitions on another NTFS disk used by Windows and visible by Ubuntu.

I used the bb28d2a4-9763-4627-97dc-fe98a51b98c4  UUID when I noticed that the UUID had changed after using SuperGrub.

No, I didn't format the hard disk.  But one of the solutions suggested SuperGrub since it was simple and easy.  I tried it and it wound up destroying my RAID 0 Windows MBR. I did have a backup for the Windows MBR so not everything was lost. SuperGrub destroyed another hard disk and the UUIDs got scrambled.

Yes, there were a number of warnings and errors during the upgrade process but since the process was already started there wasn't much I could do about it.  I don't know where the upgrade log is so I don't have the exact details.

Yes, I have applied all the updates on a regular basis.

The casual observer will notice that I was thrashing at trying every possible solution that I read in attempting to solve this problem on my own before writing an ignorant 'help me' post.

---

### Post by ST3ALTHPSYCH0 on 2009-11-04
I'd say you did well by searching first.
I understand the frustration of resetting all configurations, but is backing up all needed files and doing a fresh install completely out of question?
I don't want to completely discount repairing your install, but looking at the productivity wasted so far, it seems like that might be the fastest solution to a working system.

BTW, I'm not giving more in depth advice b/c I'm a total n00b.... I see my role as suggesting the simple things that more experienced users have forgotten that they ever struggled with :-D

---

### Post by SpotTheWonderDog on 2009-11-04
> **ST3ALTHPSYCH0 said:**
> I'd say you did well by searching first.
I understand the frustration of resetting all configurations, but is backing up all needed files and doing a fresh install completely out of question?
I don't want to completely discount repairing your install, but looking at the productivity wasted so far, it seems like that might be the fastest solution to a working system.


No, it's not completely out of the question but all too often I've read posts where the solution is 'format and reinstall'.  Many times, I've been able to recover from what seemed like total disasters.  

If I would give up on each project or start all again, I'd never learn anything.

I think that the problem was caused by the extra 3 hard disks in the computer when I upgraded.  I should have (gotta love shoulda/coulda/woulda) unplugged the extra hard disks first.

I believe that there's a solution to this problem and it lies in the fstab and menu.lst files. 

I don't understand why menu.lst is not finding the files for 2.6.31-14 when I can see them in the boot directory (I posted that in my original post).

Can someone please take at look at these files and the UUIDs and see if I've done something particularly stupid?

I would greatly appreciate any assistance you can offer.

Thank you,

---

### Post by honey toast on 2009-11-04
One thing that I have found to be helpful after several failed attempts to upgrade my jaunty to the new karmic v. was to enter systems panel, Admin, Software Sources, and reset your download from que to "download from nearest location". I'm using a laptop and although this config made it possible to download the new v. it took almost 2 hours. :mad:

---

### Post by Zoot7 on 2009-11-04
> **SpotTheWonderDog said:**
> No, it's not completely out of the question but all too often I've read posts where the solution is 'format and reinstall'.  Many times, I've been able to recover from what seemed like total disasters.  

If I would give up on each project or start all again, I'd never learn anything.
That's the spirit!! ;)

> **SpotTheWonderDog said:**
> Can someone please take at look at these files and the UUIDs and see if I've done something particularly stupid?

I would greatly appreciate any assistance you can offer.
I don't see anything glaringly wrong with fstab or menu.lst at a glance. 

TBH I'd recommend a clean install myself but if you wanted to be brazing and to to try your best to fix it; Here's 2 things to try:

Boot into the 2.6.28 that's working for and try to install a new kernel. Maybe try the latest 2.6.31 entry listed here, and see if that gets the system up and running for you. The pre compiled versions are here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Another thing maybe worth trying if the sound issue persists is to upgrade Alsa to the latest version. There's a great upgrade script posted here:
[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

Not sure if that's any use to you, but it's what I'd try. :)

---

### Post by griachae on 2009-11-04
Hey guys):P
 
Well i got a similar Problem: after Uprading from 9.04 to 9.10 it run well the first time but without sound.
I update and upgraded. Then after running 2.6.28-15: 
 
Starting up...
[Firmware Bug]:powerhow-k8:Your BIOS does not provide ACPI_PSS Objects in a way that linux understands. Please report this to the linux ACPI maintainers and complain to your BIOS vendor.
 
The same messages shown again 4 times.
 
 
Maybe it doesnt work because i should boot 2.6.31-14 ? 
Well i dont know and itll be great if somebody knows wht to do to get it run again.
 
thx

---

### Post by Zoot7 on 2009-11-04
> **griachae said:**
> Hey guys):P
 
Well i got a similar Problem: after Uprading from 9.04 to 9.10 it run well the first time but without sound.
I update and upgraded. Then after running 2.6.28-15: 
 
Starting up...
[Firmware Bug]:powerhow-k8:Your BIOS does not provide ACPI_PSS Objects in a way that linux understands. Please report this to the linux ACPI maintainers and complain to your BIOS vendor.
 
The same messages shown again 4 times.
 
 
Maybe it doesnt work because i should boot 2.6.31-14 ? 
Well i dont know and itll be great if somebody knows wht to do to get it run again.
 
thx
Can you re-post your question in your own thread please? Nobody likes to have their thread hi-jacked. :)

---

### Post by griachae on 2009-11-04
Sry but i dont have a thread and dont know how to create one :mad:

---

### Post by ST3ALTHPSYCH0 on 2009-11-04
@ OP
You said that you can get into your install with one of the kernels, correct? 
My advice (as a complete n00b) would be to d/l and burn [this](http://prdownload.berlios.de/supergrub/grub-rescue-cdrom.iso). All this disc does is boot you into a linux install (as long as you did a standard install). This may allow you into your install even if you can't access it otherwise. From there I would advise completely purging grub, rebooting, and reinstalling grub.
This may be flawed advice, so you might want to allow a more experienced user to reply first, but it's very similar to what I did Friday night (ok, very early Sat morning) to repair my system when I sodomized my grub install (yeah, I messed it up THAT badly).
BTW, I have 4 partitions on two HDDs with Windows 7 on one and Ubuntu on the other, and my in place upgrade worked fine.

---

### Post by wildweathel on 2009-11-04
Supergrub?  I think Spot mentioned that he's tried that.  I've never used it, but boy does it look snazzy.  We probably don't need it though.

This actually doesn't sound too bad.  It's especially helpful that you have the old Jaunty kernel (.28-15) and it'll even boot Karmic.  Any system you can boot from its own partitions is a very good sign.  Both restore and audio are kernel-dependent, so the second problem to deal with is that the Karmic kernel (.31-14)  isn't booting.  

The zeroth problem is making sure you back up the data you want to keep.  Things might get worse before they get better, since there's no going back to Jaunty without either a re-install or introducing all kind of fun problems--Debian-based systems don't like to downgrade.

The first problem to fix is the probably less-than-complete upgrade.

So, 
0 - Backup 
1 - make sure that apt is not confused and up-to-date
2 - figure out why kernel .31 isn't booting (unless fixed by 1)
3+ - figure out why sound and resume aren't working (unless fixed by 1 or 2)

I'm going to focus on #1 to start.

Basically, we need to make sure that this computer is pulling from the Karmic repositories and is up-to-date fixing errors along the way.  

So, the first thing to do is boot and look at /etc/apt/sources.list .  The deb lines should refer to "karmic" "karmic-security" "karmic-updates," etc, not "jaunty."  These are the minimum-required lines from mine; the URL will be different unless you download from MIT, too.
```

deb http://ubuntu.media.mit.edu/ubuntu/ karmic restricted main
deb http://ubuntu.media.mit.edu/ubuntu/ karmic-updates main restricted
deb http://ubuntu.media.mit.edu/ubuntu/ karmic-security main restricted

```If you need to recreate this file, the list of mirrors is here: [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

Now, make sure you're connected to the Internet and run "sudo apt-get update".  This will tell your computer what Karmic is supposed to have.

If it complains about missing public keys, the upgrade didn't install the keys necessary to detect tampering on the mirror.  It's fairly safe to ignore this for now--it wont hurt your installation unless someone actually has cracked the mirror.

Now that you have updated package lists, the next thing to do is upgrade the package management tools: 
```
sudo apt-get install apt-get aptitude dpkg
```Those will probably be up-to-date already, since that's the first thing upgrade does.  If apt gives an error because some packages are half-installed or half-configured,
```
sudo dpkg --configure -a
```will try to fix them.

Keep the upgrade from removing your good kernel.
```

sudo aptitude hold linux-image-2.6.28-15-generic

```Once apt-get, aptitude, and dpkg are up-to-date
```

sudo aptitude safe-upgrade
aptitude -s full-upgrade
sudo aptitude full-upgrade

```The first one doesn't remove any packages.  This means it will only make simple changes between the jauntykarmic thing you have so far and Karmic.  The second shows you what packages it will remove to make the full upgrade possible, note that | is the pipe character.

The third actually does remove outdated jaunty stuff.

Hopefully, if there are no errors, that's it.  Reboot and it works.  Hopefully.  

Good luck.

 [COLOR=DimGray]*Based on slakkie's best practices here: [http://ubuntuforums.org/showpost.php?p=8194888&postcount=9](http://ubuntuforums.org/showpost.php?p=8194888&postcount=9) .  Modified to upgrade to Karmic, not Lucid.*[/COLOR]

---

### Post by ST3ALTHPSYCH0 on 2009-11-04
Once again, I only suggested SGD to get him into his install, as a matter of fact that's all that the recovery disc does... I know b/c I used it.

---

### Post by grandtoubab on 2009-11-04
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by wildweathel on 2009-11-04
If he's booting without a CD, grub is working fine, thus no need to worry about it.  Look back to the first post, notice that he's modified the /boot/menu.lst on his harddrive to get it to work.  I might be wrong, and things can always blow up later, but I don't think a rescue CD or messing with grub is called for now.

Sincere thanks for pointing out SGD, though.  I think I'll fire up Virtualbox and try it out.

---

### Post by ST3ALTHPSYCH0 on 2009-11-04
@ WW, The link I pointed to is only an Ubuntu bootloader. SGD 1.22 is based on grub2, but I couldn't find a repair option. SGD 0.9799 (and older) will repair grub (legacy only) or a windows MBR. I happen to have all 3 and have more experience than I'd like with them (gained well after midnight last Friday, well Saturday)

---

### Post by oldfred on 2009-11-04
While a lot of this info will be duplicates of what you posted italso gives what is in the MBR or PBR and how the system is booting.

Boot Info Script 0.32 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions
[http://ubuntuforums.org/showpost.php...71&postcount=3](http://ubuntuforums.org/showpost.php...71&postcount=3)
cd to directory saved to:
chmod 755 boot_info_script032.sh
sudo ./boot_info_script032.sh
or as example if on desktop
sudo bash ~/Desktop/boot_info_script*.sh
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

I generally avoid raid issues as I do not have raid and do not understand the logic used to boot those systems. but the script should help explain what is going on. The script also has data for grub2 but does not seem to correctly identify grub2 in the MBR.

---

### Post by SpotTheWonderDog on 2009-11-05
After 3 solid days, I finally gave up trying to salvage the miserable Koala upgrade and built Jaunty from scratch on a new partition.   I kept the borked up installation just in case I needed something from it.

What I had done before starting the installation was to build a 'home' and 'root' partitions and copy those directories to the new partitions.  Yes, I work almost exclusively from root and that's where I store almost everything so rebuilding the system was far less painful than I expected; 1/2 day.  Firefox came up perfectly with all of my settings and add-ons the first time.   My purchased programming IDE didn't even ask me for my license.

I now have sound and everything works.  I changed the update preferences to Long Term Releases.

Once I know that everything is perfect, I'll clone the hard disk.  This have saved my butt several times in the past.

Not to get off the subject, but I'm a bit confused by how to make a backup of one bootable partition to another. I saw synch, pax and dd.  

Thank you to everyone who responded,

Spot

---

### Post by ST3ALTHPSYCH0 on 2009-11-05
Glad to see that you were about to get things stabilized without any data loss =D>

---

### Post by rglindley on 2009-11-06
I have had very similar problems with boot and sound.  I have only wasted a day so far.  I guess I'll do a fresh install of 9.04 before wasting any more time.  Never will I upgrade again. And I had everything working so well...

---

### Post by ST3ALTHPSYCH0 on 2009-11-07
That's what I've learned from this experience. I learned the hard way with firefox and Windows too.... one would think that I would start applying lessons cross platform.

---

### Post by rglindley on 2009-11-07
Re-partitioned my disk with Live CD saving 9.10 partition and creating a new one, then did fresh install of 9.04 on new partition.  All went well.  Able to copy from 9.10 partition to 9.04 partition and have things pretty much back the way they were.  Only 3 or 4 hours.  Glad I had had plenty of free disk space. I hope I learned a lesson.

---

