---
title: "How to make western digital hard drive work in ubuntu?"
date: 2011-10-08
forum: General Help
---

### Post by shresthanator on 2011-10-08
I just got a western digital external harddrive and I want to make it so that I can use it under ubuntu & windows. It came with some drivers and some kind of software that automatically backs up folders if u set it to (only in windows). This is not really that important to me though, I just want to be able to use in in windows and ubuntu. Can somebody please help me out?

---

### Post by Oxyris on 2011-10-08
Format the external hard drive to FAT32. Both linux and windows can read and write on it. I think if you open gparted you should see both you internal and external hd (once it's plugged in of course) you click on the external one and you should be able to switch the format to FAT32 (i'm currently not on ubuntu or gparted so i don't remember exactly what to click). There's a way to do it in windows too but I don't remember but western digital has a guide on it if you google it.
Please note that if you have anything on that hard drive it will be erased. So back up anything important that is on that hard drive!

---

### Post by jonnyboysmithy on 2011-10-08
If you format as FAT32 then you won't be able to have files bigger than 4GB.
I think NTFS is nicer because it doesn't have this limitation and, but mac computers cannot write on ntfs only read.

Edit: there is automatic backup software avaliable on ubuntu, its called deja dup works well I find.

---

### Post by Mark Phelps on 2011-10-08
Don't use FAT32.  Linux has been able to read/write NTFS drives for years now.  Use NTFS instead.

---

### Post by dcstar on 2011-10-08
> **Mark Phelps said:**
> Don't use FAT32.  Linux has been able to read/write NTFS drives for years now.  Use NTFS instead.
+1

Anyone "recommending" that FAT32 be used these days for anything but a basic USB boot drive should be bonked on the back of the head with something as thick as they are.

---

### Post by shresthanator on 2011-10-08
how do I use Gparted to format the hard drive? I dont see it under gparted?

---

### Post by jazzon on 2011-10-08
Look in System -> Administration for gparted.  If its not there use synaptic (also found there) to install it, or from a terminal (also called command line) enter:
```
sudo apt-get install gparted
```
Once the install is finished gparted should be available as described  above.

Make sure you are working on the correct drive when you use gparted.  Using it on the wrong one could cause irreversible data loss.  The steps you are taking are the linux equivalent of formatting a drive under windows.

Waiot...just re read you post....

You dont see the drive under gparted?

Is it usb, and is it plugged in?

Also plug it in and then boot, sometimes a non formatted usb wont show up unless its there at boot time.

---

### Post by shresthanator on 2011-10-08
> **jazzon said:**
> Look in System -> Administration for gparted.  If its not there use synaptic (also found there) to install it, or from a terminal (also called command line) enter:
```
sudo apt-get install gparted
```
Once the install is finished gparted should be available as described  above.

Make sure you are working on the correct drive when you use gparted.  Using it on the wrong one could cause irreversible data loss.  The steps you are taking are the linux equivalent of formatting a drive under windows.

Waiot...just re read you post....

You dont see the drive under gparted?

Is it usb, and is it plugged in?

Also plug it in and then boot, sometimes a non formatted usb wont show up unless its there at boot time.


I guess I should have elaborated. It is a external USB 2 harddrive. It is plugged in and it requires the password to get in. I had already set the password and everything. It came with software & driver I had to install when I plugged it into windows. When I try to use it when I boot into Ubuntu, I can see it but I cant get into it (because I guess of the password protection). The name of the software that was on it is like "WD smartware" it automatically detected the picture, video, doucment files on my windows and asked me if I wanted to back it up.

I just want to be able to use this hard drive on both ubuntu & windows. I guess I have to somehow reformat the hard drive in NTFS. But I just dont know how I can do this. I have tried plugging it into windows, putting in the password, and right clicking and reformatting the drive, but I don't think that is working because the progress bar is not moving? Is there a quicker way to do this?

---

### Post by jazzon on 2011-10-08
SOME secured drives wont work under linux because there is a hidden partition on it for the security features, and the software on this partition is windows only.

Ill get back to you in about 5 min. gotta look up some stuff I haven't done in a long time to help with this.

---

### Post by jazzon on 2011-10-08
ok.

For starters from a terminal execute this:
```
dmesg | grep usb
```
and then this 
```
dmesg | grep sd
```
post the output from both here.

These commands scan your boot time messages for evidence of this drive.  Note this wont work unless you boot the computer while this drive is on and plugged in, so a reboot may be in order first.  If a reboot hangs you computer, unplug the drive till bios is done and the grub screen is visible, then plug it in and finish booting.

---

### Post by shresthanator on 2011-10-08
> **jazzon said:**
> ok.

For starters from a terminal execute this:
```
dmesg | grep usb
```
and then this 
```
dmesg | grep sd
```
post the output from both here.

These commands scan your boot time messages for evidence of this drive.  Note this wont work unless you boot the computer while this drive is on and plugged in, so a reboot may be in order first.  If a reboot hangs you computer, unplug the drive till bios is done and the grub screen is visible, then plug it in and finish booting.

thank you for trying to help me out. I rebooted my computer and this is what I get: 

[    0.196399] usbcore: registered new interface driver usbfs
[    0.196407] usbcore: registered new interface driver hub
[    0.196426] usbcore: registered new device driver usb
[    0.992010] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.348010] usb 2-4: new high speed USB device using ehci_hcd and address 3
[    1.720022] usb 4-1: new low speed USB device using uhci_hcd and address 2
[    1.720883] usbcore: registered new interface driver uas
[    1.944090] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input2
[    1.944160] generic-usb 0003:046D:C316.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:1a.1-1/input0
[    1.974594] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.1/input/input3
[    1.974666] generic-usb 0003:046D:C316.0002: input,hidraw1: USB HID v1.10 Device [Logitech Logitech USB Keyboard] on usb-0000:00:1a.1-1/input1
[    1.974677] usbcore: registered new interface driver usbhid
[    1.974678] usbhid: USB HID core driver
[    2.051286] scsi6 : usb-storage 1-1:1.0
[    2.051365] usbcore: registered new interface driver usb-storage
[    2.144011] usb 6-2: new low speed USB device using uhci_hcd and address 2
[    2.329081] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0/input/input4
[    2.329181] generic-usb 0003:1BCF:0007.0003: input,hiddev0,hidraw2: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:1d.0-2/input0
[   14.755730] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x03F0 pid 0x8911
[   14.755980] usbcore: registered new interface driver usblp
[   23.457113] usb 2-4: usbfs: interface 1 claimed by usblp while 'usb' sets config #1

