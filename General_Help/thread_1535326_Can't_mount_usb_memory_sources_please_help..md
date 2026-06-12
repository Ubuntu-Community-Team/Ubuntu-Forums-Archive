---
title: "Can't mount usb memory sources please help."
date: 2010-07-20
forum: General Help
---

### Post by dalehartt on 2010-07-20
I'm having a hard time making memory sticks, and any other usb plug in memories working with my ubuntu.  Not sure what information will help but here is the error message.  


Error mounting: mount exited with exit code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Im not super comfortable with ubuntu yet, but I've enjoyed it thus far.

---

### Post by dalehartt on 2010-07-20
please let me know what information will be helpfull.  I really need to be able upload from my camera and video camera.  Any help would be appreciated.

---

### Post by robertcoulson on 2010-07-20
Have the SAME problem on my 16 gb stick...Downloaded "Testdisk" and ran it to copy important files off of it...Worked great, but stick is still bad.
Robert

---

### Post by pytheas22 on 2010-07-20
If you're having problems with all USB sticks or memory cards that you try to access in Ubuntu, then the problem is probably Ubuntu's, not a bad device.  What is the output after trying to mount the device of:
```

dmesg | tail -30
```

---

### Post by dalehartt on 2010-07-20
> **pytheas22 said:**
> If you're having problems with all USB sticks or memory cards that you try to access in Ubuntu, then the problem is probably Ubuntu's, not a bad device.  What is the output after trying to mount the device of:
```

dmesg | tail -30
```
do I need to do that from the command line?

---

### Post by dalehartt on 2010-07-20
dale@dale-desktop:~$ dmesg | tail -30
[   81.556088] FAT: Unrecognized mount option "group=user" or missing value
[  340.428114] e1000: eth0 NIC Link is Down
[  359.856374] e1000: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
[  364.404115] e1000: eth0 NIC Link is Down
[  366.060382] e1000: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  366.832114] e1000: eth0 NIC Link is Down
[  368.568374] e1000: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 7008.732182] usb 1-2.2: new high speed USB device using ehci_hcd and address 7
[ 7008.842441] usb 1-2.2: configuration #1 chosen from 2 choices
[ 7008.845279] scsi4 : SCSI emulation for USB Mass Storage devices
[ 7008.865017] usb-storage: device found at 7
[ 7008.865022] usb-storage: waiting for device to settle before scanning
[ 7013.864586] usb-storage: device scan complete
[ 7013.865517] scsi 4:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 7013.870485] sd 4:0:0:0: Attached scsi generic sg8 type 0
[ 7013.874250] sd 4:0:0:0: [sdg] Adjusting the sector count from its reported value: 3999744
[ 7013.874261] sd 4:0:0:0: [sdg] 3999743 512-byte logical blocks: (2.04 GB/1.90 GiB)
[ 7013.885800] sd 4:0:0:0: [sdg] Write Protect is off
[ 7013.885808] sd 4:0:0:0: [sdg] Mode Sense: 68 00 00 08
[ 7013.885813] sd 4:0:0:0: [sdg] Assuming drive cache: write through
[ 7013.888452] sd 4:0:0:0: [sdg] Adjusting the sector count from its reported value: 3999744
[ 7013.889627] sd 4:0:0:0: [sdg] Assuming drive cache: write through
[ 7013.889639]  sdg: sdg1 sdg2
[ 7013.897706] sd 4:0:0:0: [sdg] Adjusting the sector count from its reported value: 3999744
[ 7013.899491] sd 4:0:0:0: [sdg] Assuming drive cache: write through
[ 7013.899503] sd 4:0:0:0: [sdg] Attached SCSI removable disk
[ 7014.500490] FAT: invalid media value (0x2f)
[ 7014.500498] VFS: Can't find a valid FAT filesystem on dev sdg1.
[ 7017.703727] FAT: invalid media value (0x2f)
[ 7017.703736] VFS: Can't find a valid FAT filesystem on dev sdg1.

---

### Post by dalehartt on 2010-07-20
this time after trying to mount my memory stick


