---
title: "Cannot create partition: &quot;Unable to read /dev/sdd&quot;"
date: 2012-10-07
forum: General Help
---

### Post by antiartist on 2012-10-07
I connected a new internal HDD to my headless ubuntu server and would like to partition it so I can copy my existing system disk to it (the existing disk is way low on free space and the new disk is larger.)

The disk shows in /dev/sdd (there is not sdd1 or any partitions showing).  Yet the new disk does not show up using fdisk -l  and attempts to mount keep referring to fstab.

```
tom@HouseMedia:/$ mount /dev/sdd
mount: can't find /dev/sdd in /etc/fstab or /etc/mtab
tom@HouseMedia:/$ mount /dev/sdd1
mount: can't find /dev/sdd1 in /etc/fstab or /etc/mtab
```

I had previously mounted and partition this drive but after using dd to restore a disk image of my existing system disk, the new disk was still empty.  I'm a little lost on what exactly is wrong and would appreciate some help on getting back to square one again!

---

### Post by bab1 on 2012-10-07
> **antiartist said:**
> I connected a new internal HDD to my headless ubuntu server and would like to partition it so I can copy my existing system disk to it (the existing disk is way low on free space and the new disk is larger.)

The disk shows in /dev/sdd (there is not sdd1 or any partitions showing).  Yet the new disk does not show up using fdisk -l  and attempts to mount keep referring to fstab.

```
tom@HouseMedia:/$ mount /dev/sdd
mount: can't find /dev/sdd in /etc/fstab or /etc/mtab
tom@HouseMedia:/$ mount /dev/sdd1
mount: can't find /dev/sdd1 in /etc/fstab or /etc/mtab
```

I had previously mounted and partition this drive but after using dd to restore a disk image of my existing system disk, the new disk was still empty.  I'm a little lost on what exactly is wrong and would appreciate some help on getting back to square one again!

You need to partition the new disk (fdisk and mk2fs) before you can mount it.  If the disk is larger than 2GB then you will need to use parted (gparted) to partition the disk.

In any event you mount partitions (sdd1) not disks (sdd).

---

### Post by antiartist on 2012-10-07
> **bab1 said:**
> You need to partition the new disk (fdisk and mk2fs) before you can mount it.  If the disk is larger than 2GB then you will need to use parted (gparted) to partition the disk.

In any event you mount partitions (sdd1) not disks (sdd).

Thanks for the clarification about what I'm mounting (partitions, not disks).  I get confused :)

Using fdisk to create the partitions isn't working...
```

tom@HouseMedia:~$ sudo fdisk /dev/sdd
[sudo] password for tom:

Unable to read /dev/sdd
tom@HouseMedia:~$
 
```

Both disks are less than 2 TB (which is what I assume you meant, not 2 GB).

---

### Post by bab1 on 2012-10-07
> **antiartist said:**
> Thanks for the clarification about what I'm mounting (partitions, not disks).  I get confused :)

Using fdisk to create the partitions isn't working...
```

tom@HouseMedia:~$ sudo fdisk /dev/sdd
[sudo] password for tom:

Unable to read /dev/sdd
tom@HouseMedia:~$
 
```

Both disks are less than 2 TB (which is what I assume you meant, not 2 GB).

Yes I meant 2TB.

Post the output of```
sudo fdisk -l
```

---

### Post by antiartist on 2012-10-07
The disk doesn't show in fdisk -l

```
tom@HouseMedia:~$ sudo fdisk -l

Disk /dev/sda: 10.3 GB, 10254827520 bytes
255 heads, 63 sectors/track, 1246 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00018313

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1188     9537536   83  Linux
/dev/sda2            1188        1247      474113    5  Extended
/dev/sda5            1188        1247      474112   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005f5c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3e6caab7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      182401  1465136001    7  HPFS/NTFS
tom@HouseMedia:~$

```

---

### Post by bab1 on 2012-10-07
> **antiartist said:**
> The disk doesn't show in fdisk -l

```
tom@HouseMedia:~$ sudo fdisk -l

Disk /dev/sda: 10.3 GB, 10254827520 bytes
255 heads, 63 sectors/track, 1246 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00018313

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1188     9537536   83  Linux
/dev/sda2            1188        1247      474113    5  Extended
/dev/sda5            1188        1247      474112   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005f5c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3e6caab7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      182401  1465136001    7  HPFS/NTFS
tom@HouseMedia:~$

```
If it can't see it it can't partition it.  How is the HDD attached (internal, USB or eSATA)?  If it is USB then what do you get with```
lsusb
```