--------------------------------------------------------------
and the output of the second one was very long :

[    1.553930] sd 0:0:1:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.553935] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    1.553969] sd 0:0:1:0: [sda] Write Protect is off
[    1.553971] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[    1.553988] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.554109] sd 1:0:0:0: Attached scsi generic sg2 type 0
[    1.554154] sd 1:0:0:0: [sdb] 321672960 512-byte logical blocks: (164 GB/153 GiB)
[    1.554233] sd 1:0:0:0: [sdb] Write Protect is off
[    1.554235] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.554253] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.572682]  sdb: sdb1 sdb2
[    1.572858] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.607662]  sda: sda1 sda2 < sda5 sda6 >
[    1.607910] sd 0:0:1:0: [sda] Attached SCSI disk
[    1.982241] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    3.054466] sd 6:0:0:0: Attached scsi generic sg3 type 0
[    3.058067] sd 6:0:0:0: [sdc] Unit Not Ready
[    3.058070] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[    3.058074] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[    3.059397] sd 6:0:0:0: [sdc] 1952151552 512-byte logical blocks: (999 GB/930 GiB)
[    3.061322] sd 6:0:0:0: [sdc] Write Protect is off
[    3.061325] sd 6:0:0:0: [sdc] Mode Sense: 2b 00 10 08
[    3.061327] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[    3.063134] sd 6:0:0:0: [sdc] Unit Not Ready
[    3.063136] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[    3.063140] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[    3.065545] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[    3.066390] sd 6:0:0:0: [sdc] Unhandled sense code
[    3.066392] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    3.066396] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[    3.066400] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[    3.066405] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[    3.066415] end_request: I/O error, dev sdc, sector 0
[    3.066418] Buffer I/O error on device sdc, logical block 0
[    3.067232] sd 6:0:0:0: [sdc] Unhandled sense code
[    3.067234] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    3.067238] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[    3.067242] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[    3.067247] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[    3.067256] end_request: I/O error, dev sdc, sector 0
[    3.067258] Buffer I/O error on device sdc, logical block 0
[    3.068080] sd 6:0:0:0: [sdc] Unhandled sense code
[    3.068082] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    3.068085] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[    3.068089] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[    3.068094] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[    3.068103] end_request: I/O error, dev sdc, sector 0
[    3.068105] Buffer I/O error on device sdc, logical block 0
[    3.068921] sd 6:0:0:0: [sdc] Unhandled sense code
[    3.068924] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    3.068927] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[    3.068930] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[    3.068936] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[    3.068944] end_request: I/O error, dev sdc, sector 0
[    3.068946] Buffer I/O error on device sdc, logical block 0
[    3.069768] sd 6:0:0:0: [sdc] Unhandled sense code
[    3.069770] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    3.069773] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[    3.069777] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[    3.069782] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[    3.069790] end_request: I/O error, dev sdc, sector 0
[    3.069792] Buffer I/O error on device sdc, logical block 0
[    3.070610] sd 6:0:0:0: [sdc] Unhandled sense code
[    3.070612] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    3.070615] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[    3.070619] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[    3.070624] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[    3.070632] end_request: I/O error, dev sdc, sector 0
[    3.070634] Buffer I/O error on device sdc, logical block 0
[    3.071454] sd 6:0:0:0: [sdc] Unhandled sense code
[    3.071457] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    3.071460] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[    3.071463] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[    3.071469] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[    3.071477] end_request: I/O error, dev sdc, sector 0
[    3.071479] Buffer I/O error on device sdc, logical block 0
[    3.072303] sd 6:0:0:0: [sdc] Unhandled sense code
[    3.072305] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    3.072309] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[    3.072313] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[    3.072318] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[    3.072327] end_request: I/O error, dev sdc, sector 0
[    3.072329] Buffer I/O error on device sdc, logical block 0
[    3.073145] sd 6:0:0:0: [sdc] Unhandled sense code
[    3.073148] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    3.073151] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[    3.073154] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[    3.073160] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[    3.073168] end_request: I/O error, dev sdc, sector 0
[    3.073170] Buffer I/O error on device sdc, logical block 0
[    3.073176] Dev sdc: unable to read RDB block 0
[    3.073991] sd 6:0:0:0: [sdc] Unhandled sense code
[    3.073994] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    3.073997] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[    3.074001] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[    3.074006] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[    3.074014] end_request: I/O error, dev sdc, sector 0
[    3.074834] sd 6:0:0:0: [sdc] Unhandled sense code
[    3.074837] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    3.074840] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[    3.074843] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[    3.074848] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[    3.074857] end_request: I/O error, dev sdc, sector 0
[    3.075681] sd 6:0:0:0: [sdc] Unhandled sense code
[    3.075683] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    3.075686] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[    3.075690] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[    3.075695] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
[    3.075703] end_request: I/O error, dev sdc, sector 24
[    3.076524] sd 6:0:0:0: [sdc] Unhandled sense code
[    3.076526] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    3.076529] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[    3.076533] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[    3.076538] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
[    3.076547] end_request: I/O error, dev sdc, sector 24
[    3.077371] sd 6:0:0:0: [sdc] Unhandled sense code
[    3.077374] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    3.077377] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[    3.077381] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[    3.077386] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[    3.077394] end_request: I/O error, dev sdc, sector 0
[    3.078213] sd 6:0:0:0: [sdc] Unhandled sense code
[    3.078215] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    3.078219] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[    3.078222] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[    3.078227] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[    3.078236] end_request: I/O error, dev sdc, sector 0
[    3.078242]  sdc: unable to read partition table
[    3.080752] sd 6:0:0:0: [sdc] Unit Not Ready
[    3.080754] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[    3.080758] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[    3.083165] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[    3.083168] sd 6:0:0:0: [sdc] Attached SCSI disk
[   14.408812] Adding 7812092k swap on /dev/sda5.  Priority:-1 extents:1 across:7812092k 
[   14.654048] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.654050] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.654053] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.654056] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.654060] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.654066] end_request: I/O error, dev sdc, sector 0
[   14.654069] Buffer I/O error on device sdc, logical block 0
[   14.655364] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.655366] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.655368] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.655371] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.655374] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.655380] end_request: I/O error, dev sdc, sector 0
[   14.655381] Buffer I/O error on device sdc, logical block 0
[   14.656219] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.656221] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.656223] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.656226] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.656229] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.656235] end_request: I/O error, dev sdc, sector 0
[   14.656236] Buffer I/O error on device sdc, logical block 0
[   14.657781] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.657783] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.657785] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.657788] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.657791] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.657797] end_request: I/O error, dev sdc, sector 0
[   14.657798] Buffer I/O error on device sdc, logical block 0
[   14.658626] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.658628] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.658630] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.658633] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.658636] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.658642] end_request: I/O error, dev sdc, sector 0
[   14.658643] Buffer I/O error on device sdc, logical block 0
[   14.659465] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.659467] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.659469] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.659472] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.659475] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.659480] end_request: I/O error, dev sdc, sector 0
[   14.659482] Buffer I/O error on device sdc, logical block 0
[   14.663863] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.663865] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.663867] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.663870] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.663874] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.663879] end_request: I/O error, dev sdc, sector 0
[   14.663881] Buffer I/O error on device sdc, logical block 0
[   14.664735] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.664737] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.664739] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.664741] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.664745] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.664750] end_request: I/O error, dev sdc, sector 0
[   14.666108] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.666110] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.666113] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.666115] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.666118] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.666124] end_request: I/O error, dev sdc, sector 0
[   14.666950] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.666952] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.666954] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.666957] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.666960] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.666966] end_request: I/O error, dev sdc, sector 0
[   14.667792] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.667793] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.667796] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.667798] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.667801] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[   14.667807] end_request: I/O error, dev sdc, sector 56
[   14.668661] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.668663] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.668665] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.668668] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.668671] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.668677] end_request: I/O error, dev sdc, sector 0
[   14.669487] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.669489] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.669491] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.669494] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.669497] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.669503] end_request: I/O error, dev sdc, sector 0
[   14.670455] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.670457] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.670459] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.670461] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.670465] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 74 5b 77 80 00 00 08 00
[   14.670471] end_request: I/O error, dev sdc, sector 1952151424
[   14.671655] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.671657] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.671660] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.671662] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.671666] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 74 5b 77 f0 00 00 08 00
[   14.671671] end_request: I/O error, dev sdc, sector 1952151536
[   14.672756] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.672758] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.672760] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.672762] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.672766] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.672771] end_request: I/O error, dev sdc, sector 0
[   14.677213] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.677215] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.677218] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.677220] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.677224] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[   14.677230] end_request: I/O error, dev sdc, sector 8
[   14.678053] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.678055] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.678057] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.678059] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.678063] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 74 5b 77 f8 00 00 01 00
[   14.678069] end_request: I/O error, dev sdc, sector 1952151544
[   14.678946] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.678948] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.678950] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.678953] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.678956] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 74 5b 77 f8 00 00 01 00
[   14.678962] end_request: I/O error, dev sdc, sector 1952151544
[   14.681560] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.681562] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.681564] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.681566] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.681570] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 74 5b 77 f8 00 00 01 00
[   14.681576] end_request: I/O error, dev sdc, sector 1952151544
[   14.682418] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.682420] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.682422] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.682424] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.682428] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 74 5b 77 f8 00 00 01 00
[   14.682433] end_request: I/O error, dev sdc, sector 1952151544
[   14.683249] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.683251] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.683253] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.683255] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.683259] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 74 5b 77 f8 00 00 01 00
[   14.683264] end_request: I/O error, dev sdc, sector 1952151544
[   14.684094] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.684096] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.684098] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.684100] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.684104] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 74 5b 77 f8 00 00 01 00
[   14.684110] end_request: I/O error, dev sdc, sector 1952151544
[   14.684961] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.684962] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.684965] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.684967] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.684970] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 74 5b 77 c0 00 00 08 00
[   14.684976] end_request: I/O error, dev sdc, sector 1952151488
[   14.685787] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.685789] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.685791] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.685793] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.685797] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 74 5b 77 f0 00 00 08 00
[   14.685802] end_request: I/O error, dev sdc, sector 1952151536
[   14.687475] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.687477] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.687479] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.687482] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.687486] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[   14.687491] end_request: I/O error, dev sdc, sector 8
[   14.688325] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.688327] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.688329] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.688331] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.688334] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[   14.688340] end_request: I/O error, dev sdc, sector 8
[   14.690097] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.690099] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.690101] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.690103] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.690107] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 74 5b 77 f8 00 00 01 00
[   14.690113] end_request: I/O error, dev sdc, sector 1952151544
[   14.691085] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.691087] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.691089] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.691091] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.691095] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 74 5b 77 f8 00 00 01 00
[   14.691100] end_request: I/O error, dev sdc, sector 1952151544
[   14.691949] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.691951] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.691953] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.691955] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.691959] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 74 5b 77 f8 00 00 01 00
[   14.691964] end_request: I/O error, dev sdc, sector 1952151544
[   14.693029] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.693031] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.693033] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.693036] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.693039] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.693045] end_request: I/O error, dev sdc, sector 0
[   14.694242] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.694243] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.694246] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.694300] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.694303] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.694309] end_request: I/O error, dev sdc, sector 0
[   14.695309] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.695311] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.695313] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.695315] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.695319] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.695325] end_request: I/O error, dev sdc, sector 0
[   14.697844] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.697845] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.697848] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.697850] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.697854] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.697859] end_request: I/O error, dev sdc, sector 0
[   14.698926] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.698928] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.698930] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.698933] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.698936] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.698942] end_request: I/O error, dev sdc, sector 0
[   14.700044] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.700045] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.700047] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.700050] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.700054] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.700059] end_request: I/O error, dev sdc, sector 0
[   14.701709] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.701711] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.701713] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.701715] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.701719] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.701724] end_request: I/O error, dev sdc, sector 0
[   14.703514] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.703516] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.703518] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.703521] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.703524] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 08 00 00 00 08 00
[   14.703530] end_request: I/O error, dev sdc, sector 2048
[   14.705332] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.705334] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.705336] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.705338] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.705342] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.705347] end_request: I/O error, dev sdc, sector 0
[   14.706530] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.706532] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.706534] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.706536] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.706540] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.706545] end_request: I/O error, dev sdc, sector 0
[   14.708314] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.708316] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.708318] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.708320] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.708324] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.708330] end_request: I/O error, dev sdc, sector 0
[   14.713411] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.713413] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.713415] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.713417] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.713421] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.713427] end_request: I/O error, dev sdc, sector 0
[   14.716106] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.716107] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.716110] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.716112] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.716116] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.716122] end_request: I/O error, dev sdc, sector 0
[   14.717757] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.717759] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.717761] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.717764] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.717768] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.717773] end_request: I/O error, dev sdc, sector 0
[   14.719441] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.719443] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.719445] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.719448] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.719451] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.719457] end_request: I/O error, dev sdc, sector 0
[   14.721136] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.721138] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.721141] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.721143] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.721147] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.721152] end_request: I/O error, dev sdc, sector 0
[   14.723119] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.723121] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.723123] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.723125] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.723129] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.723135] end_request: I/O error, dev sdc, sector 0
[   14.724033] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.724035] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.724037] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.724039] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.724043] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.724048] end_request: I/O error, dev sdc, sector 0
[   14.725118] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.725120] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.725123] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.725125] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.725128] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.725134] end_request: I/O error, dev sdc, sector 0
[   14.725958] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.725960] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.725962] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.725965] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.725968] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.725974] end_request: I/O error, dev sdc, sector 0
[   14.726805] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.726806] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.726808] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.726811] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.726814] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[   14.726820] end_request: I/O error, dev sdc, sector 8
[   14.727643] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.727645] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.727647] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.727649] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.727653] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[   14.727658] end_request: I/O error, dev sdc, sector 8
[   14.728499] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.728501] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.728503] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.728505] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.728509] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[   14.728514] end_request: I/O error, dev sdc, sector 8
[   14.729341] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.729342] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.729344] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.729347] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.729350] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[   14.729356] end_request: I/O error, dev sdc, sector 8
[   14.730199] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.730201] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.730203] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.730205] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.730209] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
[   14.730214] end_request: I/O error, dev sdc, sector 24
[   14.731032] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.731034] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.731036] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.731038] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.731041] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
[   14.731047] end_request: I/O error, dev sdc, sector 24
[   14.731873] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.731875] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.731877] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.731879] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.731883] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
[   14.731888] end_request: I/O error, dev sdc, sector 24
[   14.732721] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.732722] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.732724] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.732727] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.732730] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
[   14.732735] end_request: I/O error, dev sdc, sector 24
[   14.733563] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.733564] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.733566] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.733569] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.733572] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[   14.733577] end_request: I/O error, dev sdc, sector 56
[   14.734428] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.734430] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.734432] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.734434] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.734438] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[   14.734443] end_request: I/O error, dev sdc, sector 56
[   14.735267] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.735268] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.735270] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.735273] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.735276] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[   14.735281] end_request: I/O error, dev sdc, sector 56
[   14.736585] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.736587] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.736589] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.736591] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.736595] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[   14.736600] end_request: I/O error, dev sdc, sector 56
[   14.737425] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.737426] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.737437] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.737439] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.737442] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
[   14.737448] end_request: I/O error, dev sdc, sector 120
[   14.738270] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.738271] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.738273] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.738276] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.738279] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
[   14.738284] end_request: I/O error, dev sdc, sector 120
[   14.739116] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.739117] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.739119] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.739122] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.739125] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
[   14.739130] end_request: I/O error, dev sdc, sector 120
[   14.739958] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.739960] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.739962] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.739964] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.739967] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
[   14.739973] end_request: I/O error, dev sdc, sector 120
[   14.740806] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.740807] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.740809] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.740812] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.740815] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.740820] end_request: I/O error, dev sdc, sector 0
[   14.741648] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.741650] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.741651] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.741654] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.741657] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.741662] end_request: I/O error, dev sdc, sector 0
[   14.742495] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.742497] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.742499] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.742501] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.742504] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[   14.742510] end_request: I/O error, dev sdc, sector 8
[   14.743343] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.743345] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.743347] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.743349] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.743352] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[   14.743358] end_request: I/O error, dev sdc, sector 8
[   14.744184] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.744186] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.744188] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.744190] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.744194] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
[   14.744199] end_request: I/O error, dev sdc, sector 24
[   14.745029] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.745031] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.745033] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.745036] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.745039] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
[   14.745045] end_request: I/O error, dev sdc, sector 24
[   14.745993] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.745995] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.745997] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.745999] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.746003] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[   14.746009] end_request: I/O error, dev sdc, sector 56
[   14.746839] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.746841] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.746843] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.746845] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.746848] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[   14.746854] end_request: I/O error, dev sdc, sector 56
[   14.747681] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.747683] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.747685] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.747687] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.747690] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
[   14.747696] end_request: I/O error, dev sdc, sector 120
[   14.748528] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.748530] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.748532] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.748534] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.748537] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
[   14.748543] end_request: I/O error, dev sdc, sector 120
[   14.749371] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.749373] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.749375] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.749377] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.749381] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.749386] end_request: I/O error, dev sdc, sector 0
[   14.750213] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.750215] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.750217] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.750220] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.750223] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.750229] end_request: I/O error, dev sdc, sector 0
[   14.751057] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.751059] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.751061] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.751064] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.751067] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.751073] end_request: I/O error, dev sdc, sector 0
[   14.751906] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.751908] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.751911] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.751913] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.751917] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.751922] end_request: I/O error, dev sdc, sector 0
[   14.753114] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.753116] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.753119] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.753121] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.753124] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.753130] end_request: I/O error, dev sdc, sector 0
[   14.753956] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.753957] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.753959] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.753961] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.753965] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.753970] end_request: I/O error, dev sdc, sector 0
[   14.754885] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.754887] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.754889] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.754892] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.754895] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
[   14.754901] end_request: I/O error, dev sdc, sector 16
[   14.755768] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.755770] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.755772] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.755775] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.755779] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[   14.755784] end_request: I/O error, dev sdc, sector 128
[   14.756613] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.756615] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.756617] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.756620] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.756623] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[   14.756629] end_request: I/O error, dev sdc, sector 128
[   14.757459] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.757461] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.757463] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.757466] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.757469] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[   14.757475] end_request: I/O error, dev sdc, sector 128
[   14.758425] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.758427] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.758429] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.758431] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.758434] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
[   14.758440] end_request: I/O error, dev sdc, sector 16
[   14.759267] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.759268] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.759271] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.759273] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.759277] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[   14.759282] end_request: I/O error, dev sdc, sector 128
[   14.760114] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.760116] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.760118] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.760120] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.760124] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   14.760129] end_request: I/O error, dev sdc, sector 64
[   14.760959] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.760961] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.760963] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.760965] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.760969] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   14.760974] end_request: I/O error, dev sdc, sector 64
[   14.762524] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.762526] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.762529] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.762531] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.762535] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   14.762541] end_request: I/O error, dev sdc, sector 64
[   14.763369] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.763371] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.763373] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.763375] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.763379] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   14.763384] end_request: I/O error, dev sdc, sector 64
[   14.764213] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.764215] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.764217] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.764219] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.764222] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   14.764228] end_request: I/O error, dev sdc, sector 64
[   14.765784] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.765786] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.765788] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.765791] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.765794] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   14.765800] end_request: I/O error, dev sdc, sector 64
[   14.766990] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.766992] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.766994] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.766996] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.767000] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   14.767006] end_request: I/O error, dev sdc, sector 64
[   14.767839] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.767842] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.767845] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.767850] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.767855] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   14.767864] end_request: I/O error, dev sdc, sector 64
[   14.768686] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.768690] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.768693] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.768697] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.768703] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   14.768711] end_request: I/O error, dev sdc, sector 64
[   14.770375] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.770377] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.770380] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.770384] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.770389] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   14.770398] end_request: I/O error, dev sdc, sector 64
[   14.771459] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.771461] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.771465] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.771469] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.771474] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 01 00 00 00 08 00
[   14.771483] end_request: I/O error, dev sdc, sector 256
[   14.772545] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.772547] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.772551] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.772554] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.772560] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 01 00 00 00 08 00
[   14.772568] end_request: I/O error, dev sdc, sector 256
[   14.773633] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.773635] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.773639] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.773642] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.773647] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 01 08 00 00 08 00
[   14.773656] end_request: I/O error, dev sdc, sector 264
[   14.775320] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.775322] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.775325] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.775329] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.775334] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 01 08 00 00 08 00
[   14.775342] end_request: I/O error, dev sdc, sector 264
[   14.777133] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.777135] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.777138] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.777142] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.777147] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 01 10 00 00 08 00
[   14.777156] end_request: I/O error, dev sdc, sector 272
[   14.778822] sd 6:0:0:0: [sdc] Unhandled sense code
[   14.778824] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.778828] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   14.778832] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   14.778837] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 01 10 00 00 08 00
[   14.778845] end_request: I/O error, dev sdc, sector 272
[   14.975950] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,user_xattr
[   19.901397] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[   21.645580] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.645583] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.645587] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.645592] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.645598] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 03 00 00 00 08 00
[   21.645608] end_request: I/O error, dev sdc, sector 768
[   21.645614] Buffer I/O error on device sdc, logical block 96
[   21.647867] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.647870] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.647873] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.647877] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.647882] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 03 00 00 00 08 00
[   21.647892] end_request: I/O error, dev sdc, sector 768
[   21.647894] Buffer I/O error on device sdc, logical block 96
[   21.650161] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.650164] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.650167] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.650171] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.650177] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 03 08 00 00 08 00
[   21.650185] end_request: I/O error, dev sdc, sector 776
[   21.650188] Buffer I/O error on device sdc, logical block 97
[   21.652331] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.652334] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.652338] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.652342] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.652347] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 03 08 00 00 08 00
[   21.652356] end_request: I/O error, dev sdc, sector 776
[   21.652358] Buffer I/O error on device sdc, logical block 97
[   21.654626] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.654628] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.654632] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.654636] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.654641] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 03 10 00 00 08 00
[   21.654650] end_request: I/O error, dev sdc, sector 784
[   21.654652] Buffer I/O error on device sdc, logical block 98
[   21.656798] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.656801] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.656805] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.656809] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.656814] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 03 10 00 00 08 00
[   21.656823] end_request: I/O error, dev sdc, sector 784
[   21.656825] Buffer I/O error on device sdc, logical block 98
[   21.658968] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.658971] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.658974] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.658978] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.658983] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   21.658992] end_request: I/O error, dev sdc, sector 0
[   21.658994] Buffer I/O error on device sdc, logical block 0
[   21.661263] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.661266] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.661269] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.661273] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.661278] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   21.661287] end_request: I/O error, dev sdc, sector 0
[   21.661289] Buffer I/O error on device sdc, logical block 0
[   21.667414] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.667417] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.667421] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.667424] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.667430] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   21.667438] end_request: I/O error, dev sdc, sector 0
[   21.667441] Buffer I/O error on device sdc, logical block 0
[   21.669587] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.669590] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.669593] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.669597] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.669602] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   21.669611] end_request: I/O error, dev sdc, sector 0
[   21.669614] Buffer I/O error on device sdc, logical block 0
[   21.671879] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.671882] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.671885] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.671889] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.671894] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   21.671902] end_request: I/O error, dev sdc, sector 0
[   21.679121] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.679124] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.679127] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.679131] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.679137] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
[   21.679146] end_request: I/O error, dev sdc, sector 16
[   21.680449] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.680452] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.680455] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.680459] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.680464] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   21.680473] end_request: I/O error, dev sdc, sector 0
[   21.681774] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.681776] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.681780] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.681783] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.681789] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   21.681797] end_request: I/O error, dev sdc, sector 0
[   21.683222] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.683224] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.683228] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.683231] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.683237] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   21.683245] end_request: I/O error, dev sdc, sector 0
[   21.684555] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.684557] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.684560] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.684564] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.684570] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   21.684578] end_request: I/O error, dev sdc, sector 0
[   21.685876] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.685879] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.685882] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.685886] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.685891] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   21.685899] end_request: I/O error, dev sdc, sector 0
[   21.688291] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.688293] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.688296] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.688300] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.688305] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   21.688314] end_request: I/O error, dev sdc, sector 0
[   21.689981] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.689984] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.689987] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.689991] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.689996] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   21.690004] end_request: I/O error, dev sdc, sector 0
[   21.691183] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.691185] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.691187] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.691189] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.691192] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   21.691198] end_request: I/O error, dev sdc, sector 0
[   21.692073] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.692075] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.692077] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.692080] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.692083] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   21.692089] end_request: I/O error, dev sdc, sector 0
[   21.693113] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.693114] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.693116] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.693118] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.693122] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   21.693127] end_request: I/O error, dev sdc, sector 0
[   21.693955] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.693957] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.693959] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.693961] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.693964] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   21.693970] end_request: I/O error, dev sdc, sector 0
[   21.694802] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.694803] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.694805] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.694808] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.694811] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   21.694816] end_request: I/O error, dev sdc, sector 0
[   21.695652] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.695655] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.695658] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.695662] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.695668] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[   21.695677] end_request: I/O error, dev sdc, sector 128
[   21.697702] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.697705] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.697708] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.697712] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.697717] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[   21.697726] end_request: I/O error, dev sdc, sector 128
[   21.698791] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.698793] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.698796] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.698800] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.698805] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
[   21.698814] end_request: I/O error, dev sdc, sector 16
[   21.699874] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.699877] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.699880] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.699884] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.699889] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   21.699897] end_request: I/O error, dev sdc, sector 0
[   21.700960] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.700962] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.700966] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.700969] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.700974] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   21.700983] end_request: I/O error, dev sdc, sector 0
[   21.702649] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.702652] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.702655] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.702658] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.702664] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[   21.702672] end_request: I/O error, dev sdc, sector 8
[   21.704462] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.704465] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.704468] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.704471] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.704477] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
[   21.704485] end_request: I/O error, dev sdc, sector 16
[   21.706151] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.706154] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.706157] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.706161] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.706166] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   21.706174] end_request: I/O error, dev sdc, sector 0
[   21.708925] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.708927] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.708931] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.708934] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.708939] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   21.708948] end_request: I/O error, dev sdc, sector 0
[   21.710252] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.710254] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.710257] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.710261] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.710266] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   21.710275] end_request: I/O error, dev sdc, sector 0
[   21.711940] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.711943] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.711946] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.711950] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.711955] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   21.711964] end_request: I/O error, dev sdc, sector 0
[   21.713031] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.713034] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.713038] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.713042] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.713047] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   21.713056] end_request: I/O error, dev sdc, sector 0
[   21.713871] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.713874] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.713877] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.713881] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.713886] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   21.713894] end_request: I/O error, dev sdc, sector 0
[   21.714720] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.714723] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.714726] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.714730] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.714735] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[   21.714744] end_request: I/O error, dev sdc, sector 8
[   21.715561] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.715563] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.715566] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.715570] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.715575] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[   21.715584] end_request: I/O error, dev sdc, sector 128
[   21.716527] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.716530] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.716533] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.716537] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.716542] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   21.716551] end_request: I/O error, dev sdc, sector 0
[   21.717373] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.717376] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.717379] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.717383] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.717388] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   21.717397] end_request: I/O error, dev sdc, sector 0
[   21.718215] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.718218] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.718221] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.718225] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.718230] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 10 00 00 00 08 00
[   21.718239] end_request: I/O error, dev sdc, sector 4096
[   21.723650] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.723653] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.723656] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.723660] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.723666] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   21.723675] end_request: I/O error, dev sdc, sector 0
[   21.724492] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.724495] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.724498] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.724502] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.724508] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   21.724516] end_request: I/O error, dev sdc, sector 0
[   21.725338] sd 6:0:0:0: [sdc] Unhandled sense code
[   21.725340] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   21.725343] sd 6:0:0:0: [sdc]  Sense Key : Data Protect [current] 
[   21.725347] sd 6:0:0:0: [sdc]  Add. Sense: Logical unit access not authorized
[   21.725353] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   21.725361] end_request: I/O error, dev sdc, sector 0
[   25.734712] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0

