---
title: "USB thumb drives won't auto-mount upon insertion"
date: 2009-10-11
forum: General Help
---

### Post by asaturn on 2009-10-11
none of my USB drives will mount when I plug them in. I can manually mount them just fine, but they will sit there doing nothing until I do.

here is my system log when I plug in a thumb drive:

```

Oct 11 03:06:11 n500 kernel: [   93.812367]  sdb: sdb1
Oct 11 03:06:11 n500 kernel: [   93.815711] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Oct 11 03:06:11 n500 kernel: [  278.817561] usb 2-5: USB disconnect, address 4
Oct 11 03:06:11 n500 kernel: [  282.440072] usb 2-5: new high speed USB device using ehci_hcd and address 5
Oct 11 03:06:11 n500 kernel: [  282.591929] usb 2-5: configuration #1 chosen from 1 choice
Oct 11 03:06:16 n500 kernel: [  282.592432] scsi5 : SCSI emulation for USB Mass Storage devices
Oct 11 03:06:16 n500 kernel: [  287.602604] scsi 5:0:0:0: Direct-Access     SanDisk  Cruzer Mini      0.2  PQ: 0 ANSI: 2
Oct 11 03:06:16 n500 kernel: [  287.603328] sd 5:0:0:0: Attached scsi generic sg2 type 0
Oct 11 03:06:16 n500 kernel: [  287.609690] sd 5:0:0:0: [sdb] 250879 512-byte logical blocks: (128 MB/122 MiB)
Oct 11 03:06:16 n500 kernel: [  287.611516] sd 5:0:0:0: [sdb] Write Protect is off

```

anything else I should post?

also not sure if it matters but I'm on 64bit ubuntu (core 2 duo)... everything else is working fine as far as I know.

---

### Post by jackallen0714 on 2009-10-11
It also bothers me !!! 
some output here:

sudo fdisk -l 
> Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3ffc3ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       28475   198009157+   f  W95 Ext'd (LBA)
/dev/sda3           28476       30402    15471800   12  Compaq diagnostics
/dev/sda5            3825        7741    31462654+   7  HPFS/NTFS
/dev/sda6            7742       18189    83923528+   7  HPFS/NTFS
/dev/sda7           18190       20794    20924631   83  Linux
/dev/sda8           20795       27169    51201136+   7  HPFS/NTFS
/dev/sda9           27170       28413     9992398+  83  Linux
/dev/sda10          28414       28475      497983+  82  Linux swap / Solaris

Disk /dev/sdb: 16.0 GB, 16039018496 bytes
64 heads, 32 sectors/track, 15296 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x0005e2be

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           5       15296    15659008    c  W95 FAT32 (LBA)


It seems USB storage is correctly recognized, but ...

devkit-disks --monitor-detail

> added:     /org/freedesktop/DeviceKit/Disks/devices/sdb
Showing information for /org/freedesktop/DeviceKit/Disks/devices/sdb
  native-path:                 /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.0/host7/target7:0:0/7:0:0:0/block/sdb
  device:                      8:16
  device-file:                 /dev/sdb
  system internal:             0
  removable:                   1
  has media:                   0
    detects change:            1
    detection by polling:      1
    detection inhibitable:     1
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  size:                        0
  block size:                  0
  job underway:                no
  usage:                       
  type:                        
  version:                     
  uuid:                        
  label:                       
  partition table:
    scheme:                    
    count:                     1
  drive:
    vendor:                    
    model:                     USB FLASH DRIVE
    revision:                  
    serial:                    
    detachable:                1
    can spindown:              0
    rotational media:          1
    ejectable:                 0
    media:                     
      compat:                 
    interface:                 usb
    if speed:                  480000000 bits/s
    ATA SMART:                 not available

added:     /org/freedesktop/DeviceKit/Disks/devices/sdb1
Showing information for /org/freedesktop/DeviceKit/Disks/devices/sdb1
  native-path:                 /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.0/host7/target7:0:0/7:0:0:0/block/sdb/sdb1
  device:                      8:17
  device-file:                 /dev/sdb1
 
  system internal:             0
  removable:                   0
  has media:                   1 
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  size:                        16034824192
  block size:                  512
  job underway:                no
  usage:                       
  type:                        
  version:                     
  uuid:                        
  label:                       
  partition:
    part of:                   /org/freedesktop/DeviceKit/Disks/devices/sdb
    scheme:                    
    number:                    1
    type:                      
    flags:                
    offset:                    4194304
    size:                      16034824192
    label:                     
    uuid:                      


Apparently, devicekit fails to recognize it 

In Palimpsest, this usb thumb drive is detected but the format is unknown ... 

