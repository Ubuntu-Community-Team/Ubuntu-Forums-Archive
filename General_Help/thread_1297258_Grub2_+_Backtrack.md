---
title: "Grub2 + Backtrack"
date: 2009-10-21
forum: General Help
---

### Post by Sarmacid on 2009-10-21
In the last weeks I've been working on making a bootable usb stick with some linux distros on it, and it hasn't been a complete success. As of now, I can boot ubuntu 9.04, linux mint, tinycore and memtest, but I have been struggling with Backtrack 4. I have tried booting it using the following menu entries

```
menuentry "BackTrack iso" {
 loopback loop /boot/isos/bt4-pre-final.iso
 linux (loop)/boot/vmlinuz find_iso/filename=/boot/isos/bt4-pre-final.iso BOOT=casper boot=casper nopersistent rw vga=0x317 --
 initrd (loop)/boot/initrd.gz
}
``` This is trying to boot from the iso.

```
menuentry "BackTrack 4 Pre Release" {
    linux /boot/isos/bt4/boot/vmlinuz BOOT=casper boot=casper nopersistent rw vga=0x317 --
    initrd /boot/isos/bt4/boot/initrd.gz
}
``` This is trying to boot not from the iso file, but from the folder where I extracted the files from the iso to.

Both approaches leave me to the initramfs prompt as you can see in the screenshot, and although the screenshot is from a virtual machine, the same happens when I try to boot a pc with it. I've searched to no avail and nothing seems to work, could someone help me with this?

---

### Post by dbzkid on 2010-03-17
I am having the same issue, It willnot go any farther than busybox

---

### Post by 2hot6ft2 on 2010-03-17
> **dbzkid said:**
> I am having the same issue, It willnot go any farther than busybox
The original post was over 4 months ago and I have to wonder if you're actually trying to do the same thing as the OP. Or are you just trying to make a bootable usb install?

---

### Post by Sarmacid on 2010-03-17
I wasn't trying to install backtrack on the USB, I was trying to get the iso to boot like a live CD.

---

### Post by bond711 on 2010-05-05
I'm also having trouble getting bt4 to boot, I don't think its a loopback error, because even after extracting the ISO it still won't boot properly,

here are my grub2 entries for bt4

```
menuentry "BackTrack4 ISO" {
	set isofile="/boot/bt4-final.iso"
	loopback loop $isofile
	linux (loop)/boot/vmlinuz find_iso/filename=$isofile BOOT=casper boot=casper nopersistent rw vga=0x317 --
	initrd (loop)/boot/initrd.gz
}

menuentry "BackTrack FrameBuffer (1024x768)" {
	set root=(hd0,1)
	linux /boot/bt4/boot/vmlinuz BOOT=casper boot=casper nopersistent rw vga=0x317 --
	initrd /boot/bt4/boot/initrd.gz
}

menuentry "BackTrack FrameBuffer (800x600)" {
	linux /boot/bt4/boot/vmlinuz BOOT=casper boot=casper nopersistent rw vga=0x314 --
	initrd /boot/bt4/boot/initrd800.gz
}

menuentry "BackTrack Forensics (no swap)" {
	linux /boot/bt4/boot/vmlinuz BOOT=casper boot=casper nopersistent rw vga=0x317 --
	initrd /boot/bt4/boot/initrdfr.gz
}

menuentry "BackTrack in Safe Graphical Mode" {
	linux /boot/bt4/boot/vmlinuz BOOT=casper boot=casper xforcevesa rw --
	initrd /boot/bt4/boot/initrd.gz
}

menuentry "BackTrack Persistent Live CD" {
	linux /boot/bt4/boot/vmlinuz BOOT=casper boot=casper persistent rw --
	initrd /boot/bt4/boot/initrd.gz
}

menuentry "BackTrack in Text Mode" {
	linux /boot/bt4/boot/vmlinuz BOOT=casper boot=casper nopersistent textonly rw --
	initrd /boot/bt4/boot/initrd.gz
}

menuentry "BackTrack Graphical Mode from RAM" {
	linux /boot/bt4/boot/vmlinuz BOOT=casper boot=casper toram nopersistent rw --
	initrd /boot/bt4/boot/initrd.gz
}

```

---

### Post by davidpryke on 2010-06-14
According to post #22 in this thread: [**HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2**]("http://ubuntuforums.org/showthread.php?t=1288604&page=3"), "...bear in mind that for Bactrack to work the files must be extracted from  the iso and the casper folder must be at the root of the device."

Additionally, someone mentioned later in the thread that you could modify the init script that is in initrd.gz for BackTrack4, but that it is a bit involved.  You can check out how to do that over on GParted Forum: [enhancement in initrd image]("http://gparted-forum.surf4.info/viewtopic.php?id=13623") 

The first option is by far easier, and although not ideal, may be the best solution for many cases.

---

