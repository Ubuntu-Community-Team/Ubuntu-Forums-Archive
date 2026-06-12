---
title: "Lubuntu 12.04 fails to load after clean install"
date: 2012-04-28
forum: General Help
---

### Post by Blitz Tungsten on 2012-04-28
I'm experiencing an *Odyssey* trying to clean install Lubuntu 12.04 64bit.

I've been using Ubuntu since 2008 and Lubuntu since October 2011.
I've been dual booting at first, but since a couple of years I've only *buntu installed in my 7 years old laptop.
I've been clean installing (never just upgrading) using LiveCDs and from USB sticks, on multiple computers, without any problem... until 2 days ago.

After downloading the latest Lubuntu AMD64 (through torrent), I've performed a positive checksum using MD5SUM and then I proceeded creating a bootable USB drive using UNETbootin, as usal.



1st try: after booting from the USB drive (4gb), I choose "Install Lubuntu" option, then it appears the standard Lubuntu loading screen, its dots keep on flashing for a while, then it stops, the USB drive stops flashing and nothing new happens.
So I have to manually shut down the computer.
Restarting it and booting from the HDD I can access my previous Lubuntu 11.10 and it works fine.


2nd try: I use the Usb-creator-gtk instead of UNETbootin with the same result.

3rd try: with a different USB drive (16gb) I obtain the same result (using Unetbootin). I got stuck in the Lubuntu loading screen, the dots stop chaning colors (blue/white), the USB key seems unresponsive, the notebook runs warmer, the fan runs faster, but nothing useful happens. 

4th try: again the same results using usb-creator.

5th try: I download the 64bit .iso from the website: still nothing new, always stuck in the loading screen.

nth try: I try to boot from a LiveCD after burning the ISO on a CD-RW -> stuck in the loading screen.

nth+1 try: I create a bootable USB drive from Windows, downloading again a new ISO (AMD64) -> nothing new.

