---
title: "USB sticks &amp; Linux compatibality"
date: 2011-11-11
forum: General Help
---

### Post by atravnic on 2011-11-11
How important is it to use a USB stick (flash drive) that specifically mentions Linux compatibility when it will be used to  create a bootable Ubuntu 11.10 drive? Will any USB stick work?

Thanks
...Fred

---

### Post by tartalo on 2011-11-11
> **atravnic said:**
> Will any USB stick work?

I think so, each and every one I tried worked for me.

---

### Post by ventrical on 2011-11-11
There are a  few that have the SD extender that will not  operate correctly as a bootable persitive drive.

---

### Post by buzzmandt on 2011-11-11
sandisk cruzers kinda suck....

see here:
[http://ubuntuforums.org/showthread.php?t=1743527](http://ubuntuforums.org/showthread.php?t=1743527)

---

### Post by effenberg0x0 on 2011-11-11
The thing is that there are correctly burned and incorrectly burned USB. It took me years to find this document and learn from it (it's from 2005!). I believe it's an amazing piece of work. I have recommended it two days ago in the ISO size thread here. 

Have a look at it when you have the time. I know it's a long read, but it will solve any doubt you had as to why some USBs boot and other don't boot on this or that OS. 

Using what I learned in this document, I took 5 USBs that were marked with a red pen as "won't boot" and guess what, they do boot. As long as the BIOS has basic USB support, one can create a bulletproof USB stick. And, guess what, the USB created by most recommended tools, as well as Ubuntu's Startup Disk Creator, fails in this sense.

[http://jaclaz.altervista.org/Projects/USB/USBstick.html](http://jaclaz.altervista.org/Projects/USB/USBstick.html)

---

### Post by ventrical on 2011-11-11
I install directly to USB. No third party. I remove my HDD .. etc.. Works beautiful. Every Ubuntu ISO recognizes my USBs as an HDD and installs them likewise. I just updated an old 8GB USB version Lucid. That thing has taken  a beating (more than any Timex watch lol) and it will run on ANY PC with USB support.

 Same with Precise ..  on an 8GB HP v255w. Any laptop. The HPs are a little slower but I just got a newer UHS 32GB USB drive and I'm going to be having fun with that. I did do a good burn of maveric with the Startup Disk Creator but it is so much faster just installing from CD .iso .

That is, take an Ubuntu Install disk like Oneiric Ocelot. Take out the HDD.  Click the CD tray open (with a pin). Insert CD. Close tray. Insert USB to available port. Make sure  USB is set to boot in ROM (since 2004 many pCs will boot atuomatically when a USB is detected - also can be set in ROM bios. )

 Turn on PC. Choose *install* and thats it. It's a perfect  persitive burn. PC in my pocket :) Thanks to our good friend Vin DSL I am able to  use my USB as a Malware Killer for Windows based PCs using Avast. It will scan the drive  and detect most viruses when thay can't be active (or are activated)and thats another great advantage of Ubuntu.

 add-on *I have a DANE brand 8GB with Lucid install , persitive now for 1 year and 3 months. Just updated in tonight. Not even a hicup.*

yes.. *bulletproof*

---

### Post by effenberg0x0 on 2011-11-11
In a BIOS that strictly follows standards, as they all should, yes. If the USB was also recorded correctly, or close to it, also yes. 

In BIOS that do not follow standards, or follows them loosely, or in the many cases in which USBs are not properly recorded, workarounds are needed. And the workarounds can turn any every USB into a bootable one. It's a known fact: some PCs do not boot from every USB. The article I mentioned got to the reason behind it. It's analysis show the geometry differences between different programs on same USB. And evaluates what is right and what is wrong. One can test the mentioned methods itself to prove this fact and turn a bootable USB into a non-bootable USB and back into a bootable one.

---

### Post by ronacc on 2011-11-11
I have found that the usb sticks that have the windows memory extender utility ( I forget what they call it ) cannot be fully formated by gparted or any linux partitioner that I have found , but there is an app for osx that will remove that utility and then you can get the full capacity in linux .If I remember right that utility would keep them from being used as a linux bootable stick .

---

### Post by ventrical on 2011-11-11
> **effenberg0x0 said:**
> In a BIOS that strictly follows standards, as they all should, yes. If the USB was also recorded correctly, or close to it, also yes. 

In BIOS that do not follow standards, or follows them loosely, or in the many cases in which USBs are not properly recorded, workarounds are needed. And the workarounds can turn any every USB into a bootable one. It's a known fact: some PCs do not boot from every USB. The article I mentioned got to the reason behind it. It's analysis show the geometry differences between different programs on same USB. And evaluates what is right and what is wrong. One can test the mentioned methods itself to prove this fact and turn a bootable USB into a non-bootable USB and back into a bootable one.


Nice read effenberg. USB tech has come a long way in the past 6 years. With impossible machines I use the PLOP bootloader in A: drive (or the cd verson of PLOP if the BIOS supports CD booting). It will detect (in most cases) a bootable USB drive. Older and slower machines will work great with DSL (Damn Small Linux)for instance. But , yes, there have been some machines that will boot ad other that will not.

---

### Post by teh603 on 2011-11-11
> **effenberg0x0 said:**
>  It's a known fact: some PCs do not boot from every USB. The article I mentioned got to the reason behind it.
My Winbook from '03 claims to not be able to boot from USB at all, and considering it has an extremely primitive BIOS its not surprising. The only three boot options are floppy, CD, and hard drive; and you have to manually set it because there's no boot menu.

Then again, that's legacy hardware and I mainly keep it around to show off how a Roman relic like that can still run a modern OS.

---

### Post by ventrical on 2011-11-11
> **ronacc said:**
> I have found that the usb sticks that have the windows memory extender utility ( I forget what they call it ) cannot be fully formated by gparted or any linux partitioner that I have found , but there is an app for osx that will remove that utility and then you can get the full capacity in linux .If I remember right that utility would keep them from being used as a linux bootable stick .


Thats exactly it. I kept blowing out all the data on that drive when I switched back from Linux to windows. It tries to use it as a bootable but no go. Nexxtech <sp> is the brand.

---

### Post by ventrical on 2011-11-12
> **teh603 said:**
> My Winbook from '03 claims to not be able to boot from USB at all, and considering it has an extremely primitive BIOS its not surprising. The only three boot options are floppy, CD, and hard drive; and you have to manually set it because there's no boot menu.

Then again, that's legacy hardware and I mainly keep it around to show off how a Roman relic like that can still run a modern OS.

 Have you tried the PLOP boot loader from Floppy?

---

### Post by philinux on 2011-11-12
Moved to general help forum.

---

### Post by rng on 2011-11-12
@ventrical: 
> Thanks to our good friend Vin DSLI apologize for being ignorant, but what is "Vin DSL" ?

I googled and found this site: [http://www.lenon.com/](http://www.lenon.com/)    but I am not clear.

---

### Post by kurt18947 on 2011-11-12
> **effenberg0x0 said:**
> In a BIOS that strictly follows standards, as they all should, yes. If the USB was also recorded correctly, or close to it, also yes. 

In BIOS that do not follow standards, or follows them loosely, or in the many cases in which USBs are not properly recorded, workarounds are needed. And the workarounds can turn any every USB into a bootable one. It's a known fact: some PCs do not boot from every USB. The article I mentioned got to the reason behind it. It's analysis show the geometry differences between different programs on same USB. And evaluates what is right and what is wrong. One can test the mentioned methods itself to prove this fact and turn a bootable USB into a non-bootable USB and back into a bootable one.

Yes, BIOSs can be problematic.  I have a Gigabyte desktop machine with an Award 'modular' BIOS. If I create a liveUSB with factory formatting, it will boot on other machines but not on this one.  If I format the USB stick in Windows 7 then create the LiveUSB, it will boot.  There is apparently something in one of the BIOS modules (rumored to be  supplied by Microsoft) that will prevent booting unless the device is formatted by Windows.  A preview of Microsoft's efforts at "secure booting" or whatever they call it?

---

### Post by ventrical on 2011-11-12
> **rng said:**
> @ventrical: 
I apologize for being ignorant, but what is "Vin DSL" ?

I googled and found this site: [http://www.lenon.com/](http://www.lenon.com/)    but I am not clear.

 My apologies. VinDSL is one of the contributors to the forums that helps people figure out Ubuntu problems.

---

