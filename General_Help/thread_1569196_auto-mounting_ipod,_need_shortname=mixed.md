---
title: "auto-mounting ipod, need shortname=mixed"
date: 2010-09-06
forum: General Help
---

### Post by WesleyClifford on 2010-09-06
I am running Xubuntu 10.04 that I upgraded recently from 9.04. I do not believe this is an iPod-specific problem.

In 9.04, when I plugged in my ipod, it would not mount automatically. I created an fstab entry to mount it:

```
/dev/sdb2	/media/iPod	vfat rw,user,noauto,exec,shortname=mixed	0 0
```

The important part above is "shortname=mixed" because, on my iPod, I have some directories that are in all caps. Without that option, a directory for, say, "REM" will show up as "rem" which causes all manner of problems with my scripts that sync between my computer and iPod.

Enter 10.04, which auto-mounts. I like that it auto-mounts but am willing to live without it. However, I don't know how to turn it off. I would also love to configure it to auto-mount with the "shortname=mixed" option but I do not know how to do that either.

I've looked in /etc/fstab and there is no entry for it. I've poked around in /lib/udev/ and found some iPod stuff, but nothing that says (that I can see) how to mount it. That's all I've done as I can't find anything else that leads me to see where to look.

Here's my dmesg output when I plug it in, if that helps. Any more information needed, just ask.

```

[163453.339541] usb 1-1: USB disconnect, address 3
[163453.556405] hub 1-0:1.0: unable to enumerate USB device on port 1
[163466.636438] hub 1-0:1.0: unable to enumerate USB device on port 1
[163488.144147] usb 1-1: new high speed USB device using ehci_hcd and address 10
[163488.277758] usb 1-1: configuration #1 chosen from 1 choice
[163488.284945] scsi11 : SCSI emulation for USB Mass Storage devices
[163488.285440] usb-storage: device found at 10
[163488.285446] usb-storage: waiting for device to settle before scanning
[163493.284573] usb-storage: device scan complete
[163493.379144] scsi 11:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[163493.380154] sd 11:0:0:0: Attached scsi generic sg2 type 0
[163493.389137] sd 11:0:0:0: [sdb] 58605120 512-byte logical blocks: (30.0 GB/27.9 GiB)
[163493.390059] sd 11:0:0:0: [sdb] Write Protect is off
[163493.390064] sd 11:0:0:0: [sdb] Mode Sense: 6c 00 00 08
[163493.390068] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[163493.395349] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[163493.395360]  sdb: sdb1 sdb2
[163493.815969] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[163493.815982] sd 11:0:0:0: [sdb] Attached SCSI removable disk
[163496.256444] FAT: invalid media value (0x2f)
[163496.256451] VFS: Can't find a valid FAT filesystem on dev sdb1.
[163496.824488] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[163497.023972] FAT: invalid media value (0x2f)
[163497.023983] VFS: Can't find a valid FAT filesystem on dev sdb1.
[163497.053867] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[163497.215178] FAT: invalid media value (0x2f)
[163497.215185] VFS: Can't find a valid FAT filesystem on dev sdb1.
[163498.811606] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

```

---

### Post by WesleyClifford on 2010-09-06
I don't know what happened, but it's working now. I rebooted but I'm pretty sure that's it, and I didn't do anything specifically to fix it. The reboot, even, wasn't to fix this.

But suddenly my directories look fine and work as expected.

If anybody stumbles upon this though and can tell me where I can change these settings (for example, I know no way to have it not mount as "/media/iPod" though it would be slightly easier for me if it was "/media/ipod") feel free to still answer.

---

