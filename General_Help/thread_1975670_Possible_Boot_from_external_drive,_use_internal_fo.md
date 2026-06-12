---
title: "Possible? Boot from external drive, use internal for data only (encrypted)"
date: 2012-05-07
forum: General Help
---

### Post by ufugu on 2012-05-07
Back story: Yesterday I did a fresh install of Xubuntu 12.04 to an external SSD (my plan is to use it for audio production with the KXStudio repos and not mess up my main install with audio tweaks as I have in the past).

Result: This set-up was BLAZINGLY fast to boot and was very snappy and responsive. Pure awesome.

What I want to do: I has thinking of doing it for my main setup too.  Install 12.04 to an external disk, and have the internal disk on my laptop have no OS whatsoever, only data storage, and ideally encrypted and not tied to a particular user account (maybe just as a Truecrypt voloume or something that behaves similarly).  

Is this possible?  If so, what's a good way to accomplish this? Do I run into trouble if there is no GRUB or MBR on the internal disk?

I tried searching here and Google, but couldn't find exactly what I was looking for because the terms are so generic.  Thanks!

---

### Post by oldfred on 2012-05-07
Normally everyone wants the internal to be bootable. But many install a full install of Ubuntu to an external drive and only boot Windows when the external is not connected. 

I do not know about the encryption, but without external plugged in, you internal drive will not work. You may have to erase MBR which is unusual or MBR will try to boot and if you have no operating system just give an error.

This is to encrypt the external install, install process is hardly different for newer versions:

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

An install to a external drive is no different than any install to a second drive. With an SSD you may want to make changes to reduce writes.

Does USB port slow SSD, USB ports are not as fast as SATA ports.

---

### Post by ufugu on 2012-05-08
> **oldfred said:**
>  

I do not know about the encryption, but without external plugged in, you internal drive will not work. You may have to erase MBR which is unusual or MBR will try to boot and if you have no operating system just give an error.

Thanks oldfred!

Yes, this is what I want. The computer would not boot off the internal drive.  Only the external drive would boot. The internal drive would hold encrypted data, no OS.  I have no Windows on my computer nor a desire for it (wiping it is the first thing I do on a new machine).

I guess the short version of my question is: if I wipe my internal drive 100%, can I still boot up with the external drive?

(FYI, I had no problems installing the system to an external drive.  That part I have.  Also, I didn't mention because I didn't think it was relevant, but my external SSD is booting via eSATA (not USB) and that is why it's so fast.  Boots Xubuntu in under 10 seconds.  My internal drive takes over a minute.)

---

### Post by oldfred on 2012-05-08
As long as system will boot from external it should work. Windows may not as it only works from whatever BIOS reports as internal drives, but if BIOS lets you boot from external, just set it first in boot order in BIOS. 

I think some have used Ubuntu when internal hard drive failed, but that can still be system dependent.

---

