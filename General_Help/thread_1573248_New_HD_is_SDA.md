---
title: "New HD is SDA"
date: 2010-09-12
forum: General Help
---

### Post by Mahngiel on 2010-09-12
Greetings,

Been having an issue that I haven't been able to work out yet, hopefully y'all can help.

I bought a new HDD and am not running it in a RAID config.  I backed up everything I wanted to keep and organized it accordingly, then wiped my old HDD.  

Of course, the first OS I put on was Win7 so it wouldn't overwrite GRUB.  Windows gave me a headache at first to install on the old drive, a problem I figured out afterwards - Win wanted to install on the first disk.  Appearantly, my old disk was plugged into the board in the 2nd slot, so my new HDD was SDA.  I got around this initially by unplugging the new storage drive and windows went where I wanted it to.  Fine.

Now I'm having the same problem with my 'nix install.  It seems to want to write the boot sector on the first disk, but windows MBR is on disk 2.  I can't seem to get GRUB to launch as my install is ignored in the boot loader and win loads alone.

Any suggestions without having to reinstall win again?  I've tried moving the SATA cables around, but my win recovery disk won't even recognize a previous install.

---

### Post by Mahngiel on 2010-09-27
bump?

---

### Post by cchhrriiss121212 on 2010-09-27
So, you have win7 entirely on one disk, and Ubuntu entirely on another, is that right?
If so you could just boot between them using your BIOS bootloader. If that is no good then you just need to install grub to your primary disk using a live cd

---

### Post by Mahngiel on 2010-09-29
Sorry for the delay to respond, I've all but given up on this thread.

Let's declare my HDDs as so: OS and Storage

I started by installing win7 first onto the OS hdd.
I then connected Storage to my mobo.  This SATA port I used appears to be the first to be loaded.
When attempting to install Ubuntu Studio onto OS, regardless of what I do w/ gparted, I believe grub is being put into the first sectors of Storage.

However, since the win install MBR is on the OS disk, and grub on the other, Grub is not launching.

---

