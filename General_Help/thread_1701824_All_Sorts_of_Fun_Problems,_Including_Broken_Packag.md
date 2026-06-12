---
title: "All Sorts of Fun Problems, Including: Broken Packages, Strange Boot Errors, Video Dri"
date: 2011-03-07
forum: General Help
---

### Post by ThePineappler on 2011-03-07
Let me say at first that I have searched these forums and other forums and tried many things, but none of them have worked. I have md5 checksummed both the CD and my download, and tried installing from new CD and download. I have reinstalled Ubuntu several times. According to Update Manager, I have installed all available updates.

I'm using 10.10 right now, and have none of these problems on other household computers with 10.10.

Well, let me start with the hardware, which might help:

[LIST]
[*]NVidia/Galaxy GTX 460 768MB GC Edition (Soon to be two in Sli)
[*]Intel i7-950 (Slightly overclocked to 3.2 Ghz)
[*]Hitachi 1TB HD (Don't know the model off-hand, probably doesn't matter)
[*]EVGA E758-A1 3-Way Sli (The name of the motherboard, I'm not actually using Sli)
[*]A random USB wireless G adapter I found laying around (I'm guessing the source of my errors while booting)
[*]An EVGA USB 3.0 PCIe card (Possibly also the source of my errors while booting)
[*]3x2GB OCZ 1333mhz RAM in triple-channel mode
[*]A no-brand DVD/CD SATA read/write drive
[*]A Cooler Master 700W power supply
[*]A few other things that obviously aren't the source of the problems (Case, CPU cooler, etc.)
[/LIST]

On to the issues. After Ubuntu begins to boot, but before the splash screen, these two errors come up:

```
[   9.743971 phy0 -> rt2500usb_init_eepron: Error - Invalid RT chipset detected.
[   9.743971 phy0 -> rt2500usb_init_eepron: Error - Failed to allocate device.
```

Now, if I try to install wine (both 1.2 and 1.3) using the Ubuntu Software Center, I get this error:

```
**Package dependencies cannot be resolved**
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
```

Under Details, it says either 'wine' or 'wine1.2'.

If I try to install wine using apt-get, I get this error:

```
The following packages have unmet dependencies:
 wine1.2 : Depends: libaudio2 but it is not installable
Depends: libesd0 (>= 0.2.35) but it is not installable
Depends: libmpg123-0 (>= 1.6.2) but it is not installable
Depends: libopenal1 but it is not installable
[A whole bunch of recommended packages, will add if they're necessary but I highly doubt it]
E: Broken packages
```

I tried using Aptitude, but that also just spat out errors. I'd give you the exact errors, but right now, it's not even letting me install Aptitude:

```
Package aptitude is not available, but is referred to by another package. This may mean that the package is missing, has been obseleted, or is only available from another source
```

If I try to use Synaptic Package Manager to install Wine, I get the same error as apt-get.

Whenever I try to get any of these packages that wine is supposedly dependent on, they will not install correctly.

I also tried the method of adding the Wine repository to software sources, but that also did not work.

Also, I am unable to install the NVidia proprietary driver from Additional Drivers, as I get the following error:

```
SystemError:E:Unable to correct problems, you have held broken packages.
```

When trying to install Java or Java browser plugins such as IcedTea, I get the same error:

```
SystemError:E:Unable to correct problems, you have held broken packages.
```

From this, I would generally guess a bad installation, but seeing as I have reinstalled with different discs (all of which passed an MD5 checksum test) multiple times, I think this can be ruled out.

I apologize in advance if one (or all) of these problems is something obviously easy to fix, and thank you in advance for trying to help. Also, let me know if you need more information.
:confused:](*,)

---

### Post by Shmantiv_Radio on 2011-03-07
> **ThePineappler said:**
> Let me say at first that I have searched these forums and other forums and tried many things, but none of them have worked. I have md5 checksummed both the CD and my download, and tried installing from new CD and download. I have reinstalled Ubuntu several times. According to Update Manager, I have installed all available updates.

I'm using 10.10 right now, and have none of these problems on other household computers with 10.10.

Well, let me start with the hardware, which might help:

[LIST]
[*]NVidia/Galaxy GTX 460 768MB GC Edition (Soon to be two in Sli)
[*]Intel i7-950 (Slightly overclocked to 3.2 Ghz)
[*]Hitachi 1TB HD (Don't know the model off-hand, probably doesn't matter)
[*]EVGA E758-A1 3-Way Sli (The name of the motherboard, I'm not actually using Sli)
[*]A random USB wireless G adapter I found laying around (I'm guessing the source of my errors while booting)
[*]An EVGA USB 3.0 PCIe card (Possibly also the source of my errors while booting)
[*]3x2GB OCZ 1333mhz RAM in triple-channel mode
[*]A no-brand DVD/CD SATA read/write drive
[*]A Cooler Master 700W power supply
[*]A few other things that obviously aren't the source of the problems (Case, CPU cooler, etc.)
[/LIST]

On to the issues. After Ubuntu begins to boot, but before the splash screen, these two errors come up:

```
[   9.743971 phy0 -> rt2500usb_init_eepron: Error - Invalid RT chipset detected.
[   9.743971 phy0 -> rt2500usb_init_eepron: Error - Failed to allocate device.
```Now, if I try to install wine (both 1.2 and 1.3) using the Ubuntu Software Center, I get this error:

```
**Package dependencies cannot be resolved**
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
```Under Details, it says either 'wine' or 'wine1.2'.

If I try to install wine using apt-get, I get this error:

```
The following packages have unmet dependencies:
 wine1.2 : Depends: libaudio2 but it is not installable
Depends: libesd0 (>= 0.2.35) but it is not installable
Depends: libmpg123-0 (>= 1.6.2) but it is not installable
Depends: libopenal1 but it is not installable
[A whole bunch of recommended packages, will add if they're necessary but I highly doubt it]
E: Broken packages
```I tried using Aptitude, but that also just spat out errors. I'd give you the exact errors, but right now, it's not even letting me install Aptitude:

```
Package aptitude is not available, but is referred to by another package. This may mean that the package is missing, has been obseleted, or is only available from another source
```If I try to use Synaptic Package Manager to install Wine, I get the same error as apt-get.

Whenever I try to get any of these packages that wine is supposedly dependent on, they will not install correctly.

I also tried the method of adding the Wine repository to software sources, but that also did not work.

Also, I am unable to install the NVidia proprietary driver from Additional Drivers, as I get the following error:

```
SystemError:E:Unable to correct problems, you have held broken packages.
```When trying to install Java or Java browser plugins such as IcedTea, I get the same error:

```
SystemError:E:Unable to correct problems, you have held broken packages.
```From this, I would generally guess a bad installation, but seeing as I have reinstalled with different discs (all of which passed an MD5 checksum test) multiple times, I think this can be ruled out.

I apologize in advance if one (or all) of these problems is something obviously easy to fix, and thank you in advance for trying to help. Also, let me know if you need more information.
:confused:](*,)


I know it's probably not much help, but I used to get that invalid chipset error with my old desktop/USB dongle. It booted and worked though.

---

### Post by Shmantiv_Radio on 2011-03-07
Also for whatever reason they removed aptitude from 10.10. It's apt-get only now :/

---

### Post by ThePineappler on 2011-03-07
> **Shmantiv_Radio said:**
> I know it's probably not much help, but I used to get that invalid chipset error with my old desktop/USB dongle. It booted and worked though.
It's booting fine, and I'm pretty sure that the problem with the boot errors is my wireless network adapter, which is working fine. I'm not really worried about that bit, I just thought it would be a good idea to check while I was already making a thread.

---

### Post by ThePineappler on 2011-03-07
> **Shmantiv_Radio said:**
> Also for whatever reason they removed aptitude from 10.10. It's apt-get only now :/
I thought you could still install it, though, it just didn't come pre-packaged.

Whatever. Just thought I'd mention that I'd tried it back when aptitude was working on 10.10.

Also, these forums are a lot faster than I expected.
:D

---

### Post by ThePineappler on 2011-03-07
Oh, forgot to mention that I just built this computer, and it has never had an OS put on it until now. I have used Ubuntu since 7.10 on other computers, but this one is a clean install.

---

### Post by Shmantiv_Radio on 2011-03-07
> **ThePineappler said:**
> I thought you could still install it, though, it just didn't come pre-packaged.

Whatever. Just thought I'd mention that I'd tried it back when aptitude was working on 10.10.

Also, these forums are a lot faster than I expected.
:D

Hmmmm, ok. 

Well that's about as much as I can help you. I would say try 10.04 or wait a month for 11.04.

---

### Post by ThePineappler on 2011-03-07
> **Shmantiv_Radio said:**
> Hmmmm, ok. 

Well that's about as much as I can help you. I would say try 10.04 or wait a month for 11.04.
:P I'll probably wait awhile and see what people have to say about this thread before I go to 10.04.

I'm just somewhat shocked because I've used Ubuntu for awhile (after trying out Fedora and Gentoo) and have pretty much never seen an error that wasn't easy to fix or meaningless.

For now I have other computers. :P

---

### Post by ThePineappler on 2011-03-07
I'm going to start installing 10.04 now, and I'll let you know if I get any errors from that.

---

