---
title: "How to run Compiz in LiveUSB w/ Nvidia or ATI cards w/o restricted drivers"
date: 2010-10-10
forum: General Help
---

### Post by Andy06 on 2010-10-10
Compiz works out of the box in Live systems when run on computers with integrated Intel graphics chips.

Is there a way to make it work on system with Nvidia or ATI chips? Even if I have persistence enabled, downloading and installing the drivers does not carry over to the next session and it again throws up a "restricted drivers available/needed" prompt.

Thanks

P.S The purpose of doing this is for demos. Plugging in a live system and letting people play with whizbang effects is the best way to convert them :P

---

### Post by Andy06 on 2010-10-12
*bump*

---

### Post by P4man on 2010-10-12
Dont know about live systems, but if you want to impress you are better off with a full install to USB (much faster boot) and in that case you can try this trick:
[http://ubuntuforums.org/showthread.php?p=8107778](http://ubuntuforums.org/showthread.php?p=8107778)

though frankly, on most systems the opensource ati and nouveau drivers should enable compiz nowadays.

---

### Post by C.S.Cameron on 2010-10-12
You can install Nvidia drivers to a "Full install" flash drive.

Compiz works for me on my ol' laptop with an ATI X700 GPU after installing "Simple CompizConfig Settings Manager" from Ubuntu Software Center to a Live USB.

---

### Post by Andy06 on 2010-10-13
1) I thought Nouveau drivers did not yet support 3D effects? Also I have a very generic Nvidia card and it still asks for installation of Restricted drivers

2) Won't a full install with a swap partition destroy the drive pretty quickly?

---

### Post by C.S.Cameron on 2010-10-13
> **Andy06 said:**
> 1) I thought Nouveau drivers did not yet support 3D effects? Also I have a very generic Nvidia card and it still asks for installation of Restricted drivers

2) Won't a full install with a swap partition destroy the drive pretty quickly?

In the old days I could only get compiz working using restricted drivers, now days they seem to work on just about anything.

If you use the Nvidia drivers on your flash drive it may not work on other machines.
I have not had luck with proprietary drivers with most persistent, (disk image), installs.

A flash drive is good for 10000 writes,
At 1.5MB per second it takes ~3 hours to fill a 16GB drive.
3 hours x 10000 = 30000 hours = 750 work weeks.
and that would be continuous writing.
And many flash drives have a lifetime warranty.

---

### Post by P4man on 2010-10-13
> **C.S.Cameron said:**
> 
A flash drive is good for 10000 writes,
At 1.5MB per second it takes ~3 hours to fill a 16GB drive.
3 hours x 10000 = 30000 hours = 750 work weeks.

Ive seen that argument too often. You assume perfect wear levelling and an empty stick (or at least 16GB free to use for wear levelling), neither of which is likely.

---

### Post by emoguitarist06 on 2010-10-13
When you create the USB Live Boot you should have the option to leave more space so you can actually install things in the Live Session and they'll remain there (however whatever you change in the live session will not effect the actually installation)

So if you make this USB and then boot and install the propriety drivers and restart the drivers should remain intact

---

### Post by C.S.Cameron on 2010-10-13
> **P4man said:**
> Ive seen that argument too often. You assume perfect wear levelling and an empty stick (or at least 16GB free to use for wear levelling), neither of which is likely.

Flash hdd's seem to be gaining a lot of popularity despite your argument that they will quickly wear out.

10000 writes is conservative, 100000 is more likely.
New data is written to the blocks with least writes.

