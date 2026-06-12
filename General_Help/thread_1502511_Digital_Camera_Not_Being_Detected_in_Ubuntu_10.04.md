---
title: "Digital Camera Not Being Detected in Ubuntu 10.04"
date: 2010-06-05
forum: General Help
---

### Post by Aiello on 2010-06-05
I'm having some problems with Ubuntu 10.04 64bit finding my digital camera (Nikon CoolPix S4000). For whatever reason, when I plug in the camera via USB connection, Ubuntu will not detect it. The odd thing is that on my old Ubuntu 9.04 32bit install my camera was detected fine (it appeared as an icon on the desktop, akin to a flashdrive or any other mounted drive). Any suggestions?

-Thanks!

---

### Post by arrange on 2010-06-05
Unplug the camera, then plug it back in, and after a few seconds type this in [Terminal](https://help.ubuntu.com/community/GnomeTerminal)```
lsusb
gvfs-mount -l
dmesg | tail -20
```Please post the output here.

---

### Post by Aiello on 2010-06-05
This is the output
```
eric@EricCollins-LLT:~$ lsusb
Bus 002 Device 006: ID 04b0:031a Nikon Corp. 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 046d:c52f Logitech, Inc. 
Bus 001 Device 003: ID 0ac8:c342 Z-Star Microelectronics Corp. 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
eric@EricCollins-LLT:~$ gvfs-mount -l
Drive(0): 500 GB Hard Disk
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
  Volume(0): SYSTEM
    Type: GProxyVolume (GProxyVolumeMonitorGdu)
  Volume(1): 236 GB Filesystem
    Type: GProxyVolume (GProxyVolumeMonitorGdu)
    Mount(0): 236 GB Filesystem -> file:///media/00EC7C19EC7C0AE4
      Type: GProxyMount (GProxyVolumeMonitorGdu)
Drive(1): CD/DVD/Blu-Ray Drive
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
eric@EricCollins-LLT:~$ dmesg | tail -20
[   53.552827] wlan0: no IPv6 routers present
[  310.700267] atkbd.c: Unknown key pressed (translated set 2, code 0xf9 on isa0060/serio0).
[  310.700275] atkbd.c: Use 'setkeycodes e079 <keycode>' to make it known.
[  593.494404] Inbound IN=wlan0 OUT= MAC=b4:82:fe:6b:d9:f1:00:13:10:cb:f6:70:08:00 SRC=192.168.1.1 DST=192.168.1.101 LEN=386 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1900 DPT=43205 LEN=366 
[  595.090812] Inbound IN=wlan0 OUT= MAC=b4:82:fe:6b:d9:f1:00:13:10:cb:f6:70:08:00 SRC=192.168.1.1 DST=192.168.1.101 LEN=388 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1900 DPT=43205 LEN=368 
[ 1012.934368] usb 2-1.2: new high speed USB device using ehci_hcd and address 3
[ 1013.045165] usb 2-1.2: configuration #1 chosen from 1 choice
[ 1013.440128] usb 2-1.2: reset high speed USB device using ehci_hcd and address 3
[ 1034.579670] usb 2-1.2: USB disconnect, address 3
[ 1044.699331] usb 2-1.2: new high speed USB device using ehci_hcd and address 4
[ 1044.819984] usb 2-1.2: configuration #1 chosen from 1 choice
[ 1045.222052] usb 2-1.2: reset high speed USB device using ehci_hcd and address 4
[ 1063.160191] usb 2-1.2: USB disconnect, address 4
[ 1097.676965] usb 2-1.2: new high speed USB device using ehci_hcd and address 5
[ 1097.808333] usb 2-1.2: configuration #1 chosen from 1 choice
[ 1098.218386] usb 2-1.2: reset high speed USB device using ehci_hcd and address 5
[ 3300.466322] usb 2-1.2: USB disconnect, address 5
[ 3316.691284] usb 2-1.2: new high speed USB device using ehci_hcd and address 6
[ 3316.802407] usb 2-1.2: configuration #1 chosen from 1 choice
[ 3317.211125] usb 2-1.2: reset high speed USB device using ehci_hcd and address 6

```

It seems it at least knows the camera is plugged in, with that Nikon Corp. output.

---

### Post by Aiello on 2010-06-05
Well, just for kicks, I went and rebooted the system. Now Ubuntu detects the camera! Very odd. Thanks for the help though!

---

### Post by arturo503 on 2010-08-28
I a having this same exact issue with my Nikon D70.  I tried importing my photos with Fspot and it does not detect the camera.  I tried Rebooting my system but that did not do anything.  Any suggestions?

---

### Post by arturo503 on 2010-08-28
I opened terminal and input the commands suggested.  This is what it bounced back to me:

work@work-laptop:~$ lsusb
Bus 005 Device 002: ID 0458:0003 KYE Systems Corp. (Mouse Systems) Genius NetScroll+
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 04b0:0405 Nikon Corp. D70 (mass storage mode)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
work@work-laptop:~$ gvfs-mount -l
Drive(0): CD/DVD Drive
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
work@work-laptop:~$ dmesg | tail -20


Looks like it is seeing my Nikon D70 in Mas storage mode.  Why does Fspot not see my camera?  I also tried the program Camera from the software center and neither detects the camera.  Any help would be greatly appreciated.

---

### Post by simohell on 2010-11-21
> **Aiello said:**
> Well, just for kicks, I went and rebooted the system. Now Ubuntu detects the camera! Very odd. Thanks for the help though!

I had same problem on my wife's laptop. The solution was rebooting, but for obvious - not odd - reason: a kernel update or something similar had been installed, but system was not yet rebooted.

Thus rebooting required for camera to work.

---

### Post by shosto on 2011-07-09
I see this thread is marked "Solved."  However; IMHO, reboots as a software fix isn't a fix at all, especially with a *nix box.

My wife has a similar problem.  Camera appears in "lsusb" output but the camera isn't mounted automatically.  After a bit of research whipped up a small shell script to mount the camera via nautilus.

---

### Post by goodbye-windows(tm) on 2011-10-22
I have the same problem with Xubuntu 11.10 in an old 32 bit machine. My camera is also a Nikon S4000.

Nothing happens when I plug in the USB connector. Have tried hot plugging it, and plugging it in with no software running and plugging it in after starting software-no difference. Have tried gimp and f-spot software.

Not sure whether to post here, or whether to start another thread. 

Shosto, I don't know about running scripts, am a newbee. Is this script useful in Xubuntu, 11.10?? If so, I'll look up how to run the thing.

Here is the output of the 3 commands above. Note that this output is taken after plugging the camera into the USB port.

art@art-MS-7104:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:001c Microsoft Corp. Internet Keyboard Pro
Bus 003 Device 003: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 001 Device 009: ID 04b0:031a Nikon Corp. 
art@art-MS-7104:~$ 






art@art-MS-7104:~$ gvfs-mount -l
Drive(0): CD/DVD Drive
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
  Volume(0): Xubuntu 11.10 i386
    Type: GProxyVolume (GProxyVolumeMonitorGdu)
    Mount(0): Xubuntu 11.10 i386 -> file:///media/Xubuntu%2011.10%20i386
      Type: GProxyMount (GProxyVolumeMonitorGdu)




art@art-MS-7104:~$ dmesg | tail -20
[ 8975.082133] Buffer I/O error on device sr0, logical block 810
[ 8975.082139] Buffer I/O error on device sr0, logical block 811
[ 8975.082151] Buffer I/O error on device sr0, logical block 812
[ 8975.082155] Buffer I/O error on device sr0, logical block 813
[ 8975.082158] Buffer I/O error on device sr0, logical block 814
[ 8975.082162] Buffer I/O error on device sr0, logical block 815
[ 8975.082165] Buffer I/O error on device sr0, logical block 816
[ 8975.082168] Buffer I/O error on device sr0, logical block 817
[ 8997.055560] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-5]
[ 8997.055570] ecryptfs_writepage: Error encrypting page (upper index [0x0000000000000062])
[ 9027.057829] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-5]
[ 9027.057839] ecryptfs_writepage: Error encrypting page (upper index [0x0000000000000063])
[ 9057.060094] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-5]
[ 9057.060104] ecryptfs_writepage: Error encrypting page (upper index [0x0000000000000064])
[ 9087.062373] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-5]
[ 9087.062383] ecryptfs_writepage: Error encrypting page (upper index [0x0000000000000065])
[ 9683.985233] usb 1-4: USB disconnect, device number 8
[12650.879615] usb 1-4: new high speed USB device number 9 using ehci_hcd
[12676.509704] ISO 9660 Extensions: Microsoft Joliet Level 3
[12676.512207] ISO 9660 Extensions: RRIP_1991A
art@art-MS-7104:~$ 

Appreciate any help.

Regards,

Art

---

### Post by goodbye-windows(tm) on 2011-10-22
Glad yours is running Madeline. For me, rebooting made no difference.

Regards,

Art

---

### Post by bkline on 2011-12-07
Same problem.  Rebooting does not help.  Nikon D5100 on Xubuntu 11.10.

---

### Post by goodbye-windows(tm) on 2011-12-08
Hi bk. 

I still haven't found an answer to the problem, but I did purchase a small usb drive that will accept the SD card after it is removed from the camera. But, we take a bunch of pictures, it would be nice to have ubuntu download from the camera directly.

GL.

Art

---

### Post by Palouse Penguin on 2012-01-22
libgphoto2 2.4.11 contains some new drivers ie the Nikon Coolpix S9100. Has anyone got that to work/replace the 2.4.8 version in 10.04?

[http://www.gphoto.org/news/](http://www.gphoto.org/news/)

---

### Post by mips on 2012-04-23
> **bkline said:**
> Same problem.  Rebooting does not help.  Nikon D5100 on Xubuntu 11.10.

Trying out a D5100 on 11.10 and I have the same issue.

Anyone have a fix?

---