dale@dale-desktop:~$ dmesg | tail -30
[   81.556088] FAT: Unrecognized mount option "group=user" or missing value
[  340.428114] e1000: eth0 NIC Link is Down
[  359.856374] e1000: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
[  364.404115] e1000: eth0 NIC Link is Down
[  366.060382] e1000: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  366.832114] e1000: eth0 NIC Link is Down
[  368.568374] e1000: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 7008.732182] usb 1-2.2: new high speed USB device using ehci_hcd and address 7
[ 7008.842441] usb 1-2.2: configuration #1 chosen from 2 choices
[ 7008.845279] scsi4 : SCSI emulation for USB Mass Storage devices
[ 7008.865017] usb-storage: device found at 7
[ 7008.865022] usb-storage: waiting for device to settle before scanning
[ 7013.864586] usb-storage: device scan complete
[ 7013.865517] scsi 4:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 7013.870485] sd 4:0:0:0: Attached scsi generic sg8 type 0
[ 7013.874250] sd 4:0:0:0: [sdg] Adjusting the sector count from its reported value: 3999744
[ 7013.874261] sd 4:0:0:0: [sdg] 3999743 512-byte logical blocks: (2.04 GB/1.90 GiB)
[ 7013.885800] sd 4:0:0:0: [sdg] Write Protect is off
[ 7013.885808] sd 4:0:0:0: [sdg] Mode Sense: 68 00 00 08
[ 7013.885813] sd 4:0:0:0: [sdg] Assuming drive cache: write through
[ 7013.888452] sd 4:0:0:0: [sdg] Adjusting the sector count from its reported value: 3999744
[ 7013.889627] sd 4:0:0:0: [sdg] Assuming drive cache: write through
[ 7013.889639]  sdg: sdg1 sdg2
[ 7013.897706] sd 4:0:0:0: [sdg] Adjusting the sector count from its reported value: 3999744
[ 7013.899491] sd 4:0:0:0: [sdg] Assuming drive cache: write through
[ 7013.899503] sd 4:0:0:0: [sdg] Attached SCSI removable disk
[ 7014.500490] FAT: invalid media value (0x2f)
[ 7014.500498] VFS: Can't find a valid FAT filesystem on dev sdg1.
[ 7017.703727] FAT: invalid media value (0x2f)
[ 7017.703736] VFS: Can't find a valid FAT filesystem on dev sdg1.
dale@dale-desktop:~$ dmesg | tail -30
[  364.404115] e1000: eth0 NIC Link is Down
[  366.060382] e1000: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  366.832114] e1000: eth0 NIC Link is Down
[  368.568374] e1000: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 7008.732182] usb 1-2.2: new high speed USB device using ehci_hcd and address 7
[ 7008.842441] usb 1-2.2: configuration #1 chosen from 2 choices
[ 7008.845279] scsi4 : SCSI emulation for USB Mass Storage devices
[ 7008.865017] usb-storage: device found at 7
[ 7008.865022] usb-storage: waiting for device to settle before scanning
[ 7013.864586] usb-storage: device scan complete
[ 7013.865517] scsi 4:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 7013.870485] sd 4:0:0:0: Attached scsi generic sg8 type 0
[ 7013.874250] sd 4:0:0:0: [sdg] Adjusting the sector count from its reported value: 3999744
[ 7013.874261] sd 4:0:0:0: [sdg] 3999743 512-byte logical blocks: (2.04 GB/1.90 GiB)
[ 7013.885800] sd 4:0:0:0: [sdg] Write Protect is off
[ 7013.885808] sd 4:0:0:0: [sdg] Mode Sense: 68 00 00 08
[ 7013.885813] sd 4:0:0:0: [sdg] Assuming drive cache: write through
[ 7013.888452] sd 4:0:0:0: [sdg] Adjusting the sector count from its reported value: 3999744
[ 7013.889627] sd 4:0:0:0: [sdg] Assuming drive cache: write through
[ 7013.889639]  sdg: sdg1 sdg2
[ 7013.897706] sd 4:0:0:0: [sdg] Adjusting the sector count from its reported value: 3999744
[ 7013.899491] sd 4:0:0:0: [sdg] Assuming drive cache: write through
[ 7013.899503] sd 4:0:0:0: [sdg] Attached SCSI removable disk
[ 7014.500490] FAT: invalid media value (0x2f)
[ 7014.500498] VFS: Can't find a valid FAT filesystem on dev sdg1.
[ 7017.703727] FAT: invalid media value (0x2f)
[ 7017.703736] VFS: Can't find a valid FAT filesystem on dev sdg1.
[ 8810.348438] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[ 9057.536096] usb 1-2.2: USB disconnect, address 7
[ 9096.195911] FAT: Unrecognized mount option "group=user" or missing value

---

### Post by pytheas22 on 2010-07-20
Thanks for that information.  It looks like it's expecting there to be a FAT file system, but there's not.  Do you know which file system your devices are formatted with?  On Windows, you should be able to find out by right-clicking on the disk's icon and selecting Properties; I'm sure exactly where, but I think someplace it tells you what the file system is.

