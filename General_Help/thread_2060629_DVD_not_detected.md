---
title: "DVD not detected?"
date: 2012-09-20
forum: General Help
---

### Post by jesuisbenjamin on 2012-09-20
**[SIZE="3"]When I insert a DVD in my laptop, the DVD is not detected.[/SIZE]**
 
[LIST]
[*]I use a Dell Vostro 1510 with Kubuntu 12.04, which used to read and mount the same DVDs just fine a week ago.

[*]The drive takes the DVD, I can hear it munching on it for a while, and then nothing. 

[*]Even ejecting the DVD becomes a hassle, I need to eject at boot time otherwise the OS won't allow me to. 

[*]Since I am able to boot from CD, I am assuming the issue is not a hardware issue.
[/LIST]

**How can I fix this?** Thanks! ):P

Here below is some information that may help solve the problem:

**1. wodim**
wodim --devices returns:

```
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/sg1'      rwrw-- : 'Optiarc' 'DVD+-RW AD-7640A'
-------------------------------------------------------------------------
```

**2. lshw**
sudo lshw -class disk returns:

```
  *-cdrom                 
       description: DVD-RAM writer
       product: DVD+-RW AD-7640A
       vendor: Optiarc
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom2
       logical name: /dev/cdrw2
       logical name: /dev/dvd2
       logical name: /dev/dvdrw2
       logical name: /dev/sr0
       version: JD06
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open
```

**3.lspci**
lspci returns:

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)                                                               
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
08:05.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
08:05.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
08:05.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
```

**4. lsusb**
and lsusb:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:63e0 Microdia Sonix Integrated Webcam
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
```

**5. blacklist**
The /etc/modprobe.d/blacklist.conf contains:

```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx
```

---

### Post by daslinkard on 2012-09-20
This sounds like a failing optical drive to me.

---

### Post by jesuisbenjamin on 2012-09-21
> **daslinkard said:**
> This sounds like a failing optical drive to me.

Which means?

---

### Post by Deepak A on 2012-09-21
It can be a problem with your DVD Drive. Drives using Laser's with  different wave lengths for CD's and DVD's. Have you tried any other DVD?  If it is working fine then problem is with your DVD which worked before. Also try Lens Cleaner CD if available.

---

### Post by jesuisbenjamin on 2012-09-21
> **Deepak A said:**
> It can be a problem with your DVD Drive. Drives using Laser's with  different wave lengths for CD's and DVD's. Have you tried any other DVD?  If it is working fine then problem is with your DVD which worked before. Also try Lens Cleaner CD if available.

I am not able to read any DVD indeed while I can read CDs (I assumed both were the same). I don't understand what would have caused the defect: I've hardly ever read a DVD before with this laptop (having always used internet as a source of videos).

I don't know if I can get a lens cleaner where I am now (Kathmandu).

Is there no way to test out what's really going on?

---

### Post by Deepak A on 2012-09-21
> **jesuisbenjamin said:**
> I am not able to read any DVD indeed while I can read CDs (I assumed both were the same). I don't understand what would have caused the defect: I've hardly ever read a DVD before with this laptop (having always used internet as a source of videos).

I don't know if I can get a lens cleaner where I am now (Kathmandu).

Is there no way to test out what's really going on?


Any other OS in your machine? If it is a problem with your drive, you need to do Calibration process. 

Anyways, try with other OS also, if the problem persists u need to repair your DVD drive.

One last thing you can do is, try mounting it manually via command line. 
And add the entry in /etc/fstab also.

---

### Post by jesuisbenjamin on 2012-09-21
> **Deepak A said:**
> Any other OS in your machine?
Nope.
> **Deepak A said:**
> 
If it is a problem with your drive, you need to do Calibration process. 

Can't I do that with Ubuntu?
> **Deepak A said:**
> 
Anyways, try with other OS also, if the problem persists u need to repair your DVD drive.

I can't really afford re-installing an entire other OS right now--my laptop is my main work tool. Besides, I've been using Ubuntu on this machine for the past 5 years and it always worked fine with regard to the CD/DVD drive.
> **Deepak A said:**
> 
One last thing you can do is, try mounting it manually via command line. 
And add the entry in /etc/fstab also.
How?

---

### Post by Deepak A on 2012-09-21
Calibration is a hardware process. You cant do that using any software. Lens cleaner CD perhaps does it. 

For mounting it manually, insert the DVD

1. Make a folder 
$mkdir /media/cdrom

2. Add the mount point to /etc/fstab
[COLOR=#0000FF][COLOR=Black]$vi /etc/fstab[/COLOR]

[/COLOR]The these contents:
/dev/cdrom     /media/cdrom      auto      rw,noauto,user,exec      0      0

(See the spaces and apply them properly).

---

### Post by newb85 on 2012-09-21
More info on editing fstab can be found at [https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab").

---

### Post by daslinkard on 2012-09-21
> **jesuisbenjamin said:**
> 
I can't really afford re-installing an entire other OS right now--my laptop is my main work tool. Besides, I've been using Ubuntu on this machine for the past 5 years and it always worked fine with regard to the CD/DVD drive.

So what about downloading Ubuntu to a CD an installing that route as opposed to using a DVD?

---

### Post by newb85 on 2012-09-21
> **daslinkard said:**
> So what about downloading Ubuntu to a CD an installing that route as opposed to using a DVD?

The OP is trying to watch a movie, not install anything.

---

### Post by daslinkard on 2012-09-21
> **newb85 said:**
> The OP is trying to watch a movie, not install anything.

Not sure how I missed this last night...I still think it's the optical drive going bad if other DVD's are having the same issue on the machine.

---

### Post by jesuisbenjamin on 2012-09-21
> **daslinkard said:**
> So what about downloading Ubuntu to a CD an installing that route as opposed to using a DVD?

I am not sure as to what you mean here. I am not trying to install Ubuntu, I am trying to read a DVD on Kubuntu 12.04. But perhaps I missunderstand you?

---

### Post by daslinkard on 2012-09-21
> **jesuisbenjamin said:**
> I am not sure as to what you mean here. I am not trying to install Ubuntu, I am trying to read a DVD on Kubuntu 12.04. But perhaps I missunderstand you?

It was my fault in that I misunderstood what you were originally writing.  Try a different DVD and if you are still having the same issue then you know the issue is within the optical drive.

---

### Post by jesuisbenjamin on 2012-09-21
> **daslinkard said:**
> It was my fault in that I misunderstood what you were originally writing.  Try a different DVD and if you are still having the same issue then you know the issue is within the optical drive.

I think I mentioned earlier: I cannot read any DVD, though I am able to read CDs (i mean not me, my drive can).

---

### Post by daslinkard on 2012-09-21
If you cannot read any DVD but you can on CD's then I would definitely say the issue at hand is your drive.  I would suggest looking at replacing it.

---

### Post by jesuisbenjamin on 2012-09-21
> **daslinkard said:**
> If you cannot read any DVD but you can on CD's then I would definitely say the issue at hand is your drive.  I would suggest looking at replacing it.

:( !!

I don't think i can replace it. It's embeded in the laptop (without tray) on a Dell Vostro 15010. I can't see screws or anything below to remove it.

---

### Post by daslinkard on 2012-09-21
It looks like you can replace the drive and [here]("http://support.dell.com/support/edocs/systems/vos1510/en/SM/html/optical.htm#wp1179928") is instructions how.  By doing simple Youtube searches you should be able to watch how to take it out via the video as well.

---

