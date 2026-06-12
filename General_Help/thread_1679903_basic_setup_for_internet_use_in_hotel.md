---
title: "basic setup for internet use in hotel"
date: 2011-02-01
forum: General Help
---

### Post by mgleslie on 2011-02-01
Hi,

New to Ubuntu but I think it'll be ideal for what I need it for. A local hotel want to have a computer set up with free net access for anyone. Basically what I want to do is set up Ubuntu so that when they log on in the morning it ONLY shows them a browser icon (either firefox or chrome) on the desktop and preferably no or very few options in the menu.

I'd also like to make sure that if the user manages to download any files they are automatically removed on shutdown or on boot up so it doesn't get full of rubbish.

Think that's it, can it be done?

Thanks
Mike

---

### Post by davidmohammed on 2011-02-01
[this]("http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/") looks like something you want - hope it helps.

---

### Post by mgleslie on 2011-02-02
That's great thanks.

Completely new to ubuntu. Just installed it on a brand new emachines ez1600 but on reboot I get...
VFS: Cannot open root device
and a kernel panic.

Any ideas? As I say its the first boot after a complete install on a fresh drive.

---

### Post by mastablasta on 2011-02-02
since we don't know how you installed it it would be best to use boot info script [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
 
follow the instructions on that website and post the results from it here. I believe it will create a results.txt file you can attach to your post.
 
While you are running a live session and are in the terminal it would be also good to post the output of this command:
 
lspci
 
this will tell us your system specs that can make the install less comfortable :-)

---

### Post by mgleslie on 2011-02-02
> **mastablasta said:**
> since we don't know how you installed it it would be best to use boot info script [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
 
follow the instructions on that website and post the results from it here. I believe it will create a results.txt file you can attach to your post.
 
While you are running a live session and are in the terminal it would be also good to post the output of this command:
 
lspci
 
this will tell us your system specs that can make the install less comfortable :-)

Results.txt attached and lspci spat out this...

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

I downloaded, burnt and installed the 32 bit desktop ubuntu 10.10 CD, installed it and told it to use the whole hard drive. it completed then told me to reboot which I did then it failed on startup.

Thanks.

---

### Post by mastablasta on 2011-02-04
Okay this is really pure Ubuntu install as i see it.
 
Graphics card should also work i believe, perhaps someone else can shed more light on this.
 
I think next step is to try and check the md5sum of your install disk: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
 
perhaps there is something wrong with download. there is another option that install wasn't done propperly, so if it's just a fresh install try to reinstall it (after you do md5sum check). it will only take 15 mins.

---

