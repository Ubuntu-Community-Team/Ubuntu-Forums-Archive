---
title: "Ubuntu 10.04 - Live CD extremely slow"
date: 2010-06-12
forum: General Help
---

### Post by dim3000 on 2010-06-12
Hello everyone,

Have a little problem/annoyance. I was trying to use a Live CD with Lucid Lynx 10.04 x86 edition and the speed was incredibly slow. I took more than 10 minutes just to start. I noticed the CD drive stopped spinning (or spinning so slow I couldn't hear it) at times, then starting up again. I also noticed multiple i/o error in the logs after it finally booted up.

The reason why I think this is a bug and not my drive/cd is simple:

a) The MD5ed the iso and even made two CDs with different burners.
b) I tried older Ubuntu as well as several other Linux distros and the Live CD boot time is much faster (1-2 min).
c) Tried the CD on a way, way older ancient laptop and i booted just fine and much faster.

Any ideas?

(I will provide any other info if needed).

---

### Post by jnorthr on 2010-06-12
it happened to me several years ago. the burn speed was too fast so the resulting live Cd was faulty. If you can re-burn at a slower speed and then do a md5 checksum on it just to confirm it's been burned ok, you might have more success.:)

---

### Post by jnorthr on 2010-06-12
BTW - what type of video graphics card do you have ?

---

### Post by dim3000 on 2010-06-12
EDITED my post with another key piece,

I tried the CD on a way, way older ancient laptop and i booted just fine and much faster.

---

### Post by dim3000 on 2010-06-12
> **jnorthr said:**
> BTW - what type of video graphics card do you have ?

nVidia Graphics

---

### Post by jnorthr on 2010-06-12
just looking at another problem for someone else and came across this:
[http://ubuntuforums.org/showthread.php?t=1488705](http://ubuntuforums.org/showthread.php?t=1488705)

seems like your video card may not play nicely with 10.04. looking to see if there is a work-around for this. i'm sure there is a boot option you can set at boot time to do a safe start, which may/maynot work-around your video issue. but do't have a ubuntu system close-by. can you ck this possibility ? ta

---

### Post by jnorthr on 2010-06-12
and this one:
[http://ubuntuforums.org/showthread.php?t=1491430](http://ubuntuforums.org/showthread.php?t=1491430)

nomodeset sounds like what you might try at bootup

---

### Post by dim3000 on 2010-06-12
Tried nomodeset, same thing happens.

BTW, my actual card is an nVidia 6150


EDIT: even xforcevesa fails.

(Output still shows Buffer I/O for sr0)

---

### Post by RJ12 on 2010-06-12
I know this happened to me once because every operating system I tried thought there was a floppy disk drive in the computer and there actually wasn't. I bet that there was a BIOS setting that I accidentally messed with. See if there are any devices that you have plugged in also that you don't need. sr0 is the device name for (quoted from another post in Ubuntu Forums) " /dev/sr0 normally refers to the "first" SCSI/Firewire optical drive (eg a DVD writer, Blu-ray drive, etc.)". Do you have any firewire drives / devices other than the drive you are using, try unplugging them (Webcam?).

---

### Post by dim3000 on 2010-06-13
Tried disabling different things in BIOS, same result. I'll try to upload a picture with the exact errors.

---

### Post by jnorthr on 2010-06-13
yes, please

---

### Post by dim3000 on 2010-06-13
I am sorry for not having my proper camera around and instead had to use an old webcam. Basically with nosplash the Buffer I/O error on sr0 or whatever gets prints every few seconds until it decides to stop and continues booting.

---

### Post by dim3000 on 2010-06-13
Here is a dmesg.log after finally booting:

[http://paste.ubuntu.com/449428/](http://paste.ubuntu.com/449428/)

As you can see all the sr0 errors.

---

### Post by dim3000 on 2010-06-13
Also, here's kern.log:

[http://paste.ubuntu.com/449430/](http://paste.ubuntu.com/449430/)

---

### Post by dim3000 on 2010-06-14
JJust tried a Fedora 13 cd, exact same issue

---

