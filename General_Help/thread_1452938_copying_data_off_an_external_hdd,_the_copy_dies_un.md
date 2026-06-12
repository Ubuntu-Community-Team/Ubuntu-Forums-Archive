---
title: "copying data off an external hdd, the copy dies unexpectedly"
date: 2010-04-12
forum: General Help
---

### Post by Koriban on 2010-04-12
Hi all, 
so I have 400+ Gigs on an external disk that I'm trying to move to my shiny new Kharmic  based server. I start the copy to the internal HDD's, and it gets about 1/2 way through before mysteriously stopping (no drive access indication on the USB disk, and the copy dialog disappears). If I wait a while it also loses the disk, and I have to power cycle the drive to get Ubuntu to see it again. 

Now the disk and enclosure work fine, as they both copy to and from my main PC's Fedora install with out issue, I've tried a network (SMB/CIFS) connection, to transfer the files but I encounter the same issue with the copying dying off for no apparent reason. Any ideas as to whats happening ?

-- Sean

---

### Post by N92 on 2010-04-12
Have you tried moving half of the files first then the other half after?

---

### Post by doas777 on 2010-04-12
breaking it up into groups may help. 

is there an error message? anything useful in 'dmesg | tail'?

try running the cp from the cli and see if an error message is displayed.

also a fsck/chkdsk may be warranted.

---

### Post by ajgreeny on 2010-04-12
You could also try **rsync** to copy the files over.

---

### Post by terrrorr on 2010-04-12
It would also be nice to know if the reason occurs when your copy process tries to copy some particular file. If I copy large amount of files then I use command line.

```
 cp -R -v /source/path/* /destination/path/
```

---

### Post by Koriban on 2010-04-12
nothing out of the ordinary in dmesg, and it passes a chkdsk, and i tried copying it bit by bit but I had the same behavior on any size copy but it was less likely to do it. I'm trying the CLI CP atm.

---

### Post by Koriban on 2010-04-12
the cp does the same, dmesg is here: [http://pastebin.com/E2V6k8cd ]("http://pastebin.com/E2V6k8cd") I've run out of ideas on what this could be. the only error i get is something about a Transport method failing

---

### Post by doas777 on 2010-04-13
> **Koriban said:**
> the cp does the same, dmesg is here: [http://pastebin.com/E2V6k8cd ]("http://pastebin.com/E2V6k8cd") I've run out of ideas on what this could be. the only error i get is something about a Transport method failing
looks like the usb is disappearing and then coming back online:
```

[ 4316.717718] [B]usb 1-2: USB disconnect, address 3
## on/off cycle, seen again now [/B]
[ 4330.696059] usb 1-2: new high speed USB device using ehci_hcd and address 4
[ 4330.829080] usb 1-2: configuration #1 chosen from 1 choice
[ 4330.829956] scsi7 : SCSI emulation for USB Mass Storage devices
[ 4330.830077] usb-storage: device found at 4
[ 4330.830080] usb-storage: waiting for device to settle before scanning
[ 4335.828231] usb-storage: device scan complete
[ 4335.828717] scsi 7:0:0:0: Direct-Access     MAXTOR S TM3500630AS           PQ: 0 ANSI: 2 CCS
[ 4335.829079] sd 7:0:0:0: Attached scsi generic sg4 type 0
[ 4335.832139] sd 7:0:0:0: [sde] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[ 4335.833197] sd 7:0:0:0: [sde] Write Protect is off
[ 4335.833202] sd 7:0:0:0: [sde] Mode Sense: 34 00 00 00
[ 4335.833205] sd 7:0:0:0: [sde] Assuming drive cache: write through
[ 4335.834570] sd 7:0:0:0: [sde] Assuming drive cache: write through
[ 4335.834575]  sde: sde1
[ 4335.848945] sd 7:0:0:0: [sde] Assuming drive cache: write through
[ 4335.848950] sd 7:0:0:0: [sde] Attached SCSI disk

```

---

### Post by Koriban on 2010-04-13
that message is from me powering it off, so i can get it seen again. on its own it never disconects, i just can't see the drive.

---

