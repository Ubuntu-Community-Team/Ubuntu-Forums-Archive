---
title: "USB flash drive not found"
date: 2009-09-06
forum: General Help
---

### Post by qbektrix on 2009-09-06
I saved some file on my USB flash drive using Ubuntu 9.04 and when i checked in WinXP, the drive was not found. I assumed some OS issue. Then only did it strike me that i forgot to unmount the drive before removing it from Ubuntu. Then i tried connecting it to Ubuntu. Its not detected. What can i do??? I tried to connect to WinXP & perform error-check. No luck.
Any advice -pls. 
Is the issue b'cos i forgot to unmount or my flash just died at a wrong time.

Thanks

---

### Post by RHTopics on 2009-09-06
To determine your problem, try this:

Insert the USB flash drive

Open a Terminal window

Type the following command:

    dmesg

The listing from the dmesg command will scroll off the screen, but we are interested in the last 20 or so lines, which should be on the screen.  It should have something in the messages displayed describing a problem when trying to mount the USB flash drive.

Post those 20 or so lines here if you need help understanding them.

---

### Post by qbektrix on 2009-09-06
Maxtor OneTouch is my 1tb external drive which is not connected now. But no clue why it is also referred below



[ 3425.320054] usb 1-4: new high speed USB device using ehci_hcd and address 3
[ 3425.453830] usb 1-4: configuration #1 chosen from 1 choice
[ 3425.515101] Initializing USB Mass Storage driver...
[ 3425.516510] scsi6 : SCSI emulation for USB Mass Storage devices
[ 3425.516908] usb-storage: device found at 3
[ 3425.516913] usb-storage: waiting for device to settle before scanning
[ 3425.516932] usbcore: registered new interface driver usb-storage
[ 3425.517176] USB Mass Storage support registered.
[ 3430.516308] usb-storage: device scan complete
[ 3430.516824] scsi 6:0:0:0: Direct-Access     Maxtor   OneTouch         0125 PQ: 0 ANSI: 4
[ 3430.518873] sd 6:0:0:0: [sdb] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[ 3430.519538] sd 6:0:0:0: [sdb] Write Protect is off
[ 3430.519543] sd 6:0:0:0: [sdb] Mode Sense: 2d 08 00 00
[ 3430.519548] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 3430.521418] sd 6:0:0:0: [sdb] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[ 3430.522035] sd 6:0:0:0: [sdb] Write Protect is off
[ 3430.522041] sd 6:0:0:0: [sdb] Mode Sense: 2d 08 00 00
[ 3430.522045] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 3430.522052]  sdb: sdb1
[ 3430.559687] sd 6:0:0:0: [sdb] Attached SCSI disk
[ 3430.559817] sd 6:0:0:0: Attached scsi generic sg2 type 0
[15496.106356] [drm:i915_getparam] *ERROR* Unknown parameter 6
[15496.187942] [drm:i915_getparam] *ERROR* Unknown parameter 6
[15759.854746] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[16394.703608] usb 1-4: USB disconnect, address 3
[16401.856069] usb 1-4: new high speed USB device using ehci_hcd and address 4
[16401.992610] usb 1-4: configuration #1 chosen from 1 choice
[16401.992915] hub 1-4:1.0: USB hub found
[16401.993464] hub 1-4:1.0: 4 ports detected
[16404.052344] usb 1-4.4: new high speed USB device using ehci_hcd and address 5
[16404.234236] usb 1-4.4: configuration #1 chosen from 1 choice
[16404.234541] scsi7 : SCSI emulation for USB Mass Storage devices
[16404.234704] usb-storage: device found at 5
[16404.234709] usb-storage: waiting for device to settle before scanning
[16409.233373] usb-storage: device scan complete
[16409.234134] scsi 7:0:0:0: Direct-Access     Generic  USB Flash Disk   7.76 PQ: 0 ANSI: 2
[16409.237589] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[16409.238015] sd 7:0:0:0: Attached scsi generic sg2 type 0
[16433.038968] usb 1-4.4: USB disconnect, address 5
[16434.296393] usb 1-4: USB disconnect, address 4
[16437.068059] usb 1-4: new high speed USB device using ehci_hcd and address 6
[16437.250641] usb 1-4: configuration #1 chosen from 1 choice
[16437.280058] scsi8 : SCSI emulation for USB Mass Storage devices
[16437.280482] usb-storage: device found at 6
[16437.280487] usb-storage: waiting for device to settle before scanning
[16442.276322] usb-storage: device scan complete
[16442.277033] scsi 8:0:0:0: Direct-Access     Generic  USB Flash Disk   7.76 PQ: 0 ANSI: 2
[16442.281178] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[16442.281312] sd 8:0:0:0: Attached scsi generic sg2 type 0
[16454.829021] usb 1-4: USB disconnect, address 6
[18008.901033] CE: hpet increasing min_delta_ns to 15000 nsec
[19137.219180] [drm:i915_getparam] *ERROR* Unknown parameter 6
[19137.305959] [drm:i915_getparam] *ERROR* Unknown parameter 6
[21439.893726] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[21440.150640] usb 1-4: new high speed USB device using ehci_hcd and address 7
[21440.339722] usb 1-4: configuration #1 chosen from 1 choice
[21440.340235] scsi9 : SCSI emulation for USB Mass Storage devices
[21440.344345] usb-storage: device found at 7
[21440.344350] usb-storage: waiting for device to settle before scanning
[21445.340370] usb-storage: device scan complete
[21445.341074] scsi 9:0:0:0: Direct-Access     Generic  USB Flash Disk   7.76 PQ: 0 ANSI: 2
[21445.345902] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[21445.346326] sd 9:0:0:0: Attached scsi generic sg2 type 0

