---
title: "Help needed recovering NTFS hard-drive"
date: 2009-11-27
forum: General Help
---

### Post by D0natell0 on 2009-11-27
I've a corrupt NTFS hard-drive and I'd really appreciate any help with recovering my files.

The short story is that I seem to have corrupted the MBR while resizing partitions (preparing to install ubuntu). Now windows XP won't boot. 


In addition, I'm kicking myself (everyone join in!) because I hadn't done a recent backup - Doh! I connected the bad HDD to another windows PC to try and recover things, but it isn't recognized.

So, I've made myself a disc with ubuntu (8.10) rescue-remix, and booted the spare PC from that, but once again the bad HDD isn't recognized, i.e.

```
sudo fdisk -l
```returns the other drives (sda, sdb), but that's all, so things like testdisk won't work.

So what can I do next? I don't have a windows recovery CD, so that's not an option. I could do a re-install and restore to the backup images from a few months back, but I really would prefer not to lose my most recent files.

Apart from the pub(!), please can anyone suggest where I go from here?

---

### Post by carl.davis on 2009-11-27
Does the following confirm that the drive is installed and recognized by the bios (if you are looking for a SATA drive)? 

```
dmesg |grep sd
```

---

### Post by D0natell0 on 2009-11-27
The drive is an 120Gb IDE, connected as an external drive to the spare PC.
I'm confused over whether it should appear as sd* or hd*, so I tried both of these:

```
demsg | grep sd

demsg | grep hd
```For 'sd' I get sda and sdb, the internal drives. For 'hd' I get nothing.

---

### Post by carl.davis on 2009-11-27
Even if the partition table was hosed you should get an indication of the kernel detecting the drive. I would check cables, jumpers, etc. If you go into the bios of the machine does the drive show up there?

---

### Post by oldfred on 2009-11-27
When you plug it in is your BIOS recognizing it? 

And testdisk is really good at finding backup partition tables if they exist or tryng to figure out a new partition table if it is totally corrupt.

---

### Post by D0natell0 on 2009-11-28
I've got the bad drive loaded into an external case and plugged into the spare PC via a usb cable.

When I start up and go into the BIOS, drive config, this drive doesn't show up on the list. There are two other hard drives and two optical drives, but that's all. The cpu is an intel celeron 2.4Ghz

Should I be worried that it's not showing up? Is there a limit on the number of drives the BIOS will recognize? Should I plug it back into the Acer laptop and try running the lice CD from there?

Thanks for any help.

---

### Post by carl.davis on 2009-11-28
Sorry, I didn't realize that you were connecting it via USB. In that case the Bios may not recognize it.

Leave it unplugged then boot the machine. After the computer is running plug in the drive. Going to gnome-terminal and typing dmesg should show that it detected the drive being connected. You should see something similar to this at the end of the dmesg output:

```
[ 5463.040111] usb 2-2: new high speed USB device using ehci_hcd and address 2
[ 5463.183979] usb 2-2: configuration #1 chosen from 1 choice
[ 5463.276836] Initializing USB Mass Storage driver...
[ 5463.284597] scsi5 : SCSI emulation for USB Mass Storage devices
[ 5463.284793] usbcore: registered new interface driver usb-storage
[ 5463.284801] USB Mass Storage support registered.
[ 5463.296365] usb-storage: device found at 2
[ 5463.296371] usb-storage: waiting for device to settle before scanning
[ 5468.293396] usb-storage: device scan complete
[ 5468.294045] scsi 5:0:0:0: Direct-Access     VBTM     Store 'n' Go     1.02 PQ: 0 ANSI: 0 CCS
[ 5469.042682] sd 5:0:0:0: [sdb] 1968128 512-byte hardware sectors: (1.00 GB/961 MiB)
[ 5469.043294] sd 5:0:0:0: [sdb] Write Protect is off
[ 5469.043300] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 5469.043305] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 5469.047093] sd 5:0:0:0: [sdb] 1968128 512-byte hardware sectors: (1.00 GB/961 MiB)
[ 5469.047653] sd 5:0:0:0: [sdb] Write Protect is off
[ 5469.047658] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 5469.047663] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 5469.047670]  sdb: sdb1
[ 5469.048726] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[ 5469.048856] sd 5:0:0:0: Attached scsi generic sg2 type 0

```

