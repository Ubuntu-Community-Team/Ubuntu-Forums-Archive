---
title: "udev rule question"
date: 2009-09-23
forum: General Help
---

### Post by DanInOttawa on 2009-09-23
Good afternoon,
I am trying to define a udev rule, named 85-myusbstick.rules, which takes effect when a USB stick with, say the given name "MyUSBStick", is inserted. I came up with the following:

```
#Rule for the detection of my USB Stick
ACTION!="add", GOTO="mystick_end"

KERNEL=="sd?1", SUBSYSTEMS=="usb", DRIVERS=="usb", ENV{ID_FS_LABEL_ENC}=="MyUSBStick", RUN+="/usr/local/myLocal/myusbstick.sh"

LABEL="mystick_end"

```This rule is not working. I also used *ENV{ID_FS_LABEL}=="MyUSBStick"* without success.

udevinfo reports the following information about the device:

```
daniell@daniell-laptop:~$  udevinfo -a -p $(udevinfo -q path -n /dev/sdb1)

Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/block/sdb/sdb1':
    KERNEL=="sdb1"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{dev}=="8:17"
    ATTR{start}=="32"
    ATTR{size}=="247776"
    ATTR{stat}=="     152      460        0        0"

  looking at parent device '/block/sdb':
    KERNELS=="sdb"
    SUBSYSTEMS=="block"
    DRIVERS==""
    ATTRS{dev}=="8:16"
    ATTRS{range}=="16"
    ATTRS{removable}=="1"
    ATTRS{size}=="248096"
    ATTRS{stat}=="     113      119     1100     1672        0        0        0        0        0     1004     1672"
    ATTRS{capability}=="13"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb7/7-5/7-5:1.0/host13/target13:0:0/13:0:0:0':
    KERNELS=="13:0:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{device_blocked}=="0"
    ATTRS{type}=="0"
    ATTRS{scsi_level}=="0"
    ATTRS{vendor}=="Memorex "
    ATTRS{model}=="Flashdrive 501B "
    ATTRS{rev}=="PMAP"
    ATTRS{state}=="running"
    ATTRS{timeout}=="30"
    ATTRS{iocounterbits}=="32"
    ATTRS{iorequest_cnt}=="0x1a6"
    ATTRS{iodone_cnt}=="0x1a6"
    ATTRS{ioerr_cnt}=="0x2"
    ATTRS{modalias}=="scsi:t-0x00"
    ATTRS{evt_media_change}=="0"
    ATTRS{queue_depth}=="1"
    ATTRS{queue_type}=="none"
    ATTRS{max_sectors}=="240"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb7/7-5/7-5:1.0/host13/target13:0:0':
    KERNELS=="target13:0:0"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb7/7-5/7-5:1.0/host13':
    KERNELS=="host13"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb7/7-5/7-5:1.0':
    KERNELS=="7-5:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb-storage"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{bInterfaceClass}=="08"
    ATTRS{bInterfaceSubClass}=="06"
    ATTRS{bInterfaceProtocol}=="50"
    ATTRS{modalias}=="usb:v12F7p1A00d0100dc00dsc00dp00ic08isc06ip50"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb7/7-5':
    KERNELS=="7-5"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{dev}=="189:777"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPower}=="200mA"
    ATTRS{urbnum}=="1059"
    ATTRS{idVendor}=="12f7"
    ATTRS{idProduct}=="1a00"
    ATTRS{bcdDevice}=="0100"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="7"
    ATTRS{devnum}=="10"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Memorex "
    ATTRS{product}=="Flashdrive 501B "
    ATTRS{serial}=="075B0F957E6D"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb7':
    KERNELS=="usb7"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{dev}=="189:768"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="306"
    ATTRS{idVendor}=="0000"
    ATTRS{idProduct}=="0000"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="7"
    ATTRS{devnum}=="1"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="6"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.24-24-generic ehci_hcd"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{serial}=="0000:00:1d.7"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7':
    KERNELS=="0000:00:1d.7"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x2836"
    ATTRS{subsystem_vendor}=="0x103c"
    ATTRS{subsystem_device}=="0x30c1"
    ATTRS{class}=="0x0c0320"
    ATTRS{irq}=="21"
    ATTRS{local_cpus}=="ff"
    ATTRS{modalias}=="pci:v00008086d00002836sv0000103Csd000030C1bc0Csc03i20"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""
```while *udevinfo -e* reports
```
P: /block/sdb/sdb1
N: sdb1
S: disk/by-id/usb-Memorex_Flashdrive_501B_075B0F957E6D-0:0-part1
S: disk/by-path/pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0-part1
S: disk/by-uuid/739F-CAA8
S: disk/by-label/MyUSBStick
E: DEVTYPE=partition
E: ID_VENDOR=Memorex
E: ID_MODEL=Flashdrive_501B
E: ID_REVISION=PMAP
E: ID_SERIAL=Memorex_Flashdrive_501B_075B0F957E6D-0:0
E: ID_SERIAL_SHORT=075B0F957E6D
E: ID_TYPE=disk
E: ID_INSTANCE=0:0
E: ID_BUS=usb
E: ID_PATH=pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0
E: ID_FS_USAGE=filesystem
E: ID_FS_TYPE=vfat
E: ID_FS_VERSION=FAT16
E: ID_FS_UUID=739F-CAA8
E: ID_FS_UUID_ENC=739F-CAA8
E: ID_FS_LABEL=MyUSBStick
E: ID_FS_LABEL_ENC=MyUSBStick
E: ID_FS_LABEL_SAFE=MyUSBStick

```Finally, I verified the rule using the command *udevtest /block/sdb/sdb1*

