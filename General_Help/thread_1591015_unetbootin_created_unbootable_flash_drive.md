---
title: "unetbootin created unbootable flash drive"
date: 2010-10-08
forum: General Help
---

### Post by Dustin2128 on 2010-10-08
I tried to install SliTaz to my flash drive to save a DVD. When I booted into it, it gave me a unetbootin custom boot screen with a 10 second count down to boot to default- the only option. I hit enter, it resets to 10 seconds, I wait 10 seconds and it still resets to 10 seconds. Any ideas?

---

### Post by Dustin2128 on 2010-10-08
bump

---

### Post by wilee-nilee on 2010-10-08
Have you tried just downloading the ISO and then installing or just the link from unetbootin.
http://www.slitaz.org/en/get/#stable>

---

### Post by Dustin2128 on 2010-10-09
yeah, still doesn't work.

---

### Post by lbrty on 2010-10-09
I am assuming you downloaded SliTaz GNU/Linux 3.0 (30 MB)? In the past, I have had the same issue (not with SliTaz) with a distro not booting properly. The issue was that the .iso file did not fully download and therefore was incomplete. Have you checked the size to make sure that it was completely downloaded?

[http://slitaz.org/en/get/index.html#stable](http://slitaz.org/en/get/index.html#stable)

---

### Post by Dustin2128 on 2010-10-09
I've checked; the file is uncorrupted. I've tried it with both stable and cooking. Wondering if its a unetbootin problem.

---

### Post by lbrty on 2010-10-09
Do you happen to have a blank CD-RW? If so, try burning the .iso to that medium.

---

### Post by Dustin2128 on 2010-10-09
> **lbrty said:**
> Do you happen to have a blank CD-RW? If so, try burning the .iso to that medium.
unfortunatley I don't, and I'd prefer not to totally waste a 4.7 gb dvd-r for a 30 mb iso.

---

### Post by lbrty on 2010-10-09
Try reformatting the USB flash drive and select FAT (I presume it already is FAT, but just in case it is not). 

Either way, I would try a clean format, safely eject the USB flash drive, reinsert the USB flash drive, and start UNetbootin. Once you have finished creating a bootable USB flash drive with SliTaz, right click the USB flash drive and click safely remove and try booting from it again.

---

### Post by Stafke on 2010-11-05
Well, I don't want to discourage you, but I have the same issue over and over again.

Both usb startup disk creator and unetbootin have disappointed me. If I make a bootable usb, everything works fine.

However (and here comes the problem), when I want to "burn" another distro on it, I am unable to make my usb bootable.

I have a netbook, so burning a CD/DVD is no option. Furthermore, the main advantage of using usb should be to be able to use the same usb-drive over and over again and not wasting any cd/dvd when trying new distro's through live versions. If I need to waste usb disks over and over again, that's not what I call a suitable alternative.

And yes, the files are ok. If I burn the same file on another usb pen, they work, so it probably has something to do with usb-startup-disk-creator or unetbootin, or the partitions on my usb, but gparted doesn't allow me to make a partition table :s

This has bothered me several times by now. I am certainly not a Linux expert, so there is probably a solution, but I'm getting frustrated by the "Linux = choice" idea when I need to waste usb-pens for it.

Edit: and I am not trying to burn another distro next to it, but just formatting and try a new one

---

### Post by Stafke on 2010-11-06
In the mean time, I got my usb working. Unfortunately, I had to use the program LiLi (Linux Live), which is a Win program. Kind of ironic that I have to use a Win program to get my live linux distro.

I wanted to have crunchbang statler, which is not recognised by the program. When trying to burn it, I used the previous crunchbang as an example. As Statler is Debian based and the other is ubuntu-based, this didn't work. Simple solution was to put "debian" at the start of the iso file name. The program then indicated that it didn't know the distro either, but was using debian 5 as reference, which worked alright.

I hope this could help someone which is in a similar situation. Still, if anyone has a decent linux alternative to burn live-usb-pens (and use them again to put some other distro's on), I'll be glad to here.

---

