---
title: "USB device automounting succeeds only if sd_mod module is not already loaded"
date: 2006-06-14
forum: General Help
---

### Post by julioromano on 2006-06-14
Hi guys, I started working on this since my new USB flash drive wasn't automounted on my desktop pc (OS: ubuntu dapper fresh install).
I tried on my laptop (OS: ubuntu dapper fresh install) and it was automounted correctly only for the first time. Then if I disconnect and reconnect it: no more automount.

Doing some debugging I found that the /dev/sd* device was created correctly, all is ok, I can still mount the USB stick manually or with pmount. It is only a problem related to automounting.

Well I discovered something interesting:
Automount succeeds only if the "sd_mod" kernel module is not already loaded when plugging in the USB device.

My laptop has no scsi devices so the sd_mod module is not loaded on startup.
When I first connect the USBstick the sd_mod module is not loaded and so is loaded automatically and the stick gets automounted.
Second time: the module is already loaded and so automount doesn't happen.
If I do "rmmod sg & rmmod sd_mod" as root user (module "sg" must be removed first as it depends on sd_mod) and then plug in the USB stick, automount works again.

On the desktop PC there is a SATA harddrive which is seen as scsi device, so the sd_mod module is loaded automatically on startup and I can't remove it because the OS is on the SATA drive. there is no chance here, I can't do the same trick.

I did get the same results when booting with the Ubuntu or Kubuntu dapper LiveCD so it is a problem related to a component present in bot ubuntu and kubuntu.

Please let me know your thinkings about.

---

### Post by scxtt on 2006-06-14
i have 2 SATA drives in my box and when i insert a USB flash drive it shows up on my desktop (i then right-click and unmount [or eject, it might say] it) and i can put it in again w/ no issue like you're having ... what method are you using?

---

### Post by julioromano on 2006-06-15
The problem exists olny with certain USB drives,
I Have a "128MB Usb DriveTM" and a "1GB Lexar JumpDrive" and they get automounted OK.
I recently purchased a "2GB PQI U339S" and it shows the problem I wrote about (in MacOS X and WinXP it works perfectly).
I read around in the forums and also other people have the same problem (first mount ok, second mount not ok) with some USB flash drives and also with some USB external harddisks.

---

