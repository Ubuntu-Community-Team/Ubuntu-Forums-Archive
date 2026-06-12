---
title: "Ubuntu does not read hard drive"
date: 2011-09-26
forum: General Help
---

### Post by Bucky85 on 2011-09-26
Hello all. I'm trying to install Ubuntu 11.04 to replace a corrupted older version of Ubuntu but so far I am just running into brick walls. The current problem is that it will not recognize my hard drive and with the command  ```
sudo lashw -class storage -class disk 
``` I just get ```
ubuntu@ubuntu:~$ sudo lshw -class storage -class disk
  *-storage               
       description: SATA controller
       product: SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
       vendor: ATI Technologies Inc
       physical id: 11
       bus info: pci@0000:00:11.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: storage pm ahci_1.0 bus_master cap_list
       configuration: driver=ahci latency=32
       resources: irq:22 ioport:ff00(size=8) ioport:fe00(size=4) ioport:fd00(size=8) ioport:fc00(size=4) ioport:fb00(size=16) memory:fe02f000-fe02f3ff
  *-ide
       description: IDE interface
       product: SB7x0/SB8x0/SB9x0 IDE Controller
       vendor: ATI Technologies Inc
       physical id: 14.1
       bus info: pci@0000:00:14.1
       logical name: scsi0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: ide msi bus_master cap_list emulated
       configuration: driver=pata_atiixp latency=32
       resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fa00(size=16)
     *-cdrom
          description: DVD-RAM writer
          product: DVD RW AD-7201A
          vendor: Optiarc
          physical id: 0.0.0
          bus info: scsi@0:0.0.0
          logical name: /dev/cdrom
          logical name: /dev/cdrw
          logical name: /dev/dvd
          logical name: /dev/dvdrw
          logical name: /dev/scd0
          logical name: /dev/sr0
          logical name: /cdrom
          version: 1.06
          serial: [
          capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
          configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
        *-medium
             physical id: 0
             logical name: /dev/cdrom
             logical name: /cdrom
             configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted
``` 
So as you see I'm at a loss. Any help would just be awesome.

---

### Post by searchfgold6789 on 2011-09-26
What about the full output of: ```
sudo lshw
```And also have you checked the hard disk for possible failure, corruption, and error?

---

### Post by oldfred on 2011-09-26
You are showing disk interfaces but no disks? Does BIOS show drives?

---

### Post by seawolf167 on 2011-09-27
As oldfred suggested - if the ports are turned on in BIOS but you are unable to see the disks in Ubuntu, is BIOS recognizing the drives?

If you install smartmontools

```
sudo apt-get install smartmontools
```

and run the following

```
sudo smartctl -H /dev/sda1
```

where you'll replace */dev/sda1 *with the location of your device in question what is the output?

---

