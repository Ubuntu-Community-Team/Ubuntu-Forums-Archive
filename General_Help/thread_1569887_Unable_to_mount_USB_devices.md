---
title: "Unable to mount USB devices"
date: 2010-09-07
forum: General Help
---

### Post by ender4 on 2010-09-07
I have two devices which I am unable to mount: a generic mp3 player, and a Kodak M340 digital camera.  Before upgrading to Lucid I was able to access both as USB Mass-storage devices, but now I cannot.  I have gotten the mp3 player to work once, but am unable to reproduce it.  

The devices are listed by lsusb, but I cannot find them in the /dev directory.  My flash drive and phone show up as /dev/sdb, (or /dev/sdc if there is more than one device plugged in) but with the camera and mp3 player /dev/sdb does not appear.

digiKam and F-spot both recognize the camera, but when I try to import I get "Received error 'could not lock the device'while connecting to camera" form F-spot and "Failed to connect to the camera. Please make sure it is connected properly and turned on. Would you like to try again?" from digiKam.  Both recognize my camera as a PTP USB device, though I am not sure what that means.

I can successfully mount the devices on my desktop which is also running Lucid, so my guess is that I need to fix a config file, or I am missing a package.  

Here is some output form lsusb, ls /dev, etc. when I have my camera plugged in:
```
$lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 005 Device 002: ID 046d:c045 Logitech, Inc. Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR="Lime"]Bus 002 Device 010: ID 040a:05d0 Kodak Co. [/COLOR]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
$dmesg | tail -20
[ 1572.489367] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 2036.248145] usb 6-1: USB disconnect, address 3
[ 2037.728131] usb 6-1: new full speed USB device using uhci_hcd and address 4
[ 2037.871395] usb 6-1: config 1 has an invalid interface number: 3 but max is 2
[ 2037.871402] usb 6-1: config 1 has 4 interfaces, different from the descriptor's value: 3
[ 2037.885620] usb 6-1: configuration #1 chosen from 1 choice
[ 2037.887540] cdc_acm 6-1:1.0: ttyACM0: USB ACM device
[ 2040.712272] usb 6-1: USB disconnect, address 4
[ 2060.160100] usb 2-3: new high speed USB device using ehci_hcd and address 8
[ 2060.295122] usb 2-3: configuration #1 chosen from 1 choice
[ 2060.295459] scsi7 : SCSI emulation for USB Mass Storage devices
[ 2060.295769] usb-storage: device found at 8
[ 2060.295773] usb-storage: waiting for device to settle before scanning
[ 2070.588100] usb 2-3: reset high speed USB device using ehci_hcd and address 8
[ 2554.780313] usb 2-3: USB disconnect, address 8
[ 2568.352060] usb 2-3: new high speed USB device using ehci_hcd and address 9
[ 2568.553624] usb 2-3: configuration #1 chosen from 1 choice
[ 3050.476830] usb 2-3: USB disconnect, address 9
[ 3063.068170] usb 2-3: new high speed USB device using ehci_hcd and address 10
[ 3063.275424] usb 2-3: configuration #1 chosen from 1 choice
$sudo mount -t scsi /dev/bus/usb/002/010 Media
mount: unknown filesystem type 'scsi'
$sudo mount -t usbfs /dev/bus/usb/002/010 Media
mount: unknown filesystem type 'usbfs'
$mount -l
/dev/sda5 on / type ext4 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/thayne/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=thayne)
$gvfs-mount -l
Drive(0): CD/DVD Drive
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
Drive(1): 250 GB Hard Disk
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
  Volume(0): OS
    Type: GProxyVolume (GProxyVolumeMonitorGdu)

```

Pleas help me, I can't think of anything else to try.

---

### Post by ender4 on 2010-09-07
First of all, the problem with my mp3 player is not a problem at all, I just forgot to turn it on :)

Somehow I was able to get my camera working, I think it was by changing Nautilus to automatically open the folder when a camera is detected.  Why this fixed the problem I have no idea. And it has the strange effect that the camera appears twice in the Computer pseudo-folder.  (and twice on the sidebar). Unfortunetly this only works in GNOME, and I can only import the pictures through F-spot, or through Nautilus.  I would really like it to work with KDE and digiKam (digiKam still can't import them in GNOME either), does anyone have any ideas what the problem is, or how I could fix it.  

When I plug in the camera I get a message saying "Unable to mount KODAK EASYSHARE M340 Digital Camera, Error initializing camera: -60: Could not lock the device", and then two folders open: gphoto2://[usb:002,028]/store_00020001, and gphoto2://[usb:002,028]/store_00010001.

The store_00010001 contains my photos, and the other one contains a single file called DCEMAIL.ABK.

---

