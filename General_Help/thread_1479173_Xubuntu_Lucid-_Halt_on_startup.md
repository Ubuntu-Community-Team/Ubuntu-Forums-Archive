---
title: "Xubuntu Lucid- Halt on startup"
date: 2010-05-10
forum: General Help
---

### Post by Ron O on 2010-05-10
A week after a fresh install of Xubuntu Lucid, I get the following error on starting, just before the desktop would normally load up: 

Keys: Continue to wait; or press S to skip mounting or M for manual recovery. 

I am only able to continue by pressing S. A day after first seeing this, I lost the ability to mount usb devices, either through a usb hub or directly to the computer's front panel. I have tried disconnecting all USB devices and rebooting, but the error remains.

This is a dual boot system, and I installed a utility from Synaptic called pysdm to help me mount the other partitions on the hard drive (Windoze and an archive partition) and it worked well as it always did in my prior Xubuntu installations. But I am wondering if this is where my trouble began. I uninstalled pysdm, and the two hard drive partitions continue to mount to media and my desktop via Xubuntu's stock utilities, but the start up error remains and the USB does not mount when I plug in a device.

Recovery mode at startup runs fsck and reports a clean ext3 (the extended partition that includes ext4 for the Xubuntu system and (I presume) ext3 for the swap file with a 1 mb unallocated slice between ext4 and the swap) but it says:

init: init ureadahead- other
Main process (723)
Main process (728)
terminated w/status 4

I ran another utility, Manual recovery from the start screen instead of Skip mounting (I think) and got 

USB 3-1 new low speed USB device using uhc1_hdc address xxxxx
USB 3-2 new low speed USB device using uhc1_hdc address xxxxx

Maybe I am giving too much info and making this more complicated than it should be, but my questions are:

1. Is this recoverable and how?

2. Is the file structure that the installer created correct? (the extended partition that includes ext4 for the system and I presume ext3 for the swap file with a 1 mb unallocated slice between ext4 and the swap).

3. Is this reportable as a bug, since the start up error remains, even when all USB devices are unplugged before booting?

---