[http://docs.google.com/viewer?a=v&q=cache:HFN3yvtlmKIJ:www.corsair.com/_faq/FAQ_flash_drive_wear_leveling.pdf+usb+flashd+drive+wear+levels&hl=en&gl=ca&pid=bl&srcid=ADGEEShbeKNNE3MYZJbCuAmdWIPul2d0XTyg0euN8420m1nKUQHYMeFEyPQFbqyl_iBS3QeHb4snruyQ-adIJAdQrLspLwO9RLcHXQ3P6I57qYvx6bzkhJXQG_ks9pQplhSjXvXc1oHd&sig=AHIEtbSIf_kytjMggaMWN1klLTjPijdmpA](http://docs.google.com/viewer?a=v&q=cache:HFN3yvtlmKIJ:www.corsair.com/_faq/FAQ_flash_drive_wear_leveling.pdf+usb+flashd+drive+wear+levels&hl=en&gl=ca&pid=bl&srcid=ADGEEShbeKNNE3MYZJbCuAmdWIPul2d0XTyg0euN8420m1nKUQHYMeFEyPQFbqyl_iBS3QeHb4snruyQ-adIJAdQrLspLwO9RLcHXQ3P6I57qYvx6bzkhJXQG_ks9pQplhSjXvXc1oHd&sig=AHIEtbSIf_kytjMggaMWN1klLTjPijdmpA)

And the following article points not jost at the effectiveness of wear leveling but concludes that when a flash drive does wear out it remains readable, ie a persistent flash drive will still boot but may loose it's persistence.

[http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html](http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html)

---

### Post by P4man on 2010-10-13
> **C.S.Cameron said:**
> Flash hdd's seem to be gaining a lot of popularity despite your argument that they will quickly wear out.

10000 writes is conservative, 100000 is more likely.
New data is written to the blocks with least writes.

[http://docs.google.com/viewer?a=v&q=cache:HFN3yvtlmKIJ:www.corsair.com/_faq/FAQ_flash_drive_wear_leveling.pdf+usb+flashd+drive+wear+levels&hl=en&gl=ca&pid=bl&srcid=ADGEEShbeKNNE3MYZJbCuAmdWIPul2d0XTyg0euN8420m1nKUQHYMeFEyPQFbqyl_iBS3QeHb4snruyQ-adIJAdQrLspLwO9RLcHXQ3P6I57qYvx6bzkhJXQG_ks9pQplhSjXvXc1oHd&sig=AHIEtbSIf_kytjMggaMWN1klLTjPijdmpA](http://docs.google.com/viewer?a=v&q=cache:HFN3yvtlmKIJ:www.corsair.com/_faq/FAQ_flash_drive_wear_leveling.pdf+usb+flashd+drive+wear+levels&hl=en&gl=ca&pid=bl&srcid=ADGEEShbeKNNE3MYZJbCuAmdWIPul2d0XTyg0euN8420m1nKUQHYMeFEyPQFbqyl_iBS3QeHb4snruyQ-adIJAdQrLspLwO9RLcHXQ3P6I57qYvx6bzkhJXQG_ks9pQplhSjXvXc1oHd&sig=AHIEtbSIf_kytjMggaMWN1klLTjPijdmpA)

And the following article points not jost at the effectiveness of wear leveling but concludes that when a flash drive does wear out it remains readable, ie a persistent flash drive will still boot but may loose it's persistence.

[http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html](http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html)

Ive seen both links. The last one is interesting, but the author makes a huge error; he ignores the spare cells each stick has. If one assumes his stick had 1000 spares, then his result is off by a *factor *1000x.

As for the corsair piece; they might be right. Maybe corsair sticks do have proper wear levelling, but the pile of sticks I got here with IO errors probably hadnt.

Anyway, its not like these things are expensive, so feel free.

---

### Post by Andy06 on 2010-10-13
> **C.S.Cameron said:**
> In the old days I could only get compiz working using restricted drivers, now days they seem to work on just about anything.

If you use the Nvidia drivers on your flash drive it may not work on other machines.


Wouldn't it work if I had multiple drivers installed, I think it does in fact ship with multiple drivers anyway.

Also you said they work on just about anything but in my experience it only works out of the box with Intel integrated graphics (and much more smoothly than Nvidia too)

My exact card is Geforce Go 7400 and it tells me I need the restricted drivers. Can someone confirm/deny that I should be able to get it to work with the Nouveau drivers? Also I thought Nouveau still din't support 3DFX?

What are these open source ATI drivers someone mentioned? Are there Nvidia versions too?

> 
When you create the USB Live Boot you should have the option to leave more space so you can actually install things in the Live Session and they'll remain there (however whatever you change in the live session will not effect the actually installation)

So if you make this USB and then boot and install the propriety drivers and restart the drivers should remain intact

Unfortunately, it doesn't seem to work. Installing drivers and restarting results in it asking to activate the driver again which requires....another restart......followed again by re-activation.

Can anyone confirm/deny that Live systems with persistence "remember" their drivers?

Re: USB installs

Are USB flash drives typically faster or slower than a laptop HDD? Would it matter if its a 5400 RPM or 7200 RPM or SSD (like does it fall somewhere in between)?

I ask because at times I have seen much better and much worse performance from USBs and external HDDs, so I have no idea what is going on. Perhaps read speeds are very fast but writing is dog slow.

What about interface? Is read/write speed the bottleneck or would it be the USB2.0 interface?

---

### Post by C.S.Cameron on 2010-10-13
Ubuntu does not allow installing ATI drivers and Nvidia drivers at the same time, (in my experience).
At one time Ubuntu used the xorg.conf file to load video drivers.
Switchconf is an app that allows switching conf files at boot, so one could choose to load restricted video drivers or not.

It is easy enough to install "Simple CompizConfig Settings Manager" yourself and check what Compiz will do on your machine.

I know Desktop Cube and Rotate Cube work on my laptop without loading the ATI drivers.

Last time I tried installing Proprietary drivers on a persistent flash drive was back about 8.10. Icould not get either ATI or Nvidia drivers to persist then.

USB2 is much slower than SATA and even IDE.

Some O/S, (Puppy), can be run in RAM.
Ram is much faster than SATA or even USB3.
There are instructions for running Ubuntu in RAM, but I have not tried it on a thumbdrive.
[http://ubuntuforums.org/showthread.php?t=1499338&highlight=usb](http://ubuntuforums.org/showthread.php?t=1499338&highlight=usb)

Bottleneck for flash drives is R/W speed, some models of flash drive are faster than others.
SSD's running from SATA are generally faster than mechanical drives.

---

### Post by Andy06 on 2010-10-14
Sorry to pepper you with even more questions :)

1.So the nouveau drivers support the full range of 3D effects or just some? 

2.I know USB2.0 is slower than SATA but lets say I use a USB2.0 drive (average middle of the pack sort), in that case, what would be the bottleneck? The USB interface or R/W speed? 

3.How would this change if my HDD has a SWAP partition that the Live USB recognises? All distros tend to create a swap partition and when you boot a LiveUSB, it automatically recognises and uses it. Considering that these partitions are usually multiple GBs, shouldn't the LiveUSB copy its 700MB self over to it so it could run faster? 

[QUOTE=emoguitarist06]When you create the USB Live Boot you should have the option to leave more space so you can actually install things in the Live Session and they'll remain there (however whatever you change in the live session will not effect the actually installation)

So if you make this USB and then boot and install the propriety drivers and restart the drivers should remain intact [/QUOTE]

Still very eager to hear whether it is indeed possible to get drivers to "persist" like you said. I think I din't quite understand the first part of your reply

---

### Post by P4man on 2010-10-14
> **Andy06 said:**
> Sorry to pepper you with even more questions :)

1.So the nouveau drivers support the full range of 3D effects or just some? 

Not sure, since I no longer have an nVidia card, but I think all. Why dont you try?

> 
2.I know USB2.0 is slower than SATA but lets say I use a USB2.0 drive (average middle of the pack sort), in that case, what would be the bottleneck? The USB interface or R/W speed? 


The stick itself, definitely. A typical USB stick manages no more than ~25MB/s read and less than ~10 in write. USB2 in theory can handle up to 60MB in either direction (more like 40-50Mb/s effectively).

That said, like SSDs, USB sticks do have extremely low latency, and you will find real world performance to be not that bad compared to traditional harddisks, despite a 5x throughput handicap.

> 3.How would this change if my HDD has a SWAP partition that the Live USB recognises? All distros tend to create a swap partition and when you boot a LiveUSB, it automatically recognises and uses it. Considering that these partitions are usually multiple GBs, shouldn't the LiveUSB copy its 700MB self over to it so it could run faster? 


A live session will never create a swap partition, but if it detects one on the harddrive, it will use it. This wont affect speed in any way on a machine with enough RAM.

---

### Post by blueturtl on 2010-10-14
It is my experience that the free ATi drivers are now mature enough to run Compiz in most cases. Just thought I'd point that out. The only times in recent past that I haven't had Compiz on by default on a LiveCD is with nVidias.

---

### Post by Andy06 on 2010-10-14
Wait so ATIs drivers are better now :P
To the extent that you get out of the box compiz!!

And all this while (over 2 years) all I heard was how much better Nvidia's support was. I thought ATI was like Atheros or Broadcom :)

Anyway, my current situation is:

Enabling exta effects on a Nvidia Go 7400 does not work (asks for restricted drivers).

Installing restricted drivers on a live system does not work since they do not persist (they ask for activation each boot which in turn requires another boot throwing it into a vicious circle, though they apparently only need to be downloaded once)

If anyone can find a way through this impasse, I can get converts doubly quick :P

---

### Post by blueturtl on 2010-10-14
Well I wouldn't say they're better (than nVidia) yet, but good enough to run Compiz and play videos. The open drivers are still a bit glitchy in most games I've tried and can't match the Catalyst ones in performance.

This however is a big improvement over how things used to be.

I'm running Ubuntu 10.10 with a HD 4650 here, and I have working Compiz without doing anything.

---

### Post by C.S.Cameron on 2010-10-14
If you want to install Nvidia drivers just do a Full install of Ubuntu to the flash drive.
But don't expect it to work in a machine that doesn't have a Nvidia card.

---

### Post by Andy06 on 2010-10-14
> **C.S.Cameron said:**
> If you want to install Nvidia drivers just do a Full install of Ubuntu to the flash drive.
But don't expect it to work in a machine that doesn't have a Nvidia card.

As I understand it, Ubuntu comes will support and drivers for multiple cards out of the box (none of the restricted ones though). So if I do uninstall the Nvidia drivers without removing any of the previous ones, it *should* work on anything that stock Ubuntu would work with + anything with Nvidia. Right?

And if I do a full install, should I still make a Swap partition?

---

### Post by Andy06 on 2010-10-14
> **blueturtl said:**
> Well I wouldn't say they're better (than nVidia) yet, but good enough to run Compiz and play videos. The open drivers are still a bit glitchy in most games I've tried and can't match the Catalyst ones in performance.

This however is a big improvement over how things used to be.

I'm running Ubuntu 10.10 with a HD 4650 here, and I have working Compiz without doing anything.

Had been avoiding ATI like the plague but might give it a go now. These free drivers come installed by default right? Functioning out of the box just like Intel integrated graphics?

What is the package name of the free/non-free ATI drivers?

Thanks :D

---

### Post by blueturtl on 2010-10-14
> **Andy06 said:**
> Had been avoiding ATI like the plague but might give it a go now. These free drivers come installed by default right? Functioning out of the box just like Intel integrated graphics?

What is the package name of the free/non-free ATI drivers?

Thanks :D

The ATi open source drivers are included and used by default, just like with Intel, yes. This development took place after AMD bought ATi (they released the spesifications to all their hardware)! In fact the ATi brand is soon going away, it will just be AMD graphics from there on.

Anyway, the closed-source driver provided by AMD is called Catalyst, and is also available in Ubuntu through the restricted drivers manager. I've had better luck with games using those drivers, but for everyday use the OSS drivers are actually better (less buggy).

You can also download and install the Catalyst driver manually, but that is probably asking for trouble the way you used to have it. :)

