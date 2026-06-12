---
title: "can't mount or use Kingston 8GB usb"
date: 2010-07-19
forum: General Help
---

### Post by the_storm on 2010-07-19
hey guys, I have problem with my  kingston 8gb usb. When I attached it to the computer, it doesn't mount automatically. consequently I type in the terminal ```
lsdisk
``` to see whether it is connected or not 
and this is the answer 
```
storm@storm-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 15d9:0a4c Dexon 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 015: ID 0951:1625 Kingston Technology 
Bus 001 Device 004: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```you see Kingston Technology so it is connected. after that I type 
```
fdisk -l
``` in order to see all attached storage devices and their partitions but I Found nothing  
this is the answer 
 ```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1c091c08

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6084    48869698+  83  Linux
/dev/sda2            6085        7057     7815622+   5  Extended
/dev/sda5            6085        7057     7815591   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x33853384

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12748   102398278+   7  HPFS/NTFS
/dev/sdb2           12749       38245   204804652+   f  W95 Ext'd (LBA)
/dev/sdb5           12749       38245   204804621    7  HPFS/NTFS

```the sda is my first internal hard disk and the sdb is the second internal hard disk but the Kingston usb is not exists and therefore I can't mount it 
any help guys ?

---

### Post by the_storm on 2010-07-19
one more thing guys, when i disconnect the usb and reconnect it again this is the output 
```
[50165.330949] usb 1-3: USB disconnect, address 15
[50167.696063] usb 1-3: new high speed USB device using ehci_hcd and address 16
[50167.830905] usb 1-3: configuration #1 chosen from 1 choice
[50167.831202] scsi11 : SCSI emulation for USB Mass Storage devices
[50167.831393] usb-storage: device found at 16
[50167.831396] usb-storage: waiting for device to settle before scanning
```

I think there is something wrong .. whit my Ubuntu, cause when I tried my usb on other machine using Ubuntu too, it did work .. !! 

thanks any help guys ?

---

### Post by the_storm on 2010-07-19
any help guys ?? ??

---

### Post by the_storm on 2010-07-20
guys ..? Is it that difficult or what  ?? 
why no one answers ??

---

### Post by dabl on 2010-07-20
With your USB stick inserted in the machine, run these in a terminal and post the outputs:

```
sudo fdisk -lu
```

```
sudo lsusb
```

```
sudo dmidecode -t bios
```

---

### Post by the_storm on 2010-07-20
> **dabl said:**
> With your USB stick inserted in the machine, run these in a terminal and post the outputs:

```
sudo fdisk -lu
``````
sudo lsusb
``````
sudo dmidecode -t bios
```


here is the output dude 

```
storm@storm-desktop:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1c091c08

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    97739459    48869698+  83  Linux
/dev/sda2        97739460   113370704     7815622+   5  Extended
/dev/sda5        97739523   113370704     7815591   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x33853384

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   204796619   102398278+   7  HPFS/NTFS
/dev/sdb2       204796620   614405924   204804652+   f  W95 Ext'd (LBA)
/dev/sdb5       204796683   614405924   204804621    7  HPFS/NTFS

storm@storm-desktop:~$ sudo lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 15d9:0a4c Dexon 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 017: ID 0951:1625 Kingston Technology 
Bus 001 Device 004: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


storm@storm-desktop:~$ sudo dmidecode -t bios
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: Award Software International, Inc.
    Version: F3
    Release Date: 11/14/2008
    Address: 0xE0000
    Runtime Size: 128 kB
    ROM Size: 512 kB
    Characteristics:
        PCI is supported
        PNP is supported
        APM is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        EDD is supported
        5.25"/360 KB floppy services are supported (int 13h)
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 KB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        LS-120 boot is supported
        ATAPI Zip drive boot is supported
        BIOS boot specification is supported
        Targeted content distribution is supported

Handle 0x0018, DMI type 13, 22 bytes
BIOS Language Information
    Installable Languages: 3
        n|US|iso8859-1
        n|US|iso8859-1
        r|CA|iso8859-1
    Currently Installed Language: n|US|iso8859-1





