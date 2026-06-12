---
title: "Ubuntu Tablet PCs"
date: 2012-06-10
forum: General Help
---

### Post by whynot on 2012-06-10
Hi all
I would like to buy a new tablet pc . Is it possible to install ubuntu on tablet pcs.
Thanks.

---

### Post by Mark Phelps on 2012-06-11
The question is too vague to provide a specific answer.

Every Tablet PC is a different combination of hardware -- and hardware drivers is the main weakness of Linux distros because these PCs nearly always use specialized drivers -- which are not provided for Linux OSs.

The only way to really know if any PC will run a Linux distro is to boot is using a LiveCD or LiveUSB -- which, I know, can't be done before you buy it.

I had one of the premier first-gen tablet PCs for years and it worked great with Ubuntu -- until they changed the kernel versions with Ubuntu 9.04 -- and the special hardware on it never worked again after that.

If you know a make and model number, you can search the hardware and laptop forums to see if anyone has posted on that.

---

### Post by whynot on 2012-06-12
> **Mark Phelps said:**
> The question is too vague to provide a specific answer.

Every Tablet PC is a different combination of hardware -- and hardware drivers is the main weakness of Linux distros because these PCs nearly always use specialized drivers -- which are not provided for Linux OSs.

The only way to really know if any PC will run a Linux distro is to boot is using a LiveCD or LiveUSB -- which, I know, can't be done before you buy it.

I had one of the premier first-gen tablet PCs for years and it worked great with Ubuntu -- until they changed the kernel versions with Ubuntu 9.04 -- and the special hardware on it never worked again after that.

If you know a make and model number, you can search the hardware and laptop forums to see if anyone has posted on that.

Ok if it works with Andriod OS (because in markt there are toomany working with andriod system) that means it could be working with other linux distrubutions such as Ubuntu.
Thanks

---

### Post by efflandt on 2012-06-12
I went to a local computer warehouse to buy an Android tablet, but they had Acer W500P tablet PCs for nearly half price (and somewhat less than A500), so I got one of those instead (not sure if it was a return or over stock). It is about same size and weight as a netbook with detachable keyboard, 2 GB RAM, and 1280x800 touch screen.

[http://us.acer.com/ac/en/US/content/models/iconia-tab-w](http://us.acer.com/ac/en/US/content/models/iconia-tab-w)

W500P came with Windows 7 Pro on 32 GB SSD (W500 has Win7 Home), which comes in handy for field programming electronic controls at work.  It also has a internally USB connected SD slot that I to boot 64-bit Ubuntu 11.10 from on 16 GB SDHC. Everything seems to work including touch screen, WiFi, and Logitech wireless mouse with tiny USB dongle.

It took some searching to get into CMOS setup to enable F12 to boot alternate devices. But since I set that up and installed Ubuntu from USB stick to SD, if I hold the Windows button while turning it on, it automatically boots to grub on the SD.  And I just did that without the keyboard attached and logged in using the accessibility icon to bring up an on screen keyboard. I just need to figure out how to bring up the on screen keyboard in Unity.  The keyboard needs to be attached to boot external USB (to press F12).

It is not that quick running 1 GHz 2 core cpu from SD, and for its retail price you could get a faster laptop.  But for the sale price I found it works well for what I needed.

PS: I figured out how to bring up on screen keyboard with Universal Access.

---

### Post by Kira_Belka on 2012-06-13
> [http://us.acer.com/ac/en/US/content/models/iconia-tab-w](http://us.acer.com/ac/en/US/content/models/iconia-tab-w) w series uses intel cpu ..so it's not correct to name it 
"tablet PC" .. it's netbook with touchpad display :)))

something about usual tablets //
so there are a lot platforms based on ARM7/9/11 CPU.
For example fs image and boot image for Advent Vega(Nvidia tegra 2)
platform :
[http://www.adebenham.com/vega/](http://www.adebenham.com/vega/)

Also as I remember that backtrack for ARM based cpu was produced in last year.

---

### Post by whynot on 2012-06-15
> **Kira_Belka said:**
> w series uses intel cpu ..so it's not correct to name it 
"tablet PC" .. it's netbook with touchpad display :)))

something about usual tablets //
so there are a lot platforms based on ARM7/9/11 CPU.
For example fs image and boot image for Advent Vega(Nvidia tegra 2)
platform :
[http://www.adebenham.com/vega/](http://www.adebenham.com/vega/)

Also as I remember that backtrack for ARM based cpu was produced in last year.

Ok what about Archos, Arnova or odys tablets. Are we able to install ubuntu? They have OMAP cpus.
Thanks

---

### Post by biochemistrygmcs on 2012-06-16
I had similar problem of buying a tablet with FULL PC capacity.
I purchased Acer-ICONIA-W500. It have windows 7 installed on it.
At last I have a functional lubuntu 12.04.

How I did it, I am describing as follows.

From windows 7, resize partition. I freed 6 gb(from 32 gb)
I tried all Ubuntu(10,11,12) But, touch screen never worked good.
My best success is with LUBUNTU 12.04.
Prepare a USB installation on another computer. for Lubuntu 12.04

Install on 5 GB partition (keep 1 gb for swap partition).

I resized menu, panel fonts and icons. downloaded onboard. (onboard may have problems, it require two more packages.

apt-get following:
onboard
pulseaudio
pavucontrol
libatk-adaptor (for onboard)
python-gi-cairo (for onboard)
easystroke
firefox(chrome is small-small for 10 inch
skype

edit pico .config/lxpanel/Lubuntu/panels/panel to change font size of panel etc.
use look and feel program to further chage window control etc. to make suitable to tablet
The biggest problem is with touchscreen. It hangs with all ubuntu. But not with lubuntu 12.04. It is not multitouch as with windows-7.
I downloaded   easystroke with "apt-get install easystroke"
I configured left click  "flicker"  as right click. (time-out is on, delay pattern is flick). Now a rapid light tap is right-click, a 'long' tap is left-click. with some practice it is ok.
Now only thing remaining is viewing onboard with lightdm login screen. (some have ubuntu have good assessibitlty options, not there with lxde).
I can describe further details if anybody want.

---

### Post by sandy8925 on 2012-09-01
a majority of the android tablets on the market (infact, almost all of them) use ARM architecture.

the problem is, open source drivers for such hardware don't really exist . except for some things - for example, wireless network card drivers, sound drivers, touchscreen drivers, accelerometer drivers etc. may exist. but, mostly no. 

and graphics is the biggest problem. afaik there are no proper open source graphics drivers for most ARM based tablets. even if there are proprietary drivers, i don't know of any that would be usable on a gnu/linux distribution like ubuntu, and i'm pretty sure no manufacturer actually provides an ARM binary for such drivers like AMD and NVIDIA do for x86 hardware.

the exceptions to this are the mali and adreno GPUs - there exist open source reverse engineered drivers that you may be able to use.

---

