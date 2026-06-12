---
title: "can not mounth usb memory/cards"
date: 2009-08-10
forum: General Help
---

### Post by dmaxx on 2009-08-10
none of my usb stick or card would work on my primary comp i just get "can not mounth driver" with the messenger"org.freedesktop.Hal.Device.UnknownError." but all the sticks and card work fine on my asus eee pc that i also have the same ver of ubuntu innstall on,sooo can someone please help me tell what is can do 2 fix it and get the cards/usb sticks 2 work again??

---

### Post by Lord foff on 2009-08-10
I get the same problem with my other drive (contains windows) meaning i can't access any of my documents :(

---

### Post by vallis on 2009-08-10
Hi,
Try opening up a terminal and typing
```

tail -f /var/log/messages

```
Keep the terminal open.
Plug in your usb drive and note any new lines that appear in your terminal. Post them here and someone may be able to help you.
At the very least you'll get the name of the device so you can try mounting manualy.

V.

---

### Post by Lord foff on 2009-08-10
> **vallis said:**
> Hi,
Try opening up a terminal and typing
```

tail -f /var/log/messages

```
Keep the terminal open.
Plug in your usb drive and note any new lines that appear in your terminal. Post them here and someone may be able to help you.
At the very least you'll get the name of the device so you can try mounting manualy.

V.

I can't, it's always connected as it's a secondary harddrive..

---

### Post by ajgreeny on 2009-08-10
Post the output of the command ```
sudo fdisk -l
``` while the disks are attached, which may allow you to then manually mount the drive(s) using the terminal command.  You could also try adding the Disk Mounter applet to your panel and try using that.

---

### Post by dmaxx on 2009-08-10
> **vallis said:**
> Hi,
Try opening up a terminal and typing
```

tail -f /var/log/messages

```
Keep the terminal open.
Plug in your usb drive and note any new lines that appear in your terminal. Post them here and someone may be able to help you.
At the very least you'll get the name of the device so you can try mounting manualy.

V.

the feedback from terminal was

maxie@maxie-desktop:~/Documents$ tail -f /var/log/messages
Aug 10 22:00:45 maxie-desktop kernel: [135426.775988] sd 14:0:0:0: [sdg] 3915776 512-byte hardware sectors: (2.00 GB/1.86 GiB)
Aug 10 22:00:45 maxie-desktop kernel: [135426.778254] sd 14:0:0:0: [sdg] Write Protect is off
Aug 10 22:00:45 maxie-desktop kernel: [135426.781614] sd 14:0:0:0: [sdg] 3915776 512-byte hardware sectors: (2.00 GB/1.86 GiB)
Aug 10 22:00:45 maxie-desktop kernel: [135426.782488] sd 14:0:0:0: [sdg] Write Protect is off
Aug 10 22:00:45 maxie-desktop kernel: [135426.782506]  sdg: sdg1
Aug 10 22:00:45 maxie-desktop kernel: [135426.829082] sd 14:0:0:0: [sdg] Attached SCSI removable disk
Aug 10 22:00:45 maxie-desktop kernel: [135426.829190] sd 14:0:0:0: Attached scsi generic sg7 type 0
Aug 10 22:01:09 maxie-desktop kernel: [135451.209481] Unknown OutputIN= OUT=virbr0 SRC=192.168.122.1 DST=192.168.122.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Aug 10 22:02:19 maxie-desktop kernel: [135521.258639] Unknown OutputIN= OUT=virbr0 SRC=192.168.122.1 DST=192.168.122.255 LEN=265 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=245 
Aug 10 22:04:53 maxie-desktop kernel: [135674.761606] usb 1-5: USB disconnect, address 52
Aug 10 22:05:20 maxie-desktop kernel: [135702.164023] usb 1-5: new high speed USB device using ehci_hcd and address 53
Aug 10 22:05:21 maxie-desktop kernel: [135703.043013] usb 1-5: configuration #1 chosen from 1 choice
Aug 10 22:05:21 maxie-desktop kernel: [135703.147563] scsi15 : SCSI emulation for USB Mass Storage devices
Aug 10 22:05:26 maxie-desktop kernel: [135708.145311] scsi 15:0:0:0: Direct-Access     Lexar    JD FireFly       1100 PQ: 0 ANSI: 0 CCS
Aug 10 22:05:26 maxie-desktop kernel: [135708.159158] sd 15:0:0:0: [sdg] 3915776 512-byte hardware sectors: (2.00 GB/1.86 GiB)
Aug 10 22:05:26 maxie-desktop kernel: [135708.159900] sd 15:0:0:0: [sdg] Write Protect is off
Aug 10 22:05:26 maxie-desktop kernel: [135708.163026] sd 15:0:0:0: [sdg] 3915776 512-byte hardware sectors: (2.00 GB/1.86 GiB)
Aug 10 22:05:26 maxie-desktop kernel: [135708.163899] sd 15:0:0:0: [sdg] Write Protect is off
Aug 10 22:05:26 maxie-desktop kernel: [135708.163917]  sdg: sdg1
Aug 10 22:05:26 maxie-desktop kernel: [135708.209627] sd 15:0:0:0: [sdg] Attached SCSI removable disk
Aug 10 22:05:26 maxie-desktop kernel: [135708.209733] sd 15:0:0:0: Attached scsi generic sg7 type 0


what can some of u people get out of that?? -_-

---

### Post by vallis on 2009-08-10
Hi,
Googling for "Direct-Access Lexar JD FireFly" brings up a few interesting sites that you may wish to look at.

From what you've posted nothing seems to be wrong (at least not to me) so you can probably try mounting manualy.

Try
```

sudo mkdir /media/disk
sudo mount -t vfat /dev/sdg1 /media/disk

```

I'm assuming the disk is formated as FAT, you can change that to ntfs or whatever.
If that works the drive should be accessible at /media/disk

If it doesn't work post whatever output you get and we'll take it from there.

V.

---

