---
title: "USB flash memory unreliable - SanDisk"
date: 2009-12-10
forum: General Help
---

### Post by StuartN on 2009-12-10
I have a new SanDisk 8GB Cruzer Micro USB flash drive that had the Windows U3 password protection / fake CDROM software installed at purchase. Are these SanDisk drives inherently unreliable and useless?

Background: I uninstalled the U3 utility using the Windows uninstaller and then reformatted, obtaining the full capacity. The drive worked fine for several weeks, but now I get occasional IO errors, especially with big files. Worst of all, it causes my PC to fail to resume Ubuntu after suspend.

Here is the tail of dmesg from my last copy failure. I guess the references to SCSI mean that this piece of annoying rubbish is **not** a plain USB flash drive?:

```
[ 6658.488047] usb 1-3: new high speed USB device using ehci_hcd and address 2
[ 6658.622378] usb 1-3: configuration #1 chosen from 1 choice
[ 6659.061369] usbcore: registered new interface driver libusual
[ 6659.121075] Initializing USB Mass Storage driver...
[ 6659.124787] scsi6 : SCSI emulation for USB Mass Storage devices
[ 6659.126434] usbcore: registered new interface driver usb-storage
[ 6659.126949] USB Mass Storage support registered.
[ 6659.127638] usb-storage: device found at 2
[ 6659.127646] usb-storage: waiting for device to settle before scanning
[ 6664.124255] usb-storage: device scan complete
[ 6664.125349] scsi 6:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  8.01 PQ: 0 ANSI: 0 CCS
[ 6664.140596] sd 6:0:0:0: [sdb] 15731711 512-byte hardware sectors (8055 MB)
[ 6664.142689] sd 6:0:0:0: [sdb] Write Protect is off
[ 6664.142699] sd 6:0:0:0: [sdb] Mode Sense: 45 00 00 08
[ 6664.142705] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 6664.148268] sd 6:0:0:0: [sdb] 15731711 512-byte hardware sectors (8055 MB)
[ 6664.150346] sd 6:0:0:0: [sdb] Write Protect is off
[ 6664.150356] sd 6:0:0:0: [sdb] Mode Sense: 45 00 00 08
[ 6664.150362] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 6664.153879]  sdb: sdb1
[ 6664.181160] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 6664.181438] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 6839.160099] usb 1-3: reset high speed USB device using ehci_hcd and address 2
[ 6854.272060] usb 1-3: device descriptor read/64, error -110
[ 6869.488064] usb 1-3: device descriptor read/64, error -110
[ 6869.704476] usb 1-3: reset high speed USB device using ehci_hcd and address 2
[ 6884.816062] usb 1-3: device descriptor read/64, error -110
[ 6900.032060] usb 1-3: device descriptor read/64, error -110
[ 6900.248056] usb 1-3: reset high speed USB device using ehci_hcd and address 2
[ 6905.268124] usb 1-3: device descriptor read/8, error -110
[ 6910.388184] usb 1-3: device descriptor read/8, error -110
[ 6910.604055] usb 1-3: reset high speed USB device using ehci_hcd and address 2
[ 6915.624124] usb 1-3: device descriptor read/8, error -110
[ 6920.744431] usb 1-3: device descriptor read/8, error -110
[ 6920.848083] usb 1-3: USB disconnect, address 2
[ 6920.853309] sd 6:0:0:0: Device offlined - not ready after error recovery
[ 6920.853405] sd 6:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 6920.853418] end_request: I/O error, dev sdb, sector 12170865
[ 6920.857760] sd 6:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 6920.857772] end_request: I/O error, dev sdb, sector 12171105
[ 6920.876118] sd 6:0:0:0: [sdb] READ CAPACITY failed
[ 6920.876129] sd 6:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 6920.876141] sd 6:0:0:0: [sdb] Sense not available.
[ 6920.880089] sd 6:0:0:0: [sdb] Write Protect is off
[ 6920.880099] sd 6:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 6920.880106] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 6920.880649] Buffer I/O error on device sdb1, logical block 1
[ 6920.880657] lost page write due to I/O error on sdb1
[ 6920.880672] Buffer I/O error on device sdb1, logical block 11553
[ 6920.880678] lost page write due to I/O error on sdb1
[ 6920.880686] Buffer I/O error on device sdb1, logical block 11554
[ 6920.880692] lost page write due to I/O error on sdb1
[ 6920.880700] Buffer I/O error on device sdb1, logical block 11555
[ 6920.880706] lost page write due to I/O error on sdb1
[ 6920.880713] Buffer I/O error on device sdb1, logical block 11556
[ 6920.880719] lost page write due to I/O error on sdb1
[ 6920.880726] Buffer I/O error on device sdb1, logical block 11557
[ 6920.880732] lost page write due to I/O error on sdb1
[ 6920.880739] Buffer I/O error on device sdb1, logical block 11558
[ 6920.880745] lost page write due to I/O error on sdb1
[ 6920.880752] Buffer I/O error on device sdb1, logical block 11559
[ 6920.880758] lost page write due to I/O error on sdb1
[ 6920.880766] Buffer I/O error on device sdb1, logical block 11560
[ 6920.880772] lost page write due to I/O error on sdb1
[ 6920.885597] FAT: bread failed in fat_clusters_flush
[ 6920.892816] FAT: FAT read failed (blocknr 11986)
[ 6920.892879] sd 6:0:0:0: [sdb] READ CAPACITY failed
[ 6920.892885] sd 6:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 6920.892895] sd 6:0:0:0: [sdb] Sense not available.
[ 6920.892918] FAT: FAT read failed (blocknr 11553)
[ 6920.896044] sd 6:0:0:0: [sdb] Write Protect is off
[ 6920.896053] sd 6:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 6920.896060] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 6920.950665] FAT: unable to read inode block for updating (i_pos 491046)
[ 6921.108084] usb 1-3: new high speed USB device using ehci_hcd and address 3
[ 6921.165422] FAT: unable to read inode block for updating (i_pos 491046)
[ 6921.589262] scsi 6:0:0:0: rejecting I/O to dead device
[ 6936.220061] usb 1-3: device descriptor read/64, error -110
[ 6951.436061] usb 1-3: device descriptor read/64, error -110
[ 6951.652045] usb 1-3: new high speed USB device using ehci_hcd and address 4
[ 6966.764044] usb 1-3: device descriptor read/64, error -110
[ 6981.980046] usb 1-3: device descriptor read/64, error -110
[ 6982.196062] usb 1-3: new high speed USB device using ehci_hcd and address 5
[ 6987.216173] usb 1-3: device descriptor read/8, error -110
[ 6992.336115] usb 1-3: device descriptor read/8, error -110
[ 6992.552062] usb 1-3: new high speed USB device using ehci_hcd and address 6
[ 6997.572173] usb 1-3: device descriptor read/8, error -110
[ 7002.692353] usb 1-3: device descriptor read/8, error -110
[ 7002.796069] hub 1-0:1.0: unable to enumerate USB device on port 3
[ 7003.128050] usb 3-1: new full speed USB device using ohci_hcd and address 2
[ 7018.264048] usb 3-1: device descriptor read/64, error -110
[ 7033.504072] usb 3-1: device descriptor read/64, error -110
[ 7033.744063] usb 3-1: new full speed USB device using ohci_hcd and address 3
[ 7037.903079] usb 3-1: not running at top speed; connect to a high speed hub
[ 7037.939704] usb 3-1: configuration #1 chosen from 1 choice
[ 7037.980113] scsi7 : SCSI emulation for USB Mass Storage devices
[ 7037.986049] usb-storage: device found at 3
[ 7037.986065] usb-storage: waiting for device to settle before scanning
[ 7039.019985] usb 3-1: USB disconnect, address 3
[ 7044.640050] usb 1-3: new high speed USB device using ehci_hcd and address 7
[ 7044.779456] usb 1-3: configuration #1 chosen from 1 choice
[ 7044.788194] scsi8 : SCSI emulation for USB Mass Storage devices
[ 7044.789472] usb-storage: device found at 7
[ 7044.789481] usb-storage: waiting for device to settle before scanning
[ 7049.788301] usb-storage: device scan complete
[ 7049.789410] scsi 8:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  8.01 PQ: 0 ANSI: 0 CCS
[ 7049.805366] sd 8:0:0:0: [sdb] 15731711 512-byte hardware sectors (8055 MB)
[ 7049.806613] sd 8:0:0:0: [sdb] Write Protect is off
[ 7049.806622] sd 8:0:0:0: [sdb] Mode Sense: 45 00 00 08
[ 7049.806629] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 7049.809509] sd 8:0:0:0: [sdb] 15731711 512-byte hardware sectors (8055 MB)
[ 7049.810689] sd 8:0:0:0: [sdb] Write Protect is off
[ 7049.810701] sd 8:0:0:0: [sdb] Mode Sense: 45 00 00 08
[ 7049.810707] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 7049.811894]  sdb: sdb1
[ 7049.830094] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[ 7049.830928] sd 8:0:0:0: Attached scsi generic sg2 type 0
[ 7157.577679] usb 1-3: USB disconnect, address 7
[ 7159.816050] usb 1-3: new high speed USB device using ehci_hcd and address 8
[ 7159.968851] usb 1-3: configuration #1 chosen from 1 choice
[ 7159.991274] scsi9 : SCSI emulation for USB Mass Storage devices
[ 7159.997165] usb-storage: device found at 8
[ 7159.997180] usb-storage: waiting for device to settle before scanning
[ 7164.996313] usb-storage: device scan complete
[ 7164.997408] scsi 9:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  8.01 PQ: 0 ANSI: 0 CCS
[ 7165.024169] sd 9:0:0:0: [sdb] 15731711 512-byte hardware sectors (8055 MB)
[ 7165.025483] sd 9:0:0:0: [sdb] Write Protect is off
[ 7165.025493] sd 9:0:0:0: [sdb] Mode Sense: 45 00 00 08
[ 7165.025499] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[ 7165.028358] sd 9:0:0:0: [sdb] 15731711 512-byte hardware sectors (8055 MB)
[ 7165.029356] sd 9:0:0:0: [sdb] Write Protect is off
[ 7165.029365] sd 9:0:0:0: [sdb] Mode Sense: 45 00 00 08
[ 7165.029371] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[ 7165.030462]  sdb: sdb1
[ 7165.032521] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[ 7165.033227] sd 9:0:0:0: Attached scsi generic sg2 type 0
[ 7210.463607] usb 1-3: USB disconnect, address 8
[ 7218.552048] usb 1-3: new high speed USB device using ehci_hcd and address 9
[ 7218.710029] usb 1-3: configuration #1 chosen from 1 choice
[ 7218.733845] scsi10 : SCSI emulation for USB Mass Storage devices
[ 7218.746274] usb-storage: device found at 9
[ 7218.746287] usb-storage: waiting for device to settle before scanning
[ 7223.744237] usb-storage: device scan complete
[ 7223.745464] scsi 10:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  8.01 PQ: 0 ANSI: 0 CCS
[ 7223.747672] sd 10:0:0:0: [sdb] 15731711 512-byte hardware sectors (8055 MB)
[ 7223.750271] sd 10:0:0:0: [sdb] Write Protect is off
[ 7223.750286] sd 10:0:0:0: [sdb] Mode Sense: 45 00 00 08
[ 7223.750293] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 7223.776401] sd 10:0:0:0: [sdb] 15731711 512-byte hardware sectors (8055 MB)
[ 7223.777676] sd 10:0:0:0: [sdb] Write Protect is off
[ 7223.777687] sd 10:0:0:0: [sdb] Mode Sense: 45 00 00 08
[ 7223.777694] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 7223.778863]  sdb: sdb1
[ 7223.780964] sd 10:0:0:0: [sdb] Attached SCSI removable disk
[ 7223.782457] sd 10:0:0:0: Attached scsi generic sg2 type 0
[ 7318.269216] usb 1-3: reset high speed USB device using ehci_hcd and address 9
[ 7333.380051] usb 1-3: device descriptor read/64, error -110
[ 7348.596052] usb 1-3: device descriptor read/64, error -110
[ 7348.812059] usb 1-3: reset high speed USB device using ehci_hcd and address 9
[ 7363.924046] usb 1-3: device descriptor read/64, error -110
[ 7379.140051] usb 1-3: device descriptor read/64, error -110
[ 7379.356055] usb 1-3: reset high speed USB device using ehci_hcd and address 9
[ 7384.376131] usb 1-3: device descriptor read/8, error -110
[ 7389.496156] usb 1-3: device descriptor read/8, error -110
[ 7389.712048] usb 1-3: reset high speed USB device using ehci_hcd and address 9
[ 7394.732123] usb 1-3: device descriptor read/8, error -110
[ 7399.852191] usb 1-3: device descriptor read/8, error -110
[ 7399.956075] usb 1-3: USB disconnect, address 9
[ 7399.961142] sd 10:0:0:0: Device offlined - not ready after error recovery
[ 7399.961215] sd 10:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 7399.961227] end_request: I/O error, dev sdb, sector 3537977
[ 7399.964021] __ratelimit: 861 callbacks suppressed
[ 7399.964021] Buffer I/O error on device sdb1, logical block 1
[ 7399.964021] lost page write due to I/O error on sdb1
[ 7399.966042] sd 10:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 7399.966052] end_request: I/O error, dev sdb, sector 3538217
[ 7399.992118] sd 10:0:0:0: [sdb] READ CAPACITY failed
[ 7399.992129] sd 10:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 7399.992141] sd 10:0:0:0: [sdb] Sense not available.
[ 7399.996071] sd 10:0:0:0: [sdb] Write Protect is off
[ 7399.996080] sd 10:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 7399.996087] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 7400.006050] Buffer I/O error on device sdb1, logical block 3356
[ 7400.006062] lost page write due to I/O error on sdb1
[ 7400.006071] Buffer I/O error on device sdb1, logical block 3357
[ 7400.006077] lost page write due to I/O error on sdb1
[ 7400.006085] Buffer I/O error on device sdb1, logical block 3358
[ 7400.006090] lost page write due to I/O error on sdb1
[ 7400.006098] Buffer I/O error on device sdb1, logical block 3359
[ 7400.006103] lost page write due to I/O error on sdb1
[ 7400.006113] Buffer I/O error on device sdb1, logical block 3360
[ 7400.006118] lost page write due to I/O error on sdb1
[ 7400.006126] Buffer I/O error on device sdb1, logical block 3361
[ 7400.006131] lost page write due to I/O error on sdb1
[ 7400.006139] Buffer I/O error on device sdb1, logical block 3362
[ 7400.006144] lost page write due to I/O error on sdb1
[ 7400.006151] Buffer I/O error on device sdb1, logical block 3363
[ 7400.006157] lost page write due to I/O error on sdb1
[ 7400.006164] Buffer I/O error on device sdb1, logical block 3364
[ 7400.006169] lost page write due to I/O error on sdb1
[ 7400.007464] FAT: bread failed in fat_clusters_flush
[ 7400.014089] sd 10:0:0:0: [sdb] READ CAPACITY failed
[ 7400.014098] sd 10:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 7400.014109] sd 10:0:0:0: [sdb] Sense not available.
[ 7400.016101] sd 10:0:0:0: [sdb] Write Protect is off
[ 7400.016113] sd 10:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 7400.016119] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 7400.027147] FAT: FAT read failed (blocknr 3572)
[ 7400.027224] FAT: FAT read failed (blocknr 3356)
[ 7400.094125] FAT: unable to read inode block for updating (i_pos 54794918)
[ 7400.109640] FAT: unable to read inode block for updating (i_pos 54794918)
[ 7400.220095] usb 1-3: new high speed USB device using ehci_hcd and address 10
[ 7400.742015] scsi 10:0:0:0: rejecting I/O to dead device
[ 7415.332042] usb 1-3: device descriptor read/64, error -110
[ 7430.548042] usb 1-3: device descriptor read/64, error -110
[ 7430.764043] usb 1-3: new high speed USB device using ehci_hcd and address 11
```