---

### Post by jazzon on 2011-10-08
beemac....did that land in the right forum?

---

### Post by legodude3301 on 2011-10-08
As far as i know, western digital is basically strictly windows compatible. I might be wrong, but I'm of no help either way except to say good luck!

---

### Post by jazzon on 2011-10-08
ok


the lines that look like ;
```
   21.650185] end_request: I/O error, dev sdc, sector 776
```
are happening after the drive tries to access access one of the blocks used by the encryption setup.  Western Dig externals are not linux friendly but they can be made to work, it just isnt easy the first time.

One) are you in a standard Ubuntu install (no VMWare or WUBI) (not running linux inside windows)

Two) execute ```
fdisk -l
```
and post output  (note thats lower case L not a 1 or an I)

---

### Post by Jerry N on 2011-10-08
> **jazzon said:**
>   Western Dig externals are not linux friendly but they can be made to work, it just isnt easy the first time.

I have had no trouble at all with Western Digital external drives in linux.  The first thing I do is throw away any CDs that came with the drive and the second thing is format the drive to NTFS using Windows.  In my experience, both Windows (XP and 7) and linux (Ubuntu, Linux Mint) read and write to the drive just fine.

Jerry

---

### Post by jazzon on 2011-10-08
@ jerry

Usually true, but he already installed the proprietary stuff under win.  Sometimes that flashes the firmware (hope it didn't here), and the password protected/encrypted ones can have strange hidden partitions on them that need to be gotten rid of. 

Bought 8gb flash drives for my kids for school, and they all had hidden crap on em.  Took a while to get them to mount with partitions visible so I could remove the stuff.

---

### Post by dcstar on 2011-10-09
> **jazzon said:**
> @ jerry

Usually true, but he already installed the proprietary stuff under win.  Sometimes that flashes the firmware (hope it didn't here), and the password protected/encrypted ones can have strange hidden partitions on them that need to be gotten rid of. 
......

Best to use gparted to write a new partition table to these devices, the propriety junk that comes with them can be pretty evil sometimes.

---

### Post by LinuxFan999 on 2011-10-09
> **jazzon said:**
> @ jerry
 
Usually true, but he already installed the proprietary stuff under win. Sometimes that flashes the firmware (hope it didn't here), and the password protected/encrypted ones can have strange hidden partitions on them that need to be gotten rid of. 
 
**Bought 8gb flash drives for my kids for school, and they all had hidden crap on em. Took a while to get them to mount with** **partitions visible so I could** **remove the stuff**.
That reminds me of those Sandisk flash drives which came with that U3 thing which is very difficult to remove. It's a good thing that they no longer come with it.

---

### Post by Jerry N on 2011-10-09
> **LinuxFan999 said:**
> That reminds me of those Sandisk flash drives which came with that U3 thing which is very difficult to remove. It's a good thing that they no longer come with it.

I didn't know Sandisk had quit putting that U3 crap on the flash drives but I am glad to hear it.  They also came with a Windows utility that would allow quick and easy removal of the U3 junk and allow use of the whole flash drive, which of course doesn't help if you use linux exclusively.

Jerry

---

### Post by duracella on 2011-11-02
Seems like I have the same problem, except it has been working perfectly for like two weeks, until two days ago....

read my thread here: [http://ubuntuforums.org/showthread.php?t=1874026](http://ubuntuforums.org/showthread.php?t=1874026)

Hope anyone of you can help me... some of the information i posted from typing; lsusb , might be helpful to figure out the problem...

---

### Post by pqwoerituytrueiwoq on 2011-11-02
if it is a new hdd (i think they pre-format external drives if it is disregard this)
you will need to create the partition table
**MAKE SURE YOU HAVE THE CORRECT DRIVE SELECTED** (top right in gparted) **OR THIS WILL GET REAL BAD REAL FAST**
device -> new partition table
then you can create your partition(s)

---