Also, exactly what kind of devices are these?  I'm not sure, but at least one of them looks like an iPod; is that true?

---

### Post by dalehartt on 2010-07-20
one is a ipod the other is a memory card (flash) for a camera.  I don't have windows, just ubuntu.

---

### Post by dalehartt on 2010-07-20
my home partition is ext2, the rest ext 3 and swap partitions.  My storage drive is ext 4

---

### Post by pytheas22 on 2010-07-21
Do you know the file system type of the iPod and memory card?  They also have to be formatted with something, and that's what we need to know to figure it out.

If could also be helpful to see the output of these commands while each device is plugged in:
```

fdisk -l
lsusb
```

---

### Post by dalehartt on 2010-07-21
flash card in reader


dale@dale-desktop:~$ fdisk -l
dale@dale-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:08b2 Logitech, Inc. QuickCam Pro 4000
Bus 003 Device 002: ID 03f0:4f11 Hewlett-Packard OfficeJet 5600 (USBHUB)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0781:8919 SanDisk Corp. Card Reader
Bus 001 Device 003: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by dalehartt on 2010-07-21
camera


dale@dale-desktop:~$ fdisk -l
dale@dale-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:08b2 Logitech, Inc. QuickCam Pro 4000
Bus 003 Device 002: ID 03f0:4f11 Hewlett-Packard OfficeJet 5600 (USBHUB)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 04f1:0008 Victor Company of Japan, Ltd GZ-MG30AA/MC500E Digital Video Camera
Bus 001 Device 003: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
dale@dale-desktop:~$

---

### Post by dalehartt on 2010-07-21
ipod, which actually worked today for some reason.


dale@dale-desktop:~$ fdisk -l
dale@dale-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:08b2 Logitech, Inc. QuickCam Pro 4000
Bus 003 Device 002: ID 03f0:4f11 Hewlett-Packard OfficeJet 5600 (USBHUB)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 05ac:1262 Apple, Inc. iPod Nano 3.Gen
Bus 001 Device 003: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
dale@dale-desktop:~$

---

### Post by pytheas22 on 2010-07-21
How are you trying to connect to these devices?  With your camera, a box should pop up when you plug it in asking how you want to access it.  With the iPod, you should use Rhythmbox (under Applications>Sound and Video) to connect--I'm pretty sure you can't mount the iPod as if it's a hard drive (you might be able to do so with your camera and memory card).  If Rhythmbox doesn't work with the iPod, try installing gtkpod from the Ubuntu Software Center and give that a try.

Also, the "fdisk -l" command returned no results because I mistakenly didn't ask you to run it with root privileges.  So I'm sorry to ask again, but you you please post the output of:
```

sudo fdisk -l
```

when your devices are plugged in.

---

### Post by dalehartt on 2010-07-21
When its not going to work I get a message as soon as I plug it in that looks like this


Unable to mount NIKON D2H

Error mounting: mount exited with exit code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

here is the f disk read out

dale@dale-desktop:~$ sudo fdisk -l
[sudo] password for dale: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          12       96358+  83  Linux
/dev/sda2              13        2079    16603177+  83  Linux
/dev/sda3            2080        2808     5855692+  82  Linux swap / Solaris
/dev/sda4            2809        9729    55592932+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0c6c5478

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux

Disk /dev/sdc: 1077 MB, 1077608448 bytes
16 heads, 63 sectors/track, 2088 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        2089     1052330    6  FAT16
dale@dale-desktop:~$

---

### Post by pytheas22 on 2010-07-21
Thanks, that provides helpful information.  Let's try mounting your camera (or whichever device you had plugged in when you got the output for your last post) manually.  Please post the output of:
```

sudo mkdir /mnt/camera
sudo mount /dev/sdc1 /mnt/camera
dmesg | tail -15
ls /mnt/camera
```

Note that some of those commands may have no output.

---

