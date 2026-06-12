---
title: "Karmic won't recognize USB hard drive and HTC Touch"
date: 2009-12-01
forum: General Help
---

### Post by BattMatt on 2009-12-01
When I first upgraded to Karmic, I would plug in my Western Digital USB-powered hard drive and it would work without incident.  My phone would ask me if I wanted to use it as a hard drive when I'd plug it in as well.

Somewhere along the way, I downloaded an update or changed something that has messed up this functionality.  When I plug in either of these components, the computer basically acts as if they don't exist.  No error appears in dmesg, their partitions do not appear in any logs or programs (gparted).  lsusb does not list them anymore.

I've ruled out the usb cable and either of the components as the source of the problem.  It's happening on TWO computers loaded with the updated version of Karmic....so it's something with Karmic.

Any ideas on what on earth happened?  Are other people experiencing these problems with Karmic?

---

### Post by rheaj on 2009-12-01
I have been experiencing the same problem since yesterday.  I've tried two different external USB hard drives and several different USB flash sticks, and none of them work.

When I connect a flash drive, dmesg says the following:

> 
[  434.640277] usb 1-3.4: new high speed USB device using ehci_hcd and address 10
[  434.757550] usb 1-3.4: configuration #1 chosen from 1 choice
[  434.757843] scsi8 : SCSI emulation for USB Mass Storage devices
[  434.757935] usb-storage: device found at 10
[  434.757938] usb-storage: waiting for device to settle before scanning
[  439.750226] usb-storage: device scan complete
[  439.751805] scsi 8:0:0:0: Direct-Access     Memorex  TD Classic 003B  PMAP PQ: 0 ANSI: 0 CCS
[  439.752208] sd 8:0:0:0: Attached scsi generic sg3 type 0
[  440.182447] sd 8:0:0:0: [sdb] 977664 512-byte logical blocks: (500 MB/477 MiB)
[  440.183942] sd 8:0:0:0: [sdb] Write Protect is off
[  440.183945] sd 8:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  440.183947] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  440.186944] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  440.186950]  sdb: sdb1
[  440.189946] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  440.189951] sd 8:0:0:0: [sdb] Attached SCSI removable disk


So, I know it is seeing USB devices getting connected.  The command "ls /dev | grep sd" shows the device being added (/dev/sdb) but does not show any partitions (such as /dev/sdb1) to mount.

---

### Post by rheaj on 2009-12-01
Interestingly, when I plugged in two devices, both suddenly work instantly.  I unplugged both, plugged one in and it worked.  I then plugged the second one in, and it DIDN'T work.  Wierd.

---

### Post by BattMatt on 2009-12-03
I tried rolling back to the .14 kernel- no luck.  So, we can rule out the .15 kernel as the problem, I think.  

Still looking....

---

### Post by BattMatt on 2009-12-03
Update: T'was the cable after all.  I'd ruled out a bad cable with...a bad cable.  

Now that I have a *good* cable, Karmic is running just fine.

The moral of the story:  sometimes if you think you've ruled something out, try again anyway...;)

---

