---
title: "Can't install any Linux distro on Aspire One KAV10"
date: 2011-12-03
forum: General Help
---

### Post by jampe on 2011-12-03
Hi there,

My friend had this little sleek looking netbook (Acer Aspire One KAV10) lying around, he's never actually booted it, because it "wouldn't let him past some Windows recovery tool".

I have now tried installing openSUSE, Linux Mint, KNOPPIX, Ubuntu and Fedora on this frustrating little thing to no avail. They all hang, crash or start ignoring keyboard/trackpad inputs during installation and live sessions. The only OS I've actually gotten to run on it was GParted live in failsafe mode.

The errors are difficult to describe, because they are totally inconsistent. It's something different with each distro. What seems to be a common denominator, however, is that the lock-ups only happen in hardware accelerated video mode and whenever it tries to do anything related to networking. There is no switch to turn off wifi/3G.

Judging from my experience and what information I've gathered so far, this PC really is just a cheap piece of ...., but I want it to run Linux Mint/Ubuntu so badly :D Does anyone here have any experience with these things?

---

### Post by cmcanulty on 2011-12-03
Try booting to a live CD or live USB then from there partiton the internal HD disk to ext4 (it may need to be unmounted first)then reboot to an install CD or USB and try it. However make sure to backup everything first.

---

### Post by jampe on 2011-12-03
I appreciate the reply, but that's the first thing I did. As I mentioned, I was able to start up GParted live in failsafe mode. There is nothing to back up, it's completely empty.

There doesn't seem to be any problem with the integrity of the hard drive, it's something else. I have encountered similar Linux related problems with other PCs of the scrap metal caliber, Toshibas for instance.

I've never had such issues with PCs from Asus, Lenovo, Apple or HP. Some brands just seem completely incompatible, and I'm really curious as to what the reason is.. :P

---

### Post by 2F4U on 2011-12-03
Some of the Acer machines are well know for their crappy BIOS. However, it could also be a problem with the RAM. So, what I would do is to run an extensive memtest from a liveCD and see what it reports.

---

### Post by oldtimer7777 on 2011-12-03
> **2F4U said:**
> Some of the Acer machines are well know for their crappy BIOS. However, it could also be a problem with the RAM. So, what I would do is to run an extensive memtest from a liveCD and see what it reports.

I would reset BIOS from CMOS.  First, see if there are any BIOS updates from the Acer Support Page for that make/model. Perhaps they have already fixed this issue. Let them know what you are trying to do, and ask them why it won't take Linux OS on there...

---

### Post by cmcanulty on 2011-12-03
I assume you made sda1 bootable?

---

### Post by jampe on 2011-12-04
@2F4U: I had that thought and did one early in the process, but got impatient halfway through. Thanks, I'll give that another go.

@oldertimer7777: Sounds reasonable, I'll do that first.

@cmcanulty: Yes, definitely.

I actually managed to install Debian Squeeze on it via the text based interface, and it does boot sometimes. It usually helps taking out the battery and holding the power button for 30 seconds. Sometimes not, though.

Thanks a lot guys, I'll let you know how I get on.

---

### Post by jampe on 2011-12-04
Hm.. Acer's own BIOS update utility bricked the thing, it doesn't even react to pressing the power button now :D I'll have to unsolder the CMOS battery, I guess.

UPDATE:
CMOS battery is unrecognisable. This netbook is now a frisbee.

Lessons learned (sorted by importance):
00 - If something feels out of place, stop immediately and think twice.
01 - When updating BIOS, use Unetbootin and freeDOS instead of the useless stuff the manufacturer provides
02 - Stay the hell away from Acer. They solder things that are not meant to be soldered. Toshiba and Dell do that $h!t too.

No matter, it was my flatmate's PC and he couldn't care less about it.
A lot of time wasted, but lessons learned nonetheless.

---

