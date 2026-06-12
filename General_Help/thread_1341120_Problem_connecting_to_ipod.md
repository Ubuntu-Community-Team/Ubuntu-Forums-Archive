---
title: "Problem connecting to ipod"
date: 2009-11-29
forum: General Help
---

### Post by ooolongT on 2009-11-29
When I plug my ipod into the firewire port it will show up in Dolphin, but it shows up twice, like three are two different devices.  One has the name of my ipod, and the other just says "iPod".  I can see the contents of the ipod with the correct name), and it has the ipod folders and a few songs, but it is not everything on my ipod.  I can not open the one labeled "iPod".  There is no link to either device on the desktop, I can only see these devices in Dolphin and the device manager.

Here is the result of sudo lshw | less:
```

*-scsi
          physical id: 1
          bus info: firewire@000a27000269ac30
          logical name: scsi2
        *-disk
             description: SCSI
             product: iPod
             vendor: Apple
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 1.53
             size: 13GiB (15GB)
             capabilities: removable
             configuration: ansiversion=2
           *-medium
                physical id: 0
                logical name: /dev/sdb
                size: 13GiB (15GB)
                capabilities: partitioned partitioned:dos
                configuration: signature=20202020
              *-volume:0
                   description: Empty partition
                   physical id: 1
                   logical name: /dev/sdb1
                   capacity: 39MiB
                   capabilities: primary nofs
              *-volume:1
                   description: Windows FAT volume
                   vendor: *UOKJIHC
                   physical id: 2
                   logical name: /dev/sdb2
                   logical name: /media/BADMAN
                   version: FAT32
                   serial: f188-0a18
                   size: 13GiB
                   capacity: 13GiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat label=IPOD mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush,errors=remount-ro state=mounted

```

When I try to access the ipod with Dolphin, an error pops up:
```
An error occurred while accessing 'ipod', the system responded:
org.freedesktop.Hal.Device.Volume.UnknownFailure: mount: wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or helper program, or other error 

In some cases useful info is found in syslog - try dmesg | tail or so 
```

So I tried dmesg | tail:
```
[112714.691229] FAT: invalid media value (0x2f)
[112714.691243] VFS: Can't find a valid FAT filesystem on dev sdb1.
[112735.186908] FAT: invalid media value (0x2f)
[112735.186914] VFS: Can't find a valid FAT filesystem on dev sdb1.
[112935.017470] FAT: invalid media value (0x2f)
[112935.017478] VFS: Can't find a valid FAT filesystem on dev sdb1.
[112966.909935] FAT: invalid media value (0x2f)
[112966.909943] VFS: Can't find a valid FAT filesystem on dev sdb1.
[113309.204298] FAT: invalid media value (0x2f)
[113309.204307] VFS: Can't find a valid FAT filesystem on dev sdb1.

```

I am running Kubuntu 9.1, Amarok 2.2, It is a 3rd gen ipod.  I have never used the ipod on this box before, but I used to use it all the time on my old comp and it worked beautifully.  

Can anyone tell me how to get this mounted so I can use it in Amarok?  I am tired of the same old music!

---

### Post by ooolongT on 2009-11-29
*bump*

---

### Post by ooolongT on 2009-11-30
Double bump?

---

