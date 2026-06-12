---
title: "Unable to mount media drive"
date: 2009-09-28
forum: General Help
---

### Post by Riyazd on 2009-09-28
Hi need some help urgently. I've just installed Jaunty 9.04 and now want to connect my HTC Hero.  The drive appears as mass storage but I keep getting an error.  I've been checking the forum but can't find a clear cut answer...any suggestions?

---

### Post by grturner on 2009-09-28
exactly what the error is would be helpful.

---

### Post by Riyazd on 2009-09-28
whoops!

unable to mount location - no media drive no media in the drive

---

### Post by blur xc on 2009-09-28
> **Riyazd said:**
> whoops!

unable to mount location - no media drive no media in the drive

Simple Q here- Do you have a micro sd card inserted in the slot on the phone?

BM

---

### Post by Riyazd on 2009-09-28
yes

---

### Post by blur xc on 2009-09-28
> **Riyazd said:**
> yes

Have you done a sudo fdisk -l with it connected to the computer?

BM

---

### Post by Riyazd on 2009-09-28
this is what I got? is this correct?


Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9324    74894998+  83  Linux
/dev/sda2            9325        9726     3229065    5  Extended
/dev/sda5            9325        9726     3229033+  82  Linux swap / Solaris
riyazd@riyazd-desktop:~$

---

### Post by blur xc on 2009-09-28
> **Riyazd said:**
> this is what I got? is this correct?


Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9324    74894998+  83  Linux
/dev/sda2            9325        9726     3229065    5  Extended
/dev/sda5            9325        9726     3229033+  82  Linux swap / Solaris
riyazd@riyazd-desktop:~$

Well- I think that confirms that your computer isn't seeing the drive...  hmm...  There's nothing wrong w/ the connection to the computer? USB port is ok, cable, memory card works?  What about the phone- does the owner's manual say anything special about connecting the device to the computer?  I know w/ some digital cameras, there's a setting somewhere in the menu system to make them act like a mass storage device- makes connecting and downlaoding pics work better- or work at all if they are not.

After that- I guess I'm out of ideas...

Try a memory card reader?  I use a usb card reader for my phone's micro sd card, and it works super.  I find that easier than digging out some cable (that I can never find) from the junk drawer.

BM

---

### Post by Riyazd on 2009-09-29
tried a memory card reader, no joy.  In actual fact, it doesn't even read a standard memory stick, same error msg.  However, it reads my BB as mass storage and external media drive.....anyone else?

---

### Post by rboss on 2009-10-07
Hello there!

It seems I've got the same problem; here is the output of dmesg:

[  502.781818] sd 6:0:0:0: [sdc] Device not ready
[  502.781823] sd 6:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  502.781830] sd 6:0:0:0: [sdc] Sense Key : Not Ready [current] 
[  502.781837] sd 6:0:0:0: [sdc] Add. Sense: Medium not present
[  502.781846] end_request: I/O error, dev sdc, sector 0
[  502.781863]  unable to read partition table

So far no luck.

---

### Post by rboss on 2009-10-07
Might be a problem with Android phones in general:


[http://forum.xda-developers.com/showthread.php?t=467998](http://forum.xda-developers.com/showthread.php?t=467998)

No look so far.

---

### Post by lusephur on 2009-10-11
hmmmm, that is unusual.
have the htc hero myself, and it mounts fine in karmic.
simple question though,, have you pulled down the usb menu when you connect and select usb connected? it will then ask if you want to mount.

for more info, i'm running karmic beta
the phone is rooted, and running the 2.6.27-0078c992 htc-kernel@and18-2 #851

---