### Post by dalehartt on 2010-07-21
sudo mkdir /mnt/cameradale@dale-desktop:~$ sudo mkdir /mnt/camera
[sudo] password for dale: 
dale@dale-desktop:~$ sudo mkdir /mnt/camera
mkdir: cannot create directory `/mnt/camera': File exists
dale@dale-desktop:~$ sudo mount /dev/sdc1 /mnt/camera
dale@dale-desktop:~$ dmesg | tail -15
[  267.997032] sd 4:0:0:0: [sdg] Mode Sense: 04 00 00 00
[  267.997037] sd 4:0:0:0: [sdg] Assuming drive cache: write through
[  268.003233] sd 4:0:0:1: [sdh] Attached SCSI removable disk
[  268.005865] sd 4:0:0:0: [sdg] Assuming drive cache: write through
[  268.005878]  sdg: sdg1
[  268.525682] sd 4:0:0:0: [sdg] Assuming drive cache: write through
[  268.525694] sd 4:0:0:0: [sdg] Attached SCSI removable disk
[  641.336131] e1000: eth0 NIC Link is Down
[  652.152410] e1000: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
[  656.680145] e1000: eth0 NIC Link is Down
[  658.320396] e1000: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  659.108115] e1000: eth0 NIC Link is Down
[  660.788400] e1000: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1088.283778] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[ 5201.612253] usb 1-2.4: USB disconnect, address 7
dale@dale-desktop:~$ ls /mnt/camera
100NCD2H  DCIM  NIKON001.DSC
dale@dale-desktop:~$

---

### Post by pytheas22 on 2010-07-21
It looks like mounting works from the command line.  After running those commands, if you type:
```

sudo nautilus /mnt/camera
```

are you able to browse through to your photos?

---

### Post by dalehartt on 2010-07-22
it opens up a folder, but that folder is empty.  Not sure the location of my flash drive, when I look at properties and location it says this

location: computer:///

---

### Post by pytheas22 on 2010-07-22
Did you have your flash drive plugged in before?  I thought you were using your camera.

In any case, it seems like you have multiple devices, so let's work with just the camera for now.  Please reboot the computer so you have a clean starting point.  After the reboot, plug in the camera (and only the camera), then run the following commands.  The commands should produce no output; if you get any output, please post it here:
```

sudo mount /dev/sdc1 /mnt/camera
sudo nautilus /mnt/camera
```

Can you now browse your camera's files?  If this works, we can move onto the other devices, and hopefully ultimately figure out a way for you to access the files without having to use the command line.

---

### Post by dalehartt on 2010-07-23
Sorry for the confusion, I use a memory card for my camera.  The Nautilaus thing worked, I can access the pictures.


dale@dale-desktop:~$ sudo mount /dev/sdc1 /mnt/camera
[sudo] password for dale: 
dale@dale-desktop:~$ sudo nautilus /mnt/camera
Initializing nautilus-gdu extension
** No session dbus found. Starting one **
[Info  08:44:36.712] Initializing DBus
[Info  08:44:36.984] Initializing Mono.Addins
[Info  08:44:39.434] Starting new FSpot server (f-spot 0.6.1.5)

(f-spot:7640): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem
[Info  08:44:41.159] Hack for gnome-settings-daemon engaged

(f-spot:7640): GLib-WARNING **: Invalid file descriptor.


(f-spot:7640): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.

---

### Post by dalehartt on 2010-07-23
today it opened, but now root has ownership over the files and I can't touch them.

---

### Post by dalehartt on 2010-07-23
I wish my computer had now ownership of files.

---

### Post by pytheas22 on 2010-07-23
> today it opened, but now root has ownership over the files and I can't touch them.

Do you mean it opened on its own, automatically, when you plugged the device in?  That's a good sign--if that's happening, we should be able to make it open automatically with permissions such that you can access the files.

Also keep in mind that you can always open a file browser as root by typing:
```

sudo nautilus
```

to access files that are owned by root.  I know this isn't a good solution, but at least it will let you get to your files until we figure out why your disks aren't being auto-mounted with normal permissions, as they're supposed to be.

---

### Post by dalehartt on 2010-07-23
it didn't open automatically, it was from the command line.  it always pops up, then I get the error message about not mounting.

---

### Post by pytheas22 on 2010-07-24
Too bad--I was hoping it mounted automatically.  If you plug the device in and open up your Home folder from the Places menu, do you at least see an entry for the device in the pane on the left-hand side?  (If you're not sure what I'm referring to, I can post a screenshot.)

Another thing worth testing would be to create a new user using the utility at System>Administration>Users and Groups.  Then log in as the new user and see if devices are auto-mounted there.  This will let us know whether the issue is specific to your user configuration, or is a system-wide problem.

---

### Post by dalehartt on 2010-07-25
I'll check on the new user thing, it does show up in the home file though.

---

### Post by dalehartt on 2010-07-26
a new user can't open it either.

---

### Post by pytheas22 on 2010-07-26
Well, at least we know it's a system-wide problem.  In some senses that's actually easier to troubleshoot.
> 
I'll check on the new user thing, it does show up in the home file though.

If you click on the entry for your disk in the side bar in a normal window (not one that you opened with "sudo nautilus"), does the disk mount and allow you to browse your files?

In any case, I'm still not sure why auto-mounting isn't working for you, but install gnome-volume-manager may help.  gnome-volume-manager is a service that auto-mounts removable disks when they're plugged in, without requiring any passwords.  It's not installed by default in Ubuntu 10.04, but you can install it with these commands:
```

