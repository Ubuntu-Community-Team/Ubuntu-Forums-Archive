---
title: "Compiz problems and other strange things"
date: 2010-08-10
forum: General Help
---

### Post by KFwLsKvVAs on 2010-08-10
Hello!

Have been happily using ubuntu for quite a while now, and just last night a bunch of strange things started happening.  

First of all, desktop effects were nil when I woke up.  Hadn't changed anything, but for some reason they were gone even though they've been fine for months and it's not like I updated anything.  So that's weird.  

So in trying to fix it, I ran compiz-check and get this output:

"Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) "

Which is strange...since it was just working a couple days ago and I haven't screwed around with the rendering method nor would I know how to.  

Then I go reinstall the mesa intel driver because I thought that could have been the problem, try to run compiz from the terminal, and find out for some reason compiz-core had magically disappeared?!

So I reinstalled compiz, and checked to see if any other programs were missing.  compiz-config-settings-manager was gone, vlc was gone, cairo-dock was gone...


I'm just like, "wtf..."

So I guess right now I'm just trying to get the rendering to work and if ANYBODY has any idea how a bunch of my programs somehow uninstalled themselves I'd love to hear a theory.  My only theory involves my cat standing on the keyboard but usually that just produces a bajallion "take screenshot" windows, and I had my laptop tilted down so that seems unlikely to be the cause.  

here's the output of my lspci:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
0a:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0a:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

if that's any help.  




Hopefully someone can at least help me get my desktop effects re-enabled.  Many thanks in advance.

---

### Post by KFwLsKvVAs on 2010-08-10
and another strange thing.  

my xorg.conf file is totally blank.

---

### Post by KFwLsKvVAs on 2010-08-10
Tried doing this:

  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg

still not able to enable desktop effects.

---

### Post by KFwLsKvVAs on 2010-08-10
Just read over what I've been posting, since I don't have an ati card it didn't make sense to purge the ati driver...although not certain if I should try to purge the intel driver.  also not sure how, so...if someone could help that would be cool...

---

### Post by KFwLsKvVAs on 2010-08-10
Solved the compiz thing.  

did this:
1) Purge all nvidia related packages from the system.
2) sudo aptitude reinstall xserver-xorg-video-intel libgl1-mesa-dri xserver-xorg-core
3) sudo dpkg-reconfigure xserver-xorg
4) sudo restart gdm

found in this thread:

[http://ubuntuforums.org/showthread.php?t=1441902](http://ubuntuforums.org/showthread.php?t=1441902)

who found it in this thread:

[http://ubuntuforums.org/showpost.php?p=9212078&postcount=10](http://ubuntuforums.org/showpost.php?p=9212078&postcount=10)

(better description of what to do in the second one)

Still unsure why a bunch of my applications disappeared though...

---

