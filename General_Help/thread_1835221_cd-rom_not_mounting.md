---
title: "cd-rom not mounting"
date: 2011-08-29
forum: General Help
---

### Post by jika on 2011-08-29
I've read several posts about this exact same issue but not getting far in resolving it.
Some say to use a USBdrive, others say to add parameters to kernel line at boot up.
 
While trying to install Kubuntu (11.4 or 10.04) on my older desktop, I tried the desktop i386 and alternate i386 disks but get either "[initramfs] Unable to find a medium containing a live file system" or "Installation cdrom couldn't be mounted". I also looked for an AHCI setting in the BIOS after reading another post but could not find it on my system.
 
Desktop Specs:
-Elitegroup 761GX-M754 Mainboard
-AMIBIOS 2/14/2006
-AMD Athlon XP-M 3000+ CPU
-512 MB RAM
-On-board graphics
-Two CDrom drives (one master, one slave)
-Two IDE drives (one master, one slave)
 
Hoping to get some pointers....
 
cheers

---

### Post by SiathLinux on 2011-08-29
I have ran into this and it can be a couple of issues:

When you boot and go into BIOS - does it show BOTH of your optical drives (DVD/CD type) AND does it show both of HDD drives - 

If your BIOS doesn't support AHCI - that shouldn't stop you from installing (though anytime you truly shut down you may have to push the power button after the shutdown process finishes...

And of course make sure your using the first logical drive of the CD (ie the one set as Master) for your install disk - I ran into various problems when I used the secondary one before.

You hardware should support Ubuntu 10.x -- though you may find it 'easier' on your system to run 8.04  (which I'm running on a Celeron 866Mhz system currently).

---

### Post by Echnaret on 2011-09-01
I was just finally able to solve the problem of the Ubuntu Server CD not getting mounted. I'm not exactly sure what actually solved it, but I did two things, and at least one of them seemed to fix it. First, I had already removed an extra video card (there was an internal video card I'm currently using, but I saw that I had one PCI card (an audio card) still installed, so I removed it. Second, I pulled out my CD-R and DVD drives and swapped the master/slave jumpers, so the DVD drive was master. In the end, I installed everything from the CD-R drive.

I'm still not sure why it worked. I'm guessing it was most likely a bad PCI card. If all else fails, pull all of them out and see if that helps anything.

---

