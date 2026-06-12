---
title: "Need UDEV rules help"
date: 2010-11-18
forum: General Help
---

### Post by strider22 on 2010-11-18
I have tried to adavpt the USB palm instructions from
[http://www.clasohm.com/blog/one-entry?entry_id=12096](http://www.clasohm.com/blog/one-entry?entry_id=12096)

More info on my device is at
[http://ubuntuforums.org/showthread.php?t=1610537](http://ubuntuforums.org/showthread.php?t=1610537)

I inserted this rule as 10-MP600.rules in /etc/udev/rules.d
BUS=="usb", SYSFS{model}=="HS_USB_FlashDisk", SYMLINK+="mp600"

Any suggestions on what I should do after I get this response from udevtest /block/sdc

root@beryllium:/etc/udev/rules.d# udevtest /block/sdc
This program is for debugging only, it does not run any program,
specified by a RUN key. It may show incorrect results, because
some values may be different, or not available at a simulation run.

parse_file: reading '/etc/udev/rules.d/030_sl-modem-daemon.rules' as rules file
parse_file: reading '/etc/udev/rules.d/05-options.rules' as rules file
parse_file: reading '/etc/udev/rules.d/05-udev-early.rules' as rules file
parse_file: reading '/etc/udev/rules.d/10-mp600.rules' as rules file
parse_file: reading '/etc/udev/rules.d/20-names.rules' as rules file
parse_file: reading '/etc/udev/rules.d/30-cdrom_id.rules' as rules file
parse_file: reading '/etc/udev/rules.d/40-basic-permissions.rules' as rules file
parse_file: reading '/etc/udev/rules.d/40-permissions.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-fuse.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-libmtp7.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-libnjb.rules' as rules file
parse_file: reading '/etc/udev/rules.d/50-libpisock9.rules' as rules file
parse_file: reading '/etc/udev/rules.d/50-xserver-xorg-input-wacom.rules' as rules file
parse_file: reading '/etc/udev/rules.d/55-hpmud.rules' as rules file
parse_file: reading '/etc/udev/rules.d/60-persistent-input.rules' as rules file
parse_file: reading '/etc/udev/rules.d/60-persistent-storage-tape.rules' as rules file
parse_file: reading '/etc/udev/rules.d/60-persistent-storage.rules' as rules file
parse_file: reading '/etc/udev/rules.d/60-symlinks.rules' as rules file
parse_file: reading '/etc/udev/rules.d/61-persistent-storage-edd.rules' as rules file
parse_file: reading '/etc/udev/rules.d/70-persistent-cd.rules' as rules file
parse_file: reading '/etc/udev/rules.d/70-persistent-net.rules' as rules file
parse_file: reading '/etc/udev/rules.d/75-cd-aliases-generator.rules' as rules file
parse_file: reading '/etc/udev/rules.d/75-persistent-net-generator.rules' as rules file
parse_file: reading '/etc/udev/rules.d/80-programs.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-alsa.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-brltty.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-hdparm.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-hplj10xx.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-hwclock.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-ifupdown.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-pcmcia.rules' as rules file
parse_file: reading '/etc/udev/rules.d/90-modprobe.rules' as rules file
parse_file: reading '/etc/udev/rules.d/95-hal.rules' as rules file
parse_file: reading '/etc/udev/rules.d/95-udev-late.rules' as rules file
udevtest: looking at device '/block/sdc' from subsystem 'block'
match_rule: set ENV 'DEVTYPE=disk'
run_program: 'usb_id --export /block/sdc'
run_program: '/lib/udev/usb_id' (stdout) 'ID_VENDOR=MP600'
run_program: '/lib/udev/usb_id' (stdout) 'ID_MODEL=HS_USB_FlashDisk'
run_program: '/lib/udev/usb_id' (stdout) 'ID_REVISION=0100'
run_program: '/lib/udev/usb_id' (stdout) 'ID_SERIAL=MP600_HS_USB_FlashDisk_4512482ADF0FE'
run_program: '/lib/udev/usb_id' (stdout) 'ID_SERIAL_SHORT=4512482ADF0FE'
run_program: '/lib/udev/usb_id' (stdout) 'ID_TYPE=floppy'
run_program: '/lib/udev/usb_id' (stdout) 'ID_BUS=usb'
run_program: '/lib/udev/usb_id' returned with status 0
udev_rules_get_name: add symlink 'disk/by-id/usb-MP600_HS_USB_FlashDisk_4512482ADF0FE'
run_program: 'path_id /block/sdc'
run_program: '/lib/udev/path_id' (stdout) 'ID_PATH=pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0'
run_program: '/lib/udev/path_id' returned with status 0
udev_rules_get_name: add symlink 'disk/by-path/pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0'
run_program: 'vol_id --export /dev/.tmp-8-32'
run_program: '/lib/udev/vol_id' (stderr) '/dev/.tmp-8-32: unknown volume type'
run_program: '/lib/udev/vol_id' returned with status 4
run_program: 'edd_id --export /dev/.tmp-8-32'
run_program: '/lib/udev/edd_id' (stderr) 'no kernel EDD support'
run_program: '/lib/udev/edd_id' returned with status 2
udev_rules_get_name: no node name set, will use kernel name 'sdc'
udev_device_event: device '/block/sdc' already in database, cleanup
udev_node_add: creating device node '/dev/sdc', major=8, minor=32, mode=0660, uid=0, gid=6
udev_node_update_symlinks: update symlink 'disk/by-id/usb-MP600_HS_USB_FlashDisk_4512482ADF0FE' of '/block/sdc'
udev_db_get_devices_by_name: found index directory '/dev/.udev/names/disk\x2fby-id\x2fusb-MP600_HS_USB_FlashDisk_4512482ADF0FE'
update_link: found 1 devices with name 'disk/by-id/usb-MP600_HS_USB_FlashDisk_4512482ADF0FE'
update_link: found '/block/sdc' for 'disk/by-id/usb-MP600_HS_USB_FlashDisk_4512482ADF0FE'
update_link: compare (our own) priority of '/block/sdc' 0 >= 0
update_link: 'disk/by-id/usb-MP600_HS_USB_FlashDisk_4512482ADF0FE' with target 'sdc' has the highest priority 0, create it
udev_node_update_symlinks: update symlink 'disk/by-path/pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0' of '/block/sdc'
udev_db_get_devices_by_name: found index directory '/dev/.udev/names/disk\x2fby-path\x2fpci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0'
update_link: found 1 devices with name 'disk/by-path/pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0'
update_link: found '/block/sdc' for 'disk/by-path/pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0'
update_link: compare (our own) priority of '/block/sdc' 0 >= 0
update_link: 'disk/by-path/pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0' with target 'sdc' has the highest priority 0, create it
udevtest: run: '/lib/udev/hdparm'
udevtest: run: 'socket:/org/freedesktop/hal/udev_event'
udevtest: run: 'socket:/org/kernel/udev/monitor'

---

### Post by strider22 on 2010-11-19
fdisk -l reports partition problems

# fdisk -l

Partition table entries are not in disk order

Disk /dev/sdc: 4090 MB, 4090978816 bytes
126 heads, 62 sectors/track, 1022 cylinders
Units = cylinders of 7812 * 512 = 3999744 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?       99608      245731   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(99607, 97, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(245730, 44, 51)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?       21594      269422   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(21593, 80, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(269421, 14, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?      239361      487188   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(239360, 18, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(487187, 77, 39)
Partition 3 does not end on cylinder boundary.
/dev/sdc4   ?      369391      369398       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(369390, 104, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(369397, 117, 33)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

---