Can anyone reccommend a decent brand of high capacity USB flash drive?

---

### Post by prem1er on 2009-12-10
Diesel. Only way to go. I've only seen clear caps to this brand though so you might be just as upset in a couple weeks when you lose it :)

---

### Post by StuartN on 2009-12-10
> **prem1er said:**
> I've only seen clear caps to this brand though so you might be just as upset in a couple weeks when you lose it :)

Drill a hole through the top of the cap and knot in a short length of monofilament nylon fishing line attached to the eyelet on the body, and add a string of fluorescent beads. (I lost one of those suckers for a whole year, right under my nose in the pencil tray!)

---

### Post by prem1er on 2009-12-10
You now have to apologize for jacking your own thread lol. Thanks for the advice.

---

### Post by StuartN on 2009-12-10
> **prem1er said:**
> You now have to apologize for jacking your own thread lol. Thanks for the advice.

I will deny all responsibility.

Is there any way to disable the scsi element of the U3 device? I assume this is some additional circuitry that is being recognised. If I run lshw -class disk I get:

```
  *-disk
       description: SCSI Disk
       product: U3 Cruzer Micro
       vendor: SanDisk
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/sdb
       version: 8.01
       serial: u
       size: 7681MiB (8054MB)
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdb
          size: 7681MiB (8054MB)
          capabilities: partitioned partitioned:dos
```