wget http://launchpadlibrarian.net/26064884/gnome-mount_0.8-2ubuntu1_i386.deb
wget http://launchpadlibrarian.net/27079687/gnome-volume-manager_2.24.1-3ubuntu1_i386.deb
sudo dpkg -i gnome*deb
```

Or, if you are using 64-bit Ubuntu, run these commands instead:
```

wget http://launchpadlibrarian.net/26064988/gnome-mount_0.8-2ubuntu1_amd64.deb
wget http://launchpadlibrarian.net/27079681/gnome-volume-manager_2.24.1-3ubuntu1_amd64.deb
sudo dpkg -i gnome*deb
```

If you're not sure whether you're using 64-bit Ubuntu, type:
```

uname -m
```

If the output is i686, you're using a 32-bit operating system.  If it's x86_64, you have 64-bit.

After running the commands, reboot, and with any luck your devices will be mounted on their own so that you can browse their files without having to use "sudo nautilus".

---

### Post by dalehartt on 2010-07-27
same error message unfortunatly.

---

### Post by dalehartt on 2010-07-27
I think the problem is with the mounting....  How can we figure out why it won't mount?  Thank you so much with your fantastic help.

---

### Post by pytheas22 on 2010-07-28
I don't think the problem is with mounting itself, since you can mount devices without a problem if you do it manually from the command line as root.  The problem seems to lie somewhere with the daemon that's supposed to auto-mount devices when they're plugged in with permissions such that you can access them without typing "sudo".

What is the output of:
```

cat /etc/fstab
```

That will show me the contents of your fstab file, which tells the system how it should mount some devices.  I'm wondering if something got mucked up there that's confusing the computer.

Also, just so we're clear, how many different devices have you tried mounting?  I'm aware of an iPod and a memory card that you use for your camera.  Was there anything else you've tried?  Have you been able to plug in any device--such as an ordinary USB memory stick--and get that to mount automatically without any manual intervention on your part?

Thanks for all your patience.

---

### Post by dalehartt on 2010-07-30
sorry have been gone.

dale@dale-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                     0  0  
# / was on /dev/sda2 during installation
UUID=729ddfd7-fdc1-4140-bb14-15a0e6a47c16  /               ext3         relatime,errors=remount-ro   0  1  
# /boot was on /dev/sda1 during installation
UUID=1983a9e1-fda4-49a2-9c83-ffdcb9077555  /boot           ext2         relatime                     0  2  
# /home was on /dev/sda4 during installation
UUID=e8f09f9a-8357-401c-bd3d-c6b00be4e619  /home           ext3         relatime                     0  2  
# swap was on /dev/sda3 during installation
UUID=fcd0dd9c-236d-4fe1-8c4b-509920189e31  none            swap         sw                           0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8        0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8     0  0  
/dev/sdb1                                  /media/storage  ext4         users,user,owner             0  0  
/dev/sdg1                                  /media/sdg1     vfat         users                        0  0  
/dev/sdc1                                  /media/sdc1     vfat         owner,group=user,users,user  0  0  
/dev/sdf1                                  /media/sdf1     vfat         users

---

### Post by pytheas22 on 2010-08-01
Sorry for not responding sooner--I was moving the last couple days.

The bottom four lines in your /etc/fstab file wouldn't exist by default, so I assume you probably added them manually in an attempt to get your devices to automount?  In any case, some of the options there are incorrect, which is probably what's preventing the devices from mounting.  Please open the fstab file for editing by typing:
```

sudo gedit /etc/fstab
```

and then replace the final four lines with this:
```

/dev/sdb1 /media/sdb1 ext4 user,owner 0 0
/dev/sdc1 /media/sdc1 vfat users,owner 0 0
/dev/sdd1 /media/sdd1 vfat users,owner 0 0
/dev/sde1 /media/sde1 vfat users,owner 0 0
/dev/sdf1 /media/sdf1 vfat users,owner 0 0
/dev/sdg1 /media/sdg1 vfat users,owner 0 0
```


Then save and close the file.  You should also run these commands in order to sure that the mountpoints you want to use exist:
```