```

---

### Post by the_storm on 2010-07-20
dude ??

---

### Post by the_storm on 2010-07-20
any reply from any one ?

---

### Post by the_storm on 2010-07-21
??

---

### Post by cliffdodger on 2010-07-21
Well it does appear your usb drive gets connected, just not mounted... So this should help you with the info to get it to automount.

[http://www.linuxconfig.org/Howto_mount_USB_drive_in_Linux](http://www.linuxconfig.org/Howto_mount_USB_drive_in_Linux)

---

### Post by the_storm on 2010-07-21
> **cliffdodger said:**
> Well it does appear your usb drive gets connected, just not mounted... So this should help you with the info to get it to automount.

[http://www.linuxconfig.org/Howto_mount_USB_drive_in_Linux](http://www.linuxconfig.org/Howto_mount_USB_drive_in_Linux)

No, my usb drive is not detected. look at the fdisk -l you will see that the inernal hard disk is only connected but the computer doesn't detect the usb. On the other hand, if you can see the command lsusb you will find this line 
" Bus 001 Device 022: ID 0951:1625 Kingston Technology" 
which means the usb is connected but not detected 

any help ??

---

### Post by gordintoronto on 2010-07-21
Have you tried sudo gparted? (You might need to install it first.) There is a drop-down box to select the devices, it will begin by showing your first hard drive.

I don't think you have mentioned what version of Ubuntu you are using. How is the flash drive formatted?

---

### Post by the_storm on 2010-07-21
> **gordintoronto said:**
> Have you tried sudo gparted? (You might need to install it first.) There is a drop-down box to select the devices, it will begin by showing your first hard drive.

I don't think you have mentioned what version of Ubuntu you are using. How is the flash drive formatted?

I sudo gparted but it didn't detect my usb drive it only detected my internal hard drive
I am using Ubuntu version 10.04 and the flash format id fat32 
 am sure the problem is not in the usb but I think there is something is disabled in my Ubuntu. look I have run ubuntu livecd on the same computer and I attached the usb mass storage, and it work !!
and when I attached it to my laptop which has ubuntu 10.04 is did work 
but when I attached it to my PC This message appears 
 "waiting for device to settle before scanning"

and the scan never complete ?
What is the solution ??

---

### Post by the_storm on 2010-07-23
bump ??

---

### Post by the_storm on 2010-08-04
guyyys any help ?

---

### Post by Uslayme on 2010-08-06
I too had very similar symptoms relating to my many attempts to mount my usb "thumbdrive" in this Lucid Lynx distro. 10.04    This same thumbdrive worked just fine in 8.10 and Windows. After reading over 150 pages of threads in various forums, I concluded this was either a bug or even a compatibility issue with my Lexar Firefly 4 Gig device.  Not being deterred, I scrounged an old 64M stick that I had laying around, and lo and behold it mounted! 
I had of course already exhausted all suggestions that I had gathered from those 150 some pages, of "Dmesg, lsusb, modprobe, lspci, lsmod etc" and I did Install the "USBMount" software through the sofware manager. Anyway, I got to thinking (sometimes this works for me) my 64M antique thumbdrive showed up in Ubuntu's Disk Utility as partitioned MBR with Fat16 filesystem....what if I were to duplicate this structure with my 4G Lexar? Here is what made my Lexar JD Firefly work great in Lucid Lynx....

I booted to my Windows XP (I know), plugged in my Firefly..it was immediately recognized. I BACKED-UP the data that was on the drive.   Then I right clicked "My Computer" selected "Manage" selected "Disk Management" and then selected my Firefly in the right hand panel. I then right clicked my Firefly and chose format, entered some weird name in "Volume Label", then I changed the "File System" to "FAT", as opposed to "Fat32", left the allocation size to Default, and clicked "OK". You will get a couple of "confirmation" boxes suggesting dire consequences should you continue, but continue I did. Note...one of the consequences will be loss of data, so I am assuming that you previously saved that stuff...right?  After your drive is reformatted simply close the disk management console, "Safely remove hardware" via the icon in your task bar and boot into Ubuntu. If your "stick" performs as mine did, it should be mounted as your Lucid Lynx displays its environment :) Do also note, that I previously installed "USBMOUNT" from Ubuntu's Software Center, so you may consider this if for some reason you do not experience the success that I did. Once my stick mounted (YAH) I went into System > Administration > Disk Utility, then I unmounted and reformatted the drive and the volume, to "Fat32" (my preference) and viola, my Lexar works great on Lucid Lynx 10.04.  Thanks to all who contribute to these forums, I love to learn!

---