This is USB device **Bus 001 Device 002: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/4GB Flash Drive** and I can't see an obvious way to disable the scsi element and leave the memory.

---

### Post by efflandt on 2009-12-10
I cannot tell you how to resolve the U3 thing, but I did try a 2 GB Cruzer with U3 that I normally leave on my BluRay player.

Many Linux versions currently treat all hard disk like devices (and have always treated usb mass storage) as SCSI whether the are or not.  But I doubt if that is an issue.  U3 seems to include a non-writable firmware device independent of the writable flash that appears to be an sr device (and in my case automounted as a cdrom).  It is still there after you remove and recreate partitions and format any which way.

Apparently having both sd and sr on the same device seem bog down booting from it.  A normal USB stick with bootable live/install 9.10 iso usually took me about 60-65 seconds (70 sec for microSD) from BIOS password to login screen.  The Cruzer took a solid 2 minutes.  Mine was also difficult to plug in or remove, which may stress or wear USB sockets.  So I would recommend avoiding installing a bootable system on a Cruzer w/U3.

I have been primarily using an HP 4 GB USB stick for testing/installing various systems and have not had any problems with it yet.  The microSD is 2 GB Lexar with bootable 64-bit Ubuntu 9.10 live/install iso.

---

### Post by bumanie on 2009-12-10
IMO U3 is a terrible feature - I removed it via the sandisk website as you have done. I agree that the SCSI label is not necessarily important. You say the main problem is when loading large files - what did you format the drive to? FAT16, FAT32 or some other filesystem? Some of the older filesytems have relatively small maximum sizes per file. When the drive plays up, maybe you are transferring a file larger that what the filesystem can handle.

---

### Post by yiran3344 on 2009-12-10
check the kernel is right.
Do the kernel support the SD driver?
check the modules about the SD driver.

You must ensure the kernel support the SD card.

---

### Post by StuartN on 2009-12-11
> **efflandt said:**
> U3 seems to include a non-writable firmware device independent of the writable flash that appears to be an sr device (and in my case automounted as a cdrom).  It is still there after you remove and recreate partitions and format any which way.

That seems to be the cause of the problem - in my case, the worst effect is failure to resume from standby after using this USB stick. I had assumed this was the scsi device I see, but you are right that all USB flash drives come up that way.

I removed the U3 sofware with the SanDisk tool. I can not see any way to disable the additional hardware - perhaps there is no way, because the whole purpose is that all data passes through a microcontroller that permits password protection, and the flash memory is not directly accessible. But of course their hardware design is Windows-only compatible.

@bumanie: No, that is not an issue. It is formatted FAT32. The failure typically occurs around 100MB into a transfer. I guess sustained transfer flips the hardware into an unrecoverable state.

---

