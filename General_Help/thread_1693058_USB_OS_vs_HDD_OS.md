---
title: "USB OS vs HDD OS"
date: 2011-02-22
forum: General Help
---

### Post by nhtrader on 2011-02-22
Since ubuntu and all of its flavors are so compact, I was wondering about using a 8Gb USB flash drive to store and boot the OS while using the HDD for the /home DIR.

Does anyone know what the performance hit will be when the OS resides on the USB stick? (will the system be slower or faster?)

Second, does anyone have any tips on how to do this?

---

### Post by ellgor on 2011-02-22
Hi,

I have the exact set-uo you describe ( puppy-linux as the OS), the only difference I've encountered is the fact that the transfer rate of a USB compared to a regular Hdd is way down, leading to a slight delay when loading apps or saving to the USB, the way puppy works is to use ram to operate in which makes it very fast, of course there is the slight delay while the OS finds the app and shoves it into ram,if you live with that then go ahead and try it.(Ignore my stats, outdated).

Regards, Ellgor.

---

### Post by oldfred on 2011-02-22
USB flash drive is slower than a hard drive, both because of flash drives being slower (especially writes) and USB ports being slower. It can still be functional depending on your expectations.

I prefer to have reliability of one system one drive. Or if another drive fails, this drive will boot. So MBR, and all system required files should be on one drive. (and a corollary - every drive is bootable).  Or in your case keep /home on the flash drive, but create a /data drive so most data you would store in /home is really in /data. Only user settings would be in /home in the mostly hidden files & folders.

System would be faster with entire system installed on USB hard drive, but still not as fast as IDE or SATA internal drive.

It does not have to be encrypted:
Standard full install to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.

Full install to flash drive is more like any install to a second drive with a few settings to reduce writes to improve speed (see above).


Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

I have a full install to a 8GB partition on a 16GB flash drive and it works ok. I made the rest of the 8GB a data partition to have some room for backup data.

---

### Post by snowpine on 2011-02-22
I have Linux (CrunchBang Linux, based on Debian Squeeze) installed to an 8gb thumb drive on an old laptop that has no internal HDD (it broke). It runs fine. Performance is slower than a regular HDD, so I'm not sure why you would do this if you have a functional internal HDD.

There are two different types of USB installs: persistent live USB install and full install. Mine is a full install, meaning I simply installed to the flash drive as you would install to a regular hard drive. Be careful however if you have more than one drive, you want to make sure not only do you install to the correct drive/partition but also that the GRUB bootloader is installed to the correct drive. The simplest way to avoid a mixup is to disconnect all drives except the one you're installing to.

---

### Post by 3Miro on 2011-02-22
USB should be used for mobility and testing purposes. The main OS that you will be using should reside on the HDD.

---

### Post by nhtrader on 2011-02-23
Thanks to all. It's rare to see such consistency. So I guess I won't be using a USB stick except for testing purposes.

BTW, it seemed to me to be such a waste of space to use a HDD for the OS when I separate the OS from /home. The OS only takes a few Gbs (I'll be generous and say 20Gb) and rest of the HDD would be unused b/c the /home would reside on another HDD. 


But since you all agree, USB sticks are slower. I'll just waste some space.

---

### Post by ellgor on 2011-02-23
Hi again,

You are quite right about the OS not taking up a lot of space (Puppy is on its own partion at 130Mbs) which leaves almost 7.9Gb, if you have enough ram, Puppy can load itself and any other app you might want to use into ram and be as quick as anything out there, also there is the option of putting any extras (more apps, changes you make, etc.,) on to the hard-drive, these get called as and when necessary, worth taking a look at if not the OS then the thinking behind it.

Regards, Ellgor.

---

### Post by Tu1J4kXk8NUhMz on 2011-02-23
Please someone correct me if I'm wrong here, but a USB thumb drive benefits from having solid state memory. However, you still need to access the info using USB, which is certainly slower than any standard HDD interface.

As far as doing it, I've just learned about LiLi ([www.linuxliveusb.com/]("www.linuxliveusb.com/")), though I have very little experience with it. Looks user friendly and quite simple to use. You can also use unetbootin ([http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")).

From my understanding, you can use either of the pieces of software to create a "frugal install" of the OS, allowing (what I can only assume is) a persistent Live installation on your local hard drive (though a USB HDD could probably be used too).

---

