---
title: "Problem with 2GB USB memory stick"
date: 2006-06-13
forum: General Help
---

### Post by dthiery on 2006-06-13
I just installed Dapper and love everything about it, except this problem I'm having with my USB memory stick.  After a reboot it works great, I can plug it in, it opens up and I can work with it.  When I'm done I right click on it and select eject and I can take it out.  Now, if I try to plug it in again, nothing happens.  For some reason I have to reboot for it to see the USB memory stick again.

Any suggestions??

Dave

---

### Post by rbalfour on 2006-06-13
[QUOTE=dthiery]I just installed Dapper and love everything about it, except this problem I'm having with my USB memory stick.  After a reboot it works great, I can plug it in, it opens up and I can work with it.  When I'm done I right click on it and select eject and I can take it out.  Now, if I try to plug it in again, nothing happens.  For some reason I have to reboot for it to see the USB memory stick again.

Any suggestions??

Dave[/QUOTE]

Follow the same process as above, but on the second try. Open a shell and cd /media and see if it mounted there. This MIGHT be a GDM issue.

---

### Post by zxee on 2006-06-13
In the terminal type dmesg <enter> (after this non re-mounting of your usb drive has happened) There should be some messege about sda1 towards the bottom of the dmesg output. Post that here or do a search on what you get. Hope that helps.

---

### Post by dthiery on 2006-06-13
[QUOTE=rbalfour]Follow the same process as above, but on the second try. Open a shell and cd /media and see if it mounted there. This MIGHT be a GDM issue.[/QUOTE]

I just tried that and there's nothing there.

Also of note, the light on the memory stick doens't light up at all (though it does after a fresh reboot when it works).

Dave

---

### Post by dthiery on 2006-06-13
[QUOTE=zxee]In the terminal type dmesg <enter> (after this non re-mounting of your usb drive has happened) There should be some messege about sda1 towards the bottom of the dmesg output. Post that here or do a search on what you get. Hope that helps.[/QUOTE]

I just did that and there's absolutly nothing in it after I plug it in again.  I do see messages from the first time I plugged it in after a reboot (and it successfully mounted) but nothing for the second time.  I'll paste what it says about the successful mounting after a reboot:

[4294768.233000] ohci_hcd 0000:00:02.3: wakeup
[4294768.510000] usb 2-2: new full speed USB device using ohci_hcd and address 2[4294768.787000] Initializing USB Mass Storage driver...
[4294768.787000] scsi0 : SCSI emulation for USB Mass Storage devices
[4294768.788000] usb-storage: device found at 2
[4294768.788000] usb-storage: waiting for device to settle before scanning
[4294768.788000] usbcore: registered new driver usb-storage
[4294768.788000] USB Mass Storage support registered.
[4294773.796000]   Vendor: Memorex   Model: TD Classic 003C   Rev: 1.02
[4294773.797000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294773.804000] usb-storage: device scan complete
[4294773.844000] Driver 'sd' needs updating - please use bus_type methods
[4294774.602000] SCSI device sda: 3940352 512-byte hdwr sectors (2017 MB)
[4294774.609000] sda: Write Protect is off
[4294774.610000] sda: Mode Sense: 23 00 00 00
[4294774.666000] sda: assuming drive cache: write through
[4294774.666000]  sda: sda1
[4294774.677000] sd 0:0:0:0: Attached scsi removable disk sda
[4294774.689000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[4294775.594000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4294788.043000] usb 2-2: USB disconnect, address 2

---

### Post by zxee on 2006-06-13
I do not have the line "Driver 'sd' needs updating..." when I mount my 256MB usb drive:
[4299575.992000] usb 4-6: new high speed USB device using ehci_hcd and address 4[4299576.109000] scsi4 : SCSI emulation for USB Mass Storage devices
[4299576.109000] usb-storage: device found at 4
[4299576.109000] usb-storage: waiting for device to settle before scanning
[4299581.125000]   Vendor: SanDisk   Model: Cruzer Micro      Rev: 0.2
[4299581.125000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[4299581.126000] SCSI device sdf: 501759 512-byte hdwr sectors (257 MB)
[4299581.128000] sdf: Write Protect is off
[4299581.128000] sdf: Mode Sense: 03 00 00 00
[4299581.128000] sdf: assuming drive cache: write through
[4299581.131000] SCSI device sdf: 501759 512-byte hdwr sectors (257 MB)
[4299581.132000] sdf: Write Protect is off
[4299581.132000] sdf: Mode Sense: 03 00 00 00
[4299581.132000] sdf: assuming drive cache: write through
[4299581.132000]  sdf: sdf1
[4299581.135000] sd 4:0:0:0: Attached scsi removable disk sdf
[4299581.135000] sd 4:0:0:0: Attached scsi generic sg5 type 0
[4299581.136000] usb-storage: device scan complete
There are hits on that expression, also here at the ubuntu forums, although I'm not sure if they apply to you.

---

### Post by julioromano on 2006-06-13
Same problem here:
my flash drive is a PQI U339S 2GB
The device is recognized correctly and the kernel module correctly loaded (I can mount it manually with "mount /dev/sda1 /mnt").
However It doesn't appear inside "Computer" folder in Nautilus.

---

### Post by julioromano on 2006-06-13
I'll attach an archive with some txt files with various output for debugging.

---

### Post by dthiery on 2006-06-13
Well, I believe my problem is fixed...

Earlier today my primary hard drive crashed hard (I'm SO thankful I have a seperate hard drive for /home).  So, I find a spare 15GB laying around (I told you it crashed hard...unusable), put it in and reinstall Dapper and all of a sudden the USB memory stick works as advertised.

Dave

---

### Post by julioromano on 2006-06-13
But not mine, I already did a clean install of dapper... same problem... first time it mounts ok, then nothing.

---