---

### Post by D0natell0 on 2009-11-28
Thanks for that Carl, here's a summary of the output (note - hand typed as the spare PC isn't networked):

  	 	 	 	 	```
USB Mass Storage support registered.
 usb-storage: device found at 2
 usb-storage: waiting for device to settle before scanning
 usb-storage: device scan complete
 usb 5-1: reset high speed USB device using ehci_hcd and address 2
 usb 5-1: reset high speed USB device using ehci_hcd and address 2
 usb 5-1: reset high speed USB device using ehci_hcd and address 2
 usb 5-1: reset high speed USB device using ehci_hcd and address 2
 usb 5-1: reset high speed USB device using ehci_hcd and address 2
 scsi 2:0:0:0: Device offlined – not ready after error recovery

```

---

### Post by carl.davis on 2009-11-28
Can you try removing all of the jumpers for Master, Slave and Cable Select on that drive and try plugging it into USB again?

---

### Post by D0natell0 on 2009-11-28
Sorry about this Carl, but I can't see any Master, Slave or Cable select jumpers, either on the drive (2.5" notebook IDE HDD), or on the enclosure...?

---

### Post by carl.davis on 2009-11-28
There would be jumper pins somewhere. Maybe looking at this picture will help.

[http://www.addonics.com/support/faqs/images/1825_ms_jumpers.gif](http://www.addonics.com/support/faqs/images/1825_ms_jumpers.gif)

---

### Post by 2LSS on 2009-11-28
I just had the same problem with a usb hdd

I tried testdisk, scalpel, foremost and handy recovery running in wine (it installed ok in wine but complained about not having permission to access the drive) None of these worked and I ended up having to use handy recovery on a windows box. I'm curious if there is a better tool for ntfs in linux.

good luck

---

### Post by D0natell0 on 2009-11-28
Yep, I've got those pins, but there's nothing on them, no jumpers or cables.

---

### Post by carl.davis on 2009-11-28
I am afraid I am at a loss. If it were me I would want a 2.5 to 3.5 IDE adapter and install it into a system as a Master or Slave and see if the system detects the drive.

---

### Post by D0natell0 on 2009-12-07
I'm seriously thinking about just reformatting this corrupted NTFS hardrive now, and then trying to recover the lost files using testdisk.

Can anyone suggest how to best go about reformatting this HDD when neither windows nor ubuntu seem to recognize it? Or am I barking mad?

Here's a summary of the dmesg output when I connect the drive:

```
USB Mass Storage support registered.
 usb-storage: device found at 2
 usb-storage: waiting for device to settle before scanning
 usb-storage: device scan complete
 usb 5-1: reset high speed USB device using ehci_hcd and address 2
 usb 5-1: reset high speed USB device using ehci_hcd and address 2
 usb 5-1: reset high speed USB device using ehci_hcd and address 2
 usb 5-1: reset high speed USB device using ehci_hcd and address 2
 usb 5-1: reset high speed USB device using ehci_hcd and address 2
 scsi 2:0:0:0: Device offlined – not ready after error recovery
```


All help gratefully received!
;)

---

### Post by D0natell0 on 2009-12-16
Here is my solution:

1. I removed the HDD from it's external case and re-installed it to the laptop. 
2. Booted up the machine using an ubuntu live cd (8.0.4) using the 1st (run) option
3. Opened up Computer in file browser.

Hey Presto! There were my partitions for me to backup files out to an external drive.

Thank God for the wonder that is Ubuntu Linux!! :KS

---

