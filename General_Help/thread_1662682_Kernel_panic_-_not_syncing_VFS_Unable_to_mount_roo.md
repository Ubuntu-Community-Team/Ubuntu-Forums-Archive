---
title: "Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)"
date: 2011-01-08
forum: General Help
---

### Post by isaac_moller on 2011-01-08
Hello, 

I have an HP Slimline s5310y with an AMD processor. My Ubuntu distro is 10.04 x64, and I use dual boot with Windows 7 using BURG.

I was installing the latest rounds of updates while creating a live disc using remastersys (I know I know, bad). After I was done using this program my update manager asked me to reboot so I did. Now every time I reboot Grub kicks in like normal, makes its default selection as normal, and now I get this error: 

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

So I have to hard shut down the unit, and when I try to reboot using "recovery mode" through my Grub I get this error: (where xxxxx represents numbers that I got too tired to write)

[ 0.881860] md: Waiting for all devices to be available before autodetect
[ 0.881924] md: If you don't use raid, use raid=noautodetect
[ 0.882081] md: Autodetecting RAID arrays.
[ xxxxxxxx] md: Scanned 0 and added 0 devices.
[ xxxxxxxx] md: autorun ...
[ xxxxxxxx] md: .... autorun DONE.
[ xxxxxxxx] RAMDISK: gzip image found at block 0
[ xxxxxxxx] usb 1-9: new high speed USB device sing ehci_hcd and address 4
[ xxxxxxxx] usb 1-9: configuration #1 chosen from 1 choice
[ xxxxxxxx] List of all partitions:
[ xxxxxxxx] No filesystem could mount root, tried: ext3 ext2 ext3 fuseblk
[ xxxxxxxx] Kernel panic - not syncing: VFS: Unable to mount root fs on unkown-block(0,0)
[ xxxxxxxx] Pid: 1, comm: swapper Not tainted 2.6.32-26-generic #48-Ubuntu
[ xxxxxxxx] Call Trace:
<<bunch of numbers>> <<letter and numbers>> panic+0x78/137
<<bunch of numbers>> <<letter and numbers>> mount_bloc_root
<<bunch of numbers>> <<letter and numbers>> handle_initrd
<<bunch of numbers>> <<letter and numbers>> initrd_load
<<bunch of numbers>> <<letter and numbers>> prepare_namespace
<<bunch of numbers>> <<letter and numbers>> kernel_init
<<bunch of numbers>> <<letter and numbers>> child_rip
<<bunch of numbers>> <<letter and numbers>> ? kernel _init
<<bunch of numbers>> <<letter and numbers>> ? child_rip

I looked to see if GRUB was actually pointing to the right partition, so this is what GRUB says when pressing the 'e' key.

insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 8a49f5a3-9c16-40ac-ac079-f3681ddd655f
echo 'Loading Linux 2.6.32-26-generic ...'
linux /boot/vmlinuz-2.6.32-26-generic root=UUID=8a49f5a3-9c16-40ac-a079-f3681d
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.32-26-generic

I booted using my Ubuntu live Cd, and I made sure that my Linux partition is actually on (hd0,5) and it is.

So I think Grub is ok?
I am able to access my Windows 7 partition using Grub (BURG) like always, my unit passed memtest and all the hardware seems to be in good shape.

Is there any way to fix my Kernel without having to completely reinstall my Ubuntu partition? I've spend my whole evening yesterday and this morning looking for a solution, but I can't find anything :(

HALP!?
:)

---

### Post by isaac_moller on 2011-01-12
No one?

---

### Post by isaac_moller on 2011-01-19
K fine!

I was able to fix this problem by reinstalling GRUB2 using CHROOT (method 3)

Instructions are here [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

for more information on this issue visit this post:
Question #141254 in launchpad.net

[https://answers.launchpad.net/ubuntu/+source/linux/+question/141254](https://answers.launchpad.net/ubuntu/+source/linux/+question/141254)

---

