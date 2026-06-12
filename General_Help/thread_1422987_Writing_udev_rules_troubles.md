---
title: "Writing udev rules troubles"
date: 2010-03-06
forum: General Help
---

### Post by Mainiac on 2010-03-06
Hi

  I have a MythTV setup running 8.04.3 LTS, with 2 PVR-150 and lately added a Philips webcam (for zoneminder), everything was great until an extended power outage exceeded the runtime of the UPS and the system shut down.  Upon reboot after the outage the webcam moved to /dev/video0 from /dev/video2 and bumped the 2 pvr-150 up to /dev/video1 & /dev/video2, as you might imagine, things did not work quite right with the mixed up video devices, so I figured use some udev rules to create symlinks so that if they moved again the links would still point to the correct devices.

Intent was:

/dev/video/pvr150-1 -> 1st pvr150 device (ivtv0)
/dev/video/pvr150-2 -> 2nd pvr150 device (ivtv1)
/dev/video/PhilipsWC -> Philips webcam

I created ***81-video-symlinks.rules*** as follows:
```
KERNEL=="video*", ATTR{name}=="ivtv0 encoder MPG", SYMLINK+="video/pvr150-1"
KERNEL=="video*", ATTR{name}=="ivtv1 encoder MPG", SYMLINK+="video/pvr150-2"
KERNEL=="video*", ATTR{name}=="Philips SPC 900NC webcam", SYMLINK+="video/PhilipsWC"

```Running ***udevtest $(udevinfo -q path -n /dev/video1)*** produces:
```
This program is for debugging only, it does not run any program,
specified by a RUN key. It may show incorrect results, because
some values may be different, or not available at a simulation run.

parse_file: reading '/etc/udev/rules.d/05-options.rules' as rules file
parse_file: reading '/etc/udev/rules.d/05-udev-early.rules' as rules file
parse_file: reading '/etc/udev/rules.d/20-names.rules' as rules file
parse_file: reading '/etc/udev/rules.d/30-cdrom_id.rules' as rules file
parse_file: reading '/etc/udev/rules.d/40-basic-permissions.rules' as rules file
parse_file: reading '/etc/udev/rules.d/40-permissions.rules' as rules file
parse_file: reading '/etc/udev/rules.d/41-mythtv-permissions.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-fuse.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-hplip.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-libmtp7.rules' as rules file
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
parse_file: reading '/etc/udev/rules.d/81-video-symlinks.rules' as rules file
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
import_uevent_var: import into environment: 'MAJOR=81'
import_uevent_var: import into environment: 'MINOR=1'
udevtest: looking at device '/devices/pci0000:00/0000:00:1e.0/0000:05:00.0/video4linux/video1' from subsystem 'video4linux'
udev_rules_get_name: add symlink 'video/pvr150-1'
udev_rules_get_name: no node name set, will use kernel name 'video1'
udev_db_get_device: found a symlink as db file
udev_device_event: device '/devices/pci0000:00/0000:00:1e.0/0000:05:00.0/video4linux/video1' already in database, cleanup
udev_node_add: creating device node '/dev/video1', major=81, minor=1, mode=0660, uid=0, gid=44
udev_node_update_symlinks: update symlink 'video/pvr150-1' of '/devices/pci0000:00/0000:00:1e.0/0000:05:00.0/video4linux/video1'
udev_db_get_devices_by_name: no index directory '/dev/.udev/names/video\x2fpvr150-1': No such file or directory
[B]update_link: found -1 devices with name 'video/pvr150-1'
update_link: no reference left, remove 'video/pvr150-1'[/B]
udevtest: run: 'socket:/org/freedesktop/hal/udev_event'
udevtest: run: 'socket:/org/kernel/udev/monitor'
```which seems to indicate that the symlinks are created and then removed.

Other info that may help ***udevinfo -a -p $(udevinfo -q path -n /dev/video1)*** :
```
Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1e.0/0000:05:00.0/video4linux/video1':
   ** KERNEL=="video1"**
    SUBSYSTEM=="video4linux"
    DRIVER==""
    ATTR{dev}=="81:1"
    **ATTR{name}=="ivtv0 encoder MPG"**

  looking at parent device '/devices/pci0000:00/0000:00:1e.0/0000:05:00.0/video4linux':
    KERNELS=="video4linux"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1e.0/0000:05:00.0':
    KERNELS=="0000:05:00.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="ivtv"
    ATTRS{vendor}=="0x4444"
    ATTRS{device}=="0x0016"
    ATTRS{subsystem_vendor}=="0x0070"
    ATTRS{subsystem_device}=="0x8003"
    ATTRS{class}=="0x040000"
    ATTRS{irq}=="21"
    ATTRS{local_cpus}=="ff"
    ATTRS{modalias}=="pci:v00004444d00000016sv00000070sd00008003bc04sc00i00"
    ATTRS{enable}=="1"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00/0000:00:1e.0':
    KERNELS=="0000:00:1e.0"
    SUBSYSTEMS=="pci"
    DRIVERS==""
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x244e"
    ATTRS{subsystem_vendor}=="0x0000"
    ATTRS{subsystem_device}=="0x0000"
    ATTRS{class}=="0x060401"
    ATTRS{irq}=="0"
    ATTRS{local_cpus}=="ff"
    ATTRS{modalias}=="pci:v00008086d0000244Esv00000000sd00000000bc06sc04i01"
    ATTRS{enable}=="1"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}=="1"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```Am I missing something, doing something not quite right?

Thank you for any ideas you may have.

---

