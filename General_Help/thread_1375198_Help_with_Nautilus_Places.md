---
title: "Help with Nautilus Places"
date: 2010-01-07
forum: General Help
---

### Post by shilo on 2010-01-07
I recently installed Ubuntu 9.10 Karmic 64-Bit on an new HP laptop.  I am dual-booting with Windows 7.

When I first opened Nautilus, I saw two entries I didn't care for.  One had the label "SYSTEM", the other had the label "256 GB Filesystem".  Neither was mounted.  The smaller is a 200 MB partition (/dev/sda1).  The larger is the Windows 7 partition (/dev/sda2).

My (2) goals:

1) Remove "SYSTEM" from Places completely, as I will never need to mount it under Ubuntu.
2) Change the label for "256 GB Filesystem" to "Windows 7", so it's easy to remember should I want to mount the partition.

Sounds easy enough.  Here is what I tried.

I created an .fdi file so HAL would take care of all of this:

```
shilo@shilo-laptop:~$ cat /usr/share/hal/fdi/policy/90-backup.fdi
<?xml version="1.0" encoding="UTF-8"?><!-- -*- SGML -*- -->
<deviceinfo version="0.2">
<device>
<match key="info.category" string="volume">
<match key="volume.uuid" string="50C4E42FC4E4194C">
<merge key="volume.label" type="string">Windows 7</merge>
</match>
</match>
</device>
<device>
<match key="block.device" string="/dev/sda1">
<merge key="volume.ignore" type="bool">true</merge>
<merge key="info.ignore" type="bool">true</merge>
</match>
</device>
</deviceinfo>
```I rebooted to find that there was absolutely no change.  Had my file been parsed?  Yes.

```
shilo@shilo-laptop:~$ hal-device
```<SNIP>