---

### Post by RHTopics on 2009-09-06
Actually having the Maxtor OneTouch appear in the dmesg display is helpful, for it shows what a valid USB attachment looks like.  I can see with this line that it was removed:

[16394.703608] usb 1-4: USB disconnect, address 3

For the USB Flash drive, I can see where you have tried to insert and remove it multiple times.  Each time it is inserted it is recognized enough to partially identify it but seems like it can not get enough information to mount it.  It should be displaying in dmesg something similar to the lines for the Maxtor OneTouch when it was inserted:

[ 3430.518873] sd 6:0:0:0: [sdb] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[ 3430.519538] sd 6:0:0:0: [sdb] Write Protect is off
[ 3430.519543] sd 6:0:0:0: [sdb] Mode Sense: 2d 08 00 00
[ 3430.519548] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 3430.521418] sd 6:0:0:0: [sdb] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[ 3430.522035] sd 6:0:0:0: [sdb] Write Protect is off
[ 3430.522041] sd 6:0:0:0: [sdb] Mode Sense: 2d 08 00 00
[ 3430.522045] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 3430.522052] sdb: sdb1

With the USB Flash drive inserted, do the following command in a Terminal window:

lsusb

This is just to make sure it shows up as a USB device.

Then do the following command:

sudo fdisk -l

This is to see if the device shows up in fdisk.

---

### Post by RHTopics on 2009-09-06
One other place to check for messages.

Check /var/log/syslog which can be accessed from the menu (System -> Administration -> System Log) and then choose syslog from the list on the left side of the window.

It may give additional information on what is going wrong.

I am going to be away from computer for several hours.

---

### Post by qbektrix on 2009-09-06
I ran the commands after inserting another Flash Drive (TwinMos 1Gb) along with the Flash Drive with the problem (Transcend 4gb)

[I]lsusb:

Bus 001 Device 012: ID 058f:1234 Alcor Micro Corp. 
Bus 001 Device 011: ID 126f:0161 TwinMOS 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/I]

The flash drive with the problem is Transscend 4GB. I wonder if my machine is identifying that as Alcor.
[I]
sudo fdisk -l:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa930a930

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2            3825        9729    47431912+   5  Extended
/dev/sda5            3825        3946      979933+  82  Linux swap / Solaris
/dev/sda6            3947        9729    46451916   83  Linux