sudo mkdir /media/sdb1
sudo mkdir /media/sdc1
sudo mkdir /media/sdd1
sudo mkdir /media/sde1
sudo mkdir /media/sdf1
sudo mkdir /media/sdg1
```

Finally, reboot with your media plugged in and it should be mounted automatically under the /media directory, with permissions that allow you to edit it.  If you plug the devices in after booting, you will need to type:
```

sudo mount -a
```

to mount them.

If this still doesn't work, please post the output of:

cat /etc/fstab```

dmesg | grep -e dev -e mount -ie fat
```

---

### Post by dalehartt on 2010-08-08
dale@dale-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                     0  0  
# / was on /dev/sda2 during installation
UUID=729ddfd7-fdc1-4140-bb14-15a0e6a47c16  /               ext3         relatime,errors=remount-ro   0  1  
# /boot was on /dev/sda1 during installation
UUID=1983a9e1-fda4-49a2-9c83-ffdcb9077555  /boot           ext2         relatime                     0  2  
# /home was on /dev/sda4 during installation
UUID=e8f09f9a-8357-401c-bd3d-c6b00be4e619  /home           ext3         relatime                     0  2  
# swap was on /dev/sda3 during installation
UUID=fcd0dd9c-236d-4fe1-8c4b-509920189e31  none            swap         sw                           0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8        0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8     0  0  
/dev/sdb1 /media/sdb1 ext4 user,owner 0 0
/dev/sdc1 /media/sdc1 vfat users,owner 0 0
/dev/sdd1 /media/sdd1 vfat users,owner 0 0
/dev/sde1 /media/sde1 vfat users,owner 0 0
/dev/sdf1 /media/sdf1 vfat users,owner 0 0
/dev/sdg1 /media/sdg1 vfat users,owner 0 0
dale@dale-desktop:~$

---

### Post by dalehartt on 2010-08-08
don't know if I did this right but its not working at all right now. I get this message when trying to mount.

dale@dale-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                     0  0  
# / was on /dev/sda2 during installation
UUID=729ddfd7-fdc1-4140-bb14-15a0e6a47c16  /               ext3         relatime,errors=remount-ro   0  1  
# /boot was on /dev/sda1 during installation
UUID=1983a9e1-fda4-49a2-9c83-ffdcb9077555  /boot           ext2         relatime                     0  2  
# /home was on /dev/sda4 during installation
UUID=e8f09f9a-8357-401c-bd3d-c6b00be4e619  /home           ext3         relatime                     0  2  
# swap was on /dev/sda3 during installation
UUID=fcd0dd9c-236d-4fe1-8c4b-509920189e31  none            swap         sw                           0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8        0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8     0  0  
/dev/sdb1 /media/sdb1 ext4 user,owner 0 0
/dev/sdc1 /media/sdc1 vfat users,owner 0 0
/dev/sdd1 /media/sdd1 vfat users,owner 0 0
/dev/sde1 /media/sde1 vfat users,owner 0 0
/dev/sdf1 /media/sdf1 vfat users,owner 0 0
/dev/sdg1 /media/sdg1 vfat users,owner 0 0
dale@dale-desktop:~$

---

### Post by dino99 on 2010-08-08
if you want to use the easy way, install mountmanager and set your prefs into "system admin mountmanager, no need to tweak fstab or mtab

---

### Post by pytheas22 on 2010-08-10
> 
don't know if I did this right but its not working at all right now. I get this message when trying to mount.

dale@dale-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda2 during installation
UUID=729ddfd7-fdc1-4140-bb14-15a0e6a47c16 / ext3 relatime,errors=remount-ro 0 1
# /boot was on /dev/sda1 during installation
UUID=1983a9e1-fda4-49a2-9c83-ffdcb9077555 /boot ext2 relatime 0 2
# /home was on /dev/sda4 during installation
UUID=e8f09f9a-8357-401c-bd3d-c6b00be4e619 /home ext3 relatime 0 2
# swap was on /dev/sda3 during installation
UUID=fcd0dd9c-236d-4fe1-8c4b-509920189e31 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sdb1 /media/sdb1 ext4 user,owner 0 0
/dev/sdc1 /media/sdc1 vfat users,owner 0 0
/dev/sdd1 /media/sdd1 vfat users,owner 0 0
/dev/sde1 /media/sde1 vfat users,owner 0 0
/dev/sdf1 /media/sdf1 vfat users,owner 0 0
/dev/sdg1 /media/sdg1 vfat users,owner 0 0
dale@dale-desktop:~$

What command were you trying to use to mount?  Above, you posted the output of "cat /etc/fstab", which is the command to display your fstab configuration file, not to mount.  To mount, you should plug in your device and type "sudo mount -a".

If you like, you can also try dino99's useful suggestion and install mountmanager with:
```

