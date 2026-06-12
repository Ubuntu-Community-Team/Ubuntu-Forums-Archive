---
title: "Broadcom wireless in Karmic (9.10)"
date: 2009-11-18
forum: General Help
---

### Post by thenanodude on 2009-11-18
As it seems many have done recently, I just upgrade to 9.10 from 9.04 only to discover that my Broadcom Wireless card stopped working.  This is of course horribly disappointing considering that the upgrade to 9.04 worked fine, and I had hoped the situation would be under control from that point on.  :(

The main problem, for me anyway, is that the device drivers were simply not installed.  The ideal fix would have been to connect to the internet via a wired ethernet connection and do:

sudo apt-get install b43-fwcutter

Unfortunately I do not have a wired connection available.  Thus, I had to go to another computer that was connected and do the following:

1. Download the b43-fwcutter package from [http://packages.ubuntu.com/karmic/utils/b43-fwcutter](http://packages.ubuntu.com/karmic/utils/b43-fwcutter)
  -  I am running on a 64-bit AMD platform, so I downloaded b43-fwcutter_012-1_amd64.deb

2. Download the appropriate driver tarball from [http://mirror2.openwrt.org/sources/](http://mirror2.openwrt.org/sources/)
  - The tarball should be of the form broadcom-wl-X.X.X.X.tar.bz2
  - I have a Broadcom card with the 4311 chipset, so as near as I could tell, I needed broadcom-wl-4.150.10.5.tar.bz2
  - You may be able to find more information about which package you need here [http://linuxwireless.org/en/users/Drivers/b43#fw-b43-new](http://linuxwireless.org/en/users/Drivers/b43#fw-b43-new)

3. Copy both downloaded packages onto a USB memory stick and move them to my laptop.  I placed both into one directory, for example tmp/broadcom,  cd'd into that directory, and issued the commands:
  - sudo dpkg -i b43-fwcutter*deb
    (NOTE: when this package is installed, it asked if I wanted it to look for and download the appropriate driver.  The reason I was doing this at all is that I didn't have an internet connect, so I had to tell it "no")
  - tar -xvjf broadcom-wl-4.150.10.5.tar.bz2
     (NOTE:  you may have to change the numbers to fit your tarball version)
  - cd broadcom-wl-4.150.10.5/driver
  - sudo b43-fwcutter -w /lib/firmware wl_apsta_mimo.o

4. At this point, I rebooted my machine and I had wireless!  Incidentally, the blue/orange light in the front of my computer (An HP Pavilion dz2000) that indicates whether the wireless card is on now WORKS!  It never did in previous versions.


I also saw another solution using the LiveCD, but cannot confirm that it works:

[http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)

---

### Post by WatTwo on 2009-11-18
Hi, I have tried the live CD and for me it didn't work.

So I want to try your way, but I have no idea what tarball to get.

Could any help me?

I have a Compaq Presario F572US if that helps any :/

---

### Post by matthewbpt on 2009-11-18
This depends on what broadcom driver you have? The b43 driver is not compatible with new broadcom cards, but there is a newer driver, the bcmwl driver, which is included in ubuntu by default. If you have one of the newer cards, then install the driver like this:

```
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```

From the package description:
> These package contains Broadcom 802.11 Linux STA wireless driver
for use with Broadcom's BCM4311-, BCM4312-, BCM4321-, and
BCM4322-based hardware

---

### Post by WatTwo on 2009-11-18
Well, i can get it to display on the restricted drivers now.

But when i try to install, it just does nothing.

---

### Post by thenanodude on 2009-11-30
> This depends on what broadcom driver you have?

It does depend on what Broadcom chipset you have.  According to [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) this method should work for:
# bcm4303 (802.11b-only chips, uses b43legacy)
# bcm4306 (Rev. 2 uses b43legacy, Rev. 3 uses b43)
# bcm4309 (only the 2.4GHz part)
# bcm4311 rev 1 / bcm4312
# bcm4311 rev 2 / bcm4312 (needs patches for 2.6.24)
# bcm4312 with a/b/g (only the 2.4GHz part and no low-power LP-PHY devices)
# bcm4318 

to find out which broadcom chipset you have, use:

  lspci | grep -i broadcom

> So I want to try your way, but I have no idea what tarball to get.

I am not an expert at Broadcom chipsets and drivers.  I found that broadcom-wl-4.150.10.5.tar.bz2 worked for my 4311 chipset.  I found this website useful:  [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

> If you have one of the newer cards, then install the driver like this:

Code:

sudo apt-get install bcmwl-kernel-source
sudo modprobe wl

My problem was that I had no network connection (wireless or wired) for this computer, so issuing any "apt-get"-like commands would not work for me.  Since your post, I thought it would be worth trying to install the bcmwl-kernel-source package.  I un-installed the b43-fwcutter

   sudo dpkg --purge b43-fwcutter

and installed bcmwl-kernel-source: 

1. Downloaded the appropriate .deb package on another computer from:
   [https://launchpad.net/ubuntu/karmic/+package/bcmwl-kernel-source](https://launchpad.net/ubuntu/karmic/+package/bcmwl-kernel-source)
2. Copy bcmwl-kernel-source*deb onto my computer using a USB drive
3. Run "sudo dpkg -i bcmwl-kernel-source*deb"
4. Restarted computer.


Wireless seems to work great!  In the "Hardware Drivers", Broadcom STA wireless driver is installed and active.

Again, it does seem like it should be possible to install the bcmwl-kernel-source package from the LiveCD, as described here: [http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)

---

### Post by thenanodude on 2009-11-30
> **WatTwo said:**
> Well, i can get it to display on the restricted drivers now.

But when i try to install, it just does nothing.

You need to provide a bit more information for anybody to be able to help.  What did you try to install and how?  What is the output of these commands:

  lspci | grep -i broadcom
  dpkg -l | grep -i broadcom

---

### Post by Digikid on 2009-11-30
Why not just use the STA?  Works perfectly for my broadcom Wifi.

---

### Post by StuartN on 2009-11-30
There is a really sad problem with the Live CD - it contains both B43 and Broadcom STA drivers (both of them work well), but neither is available after installing Ubuntu 9.10.

This means you trial the system with the Live CD and everything works well, but the functions of the Live CD are no longer available after install.

You can search in Synaptic for Broadcom if you remember what to look for (although I think the latter driver is called wl there, instead of STA), and install over a cable.

---

### Post by jaj23 on 2010-01-19
I'm using a "Broadcom Corporation BCM4312 802.11b/g (rev 01)"

I just did a fresh install and having problems with wireless set-up. Got cable set up working, so in theory I should be able to just "sudo apt-get install b43-fwcutter" to update driver as the first post suggests.

I tried sudo apt-get install b43-fwcutter and it updated the driver. But I still have no wireless connection. There are still no available wireless networks in the network applet and I think I have correctly configured the VPN wireless (if that is relavent, I'm not too clued up on network stuff).

Does anyone have any ideas of what else I can try.

thanks

---

### Post by bkratz on 2010-01-19
This should help

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