---

### Post by Andy06 on 2011-01-13
*bump*

As I understand it, Ubuntu comes will support and drivers for multiple cards out of the box (none of the restricted ones though). So if I install the Nvidia drivers without removing any of the previous ones, it *should* work on anything that stock Ubuntu would work with + anything with Nvidia. Right?

---

### Post by C.S.Cameron on 2011-01-14
Back about 8.04 I would install Nvidia or ATI drivers in my flash drives and used switchconf to switch xorg.conf files at boot so I could choose restricted drivers or generic. 
I think nowadays if you install Nvidia drivers you can only boot Nvidia machines.
Lately on my machines I don't seem to need the proprietary drivers to get desktop effects.

Edit:
Or dual monitors.

---

### Post by Andy06 on 2011-01-14
> Lately on my machines I don't seem to need the proprietary drivers to get desktop effects.

Is that for Nvidia or ATI or both?

ATI now has open source drivers installed by default.
But with Nvidia cards, there is no way to enable compiz without proprietary drivers. Right? (There's been a lot of confusion about this with people saying its possible but I get no reply when I ask how :()

---

### Post by efflandt on 2011-01-14
If you have live USB iso with persistence, you might try libgl1-mesa-dri-experimental.  If that works it does glx (glxinfo and glxgears work).  Although, it would be much slower than nvidia drivers.

On a live iso you cannot install proprietary drivers, or kernel updates, or anything that initially comes up during boot, because that is all fixed, unless you first roll your own iso with what you want on it (more complicated than regular install).

If you have enough RAM, you do not need any swap at all.  I do not use swap on my work laptop booted from USB hd when it had 1 GB RAM, although, it now has 2.5 GB.  I do not use any swap on my 8 GB desktop (Maverick from hd or Natty from SSD).  You do not need swap to suspend, it is only needed (at least as large as RAM) if you want to hibernate.  Or if you do have swap on flash, you can set swappiness to 1 to only use it when absolutely necessary.

---

### Post by C.S.Cameron on 2011-01-14
> **Andy06 said:**
> Is that for Nvidia or ATI or both?

ATI now has open source drivers installed by default.
But with Nvidia cards, there is no way to enable compiz without proprietary drivers. Right? (There's been a lot of confusion about this with people saying its possible but I get no reply when I ask how :()

I just checked my Full install flash drive on my office machine with Quadro FX 4600. 
Dual view is working ok but rotate cube is not.
Rotate cube does work ok on my laptop with ATI X700 graphics.

---

### Post by Andy06 on 2011-01-14
Whats Dual view?

And was this the same flash drive? If so, which proprietary driver (if any) do you have installed on it?

ATI and Intel cards should work perfectly fine out of the box due to the included open source drivers. The Nvidia ones however shouldn't typically allow any compiz magic without proprietary drivers. 

Thanks for the help :D

---

### Post by Andy06 on 2011-01-14
Whats Dual view?

And was this the same flash drive? If so, which proprietary driver (if any) do you have installed on it?

ATI and Intel cards should work perfectly fine out of the box due to the included open source drivers. The Nvidia ones however shouldn't typically allow any compiz magic without proprietary drivers. 

Thanks for the help :D

---

### Post by Andy06 on 2011-01-14
Whats Dual view?

And was this the same flash drive? If so, which proprietary driver (if any) do you have installed on it?

ATI and Intel cards should work perfectly fine out of the box due to the included open source drivers. The Nvidia ones however shouldn't typically allow any compiz magic without proprietary drivers. 

Thanks for the help :D

---

### Post by Andy06 on 2011-01-14
Whats Dual view?

And was this the same flash drive? If so, which proprietary driver (if any) do you have installed on it?

ATI and Intel cards should work perfectly fine out of the box due to the included open source drivers. The Nvidia ones however shouldn't typically allow any compiz magic without proprietary drivers. 

Thanks for the help :D

---

### Post by Andy06 on 2011-01-14
Whats Dual view?

And was this the same flash drive? If so, which proprietary driver (if any) do you have installed on it?

ATI and Intel cards should work perfectly fine out of the box due to the included open source drivers. The Nvidia ones however shouldn't typically allow any compiz magic without proprietary drivers. 

Thanks for the help :D

---

### Post by Andy06 on 2011-01-14
Whats Dual view?

And was this the same flash drive? If so, which proprietary driver (if any) do you have installed on it?

ATI and Intel cards should work perfectly fine out of the box due to the included open source drivers. The Nvidia ones however shouldn't typically allow any compiz magic without proprietary drivers. 

Thanks for the help :D

---

### Post by Andy06 on 2011-01-14
Whats Dual view?

And was this the same flash drive? If so, which proprietary driver (if any) do you have installed on it?

ATI and Intel cards should work perfectly fine out of the box due to the included open source drivers. The Nvidia ones however shouldn't typically allow any compiz magic without proprietary drivers. 

Thanks for the help :D

---

### Post by C.S.Cameron on 2011-01-14
> **Andy06 said:**
> Whats Dual view?

And was this the same flash drive? If so, which proprietary driver (if any) do you have installed on it?

ATI and Intel cards should work perfectly fine out of the box due to the included open source drivers. The Nvidia ones however shouldn't typically allow any compiz magic without proprietary drivers. 

Thanks for the help :D

Spanning dual monitors?

---

### Post by Andy06 on 2011-01-15
Ah ok. That's not an effect though right?

I'm pretty sure you will need the driver to enable everything "blingy" :D

BTW, wheres the damn delete post button :O, accidental multiple posts.........

---

### Post by Andy06 on 2011-02-20
Installing proprietary Nvidia drivers does not uninstall the generic intel graphics drivers, I verified this via Synaptic package manager. Basically all of the open source drivers that come included remain even after a proprietary driver is installed.

Does this mean Ubuntu will know which driver to use and can now successfully run Compiz on machines with Nvidia AND Intel graphics? I'd imagine switching on boot would be impossible but then they do it with the included open source drivers anyway.

Thanks

---

### Post by Veazer on 2011-02-20
> **C.S.Cameron said:**
> If you want to install Nvidia drivers just do a Full install of Ubuntu to the flash drive.
But don't expect it to work in a machine that doesn't have a Nvidia card.

Is there ANY way around this? Would it be possible to have multiple entries in grub, like Standard, nVidia and ATI/AMD?

---

### Post by P4man on 2011-02-21
With previous versions of ubuntu, it was enough to change the xorg.conf file. I made a little script that does that automatically, I linked it earlier:
[http://ubuntuforums.org/showthread.php?p=8107778](http://ubuntuforums.org/showthread.php?p=8107778)

That worked fine, but I dont know if it still does. I suspect so.

---

### Post by amsterdamharu on 2011-02-21
There is a very complicated way of doing it and that is to customize the live cd:
[http://ubuntuforums.org/showthread.php?t=1642953](http://ubuntuforums.org/showthread.php?t=1642953)

The good thing is that since it's going to be on a usb and you have some extra space you can add some programs in there as well and even have 3d stuff enabled/custom menu if you save the settings to /etc/skel

---

