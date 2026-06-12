---
title: "Slow transfers to external HDD"
date: 2011-05-31
forum: General Help
---

### Post by Ecstatic23 on 2011-05-31
I am transferring 80gb of files from my computers hard drive to an external drive and while the speed should around 25mb/s, it's going at exactly 1mb/s.

Ubuntu 11.04 64-bit on a Mac Mini, 8gb RAM.

---

### Post by searchfgold6789 on 2011-05-31
You may have to install a driver, either a usb one or one for your hard disk. Try using a different type of partition as well.

---

### Post by Ecstatic23 on 2011-05-31
> **searchfgold6789 said:**
> You may have to install a driver, either a usb one or one for your hard disk. Try using a different type of partition as well.

Both partitions are ext4. Which drivers are you talking about?

---

### Post by searchfgold6789 on 2011-05-31
Sometimes, a company will require special software to run the disk at its full potential, and also the same for USB. Also, some external hard disks are just designed to handle NTFS or FAT better. I don't know which type of external hard disk you have but I would look up the specifications on the internet to see if you would have to do anything extra to take advantage of the max speed.

---

### Post by psusi on 2011-05-31
That's a bunch of FUD.

It sounds like you're only using a USB 1.1 port.  Check /var/log/kern.log to see how it's connecting, and are you sure the port is USB2?  Also are you using a HUB?  If so, remove it.

---

### Post by Ecstatic23 on 2011-06-01
> **psusi said:**
> That's a bunch of FUD.

It sounds like you're only using a USB 1.1 port.  Check /var/log/kern.log to see how it's connecting, and are you sure the port is USB2?  Also are you using a HUB?  If so, remove it.

I have 4 hard drives going through a USB hub, I need it because my computer only has 4 USB ports and it sources power for the hard drives.

I reset the computer and I managed to transfer at 10 - 12mb/s, better, but still not ideal

What I found from kern.log
> May 31 23:29:45 MagicONE kernel: [    3.550102] usb 4-5: new low speed USB device using ohci_hcd and address 3
May 31 23:29:45 MagicONE kernel: [    4.120100] usb 4-6: new full speed USB device using ohci_hcd and address 4
May 31 23:29:45 MagicONE kernel: [    4.358171] hub 4-6:1.0: USB hub found
May 31 23:29:45 MagicONE kernel: [    4.361204] hub 4-6:1.0: 3 ports detected
May 31 23:29:45 MagicONE kernel: [    4.451153] usb 1-1.3: new high speed USB device using ehci_hcd and address 4
May 31 23:29:45 MagicONE kernel: [    4.641154] usb 1-1.4: new high speed USB device using ehci_hcd and address 5
May 31 23:29:45 MagicONE kernel: [    4.751842] hub 1-1.4:1.0: USB hub found
May 31 23:29:45 MagicONE kernel: [    4.751944] hub 1-1.4:1.0: 4 ports detected
May 31 23:29:45 MagicONE kernel: [    4.831209] usb 4-6.1: new full speed USB device using ohci_hcd and address 5

---

### Post by psusi on 2011-06-01
> **Ecstatic23 said:**
> I have 4 hard drives going through a USB hub, I need it because my computer only has 4 USB ports and it sources power for the hard drives.

I reset the computer and I managed to transfer at 10 - 12mb/s, better, but still not ideal

What I found from kern.log

I think that's about what most people see with USB2.  USB is a horrible protocol so you never get anywhere near its theoretical capacity.  If you want good performance, you need to use eSATA.

---

### Post by Ecstatic23 on 2011-06-01
> **psusi said:**
> I think that's about what most people see with USB2.  USB is a horrible protocol so you never get anywhere near its theoretical capacity.  If you want good performance, you need to use eSATA.

I usually get ~22mb/s. eSATA has never seemed to be any faster for me then USB2.

---

### Post by psusi on 2011-06-01
> **Ecstatic23 said:**
> I usually get ~22mb/s. eSATA has never seemed to be any faster for me then USB2.

That's odd... with eSATA it is exactly like having the drive installed internally; you will get the full capacity of the drive, and most drives these days can do 60-100 MB/s.

---

### Post by Grenage on 2011-06-01
If the hard drives are all connected by USB then you're never going to get a great speed; they are sharing bus bandwidth.

For comparison, and to back up Psusi, I get around 85MB/s on my eSATA drives.

---

### Post by ivanovnegro on 2011-06-01
> **psusi said:**
> I think that's about what most people see with USB2.  USB is a horrible protocol so you never get anywhere near its theoretical capacity.  If you want good performance, you need to use eSATA.

Thats right, thats the way to go.
But honestly under Linux for me it is always slower as on Windows with USB 2.0.

---