[COLOR="Blue"]Edit:  What do you get if with this[/COLOR]```
sudo lshw
```

---

### Post by antiartist on 2012-10-07
it's currently attached via USB but once this is all finished, I intend to connect it internally.

Aaaaand, I have no idea which one of these entries is the disk.  The Seagate entry is another external usb disk that is connected.  I'm not sure what the Lite-on entry would be as the new disk I am attempting to make use of is made by Hitachi.  thoughts?
  
```
tom@HouseMedia:~$ lsusb
Bus 002 Device 002: ID 04ca:002a Lite-On Technology Corp.
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 001 Device 005: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
Bus 001 Device 002: ID 0bc2:3300 Seagate RSS LLC
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
tom@HouseMedia:~$

```

Using "sudo lshw" returned a lot of stuff.  I'm pretty sure the top portion of the output was cut off but here's what was left visible:

```
½ï¿½ïï¿½ï¿½ï¿½ï¿½ïï¿½ï¿½ï¿½ï¿½<ï¿½}ï¿½ï¿½ï¿½}ï¿½ï¿½ïï¿½ï¿½ modified=2012-09-03 00:08:40 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2012-10-04 23:31:13 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 463MiB
                capacity: 463MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 463MiB
                   capabilities: nofs
        *-disk:1
             description: ATA Disk
             product: ST3320820A
             vendor: Seagate
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/sdb
             version: 3.AA
             serial: 5QF1VYTG
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=0005f5c2
           *-volume
                description: EXT3 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.1.0,1
                logical name: /dev/sdb1
                logical name: /mediastorage
                version: 1.0
                serial: 26bc4db0-3e1f-4e7c-af3a-de0351fa35b1
                size: 298GiB
                capacity: 298GiB
                capabilities: primary journaled extended_attributes large_files recover ext3 ext2 initialized
                configuration: created=2011-02-13 14:37:08 filesystem=ext3 modified=2012-10-04 23:31:13 mount.fstype=ext3 mount.options=rw,nosuid,nodev,noexec,relatime,errors=continue,data=ordered mounted=2012-10-04 23:31:13 state=mounted
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth1
          version: a2
          serial: 00:1b:b9:55:a8:86
          size: 100000000
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.0.111 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
          resources: irq:27 memory:fe02d000-fe02dfff ioport:ec00(size=8)
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          logical name: scsi5
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:d800(size=16) memory:fe02c000-fe02cfff
        *-cdrom
             description: DVD-RAM writer
             product: DVDRRW GSA-H30L
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: S755
             serial: [HL-DT-STDVDRRW GSA-H30L S75506/12/26ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:24 ioport:b000(size=4096) memory:fde00000-fdefffff ioport:fdd00000(size=1048576)
     *-pci:2
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:25 ioport:a000(size=4096) memory:fdc00000-fdcfffff ioport:fdb00000(size=1048576)
     *-pci:3
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:26 ioport:9000(size=4096) memory:fda00000-fdafffff ioport:fd900000(size=1048576)
     *-display
          description: VGA compatible controller
          product: C61 [GeForce 6150SE nForce 430]
          vendor: nVidia Corporation
          physical id: 10
          bus info: pci@0000:00:0d.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi bus_master cap_list rom
          configuration: driver=nouveau latency=0
          resources: irq:22 memory:fb000000-fbffffff memory:e0000000-efffffff(prefetchable) memory:fc000000-fcffffff memory:80000000-8001ffff(prefetchable)
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi:0
          physical id: 11
          bus info: usb@1:1
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Desktop
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdc
             version: 0130
             serial: 2GHN6GFL
             size: 1397GiB (1500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=4 signature=3e6caab7
           *-volume
                description: Windows FAT volume
                vendor: mkdosfs
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdc1
                logical name: /mediastorage2
                version: FAT32
                serial: 228f-2d10
                size: 1397GiB
                capacity: 1397GiB
                capabilities: primary fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,noexec,relatime,uid=1000,gid=1000,fmask=0000,dmask=0000,allow_utime=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
     *-scsi:1
          physical id: 12
          bus info: usb@1:6
          logical name: scsi7
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@7:0.0.0
             logical name: /dev/sdd
     *-scsi:2
          physical id: 13
          bus info: usb@1:9
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sde
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@6:0.0.1
             logical name: /dev/sdf
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@6:0.0.2
             logical name: /dev/sdg
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@6:0.0.3
             logical name: /dev/sdh

```