Disk /dev/sdb: 1048 MB, 1048576000 bytes
32 heads, 63 sectors/track, 1015 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0x9523c132

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1014     1022080+   b  W95 FAT32[/I]


the 80 gb is my internal HD. The twinmos one is also shown. But the Transcend one is no where to be seen.

What does this mean?

As for system log, under System->Administrator.
The is System Monitor & System Testing. But there is another one called Log File Viewer. There under syslog, i monitored the log but inserting both my flash drive one by one.

When i inserted the Transcend 4gb drive:
[I]Sep  6 19:24:59 nx6310 kernel: [29981.712064] usb 1-4: new high speed USB device using ehci_hcd and address 15
Sep  6 19:25:00 nx6310 kernel: [29981.902884] usb 1-4: configuration #1 chosen from 1 choice
Sep  6 19:25:00 nx6310 kernel: [29981.905425] scsi15 : SCSI emulation for USB Mass Storage devices
Sep  6 19:25:05 nx6310 kernel: [29986.906720] scsi 15:0:0:0: Direct-Access     Generic  USB Flash Disk   7.76 PQ: 0 ANSI: 2
Sep  6 19:25:05 nx6310 kernel: [29986.910112] sd 15:0:0:0: [sdb] Attached SCSI removable disk
Sep  6 19:25:05 nx6310 kernel: [29986.910244] sd 15:0:0:0: Attached scsi generic sg2 type 0
Sep  6 19:26:07 nx6310 kernel: [30049.629541] usb 1-4: USB disconnect, address 15[/I]