sudo apt-get install mountmanager
```

I think the interface for mountmanager is a little confusing, but it may help you.

---

### Post by QLee on 2010-08-10
dalehartt,

Are you doing any in/out operations, for example deleting pictures, while you have the camera plugged in, and, if so, are you letting the operation completely finish and then properly unmounting the device before you unplug it?

When it doesn't mount, have you tried running a fsck on the unmounted device and if and when it completes successfully does it then mount?

---

### Post by cmcanulty on 2010-08-10
Whenever I get that error message I plug it into a windows machine and then safely remove it. Ubuntu has a big problem with mounting.It constantly unmounts my ext hard drives and then I have to find a windows machine and unmount then Ubuntu sees it again. This is a fault of some hardware not working well in Linux especially seagate and western digital though a lot work fine.

---

### Post by QLee on 2010-08-10
Well, actually, it is a result of Windows being more tolerant of such devices being removed unsafely, Ubuntu prefers to see a device that has been unmounted properly so that it is confident the data is good. I prefer the GNU/Linux behaviour but not everyone agrees.

---

### Post by cmcanulty on 2010-08-11
With mine it is the problem that some external hard drives automatically spin down and then in Linux they unmount themselves and then won't remount without  windows machine.

---

### Post by dalehartt on 2010-08-12
> **QLee said:**
> dalehartt,

Are you doing any in/out operations, for example deleting pictures, while you have the camera plugged in, and, if so, are you letting the operation completely finish and then properly unmounting the device before you unplug it?

When it doesn't mount, have you tried running a fsck on the unmounted device and if and when it completes successfully does it then mount?

now im having a hard time getting at my pictures at all

---

### Post by dalehartt on 2010-08-12
> **cmcanulty said:**
> Whenever I get that error message I plug it into a windows machine and then safely remove it. Ubuntu has a big problem with mounting.It constantly unmounts my ext hard drives and then I have to find a windows machine and unmount then Ubuntu sees it again. This is a fault of some hardware not working well in Linux especially seagate and western digital though a lot work fine.

well that would be annoying for me because every computer in my house is linux lol.

---

### Post by dalehartt on 2010-08-12
> **pytheas22 said:**
> What command were you trying to use to mount?  Above, you posted the output of "cat /etc/fstab", which is the command to display your fstab configuration file, not to mount.  To mount, you should plug in your device and type "sudo mount -a".

If you like, you can also try dino99's useful suggestion and install mountmanager with:
```

sudo apt-get install mountmanager
```

I think the interface for mountmanager is a little confusing, but it may help you.

I showed you my fstab to see if I did it right, which I suspect I didn't because stuff has been jacked since.

---

### Post by pytheas22 on 2010-08-13
> I showed you my fstab to see if I did it right, which I suspect I didn't because stuff has been jacked since.

Ah, that makes sense--I misunderstood earlier.

Unfortunately, if modifying /etc/fstab also failed, I'm not sure why this won't work and I'm essentially out of ideas on what else to try, besides what's already been mentioned.  I don't want to run you in circles with this if I don't have any more good solutions to suggest.

So unfortunately, I have no idea why this won't work on your computer and I'm not sure that there's a way to mount your devices, besides doing it manually from the command line and then accessing the files with the "sudo nautilus" command, as you did earlier in this thread (if you want a better explanation of how to mount devices manually from the command line so that you can do it with any memory device, let me know).

Another idea is to try reinstalling Ubuntu from scratch.  That may or may not make sense, depending on how much time you've invested setting up your current system, but it's possible that auto-mounting would work if you go back to a "clean slate."  You may have changed some setting after installing the operating system that prevents it from auto-mounting memory devices like it's supposed to, and like Windows and OS X do.

I'm very sorry I can't offer any more suggestions on a good fix for the problem, but let me know if you have any questions or if there's any other assistance I can provide.

---

### Post by dalehartt on 2010-08-14
thank you very much, can you give me a explanation of mounting manually?

---

### Post by dalehartt on 2010-08-14
can I just redo my fstab?

---

### Post by pytheas22 on 2010-08-14
You can edit your fstab file by typing "sudo gedit /etc/fstab" and restore it to the defaults, which should be just:

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda2 during installation
UUID=729ddfd7-fdc1-4140-bb14-15a0e6a47c16 / ext3 relatime,errors=remount-ro 0 1
# /boot was on /dev/sda1 during installation
UUID=1983a9e1-fda4-49a2-9c83-ffdcb9077555 /boot ext2 relatime 0 2
# /home was on /dev/sda4 during installation
UUID=e8f09f9a-8357-401c-bd3d-c6b00be4e619 /home ext3 relatime 0 2
# swap was on /dev/sda3 during installation
UUID=fcd0dd9c-236d-4fe1-8c4b-509920189e31 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0 
```