When plug this storage drive in USB sockets before booting, it will be correctly mounted... But then when eject it in naultilus, it disappear (normally there's still a icon left in naultilus)

Anyone can solve ?

---

### Post by asaturn on 2009-11-05
not sure if this helps anyone else, but I tried the recommendation of disabling "Legacy USB Support" in the BIOS

and it fixed it for me

shocked, but whatever... it works!

(on a Lenovo n500 laptop, ubtuntu 9.10 64bit)

:D

---

### Post by P4man on 2009-11-05
I have seen others claim it is related to virtualbox kernel drivers. Are you guys using virtualbox?

---

### Post by asaturn on 2009-11-05
> **P4man said:**
> I have seen others claim it is related to virtualbox kernel drivers. Are you guys using virtualbox?

I do have virtualbox installed... but the problem existed before that. I only installed virtualbox a couple of weeks ago, and I had this problem since 9.04 came out. luckily the USB Legacy mode being disabled has seemed to fix it... when I enable it in the BIOS the problem comes back. weird???

another weird thing: my built-in multi-card reader (does SD, MMC, MS, MSPro) also works now. not sure if that is related to the legacy USB or to the 9.10 update adding more drivers. again, this is on a Lenovo n500 laptop.

---

### Post by raimennendez on 2009-11-06
Hi,

my MSI Wind U100 where just upgraded doesn't neither automount nor read at all the usb thumb:

> 
lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


> 
sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf1ad17dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9356    75152038+  83  Linux
/dev/sda2            9357        9729     2996122+   5  Extended
/dev/sda5            9357        9729     2996091   82  Linux swap / Solaris



Thus I cannot mount my usb thumb on my laptop. It worked well before the upgrade and it still work on other computer.

If someone has some suggestion I'll thank you very much. I need the usb thumb because my laptop dosn't have cdrom.

---

### Post by asaturn on 2009-11-06
did you try the things recommended in this thread?

also is it in one of the USB1.1 ports or in the USB2.0 port?

---

### Post by raimennendez on 2009-11-08
Sorry for answering late but I tested several time the behaviour of the OS to be sure that it doesn't work properly. I tried to disable the USB legacy policy in the BIOS (the only suggestion that I found in the thread). I don't use virtualbox.

When I disabled the USB Legacy Policy at the first boot the OS read the USB Thumb

When I restart the laptop an other time an error message appear: something like "Cannot reset port number 6: maybe USB ..." I couldn't read properly because it's too fast (there is a way to read the error message afterward?). When I login the OS dosn't read the USB thunb. 

If I enable and after disable one more time, first time that boot it reads the USB thumb, when I restart it doesn't read it.

To summarize. First start that I boot after disabling USB legacy poloicy:

> 
~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/raimondo/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=raimondo)
/dev/sdc1 on /media/5C61-D1C6 type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


$ lsusb
Bus 001 Device 005: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 2.0 Stick (4GB) / PNY Attache 4GB Stick
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0db0:a97a Micro Star International Bluetooth EDR Device
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root  

~$ sudo fdisk -l 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf1ad17dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9356    75152038+  83  Linux
/dev/sda2            9357        9729     2996122+   5  Extended
/dev/sda5            9357        9729     2996091   82  Linux swap / Solaris

Disk /dev/sdc: 4029 MB, 4029677568 bytes
1 heads, 1 sectors/track, 7870464 cylinders, total 7870464 sectors
Units = cylinders of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            8065     7870464     3931200    c  W95 FAT32 (LBA)
 

/dev/sdc1 is the USB thumb, of course

when I restart the second time:
> 
~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


~$ sudo fdisk -l


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf1ad17dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9356    75152038+  83  Linux
/dev/sda2            9357        9729     2996122+   5  Extended
/dev/sda5            9357        9729     2996091   82  Linux swap / Solaris

~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/raimondo/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=raimondo)

~$ sudo mount /dev/sdc1 /media/usb
mount: special device /dev/sdc1 does not exist


Thus it doesn't work. Some suggestion?

Thank you

---

### Post by raimennendez on 2009-11-08
Is a bug in 9.10. following this link:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/435352](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/435352)

 I resolved the problem with the USB but I cannot use the web cam,

Thank you again

---

### Post by raimennendez on 2009-11-09
Finally I reinstalled 9.04.

9.10 on MSI doesn't work properly: there are some bugs.

---

### Post by Shibblet on 2009-11-10
I installed 9.04, then did the upgrade to 9.10 of Kubuntu.  After the update, the USB Drives seem to be working just fine.  I still have the brightness issue though.

---