When i inserted the TwinMOS 1gb drive:
[I]Sep  6 19:26:24 nx6310 kernel: [30066.696081] usb 1-4: new high speed USB device using ehci_hcd and address 16
Sep  6 19:26:24 nx6310 kernel: [30066.829409] usb 1-4: configuration #1 chosen from 1 choice
Sep  6 19:26:24 nx6310 kernel: [30066.829811] scsi16 : SCSI emulation for USB Mass Storage devices
Sep  6 19:26:29 nx6310 kernel: [30071.829543] scsi 16:0:0:0: Direct-Access     USB2.0   Mobile Disk      1.00 PQ: 0 ANSI: 2
Sep  6 19:26:29 nx6310 kernel: [30071.832081] sd 16:0:0:0: [sdb] 2048000 512-byte hardware sectors: (1.04 GB/1000 MiB)
Sep  6 19:26:29 nx6310 kernel: [30071.832740] sd 16:0:0:0: [sdb] Write Protect is off
Sep  6 19:26:29 nx6310 kernel: [30071.834116] sd 16:0:0:0: ioctl_internal_command return code = 8000002
Sep  6 19:26:29 nx6310 kernel: [30071.834121]    : Sense Key : No Sense [current] 
Sep  6 19:26:29 nx6310 kernel: [30071.834128]    : Add. Sense: No additional sense information
Sep  6 19:26:29 nx6310 kernel: [30071.834993] sd 16:0:0:0: [sdb] 2048000 512-byte hardware sectors: (1.04 GB/1000 MiB)
Sep  6 19:26:29 nx6310 kernel: [30071.835615] sd 16:0:0:0: [sdb] Write Protect is off
Sep  6 19:26:30 nx6310 kernel: [30071.835634]  sdb: sdb1
Sep  6 19:26:30 nx6310 kernel: [30071.945435] sd 16:0:0:0: [sdb] Attached SCSI removable disk
Sep  6 19:26:30 nx6310 kernel: [30071.945565] sd 16:0:0:0: Attached scsi generic sg2 type 0
Sep  6 19:26:30 nx6310 kernel: [30071.984010] sd 16:0:0:0: ioctl_internal_command return code = 8000002
Sep  6 19:26:30 nx6310 kernel: [30071.984016]    : Sense Key : No Sense [current] 
Sep  6 19:26:30 nx6310 kernel: [30071.984024]    : Add. Sense: No additional sense information
Sep  6 19:26:30 nx6310 kernel: [30072.168734] sd 16:0:0:0: ioctl_internal_command return code = 8000002
Sep  6 19:26:30 nx6310 kernel: [30072.168740]    : Sense Key : No Sense [current] 
Sep  6 19:26:30 nx6310 kernel: [30072.168748]    : Add. Sense: No additional sense information
Sep  6 19:26:30 nx6310 kernel: [30072.180611] sd 16:0:0:0: ioctl_internal_command return code = 8000002
Sep  6 19:26:30 nx6310 kernel: [30072.180617]    : Sense Key : No Sense [current] 
Sep  6 19:26:30 nx6310 kernel: [30072.180625]    : Add. Sense: No additional sense information
Sep  6 19:26:30 nx6310 kernel: [30072.229110] sd 16:0:0:0: ioctl_internal_command return code = 8000002
Sep  6 19:26:30 nx6310 kernel: [30072.229117]    : Sense Key : No Sense [current] 
Sep  6 19:26:30 nx6310 kernel: [30072.229125]    : Add. Sense: No additional sense information
Sep  6 19:26:30 nx6310 kernel: [30072.482867] sd 16:0:0:0: ioctl_internal_command return code = 8000002
Sep  6 19:26:30 nx6310 kernel: [30072.482872]    : Sense Key : No Sense [current] 
Sep  6 19:26:30 nx6310 kernel: [30072.482877]    : Add. Sense: No additional sense information
Sep  6 19:26:41 nx6310 kernel: [30082.887141] sd 16:0:0:0: ioctl_internal_command return code = 8000002
Sep  6 19:26:41 nx6310 kernel: [30082.887149]    : Sense Key : No Sense [current] 
Sep  6 19:26:41 nx6310 kernel: [30082.887156]    : Add. Sense: No additional sense information
Sep  6 19:26:43 nx6310 kernel: [30084.887496] sd 16:0:0:0: ioctl_internal_command return code = 8000002
Sep  6 19:26:43 nx6310 kernel: [30084.887503]    : Sense Key : No Sense [current] 
Sep  6 19:26:43 nx6310 kernel: [30084.887511]    : Add. Sense: No additional sense information
Sep  6 19:26:44 nx6310 kernel: [30086.159912] usb 1-4: USB disconnect, address 16[/I]

---

### Post by RHTopics on 2009-09-06
Sorry about the menu misdirection for displaying /var/log/syslog.  The computer I am currently using has Ubuntu 8.04.3 installed and the menu layout is different than 9.04.

Out of curiousity, I did a Google search for "alcor micro transcend" and found an interesting forum message addressing your problem.  So yes, Alcor Micro and Transcend are the same device, and it appears from this forum message their USB drives have known problems like you are experiencing.  This message appears to provide a solution from the manufacturer. 

[http://www.thinkdigit.com/forum/archive/index.php/t-106484.html](http://www.thinkdigit.com/forum/archive/index.php/t-106484.html) 

Maybe that solution will work for you.:)

---

### Post by qbektrix on 2009-09-06
Thanks a lot dude for the link & helping me out with my issue.
But my new issue is that fact that i dont have my s/n of the USB drive. Anyways, contacted the Transcend support team to check if they can help me.
Hope they can help me out.
Is there any other way i can format the drive if the transcend guys say that they cannot do anything if i dont have the serial number?

---

### Post by RHTopics on 2009-09-06
From what I know, the serial number should be on the drive, but it maybe small and faint, making it hard to see.

Try using a magnifying glass while the drive is under a good source of light.  Turn the drive different ways to see if you can see the serial numbers.

Here is another link for more information:

[http://www.articlesbase.com/computers-articles/transcend-pen-drive-not-working-or-not-identified-on-your-system-what-to-do-1102255.html](http://www.articlesbase.com/computers-articles/transcend-pen-drive-not-working-or-not-identified-on-your-system-what-to-do-1102255.html)

---