---

### Post by bab1 on 2012-10-07
> **antiartist said:**
> it's currently attached via USB but once this is all finished, I intend to connect it internally.

Aaaaand, I have no idea which one of these entries is the disk.  The Seagate entry is another external usb disk that is connected.  I'm not sure what the Lite-on entry would be as the new disk I am attempting to make use of is made by Hitachi.  thoughts?
  

I assume you are using Ubuntu 12.04 and that the udev daemon didn't enumerate the Hitachi disk when you plugged it in.  I would reboot the system and see what you get with *lsusb *again.  To see all the output of *sudo lshw* you dump it to a file in your home dir like this```
sudo lshw > hardware.txt
```...then you can look for the Hitachi disk in the file.

[COLOR="Blue"]Edit:  I found it in the hardware file[/COLOR]```
 *-scsi:1
          physical id: 12
          bus info: usb@1:6
          logical name: scsi7
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@7:0.0.0
             logical name: [COLOR="Blue"]**/dev/sdd**[/COLOR]
```... this means the HDD driver is loaded up and the drive should be seen by udev.

---

### Post by antiartist on 2012-10-07
restarted the server and made the output again, just to be sure.

I see the /sdd device in the output as well but I'm not sure what to do from here.  Interesting, there is also /sde /sdf /sdg as well...which seems wrong.  I don't have that many disks attached.

---

### Post by bab1 on 2012-10-07
> **antiartist said:**
> restarted the server and made the output again, just to be sure.

I see the /sdd device in the output as well but I'm not sure what to do from here.  Interesting, there is also /sde /sdf /sdg as well...which seems wrong.  I don't have that many disks attached.
]

First things first -- Don't post such a long file directly to the thread.  Attach it to the post.  It's easier for folks that are just reading the thread.   Short amounts of data should be posted between the ```

``` brackets using the # icon at the top of the editor.

Do you see the disk using ```
sudo fdisk -l
```

What do you get with this ```
sudo blkid
```

---

### Post by antiartist on 2012-10-08
I know better than to post that much text into a post....sorry :(

Out put of sudo fdisk -l (in which there are no /sdd or higher devices listed):
```
tom@HouseMedia:~$ sudo fdisk -l
[sudo] password for tom:

Disk /dev/sda: 10.3 GB, 10254827520 bytes
255 heads, 63 sectors/track, 1246 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00018313

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1188     9537536   83  Linux
/dev/sda2            1188        1247      474113    5  Extended
/dev/sda5            1188        1247      474112   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005f5c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3e6caab7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      182401  1465136001    7  HPFS/NTFS
tom@HouseMedia:~$

```

Output from sudo blkid (also no /sdd or higher devices):
```
tom@HouseMedia:~$ sudo blkid
/dev/sda1: UUID="39609753-75df-4ff0-9381-0d00fd4af125" TYPE="ext4"
/dev/sda5: UUID="d5a546d6-5d61-40ef-91b6-85739d59f789" TYPE="swap"
/dev/sdb1: UUID="26bc4db0-3e1f-4e7c-af3a-de0351fa35b1" TYPE="ext3"
/dev/sdc1: UUID="228F-2D10" TYPE="vfat"

```

Any ideas?  Is there a way to start over that won't cause me to break things further?

---

### Post by bab1 on 2012-10-08
> **antiartist said:**
> I know better than to post that much text into a post....sorry :(

Out put of sudo fdisk -l (in which there are no /sdd or higher devices listed)...


Any ideas?  Is there a way to start over that won't cause me to break things further?

Let's just try and partition the disk one more time.  What do you get with this command```
sudo fdisk /dev/sdd
```

If you get something like this```
WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Command (m for help):
```...then you have had success.  The important part is this ```
Command (m for help):
``` ... This is the command prompt for fdisk.  Enter **m ** to see the menu of options.  The option **n** will create a new partition.  Have you used fdisk before?  If not, see [**_[COLOR="Blue"]here[/COLOR]_**]("https://help.ubuntu.com/community/InstallingANewHardDrive") and [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.howtogeek.com/106873/how-to-use-fdisk-to-manage-partitions-on-linux/") for basic information.

---

### Post by antiartist on 2012-10-08
I have used fdisk once before; when I setup a single partition on this new disk.  I then used dd to write a disk image I had made (also with dd) to this disk and that is when the disk stopped working propertly.

fdisk continues to return the same error:
```
tom@HouseMedia:~$ sudo fdisk /dev/sdd
[sudo] password for tom:

