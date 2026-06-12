---
title: "External drives are unmounted when they sleep"
date: 2012-02-02
forum: General Help
---

### Post by Warthaug on 2012-02-02
I am using ubuntu to run a server based on external RAID-drives connected via USB3.  As part of their normal function, these external drives go to sleep to save power when they are not in use.  However, when this happens ubuntu perceives them as being unmounted.  Is there any way to "force" ubuntu to maintain the link during sleep?  AFAIK, I cannot shut off the sleep function.

Bryan

---

### Post by TheFu on 2012-02-02
Check out "automounter" to automatically mount the partitions when requested.
[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

---

### Post by xyzzyman on 2012-02-02
What brand and model of drive? I had seagate esata drive's that I had to use a windows utility to get them to stop powering off after so long.

---

### Post by Warthaug on 2012-02-02
I'm not sure the automounter will work; I have been trying to follow these instructions:
[www.ctrlv.ca/2010/04/181/](www.ctrlv.ca/2010/04/181/)

But I get stuck at the **sudo sdparm -a** command.  I run:
sudo sdparm -a /dev/sdc

I do not get the expected output; instead I get:
```

/dev/sdc: Rack Pro   RAID0            
Read write error recovery mode page:
  AWRE        0
  ARRE        0
  TB          0
  RC          0
  EER         0
  PER         0
  DTE         0
  DCR         0
  RRC         0
  COR_S       0
  HOC         0
  DSOC        0
  LBPERE      0
  WRC         0
  RTL         0
```

Any ideas how to keep this from powering down?

Bryan

---

### Post by TheFu on 2012-02-02
> **Warthaug said:**
> I'm not sure the automounter will work
Any ideas how to keep this from powering down?

Some cheap USB HDDs have firmware that forces them to sleep after periods of dis-use.  I have a WD 2TB "Green" USB3 HDD like that.  Automounter is able to wake it up - it isn't instant - it takes 10-20 seconds, but it does wake up.  

Could be part of the USB3 controller capabilities?

---

### Post by Warthaug on 2012-02-02
> **TheFu said:**
> Some cheap USB HDDs have firmware that forces them to sleep after periods of dis-use.  I have a WD 2TB "Green" USB3 HDD like that.  Automounter is able to wake it up - it isn't instant - it takes 10-20 seconds, but it does wake up.  

Could be part of the USB3 controller capabilities?
These are not cheap HDDs; their high-quality RAID-in-a-box units:
[http://eshop.macsales.com/shop/hard-drives/RAID/Rack_Mount/FireWire_USB3_eSATA_1U](http://eshop.macsales.com/shop/hard-drives/RAID/Rack_Mount/FireWire_USB3_eSATA_1U)

I'll give the automount a go, although those 10-20sec could be a problem.

Just out of curiosity; if you use automount, even when the drive is off, does it still appear as mounted on the system?

Bryan

---

### Post by xyzzyman on 2012-02-02
> Mercury Rack Pro key features:

**User controllable** Smart Power feature for energy savings

According to the link you gave us, you need to use the OWC RAID Manager and use it's advanced mode:

> Selectable standby/sleep time for the Rack Pro
Select no standby or up to 10922 minutes for the Rack Pro to enter standby mode.


That software looks to be only for MacOS X though.

As far as being cheap or not, he was probably referring more to the USB controllers that are in some external HDD's. There's only so many HDD manufacturer's, and usually when you open up any USB or eSATA drive that isn't from Toshiba, Seagate or WD, it's still a drive inside made by them anyways.

---

### Post by TheFu on 2012-02-03
> **Warthaug said:**
> Just out of curiosity; if you use automount, even when the drive is off, does it still appear as mounted on the system?
Bryan

No.  Until you access the drive, it isn't mounted.  If the drive is powered off, the mount will fail - obviously.  You could automate accessing a file on the file system every 5 minutes to keep the mount active, right?

I've used automounter mostly for network NFS drives. They mount quickly since the drive is already spinning.  For a "sleeping" USB HDD, it takes time for the HDD to spin up and if there are multiple disks, usually an enclosure will spin them up in series, hence the 10-20 period.  It is a hardware thing, nothing to do with the automount software.

I think the base issue for your situation will need to be solved on the external array settings from the device or in firmware.  I've read that some HDDs do not support disabling the sleep function of the firmware on the HDD device.  Other HDDs provide a utility to disable this - but you need to use it on each drive, not the RAID device.

OTOH, I could be completely wrong too.

---

### Post by Warthaug on 2012-02-03
Thanx everyone.  I contacted the manufacturer and they confirmed that on non-mac systems I simply need to use their software (for which I need a mac) to turn off the sleep function.  By the sounds of it the drives will still sleep, but the RAID controller will stay awake.  Apparently mac has some sort of work-around that allows the RAID controller to sleep as well - gotta love non-standard implementations...

Thanx for the help, now I just need to borrow a mac (luckily there are a lot kicking around here)

Bryan

---

