---
title: "Thunar volume management - how to reconfigure?"
date: 2009-10-19
forum: General Help
---

### Post by GeneralSpecific on 2009-10-19
Dell Optiplex GX260
Running Xubuntu Jaunty.
Fluxbox WM
Thunar for file management and mounting/unmounting drives and removeable media

I am having problems writing to my [COLOR="Blue"]Sansa C250 MP3 player[/COLOR].  
It mounts using MTP as "2GB removable media".

[INDENT]It was _previously working great_, but now when I try to write to the drive
it will usually only get about 30% of the way copied and then **freeze up**.
This happens if I am copying a single file or an entire folder.
Every once in a while it will copy the entire file, but rarely. 
And even then it will now allow me to unmount, saying it is still in use.

It seems to read ok, but the problem is when I try to write to the device.

The same thing happens when I use Thunar to mount the drive and then
try to copy with **Gnome-commander**, or from the **command line**[/INDENT].

I can usually cancel the action, though sometimes Thunar locks up.

Thunar works fine with all my other removable devices (cdroms/SD cards/etc)
[SIZE="4"]
I would like to know how to _reset/reconfigure thunar volume management_ 
to hopefully get rid of whatever bug is causing this problem.[/SIZE]

I have tried reinstalling Thunar and Thunar-volman with synaptic.
I also tried "dpkg-reconfigre thunar"

It hasn't helped.

[INDENT]I am wondering if my **other problem** I am working on:

[http://ubuntuforums.org/showthread.php?p=8085630#post8085630]("http://ubuntuforums.org/showthread.php?p=8085630#post8085630")


maybe caused this.  I may have had my Player plugged in and Thunar running 
one time I forced my computer to go to sleep (etc/acpi/sleep.sh)[/INDENT]


I am grateful for any help I can get.

-Ryan

---

### Post by GeneralSpecific on 2009-10-22
I hate posting my own reply...but I'm still working on this-

Here is what my .[COLOR="Blue"]xsession-errors[/COLOR] file says when I plug in my mp3 player, try to copy something(fail), cancel it, try(fail) to eject it, unplug it, and close thunar:

[PHP]thunar-volman: No property info.capabilities on device with id /org/freedesktop/Hal/devices/usb_device_781_7452_FD0FCC097638B49F0000000000000000_if0.
thunar-volman: No property info.capabilities on device with id /org/freedesktop/Hal/devices/usb_device_781_7452_FD0FCC097638B49F0000000000000000.
thunar-volman: No property info.capabilities on device with id /org/freedesktop/Hal/devices/usb_device_781_7452_FD0FCC097638B49F0000000000000000_if0_scsi_host_0_scsi_device_lun0.
thunar-volman: No property info.capabilities on device with id /org/freedesktop/Hal/devices/usb_device_781_7452_FD0FCC097638B49F0000000000000000_if0_scsi_host_0_scsi_device_lun1.
**
thunar-vfs:ERROR:thunar-vfs-path.c:1201:_thunar_vfs_path_shutdown: assertion failed: (home_components[n]->ref_count == 1)
[/PHP]
Here is my [COLOR="Blue"]kern.log[/COLOR]:

[PHP]Oct 22 16:41:23 ryan-desktop kernel: [ 2318.692016] usb 1-4: new high speed USB device using ehci_hcd and address 9
Oct 22 16:41:25 ryan-desktop kernel: [ 2320.532288] hub 1-0:1.0: unable to enumerate USB device on port 4
Oct 22 16:41:25 ryan-desktop kernel: [ 2320.860019] usb 1-4: new high speed USB device using ehci_hcd and address 10
Oct 22 16:41:26 ryan-desktop kernel: [ 2321.015553] usb 1-4: configuration #1 chosen from 1 choice
Oct 22 16:41:26 ryan-desktop kernel: [ 2321.046230] scsi6 : SCSI emulation for USB Mass Storage devices
Oct 22 16:41:26 ryan-desktop kernel: [ 2321.052131] usb-storage: device found at 10
Oct 22 16:41:26 ryan-desktop kernel: [ 2321.052135] usb-storage: waiting for device to settle before scanning
Oct 22 16:41:31 ryan-desktop kernel: [ 2326.053767] usb-storage: device scan complete
Oct 22 16:41:31 ryan-desktop kernel: [ 2326.054974] scsi 6:0:0:0: Direct-Access     SanDisk  Sansa c250       v03. PQ: 0 ANSI: 0
Oct 22 16:41:31 ryan-desktop kernel: [ 2326.055714] scsi 6:0:0:1: Direct-Access     SanDisk  Sansa c250       v03. PQ: 0 ANSI: 0
Oct 22 16:41:31 ryan-desktop kernel: [ 2326.092269] sd 6:0:0:0: [sde] 3992576 512-byte hardware sectors: (2.04 GB/1.90 GiB)
Oct 22 16:41:31 ryan-desktop kernel: [ 2326.092969] sd 6:0:0:0: [sde] Write Protect is off
Oct 22 16:41:31 ryan-desktop kernel: [ 2326.092974] sd 6:0:0:0: [sde] Mode Sense: 04 00 00 00
Oct 22 16:41:31 ryan-desktop kernel: [ 2326.092977] sd 6:0:0:0: [sde] Assuming drive cache: write through
Oct 22 16:41:31 ryan-desktop kernel: [ 2326.095105] sd 6:0:0:0: [sde] 3992576 512-byte hardware sectors: (2.04 GB/1.90 GiB)
Oct 22 16:41:31 ryan-desktop kernel: [ 2326.096002] sd 6:0:0:0: [sde] Write Protect is off
Oct 22 16:41:31 ryan-desktop kernel: [ 2326.096041] sd 6:0:0:0: [sde] Mode Sense: 04 00 00 00
Oct 22 16:41:31 ryan-desktop kernel: [ 2326.096045] sd 6:0:0:0: [sde] Assuming drive cache: write through
Oct 22 16:41:31 ryan-desktop kernel: [ 2326.097431]  sde:
Oct 22 16:41:31 ryan-desktop kernel: [ 2326.099974] sd 6:0:0:0: [sde] Attached SCSI removable disk
Oct 22 16:41:31 ryan-desktop kernel: [ 2326.100639] sd 6:0:0:0: Attached scsi generic sg6 type 0
Oct 22 16:41:31 ryan-desktop kernel: [ 2326.103664] sd 6:0:0:1: [sdf] Attached SCSI removable disk
Oct 22 16:41:31 ryan-desktop kernel: [ 2326.103785] sd 6:0:0:1: Attached scsi generic sg7 type 0
Oct 22 16:42:28 ryan-desktop kernel: [ 2383.112023] usb 1-4: reset high speed USB device using ehci_hcd and address 10
Oct 22 16:42:59 ryan-desktop kernel: [ 2414.112024] usb 1-4: reset high speed USB device using ehci_hcd and address 10
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.672261] usb 1-4: USB disconnect, address 10
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.672427] sd 6:0:0:0: [sde] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.672434] end_request: I/O error, dev sde, sector 132489
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.676325] __ratelimit: 68 callbacks suppressed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.676325] Buffer I/O error on device sde, logical block 9
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.676325] lost page write due to I/O error on sde
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.676325] Buffer I/O error on device sde, logical block 10
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.676325] lost page write due to I/O error on sde
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.676325] Buffer I/O error on device sde, logical block 11
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.676325] lost page write due to I/O error on sde
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.676325] Buffer I/O error on device sde, logical block 253
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.676325] lost page write due to I/O error on sde
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.676325] Buffer I/O error on device sde, logical block 254
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.676325] lost page write due to I/O error on sde
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.676325] Buffer I/O error on device sde, logical block 255
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.676325] lost page write due to I/O error on sde
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.676325] Buffer I/O error on device sde, logical block 489
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.676325] lost page write due to I/O error on sde
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.676325] Buffer I/O error on device sde, logical block 490
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.676325] lost page write due to I/O error on sde
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.677722] sd 6:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.677728] end_request: I/O error, dev sde, sector 132729
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.684200] Buffer I/O error on device sde, logical block 713
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.684209] lost page write due to I/O error on sde
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.693087] VFS: busy inodes on changed media or resized disk sde
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.693779] Buffer I/O error on device sde, logical block 131465
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.693785] lost page write due to I/O error on sde
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.693869] sd 6:0:0:1: [sdf] READ CAPACITY failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.693872] sd 6:0:0:1: [sdf] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.693878] sd 6:0:0:1: [sdf] Sense not available.
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.693932] sd 6:0:0:1: [sdf] Write Protect is off
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.693936] sd 6:0:0:1: [sdf] Mode Sense: 00 00 00 00
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.693938] sd 6:0:0:1: [sdf] Assuming drive cache: write through
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.694009] sd 6:0:0:0: [sde] READ CAPACITY failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.694012] sd 6:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.694016] sd 6:0:0:0: [sde] Sense not available.
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.694045] sd 6:0:0:0: [sde] Write Protect is off
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.694049] sd 6:0:0:0: [sde] Mode Sense: 00 00 00 00
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.694051] sd 6:0:0:0: [sde] Assuming drive cache: write through
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.694277] VFS: busy inodes on changed media or resized disk sde
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.694298] sd 6:0:0:1: [sdf] READ CAPACITY failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.694301] sd 6:0:0:1: [sdf] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.694305] sd 6:0:0:1: [sdf] Sense not available.
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.694336] sd 6:0:0:1: [sdf] Write Protect is off
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.694339] sd 6:0:0:1: [sdf] Mode Sense: 00 00 00 00
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.694342] sd 6:0:0:1: [sdf] Assuming drive cache: write through
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.700420] FAT: FAT read failed (blocknr 11)
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.700460] FAT: FAT read failed (blocknr 11)
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.700865] FAT: Directory bread(block 131465) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.700875] FAT: Directory bread(block 131466) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.700884] FAT: Directory bread(block 131467) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.700893] FAT: Directory bread(block 131468) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.700901] FAT: Directory bread(block 131469) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.700910] FAT: Directory bread(block 131470) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.700919] FAT: Directory bread(block 131471) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.700927] FAT: Directory bread(block 131472) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.700936] FAT: Directory bread(block 131473) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.700945] FAT: Directory bread(block 131474) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.700953] FAT: Directory bread(block 131475) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.700962] FAT: Directory bread(block 131476) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.700971] FAT: Directory bread(block 131477) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.700980] FAT: Directory bread(block 131478) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.700988] FAT: Directory bread(block 131479) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.700997] FAT: Directory bread(block 131480) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701005] FAT: Directory bread(block 131481) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701014] FAT: Directory bread(block 131482) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701022] FAT: Directory bread(block 131483) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701030] FAT: Directory bread(block 131484) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701039] FAT: Directory bread(block 131485) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701047] FAT: Directory bread(block 131486) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701056] FAT: Directory bread(block 131487) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701064] FAT: Directory bread(block 131488) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701073] FAT: Directory bread(block 131489) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701081] FAT: Directory bread(block 131490) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701090] FAT: Directory bread(block 131491) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701098] FAT: Directory bread(block 131492) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701107] FAT: Directory bread(block 131493) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701115] FAT: Directory bread(block 131494) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701124] FAT: Directory bread(block 131495) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701132] FAT: Directory bread(block 131496) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701141] FAT: Directory bread(block 131497) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701149] FAT: Directory bread(block 131498) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701158] FAT: Directory bread(block 131499) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701166] FAT: Directory bread(block 131500) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701174] FAT: Directory bread(block 131501) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701183] FAT: Directory bread(block 131502) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701191] FAT: Directory bread(block 131503) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701200] FAT: Directory bread(block 131504) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701208] FAT: Directory bread(block 131505) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701216] FAT: Directory bread(block 131506) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701225] FAT: Directory bread(block 131507) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701233] FAT: Directory bread(block 131508) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701242] FAT: Directory bread(block 131509) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701250] FAT: Directory bread(block 131510) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701258] FAT: Directory bread(block 131511) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701267] FAT: Directory bread(block 131512) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701275] FAT: Directory bread(block 131513) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701283] FAT: Directory bread(block 131514) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701292] FAT: Directory bread(block 131515) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701300] FAT: Directory bread(block 131516) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701308] FAT: Directory bread(block 131517) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701317] FAT: Directory bread(block 131518) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701325] FAT: Directory bread(block 131519) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701334] FAT: Directory bread(block 131520) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701342] FAT: Directory bread(block 131521) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701350] FAT: Directory bread(block 131522) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701359] FAT: Directory bread(block 131523) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701367] FAT: Directory bread(block 131524) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701375] FAT: Directory bread(block 131525) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701384] FAT: Directory bread(block 131526) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701392] FAT: Directory bread(block 131527) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.701400] FAT: Directory bread(block 131528) failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.712946] sd 6:0:0:1: [sdf] READ CAPACITY failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.712954] sd 6:0:0:1: [sdf] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.712959] sd 6:0:0:1: [sdf] Sense not available.
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.712975] sd 6:0:0:0: [sde] READ CAPACITY failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.712978] sd 6:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.712982] sd 6:0:0:0: [sde] Sense not available.
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.713007] sd 6:0:0:1: [sdf] Write Protect is off
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.713010] sd 6:0:0:1: [sdf] Mode Sense: 00 00 00 00
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.713013] sd 6:0:0:1: [sdf] Assuming drive cache: write through
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.713027] sd 6:0:0:0: [sde] Write Protect is off
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.713031] sd 6:0:0:0: [sde] Mode Sense: 00 00 00 00
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.713033] sd 6:0:0:0: [sde] Assuming drive cache: write through
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.713112] sd 6:0:0:1: [sdf] READ CAPACITY failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.713115] sd 6:0:0:1: [sdf] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.713119] sd 6:0:0:1: [sdf] Sense not available.
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.713135] sd 6:0:0:1: [sdf] Write Protect is off
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.713138] sd 6:0:0:1: [sdf] Mode Sense: 00 00 00 00
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.713140] sd 6:0:0:1: [sdf] Assuming drive cache: write through
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.713169] FAT: unable to read inode block for updating (i_pos 2103491)
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.714341] sd 6:0:0:1: [sdf] READ CAPACITY failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.714346] sd 6:0:0:1: [sdf] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.714351] sd 6:0:0:1: [sdf] Sense not available.
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.714417] sd 6:0:0:1: [sdf] Write Protect is off
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.714421] sd 6:0:0:1: [sdf] Mode Sense: 00 00 00 00
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.714424] sd 6:0:0:1: [sdf] Assuming drive cache: write through
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.714579] scsi 6:0:0:1: rejecting I/O to dead device
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.714588] scsi 6:0:0:1: rejecting I/O to dead device
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.714593] scsi 6:0:0:1: [sdf] READ CAPACITY failed
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.714596] scsi 6:0:0:1: [sdf] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.714600] scsi 6:0:0:1: [sdf] Sense not available.
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.714606] scsi 6:0:0:1: rejecting I/O to dead device
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.714611] scsi 6:0:0:1: [sdf] Write Protect is off
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.714614] scsi 6:0:0:1: [sdf] Mode Sense: 00 00 00 00
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.714617] scsi 6:0:0:1: [sdf] Assuming drive cache: write through
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.717074] scsi 6:0:0:1: rejecting I/O to dead device
Oct 22 16:43:19 ryan-desktop kernel: [ 2434.845744] scsi 6:0:0:0: rejecting I/O to dead device
[/PHP]


I would still like to know what file/package to *delete/reconfigure/rollback* to solve this problem and get it working like it used to.

I will continue to try.
Any suggestions are appreciated.

-Ryan

---

### Post by GeneralSpecific on 2009-10-29
Thread closed.

The problem seems to have fixed itself after the most recent update...I don't know why, but I'm sure not complaining!!

-Ryan

---