```

26: udi = '/org/freedesktop/Hal/devices/volume_uuid_50C4E42FC4E4194C'
  volume.uuid = '50C4E42FC4E4194C'  (string)
  volume.label = 'Windows 7'  (string)
  volume.mount_point = ''  (string)
  volume.is_mounted = false  (bool)
  block.device = '/dev/sda2'  (string)
  block.major = 8  (0x8)  (int)
  block.minor = 2  (0x2)  (int)
  block.is_volume = true  (bool)
  volume.linux.is_device_mapper = false  (bool)
  volume.is_disc = false  (bool)
  volume.is_partition = true  (bool)
  volume.num_blocks = 500465712  (0x1dd48030)  (uint64)
  volume.block_size = 512  (0x200)  (int)
  volume.partition.start = 209715200  (0xc800000)  (uint64)
  volume.partition.number = 2  (0x2)  (int)
  volume.ignore = false  (bool)
  volume.partition.media_size = 500107862016  (0x7470c06000)  (uint64)
  info.product = 'Volume (ntfs)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_50C4E42FC4E4194C'  (string)
  volume.is_mounted_read_only = false  (bool)
org.freedesktop.Hal.Device.Volume.method_argnames = { 'mount_point fstype extra_options', 'extra_options', 'extra_options' } (string list)
  volume.size = 256238444544  (0x3ba9006000)  (uint64)
  org.freedesktop.Hal.Device.Volume.method_signatures = { 'ssas', 'as', 'as' } (string list)
  volume.unmount.valid_options = { 'lazy' } (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = { 'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject' } (string list)
  org.freedesktop.Hal.Device.Volume.method_names = { 'Mount', 'Unmount', 'Eject' } (string list)
  volume.unmount.ntfs.valid_options = { 'lazy' } (string list)
  volume.fstype.alternative = 'ntfs'  (string)
  volume.mount.ntfs.valid_options = { 'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'uid=', 'gid=', 'umask=', 'utf8' } (string list)
  volume.mount.valid_options = { 'ro', 'atime', 'noatime', 'relatime', 'fake_rw', 'no_def_opts', 'default_permissions', 'umask=', 'fmask=', 'dmask=', 'uid=', 'gid=', 'show_sys_files', 'silent', 'force', 'remove_hiberfile', 'locale=', 'streams_interface=', 'debug', 'no_detach', 'sync', 'dirsync', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'recover', 'norecover' } (string list)
  volume.policy.mount_filesystem = 'ntfs-3g'  (string)
  info.capabilities = { 'volume', 'block' } (string list)
  info.category = 'volume'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda2'  (string)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_FUJITSU_MJA2500BH_G2_K94ST9828JYN'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_FUJITSU_MJA2500BH_G2_K94ST9828JYN'  (string)
  volume.fstype = 'ntfs-3g'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fsversion = ''  (string)
  info.interfaces = { 'org.freedesktop.Hal.Device.Volume' } (string list)
```<SNIP>
```

28: udi = '/org/freedesktop/Hal/devices/volume_uuid_48A4F2E3A4F2D304'
  volume.uuid = '48A4F2E3A4F2D304'  (string)
  volume.label = 'SYSTEM'  (string)
  volume.mount_point = ''  (string)
  volume.is_mounted = false  (bool)
  block.device = '/dev/sda1'  (string)
  block.major = 8  (0x8)  (int)
  block.minor = 1  (0x1)  (int)
  block.is_volume = true  (bool)
  volume.linux.is_device_mapper = false  (bool)
  volume.is_disc = false  (bool)
  volume.is_partition = true  (bool)
  volume.num_blocks = 407552  (0x63800)  (uint64)
  volume.block_size = 512  (0x200)  (int)
  volume.partition.start = 1048576  (0x100000)  (uint64)
  volume.partition.number = 1  (0x1)  (int)
  volume.ignore = true  (bool)
  volume.partition.media_size = 500107862016  (0x7470c06000)  (uint64)
  info.product = 'SYSTEM'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_48A4F2E3A4F2D304'  (string)
  volume.is_mounted_read_only = false  (bool)
  org.freedesktop.Hal.Device.Volume.method_argnames = { 'mount_point fstype extra_options', 'extra_options', 'extra_options' } (string list)
  volume.size = 208666624  (0xc700000)  (uint64)
  org.freedesktop.Hal.Device.Volume.method_signatures = { 'ssas', 'as', 'as' } (string list)
  volume.unmount.valid_options = { 'lazy' } (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = { 'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject' } (string list)
  org.freedesktop.Hal.Device.Volume.method_names = { 'Mount', 'Unmount', 'Eject' } (string list)
  volume.unmount.ntfs.valid_options = { 'lazy' } (string list)
  volume.fstype.alternative = 'ntfs'  (string)
  volume.mount.ntfs.valid_options = { 'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'uid=', 'gid=', 'umask=', 'utf8' } (string list)
  volume.mount.valid_options = { 'ro', 'atime', 'noatime', 'relatime', 'fake_rw', 'no_def_opts', 'default_permissions', 'umask=', 'fmask=', 'dmask=', 'uid=', 'gid=', 'show_sys_files', 'silent', 'force', 'remove_hiberfile', 'locale=', 'streams_interface=', 'debug', 'no_detach', 'sync', 'dirsync', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'recover', 'norecover' } (string list)
  volume.policy.mount_filesystem = 'ntfs-3g'  (string)
  info.ignore = true  (bool)
  info.capabilities = { 'volume', 'block' } (string list)
  info.category = 'volume'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda1'  (string)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_FUJITSU_MJA2500BH_G2_K94ST9828JYN'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_FUJITSU_MJA2500BH_G2_K94ST9828JYN'  (string)
  volume.fstype = 'ntfs-3g'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fsversion = ''  (string)
  info.interfaces = { 'org.freedesktop.Hal.Device.Volume' } (string list)
```Any ideas on why Nautilus isn't:

1) Hiding "SYSTEM" (/dev/sda1)
2) Using the "Windows 7" label (dev/sda2)

Thanks in advance for any thoughts and help.

---

