---
title: "Ubuntu not recognizing Sony DRX-840U External Burner"
date: 2012-03-18
forum: General Help
---

### Post by johnsmoke on 2012-03-18
I have a Sony DRX-840U External DVD burner, I power it on, plug in the USB cord, and nothing. It appears that the drive is getting some activity from my USB port as I see the indicator light on the burner light up when I plug in the USB, but nothing is being mounted on the desktop and it appears the drive is not being recognized.. I plug in a cd, nothing happens. Not sure where to go from here?

---

### Post by dcstar on 2012-03-19
> **johnsmoke said:**
> I have a Sony DRX-840U External DVD burner, I power it on, plug in the USB cord, and nothing. It appears that the drive is getting some activity from my USB port as I see the indicator light on the burner light up when I plug in the USB, but nothing is being mounted on the desktop and it appears the drive is not being recognized.. I plug in a cd, nothing happens. Not sure where to go from here?

Open a terminal, plug it in and after 10 seconds then run the following command:
```
dmesg
```
Then post the last screen here.

---

### Post by johnsmoke on 2012-03-19
> **dcstar said:**
> Open a terminal, plug it in and after 10 seconds then run the following command:
```
dmesg
```Then post the last screen here.

It spit out lots of info, but here' the last bit of it:

[ 8927.816042] usb 1-2: new high speed USB device using ehci_hcd and address 3
[ 8927.950084] scsi7 : usb-storage 1-2:1.0
[ 8928.994610] scsi 7:0:0:0: CD-ROM            SONY     DVD RW DRU-840A  SS01 PQ: 0 ANSI: 0
[ 8929.102572] sr1: scsi3-mmc drive: 12x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[ 8929.102847] sr 7:0:0:0: Attached scsi CD-ROM sr1
[ 8929.105625] sr 7:0:0:0: Attached scsi generic sg6 type 5
johnsmoke@johnsmoke-desktop:~$

---

### Post by dcstar on 2012-03-21
> **johnsmoke said:**
> It spit out lots of info, but here' the last bit of it:

[ 8927.816042] usb 1-2: new high speed USB device using ehci_hcd and address 3
[ 8927.950084] scsi7 : usb-storage 1-2:1.0
[ 8928.994610] scsi 7:0:0:0: CD-ROM            SONY     DVD RW DRU-840A  SS01 PQ: 0 ANSI: 0
[ 8929.102572] sr1: scsi3-mmc drive: 12x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[ 8929.102847] sr 7:0:0:0: Attached scsi CD-ROM sr1
[ 8929.105625] sr 7:0:0:0: Attached scsi generic sg6 type 5
johnsmoke@johnsmoke-desktop:~$

That shows the hardware is being recognised by the system. If you put a CD or DVD in and go to "Places" is it listed?

You need to test the external drive on another PC, it could be faulty and unable to read disks.

---

### Post by johnsmoke on 2012-03-22
> **dcstar said:**
> That shows the hardware is being recognised by the system. If you put a CD or DVD in and go to "Places" is it listed?
 
You need to test the external drive on another PC, it could be faulty and unable to read disks.
 
 
Thanks for the info. When I put a cd in my normal internal drive of my PC, it is mounted on the desktop as "Audio CD" or whatver it is. I thought the same would hold true fo the external drive. But maybe not since it's not my primary optical drive? I will go to Places ("Places" is in Ubuntu 11.04?) and see if the CD/DVD is listed there. I'll check it tonight when I get home from work. Thanks again for the help.

---

### Post by johnsmoke on 2012-03-23
Yes, nothing in Places at all when I put a cd in... Well, this stinks. I've had this external burner in the closet for years and haven't used it.. maybe that's part of the problem? Wonder if the laser head just needs to be cleaned? Anyway, if anyone has any tips, I'd love to hear them.... When I pop a disc in I do hear the drive doing things... I guess it's just trying to read it.

---

### Post by dcstar on 2012-03-24
> **johnsmoke said:**
> Thanks for the info. When I put a cd in my normal internal drive of my PC, it is mounted on the desktop as "Audio CD" or whatver it is. I thought the same would hold true fo the external drive. But maybe not since it's not my primary optical drive? I will go to Places ("Places" is in Ubuntu 11.04?) and see if the CD/DVD is listed there. I'll check it tonight when I get home from work. Thanks again for the help.

You were asked to test the external drive on **another** PC and see if it works, **did you do that?**

---

### Post by johnsmoke on 2012-03-25
> **dcstar said:**
> You were asked to test the external drive on **another** PC and see if it works, **did you do that?**

Sorry about that, I just got caught up in this not working on my main machine w/ Ubuntu that I didn't do it... Just tried it on an old laptop with Windows Vista and it played a cd with no problem. So it looks like the Burner is still good. I'd really just like to use it on my main Ubuntu Desktop here as that is what I'm using to complete a big archiving project I am working on. Is there any way I can get it to work on Ubuntu? I really appreciate the help.

---

### Post by dcstar on 2012-03-27
> **johnsmoke said:**
> Sorry about that, I just got caught up in this not working on my main machine w/ Ubuntu that I didn't do it... Just tried it on an old laptop with Windows Vista and it played a cd with no problem. So it looks like the Burner is still good. I'd really just like to use it on my main Ubuntu Desktop here as that is what I'm using to complete a big archiving project I am working on. Is there any way I can get it to work on Ubuntu? I really appreciate the help.

If it doesn't work then there is some other issue that is not apparent or it is not 100% Linux compatible.

---