nth+2 try: I decide to download the minimal ISO version. I boot from the USB drive, I do all the required steps, I download the lubuntu-desktop, etc. etc., I reboot, I choose "Ubuntu 12.04" from the GRUB, the flashing "-" appears for a while, then a message saying that the b43 firmware/drivers are missing (for the WiFi, but whatever, I'm plugged in through ethernet) and then the only action that I can do is to manually shut the notebook down.

nth+3 try: I boot from the HDD, whatever option I choose from the GRUB: no partition exsists (or similar)


I am at a loss.

TL;DR; I always got stuck in the Lubuntu loading screen whatever kind of installation I try to do (LiveCD/USB), I can't log in after installing the Minimal ISO.

PS I've always performed a Checkdisk with no errors.

---

### Post by sudodus on 2012-04-28
Hi Blitz,

If you let us know about your hardware, particularly cpu, ram (size) and graphics chip or card, it makes it easier to help.

0. Are you sure that your hardware can manage 64-bits? I mean, you can try the 32-bit version, it works also with 64-bit computers.

1. I think you have problems because some part of the hardware does not co-operate with Lubuntu, at least not during the install process, so I suggest that you try one or more of the boot options. It is easy to find them if you boot from the CD or the USB stick made with the usb creator (F6 at the first screen). See also this link
[[COLOR="Red"]_https://help.ubuntu.com/community/BootOptions_[/COLOR]]("https://help.ubuntu.com/community/BootOptions")

---

### Post by Blitz Tungsten on 2012-04-28
> **sudodus said:**
> Hi Blitz,

If you let us know about your hardware, particularly cpu, ram (size) and graphics chip or card, it makes it easier to help.

0. Are you sure that your hardware can manage 64-bits? I mean, you can try the 32-bit version, it works also with 64-bit computers.

1. I think you have problems because some part of the hardware does not co-operate with Lubuntu, at least not during the install process, so I suggest that you try one or more of the boot options. It is easy to find them if you boot from the CD or the USB stick made with the usb creator (F6 at the first screen). See also this link
[[COLOR="Red"]_https://help.ubuntu.com/community/BootOptions_[/COLOR]]("https://help.ubuntu.com/community/BootOptions")

0. Of course. I've been using 64bit OS since Windows XP 64bit version and from Ubuntu 8.04.
I've an Acer Ferrari 4005 WMLi, with an AMD Turion ML-37 (2.0 Ghz), ATI Radeon X700 (128mb), 2GB of RAM, 100gb of HDD @7200rpm.

Never had a single hardware problem with any version that I've used of Ubuntu, Debian and Mint.

1. That's what I was thinking about. But I've no clue of what could've gone wrong since everything seems to work perfectly (temperature, clock, memory, just any hardware parameter that I can keep track from my OS)... apart from the install part.
For this reason I've tried to boot from the USB drive first, then from the CD-ROM, then from the HDD.

---

### Post by sudodus on 2012-04-29
> **Blitz Tungsten said:**
> 0. Of course. I've been using 64bit OS since Windows XP 64bit version and from Ubuntu 8.04.
I've an Acer Ferrari 4005 WMLi, with an AMD Turion ML-37 (2.0 Ghz), ATI Radeon X700 (128mb), 2GB of RAM, 100gb of HDD @7200rpm.

Never had a single hardware problem with any version that I've used of Ubuntu, Debian and Mint.

1. That's what I was thinking about. But I've no clue of what could've gone wrong since everything seems to work perfectly (temperature, clock, memory, just any hardware parameter that I can keep track from my OS)... apart from the install part.
For this reason I've tried to boot from the USB drive first, then from the CD-ROM, then from the HDD.
Even if you have no clue, it is worth trying with the boot options, one or more of them each time. When it starts working, you will get a clue (from the option that makes it work), so go ahead and try! If you want a starting point, I'd suggest*** nomodeset***.

---

### Post by Blitz Tungsten on 2012-04-30
I've been trying almost all boot combinations, starting from nomodeset (booting from LiveCD).
**nomodeset** in particular gave different results:
- blinking dash (top left corner);
- Welcome to Ubuntu 12.04 LTS + Website link + blinking dash;
- b43-phy0 ERROR: firmware file "b43/ucode5.fw" not found. 
You must go to [https://wireless.kernel.org/](https://wireless.kernel.org/)... even tough I had the wifi turned off and a wired connection to the internet.

I've tried the other options (combined or alone by themselves) without nomodeset and I got back to the original problem: unresponsive loading screen.

I don't know what to do.

---

### Post by Blitz Tungsten on 2012-05-01
I've tried to boot from USB and then to use the nomodeset option.
After a while I get again this error:

```
b43-phy0: Broadcom 4318 WLAN found (core version 9)
Broadcom 43XX driver loaded [Features: PNL]
b43-phy0 ERROR: firmware file "b43/ucode5.fw" not found.
b43-phy0 ERROR: firmware file "b43-open/ucode5.fw" not found.  
You must go to [https://wireless.kernel.org/en/users/Driver/b43#devicefirmware](https://wireless.kernel.org/en/users/Driver/b43#devicefirmware) etc. etc.
```

Again, I had the wifi turned off and a working ethernet connection.

---

### Post by MorrisseyJ on 2012-05-01
Solution here: [http://ubuntuforums.org/showthread.php?t=1966655](http://ubuntuforums.org/showthread.php?t=1966655)
- See post #6

---

### Post by Blitz Tungsten on 2012-05-01
I solved this issue in this way, before reading the linked solution.

I booted the minimal ISO from the USB key, then I downloaded manually the b43-fwcutter and firmware-b43-installer and then after rebooting everything seems to work fine.

As linked by MorrisseyJ, if anybody encounters a similar problem, please refer to this [http://ubuntuforums.org/showthread.php?t=1966655]("http://ubuntuforums.org/showthread.php?t=1966655").

Thanks also to sudodus for the hint!

---

### Post by sudodus on 2012-05-02
Congratulations to the solution :KS

Please click on [COLOR="Red"]**Thread Tools**[/COLOR] at the top of this page to mark this thread as SOLVED

---

