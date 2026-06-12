---
title: "usb multiboot"
date: 2009-08-31
forum: General Help
---

### Post by yoma819 on 2009-08-31
Hello all
i am trying to create a multi boot usb stick and need a bit of help!
using unetbootin i have installed the first iso (backtrack 4 prerelease) to my usb stick
i have read in many threads that the next thing i have to do is move all the boot files etc into a single folder and modify syslinux.cfg
then i have to make additions to the syslinux.cfg after i have extracted all the other isos
my syslinux.cf file is:

default vesamenu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit BOOT=casper boot=casper nopersistent rw quiet vga=0x317

label ubnentry0
menu label Start BackTrack FrameBuffer (1024x768)
kernel /boot/vmlinuz
append initrd=/boot/initrd.gz BOOT=casper boot=casper nopersistent rw quiet vga=0x317

label ubnentry1
menu label Start BackTrack FrameBuffer (800x600)
kernel /boot/vmlinuz
append initrd=/boot/initrd800.gz BOOT=casper boot=casper nopersistent rw quiet vga=0x314

label ubnentry2
menu label Start BackTrack Forensics (no swap)
kernel /boot/vmlinuz
append initrd=/boot/initrdfr.gz BOOT=casper boot=casper nopersistent rw vga=0x317

label ubnentry3
menu label Start BackTrack in Safe Graphical Mode
kernel /boot/vmlinuz
append initrd=/boot/initrd.gz BOOT=casper boot=casper xforcevesa rw quiet

label ubnentry4
menu label Start Persistent Live CD
kernel /boot/vmlinuz
append initrd=/boot/initrd.gz BOOT=casper boot=casper persistent rw quiet

label ubnentry5
menu label Start BackTrack in Text Mode
kernel /boot/vmlinuz
append initrd=/boot/initrd.gz BOOT=casper boot=casper nopersistent textonly rw quiet

label ubnentry6
menu label Start BackTrack Graphical Mode from RAM
kernel /boot/vmlinuz
append initrd=/boot/initrd.gz BOOT=casper boot=casper toram nopersistent rw quiet

label ubnentry7
menu label Memory Test
kernel /ubnkern
append initrd=/ubninit 

label ubnentry8
menu label Boot the First Hard Disk
kernel /ubnkern
append initrd=/ubninit 


i am trying to add:
ubuntu 9.04, vista home, hirens boot cd, quick tech pro and erd commander.
how do i go about adding these lines into the syslinux.cfg file?
cheers
yoma

---

### Post by yoma819 on 2009-08-31
bump

---

### Post by Mighty_Joe on 2009-09-01
I haven't had any luck with making a multi-boot USB drive, but [this guy]("http://ubuntuforums.org/showthread.php?t=1226410&highlight=isolinux") claims success.  Perhaps you can use his technique?

---