```
udevtest: looking at device '/block/sdb/sdb1' from subsystem 'block'
match_rule: set ENV 'DEVTYPE=partition'
udev_rules_get_name: add symlink 'disk/by-id/usb-Memorex_Flashdrive_501B_075B0F957E6D-0:0-part1'
udev_rules_get_name: add symlink 'disk/by-path/pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0-part1'
udev_node_mknod: atomically replace '/dev/.tmp-8-17'
udev_node_mknod: mknod(/dev/.tmp-8-17.udev-tmp, 060600, 8, 17) failed: Permission denied
run_program: 'vol_id --export /dev/.tmp-8-17'
run_program: '/lib/udev/vol_id' (stderr) '/dev/.tmp-8-17: error opening volume'
run_program: '/lib/udev/vol_id' returned with status 2
udev_rules_get_name: no node name set, will use kernel name 'sdb1'
unlink_secure: chown(/dev/.tmp-8-17, 0, 0) failed: No such file or directory
unlink_secure: chmod(/dev/.tmp-8-17, 0000) failed: No such file or directory
udev_device_event: device '/block/sdb/sdb1' already in database, cleanup
udev_node_add: creating device node '/dev/sdb1', major=8, minor=17, mode=0660, uid=0, gid=6
udev_node_update_symlinks: update symlink 'disk/by-id/usb-Memorex_Flashdrive_501B_075B0F957E6D-0:0-part1' of '/block/sdb/sdb1'
udev_db_get_devices_by_name: found index directory '/dev/.udev/names/disk\x2fby-id\x2fusb-Memorex_Flashdrive_501B_075B0F957E6D-0:0-part1'
update_link: found 1 devices with name 'disk/by-id/usb-Memorex_Flashdrive_501B_075B0F957E6D-0:0-part1'
update_link: found '/block/sdb/sdb1' for 'disk/by-id/usb-Memorex_Flashdrive_501B_075B0F957E6D-0:0-part1'
update_link: compare (our own) priority of '/block/sdb/sdb1' 0 >= 0
update_link: 'disk/by-id/usb-Memorex_Flashdrive_501B_075B0F957E6D-0:0-part1' with target 'sdb1' has the highest priority 0, create it
udev_node_update_symlinks: update symlink 'disk/by-path/pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0-part1' of '/block/sdb/sdb1'
udev_db_get_devices_by_name: found index directory '/dev/.udev/names/disk\x2fby-path\x2fpci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0-part1'
update_link: found 1 devices with name 'disk/by-path/pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0-part1'
update_link: found '/block/sdb/sdb1' for 'disk/by-path/pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0-part1'
update_link: compare (our own) priority of '/block/sdb/sdb1' 0 >= 0
update_link: 'disk/by-path/pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0-part1' with target 'sdb1' has the highest priority 0, create it
udev_node_update_symlinks: update old symlink 'disk/by-uuid/739F-CAA8' no longer belonging to '/block/sdb/sdb1'
udev_db_get_devices_by_name: found index directory '/dev/.udev/names/disk\x2fby-uuid\x2f739F-CAA8'
update_link: found 1 devices with name 'disk/by-uuid/739F-CAA8'
update_link: found '/block/sdb/sdb1' for 'disk/by-uuid/739F-CAA8'
update_link: compare (our own) priority of '/block/sdb/sdb1' 0 >= 0
update_link: 'disk/by-uuid/739F-CAA8' with target 'sdb1' has the highest priority 0, create it
udev_node_update_symlinks: update old symlink 'disk/by-label/MyUSBStick' no longer belonging to '/block/sdb/sdb1'
udev_db_get_devices_by_name: found index directory '/dev/.udev/names/disk\x2fby-label\x2MyUSBStick'
update_link: found 1 devices with name 'disk/by-label/MyUSBStick'
update_link: found '/block/sdb/sdb1' for 'disk/by-label/MyUSBStick'
update_link: compare (our own) priority of '/block/sdb/sdb1' 0 >= 0
update_link: 'disk/by-label/MyUSBStick' with target 'sdb1' has the highest priority 0, create it
udevtest: run: '/usr/local/myLocal/myusbstick.sh'
udevtest: run: 'socket:/org/freedesktop/hal/udev_event'
udevtest: run: 'socket:/org/kernel/udev/monitor'
```I launched the script (*/usr/local/myLocal/myusbstick.sh) *manually and verified that it worked.

