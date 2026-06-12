---
title: "Problems mounting Samsung MP3 player"
date: 2006-06-28
forum: General Help
---

### Post by alexsb on 2006-06-28
Hi,

I just got my Samsung YP-Z5AS/ELS Player.

Unfortunately I am unable to mount it. The reason is that no device sda1 appears in /dev/, only sda

Here is the output of  dmesg | tail -n 20
```

[17180801.888000] printk: 61 messages suppressed.
[17180801.888000] Buffer I/O error on device sda1, logical block 1011808
[17180832.004000] usb 3-1: reset high speed USB device using ehci_hcd and address 8
[17180862.512000] usb 3-1: reset high speed USB device using ehci_hcd and address 8
[17180893.024000] usb 3-1: reset high speed USB device using ehci_hcd and address 8
[17180923.540000] usb 3-1: reset high speed USB device using ehci_hcd and address 8
[17180954.048000] usb 3-1: reset high speed USB device using ehci_hcd and address 8
[17180954.452000] sd 3:0:0:0: SCSI error: return code = 0x50000
[17180954.452000] end_request: I/O error, dev sda, sector 8094496
[17180954.452000] Buffer I/O error on device sda1, logical block 1011808
[17180954.452000] FAT: bogus number of reserved sectors
[17180954.456000] VFS: Can't find a valid FAT filesystem on dev sda.
[17180984.568000] usb 3-1: reset high speed USB device using ehci_hcd and address 8
[17181015.088000] usb 3-1: reset high speed USB device using ehci_hcd and address 8
[17181045.600000] usb 3-1: reset high speed USB device using ehci_hcd and address 8
[17181076.112000] usb 3-1: reset high speed USB device using ehci_hcd and address 8
[17181106.624000] usb 3-1: reset high speed USB device using ehci_hcd and address 8
[17181107.024000] sd 3:0:0:0: SCSI error: return code = 0x50000
[17181107.024000] end_request: I/O error, dev sda, sector 8094712
[17181107.024000] Buffer I/O error on device sda1, logical block 1011835
root@x10:/home/alexsb# dmesg | tail -n 20
[17181134.160000]  3:0:0:0: rejecting I/O to dead device
[17181134.160000]  3:0:0:0: rejecting I/O to dead device
[17181143.304000] usb 3-1: new high speed USB device using ehci_hcd and address 9
[17181143.600000] scsi4 : SCSI emulation for USB Mass Storage devices
[17181143.600000] usb-storage: device found at 9
[17181143.600000] usb-storage: waiting for device to settle before scanning
[17181148.848000]   Vendor: Samsung   Model: YP-Z5 (MSC)       Rev:
[17181148.848000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17181148.848000] SCSI device sda: 8094720 512-byte hdwr sectors (4144 MB)
[17181148.852000] sda: Write Protect is off
[17181148.852000] sda: Mode Sense: 07 00 00 00
[17181148.852000] sda: assuming drive cache: write through
[17181148.856000] SCSI device sda: 8094720 512-byte hdwr sectors (4144 MB)
[17181148.856000] sda: Write Protect is off
[17181148.856000] sda: Mode Sense: 07 00 00 00
[17181148.856000] sda: assuming drive cache: write through
[17181148.856000]  sda: sda1
[17181148.864000] sd 4:0:0:0: Attached scsi removable disk sda
[17181148.864000] sd 4:0:0:0: Attached scsi generic sg0 type 0
[17181148.864000] usb-storage: device scan complete

```

Under windows it worked just fine.

Furthermore the latest firmware version I can find on the net ist VER 1.01 while my player seems to have VER 1.06 US installed.

BTW: I am using Kubuntu 6.06 on a Samsung x10 Notebook

Using Gentoo on my desktop it works :(

Alex

---

### Post by dannythomas13 on 2006-07-05
i can also not get this player to work, it appears as a drive under computer but not o the desktop and when i try to access it it simply says about opening....click cancel to stop operation =(

---

### Post by alexsb on 2006-07-18
It works with the latest software. Check out [http://www.anythingbutipod.com]("http://www.anythingbutipod.com")

for details.

---

### Post by patch0 on 2006-08-01
It does indeed.  The latest firmware does the trick (I was about to take mine back to the shop!).  You can get the firmware and upgrade instructions directly from
[Samsung]("http://www.samsung.com/sg/support/productsupport/download/Model_Select.aspx?type=Digital+Audio+Player&typecode=8&subtype=Yepp&cmssubtypecode=801&model=YP-Z5FAB/ELS&filetype=FM&language=").

phew!

---

### Post by marikohurst on 2007-03-06
HELP!! I have a Samsung YP-T9JQB/XAC mp3 player & I'm currently using Linux Mint 2.2 & I can't mount it. I also don't know how to upgrade my firmware to version 1.27. Does anyone have any advice for me, I keep wanting to change my music on it & I can't. :( I hope someone can help me, thanks!

---

### Post by alexsb on 2007-03-06
[http://www.anythingbutipod.com](http://www.anythingbutipod.com)

There is everything described you need to know (search), how to update the firmware. And I'd STRONGLY reccomend doing so, I crashed a player completely with the old frimware.

I don't remember the exact steps from the top of my head though.

Alex

---

### Post by marikohurst on 2007-03-06
> **alexsb said:**
> [http://www.anythingbutipod.com](http://www.anythingbutipod.com)

There is everything described you need to know (search), how to update the firmware. And I'd STRONGLY reccomend doing so, I crashed a player completely with the old frimware.

I don't remember the exact steps from the top of my head though.

Alex

Alright, I looked at that & I know how to update my firmware. However now I need to delete some music and/or pictures to make space for it & I have no idea how to do that without it being mounted.:confused: The location of my mp3 player is /sys/devices/pci0000:00 & I need to find some files & delete them. Thanks

---