Unable to read /dev/sdd
tom@HouseMedia:~$

```

---

### Post by bab1 on 2012-10-08
> **antiartist said:**
> I have used fdisk once before; when I setup a single partition on this new disk.  I then used dd to write a disk image I had made (also with dd) to this disk and that is when the disk stopped working propertly.

fdisk continues to return the same error:
```
tom@HouseMedia:~$ sudo fdisk /dev/sdd
[sudo] password for tom:

Unable to read /dev/sdd
tom@HouseMedia:~$

```
What is confusing to me is how you wrote the image to /dev/sdd rather than /dev/sdd1.

You can't break this disk any more than it already is.  Is this host a desktop with a GUI?  If so you might be able to use *Disk Utility* to fix things.  See if you can start the *Disk Utility *with root powers like this```
sudo palimpsest
```... Navigate to the disk /dev/sdd and see if you can use this to create a partition and format it.

Why are you using ***dd*** to format the drive?  What kind of image are you working with?

---

### Post by antiartist on 2012-10-08
I had a created an image of my existing system disk using dd using [directions very similar to these]("http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/") except I did not realize until later that with the disk still mounted, what I was making an image of was basically useless.

I believe I wrote the image to /sdd1 and then I discovered that about restoring 9GB of stuff, the partition was still showed as empty (using ls).  I then fumbled around trying to get to a point where I could wipe and repartition the drive again.  At some point, I realized that I was in the current situation (where the disk both exists and doesn't exist, according to ubuntu.)   This seemed so simple and straight forward.  And of course, it was not as I am still learning.

No, there is no GUI available.  This is a headless box.

So whatever is on this disk is obviously buggered.  How can I start over?  In my fumbling, I noticed that /dev/sdd exists even when the disk is not actually plugged into the box.  Is this unusual?

---

### Post by bab1 on 2012-10-08
> **antiartist said:**
> I had a created an image of my existing system disk using dd using [directions very similar to these]("http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/") except I did not realize until later that with the disk still mounted, what I was making an image of was basically useless.

I believe I wrote the image to /sdd1 and then I discovered that about restoring 9GB of stuff, the partition was still showed as empty (using ls).  I then fumbled around trying to get to a point where I could wipe and repartition the drive again.  At some point, I realized that I was in the current situation (where the disk both exists and doesn't exist, according to ubuntu.)   This seemed so simple and straight forward.  And of course, it was not as I am still learning.

No, there is no GUI available.  This is a headless box.

So whatever is on this disk is obviously buggered.  How can I start over?  In my fumbling, I noticed that /dev/sdd exists even when the disk is not actually plugged into the box.  Is this unusual?

No it is not unusual.  The system caches the info, assuming you will plug the disk in at some later date.  If a new disk is installed it uses the next description.  This also explains all the other descriptions (sde, sdf, sdg etc)  You must have unplugged and then installed the disk multiple times.

Since the disk may have a newly assigned descriptor, we might only need to see what is being used currently.  I would try the last descriptor sd? and see if I could get fdisk to recognise the disk.

The latest formatter for Linux is *parted*.  I have never used it so you would have to read up on it, but you would have to know the descriptor for the disk with this too.

---

### Post by antiartist on 2012-10-15
Sorry the delay in responding.  I had to take a break as this was getting a little frustrating.  

So tried using fdisk against the different /dev/sd? variations and the drive doesn't seem to be attached to any of them:
```
tom@HouseMedia:~$ sudo fdisk /dev/sdd

Unable to read /dev/sdd
tom@HouseMedia:~$ sudo fdisk /dev/sde

Unable to open /dev/sde
tom@HouseMedia:~$ sudo fdisk /dev/sdf

Unable to open /dev/sdf
tom@HouseMedia:~$ sudo fdisk /dev/sdg

Unable to open /dev/sdg
tom@HouseMedia:~$ sudo fdisk /dev/sdh

Unable to open /dev/sdh

```

---

### Post by bab1 on 2012-10-15
> **antiartist said:**
> Sorry the delay in responding.  I had to take a break as this was getting a little frustrating.  

So tried using fdisk against the different /dev/sd? variations and the drive doesn't seem to be attached to any of them:
```
tom@HouseMedia:~$ sudo fdisk /dev/sdd

Unable to read /dev/sdd
tom@HouseMedia:~$ sudo fdisk /dev/sde

