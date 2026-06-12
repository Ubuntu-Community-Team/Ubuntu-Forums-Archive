---
title: "Trying to Connect Garmin eTrex"
date: 2010-10-22
forum: General Help
---

### Post by igb on 2010-10-22
I am trying to connect a Garmin eTrex to my Maverick notebook. I am using a usb to serial convertor, which appears to use a well known chip set and is recognised:


```
Oct 22 07:44:16 scamper kernel: [ 1068.953367] usb 5-1: pl2303 converter now attached to ttyUSB0
Oct 22 07:48:57 scamper kernel: [ 1350.542746] usb 5-1: USB disconnect, address 7
Oct 22 07:48:57 scamper kernel: [ 1350.543003] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
Oct 22 07:48:57 scamper kernel: [ 1350.543038] pl2303 5-1:1.0: device disconnected
Oct 22 07:49:31 scamper kernel: [ 1384.472677] usb 5-1: new full speed USB device using uhci_hcd and address 8
Oct 22 07:49:31 scamper kernel: [ 1384.633321] pl2303 5-1:1.0: pl2303 converter detected
Oct 22 07:49:31 scamper kernel: [ 1384.646366] usb 5-1: pl2303 converter now attached to ttyUSB0
```


I now try to download something using gpsbabel:

```
sudo gpsbabel -i garmin -f /dev/ttyUSB0 -o gpx -F waypoints.gpx

```

This doesn't return any errors, but just hangs waiting for data until I hit ctlr-C. I have tried setting the interface on the Garmin to "Garmin" and "NMEA". I have also tried using gpsd, but still not managed to connect to the eTrex.

Everyone else seems to get this to work with no problems, so what stupid thing am I doing wrong?

[Edit]
Using XP running under Virtualbox on the same hardware, I can connect to the GPS using gpsbabel, so it's not a hardware problem.

Definitely seems to be a Maverick problem. Just tried it with Lucid and it works fine.

Ian.

---

### Post by tdekov on 2010-10-23
Just want to say, that I have the same problem. I have tried various applications, and the all behave as you describe. (Some of them use gpsbabel, so that explains the problems there.)

If I find a solution, I'll post it here.

---

### Post by captainron on 2010-10-25
I'm having a similar problem. I'm running 10.04 LTS Lucid Lynx on a laptop and the netbook remix on a EEEpc 701sd with oziexplorer under wine on both. The gps worked with moving map on the laptop but not the netbook.  I had a usb issue on both machines described in thread [http://ubuntuforums.org/showthread.php?t=1477372&highlight=usb](http://ubuntuforums.org/showthread.php?t=1477372&highlight=usb) which the removal of usbmount fixed on the laptop. Problem was it also stopped the gps from working same as in this thread. Reinstalling usbmount has not restored the gps working nor has the reinstall of the usb/serial driver(v6). At this stage I have not been able to get the gps working at all on the netbook. Thought I would sought out the issues on the laptop first.

---

### Post by igb on 2010-10-26
I have been able to reproduce my problem on another computer. Basically eTrex works i=fine with Lucid, but not Maverick. I have opened a bug [https://bugs.launchpad.net/ubuntu/+source/gpsbabel/+bug/666633]("https://bugs.launchpad.net/ubuntu/+source/gpsbabel/+bug/666633")

Ian.

---

### Post by efflandt on 2010-10-26
My eTrex Legend HCx uses a regular USB cable instead of USB to serial.  When I connect it in Lucid or Maverick dmesg only shows one line for it which does not mention any /dev for it and I cannot find anything in /dev for it (no ttyUSB0 or anything else I can find):

[ 6845.781777] usb 2-1.6: new full speed USB device using ehci_hcd and address 5

If I switch it to **usb storage** mode I it does automount its microSD:

[ 8980.319811] usb 2-1.6: new full speed USB device using ehci_hcd and address 7
[ 8980.430554] scsi8 : usb-storage 2-1.6:1.0
[ 8981.429192] scsi 8:0:0:0: Direct-Access     Garmin   eTrexHCx microSD 1.00 PQ: 0 ANSI: 5
[ 8981.430056] sd 8:0:0:0: Attached scsi generic sg7 type 0
[ 8981.432475] sd 8:0:0:0: [sdg] 3970048 512-byte logical blocks: (2.03 GB/1.89 GiB)
[ 8981.433491] sd 8:0:0:0: [sdg] Write Protect is off
[ 8981.435979]  sdg: sdg1

I connected my ancient Garmin GPS45 to Maverick using serial to USB, and that does create /dev/ttyUSB0, but I cannot communicate with it with gpstrans or gpsbabel.  I also tried gpsman, but its minimum baud rate is 9600 and the GPS45 is only 4800 baud.  So that might explain why nothing can communicate with it.

---

### Post by igb on 2010-10-31
> **efflandt said:**
> 
I connected my ancient Garmin GPS45 to Maverick using serial to USB, and that does create /dev/ttyUSB0, but I cannot communicate with it with gpstrans or gpsbabel.  I also tried gpsman, but its minimum baud rate is 9600 and the GPS45 is only 4800 baud.  So that might explain why nothing can communicate with it.

I think that this may be a bug in either the driver or the kernel shipped with Maverick. See [https://bugs.launchpad.net/bugs/666633]("https://bugs.launchpad.net/bugs/666633")for my report.

Ian.

---

