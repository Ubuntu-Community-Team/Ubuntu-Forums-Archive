---
title: "/boot is full"
date: 2012-05-24
forum: General Help
---

### Post by Belrick on 2012-05-24
Hi
 
My linux server has been running happily for years now, really happy with even though all i really know is windows.
 
Anyway i hit a series of cascading issues that i cannot resolve, please help me!
 
At the root of the problem is that my /boot used on install is full. Its only set to 50meg but in all honesty i still dont know why its used for anything furthur.
 
Series of commands ive run
 
 
**> uname -r**
2.6.24-28-server
 
**> df**
/dev/sda1 46633 41881 2344 95% /boot
 
**> sudo dpkg --configure -a**
Setting up initramfs-tools (0.85eubuntu39.3) ...
update-initramfs: deferring update (trigger activated)
 
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-28-server
 
gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-28-server
dpkg: subprocess post-installation script returned error exit status 1
 
 
Last one is a biggy, in order to be able to do anything auto i figure i need to use dpkg but i cant run dpkg till i fix the boot full issue.
 
Can someone please help me?
 
In all honesty all i wanted to do was to install PHP PEAR. Sigh.

---

### Post by drs305 on 2012-05-24
The days of 50MB /boot partitions are over. Grub now puts a lot of modules in /boot/grub and other things take up space. It still doesn't have to be huge, but 50MB gets full these days.

Do you have more than one kernel? You probably do if you've been running this OS for years.  If so, you can remove older kernel(s) and their initrd.img-<version> via the terminal (sudo rm /boot/vmlinuz-<some kernel version>, etc. Just make sure you don't remove ...-2.6.24-28-server or whatever your current kernel is, and be very careful with the 'sudo rm' command!

That might free up enough space until you can grow your /boot partition or take other measures.

---

### Post by Belrick on 2012-05-24
Thankyou for your quick reply
 
**> ls /boot**
abi-2.6.24-23-server
abi-2.6.24-28-server
config-2.6.24-23-server
config-2.6.24-28-server
grub
initrd.img-2.6.24-23-server
initrd.img-2.6.24-23-server.bak
initrd.img-2.6.24-28-server
initrd.img-2.6.24-28-server.bak
lost+found
memtest86+.bin
System.map-2.6.24-23-server
System.map-2.6.24-28-server
vmlinuz-2.6.24-28-server

 
Anything else i can safely delete?
 
 
I suppose in order to increase /boot size i would be looking at a fresh install? COnsidering how much of a mission it was for me to setup the raid partitions i shy away from that idea!

---

### Post by drs305 on 2012-05-24
> **Belrick said:**
> Thankyou for your quick reply

Anything else i can safely delete?
 
 
I suppose in order to increase /boot size i would be looking at a fresh install? COnsidering how much of a mission it was for me to setup the raid partitions i shy away from that idea!

Assuming you are using -28 you could remove all the -23 files as long as you are comfortable not having a backup kernel available. Don't delete the grub folder but you could go into it and delete some of the *.mod files (grub modules) that you know you don't need (don't ask me which ones though).  I am not familiar enough to know if any of the -28 items could be safely removed.

If resizing the /boot partition isn't convenient or possible, you'll just have to keep up with an occasional cleaning when a new kernel is introduced.

It might be possible to symlink some of the files you currently have in /boot to save a bit of space, but again that's an area I don't have enough experience with to give specifics.

---