Unable to open /dev/sde
tom@HouseMedia:~$ sudo fdisk /dev/sdf

Unable to open /dev/sdf
tom@HouseMedia:~$ sudo fdisk /dev/sdg

Unable to open /dev/sdg
tom@HouseMedia:~$ sudo fdisk /dev/sdh

Unable to open /dev/sdh

```

Let's start over again.  The following should show all disks attached to the machine.  Post the output of this```
sudo lshw -C disk

```

---

### Post by antiartist on 2012-10-15
```
tom@HouseMedia:~$ sudo lshw -C disk
[sudo] password for tom:
  *-disk:0
       description: ATA Disk
       product: WDC WD102BB
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sda
       version: 07.0
       serial: WD-WMA471224295
       size: 9779MiB (10GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00018313
  *-disk:1
       description: ATA Disk
       product: ST3320820A
       vendor: Seagate
       physical id: 0.1.0
       bus info: scsi@4:0.1.0
       logical name: /dev/sdb
       version: 3.AA
       serial: 5QF1VYTG
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0005f5c2
  *-cdrom
       description: DVD-RAM writer
       product: DVDRRW GSA-H30L
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: S755
       serial: [HL-DT-STDVDRRW GSA-H30L S75506/12/26ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: SCSI Disk
       product: Desktop
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sdc
       version: 0130
       serial: 2GHN6GFL
       size: 1397GiB (1500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=4 signature=3e6caab7
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sdd
  *-disk:0
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/sde
  *-disk:1
       description: SCSI Disk
       physical id: 0.0.1
       bus info: scsi@6:0.0.1
       logical name: /dev/sdf
  *-disk:2
       description: SCSI Disk
       physical id: 0.0.2
       bus info: scsi@6:0.0.2
       logical name: /dev/sdg
  *-disk:3
       description: SCSI Disk
       physical id: 0.0.3
       bus info: scsi@6:0.0.3
       logical name: /dev/sdh
tom@HouseMedia:~$

```

---

### Post by bab1 on 2012-10-16
```
 *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sdd
  *-disk:0
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/sde
  *-disk:1
       description: SCSI Disk
       physical id: 0.0.1
       bus info: scsi@6:0.0.1
       logical name: /dev/sdf
  *-disk:2
       description: SCSI Disk
       physical id: 0.0.2
       bus info: scsi@6:0.0.2
       logical name: /dev/sdg
  *-disk:3
       description: SCSI Disk
       physical id: 0.0.3
       bus info: scsi@6:0.0.3
       logical name: /dev/sdh
```

The above appears to be the disk in question. I would remove the disk in question and see what you get from the *sudo lshw -C disk* command with it removed.  

My best guess is this disk is formatted vfat and is corrupted by being removed without unmounting it first.  If you have a windows machine, you might try installing it there and *"safely unmounting"* it.  Then adding it back to the Ubuntu machine to see what you have then.

---

### Post by antiartist on 2012-11-17
I just realized I never did follow up on this post and thought I should do so for the sake of anyone else googling about a simliar problem.  

So I found the problem and was able to fix it a couple weeks back.  I unplugged the disk from the ubuntu box and plugged into my windows machine.  Windows could also not identify it property either.  Using Windows Computer Management (Disk Management) console, I noticed right away that the disk wasn't formatted properly.  I want the disk to have NTFS formatting so the fact Windows didn't recognize it spoke volumes.  I don't recall ~exactly~ what the problem was (I want to say it had something to do with an 'Unallocated table"....?)  but I corrected it easily within Disk Management and Windows was able to recognize the drive again.  I then plug the disk back into the ubuntu box and mounted it without an issue.

I then used Clonezilla to clone my tiny-sized system disk to the now-working disk (this time using the -K switch so that it would size the last partition to use all the disk space) and all is well now.

My only outstanding issue is that all these dummy disks are still listed when using sudo lshw -C disk
```
*-disk:0
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/sde
  *-disk:1
       description: SCSI Disk
       physical id: 0.0.1
       bus info: scsi@6:0.0.1
       logical name: /dev/sdf
  *-disk:2
       description: SCSI Disk
       physical id: 0.0.2
       bus info: scsi@6:0.0.2
       logical name: /dev/sdg
  *-disk:3
       description: SCSI Disk
       physical id: 0.0.3
       bus info: scsi@6:0.0.3
       logical name: /dev/sdh
```
How do I go about removing them from the system?

---

