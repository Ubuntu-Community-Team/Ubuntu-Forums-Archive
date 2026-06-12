---
title: "Transfering a Linux hard drive to a new computer"
date: 2010-11-16
forum: General Help
---

### Post by crayZsaaron on 2010-11-16
Today, I finished assembling my dream computer.  I can boot it into the BIOS, and I checked that everything was working correctly through there.  Anyway, I attempted to transfer the hard drive from this computer to that one.  This computer is a Dell (blech) Optiplex GX280 with an Intel processor and integrated graphics.  The new one has an AMD Phenom II processor with an ATI card and an ASRock motherboard (drastically different machines, I know...)  When I try to boot, GRUB gives me an error message that says something like:

```
blah whatever cannot find /dev/disk/by-uuid/372de761-9577-48be-ba19-c6b2890cb229
```

Did I do something wrong installing the hard drive?  Or is this a problem that is going to happen no matter how hard I try to make it not happen?  If the second is true, will it help if I wipe the disk and reinstall Ubuntu on the new computer?

Thanks.

-Seth

P.S.  I know similar threads about transferring hard disks have been posted, but no thread has mentioned this error.

---

### Post by amauk on 2010-11-16
With the disk in the new machine, boot to a LiveCD
then run ```
sudo blkid
```

make a note of the UUID for your ubuntu partition

Mount your disk
(it'll be accessable under /media)

then edit /media/<your HDD>/etc/fstab
and replace the old UUID with the one from blkid

Reboot

---

### Post by crayZsaaron on 2010-11-17
I made a ["boot CD" on a USB stick]("http://unetbootin.sourceforge.net/").  I booted up the new computer with that, in "Try it out" or whatever mode.  Actually, that's what I'm in right now.  So, but, Linux has no idea that I have a hard drive.  I can't find it anywhere.  When I start up the computer, the motherboard recognizes the hard drive and gives me the option to boot from it, so I feel like that's most likely not the problem.  Before I booted with the USB stick on this computer, I tested it out on the old computer, with the hard drive connected to that one.  It recognized the hard drive.   What do you recommend as the next course of action?  I think it's really strange that it can't find the hard drive.  Have I connected something incorrectly?  

Also, I believe it's a SATA hard drive (it's a WD800 80 gig hard drive), and the motherboard connection is SATA II... but SATA II is backward compatible, right?  hm.

---

### Post by Ocxic on 2010-11-17
Yes SATA II is backward comatible.

the drive is just not showing up. try "sudo fdisk -l" that will list all drive on the machine, and give partition info.

Also on new Motherboards there are ESATA connectors that are supposed to connect to front panel ports on your case, usually these ports are of a different color then the other normal SATA ports and there are fewer of them, make sure your drive is not plugged into these ports as this could be an issue.

---

### Post by crayZsaaron on 2010-11-17
Well, guess who had their hard drive plugged into the SATA III connection!

Thanks guys, haha.  Everything is working wonderfully.

---