Note that the script is called if *ENV{ID_FS_LABEL_ENC}=="MyUSBStick"* is removed from the rule.  The problem is that the script is executed for any USB stick used.

This was tested on systems running versions 8.04.3 and 8.10.

Any suggestions?
Thanks
Daniel

---

### Post by 3L33T on 2009-09-23
Try to disable auto-mounting.  The following works in Jaunty, not sure if it works on your version.

```

gconftool-2 --type bool --set /apps/nautilus/preferences/media_automount False
gconftool-2 --type bool --set /apps/nautilus/preferences/media_automount_open False

```

---

### Post by DanInOttawa on 2009-09-23
There was no change in behaviour, but here is what I noticed when using *udevtest* for different users:

As myself (daniell), *udevtest* reports the following
```
match_rule: set ENV 'DEVTYPE=partition'
udev_rules_get_name: add symlink 'disk/by-id/usb-Memorex_Flashdrive_501B_075B0F957E6D-0:0-part1'
udev_rules_get_name: add symlink 'disk/by-path/pci-0000:00:1d.7-usb-0:6:1.0-scsi-0:0:0:0-part1'
[COLOR=DarkRed]udev_node_mknod: atomically replace '/dev/.tmp-8-17'
udev_node_mknod: mknod(/dev/.tmp-8-17.udev-tmp, 060600, 8, 17) failed: Permission denied
[/COLOR] [COLOR=DarkRed]run_program: 'vol_id --export /dev/.tmp-8-17'
run_program: '/lib/udev/vol_id' (stderr) '/dev/.tmp-8-17: error opening volume'
run_program: '/lib/udev/vol_id' returned with status 2[/COLOR]
udev_rules_get_name: no node name set, will use kernel name 'sdb1'

```but when is superuser mode, the following is reported:
```
match_rule: set ENV 'DEVTYPE=partition'
udev_rules_get_name: add symlink 'disk/by-id/usb-Memorex_Flashdrive_501B_075B0F957E6D-0:0-part1'
udev_rules_get_name: add symlink 'disk/by-path/pci-0000:00:1d.7-usb-0:6:1.0-scsi-0:0:0:0-part1'
run_program: 'vol_id --export /dev/.tmp-8-17'
run_program: '/lib/udev/vol_id' (stdout) 'ID_FS_USAGE=filesystem'
run_program: '/lib/udev/vol_id' (stdout) 'ID_FS_TYPE=vfat'
run_program: '/lib/udev/vol_id' (stdout) 'ID_FS_VERSION=FAT16'
run_program: '/lib/udev/vol_id' (stdout) 'ID_FS_UUID=739F-CAA8'
run_program: '/lib/udev/vol_id' (stdout) 'ID_FS_UUID_ENC=739F-CAA8'
run_program: '/lib/udev/vol_id' (stdout) 'ID_FS_LABEL=MyUSBStick'
run_program: '/lib/udev/vol_id' (stdout) 'ID_FS_LABEL_ENC=MyUSBStick'
run_program: '/lib/udev/vol_id' (stdout) 'ID_FS_LABEL_SAFE=MyUSBStick'
run_program: '/lib/udev/vol_id' returned with status 0
```The man pages on mknod and vol_id are not very descriptive. I looked at the permission for the rule, script and things look OK.

Finally, the script associated to the rule gets executed if I do */etc/init.d/udev restart* from a superuser.

Daniel

---

### Post by DanInOttawa on 2009-09-25
I have resolved this issue. The original rule was named 85-mystick.rules.  It was renamed to 96-mystick.rules.  This was done because the rule launches a script which in turns runs a python program which updates a MySQL database with the content of a file located on the USB stick.
This python program refers to the file as "/media/MyUSBStick/myDbChanges.txt" which was not recognized and caused an IOError when opened. 

Looking at syslog, I saw that the stick was mounted after the execution of the 85-mystick.rules. Renaming the rule corrected this; the python program was able to access "/media/MyUSBStick/myDbChanges.txt".
However, I had to add a 3 sec sleep before opening the file to avoid the IOError. I will investigate more.

Automount is left enabled

The final rule is the defined as
```
#Rule for the detection of MY USB Stick
ACTION!="add", GOTO="mystick_end"

KERNEL=="sd?1", SUBSYSTEMS=="usb", DRIVERS=="usb", ENV{ID_FS_LABEL}=="MyUSBStick", RUN+="/usr/local/MyLocal/myusbstick.sh"

LABEL="mystick_end"

```Thanks for the help
Daniel

---