However, I don't think fstab is the problem.  fstab tells the system how to mount your internal hard disks, but it's not supposed to be responsible for auto-mounting USB sticks and memory cards when they're plugged in.  A Gnome process is supposed to take care of that.  It's possible to create entries in fstab for mounting external media as well as internal media if you want, but that should not be necessary in modern Ubuntu.  But in any case, setting /etc/fstab back to the defaults won't hurt anything, since the entries you added don't seem to do anything anyway.

As for mounting a drive manually from the command line, there are three things you need to know: 1) the device identifier that corresponds to the drive; 2) the partition number of the partition that you want to mount; and 3) the mountpoint.  I'll explain below how to determine this information.

**Device identifier**: every storage device attached to your computer--whether it's a hard drive, USB stick or anything else--is automatically assigned an identifier when it's plugged in.  In most cases, this identifier is in the form of /dev/sdX, where X is a letter.  /dev/sda usually corresponds to your primary hard disk, /dev/sdb is the second disk or memory card, /dev/sdc is the third, etc.

**Partition number**: each partition of each device is assigned a number, beginning with 1.  So /dev/sda1 represents the first partition of the device /dev/sda, while /dev/sda2 is the second partition of that device and /dev/sdb1 is the first partition of /dev/sdb, etc.

**Mountpont**: a mountpoint is a directory somewhere on your system where the files on your device will be accessible once it's mounted.  The directory can be anywhere you want, but the conventional approach is to create a mountpoint for each partition under the /mnt directory of your system.  For example, if the device and partition you're going to mount are /dev/sdb1, your mountpoint could be /mnt/sdb1.

If the mountpoint doesn't exist, you have to create it using the "mkdir" (make directory) command, e.g.:
```

sudo mkdir /mnt/sdb1
```

**Mounting**: once you have the device identifier, partition number and mountpoint sorted out, mounting the device is done using the command "mount".  The syntax is:
```

sudo mount device-identifier-partition mountpoint
```

So, to mount /dev/sdb1 on the mountpoint /mnt/sdb1, you would type:
```

sudo mount /dev/sdb1 /mnt/sdb1
```

You could then open a file browser with "sudo nautilus", browse to the location /mnt/sdb1 and view your files.

To unmount a device once you're done with it, use the "umount" command (not unmount, just umount), e.g.:

```
sudo umount /dev/sdb1
```

This process probably seems convoluted, but hopefully it makes sense once you try it a few times.  Once you understand how mounting works, you should be able to mount any device after you figure out what its identifier is.

If you only have one internal hard disk, then any USB stick or memory card that you plug in will probably be assigned /dev/sdb and /dev/sdb1 will be the partition you want to mount.  But if you're not sure what the identifier and partition is, a useful way to figure it out is by running the command:
```

sudo fdisk -l
```

The output will include sections that look like this:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        4344    19535040   83  Linux
/dev/sda3            4345        4709     2931862+  82  Linux swap / Solaris
/dev/sda4            4710       24321   157533390   83  Linux

[ ...more stuff in between... ]

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         792     3118073    c  W95 FAT32 (LBA)
```

In the example above, I can see that /dev/sda has four partitions.  /dev/sda1 is formatted as NTFS, the Windows file system, so I know that it represents my Windows partition--so if I wanted to access my Windows files, I would mount /dev/sda1.  The other partitions of /dev/sda are Linux.  I can also see that /dev/sdb has one partition formatted as FAT32, which is a DOS file system used on many portable USB sticks.  This is a good tip off that /dev/sdb1 is a USB stick, so if I wanted to access its files, I would mount /dev/sdb1.

Sorry to write so much, but hopefully this makes sense and will allow you to access your files in the absence of a better solution.  Let me know if you have any questions.

---

### Post by dalehartt on 2010-08-14
that is absolutely fantastic.  I believe the people on this forums attitudes towards idiots like myself will be the reason for its ultimate success.  Thank you so much, I learn more everyday.

---

### Post by pytheas22 on 2010-08-15
Don't worry, we were all "idiots" once, if by idiots you mean beginners.  Sorry again that we couldn't figure out a better solution for you, but let me know if you have any more questions about anything.

---

