---
title: "GRUB: Keyboard will not work!"
date: 2012-01-30
forum: General Help
---

### Post by renegadeandy on 2012-01-30
Hey guys, just installed Lucid on my pc - grub 1.98 and when I go to pick a different startup option the countdown 10 seconds disappears on the grub menu - but the menu option does not move, enter down, up etc all dont work.

One time i started hammering the keyboard and the selection did move down 1! But I have no idea what combination made it do that and have not been able to repeat!

Please help!

---

### Post by WasMeHere on 2012-01-30
> **renegadeandy said:**
> Hey guys, just installed Lucid on my pc - grub 1.98 and when I go to pick a different startup option the countdown 10 seconds disappears on the grub menu - but the menu option does not move, enter down, up etc all dont work.

One time i started hammering the keyboard and the selection did move down 1! But I have no idea what combination made it do that and have not been able to repeat!

Please help!
Normally the 'arrow up and down' keys, 'home and end' keys will move the high-lighted line (selection) and the 'Enter' key will activate the selected alternative. There must be something wrong with your installation, if that does not work. Is your keyboard properly connected? If it is a USB keyboard, try another slot!

Or is there something wrong with the display, so that the selected alternative is not high-lighted? Try with one 'arrow-down' and 'Enter'!

---

### Post by ajgreeny on 2012-01-30
Also make sure **legacy usb support** is enabled in BIOS, if it is an option.

---

### Post by renegadeandy on 2012-01-30
Legacy keyboard is enabled, and what you suggested to try did not work. I hammered the keyboard again and somehow got it to move, but still cannot workout what I pressed, its non obvious thats for sure....

---

### Post by renegadeandy on 2012-01-30
Does anybody have anything else I can try please?

---

### Post by renegadeandy on 2012-01-30
<bump>

---

### Post by WasMeHere on 2012-01-30
This is an unusual error, I guess that is why there are so few suggestions. But I'll try again:

Please let us know more about your computer:
- manufacturer (brand name and model number
- motherboard
- bios

What have you been running before? Windows version or ...

---
If you have a laptop or netbook and use the built-in keyboard, maybe you have not enabled the arrow keys, so 

try **ctrl + n** (for next line) and **ctrl + p** (for previous line )

---

### Post by renegadeandy on 2012-01-30
OK so this is what hwinfo reports:

```
============ start debug info ============
libhd version 16.0u (ia32)
using /var/lib/hardware
kernel version is 2.6
----- /proc/cmdline -----
  BOOT_IMAGE=/vmlinuz-2.6.32-38-generic-pae root=/dev/mapper/ubuntu-root ro quiet splash
----- /proc/cmdline end -----
debug = 0xff7ffff7
probe = 0x00138fc4aa17fcf9fffe (+memory +pci +isapnp +net +floppy +misc +misc.serial +misc.par +misc.floppy +serial +cpu +bios +monitor +mouse +scsi +usb -usb.mods +modem +modem.usb +parallel +parallel.lp +parallel.zip -isa -isa.isdn +isdn +kbd +prom +sbus +int +braille +braille.alva +braille.fhp +braille.ht -ignx11 +sys -bios.vbe -isapnp.old -isapnp.new -isapnp.mod +braille.baum -manual +fb +pppoe -scan +pcmcia -fork -parallel.imm +s390 -cpuemu -sysfs -s390disks +udev +block +block.cdrom +block.part +edd +edd.mod -bios.ddc -bios.fb -bios.mode +input +block.mods +bios.vesa -cpuemu.debug -scsi.noserial +wlan -bios.crc -hal -bios.vram -bios.acpi -bios.ddc.ports -modules.pata -net.eeprom -x86emu -max -lxrc)
shm: attached segment 7241759 at 0xb73d1000
>> hal.1: read hal data
  hal: connected to: :1.75
----- hal device list -----
  0: udi = '/org/freedesktop/Hal/devices/net_computer'
  net.originating_device = '/org/freedesktop/Hal/devices/computer'
  net.interface = 'tun0'
  net.address = '00:00:00:00:00:00'
  net.linux.ifindex = 4 (0x4)
  net.arp_proto_hw_id = 65534 (0xfffe)
  linux.subsystem = 'net'
  linux.hotplug_type = 2 (0x2)
  info.subsystem = 'net'
  info.udi = '/org/freedesktop/Hal/devices/net_computer'
  linux.sysfs_path = '/sys/devices/virtual/net/tun0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.category = 'net'
  info.capabilities = { 'net' }

  1: udi = '/org/freedesktop/Hal/devices/computer'
  power_management.type = 'acpi'
  power_management.acpi.linux.version = '20090903'
  power_management.quirk.vbe_post = true
  info.subsystem = 'unknown'
  info.product = 'Computer'
  info.udi = '/org/freedesktop/Hal/devices/computer'
  org.freedesktop.Hal.version = '0.5.14'
  org.freedesktop.Hal.version.major = 0 (0x0)
  org.freedesktop.Hal.version.minor = 5 (0x5)
  org.freedesktop.Hal.version.micro = 14 (0xe)
  system.kernel.name = 'Linux'
  system.kernel.version = '2.6.32-38-generic-pae'
  system.kernel.version.major = 2 (0x2)
  system.kernel.version.minor = 6 (0x6)
  system.kernel.version.micro = 32 (0x20)
  system.kernel.machine = 'i686'
  power_management.can_suspend = true
  power_management.can_suspend_hybrid = true
  power_management.can_hibernate = true
  system.hardware.primary_video.vendor = 4318 (0x10de)
  system.hardware.primary_video.product = 4608 (0x1200)
  system.hardware.serial = 'To be filled by O.E.M.'
  system.hardware.uuid = '00000000-0000-0000-0000-6C626DE99387'
  system.board.serial = 'To be filled by O.E.M.'
  system.firmware.vendor = 'American Megatrends Inc.'
  system.firmware.version = 'V1.8'
  system.firmware.release_date = '02/14/2011'
  system.hardware.vendor = 'MSI'
  system.hardware.product = 'MS-7673'
  system.hardware.version = '2.0'
  system.chassis.manufacturer = 'MSI'
  system.board.product = 'P67A-G45 (MS-7673)'
  system.board.version = '2.0'
  system.board.vendor = 'MSI'
  system.chassis.type = 'Desktop'
  system.formfactor = 'desktop'
  info.addons = { 'hald-addon-cpufreq', 'hald-addon-acpi' }
  info.interfaces = { 'org.freedesktop.Hal.Device.SystemPowerManagement', 'org.freedesktop.Hal.Device.CPUFreq' }
  org.freedesktop.Hal.Device.SystemPowerManagement.method_signatures = { 'i', 'i', '', '', '', 'b' }
  power_management.quirk.dpms_on = true
  power_management.quirk.vbestate_restore = true
  power_management.quirk.vbemode_restore = true
  power_management.quirk.dpms_suspend = true
  power_management.quirk.vga_mode_3 = true
  info.capabilities = { 'cpufreq_control' }
  org.freedesktop.Hal.Device.SystemPowerManagement.method_names = { 'Suspend', 'SuspendHybrid', 'Hibernate', 'Shutdown', 'Reboot', 'SetPowerSave' }
  org.freedesktop.Hal.Device.SystemPowerManagement.method_argnames = { 'num_seconds_to_sleep', 'num_seconds_to_sleep', '', '', '', 'enable_power_save' }
  org.freedesktop.Hal.Device.SystemPowerManagement.method_execpaths = { 'hal-system-power-suspend', 'hal-system-power-suspend-hybrid', 'hal-system-power-hibernate', 'hal-system-power-shutdown', 'hal-system-power-reboot', 'hal-system-power-set-power-save' }
  power_management.is_powersave_set = false
  info.callouts.add = { 'hal-storage-cleanup-all-mountpoints' }

  2: udi = '/org/freedesktop/Hal/devices/storage_model_iHAS124___B'
  storage.originating_device = '/org/freedesktop/Hal/devices/computer'
  info.vendor = 'ATAPI'
  storage.removable = true
  linux.hotplug_type = 3 (0x3)
  storage.removable.support_async_notification = false
  storage.hotpluggable = false
  storage.requires_eject = true
  storage.removable.media_available = false
  storage.size = 0ull (0x0ull)
  storage.firmware_version = 'AL0Q'
  info.addons = { 'hald-addon-storage' }
  org.freedesktop.Hal.Device.Storage.method_execpaths = { 'hal-storage-eject', 'hal-storage-closetray' }
  storage.partitioning_scheme = ''
  info.product = 'iHAS124   B'
  info.udi = '/org/freedesktop/Hal/devices/storage_model_iHAS124___B'
  storage.cdrom.cdr = true
  storage.cdrom.cdrw = true
  storage.cdrom.dvd = true
  storage.cdrom.dvdr = true
  storage.cdrom.dvdrw = true
  storage.cdrom.dvdrdl = true
  storage.cdrom.dvdram = true
  storage.cdrom.dvdplusr = true
  storage.cdrom.dvdplusrw = true
  storage.cdrom.dvdplusrwdl = false
  storage.cdrom.dvdplusrdl = true
  storage.cdrom.bd = false
  storage.cdrom.bdr = false
  storage.cdrom.bdre = false
  storage.cdrom.hddvd = false
  storage.cdrom.hddvdr = false
  storage.cdrom.hddvdrw = false
  storage.cdrom.mo = false
  storage.cdrom.mrw = true
  storage.cdrom.mrw_w = true
  storage.cdrom.support_media_changed = true
  storage.cdrom.support_multisession = true
  storage.cdrom.read_speed = 8468 (0x2114)
  storage.cdrom.write_speed = 8468 (0x2114)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_model_iHAS124___B'
  org.freedesktop.Hal.Device.Storage.method_names = { 'Eject', 'CloseTray' }
  org.freedesktop.Hal.Device.Storage.method_signatures = { 'as', 'as' }
  info.interfaces = { 'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage.Removable' }
  org.freedesktop.Hal.Device.Storage.method_argnames = { 'extra_options', 'extra_options' }
  block.device = '/dev/sr0'
  block.major = 11 (0xb)
  block.minor = 0 (0x0)
  block.is_volume = false
  storage.bus = 'pci'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_1c00_scsi_host_scsi_device_lun0'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sr0'
  storage.media_check_enabled = true
  info.category = 'storage'
  info.capabilities = { 'storage', 'block', 'storage.cdrom' }
  storage.automount_enabled_hint = true
  storage.no_partitions_hint = true
  storage.model = 'iHAS124   B'
  storage.vendor = 'ATAPI'
  storage.drive_type = 'cdrom'
  storage.lun = 0 (0x0)

  3: udi = '/org/freedesktop/Hal/devices/volume_part3_size_1024'
  linux.hotplug_type = 3 (0x3)
  volume.partition.scheme = 'mbr'
  volume.partition.type = '0x05'
  volume.partition.label = ''
  info.product = 'Volume'
  volume.partition.uuid = ''
  volume.partition.flags = {  }
  info.udi = '/org/freedesktop/Hal/devices/volume_part3_size_1024'
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_WDC_WD5000AAKX_001CA0_WD_WCAYUR040248'
  volume.fstype = ''
  volume.fsusage = 'partitiontable'
  volume.fsversion = ''
  volume.uuid = ''
  volume.label = ''
  volume.mount_point = ''
  volume.is_mounted = false
  volume.is_mounted_read_only = false
  volume.linux.is_device_mapper = false
  volume.is_disc = false
  volume.is_partition = true
  block.device = '/dev/sda3'
  block.major = 8 (0x8)
  block.minor = 3 (0x3)
  block.is_volume = true
  volume.block_size = 512 (0x200)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sda/sda3'
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_WDC_WD5000AAKX_001CA0_WD_WCAYUR040248'
  volume.partition.start = 405081684992ull (0x5e50bffc00ull)
  info.category = 'volume'
  info.capabilities = { 'volume', 'block' }
  volume.partition.number = 3 (0x3)
  volume.partition.media_size = 500107862016ull (0x7470c06000ull)
  volume.num_blocks = 2ull (0x2ull)
  volume.size = 1024ull (0x400ull)

  4: udi = '/org/freedesktop/Hal/devices/volume_uuid_5de13091_a2a0_467d_a3af_577c9da25d1f'
  org.freedesktop.Hal.Device.Volume.method_names = { 'Mount', 'Unmount', 'Eject' }
  org.freedesktop.Hal.Device.Volume.method_signatures = { 'ssas', 'as', 'as' }
  org.freedesktop.Hal.Device.Volume.method_argnames = { 'mount_point fstype extra_options', 'extra_options', 'extra_options' }
  linux.hotplug_type = 3 (0x3)
  info.interfaces = { 'org.freedesktop.Hal.Device.Volume' }
  volume.mount.valid_options = { 'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'relatime', 'noexec', 'quiet', 'remount', 'exec' }
  org.freedesktop.Hal.Device.Volume.method_execpaths = { 'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject' }
  volume.unmount.valid_options = { 'lazy' }
  info.product = 'Volume (ext4)'
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_5de13091_a2a0_467d_a3af_577c9da25d1f'
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_WDC_WD5000AAKX_001CA0_WD_WCAYUR040248'
  volume.fstype = 'ext4'
  volume.fsusage = 'filesystem'
  volume.fsversion = '1.0'
  volume.uuid = '5de13091-a2a0-467d-a3af-577c9da25d1f'
  volume.label = ''
  volume.mount_point = '/boot'
  volume.is_mounted = true
  volume.is_mounted_read_only = false
  volume.linux.is_device_mapper = false
  volume.is_disc = false
  volume.is_partition = true
  block.device = '/dev/sda5'
  block.major = 8 (0x8)
  block.minor = 5 (0x5)
  block.is_volume = true
  volume.block_size = 512 (0x200)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sda/sda5'
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_WDC_WD5000AAKX_001CA0_WD_WCAYUR040248'
  volume.partition.start = 405082733568ull (0x5e50cffc00ull)
  info.category = 'volume'
  info.capabilities = { 'volume', 'block' }
  volume.partition.number = 5 (0x5)
  volume.partition.media_size = 500107862016ull (0x7470c06000ull)
  volume.num_blocks = 524288ull (0x80000ull)
  volume.size = 268435456ull (0x10000000ull)
  volume.ignore = false

  5: udi = '/org/freedesktop/Hal/devices/volume_uuid_1d541567_4b9a_441b_b8ac_c449be714fb0'
  linux.hotplug_type = 3 (0x3)
  info.interfaces = { 'org.freedesktop.Hal.Device.Volume.Crypto' }
  org.freedesktop.Hal.Device.Volume.Crypto.method_names = { 'Setup', 'Teardown' }
  org.freedesktop.Hal.Device.Volume.Crypto.method_signatures = { 's', '' }
  org.freedesktop.Hal.Device.Volume.Crypto.method_argnames = { 'passphrase', '' }
  org.freedesktop.Hal.Device.Volume.Crypto.method_execpaths = { 'hal-luks-setup', 'hal-luks-teardown' }
  info.product = 'Volume (crypto_LUKS)'
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_1d541567_4b9a_441b_b8ac_c449be714fb0'
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_WDC_WD5000AAKX_001CA0_WD_WCAYUR040248'
  volume.fstype = 'crypto_LUKS'
  volume.fsusage = 'crypto'
  volume.fsversion = '256'
  volume.uuid = '1d541567-4b9a-441b-b8ac-c449be714fb0'
  volume.label = ''
  volume.mount_point = ''
  volume.is_mounted = false
  volume.is_mounted_read_only = false
  volume.linux.is_device_mapper = false
  volume.is_disc = false
  volume.is_partition = true
  block.device = '/dev/sda6'
  block.major = 8 (0x8)
  block.minor = 6 (0x6)
  block.is_volume = true
  volume.block_size = 512 (0x200)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sda/sda6'
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_WDC_WD5000AAKX_001CA0_WD_WCAYUR040248'
  volume.partition.start = 405352217600ull (0x5e60dffc00ull)
  info.category = 'volume'
  info.capabilities = { 'volume', 'block' }
  volume.partition.number = 6 (0x6)
  volume.partition.media_size = 500107862016ull (0x7470c06000ull)
  volume.num_blocks = 185067522ull (0xb07e802ull)
  volume.size = 94754571264ull (0x160fd00400ull)
  volume.ignore = true

  6: udi = '/org/freedesktop/Hal/devices/volume_uuid_142CF4E82CF4C5B0'
  org.freedesktop.Hal.Device.Volume.method_names = { 'Mount', 'Unmount', 'Eject' }
  org.freedesktop.Hal.Device.Volume.method_signatures = { 'ssas', 'as', 'as' }
  org.freedesktop.Hal.Device.Volume.method_argnames = { 'mount_point fstype extra_options', 'extra_options', 'extra_options' }
  linux.hotplug_type = 3 (0x3)
  info.interfaces = { 'org.freedesktop.Hal.Device.Volume' }
  volume.mount.valid_options = { 'ro', 'atime', 'noatime', 'relatime', 'fake_rw', 'no_def_opts', 'default_permissions', 'umask=', 'fmask=', 'dmask=', 'uid=', 'gid=', 'show_sys_files', 'silent', 'force', 'remove_hiberfile', 'locale=', 'streams_interface=', 'debug', 'no_detach', 'sync', 'dirsync', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'recover', 'norecover' }
  org.freedesktop.Hal.Device.Volume.method_execpaths = { 'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject' }
  volume.fstype.alternative = 'ntfs'
  volume.unmount.valid_options = { 'lazy' }
  volume.unmount.ntfs.valid_options = { 'lazy' }
  volume.mount.ntfs.valid_options = { 'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'relatime', 'noexec', 'quiet', 'remount', 'exec', 'uid=', 'gid=', 'umask=', 'utf8' }
  volume.policy.mount_filesystem = 'ntfs-3g'
  info.product = 'Volume (ntfs)'
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_142CF4E82CF4C5B0'
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_WDC_WD5000AAKX_001CA0_WD_WCAYUR040248'
  volume.fstype = 'ntfs-3g'
  volume.fsusage = 'filesystem'
  volume.fsversion = ''
  volume.uuid = '142CF4E82CF4C5B0'
  volume.label = ''
  volume.mount_point = ''
  volume.is_mounted = false
  volume.is_mounted_read_only = false
  volume.linux.is_device_mapper = false
  volume.is_disc = false
  volume.is_partition = true
  block.device = '/dev/sda2'
  block.major = 8 (0x8)
  block.minor = 2 (0x2)
  block.is_volume = true
  volume.block_size = 512 (0x200)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sda/sda2'
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_WDC_WD5000AAKX_001CA0_WD_WCAYUR040248'
  volume.partition.start = 105906176ull (0x6500000ull)
  info.category = 'volume'
  info.capabilities = { 'volume', 'block' }
  volume.partition.number = 2 (0x2)
  volume.partition.media_size = 500107862016ull (0x7470c06000ull)
  volume.num_blocks = 790967680ull (0x2f253580ull)
  volume.size = 404975452160ull (0x5e4a6b0000ull)
  volume.ignore = false

  7: udi = '/org/freedesktop/Hal/devices/volume_uuid_60C2F3B7C2F39010'
  org.freedesktop.Hal.Device.Volume.method_names = { 'Mount', 'Unmount', 'Eject' }
  org.freedesktop.Hal.Device.Volume.method_signatures = { 'ssas', 'as', 'as' }
  org.freedesktop.Hal.Device.Volume.method_argnames = { 'mount_point fstype extra_options', 'extra_options', 'extra_options' }
  linux.hotplug_type = 3 (0x3)
  info.interfaces = { 'org.freedesktop.Hal.Device.Volume' }
  volume.mount.valid_options = { 'ro', 'atime', 'noatime', 'relatime', 'fake_rw', 'no_def_opts', 'default_permissions', 'umask=', 'fmask=', 'dmask=', 'uid=', 'gid=', 'show_sys_files', 'silent', 'force', 'remove_hiberfile', 'locale=', 'streams_interface=', 'debug', 'no_detach', 'sync', 'dirsync', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'recover', 'norecover' }
  org.freedesktop.Hal.Device.Volume.method_execpaths = { 'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject' }
  volume.fstype.alternative = 'ntfs'
  volume.unmount.valid_options = { 'lazy' }
  volume.unmount.ntfs.valid_options = { 'lazy' }
  volume.mount.ntfs.valid_options = { 'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'relatime', 'noexec', 'quiet', 'remount', 'exec', 'uid=', 'gid=', 'umask=', 'utf8' }
  volume.policy.mount_filesystem = 'ntfs-3g'
  info.product = 'System Reserved'
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_60C2F3B7C2F39010'
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_WDC_WD5000AAKX_001CA0_WD_WCAYUR040248'
  volume.fstype = 'ntfs-3g'
  volume.fsusage = 'filesystem'
  volume.fsversion = ''
  volume.uuid = '60C2F3B7C2F39010'
  volume.label = 'System Reserved'
  volume.mount_point = ''
  volume.is_mounted = false
  volume.is_mounted_read_only = false
  volume.linux.is_device_mapper = false
  volume.is_disc = false
  volume.is_partition = true
  block.device = '/dev/sda1'
  block.major = 8 (0x8)
  block.minor = 1 (0x1)
  block.is_volume = true
  volume.block_size = 512 (0x200)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sda/sda1'
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_WDC_WD5000AAKX_001CA0_WD_WCAYUR040248'
  volume.partition.start = 1048576ull (0x100000ull)
  info.category = 'volume'
  info.capabilities = { 'volume', 'block' }
  volume.partition.number = 1 (0x1)
  volume.partition.media_size = 500107862016ull (0x7470c06000ull)
  volume.num_blocks = 204800ull (0x32000ull)
  volume.size = 104857600ull (0x6400000ull)
  volume.ignore = false

  8: udi = '/org/freedesktop/Hal/devices/usb_device_3f0_9311_CN0BB3B48F05HX_if1_printer_CN0BB3B48F05HX'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  printer.device = '/dev/usb/lp0'
  printer.originating_device = '/org/freedesktop/Hal/devices/usb_device_3f0_9311_CN0BB3B48F05HX_if1'
  info.subsystem = 'usb'
  info.product = 'Deskjet 3050 J610 series'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_3f0_9311_CN0BB3B48F05HX_if1_printer_CN0BB3B48F05HX'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.1/usb/lp0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_3f0_9311_CN0BB3B48F05HX_if1'
  printer.vendor = 'HP'
  printer.product = 'Deskjet 3050 J610 series'
  info.category = 'printer'
  info.capabilities = { 'printer' }
  printer.serial = 'CN0BB3B48F05HX'
  linux.device_file = '/dev/usb/lp0'
  printer.commandset = { 'MLC', 'PCL', 'DW-PCL', 'PML', '802.11', 'DESKJET', 'DYN' }
  printer.description = 'CH376B'
  info.vendor = 'HP'

  9: udi = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if0_video4linux'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'video4linux'
  video4linux.version = '2'
  video4linux.device = '/dev/video0'
  info.subsystem = 'video4linux'
  info.product = 'USB 2.0 Camera'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if0_video4linux'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/video4linux/video0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if0'
  info.category = 'video4linux'
  info.capabilities = { 'video4linux', 'video4linux.video_capture' }
  linux.device_file = '/dev/video0'

  10: udi = '/org/freedesktop/Hal/devices/storage_serial_WDC_WD5000AAKX_001CA0_WD_WCAYUR040248'
  storage.originating_device = '/org/freedesktop/Hal/devices/computer'
  info.vendor = 'ATA'
  storage.removable = false
  linux.hotplug_type = 3 (0x3)
  storage.removable.media_available = true
  storage.hotpluggable = false
  storage.requires_eject = false
  storage.serial = 'WDC_WD5000AAKX-001CA0_WD-WCAYUR040248'
  storage.size = 500107862016ull (0x7470c06000ull)
  storage.firmware_version = '15.01H51'
  info.product = 'WDC WD5000AAKX-0'
  info.udi = '/org/freedesktop/Hal/devices/storage_serial_WDC_WD5000AAKX_001CA0_WD_WCAYUR040248'
  storage.removable.media_size = 500107862016ull (0x7470c06000ull)
  storage.partitioning_scheme = 'mbr'
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_WDC_WD5000AAKX_001CA0_WD_WCAYUR040248'
  block.device = '/dev/sda'
  block.major = 8 (0x8)
  block.minor = 0 (0x0)
  block.is_volume = false
  storage.bus = 'pci'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_1c00_scsi_host_0_scsi_device_lun0'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sda'
  storage.media_check_enabled = false
  info.category = 'storage'
  info.capabilities = { 'storage', 'block' }
  storage.automount_enabled_hint = true
  storage.no_partitions_hint = false
  storage.model = 'WDC WD5000AAKX-0'
  storage.vendor = 'ATA'
  storage.drive_type = 'disk'
  storage.lun = 0 (0x0)

  11: udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'tty'
  serial.originating_device = '/org/freedesktop/Hal/devices/pnp_PNP0501'
  serial.device = '/dev/ttyS0'
  serial.port = 0 (0x0)
  serial.type = 'platform'
  info.subsystem = 'tty'
  info.product = '16550A-compatible COM port'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'
  linux.sysfs_path = '/sys/devices/pnp0/00:03/tty/ttyS0'
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501'
  info.category = 'serial'
  info.capabilities = { 'serial' }
  linux.device_file = '/dev/ttyS0'

  12: udi = '/org/freedesktop/Hal/devices/acpi_CPU0'
  linux.hotplug_type = 4 (0x4)
  info.product = 'Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz'
  info.udi = '/org/freedesktop/Hal/devices/acpi_CPU0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.category = 'processor'
  info.capabilities = { 'processor' }
  linux.acpi_type = 1 (0x1)
  processor.number = 0 (0x0)
  processor.can_throttle = true
  linux.acpi_path = '/proc/acpi/processor/CPU0'

  13: udi = '/org/freedesktop/Hal/devices/acpi_CPU1'
  linux.hotplug_type = 4 (0x4)
  info.product = 'Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz'
  info.udi = '/org/freedesktop/Hal/devices/acpi_CPU1'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.category = 'processor'
  info.capabilities = { 'processor' }
  linux.acpi_type = 1 (0x1)
  processor.number = 1 (0x1)
  processor.can_throttle = true
  linux.acpi_path = '/proc/acpi/processor/CPU1'

  14: udi = '/org/freedesktop/Hal/devices/acpi_CPU2'
  linux.hotplug_type = 4 (0x4)
  info.product = 'Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz'
  info.udi = '/org/freedesktop/Hal/devices/acpi_CPU2'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.category = 'processor'
  info.capabilities = { 'processor' }
  linux.acpi_type = 1 (0x1)
  processor.number = 2 (0x2)
  processor.can_throttle = true
  linux.acpi_path = '/proc/acpi/processor/CPU2'

  15: udi = '/org/freedesktop/Hal/devices/acpi_CPU3'
  linux.hotplug_type = 4 (0x4)
  info.product = 'Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz'
  info.udi = '/org/freedesktop/Hal/devices/acpi_CPU3'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.category = 'processor'
  info.capabilities = { 'processor' }
  linux.acpi_type = 1 (0x1)
  processor.number = 3 (0x3)
  processor.can_throttle = true
  linux.acpi_path = '/proc/acpi/processor/CPU3'

  16: udi = '/org/freedesktop/Hal/devices/computer_alsa_timer'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'
  info.subsystem = 'sound'
  info.product = 'ALSA Timer Device'
  info.udi = '/org/freedesktop/Hal/devices/computer_alsa_timer'
  linux.sysfs_path = '/sys/devices/virtual/sound/timer'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.category = 'alsa'
  info.capabilities = { 'alsa' }
  alsa.type = 'timer'
  linux.device_file = '/dev/snd/timer'
  alsa.device_file = '/dev/snd/timer'

  17: udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'
  info.subsystem = 'sound'
  info.product = 'OSS Sequencer Device'
  oss.device_file = '/dev/sequencer2'
  info.udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'
  linux.sysfs_path = '/sys/devices/virtual/sound/sequencer2'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  oss.type = 'sequencer'
  info.category = 'oss'
  info.capabilities = { 'oss' }
  linux.device_file = '/dev/sequencer2'

  18: udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'
  info.subsystem = 'sound'
  info.product = 'OSS Sequencer Device'
  oss.device_file = '/dev/sequencer'
  info.udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer'
  linux.sysfs_path = '/sys/devices/virtual/sound/sequencer'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  oss.type = 'sequencer'
  info.category = 'oss'
  info.capabilities = { 'oss' }
  linux.device_file = '/dev/sequencer'

  19: udi = '/org/freedesktop/Hal/devices/computer_alsa_sequencer'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'
  info.subsystem = 'sound'
  info.product = 'ALSA Sequencer Device'
  info.udi = '/org/freedesktop/Hal/devices/computer_alsa_sequencer'
  linux.sysfs_path = '/sys/devices/virtual/sound/seq'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.category = 'alsa'
  info.capabilities = { 'alsa' }
  alsa.type = 'sequencer'
  linux.device_file = '/dev/snd/seq'
  alsa.device_file = '/dev/snd/seq'

  20: udi = '/org/freedesktop/Hal/devices/net_computer_loopback'
  net.originating_device = '/org/freedesktop/Hal/devices/computer'
  net.interface = 'lo'
  net.address = '00:00:00:00:00:00'
  net.linux.ifindex = 1 (0x1)
  net.arp_proto_hw_id = 772 (0x304)
  linux.subsystem = 'net'
  linux.hotplug_type = 2 (0x2)
  info.subsystem = 'net'
  info.product = 'Loopback device Interface'
  info.udi = '/org/freedesktop/Hal/devices/net_computer_loopback'
  linux.sysfs_path = '/sys/devices/virtual/net/lo'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.category = 'net.loopback'
  info.capabilities = { 'net', 'net.loopback' }

  21: udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'input'
  input.device = '/dev/input/event2'
  input.product = 'Macintosh mouse button emulation'
  info.subsystem = 'input'
  info.product = 'Macintosh mouse button emulation'
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'
  linux.sysfs_path = '/sys/devices/virtual/input/input2/event2'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.category = 'input'
  info.capabilities = { 'input', 'input.mouse' }
  linux.device_file = '/dev/input/event2'

  22: udi = '/org/freedesktop/Hal/devices/computer_drm__null__ttm'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'drm'
  info.subsystem = 'drm'
  info.product = 'Direct Rendering Manager Device'
  info.udi = '/org/freedesktop/Hal/devices/computer_drm__null__ttm'
  linux.sysfs_path = '/sys/devices/virtual/drm/ttm'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.category = 'drm'
  info.capabilities = { 'drm' }
  linux.device_file = ''

  23: udi = '/org/freedesktop/Hal/devices/pci_8086_1c08_scsi_host_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi_host'
  info.subsystem = 'scsi_host'
  info.product = 'SCSI Host Adapter'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_1c08_scsi_host_0'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.5/host3/scsi_host/host3'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_1c08'
  scsi_host.host = 3 (0x3)
  info.category = 'scsi_host'
  info.capabilities = { 'scsi_host' }

  24: udi = '/org/freedesktop/Hal/devices/pci_8086_1c08_scsi_host'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi_host'
  info.subsystem = 'scsi_host'
  info.product = 'SCSI Host Adapter'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_1c08_scsi_host'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.5/host2/scsi_host/host2'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_1c08'
  scsi_host.host = 2 (0x2)
  info.category = 'scsi_host'
  info.capabilities = { 'scsi_host' }

  25: udi = '/org/freedesktop/Hal/devices/pci_8086_1c00_scsi_host_0_scsi_device_lun0_scsi_generic'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi_generic'
  scsi_generic.device = '/dev/sg1'
  info.subsystem = 'scsi_generic'
  info.product = 'SCSI Generic Interface'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_1c00_scsi_host_0_scsi_device_lun0_scsi_generic'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/scsi_generic/sg1'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_1c00_scsi_host_0_scsi_device_lun0'
  info.category = 'scsi_generic'
  info.capabilities = { 'scsi_generic' }
  linux.device_file = '/dev/sg1'

  26: udi = '/org/freedesktop/Hal/devices/pci_8086_1c00_scsi_host_0_scsi_host'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi_host'
  info.subsystem = 'scsi_host'
  info.product = 'SCSI Host Adapter'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_1c00_scsi_host_0_scsi_host'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host1/scsi_host/host1'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_1c00_scsi_host_0'
  scsi_host.host = 1 (0x1)
  info.category = 'scsi_host'
  info.capabilities = { 'scsi_host' }

  27: udi = '/org/freedesktop/Hal/devices/pci_8086_1c00_scsi_host_scsi_device_lun0_scsi_generic'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi_generic'
  scsi_generic.device = '/dev/sg0'
  info.subsystem = 'scsi_generic'
  info.product = 'SCSI Generic Interface'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_1c00_scsi_host_scsi_device_lun0_scsi_generic'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_generic/sg0'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_1c00_scsi_host_scsi_device_lun0'
  info.category = 'scsi_generic'
  info.capabilities = { 'scsi_generic' }
  linux.device_file = '/dev/sg0'

  28: udi = '/org/freedesktop/Hal/devices/pci_8086_1c00_scsi_host_scsi_host'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi_host'
  info.subsystem = 'scsi_host'
  info.product = 'SCSI Host Adapter'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_1c00_scsi_host_scsi_host'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/scsi_host/host0'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_1c00_scsi_host'
  scsi_host.host = 0 (0x0)
  info.category = 'scsi_host'
  info.capabilities = { 'scsi_host' }

  29: udi = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if2_sound_card_1_alsa_capture_0'
  alsa.type = 'capture'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'
  linux.device_file = '/dev/snd/pcmC1D0c'
  info.subsystem = 'sound'
  info.product = 'USB Audio ALSA Capture Device'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if2_sound_card_1_alsa_capture_0'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/sound/card1/pcmC1D0c'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if2_sound_card_1'
  info.category = 'alsa'
  alsa.originating_device = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if2_sound_card_1'
  info.capabilities = { 'alsa' }
  alsa.device_file = '/dev/snd/pcmC1D0c'
  alsa.card_id = 'Sonix Technology Co., Ltd. USB 2.0 Camera'
  alsa.device = 0 (0x0)
  alsa.pcm_class = 'generic'
  alsa.device_id = 'USB Audio'
  alsa.card = 1 (0x1)

  30: udi = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if2_sound_card_1_oss_mixer__1'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if2_sound_card_1_oss_mixer__1'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'
  info.subsystem = 'sound'
  oss.device_file = '/dev/mixer1'
  oss.originating_device = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if2_sound_card_1'
  oss.card = 1 (0x1)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/sound/card1/mixer1'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if2_sound_card_1'
  oss.card_id = 'Sonix Technology Co., Ltd. USB 2.0 Camera'
  info.category = 'oss'
  info.capabilities = { 'oss' }
  oss.type = 'mixer'
  info.product = 'Sonix Technology Co., Ltd. USB 2.0 Camera OSS Control Device'
  linux.device_file = '/dev/mixer1'

  31: udi = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if2_sound_card_1_oss_pcm_0_0'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if2_sound_card_1_oss_pcm_0_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'
  info.subsystem = 'sound'
  oss.device_file = '/dev/dsp1'
  oss.originating_device = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if2_sound_card_1'
  oss.card = 1 (0x1)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/sound/card1/dsp1'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if2_sound_card_1'
  oss.device = 0 (0x0)
  oss.card_id = 'Sonix Technology Co., Ltd. USB 2.0 Camera'
  info.category = 'oss'
  info.capabilities = { 'oss' }
  oss.type = 'pcm'
  info.product = 'Sonix Technology Co., Ltd. USB 2.0 Camera OSS PCM Device'
  linux.device_file = '/dev/dsp1'

  32: udi = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if2_sound_card_1_alsa_control__1'
  linux.device_file = '/dev/snd/controlC1'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'
  info.subsystem = 'sound'
  info.product = 'Sonix Technology Co., Ltd. USB 2.0 Camera ALSA Control Device'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if2_sound_card_1_alsa_control__1'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/sound/card1/controlC1'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if2_sound_card_1'
  info.category = 'alsa'
  alsa.originating_device = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if2_sound_card_1'
  info.capabilities = { 'alsa' }
  alsa.type = 'control'
  alsa.card_id = 'Sonix Technology Co., Ltd. USB 2.0 Camera'
  alsa.card = 1 (0x1)
  alsa.device_file = '/dev/snd/controlC1'

  33: udi = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if2_sound_card_1_oss_pcm_0'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if2_sound_card_1_oss_pcm_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'
  info.subsystem = 'sound'
  oss.device_file = '/dev/audio1'
  oss.originating_device = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if2_sound_card_1'
  oss.card = 1 (0x1)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/sound/card1/audio1'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if2_sound_card_1'
  oss.device = 0 (0x0)
  oss.card_id = 'Sonix Technology Co., Ltd. USB 2.0 Camera'
  info.category = 'oss'
  info.capabilities = { 'oss' }
  oss.type = 'pcm'
  info.product = 'Sonix Technology Co., Ltd. USB 2.0 Camera OSS PCM Device'
  linux.device_file = '/dev/audio1'

  34: udi = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if2_sound_card_1'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'
  sound.originating_device = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if2'
  sound.card = 1 (0x1)
  sound.card_id = 'Sonix Technology Co., Ltd. USB 2.0 Camera'
  info.product = 'Sonix Technology Co., Ltd. USB 2.0 Camera Sound Card'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if2_sound_card_1'
  info.subsystem = 'sound'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/sound/card1'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if2'
  info.category = 'sound'
  info.capabilities = { 'sound' }

  35: udi = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if0_logicaldev_input'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'input'
  input.device = '/dev/input/event7'
  input.product = 'USB 2.0 Camera'
  button.has_state = false
  info.addons.singleton = { 'hald-addon-input' }
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if0'
  info.subsystem = 'input'
  info.product = 'USB 2.0 Camera'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if0_logicaldev_input'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input7/event7'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if0'
  info.category = 'input'
  info.capabilities = { 'input', 'button', 'input.keys' }
  linux.device_file = '/dev/input/event7'

  36: udi = '/org/freedesktop/Hal/devices/net_00_16_0a_07_ad_dd'
  net.originating_device = '/org/freedesktop/Hal/devices/pci_10ec_8139'
  net.interface = 'eth0'
  net.address = '00:16:0a:07:ad:dd'
  net.linux.ifindex = 2 (0x2)
  net.arp_proto_hw_id = 1 (0x1)
  net.80203.mac_address = 94657555933ull (0x160a07adddull)
  info.interfaces = { 'org.freedesktop.Hal.Device.WakeOnLan' }
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'net'
  org.freedesktop.Hal.Device.WakeOnLan.method_signatures = { '', '', 'b' }
  org.freedesktop.Hal.Device.WakeOnLan.method_names = { 'GetSupported', 'GetEnabled', 'SetEnabled' }
  org.freedesktop.Hal.Device.WakeOnLan.method_execpaths = { 'hal-system-wol-supported', 'hal-system-wol-enabled', 'hal-system-wol-enable' }
  org.freedesktop.Hal.Device.WakeOnLan.method_argnames = { '', '', 'enable' }
  info.subsystem = 'net'
  info.product = 'Networking Interface'
  info.udi = '/org/freedesktop/Hal/devices/net_00_16_0a_07_ad_dd'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/0000:05:01.0/net/eth0'
  info.parent = '/org/freedesktop/Hal/devices/pci_10ec_8139'
  info.category = 'net.80203'
  info.capabilities = { 'net', 'net.80203', 'wake_on_lan' }

  37: udi = '/org/freedesktop/Hal/devices/pci_8086_1c20_sound_card_0_alsa_playback_0'
  alsa.type = 'playback'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'
  linux.device_file = '/dev/snd/pcmC0D0p'
  info.subsystem = 'sound'
  info.product = 'HDA Generic ALSA Playback Device'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_1c20_sound_card_0_alsa_playback_0'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0p'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_1c20_sound_card_0'
  info.category = 'alsa'
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_1c20_sound_card_0'
  info.capabilities = { 'alsa' }
  alsa.device_file = '/dev/snd/pcmC0D0p'
  alsa.card_id = 'HDA Intel PCH'
  alsa.device = 0 (0x0)
  alsa.pcm_class = 'generic'
  alsa.device_id = 'HDA Generic'
  alsa.card = 0 (0x0)

  38: udi = '/org/freedesktop/Hal/devices/pci_8086_1c20_sound_card_0_alsa_capture_0'
  alsa.type = 'capture'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'
  linux.device_file = '/dev/snd/pcmC0D0c'
  info.subsystem = 'sound'
  info.product = 'HDA Generic ALSA Capture Device'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_1c20_sound_card_0_alsa_capture_0'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0c'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_1c20_sound_card_0'
  info.category = 'alsa'
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_1c20_sound_card_0'
  info.capabilities = { 'alsa' }
  alsa.device_file = '/dev/snd/pcmC0D0c'
  alsa.card_id = 'HDA Intel PCH'
  alsa.device = 0 (0x0)
  alsa.pcm_class = 'generic'
  alsa.device_id = 'HDA Generic'
  alsa.card = 0 (0x0)

  39: udi = '/org/freedesktop/Hal/devices/pci_8086_1c20_sound_card_0_oss_mixer__1'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_1c20_sound_card_0_oss_mixer__1'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'
  info.subsystem = 'sound'
  oss.device_file = '/dev/mixer'
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_8086_1c20_sound_card_0'
  oss.card = 0 (0x0)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/mixer'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_1c20_sound_card_0'
  oss.device_id = 'HDA Generic'
  oss.card_id = 'HDA Intel PCH'
  info.category = 'oss'
  info.capabilities = { 'oss' }
  oss.type = 'mixer'
  info.product = 'HDA Generic OSS Control Device'
  linux.device_file = '/dev/mixer'

  40: udi = '/org/freedesktop/Hal/devices/pci_8086_1c20_sound_card_0_alsa_hw_specific_1'
  linux.device_file = '/dev/snd/hwC0D1'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'
  info.subsystem = 'sound'
  info.product = 'HDA Intel PCH ALSA hardware specific Device'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_1c20_sound_card_0_alsa_hw_specific_1'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D1'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_1c20_sound_card_0'
  info.category = 'alsa'
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_1c20_sound_card_0'
  info.capabilities = { 'alsa' }
  alsa.device_file = '/dev/snd/hwC0D1'
  alsa.card_id = 'HDA Intel PCH'
  alsa.device = 1 (0x1)
  alsa.type = 'hw_specific'
  alsa.card = 0 (0x0)

  41: udi = '/org/freedesktop/Hal/devices/pci_8086_1c20_sound_card_0_oss_pcm_0_0'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_1c20_sound_card_0_oss_pcm_0_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'
  info.subsystem = 'sound'
  oss.device_file = '/dev/dsp'
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_8086_1c20_sound_card_0'
  oss.card = 0 (0x0)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/dsp'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_1c20_sound_card_0'
  oss.device_id = 'HDA Generic'
  oss.card_id = 'HDA Intel PCH'
  info.category = 'oss'
  info.capabilities = { 'oss' }
  oss.type = 'pcm'
  info.product = 'HDA Generic OSS PCM Device'
  oss.device = 0 (0x0)
  linux.device_file = '/dev/dsp'

  42: udi = '/org/freedesktop/Hal/devices/pci_8086_1c20_sound_card_0_alsa_control__1'
  linux.device_file = '/dev/snd/controlC0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'
  info.subsystem = 'sound'
  info.product = 'HDA Intel PCH ALSA Control Device'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_1c20_sound_card_0_alsa_control__1'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/controlC0'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_1c20_sound_card_0'
  info.category = 'alsa'
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_1c20_sound_card_0'
  info.capabilities = { 'alsa' }
  alsa.type = 'control'
  alsa.card_id = 'HDA Intel PCH'
  alsa.card = 0 (0x0)
  alsa.device_file = '/dev/snd/controlC0'

  43: udi = '/org/freedesktop/Hal/devices/pci_8086_1c20_sound_card_0_oss_pcm_0'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_1c20_sound_card_0_oss_pcm_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'
  info.subsystem = 'sound'
  oss.device_file = '/dev/audio'
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_8086_1c20_sound_card_0'
  oss.card = 0 (0x0)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/audio'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_1c20_sound_card_0'
  oss.device_id = 'HDA Generic'
  oss.card_id = 'HDA Intel PCH'
  info.category = 'oss'
  info.capabilities = { 'oss' }
  oss.type = 'pcm'
  info.product = 'HDA Generic OSS PCM Device'
  oss.device = 0 (0x0)
  linux.device_file = '/dev/audio'

  44: udi = '/org/freedesktop/Hal/devices/pci_8086_1c20_sound_card_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'
  sound.originating_device = '/org/freedesktop/Hal/devices/pci_8086_1c20'
  sound.card = 0 (0x0)
  sound.card_id = 'HDA Intel PCH'
  info.product = 'HDA Intel PCH Sound Card'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_1c20_sound_card_0'
  info.subsystem = 'sound'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_1c20'
  info.category = 'sound'
  info.capabilities = { 'sound' }

  45: udi = '/org/freedesktop/Hal/devices/usb_device_4b4_121f_noserial_if0_logicaldev_input'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'input'
  input.device = '/dev/input/event3'
  input.product = 'SteelSeries ApS Ikari Laser'
  info.addons.singleton = { 'hald-addon-input' }
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_4b4_121f_noserial_if0'
  info.subsystem = 'input'
  info.product = 'SteelSeries ApS Ikari Laser'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_4b4_121f_noserial_if0_logicaldev_input'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input3/event3'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_4b4_121f_noserial_if0'
  info.category = 'input'
  info.capabilities = { 'input', 'input.keyboard', 'input.keypad', 'input.keys', 'input.mouse', 'button' }
  linux.device_file = '/dev/input/event3'

  46: udi = '/org/freedesktop/Hal/devices/usb_device_46d_c22a_noserial_if1_logicaldev_input'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'input'
  input.device = '/dev/input/event6'
  input.product = 'Gaming Keyboard G110'
  info.addons.singleton = { 'hald-addon-input' }
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_46d_c22a_noserial_if1'
  info.subsystem = 'input'
  info.product = 'Gaming Keyboard G110'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c22a_noserial_if1_logicaldev_input'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.1/input/input6/event6'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_46d_c22a_noserial_if1'
  info.category = 'input'
  info.capabilities = { 'input', 'input.keys', 'button' }
  linux.device_file = '/dev/input/event6'

  47: udi = '/org/freedesktop/Hal/devices/usb_device_46d_c22a_noserial_if0_logicaldev_input'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'input'
  input.device = '/dev/input/event5'
  input.product = 'Gaming Keyboard G110'
  info.addons.singleton = { 'hald-addon-input' }
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_46d_c22a_noserial_if0'
  info.subsystem = 'input'
  info.product = 'Gaming Keyboard G110'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c22a_noserial_if0_logicaldev_input'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.0/input/input5/event5'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_46d_c22a_noserial_if0'
  info.category = 'input'
  info.capabilities = { 'input', 'input.keyboard', 'input.keypad', 'input.keys', 'button' }
  linux.device_file = '/dev/input/event5'

  48: udi = '/org/freedesktop/Hal/devices/usb_device_46d_c22b_noserial_if0_logicaldev_input'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'input'
  input.device = '/dev/input/event4'
  input.product = 'LOGITECH G110 G-keys'
  info.addons.singleton = { 'hald-addon-input' }
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_46d_c22b_noserial_if0'
  info.subsystem = 'input'
  info.product = 'LOGITECH G110 G-keys'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c22b_noserial_if0_logicaldev_input'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.0/input/input4/event4'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_46d_c22b_noserial_if0'
  info.category = 'input'
  info.capabilities = { 'input', 'input.keyboard', 'input.keypad', 'input.keys', 'button' }
  linux.device_file = '/dev/input/event4'

  49: udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'input'
  input.device = '/dev/input/event0'
  input.product = 'Power Button'
  button.has_state = false
  button.type = 'power'
  info.addons.singleton = { 'hald-addon-input' }
  info.subsystem = 'input'
  info.product = 'Power Button'
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.category = 'input'
  info.capabilities = { 'input', 'button', 'input.keys' }
  linux.device_file = '/dev/input/event0'

  50: udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'input'
  input.device = '/dev/input/event1'
  input.product = 'Power Button'
  button.has_state = false
  button.type = 'power'
  info.addons.singleton = { 'hald-addon-input' }
  info.subsystem = 'input'
  info.product = 'Power Button'
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.category = 'input'
  info.capabilities = { 'input', 'button', 'input.keys' }
  linux.device_file = '/dev/input/event1'

  51: udi = '/org/freedesktop/Hal/devices/pnp_PNP0103'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'
  pnp.id = 'PNP0103'
  info.subsystem = 'pnp'
  info.product = 'PnP Device (PNP0103)'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0103'
  linux.sysfs_path = '/sys/devices/pnp0/00:0b'
  info.parent = '/org/freedesktop/Hal/devices/computer'

  52: udi = '/org/freedesktop/Hal/devices/pnp_INT3f0d'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'
  info.linux.driver = 'system'
  pnp.id = 'INT3f0d'
  info.subsystem = 'pnp'
  info.product = 'PnP Device (INT3f0d)'
  info.udi = '/org/freedesktop/Hal/devices/pnp_INT3f0d'
  linux.sysfs_path = '/sys/devices/pnp0/00:0a'
  info.parent = '/org/freedesktop/Hal/devices/computer'

  53: udi = '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'
  info.linux.driver = 'system'
  pnp.id = 'PNP0c01'
  pnp.description = 'System Board'
  info.subsystem = 'pnp'
  info.product = 'System Board'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'
  linux.sysfs_path = '/sys/devices/pnp0/00:09'
  info.parent = '/org/freedesktop/Hal/devices/computer'

  54: udi = '/org/freedesktop/Hal/devices/pnp_PNP0c04'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'
  pnp.id = 'PNP0c04'
  pnp.description = 'Math Coprocessor'
  info.subsystem = 'pnp'
  info.product = 'Math Coprocessor'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c04'
  linux.sysfs_path = '/sys/devices/pnp0/00:08'
  info.parent = '/org/freedesktop/Hal/devices/computer'

  55: udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'
  info.linux.driver = 'system'
  pnp.id = 'PNP0c02'
  pnp.description = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'
  info.subsystem = 'pnp'
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_0'
  linux.sysfs_path = '/sys/devices/pnp0/00:07'
  info.parent = '/org/freedesktop/Hal/devices/computer'

  56: udi = '/org/freedesktop/Hal/devices/pnp_PNP0800'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'
  pnp.id = 'PNP0800'
  pnp.description = 'AT-style speaker sound'
  info.subsystem = 'pnp'
  info.product = 'AT-style speaker sound'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0800'
  linux.sysfs_path = '/sys/devices/pnp0/00:06'
  info.parent = '/org/freedesktop/Hal/devices/computer'

  57: udi = '/org/freedesktop/Hal/devices/pnp_PNP0b00'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'
  info.linux.driver = 'rtc_cmos'
  pnp.id = 'PNP0b00'
  pnp.description = 'AT Real-Time Clock'
  info.subsystem = 'pnp'
  info.product = 'AT Real-Time Clock'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0b00'
  linux.sysfs_path = '/sys/devices/pnp0/00:05'
  info.parent = '/org/freedesktop/Hal/devices/computer'

  58: udi = '/org/freedesktop/Hal/devices/pnp_PNP0200'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'
  pnp.id = 'PNP0200'
  pnp.description = 'AT DMA Controller'
  info.subsystem = 'pnp'
  info.product = 'AT DMA Controller'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0200'
  linux.sysfs_path = '/sys/devices/pnp0/00:04'
  info.parent = '/org/freedesktop/Hal/devices/computer'

  59: udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'
  info.linux.driver = 'serial'
  pnp.id = 'PNP0501'
  pnp.description = '16550A-compatible COM port'
  info.subsystem = 'pnp'
  info.product = '16550A-compatible COM port'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'
  linux.sysfs_path = '/sys/devices/pnp0/00:03'
  info.parent = '/org/freedesktop/Hal/devices/computer'

  60: udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'
  info.linux.driver = 'system'
  pnp.id = 'PNP0c02'
  pnp.description = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'
  info.subsystem = 'pnp'
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02'
  linux.sysfs_path = '/sys/devices/pnp0/00:02'
  info.parent = '/org/freedesktop/Hal/devices/computer'

  61: udi = '/org/freedesktop/Hal/devices/pnp_PNP0c01'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'
  info.linux.driver = 'system'
  pnp.id = 'PNP0c01'
  pnp.description = 'System Board'
  info.subsystem = 'pnp'
  info.product = 'System Board'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c01'
  linux.sysfs_path = '/sys/devices/pnp0/00:01'
  info.parent = '/org/freedesktop/Hal/devices/computer'

  62: udi = '/org/freedesktop/Hal/devices/pnp_PNP0a08'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'
  pnp.id = 'PNP0a08'
  info.subsystem = 'pnp'
  info.product = 'PnP Device (PNP0a08)'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0a08'
  linux.sysfs_path = '/sys/devices/pnp0/00:00'
  info.parent = '/org/freedesktop/Hal/devices/computer'

  63: udi = '/org/freedesktop/Hal/devices/platform_vga16fb_0'
  platform.id = 'vga16fb.0'
  linux.subsystem = 'platform'
  info.linux.driver = 'vga16fb'
  linux.hotplug_type = 2 (0x2)
  info.subsystem = 'platform'
  info.product = 'Platform Device (vga16fb.0)'
  info.udi = '/org/freedesktop/Hal/devices/platform_vga16fb_0'
  linux.sysfs_path = '/sys/devices/platform/vga16fb.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'

  64: udi = '/org/freedesktop/Hal/devices/platform_serial8250'
  platform.id = 'serial8250'
  linux.subsystem = 'platform'
  info.linux.driver = 'serial8250'
  linux.hotplug_type = 2 (0x2)
  info.subsystem = 'platform'
  info.product = 'Platform Device (serial8250)'
  info.udi = '/org/freedesktop/Hal/devices/platform_serial8250'
  linux.sysfs_path = '/sys/devices/platform/serial8250'
  info.parent = '/org/freedesktop/Hal/devices/computer'

  65: udi = '/org/freedesktop/Hal/devices/platform_pcspkr'
  platform.id = 'pcspkr'
  linux.subsystem = 'platform'
  linux.hotplug_type = 2 (0x2)
  info.subsystem = 'platform'
  info.product = 'Platform Device (pcspkr)'
  info.udi = '/org/freedesktop/Hal/devices/platform_pcspkr'
  linux.sysfs_path = '/sys/devices/platform/pcspkr'
  info.parent = '/org/freedesktop/Hal/devices/computer'

  66: udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'serio'
  serio.description = 'i8042 AUX port'
  serio.id = 'serio1'
  info.subsystem = 'serio'
  info.product = 'i8042 AUX port'
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1'
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'

  67: udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'serio'
  serio.description = 'i8042 KBD port'
  serio.id = 'serio0'
  info.subsystem = 'serio'
  info.product = 'i8042 KBD port'
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'
  linux.sysfs_path = '/sys/devices/platform/i8042/serio0'
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'

  68: udi = '/org/freedesktop/Hal/devices/platform_i8042'
  platform.id = 'i8042'
  linux.subsystem = 'platform'
  info.linux.driver = 'i8042'
  linux.hotplug_type = 2 (0x2)
  info.subsystem = 'platform'
  info.product = 'Platform Device (i8042)'
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042'
  linux.sysfs_path = '/sys/devices/platform/i8042'
  info.parent = '/org/freedesktop/Hal/devices/computer'

  69: udi = '/org/freedesktop/Hal/devices/platform_eisa_0'
  platform.id = 'eisa.0'
  linux.subsystem = 'platform'
  linux.hotplug_type = 2 (0x2)
  info.subsystem = 'platform'
  info.product = 'Platform Device (eisa.0)'
  info.udi = '/org/freedesktop/Hal/devices/platform_eisa_0'
  linux.sysfs_path = '/sys/devices/platform/eisa.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'

  70: udi = '/org/freedesktop/Hal/devices/platform_Fixed_MDIO_bus_0'
  platform.id = 'Fixed MDIO bus.0'
  linux.subsystem = 'platform'
  linux.hotplug_type = 2 (0x2)
  info.subsystem = 'platform'
  info.product = 'Platform Device (Fixed MDIO bus.0)'
  info.udi = '/org/freedesktop/Hal/devices/platform_Fixed_MDIO_bus_0'
  linux.sysfs_path = '/sys/devices/platform/Fixed MDIO bus.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'

  71: udi = '/org/freedesktop/Hal/devices/pci_8086_1c08'
  pci.subsys_vendor = 'Micro-Star International Co., Ltd.'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.linux.driver = 'ata_piix'
  pci.product = 'Cougar Point 2 port SATA IDE Controller'
  info.subsystem = 'pci'
  info.product = 'Cougar Point 2 port SATA IDE Controller'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_1c08'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.5'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.5'
  pci.product_id = 7176 (0x1c08)
  pci.vendor_id = 32902 (0x8086)
  pci.subsys_product_id = 30323 (0x7673)
  pci.subsys_vendor_id = 5218 (0x1462)
  pci.device_class = 1 (0x1)
  pci.device_subclass = 1 (0x1)
  pci.device_protocol = 133 (0x85)
  pci.vendor = 'Intel Corporation'
  info.vendor = 'Intel Corporation'

  72: udi = '/org/freedesktop/Hal/devices/pci_8086_1c22'
  pci.subsys_vendor = 'Micro-Star International Co., Ltd.'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  pci.product = 'Cougar Point SMBus Controller'
  info.subsystem = 'pci'
  info.product = 'Cougar Point SMBus Controller'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_1c22'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.3'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.3'
  pci.product_id = 7202 (0x1c22)
  pci.vendor_id = 32902 (0x8086)
  pci.subsys_product_id = 30323 (0x7673)
  pci.subsys_vendor_id = 5218 (0x1462)
  pci.device_class = 12 (0xc)
  pci.device_subclass = 5 (0x5)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Intel Corporation'
  info.vendor = 'Intel Corporation'

  73: udi = '/org/freedesktop/Hal/devices/pci_8086_1c00_scsi_host_0_scsi_device_lun0'
  scsi.type = 'disk'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi'
  info.linux.driver = 'sd'
  info.subsystem = 'scsi'
  info.product = 'SCSI Device'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_1c00_scsi_host_0_scsi_device_lun0'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_1c00_scsi_host_0'
  scsi.host = 1 (0x1)
  scsi.bus = 0 (0x0)
  scsi.target = 0 (0x0)
  scsi.lun = 0 (0x0)
  scsi.model = 'WDC WD5000AAKX-0'
  scsi.vendor = 'ATA'

  74: udi = '/org/freedesktop/Hal/devices/pci_8086_1c00_scsi_host_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi_host'
  info.subsystem = 'scsi_host'
  info.product = 'SCSI Host Adapter'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_1c00_scsi_host_0'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host1'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_1c00'
  scsi_host.host = 1 (0x1)
  info.category = 'scsi_host'
  info.capabilities = { 'scsi_host' }

  75: udi = '/org/freedesktop/Hal/devices/pci_8086_1c00_scsi_host_scsi_device_lun0'
  scsi.type = 'cdrom'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi'
  info.linux.driver = 'sr'
  info.subsystem = 'scsi'
  info.product = 'SCSI Device'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_1c00_scsi_host_scsi_device_lun0'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_1c00_scsi_host'
  scsi.host = 0 (0x0)
  scsi.bus = 0 (0x0)
  scsi.target = 0 (0x0)
  scsi.lun = 0 (0x0)
  scsi.model = 'iHAS124   B'
  scsi.vendor = 'ATAPI'

  76: udi = '/org/freedesktop/Hal/devices/pci_8086_1c00_scsi_host'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi_host'
  info.subsystem = 'scsi_host'
  info.product = 'SCSI Host Adapter'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_1c00_scsi_host'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_1c00'
  scsi_host.host = 0 (0x0)
  info.category = 'scsi_host'
  info.capabilities = { 'scsi_host' }

  77: udi = '/org/freedesktop/Hal/devices/pci_8086_1c00'
  pci.subsys_vendor = 'Micro-Star International Co., Ltd.'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.linux.driver = 'ata_piix'
  pci.product = 'Cougar Point 4 port SATA IDE Controller'
  info.subsystem = 'pci'
  info.product = 'Cougar Point 4 port SATA IDE Controller'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_1c00'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2'
  pci.product_id = 7168 (0x1c00)
  pci.vendor_id = 32902 (0x8086)
  pci.subsys_product_id = 30323 (0x7673)
  pci.subsys_vendor_id = 5218 (0x1462)
  pci.device_class = 1 (0x1)
  pci.device_subclass = 1 (0x1)
  pci.device_protocol = 138 (0x8a)
  pci.vendor = 'Intel Corporation'
  info.vendor = 'Intel Corporation'

  78: udi = '/org/freedesktop/Hal/devices/pci_8086_1c46'
  pci.subsys_vendor = 'Micro-Star International Co., Ltd.'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.subsystem = 'pci'
  info.product = 'Unknown (0x1c46)'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_1c46'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.0'
  pci.product_id = 7238 (0x1c46)
  pci.vendor_id = 32902 (0x8086)
  pci.subsys_product_id = 30323 (0x7673)
  pci.subsys_vendor_id = 5218 (0x1462)
  pci.device_class = 6 (0x6)
  pci.device_subclass = 1 (0x1)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Intel Corporation'
  info.vendor = 'Intel Corporation'

  79: udi = '/org/freedesktop/Hal/devices/usb_device_8087_24_noserial_0_if0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'hub'
  info.subsystem = 'usb'
  info.product = 'USB Hub Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_8087_24_noserial_0_if0'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.num_interfaces = 1 (0x1)
  usb.device_class = 9 (0x9)
  usb.device_subclass = 0 (0x0)
  usb.device_protocol = 1 (0x1)
  usb.vendor_id = 32903 (0x8087)
  usb.product_id = 36 (0x24)
  usb.max_power = 0 (0x0)
  usb.product = 'USB Hub Interface'
  usb.num_ports = 8 (0x8)
  usb.device_revision_bcd = 0 (0x0)
  usb.is_self_powered = true
  usb.speed = 480.000
  usb.linux.device_number = 2 (0x2)
  usb.can_wake_up = true
  usb.version = 2.00000
  usb.bus_number = 2 (0x2)
  usb.interface.number = 0 (0x0)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_8087_24_noserial_0'
  usb.interface.subclass = 0 (0x0)
  usb.interface.class = 9 (0x9)
  usb.interface.protocol = 0 (0x0)

  80: udi = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if3'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'snd-usb-audio'
  info.subsystem = 'usb'
  info.product = 'USB Audio Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if3'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.3'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.num_interfaces = 4 (0x4)
  usb.device_class = 239 (0xef)
  usb.device_subclass = 2 (0x2)
  usb.device_protocol = 1 (0x1)
  usb.vendor_id = 3141 (0xc45)
  usb.product_id = 25312 (0x62e0)
  usb.vendor = 'Microdia'
  usb.max_power = 168 (0xa8)
  usb.product = 'USB Audio Interface'
  usb.num_ports = 0 (0x0)
  usb.device_revision_bcd = 256 (0x100)
  usb.is_self_powered = false
  usb.speed = 480.000
  usb.linux.device_number = 4 (0x4)
  usb.can_wake_up = false
  usb.version = 2.00000
  usb.bus_number = 2 (0x2)
  usb.interface.number = 3 (0x3)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.3'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial'
  usb.interface.subclass = 2 (0x2)
  usb.interface.class = 1 (0x1)
  usb.interface.protocol = 0 (0x0)

  81: udi = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if2'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'snd-usb-audio'
  info.subsystem = 'usb'
  info.product = 'USB Audio Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if2'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.num_interfaces = 4 (0x4)
  usb.device_class = 239 (0xef)
  usb.device_subclass = 2 (0x2)
  usb.device_protocol = 1 (0x1)
  usb.vendor_id = 3141 (0xc45)
  usb.product_id = 25312 (0x62e0)
  usb.vendor = 'Microdia'
  usb.max_power = 168 (0xa8)
  usb.product = 'USB Audio Interface'
  usb.num_ports = 0 (0x0)
  usb.device_revision_bcd = 256 (0x100)
  usb.is_self_powered = false
  usb.speed = 480.000
  usb.linux.device_number = 4 (0x4)
  usb.can_wake_up = false
  usb.version = 2.00000
  usb.bus_number = 2 (0x2)
  usb.interface.number = 2 (0x2)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial'
  usb.interface.subclass = 1 (0x1)
  usb.interface.class = 1 (0x1)
  usb.interface.description = 'USB Audio Device'
  usb.interface.protocol = 0 (0x0)

  82: udi = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if1'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'uvcvideo'
  info.subsystem = 'usb'
  info.product = 'USB Video Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if1'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.1'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.num_interfaces = 4 (0x4)
  usb.device_class = 239 (0xef)
  usb.device_subclass = 2 (0x2)
  usb.device_protocol = 1 (0x1)
  usb.vendor_id = 3141 (0xc45)
  usb.product_id = 25312 (0x62e0)
  usb.vendor = 'Microdia'
  usb.max_power = 168 (0xa8)
  usb.product = 'USB Video Interface'
  usb.num_ports = 0 (0x0)
  usb.device_revision_bcd = 256 (0x100)
  usb.is_self_powered = false
  usb.speed = 480.000
  usb.linux.device_number = 4 (0x4)
  usb.can_wake_up = false
  usb.version = 2.00000
  usb.bus_number = 2 (0x2)
  usb.interface.number = 1 (0x1)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.1'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial'
  usb.interface.subclass = 2 (0x2)
  usb.interface.class = 14 (0xe)
  usb.interface.protocol = 0 (0x0)

  83: udi = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'uvcvideo'
  info.subsystem = 'usb'
  info.product = 'USB Video Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if0'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.num_interfaces = 4 (0x4)
  usb.device_class = 239 (0xef)
  usb.device_subclass = 2 (0x2)
  usb.device_protocol = 1 (0x1)
  usb.vendor_id = 3141 (0xc45)
  usb.product_id = 25312 (0x62e0)
  usb.vendor = 'Microdia'
  usb.max_power = 168 (0xa8)
  usb.product = 'USB Video Interface'
  usb.num_ports = 0 (0x0)
  usb.device_revision_bcd = 256 (0x100)
  usb.is_self_powered = false
  usb.speed = 480.000
  usb.linux.device_number = 4 (0x4)
  usb.can_wake_up = false
  usb.version = 2.00000
  usb.bus_number = 2 (0x2)
  usb.interface.number = 0 (0x0)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial'
  usb.interface.subclass = 1 (0x1)
  usb.interface.class = 14 (0xe)
  usb.interface.description = 'USB Camera'
  usb.interface.protocol = 0 (0x0)

  84: udi = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'usb'
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6'
  usb_device.configuration_value = 1 (0x1)
  usb_device.num_configurations = 1 (0x1)
  usb_device.num_interfaces = 4 (0x4)
  usb_device.device_class = 239 (0xef)
  usb_device.device_subclass = 2 (0x2)
  usb_device.device_protocol = 1 (0x1)
  usb_device.vendor_id = 3141 (0xc45)
  usb_device.product_id = 25312 (0x62e0)
  usb_device.vendor = 'Microdia'
  info.subsystem = 'usb_device'
  usb_device.product = 'MSI Starcam Racer'
  info.product = 'MSI Starcam Racer'
  usb_device.max_power = 168 (0xa8)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_8087_24_noserial_0'
  usb_device.num_ports = 0 (0x0)
  usb_device.device_revision_bcd = 256 (0x100)
  usb_device.version = 2.00000
  usb_device.speed = 480.000
  usb_device.linux.device_number = 4 (0x4)
  usb_device.is_self_powered = false
  usb_device.can_wake_up = false
  usb_device.bus_number = 2 (0x2)
  linux.device_file = '/dev/bus/usb/002/004'
  info.vendor = 'Microdia'

  85: udi = '/org/freedesktop/Hal/devices/usb_device_3f0_9311_CN0BB3B48F05HX_if2'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.subsystem = 'usb'
  info.product = 'USB Vendor Specific Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_3f0_9311_CN0BB3B48F05HX_if2'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.2'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.num_interfaces = 3 (0x3)
  usb.device_class = 0 (0x0)
  usb.device_subclass = 0 (0x0)
  usb.device_protocol = 0 (0x0)
  usb.vendor_id = 1008 (0x3f0)
  usb.product_id = 37649 (0x9311)
  usb.vendor = 'Hewlett-Packard'
  usb.max_power = 2 (0x2)
  usb.product = 'USB Vendor Specific Interface'
  usb.num_ports = 0 (0x0)
  usb.serial = 'CN0BB3B48F05HX'
  usb.device_revision_bcd = 256 (0x100)
  usb.is_self_powered = true
  usb.speed = 480.000
  usb.linux.device_number = 3 (0x3)
  usb.can_wake_up = false
  usb.version = 2.00000
  usb.bus_number = 2 (0x2)
  usb.interface.number = 2 (0x2)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.2'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_3f0_9311_CN0BB3B48F05HX'
  usb.interface.subclass = 4 (0x4)
  usb.interface.class = 255 (0xff)
  usb.interface.protocol = 1 (0x1)

  86: udi = '/org/freedesktop/Hal/devices/usb_device_3f0_9311_CN0BB3B48F05HX_if1'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'usblp'
  info.subsystem = 'usb'
  info.product = 'USB Printer Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_3f0_9311_CN0BB3B48F05HX_if1'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.1'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.num_interfaces = 3 (0x3)
  usb.device_class = 0 (0x0)
  usb.device_subclass = 0 (0x0)
  usb.device_protocol = 0 (0x0)
  usb.vendor_id = 1008 (0x3f0)
  usb.product_id = 37649 (0x9311)
  usb.vendor = 'Hewlett-Packard'
  usb.max_power = 2 (0x2)
  usb.product = 'USB Printer Interface'
  usb.num_ports = 0 (0x0)
  usb.serial = 'CN0BB3B48F05HX'
  usb.device_revision_bcd = 256 (0x100)
  usb.is_self_powered = true
  usb.speed = 480.000
  usb.linux.device_number = 3 (0x3)
  usb.can_wake_up = false
  usb.version = 2.00000
  usb.bus_number = 2 (0x2)
  usb.interface.number = 1 (0x1)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.1'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_3f0_9311_CN0BB3B48F05HX'
  usb.interface.subclass = 1 (0x1)
  usb.interface.class = 7 (0x7)
  usb.interface.protocol = 2 (0x2)

  87: udi = '/org/freedesktop/Hal/devices/usb_device_3f0_9311_CN0BB3B48F05HX_if0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.subsystem = 'usb'
  info.product = 'USB Vendor Specific Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_3f0_9311_CN0BB3B48F05HX_if0'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.num_interfaces = 3 (0x3)
  usb.device_class = 0 (0x0)
  usb.device_subclass = 0 (0x0)
  usb.device_protocol = 0 (0x0)
  usb.vendor_id = 1008 (0x3f0)
  usb.product_id = 37649 (0x9311)
  usb.vendor = 'Hewlett-Packard'
  usb.max_power = 2 (0x2)
  usb.product = 'USB Vendor Specific Interface'
  usb.num_ports = 0 (0x0)
  usb.serial = 'CN0BB3B48F05HX'
  usb.device_revision_bcd = 256 (0x100)
  usb.is_self_powered = true
  usb.speed = 480.000
  usb.linux.device_number = 3 (0x3)
  usb.can_wake_up = false
  usb.version = 2.00000
  usb.bus_number = 2 (0x2)
  usb.interface.number = 0 (0x0)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_3f0_9311_CN0BB3B48F05HX'
  usb.interface.subclass = 204 (0xcc)
  usb.interface.class = 255 (0xff)
  usb.interface.protocol = 0 (0x0)

  88: udi = '/org/freedesktop/Hal/devices/usb_device_3f0_9311_CN0BB3B48F05HX'
  info.vendor = 'Hewlett-Packard'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'usb'
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5'
  usb_device.configuration_value = 1 (0x1)
  usb_device.num_configurations = 1 (0x1)
  usb_device.num_interfaces = 3 (0x3)
  usb_device.device_class = 0 (0x0)
  usb_device.device_subclass = 0 (0x0)
  usb_device.device_protocol = 0 (0x0)
  usb_device.vendor_id = 1008 (0x3f0)
  usb_device.product_id = 37649 (0x9311)
  usb_device.vendor = 'Hewlett-Packard'
  info.subsystem = 'usb_device'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_3f0_9311_CN0BB3B48F05HX'
  usb_device.max_power = 2 (0x2)
  usb_device.product = 'Deskjet 3050 J610 series'
  usb_device.num_ports = 0 (0x0)
  usb_device.serial = 'CN0BB3B48F05HX'
  info.product = 'Deskjet 3050 J610 series'
  usb_device.device_revision_bcd = 256 (0x100)
  usb_device.is_self_powered = true
  usb_device.speed = 480.000
  usb_device.linux.device_number = 3 (0x3)
  linux.device_file = '/dev/bus/usb/002/003'
  usb_device.can_wake_up = false
  usb_device.version = 2.00000
  usb_device.bus_number = 2 (0x2)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_8087_24_noserial_0'

  89: udi = '/org/freedesktop/Hal/devices/usb_device_8087_24_noserial_0'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_8087_24_noserial_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'usb'
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1'
  usb_device.configuration_value = 1 (0x1)
  usb_device.num_configurations = 1 (0x1)
  usb_device.num_interfaces = 1 (0x1)
  usb_device.device_class = 9 (0x9)
  usb_device.device_subclass = 0 (0x0)
  usb_device.device_protocol = 1 (0x1)
  usb_device.vendor_id = 32903 (0x8087)
  usb_device.product_id = 36 (0x24)
  info.subsystem = 'usb_device'
  info.product = 'Unknown (0x0024)'
  usb_device.device_revision_bcd = 0 (0x0)
  usb_device.max_power = 0 (0x0)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_0'
  usb_device.num_ports = 8 (0x8)
  usb_device.linux.device_number = 2 (0x2)
  usb_device.version = 2.00000
  usb_device.speed = 480.000
  usb_device.can_wake_up = true
  usb_device.is_self_powered = true
  linux.device_file = '/dev/bus/usb/002/002'
  usb_device.bus_number = 2 (0x2)
  info.vendor = 'Unknown (0x8087)'

  90: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_0_if0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'hub'
  info.subsystem = 'usb'
  info.product = 'USB Hub Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_0_if0'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.num_interfaces = 1 (0x1)
  usb.device_class = 9 (0x9)
  usb.device_subclass = 0 (0x0)
  usb.device_protocol = 0 (0x0)
  usb.vendor_id = 7531 (0x1d6b)
  usb.product_id = 2 (0x2)
  usb.vendor = 'Linux Foundation'
  usb.max_power = 0 (0x0)
  usb.product = 'USB Hub Interface'
  usb.num_ports = 2 (0x2)
  usb.serial = '0000:00:1d.0'
  usb.device_revision_bcd = 518 (0x206)
  usb.is_self_powered = true
  usb.speed = 480.000
  usb.linux.device_number = 1 (0x1)
  usb.can_wake_up = true
  usb.version = 2.00000
  usb.bus_number = 2 (0x2)
  usb.interface.number = 0 (0x0)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_0'
  usb.interface.subclass = 0 (0x0)
  usb.interface.class = 9 (0x9)
  usb.interface.protocol = 0 (0x0)

  91: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_0'
  info.vendor = 'Linux Foundation'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'usb'
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2'
  usb_device.configuration_value = 1 (0x1)
  usb_device.num_configurations = 1 (0x1)
  usb_device.num_interfaces = 1 (0x1)
  usb_device.device_class = 9 (0x9)
  usb_device.device_subclass = 0 (0x0)
  usb_device.device_protocol = 0 (0x0)
  usb_device.vendor_id = 7531 (0x1d6b)
  usb_device.product_id = 2 (0x2)
  usb_device.vendor = 'Linux Foundation'
  info.subsystem = 'usb_device'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_0'
  usb_device.max_power = 0 (0x0)
  usb_device.product = '2.0 root hub'
  usb_device.num_ports = 2 (0x2)
  usb_device.serial = '0000:00:1d.0'
  info.product = '2.0 root hub'
  usb_device.device_revision_bcd = 518 (0x206)
  usb_device.is_self_powered = true
  usb_device.speed = 480.000
  usb_device.linux.device_number = 1 (0x1)
  linux.device_file = '/dev/bus/usb/002/001'
  usb_device.can_wake_up = true
  usb_device.version = 2.00000
  usb_device.bus_number = 2 (0x2)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_1c26'

  92: udi = '/org/freedesktop/Hal/devices/pci_8086_1c26'
  pci.subsys_vendor = 'Micro-Star International Co., Ltd.'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.linux.driver = 'ehci_hcd'
  pci.product = 'Cougar Point USB Enhanced Host Controller #1'
  info.subsystem = 'pci'
  info.product = 'Cougar Point USB Enhanced Host Controller #1'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_1c26'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0'
  pci.product_id = 7206 (0x1c26)
  pci.vendor_id = 32902 (0x8086)
  pci.subsys_product_id = 30323 (0x7673)
  pci.subsys_vendor_id = 5218 (0x1462)
  pci.device_class = 12 (0xc)
  pci.device_subclass = 3 (0x3)
  pci.device_protocol = 32 (0x20)
  pci.vendor = 'Intel Corporation'
  info.vendor = 'Intel Corporation'

  93: udi = '/org/freedesktop/Hal/devices/pci_1106_3403'
  pci.subsys_vendor = 'Micro-Star International Co., Ltd.'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.linux.driver = 'ohci1394'
  info.subsystem = 'pci'
  info.product = 'Unknown (0x3403)'
  info.udi = '/org/freedesktop/Hal/devices/pci_1106_3403'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.7/0000:07:00.0'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_1c1e'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.7/0000:07:00.0'
  pci.product_id = 13315 (0x3403)
  pci.vendor_id = 4358 (0x1106)
  pci.subsys_product_id = 26429 (0x673d)
  pci.subsys_vendor_id = 5218 (0x1462)
  pci.device_class = 12 (0xc)
  pci.device_subclass = 0 (0x0)
  pci.device_protocol = 16 (0x10)
  pci.vendor = 'VIA Technologies, Inc.'
  info.vendor = 'VIA Technologies, Inc.'

  94: udi = '/org/freedesktop/Hal/devices/pci_8086_1c1e'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.linux.driver = 'pcieport'
  pci.product = 'Cougar Point PCI Express Root Port 8'
  info.subsystem = 'pci'
  info.product = 'Cougar Point PCI Express Root Port 8'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_1c1e'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.7'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.7'
  pci.product_id = 7198 (0x1c1e)
  pci.vendor_id = 32902 (0x8086)
  pci.subsys_product_id = 0 (0x0)
  pci.subsys_vendor_id = 0 (0x0)
  pci.device_class = 6 (0x6)
  pci.device_subclass = 4 (0x4)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Intel Corporation'
  info.vendor = 'Intel Corporation'

  95: udi = '/org/freedesktop/Hal/devices/pci_8086_1c1c'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.linux.driver = 'pcieport'
  pci.product = 'Cougar Point PCI Express Root Port 7'
  info.subsystem = 'pci'
  info.product = 'Cougar Point PCI Express Root Port 7'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_1c1c'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.6'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.6'
  pci.product_id = 7196 (0x1c1c)
  pci.vendor_id = 32902 (0x8086)
  pci.subsys_product_id = 0 (0x0)
  pci.subsys_vendor_id = 0 (0x0)
  pci.device_class = 6 (0x6)
  pci.device_subclass = 4 (0x4)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Intel Corporation'
  info.vendor = 'Intel Corporation'

  96: udi = '/org/freedesktop/Hal/devices/pci_10ec_8139'
  pci.subsys_vendor = 'Realtek Semiconductor Co., Ltd.'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.linux.driver = '8139too'
  pci.product = 'RTL-8139/8139C/8139C+'
  info.subsystem = 'pci'
  info.product = 'RTL-8139/8139C/8139C+'
  info.udi = '/org/freedesktop/Hal/devices/pci_10ec_8139'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/0000:05:01.0'
  info.parent = '/org/freedesktop/Hal/devices/pci_1b21_1080'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/0000:05:01.0'
  pci.product_id = 33081 (0x8139)
  pci.vendor_id = 4332 (0x10ec)
  pci.subsys_product_id = 33081 (0x8139)
  pci.subsys_vendor_id = 4332 (0x10ec)
  pci.device_class = 2 (0x2)
  pci.device_subclass = 0 (0x0)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Realtek Semiconductor Co., Ltd.'
  info.vendor = 'Realtek Semiconductor Co., Ltd.'

  97: udi = '/org/freedesktop/Hal/devices/pci_1b21_1080'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.subsystem = 'pci'
  info.product = 'Unknown (0x1080)'
  info.udi = '/org/freedesktop/Hal/devices/pci_1b21_1080'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_244e'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0'
  pci.product_id = 4224 (0x1080)
  pci.vendor_id = 6945 (0x1b21)
  pci.subsys_product_id = 0 (0x0)
  pci.subsys_vendor_id = 0 (0x0)
  pci.device_class = 6 (0x6)
  pci.device_subclass = 4 (0x4)
  pci.device_protocol = 0 (0x0)
  info.vendor = 'Unknown (0x1b21)'

  98: udi = '/org/freedesktop/Hal/devices/pci_8086_244e'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  pci.product = '82801 PCI Bridge'
  info.subsystem = 'pci'
  info.product = '82801 PCI Bridge'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_244e'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.4'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.4'
  pci.product_id = 9294 (0x244e)
  pci.vendor_id = 32902 (0x8086)
  pci.subsys_product_id = 0 (0x0)
  pci.subsys_vendor_id = 0 (0x0)
  pci.device_class = 6 (0x6)
  pci.device_subclass = 4 (0x4)
  pci.device_protocol = 1 (0x1)
  pci.vendor = 'Intel Corporation'
  info.vendor = 'Intel Corporation'

  99: udi = '/org/freedesktop/Hal/devices/pci_8086_1c10'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.linux.driver = 'pcieport'
  pci.product = 'Cougar Point PCI Express Root Port 1'
  info.subsystem = 'pci'
  info.product = 'Cougar Point PCI Express Root Port 1'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_1c10'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.0'
  pci.product_id = 7184 (0x1c10)
  pci.vendor_id = 32902 (0x8086)
  pci.subsys_product_id = 0 (0x0)
  pci.subsys_vendor_id = 0 (0x0)
  pci.device_class = 6 (0x6)
  pci.device_subclass = 4 (0x4)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Intel Corporation'
  info.vendor = 'Intel Corporation'

  100: udi = '/org/freedesktop/Hal/devices/pci_8086_1c20'
  pci.subsys_vendor = 'Micro-Star International Co., Ltd.'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.linux.driver = 'HDA Intel'
  pci.product = 'Cougar Point High Definition Audio Controller'
  info.subsystem = 'pci'
  info.product = 'Cougar Point High Definition Audio Controller'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_1c20'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0'
  pci.product_id = 7200 (0x1c20)
  pci.vendor_id = 32902 (0x8086)
  pci.subsys_product_id = 30323 (0x7673)
  pci.subsys_vendor_id = 5218 (0x1462)
  pci.device_class = 4 (0x4)
  pci.device_subclass = 3 (0x3)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Intel Corporation'
  info.vendor = 'Intel Corporation'

  101: udi = '/org/freedesktop/Hal/devices/usb_device_8087_24_noserial_if0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'hub'
  info.subsystem = 'usb'
  info.product = 'USB Hub Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_8087_24_noserial_if0'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1:1.0'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.num_interfaces = 1 (0x1)
  usb.device_class = 9 (0x9)
  usb.device_subclass = 0 (0x0)
  usb.device_protocol = 1 (0x1)
  usb.vendor_id = 32903 (0x8087)
  usb.product_id = 36 (0x24)
  usb.max_power = 0 (0x0)
  usb.product = 'USB Hub Interface'
  usb.num_ports = 6 (0x6)
  usb.device_revision_bcd = 0 (0x0)
  usb.is_self_powered = true
  usb.speed = 480.000
  usb.linux.device_number = 2 (0x2)
  usb.can_wake_up = true
  usb.version = 2.00000
  usb.bus_number = 1 (0x1)
  usb.interface.number = 0 (0x0)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1:1.0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_8087_24_noserial'
  usb.interface.subclass = 0 (0x0)
  usb.interface.class = 9 (0x9)
  usb.interface.protocol = 0 (0x0)

  102: udi = '/org/freedesktop/Hal/devices/usb_device_4b4_121f_noserial_if0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'usbhid'
  info.subsystem = 'usb'
  info.product = 'USB HID Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_4b4_121f_noserial_if0'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.num_interfaces = 1 (0x1)
  usb.device_class = 0 (0x0)
  usb.device_subclass = 0 (0x0)
  usb.device_protocol = 0 (0x0)
  usb.vendor_id = 1204 (0x4b4)
  usb.product_id = 4639 (0x121f)
  usb.vendor = 'Cypress Semiconductor Corp.'
  usb.max_power = 50 (0x32)
  usb.product = 'USB HID Interface'
  usb.num_ports = 0 (0x0)
  usb.device_revision_bcd = 256 (0x100)
  usb.is_self_powered = false
  usb.speed = 12.0000
  usb.linux.device_number = 4 (0x4)
  usb.can_wake_up = true
  usb.version = 2.00000
  usb.bus_number = 1 (0x1)
  usb.interface.number = 0 (0x0)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_4b4_121f_noserial'
  usb.interface.subclass = 1 (0x1)
  usb.interface.class = 3 (0x3)
  usb.interface.protocol = 2 (0x2)

  103: udi = '/org/freedesktop/Hal/devices/usb_device_4b4_121f_noserial'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_4b4_121f_noserial'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'usb'
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6'
  usb_device.configuration_value = 1 (0x1)
  usb_device.num_configurations = 1 (0x1)
  usb_device.num_interfaces = 1 (0x1)
  usb_device.device_class = 0 (0x0)
  usb_device.device_subclass = 0 (0x0)
  usb_device.device_protocol = 0 (0x0)
  usb_device.vendor_id = 1204 (0x4b4)
  usb_device.product_id = 4639 (0x121f)
  usb_device.vendor = 'Cypress Semiconductor Corp.'
  info.subsystem = 'usb_device'
  usb_device.product = 'Ikari Laser'
  info.product = 'Ikari Laser'
  usb_device.max_power = 50 (0x32)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_8087_24_noserial'
  usb_device.num_ports = 0 (0x0)
  usb_device.device_revision_bcd = 256 (0x100)
  usb_device.version = 2.00000
  usb_device.speed = 12.0000
  usb_device.linux.device_number = 4 (0x4)
  usb_device.is_self_powered = false
  usb_device.can_wake_up = true
  usb_device.bus_number = 1 (0x1)
  linux.device_file = '/dev/bus/usb/001/004'
  info.vendor = 'Cypress Semiconductor Corp.'

  104: udi = '/org/freedesktop/Hal/devices/usb_device_5e3_607_noserial_if0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'hub'
  info.subsystem = 'usb'
  info.product = 'USB Hub Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_5e3_607_noserial_if0'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.num_interfaces = 1 (0x1)
  usb.device_class = 9 (0x9)
  usb.device_subclass = 0 (0x0)
  usb.device_protocol = 2 (0x2)
  usb.vendor_id = 1507 (0x5e3)
  usb.product_id = 1543 (0x607)
  usb.vendor = 'Genesys Logic, Inc.'
  usb.max_power = 500 (0x1f4)
  usb.product = 'USB Hub Interface'
  usb.num_ports = 4 (0x4)
  usb.device_revision_bcd = 2049 (0x801)
  usb.is_self_powered = true
  usb.speed = 480.000
  usb.linux.device_number = 3 (0x3)
  usb.can_wake_up = true
  usb.version = 2.00000
  usb.bus_number = 1 (0x1)
  usb.interface.number = 0 (0x0)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_5e3_607_noserial'
  usb.interface.subclass = 0 (0x0)
  usb.interface.class = 9 (0x9)
  usb.interface.protocol = 2 (0x2)

  105: udi = '/org/freedesktop/Hal/devices/usb_device_46d_c22a_noserial_if1'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'usbhid'
  info.subsystem = 'usb'
  info.product = 'USB HID Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c22a_noserial_if1'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.1'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.num_interfaces = 2 (0x2)
  usb.device_class = 0 (0x0)
  usb.device_subclass = 0 (0x0)
  usb.device_protocol = 0 (0x0)
  usb.vendor_id = 1133 (0x46d)
  usb.product_id = 49706 (0xc22a)
  usb.vendor = 'Logitech, Inc.'
  usb.max_power = 100 (0x64)
  usb.product = 'USB HID Interface'
  usb.num_ports = 0 (0x0)
  usb.device_revision_bcd = 256 (0x100)
  usb.is_self_powered = false
  usb.speed = 1.50000
  usb.linux.device_number = 6 (0x6)
  usb.can_wake_up = true
  usb.version = 2.00000
  usb.bus_number = 1 (0x1)
  usb.interface.number = 1 (0x1)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.1'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_46d_c22a_noserial'
  usb.interface.subclass = 0 (0x0)
  usb.interface.class = 3 (0x3)
  usb.interface.protocol = 0 (0x0)

  106: udi = '/org/freedesktop/Hal/devices/usb_device_46d_c22a_noserial_if0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'usbhid'
  info.subsystem = 'usb'
  info.product = 'USB HID Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c22a_noserial_if0'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.0'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.num_interfaces = 2 (0x2)
  usb.device_class = 0 (0x0)
  usb.device_subclass = 0 (0x0)
  usb.device_protocol = 0 (0x0)
  usb.vendor_id = 1133 (0x46d)
  usb.product_id = 49706 (0xc22a)
  usb.vendor = 'Logitech, Inc.'
  usb.max_power = 100 (0x64)
  usb.product = 'USB HID Interface'
  usb.num_ports = 0 (0x0)
  usb.device_revision_bcd = 256 (0x100)
  usb.is_self_powered = false
  usb.speed = 1.50000
  usb.linux.device_number = 6 (0x6)
  usb.can_wake_up = true
  usb.version = 2.00000
  usb.bus_number = 1 (0x1)
  usb.interface.number = 0 (0x0)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_46d_c22a_noserial'
  usb.interface.subclass = 1 (0x1)
  usb.interface.class = 3 (0x3)
  usb.interface.protocol = 1 (0x1)

  107: udi = '/org/freedesktop/Hal/devices/usb_device_46d_c22a_noserial'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c22a_noserial'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'usb'
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3'
  usb_device.configuration_value = 1 (0x1)
  usb_device.num_configurations = 1 (0x1)
  usb_device.num_interfaces = 2 (0x2)
  usb_device.device_class = 0 (0x0)
  usb_device.device_subclass = 0 (0x0)
  usb_device.device_protocol = 0 (0x0)
  usb_device.vendor_id = 1133 (0x46d)
  usb_device.product_id = 49706 (0xc22a)
  usb_device.vendor = 'Logitech, Inc.'
  info.subsystem = 'usb_device'
  usb_device.product = 'Gaming Keyboard G110'
  info.product = 'Gaming Keyboard G110'
  usb_device.max_power = 100 (0x64)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_5e3_607_noserial'
  usb_device.num_ports = 0 (0x0)
  usb_device.device_revision_bcd = 256 (0x100)
  usb_device.version = 2.00000
  usb_device.speed = 1.50000
  usb_device.linux.device_number = 6 (0x6)
  usb_device.is_self_powered = false
  usb_device.can_wake_up = true
  usb_device.bus_number = 1 (0x1)
  linux.device_file = '/dev/bus/usb/001/006'
  info.vendor = 'Logitech, Inc.'

  108: udi = '/org/freedesktop/Hal/devices/usb_device_46d_c22b_noserial_if1'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.subsystem = 'usb'
  info.product = 'USB HID Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c22b_noserial_if1'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.1'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.num_interfaces = 2 (0x2)
  usb.device_class = 0 (0x0)
  usb.device_subclass = 0 (0x0)
  usb.device_protocol = 0 (0x0)
  usb.vendor_id = 1133 (0x46d)
  usb.product_id = 49707 (0xc22b)
  usb.vendor = 'Logitech, Inc.'
  usb.max_power = 100 (0x64)
  usb.product = 'USB HID Interface'
  usb.num_ports = 0 (0x0)
  usb.device_revision_bcd = 256 (0x100)
  usb.is_self_powered = false
  usb.speed = 1.50000
  usb.linux.device_number = 5 (0x5)
  usb.can_wake_up = false
  usb.version = 2.00000
  usb.bus_number = 1 (0x1)
  usb.interface.number = 1 (0x1)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.1'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_46d_c22b_noserial'
  usb.interface.subclass = 0 (0x0)
  usb.interface.class = 3 (0x3)
  usb.interface.protocol = 0 (0x0)

  109: udi = '/org/freedesktop/Hal/devices/usb_device_46d_c22b_noserial_if0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'usbhid'
  info.subsystem = 'usb'
  info.product = 'USB HID Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c22b_noserial_if0'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.0'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.num_interfaces = 2 (0x2)
  usb.device_class = 0 (0x0)
  usb.device_subclass = 0 (0x0)
  usb.device_protocol = 0 (0x0)
  usb.vendor_id = 1133 (0x46d)
  usb.product_id = 49707 (0xc22b)
  usb.vendor = 'Logitech, Inc.'
  usb.max_power = 100 (0x64)
  usb.product = 'USB HID Interface'
  usb.num_ports = 0 (0x0)
  usb.device_revision_bcd = 256 (0x100)
  usb.is_self_powered = false
  usb.speed = 1.50000
  usb.linux.device_number = 5 (0x5)
  usb.can_wake_up = false
  usb.version = 2.00000
  usb.bus_number = 1 (0x1)
  usb.interface.number = 0 (0x0)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_46d_c22b_noserial'
  usb.interface.subclass = 1 (0x1)
  usb.interface.class = 3 (0x3)
  usb.interface.protocol = 1 (0x1)

  110: udi = '/org/freedesktop/Hal/devices/usb_device_46d_c22b_noserial'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c22b_noserial'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'usb'
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1'
  usb_device.configuration_value = 1 (0x1)
  usb_device.num_configurations = 1 (0x1)
  usb_device.num_interfaces = 2 (0x2)
  usb_device.device_class = 0 (0x0)
  usb_device.device_subclass = 0 (0x0)
  usb_device.device_protocol = 0 (0x0)
  usb_device.vendor_id = 1133 (0x46d)
  usb_device.product_id = 49707 (0xc22b)
  usb_device.vendor = 'Logitech, Inc.'
  info.subsystem = 'usb_device'
  usb_device.product = 'G110 G-keys'
  info.product = 'G110 G-keys'
  usb_device.max_power = 100 (0x64)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_5e3_607_noserial'
  usb_device.num_ports = 0 (0x0)
  usb_device.device_revision_bcd = 256 (0x100)
  usb_device.version = 2.00000
  usb_device.speed = 1.50000
  usb_device.linux.device_number = 5 (0x5)
  usb_device.is_self_powered = false
  usb_device.can_wake_up = false
  usb_device.bus_number = 1 (0x1)
  linux.device_file = '/dev/bus/usb/001/005'
  info.vendor = 'Logitech, Inc.'

  111: udi = '/org/freedesktop/Hal/devices/usb_device_5e3_607_noserial'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_5e3_607_noserial'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'usb'
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3'
  usb_device.configuration_value = 1 (0x1)
  usb_device.num_configurations = 1 (0x1)
  usb_device.num_interfaces = 1 (0x1)
  usb_device.device_class = 9 (0x9)
  usb_device.device_subclass = 0 (0x0)
  usb_device.device_protocol = 2 (0x2)
  usb_device.vendor_id = 1507 (0x5e3)
  usb_device.product_id = 1543 (0x607)
  usb_device.vendor = 'Genesys Logic, Inc.'
  info.subsystem = 'usb_device'
  usb_device.product = 'USB2.0 Hub'
  info.product = 'USB2.0 Hub'
  usb_device.max_power = 500 (0x1f4)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_8087_24_noserial'
  usb_device.num_ports = 4 (0x4)
  usb_device.device_revision_bcd = 2049 (0x801)
  usb_device.version = 2.00000
  usb_device.speed = 480.000
  usb_device.linux.device_number = 3 (0x3)
  usb_device.is_self_powered = true
  usb_device.can_wake_up = true
  usb_device.bus_number = 1 (0x1)
  linux.device_file = '/dev/bus/usb/001/003'
  info.vendor = 'Genesys Logic, Inc.'

  112: udi = '/org/freedesktop/Hal/devices/usb_device_8087_24_noserial'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_8087_24_noserial'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'usb'
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1'
  usb_device.configuration_value = 1 (0x1)
  usb_device.num_configurations = 1 (0x1)
  usb_device.num_interfaces = 1 (0x1)
  usb_device.device_class = 9 (0x9)
  usb_device.device_subclass = 0 (0x0)
  usb_device.device_protocol = 1 (0x1)
  usb_device.vendor_id = 32903 (0x8087)
  usb_device.product_id = 36 (0x24)
  info.subsystem = 'usb_device'
  info.product = 'Unknown (0x0024)'
  usb_device.device_revision_bcd = 0 (0x0)
  usb_device.max_power = 0 (0x0)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1a_0'
  usb_device.num_ports = 6 (0x6)
  usb_device.linux.device_number = 2 (0x2)
  usb_device.version = 2.00000
  usb_device.speed = 480.000
  usb_device.can_wake_up = true
  usb_device.is_self_powered = true
  linux.device_file = '/dev/bus/usb/001/002'
  usb_device.bus_number = 1 (0x1)
  info.vendor = 'Unknown (0x8087)'

  113: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1a_0_if0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'hub'
  info.subsystem = 'usb'
  info.product = 'USB Hub Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1a_0_if0'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-0:1.0'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.num_interfaces = 1 (0x1)
  usb.device_class = 9 (0x9)
  usb.device_subclass = 0 (0x0)
  usb.device_protocol = 0 (0x0)
  usb.vendor_id = 7531 (0x1d6b)
  usb.product_id = 2 (0x2)
  usb.vendor = 'Linux Foundation'
  usb.max_power = 0 (0x0)
  usb.product = 'USB Hub Interface'
  usb.num_ports = 2 (0x2)
  usb.serial = '0000:00:1a.0'
  usb.device_revision_bcd = 518 (0x206)
  usb.is_self_powered = true
  usb.speed = 480.000
  usb.linux.device_number = 1 (0x1)
  usb.can_wake_up = true
  usb.version = 2.00000
  usb.bus_number = 1 (0x1)
  usb.interface.number = 0 (0x0)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-0:1.0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1a_0'
  usb.interface.subclass = 0 (0x0)
  usb.interface.class = 9 (0x9)
  usb.interface.protocol = 0 (0x0)

  114: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1a_0'
  info.vendor = 'Linux Foundation'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'usb'
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1'
  usb_device.configuration_value = 1 (0x1)
  usb_device.num_configurations = 1 (0x1)
  usb_device.num_interfaces = 1 (0x1)
  usb_device.device_class = 9 (0x9)
  usb_device.device_subclass = 0 (0x0)
  usb_device.device_protocol = 0 (0x0)
  usb_device.vendor_id = 7531 (0x1d6b)
  usb_device.product_id = 2 (0x2)
  usb_device.vendor = 'Linux Foundation'
  info.subsystem = 'usb_device'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1a_0'
  usb_device.max_power = 0 (0x0)
  usb_device.product = '2.0 root hub'
  usb_device.num_ports = 2 (0x2)
  usb_device.serial = '0000:00:1a.0'
  info.product = '2.0 root hub'
  usb_device.device_revision_bcd = 518 (0x206)
  usb_device.is_self_powered = true
  usb_device.speed = 480.000
  usb_device.linux.device_number = 1 (0x1)
  linux.device_file = '/dev/bus/usb/001/001'
  usb_device.can_wake_up = true
  usb_device.version = 2.00000
  usb_device.bus_number = 1 (0x1)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_1c2d'

  115: udi = '/org/freedesktop/Hal/devices/pci_8086_1c2d'
  pci.subsys_vendor = 'Micro-Star International Co., Ltd.'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.linux.driver = 'ehci_hcd'
  pci.product = 'Cougar Point USB Enhanced Host Controller #2'
  info.subsystem = 'pci'
  info.product = 'Cougar Point USB Enhanced Host Controller #2'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_1c2d'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0'
  pci.product_id = 7213 (0x1c2d)
  pci.vendor_id = 32902 (0x8086)
  pci.subsys_product_id = 30323 (0x7673)
  pci.subsys_vendor_id = 5218 (0x1462)
  pci.device_class = 12 (0xc)
  pci.device_subclass = 3 (0x3)
  pci.device_protocol = 32 (0x20)
  pci.vendor = 'Intel Corporation'
  info.vendor = 'Intel Corporation'

  116: udi = '/org/freedesktop/Hal/devices/pci_8086_1c3a'
  pci.subsys_vendor = 'Micro-Star International Co., Ltd.'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  pci.product = 'Cougar Point HECI Controller #1'
  info.subsystem = 'pci'
  info.product = 'Cougar Point HECI Controller #1'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_1c3a'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:16.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:16.0'
  pci.product_id = 7226 (0x1c3a)
  pci.vendor_id = 32902 (0x8086)
  pci.subsys_product_id = 30323 (0x7673)
  pci.subsys_vendor_id = 5218 (0x1462)
  pci.device_class = 7 (0x7)
  pci.device_subclass = 128 (0x80)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Intel Corporation'
  info.vendor = 'Intel Corporation'

  117: udi = '/org/freedesktop/Hal/devices/pci_10de_e0c'
  pci.subsys_vendor = 'Micro-Star International Co., Ltd.'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.subsystem = 'pci'
  info.product = 'Unknown (0x0e0c)'
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_e0c'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.1/0000:02:00.1'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_105'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.1/0000:02:00.1'
  pci.product_id = 3596 (0xe0c)
  pci.vendor_id = 4318 (0x10de)
  pci.subsys_product_id = 9090 (0x2382)
  pci.subsys_vendor_id = 5218 (0x1462)
  pci.device_class = 4 (0x4)
  pci.device_subclass = 3 (0x3)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'nVidia Corporation'
  info.vendor = 'nVidia Corporation'

  118: udi = '/org/freedesktop/Hal/devices/pci_10de_1200'
  pci.subsys_vendor = 'Micro-Star International Co., Ltd.'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.linux.driver = 'nvidia'
  info.subsystem = 'pci'
  info.product = 'Unknown (0x1200)'
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_1200'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.1/0000:02:00.0'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_105'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.1/0000:02:00.0'
  pci.product_id = 4608 (0x1200)
  pci.vendor_id = 4318 (0x10de)
  pci.subsys_product_id = 9090 (0x2382)
  pci.subsys_vendor_id = 5218 (0x1462)
  pci.device_class = 3 (0x3)
  pci.device_subclass = 0 (0x0)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'nVidia Corporation'
  info.vendor = 'nVidia Corporation'

  119: udi = '/org/freedesktop/Hal/devices/pci_8086_105'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.linux.driver = 'pcieport'
  pci.product = 'Sandy Bridge PCI Express Root Port'
  info.subsystem = 'pci'
  info.product = 'Sandy Bridge PCI Express Root Port'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_105'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.1'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.1'
  pci.product_id = 261 (0x105)
  pci.vendor_id = 32902 (0x8086)
  pci.subsys_product_id = 0 (0x0)
  pci.subsys_vendor_id = 0 (0x0)
  pci.device_class = 6 (0x6)
  pci.device_subclass = 4 (0x4)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Intel Corporation'
  info.vendor = 'Intel Corporation'

  120: udi = '/org/freedesktop/Hal/devices/pci_8086_101'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.linux.driver = 'pcieport'
  pci.product = 'Sandy Bridge PCI Express Root Port'
  info.subsystem = 'pci'
  info.product = 'Sandy Bridge PCI Express Root Port'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_101'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0'
  pci.product_id = 257 (0x101)
  pci.vendor_id = 32902 (0x8086)
  pci.subsys_product_id = 0 (0x0)
  pci.subsys_vendor_id = 0 (0x0)
  pci.device_class = 6 (0x6)
  pci.device_subclass = 4 (0x4)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Intel Corporation'
  info.vendor = 'Intel Corporation'

  121: udi = '/org/freedesktop/Hal/devices/pci_8086_100'
  pci.subsys_vendor = 'Micro-Star International Co., Ltd.'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.subsystem = 'pci'
  info.product = 'Unknown (0x0100)'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_100'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:00.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:00.0'
  pci.product_id = 256 (0x100)
  pci.vendor_id = 32902 (0x8086)
  pci.subsys_product_id = 30337 (0x7681)
  pci.subsys_vendor_id = 5218 (0x1462)
  pci.device_class = 6 (0x6)
  pci.device_subclass = 0 (0x0)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Intel Corporation'
  info.vendor = 'Intel Corporation'
----- hal device list end -----
>> floppy.1: get nvram
>> floppy.2: klog info
>> bios.1: cmdline
>> bios.1.1: apm
>> bios.2: ram
  bios: 0 disks
>> bios.2: rom
>> bios.3: smp
----- BIOS data 0x00400 - 0x004ff -----
  400  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  410  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  420  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  430  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  440  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  450  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  460  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  470  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  480  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  490  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  4a0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  4b0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  4c0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  4d0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  4e0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  4f0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
----- BIOS data end -----
>> bios.4: vbe
VBE: Could not init Int10
>> bios.5: 32
>> bios.6: acpi
>> sys.1: cpu
  vm check: vm_1 = 0, vm_2 = -1
  is_vmware = 0, has_vmware_mouse = 0
>> misc.9: kernel log
----- kernel log -----
  <6>[ 7967.018941] FIREWALL: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:f2:97:65:ad:08:00 SRC=192.168.0.3 DST=192.168.0.255 LEN=147 TOS=0x00 PREC=0x00 TTL=64 ID=51293 PROTO=UDP SPT=17500 DPT=17500 LEN=127 
  <6>[ 7997.015646] FIREWALL: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:f2:97:65:ad:08:00 SRC=192.168.0.3 DST=255.255.255.255 LEN=147 TOS=0x00 PREC=0x00 TTL=64 ID=37133 PROTO=UDP SPT=17500 DPT=17500 LEN=127 
  <4>[ 8012.913615] martian source 192.168.0.6 from 94.175.156.71, on dev eth0
  <4>[ 8012.913617] ll header: 00:16:0a:07:ad:dd:00:25:69:2e:0c:16:08:00
  <4>[ 8014.913701] martian source 192.168.0.6 from 94.175.156.71, on dev eth0
  <4>[ 8014.913705] ll header: 00:16:0a:07:ad:dd:00:25:69:2e:0c:16:08:00
  <4>[ 8019.013234] martian source 192.168.0.6 from 94.175.156.71, on dev eth0
  <4>[ 8019.013238] ll header: 00:16:0a:07:ad:dd:00:25:69:2e:0c:16:08:00
  <6>[ 8027.012348] FIREWALL: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:f2:97:65:ad:08:00 SRC=192.168.0.3 DST=255.255.255.255 LEN=147 TOS=0x00 PREC=0x00 TTL=64 ID=48984 PROTO=UDP SPT=17500 DPT=17500 LEN=127 
  <6>[ 8027.112058] FIREWALL: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:f2:97:65:ad:08:00 SRC=192.168.0.3 DST=192.168.0.255 LEN=147 TOS=0x00 PREC=0x00 TTL=64 ID=11391 PROTO=UDP SPT=17500 DPT=17500 LEN=127 
  <4>[ 8051.009707] martian source 192.168.0.6 from 62.31.11.177, on dev eth0
  <4>[ 8051.009709] ll header: 00:16:0a:07:ad:dd:00:25:69:2e:0c:16:08:00
  <3>[ 8051.308767] NVRM: Xid (0000:02:00): 13, 0001 00000000 00009097 00000ff8 ffff0000 00000004
  <3>[ 8051.508670] NVRM: Xid (0000:02:00): 13, 0001 00000000 00009097 00000ff8 fffd0000 00000004
  <3>[ 8052.809266] NVRM: Xid (0000:02:00): 13, 0001 00000000 00009097 00000ff8 ffff0000 00000004
  <3>[ 8053.009272] NVRM: Xid (0000:02:00): 13, 0001 00000000 00009097 00000ff8 fffd0000 00000004
  <6>[ 8057.108534] FIREWALL: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:f2:97:65:ad:08:00 SRC=192.168.0.3 DST=255.255.255.255 LEN=147 TOS=0x00 PREC=0x00 TTL=64 ID=3635 PROTO=UDP SPT=17500 DPT=17500 LEN=127 
  <4>[ 8059.008907] martian source 192.168.0.6 from 62.31.11.177, on dev eth0
  <4>[ 8059.008911] ll header: 00:16:0a:07:ad:dd:00:25:69:2e:0c:16:08:00
  <4>[ 8065.107964] martian source 192.168.0.6 from 212.248.196.64, on dev eth0
  <4>[ 8065.107968] ll header: 00:16:0a:07:ad:dd:00:25:69:2e:0c:16:08:00
  <4>[ 8068.207857] martian source 192.168.0.6 from 212.248.196.64, on dev eth0
  <4>[ 8068.207861] ll header: 00:16:0a:07:ad:dd:00:25:69:2e:0c:16:08:00
  <4>[ 8072.407143] martian source 192.168.0.6 from 212.248.196.64, on dev eth0
  <4>[ 8072.407145] ll header: 00:16:0a:07:ad:dd:00:25:69:2e:0c:16:08:00
  <6>[ 8087.105634] FIREWALL: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:f2:97:65:ad:08:00 SRC=192.168.0.3 DST=255.255.255.255 LEN=147 TOS=0x00 PREC=0x00 TTL=64 ID=25149 PROTO=UDP SPT=17500 DPT=17500 LEN=127 
  <6>[ 8087.105675] FIREWALL: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:f2:97:65:ad:08:00 SRC=192.168.0.3 DST=192.168.0.255 LEN=147 TOS=0x00 PREC=0x00 TTL=64 ID=61716 PROTO=UDP SPT=17500 DPT=17500 LEN=127 
  <4>[ 8115.202543] martian source 192.168.0.6 from 62.244.186.34, on dev eth0
  <4>[ 8115.202547] ll header: 00:16:0a:07:ad:dd:00:25:69:2e:0c:16:08:00
  <3>[ 8115.802384] NVRM: Xid (0000:02:00): 13, 0001 00000000 00009097 00000ff8 ffff0000 00000004
  <3>[ 8116.002379] NVRM: Xid (0000:02:00): 13, 0001 00000000 00009097 00000ff8 fffd0000 00000004
  <3>[ 8116.702429] NVRM: Xid (0000:02:00): 13, 0001 00000000 00009097 00000ff8 ffff0000 00000004
  <3>[ 8116.902393] NVRM: Xid (0000:02:00): 13, 0001 00000000 00009097 00000ff8 fffd0000 00000004
  <6>[ 8117.102336] FIREWALL: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:f2:97:65:ad:08:00 SRC=192.168.0.3 DST=255.255.255.255 LEN=147 TOS=0x00 PREC=0x00 TTL=64 ID=60254 PROTO=UDP SPT=17500 DPT=17500 LEN=127 
  <4>[ 8117.202306] martian source 192.168.0.6 from 62.244.186.34, on dev eth0
  <4>[ 8117.202309] ll header: 00:16:0a:07:ad:dd:00:25:69:2e:0c:16:08:00
  <4>[ 8123.000900] martian source 192.168.0.6 from 62.244.186.34, on dev eth0
  <4>[ 8123.000904] ll header: 00:16:0a:07:ad:dd:00:25:69:2e:0c:16:08:00
  <4>[ 8145.299440] martian source 192.168.0.6 from 94.175.156.71, on dev eth0
  <4>[ 8145.299442] ll header: 00:16:0a:07:ad:dd:00:25:69:2e:0c:16:08:00
  <6>[ 8147.099220] FIREWALL: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:f2:97:65:ad:08:00 SRC=192.168.0.3 DST=255.255.255.255 LEN=147 TOS=0x00 PREC=0x00 TTL=64 ID=47337 PROTO=UDP SPT=17500 DPT=17500 LEN=127 
  <6>[ 8147.099254] FIREWALL: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:f2:97:65:ad:08:00 SRC=192.168.0.3 DST=192.168.0.255 LEN=147 TOS=0x00 PREC=0x00 TTL=64 ID=60121 PROTO=UDP SPT=17500 DPT=17500 LEN=127 
  <4>[ 8147.299206] martian source 192.168.0.6 from 94.175.156.71, on dev eth0
  <4>[ 8147.299207] ll header: 00:16:0a:07:ad:dd:00:25:69:2e:0c:16:08:00
  <4>[ 8151.498632] martian source 192.168.0.6 from 94.175.156.71, on dev eth0
  <4>[ 8151.498636] ll header: 00:16:0a:07:ad:dd:00:25:69:2e:0c:16:08:00
  <6>[ 8176.095941] FIREWALL: IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:17:f2:97:65:ad:08:00 SRC=192.168.0.3 DST=224.0.0.251 LEN=160 TOS=0x00 PREC=0x00 TTL=255 ID=36749 PROTO=UDP SPT=5353 DPT=5353 LEN=140 
  <4>[ 8183.795253] martian source 192.168.0.6 from 86.12.58.80, on dev eth0
  <4>[ 8183.795257] ll header: 00:16:0a:07:ad:dd:00:25:69:2e:0c:16:08:00
  <4>[ 8191.794142] martian source 192.168.0.6 from 86.12.58.80, on dev eth0
  <4>[ 8191.794144] ll header: 00:16:0a:07:ad:dd:00:25:69:2e:0c:16:08:00
  <4>[ 8202.192972] martian source 192.168.0.6 from 82.34.39.34, on dev eth0
  <4>[ 8202.192974] ll header: 00:16:0a:07:ad:dd:00:25:69:2e:0c:16:08:00
  <4>[ 8204.193003] martian source 192.168.0.6 from 82.34.39.34, on dev eth0
  <4>[ 8204.193004] ll header: 00:16:0a:07:ad:dd:00:25:69:2e:0c:16:08:00
  <6>[ 8207.091724] FIREWALL: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:f2:97:65:ad:08:00 SRC=192.168.0.3 DST=255.255.255.255 LEN=147 TOS=0x00 PREC=0x00 TTL=64 ID=23281 PROTO=UDP SPT=17500 DPT=17500 LEN=127 
  <6>[ 8207.091766] FIREWALL: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:f2:97:65:ad:08:00 SRC=192.168.0.3 DST=192.168.0.255 LEN=147 TOS=0x00 PREC=0x00 TTL=64 ID=30665 PROTO=UDP SPT=17500 DPT=17500 LEN=127 
  <4>[ 8208.492313] martian source 192.168.0.6 from 82.34.39.34, on dev eth0
  <4>[ 8208.492317] ll header: 00:16:0a:07:ad:dd:00:25:69:2e:0c:16:08:00
  <4>[ 8219.891322] martian source 192.168.0.6 from 109.153.192.135, on dev eth0
  <4>[ 8219.891326] ll header: 00:16:0a:07:ad:dd:00:25:69:2e:0c:16:08:00
  <4>[ 8219.891362] martian source 192.168.0.6 from 109.153.192.135, on dev eth0
  <4>[ 8219.891364] ll header: 00:16:0a:07:ad:dd:00:25:69:2e:0c:16:08:00
  <4>[ 8221.990803] martian source 192.168.0.6 from 109.153.192.135, on dev eth0
  <4>[ 8221.990812] ll header: 00:16:0a:07:ad:dd:00:25:69:2e:0c:16:08:00
  <4>[ 8221.990836] martian source 192.168.0.6 from 109.153.192.135, on dev eth0
  <4>[ 8221.990837] ll header: 00:16:0a:07:ad:dd:00:25:69:2e:0c:16:08:00
  <4>[ 8226.090407] martian source 192.168.0.6 from 109.153.192.135, on dev eth0
  <4>[ 8226.090409] ll header: 00:16:0a:07:ad:dd:00:25:69:2e:0c:16:08:00
  <4>[ 8226.090434] martian source 192.168.0.6 from 109.153.192.135, on dev eth0
  <4>[ 8226.090435] ll header: 00:16:0a:07:ad:dd:00:25:69:2e:0c:16:08:00
  <6>[ 8237.089145] FIREWALL: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:f2:97:65:ad:08:00 SRC=192.168.0.3 DST=255.255.255.255 LEN=147 TOS=0x00 PREC=0x00 TTL=64 ID=31879 PROTO=UDP SPT=17500 DPT=17500 LEN=127 
  <6>[ 8267.086177] FIREWALL: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:f2:97:65:ad:08:00 SRC=192.168.0.3 DST=255.255.255.255 LEN=147 TOS=0x00 PREC=0x00 TTL=64 ID=24732 PROTO=UDP SPT=17500 DPT=17500 LEN=127 
  <6>[ 8267.086219] FIREWALL: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:17:f2:97:65:ad:08:00 SRC=192.168.0.3 DST=192.168.0.255 LEN=147 TOS=0x00 PREC=0x00 TTL=64 ID=39677 PROTO=UDP SPT=17500 DPT=17500 LEN=127 
  <4>[ 8282.383503] martian source 192.168.0.6 from 94.174.192.37, on dev eth0
  <4>[ 8282.383506] ll header: 00:16:0a:07:ad:dd:00:25:69:2e:0c:16:08:00
  <4>[ 8284.383830] martian source 192.168.0.6 from 94.174.192.37, on dev eth0
  <4>[ 8284.383834] ll header: 00:16:0a:07:ad:dd:00:25:69:2e:0c:16:08:00
----- kernel log end -----
>> misc.1: misc data
>> misc.1.1: open serial
>> misc.1.2: open parallel
----- exec: "/sbin/rmmod lp" -----
  ERROR: Removing 'lp': Operation not permitted
----- return code: ? -----
----- exec: "/sbin/rmmod parport" -----
  ERROR: Module parport is in use by ppdev,lp
----- return code: ? -----
----- exec: "/sbin/modprobe parport_pc " -----
  FATAL: Error inserting parport_pc (/lib/modules/2.6.32-38-generic-pae/kernel/drivers/parport/parport_pc.ko): Operation not permitted
----- return code: ? -----
>> misc.2.1: io
>> misc.2.2: dma
>> misc.2.3: irq
----- /proc/ioports -----
  0000-001f : dma1
  0020-0021 : pic1
  0040-0043 : timer0
  0050-0053 : timer1
  0060-0060 : keyboard
  0064-0064 : keyboard
  0070-0071 : rtc0
  0080-008f : dma page reg
  00a0-00a1 : pic2
  00c0-00df : dma2
  00f0-00ff : fpu
  0170-0177 : 0000:00:1f.2
    0170-0177 : ata_piix
  01f0-01f7 : 0000:00:1f.2
    01f0-01f7 : ata_piix
  0376-0376 : 0000:00:1f.2
    0376-0376 : ata_piix
  03c0-03df : vga+
  03f6-03f6 : 0000:00:1f.2
    03f6-03f6 : ata_piix
  03f8-03ff : serial
  0400-0453 : pnp 00:09
    0400-0403 : ACPI PM1a_EVT_BLK
    0404-0405 : ACPI PM1a_CNT_BLK
    0408-040b : ACPI PM_TMR
    0410-0415 : ACPI CPU throttle
    0420-042f : ACPI GPE0_BLK
    0450-0450 : ACPI PM2_CNT_BLK
  0454-0457 : pnp 00:0a
  0458-047f : pnp 00:09
  04d0-04d1 : pnp 00:07
  0500-057f : pnp 00:09
  0a00-0a0f : pnp 00:02
  0cf8-0cff : PCI conf1
  1180-119f : pnp 00:09
  c000-cfff : PCI Bus 0000:07
    c000-c0ff : 0000:07:00.0
  d000-dfff : PCI Bus 0000:04
    d000-dfff : PCI Bus 0000:05
      d000-d0ff : 0000:05:01.0
        d000-d0ff : 8139too
  e000-efff : PCI Bus 0000:02
    e000-e07f : 0000:02:00.0
  f000-f01f : 0000:00:1f.3
  f020-f02f : 0000:00:1f.5
    f020-f02f : ata_piix
  f030-f03f : 0000:00:1f.5
    f030-f03f : ata_piix
  f040-f043 : 0000:00:1f.5
    f040-f043 : ata_piix
  f050-f057 : 0000:00:1f.5
    f050-f057 : ata_piix
  f060-f063 : 0000:00:1f.5
    f060-f063 : ata_piix
  f070-f077 : 0000:00:1f.5
    f070-f077 : ata_piix
  f080-f08f : 0000:00:1f.2
    f080-f08f : ata_piix
  f090-f09f : 0000:00:1f.2
    f090-f09f : ata_piix
----- /proc/ioports end -----
----- /proc/interrupts -----
    0:         74          0          0          0   IO-APIC-edge      timer
    1:          2          0          0          0   IO-APIC-edge      i8042
    4:          7          0          0          0   IO-APIC-edge      serial
    8:          1          0          0          0   IO-APIC-edge      rtc0
    9:          0          0          0          0   IO-APIC-fasteoi   acpi
   12:          4          0          0          0   IO-APIC-edge      i8042
   14:     125729          0          0          0   IO-APIC-edge      ata_piix
   15:      77991          0          0          0   IO-APIC-edge      ata_piix
   16:        643          0     140120          0   IO-APIC-fasteoi   ehci_hcd:usb1
   17:     200036          0          0          0   IO-APIC-fasteoi   eth0, nvidia
   19:          2          0          0          0   IO-APIC-fasteoi   ata_piix, ohci1394
   22:        410          0          0        224   IO-APIC-fasteoi   HDA Intel
   23:       5228       5710          0          0   IO-APIC-fasteoi   ehci_hcd:usb2
  NMI:          0          0          0          0   Non-maskable interrupts
  LOC:    1783249    1650092    4009498    1335878   Local timer interrupts
  SPU:          0          0          0          0   Spurious interrupts
  PMI:          0          0          0          0   Performance monitoring interrupts
  PND:          0          0          0          0   Performance pending work
  RES:     871308     838758     188553      84340   Rescheduling interrupts
  CAL:        442       2494       2292       2444   Function call interrupts
  TLB:     354538     368739     354095     336337   TLB shootdowns
  TRM:          0          0          0          0   Thermal event interrupts
  THR:          0          0          0          0   Threshold APIC interrupts
  MCE:          0          0          0          0   Machine check exceptions
  MCP:         29         29         29         29   Machine check polls
  ERR:          0
  MIS:          0
----- /proc/interrupts end -----
----- /proc/dma -----
   4: cascade
----- /proc/dma end -----
>> misc.3: FPU
>> misc.3.1: DMA
>> misc.3.2: PIC
>> misc.3.3: timer
>> misc.3.4: RTC
>> cpu.1: cpuinfo
----- /proc/cpuinfo -----
  processor	: 0
  vendor_id	: GenuineIntel
  cpu family	: 6
  model		: 42
  model name	: Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz
  stepping	: 7
  cpu MHz		: 1600.000
  cache size	: 6144 KB
  physical id	: 0
  siblings	: 4
  core id		: 0
  cpu cores	: 4
  apicid		: 0
  initial apicid	: 0
  fdiv_bug	: no
  hlt_bug		: no
  f00f_bug	: no
  coma_bug	: no
  fpu		: yes
  fpu_exception	: yes
  cpuid level	: 13
  wp		: yes
  flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt aes xsave avx lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid
  bogomips	: 6584.49
  clflush size	: 64
  cache_alignment	: 64
  address sizes	: 36 bits physical, 48 bits virtual
  power management:
  
  processor	: 1
  vendor_id	: GenuineIntel
  cpu family	: 6
  model		: 42
  model name	: Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz
  stepping	: 7
  cpu MHz		: 1600.000
  cache size	: 6144 KB
  physical id	: 0
  siblings	: 4
  core id		: 1
  cpu cores	: 4
  apicid		: 2
  initial apicid	: 2
  fdiv_bug	: no
  hlt_bug		: no
  f00f_bug	: no
  coma_bug	: no
  fpu		: yes
  fpu_exception	: yes
  cpuid level	: 13
  wp		: yes
  flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt aes xsave avx lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid
  bogomips	: 6584.98
  clflush size	: 64
  cache_alignment	: 64
  address sizes	: 36 bits physical, 48 bits virtual
  power management:
  
  processor	: 2
  vendor_id	: GenuineIntel
  cpu family	: 6
  model		: 42
  model name	: Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz
  stepping	: 7
  cpu MHz		: 1600.000
  cache size	: 6144 KB
  physical id	: 0
  siblings	: 4
  core id		: 2
  cpu cores	: 4
  apicid		: 4
  initial apicid	: 4
  fdiv_bug	: no
  hlt_bug		: no
  f00f_bug	: no
  coma_bug	: no
  fpu		: yes
  fpu_exception	: yes
  cpuid level	: 13
  wp		: yes
  flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt aes xsave avx lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid
  bogomips	: 6585.00
  clflush size	: 64
  cache_alignment	: 64
  address sizes	: 36 bits physical, 48 bits virtual
  power management:
  
  processor	: 3
  vendor_id	: GenuineIntel
  cpu family	: 6
  model		: 42
  model name	: Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz
  stepping	: 7
  cpu MHz		: 1600.000
  cache size	: 6144 KB
  physical id	: 0
  siblings	: 4
  core id		: 3
  cpu cores	: 4
  apicid		: 6
  initial apicid	: 6
  fdiv_bug	: no
  hlt_bug		: no
  f00f_bug	: no
  coma_bug	: no
  fpu		: yes
  fpu_exception	: yes
  cpuid level	: 13
  wp		: yes
  flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt aes xsave avx lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid
  bogomips	: 6585.00
  clflush size	: 64
  cache_alignment	: 64
  address sizes	: 36 bits physical, 48 bits virtual
  power management:
  
----- /proc/cpuinfo end -----
>> memory.1: main memory size
  kcore mem:  0x3f9fe000
  klog mem 0: 0x0
  klog mem 1: 0x0
  klog mem:   0x0
  bios mem:   0x0
  meminfo:    0xfa4fb000
>> pci.1: sysfs drivers
----- sysfs driver list (id 0x8dccb6506972eaa2) -----
      serial8250: /devices/platform/serial8250
           i8042: /devices/platform/i8042
         vga16fb: /devices/platform/vga16fb.0
        pcieport: /devices/pci0000:00/0000:00:01.0
        pcieport: /devices/pci0000:00/0000:00:01.1
        pcieport: /devices/pci0000:00/0000:00:1c.0
        pcieport: /devices/pci0000:00/0000:00:1c.6
        pcieport: /devices/pci0000:00/0000:00:1c.7
        ata_piix: /devices/pci0000:00/0000:00:1f.2
        ata_piix: /devices/pci0000:00/0000:00:1f.5
        ehci_hcd: /devices/pci0000:00/0000:00:1a.0
        ehci_hcd: /devices/pci0000:00/0000:00:1d.0
        ehci_hcd: module = ehci_hcd
        uhci_hcd: module = uhci_hcd
          8139cp: module = 8139cp
        ohci1394: /devices/pci0000:00/0000:00:1c.7/0000:07:00.0
        ohci1394: module = ohci1394
         nouveau: module = drm
         8139too: /devices/pci0000:00/0000:00:1c.4/0000:04:00.0/0000:05:01.0
         8139too: module = 8139too
          shpchp: module = shpchp
          nvidia: /devices/pci0000:00/0000:00:01.1/0000:02:00.0
          nvidia: module = nvidia
       HDA Intel: /devices/pci0000:00/0000:00:1b.0
       HDA Intel: module = snd_hda_intel
        pci_root: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00
        pci_link: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0F:00
        pci_link: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0F:01
        pci_link: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0F:02
        pci_link: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0F:03
        pci_link: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0F:04
        pci_link: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0F:05
        pci_link: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0F:06
        pci_link: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0F:07
             wmi: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/pnp0c14:00
          button: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00
          button: /devices/LNXSYSTM:00/LNXPWRBN:00
       processor: /devices/LNXSYSTM:00/LNXCPU:00
       processor: /devices/LNXSYSTM:00/LNXCPU:01
       processor: /devices/LNXSYSTM:00/LNXCPU:02
       processor: /devices/LNXSYSTM:00/LNXCPU:03
          system: /devices/pnp0/00:01
          system: /devices/pnp0/00:02
          system: /devices/pnp0/00:07
          system: /devices/pnp0/00:09
          system: /devices/pnp0/00:0a
          serial: /devices/pnp0/00:03
        rtc_cmos: /devices/pnp0/00:05
              sd: /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0
              sr: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0
           usbfs: module = usbcore
             hub: module = usbcore
             hub: /devices/pci0000:00/0000:00:1a.0/usb1/1-0:1.0
             hub: /devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0
             hub: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1:1.0
             hub: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0
             hub: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0
             usb: /devices/pci0000:00/0000:00:1a.0/usb1
             usb: /devices/pci0000:00/0000:00:1d.0/usb2
             usb: /devices/pci0000:00/0000:00:1a.0/usb1/1-1
             usb: /devices/pci0000:00/0000:00:1d.0/usb2/2-1
             usb: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3
             usb: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6
             usb: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5
             usb: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6
             usb: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1
             usb: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3
          hiddev: module = usbhid
          usbhid: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0
          usbhid: module = usbhid
          usbhid: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.0
          usbhid: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.0
          usbhid: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.1
        uvcvideo: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0
        uvcvideo: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.1
        uvcvideo: module = uvcvideo
           usblp: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.1
           usblp: module = usblp
   snd-usb-audio: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2
   snd-usb-audio: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.3
   snd-usb-audio: module = snd_usb_audio
       serio_raw: module = serio_raw
         psmouse: module = psmouse
         nodemgr: module = ieee1394
         nodemgr: /devices/pci0000:00/0000:00:1c.7/0000:07:00.0/fw-host0
     generic-usb: module = usbhid
     generic-usb: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/0003:04B4:121F.0001
     generic-usb: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.0/0003:046D:C22B.0002
     generic-usb: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.0/0003:046D:C22A.0003
     generic-usb: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.1/0003:046D:C22A.0004
----- sysfs driver list end -----
>> pci.2: get sysfs pci data
  pci device: name = 0000:00:00.0
    path = /devices/pci0000:00/0000:00:00.0
    modalias = "pci:v00008086d00000100sv00001462sd00007681bc06sc00i00"
    class = 0x60000
    vendor = 0x8086
    device = 0x100
    subvendor = 0x1462
    subdevice = 0x7681
    irq = 0
    config[64]
  pci device: name = 0000:00:01.0
    path = /devices/pci0000:00/0000:00:01.0
    modalias = "pci:v00008086d00000101sv00000000sd00000000bc06sc04i00"
    class = 0x60400
    vendor = 0x8086
    device = 0x101
    subvendor = 0x0
    subdevice = 0x0
    irq = 24
    config[64]
  pci device: name = 0000:00:01.1
    path = /devices/pci0000:00/0000:00:01.1
    modalias = "pci:v00008086d00000105sv00000000sd00000000bc06sc04i00"
    class = 0x60400
    vendor = 0x8086
    device = 0x105
    subvendor = 0x0
    subdevice = 0x0
    irq = 25
    config[64]
  pci device: name = 0000:00:16.0
    path = /devices/pci0000:00/0000:00:16.0
    modalias = "pci:v00008086d00001C3Asv00001462sd00007673bc07sc80i00"
    class = 0x78000
    vendor = 0x8086
    device = 0x1c3a
    subvendor = 0x1462
    subdevice = 0x7673
    irq = 11
    res[0] = 0xfa307000 0xfa30700f 0x120204
    config[64]
  pci device: name = 0000:00:1a.0
    path = /devices/pci0000:00/0000:00:1a.0
    modalias = "pci:v00008086d00001C2Dsv00001462sd00007673bc0Csc03i20"
    class = 0xc0320
    vendor = 0x8086
    device = 0x1c2d
    subvendor = 0x1462
    subdevice = 0x7673
    irq = 16
    res[0] = 0xfa306000 0xfa3063ff 0x20200
    config[64]
  pci device: name = 0000:00:1b.0
    path = /devices/pci0000:00/0000:00:1b.0
    modalias = "pci:v00008086d00001C20sv00001462sd00007673bc04sc03i00"
    class = 0x40300
    vendor = 0x8086
    device = 0x1c20
    subvendor = 0x1462
    subdevice = 0x7673
    irq = 22
    res[0] = 0xfa300000 0xfa303fff 0x120204
    config[64]
  pci device: name = 0000:00:1c.0
    path = /devices/pci0000:00/0000:00:1c.0
    modalias = "pci:v00008086d00001C10sv00000000sd00000000bc06sc04i00"
    class = 0x60400
    vendor = 0x8086
    device = 0x1c10
    subvendor = 0x0
    subdevice = 0x0
    irq = 26
    config[64]
  pci device: name = 0000:00:1c.4
    path = /devices/pci0000:00/0000:00:1c.4
    modalias = "pci:v00008086d0000244Esv00000000sd00000000bc06sc04i01"
    class = 0x60401
    vendor = 0x8086
    device = 0x244e
    subvendor = 0x0
    subdevice = 0x0
    irq = 17
    config[64]
  pci device: name = 0000:00:1c.6
    path = /devices/pci0000:00/0000:00:1c.6
    modalias = "pci:v00008086d00001C1Csv00000000sd00000000bc06sc04i00"
    class = 0x60400
    vendor = 0x8086
    device = 0x1c1c
    subvendor = 0x0
    subdevice = 0x0
    irq = 27
    config[64]
  pci device: name = 0000:00:1c.7
    path = /devices/pci0000:00/0000:00:1c.7
    modalias = "pci:v00008086d00001C1Esv00000000sd00000000bc06sc04i00"
    class = 0x60400
    vendor = 0x8086
    device = 0x1c1e
    subvendor = 0x0
    subdevice = 0x0
    irq = 28
    config[64]
  pci device: name = 0000:00:1d.0
    path = /devices/pci0000:00/0000:00:1d.0
    modalias = "pci:v00008086d00001C26sv00001462sd00007673bc0Csc03i20"
    class = 0xc0320
    vendor = 0x8086
    device = 0x1c26
    subvendor = 0x1462
    subdevice = 0x7673
    irq = 23
    res[0] = 0xfa305000 0xfa3053ff 0x20200
    config[64]
  pci device: name = 0000:00:1f.0
    path = /devices/pci0000:00/0000:00:1f.0
    modalias = "pci:v00008086d00001C46sv00001462sd00007673bc06sc01i00"
    class = 0x60100
    vendor = 0x8086
    device = 0x1c46
    subvendor = 0x1462
    subdevice = 0x7673
    irq = 0
    config[64]
  pci device: name = 0000:00:1f.2
    path = /devices/pci0000:00/0000:00:1f.2
    modalias = "pci:v00008086d00001C00sv00001462sd00007673bc01sc01i8a"
    class = 0x1018a
    vendor = 0x8086
    device = 0x1c00
    subvendor = 0x1462
    subdevice = 0x7673
    irq = 19
    res[0] = 0x1f0 0x1f7 0x110
    res[1] = 0x3f6 0x3f6 0x110
    res[2] = 0x170 0x177 0x110
    res[3] = 0x376 0x376 0x110
    res[4] = 0xf090 0xf09f 0x20101
    res[5] = 0xf080 0xf08f 0x20101
    config[64]
  pci device: name = 0000:00:1f.3
    path = /devices/pci0000:00/0000:00:1f.3
    modalias = "pci:v00008086d00001C22sv00001462sd00007673bc0Csc05i00"
    class = 0xc0500
    vendor = 0x8086
    device = 0x1c22
    subvendor = 0x1462
    subdevice = 0x7673
    irq = 5
    res[0] = 0xfa304000 0xfa3040ff 0x120204
    res[4] = 0xf000 0xf01f 0x20101
    config[64]
  pci device: name = 0000:00:1f.5
    path = /devices/pci0000:00/0000:00:1f.5
    modalias = "pci:v00008086d00001C08sv00001462sd00007673bc01sc01i85"
    class = 0x10185
    vendor = 0x8086
    device = 0x1c08
    subvendor = 0x1462
    subdevice = 0x7673
    irq = 19
    res[0] = 0xf070 0xf077 0x20101
    res[1] = 0xf060 0xf063 0x20101
    res[2] = 0xf050 0xf057 0x20101
    res[3] = 0xf040 0xf043 0x20101
    res[4] = 0xf030 0xf03f 0x20101
    res[5] = 0xf020 0xf02f 0x20101
    config[64]
  pci device: name = 0000:02:00.0
    path = /devices/pci0000:00/0000:00:01.1/0000:02:00.0
    modalias = "pci:v000010DEd00001200sv00001462sd00002382bc03sc00i00"
    class = 0x30000
    vendor = 0x10de
    device = 0x1200
    subvendor = 0x1462
    subdevice = 0x2382
    irq = 17
    res[0] = 0xf8000000 0xf9ffffff 0x20200
    res[1] = 0xd0000000 0xd7ffffff 0x12120c
    res[3] = 0xd8000000 0xdbffffff 0x12120c
    res[5] = 0xe000 0xe07f 0x20101
    res[6] = 0xfa000000 0xfa07ffff 0x27202
    config[64]
  pci device: name = 0000:02:00.1
    path = /devices/pci0000:00/0000:00:01.1/0000:02:00.1
    modalias = "pci:v000010DEd00000E0Csv00001462sd00002382bc04sc03i00"
    class = 0x40300
    vendor = 0x10de
    device = 0xe0c
    subvendor = 0x1462
    subdevice = 0x2382
    irq = 5
    res[0] = 0xfa080000 0xfa083fff 0x20200
    config[64]
  pci device: name = 0000:04:00.0
    path = /devices/pci0000:00/0000:00:1c.4/0000:04:00.0
    modalias = "pci:v00001B21d00001080sv00000000sd00000000bc06sc04i00"
    class = 0x60400
    vendor = 0x1b21
    device = 0x1080
    subvendor = 0x0
    subdevice = 0x0
    irq = 16
    config[64]
  pci device: name = 0000:05:01.0
    path = /devices/pci0000:00/0000:00:1c.4/0000:04:00.0/0000:05:01.0
    modalias = "pci:v000010ECd00008139sv000010ECsd00008139bc02sc00i00"
    class = 0x20000
    vendor = 0x10ec
    device = 0x8139
    subvendor = 0x10ec
    subdevice = 0x8139
    irq = 17
    res[0] = 0xd000 0xd0ff 0x20101
    res[1] = 0xfa220000 0xfa2200ff 0x20200
    res[6] = 0xfa200000 0xfa21ffff 0x27200
    config[64]
  pci device: name = 0000:07:00.0
    path = /devices/pci0000:00/0000:00:1c.7/0000:07:00.0
    modalias = "pci:v00001106d00003403sv00001462sd0000673Dbc0Csc00i10"
    class = 0xc0010
    vendor = 0x1106
    device = 0x3403
    subvendor = 0x1462
    subdevice = 0x673d
    irq = 19
    res[0] = 0xfa100000 0xfa1007ff 0x120204
    res[2] = 0xc000 0xc0ff 0x20101
    config[64]
---------- PCI raw data ----------
bus 00, slot 00, func 0, vend:dev:s_vend:s_dev:rev 8086:0100:1462:7681:09
class 06, sub_class 00 prog_if 00, hdr 0, flags <>, irq 0
  00: 86 80 00 01 06 00 90 20 09 00 00 06 00 00 00 00  "....... ........"
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 62 14 81 76  "............b..v"
  30: 00 00 00 00 e0 00 00 00 00 00 00 00 00 00 00 00  "................"

bus 00->01, slot 01, func 0, vend:dev:s_vend:s_dev:rev 8086:0101:0000:0000:09
class 06, sub_class 04 prog_if 00, hdr 1, flags <>, irq 24
  00: 86 80 01 01 07 04 10 00 09 00 04 06 10 00 81 00  "................"
  10: 00 00 00 00 00 00 00 00 00 01 01 00 f0 00 00 00  "................"
  20: f0 ff 00 00 f1 ff 01 00 00 00 00 00 00 00 00 00  "................"
  30: 00 00 00 00 88 00 00 00 00 00 00 00 0b 01 10 00  "................"

bus 00->02, slot 01, func 1, vend:dev:s_vend:s_dev:rev 8086:0105:0000:0000:09
class 06, sub_class 04 prog_if 00, hdr 1, flags <>, irq 25
  00: 86 80 05 01 07 04 10 00 09 00 04 06 10 00 81 00  "................"
  10: 00 00 00 00 00 00 00 00 00 02 02 00 e0 e0 00 00  "................"
  20: 00 f8 00 fa 01 d0 f1 db 00 00 00 00 00 00 00 00  "................"
  30: 00 00 00 00 88 00 00 00 00 00 00 00 0b 01 18 00  "................"

bus 00, slot 16, func 0, vend:dev:s_vend:s_dev:rev 8086:1c3a:1462:7673:04
class 07, sub_class 80 prog_if 00, hdr 0, flags <>, irq 11
  addr0 fa307000, size 00000010
  00: 86 80 3a 1c 06 00 18 00 04 00 80 07 00 00 80 00  "..:............."
  10: 04 70 30 fa 00 00 00 00 00 00 00 00 00 00 00 00  ".p0............."
  20: 00 00 00 00 00 00 00 00 00 00 00 00 62 14 73 76  "............b.sv"
  30: 00 00 00 00 50 00 00 00 00 00 00 00 0b 01 00 00  "....P..........."

bus 00, slot 1a, func 0, vend:dev:s_vend:s_dev:rev 8086:1c2d:1462:7673:05
class 0c, sub_class 03 prog_if 20, hdr 0, flags <>, irq 16
  addr0 fa306000, size 00000400
  00: 86 80 2d 1c 06 00 90 02 05 20 03 0c 00 00 00 00  "..-...... ......"
  10: 00 60 30 fa 00 00 00 00 00 00 00 00 00 00 00 00  ".`0............."
  20: 00 00 00 00 00 00 00 00 00 00 00 00 62 14 73 76  "............b.sv"
  30: 00 00 00 00 50 00 00 00 00 00 00 00 0b 01 00 00  "....P..........."

bus 00, slot 1b, func 0, vend:dev:s_vend:s_dev:rev 8086:1c20:1462:7673:05
class 04, sub_class 03 prog_if 00, hdr 0, flags <>, irq 22
  addr0 fa300000, size 00004000
  00: 86 80 20 1c 06 00 10 00 05 00 03 04 10 00 00 00  ".. ............."
  10: 04 00 30 fa 00 00 00 00 00 00 00 00 00 00 00 00  "..0............."
  20: 00 00 00 00 00 00 00 00 00 00 00 00 62 14 73 76  "............b.sv"
  30: 00 00 00 00 50 00 00 00 00 00 00 00 03 01 00 00  "....P..........."

bus 00->03, slot 1c, func 0, vend:dev:s_vend:s_dev:rev 8086:1c10:0000:0000:b5
class 06, sub_class 04 prog_if 00, hdr 1, flags <>, irq 26
  00: 86 80 10 1c 07 04 10 00 b5 00 04 06 10 00 81 00  "................"
  10: 00 00 00 00 00 00 00 00 00 03 03 00 f0 00 00 20  "............... "
  20: f0 ff 00 00 f1 ff 01 00 00 00 00 00 00 00 00 00  "................"
  30: 00 00 00 00 40 00 00 00 00 00 00 00 0a 01 10 00  "....@..........."

bus 00->04, slot 1c, func 4, vend:dev:s_vend:s_dev:rev 8086:244e:0000:0000:b5
class 06, sub_class 04 prog_if 01, hdr 1, flags <>, irq 17
  00: 86 80 4e 24 07 00 10 00 b5 01 04 06 10 00 81 00  "..N$............"
  10: 00 00 00 00 00 00 00 00 00 04 05 00 d0 d0 00 20  "............... "
  20: 20 fa 20 fa f1 ff 01 00 00 00 00 00 00 00 00 00  " . ............."
  30: 00 00 00 00 40 00 00 00 00 00 00 00 0a 01 10 00  "....@..........."

bus 00->06, slot 1c, func 6, vend:dev:s_vend:s_dev:rev 8086:1c1c:0000:0000:b5
class 06, sub_class 04 prog_if 00, hdr 1, flags <>, irq 27
  00: 86 80 1c 1c 07 04 10 00 b5 00 04 06 10 00 81 00  "................"
  10: 00 00 00 00 00 00 00 00 00 06 06 00 f0 00 00 20  "............... "
  20: f0 ff 00 00 f1 ff 01 00 00 00 00 00 00 00 00 00  "................"
  30: 00 00 00 00 40 00 00 00 00 00 00 00 05 03 10 00  "....@..........."

bus 00->07, slot 1c, func 7, vend:dev:s_vend:s_dev:rev 8086:1c1e:0000:0000:b5
class 06, sub_class 04 prog_if 00, hdr 1, flags <>, irq 28
  00: 86 80 1e 1c 07 04 10 00 b5 00 04 06 10 00 81 00  "................"
  10: 00 00 00 00 00 00 00 00 00 07 07 00 c0 c0 00 00  "................"
  20: 10 fa 10 fa f1 ff 01 00 00 00 00 00 00 00 00 00  "................"
  30: 00 00 00 00 40 00 00 00 00 00 00 00 0b 04 10 00  "....@..........."

bus 00, slot 1d, func 0, vend:dev:s_vend:s_dev:rev 8086:1c26:1462:7673:05
class 0c, sub_class 03 prog_if 20, hdr 0, flags <>, irq 23
  addr0 fa305000, size 00000400
  00: 86 80 26 1c 06 00 90 02 05 20 03 0c 00 00 00 00  "..&...... ......"
  10: 00 50 30 fa 00 00 00 00 00 00 00 00 00 00 00 00  ".P0............."
  20: 00 00 00 00 00 00 00 00 00 00 00 00 62 14 73 76  "............b.sv"
  30: 00 00 00 00 50 00 00 00 00 00 00 00 07 01 00 00  "....P..........."

bus 00, slot 1f, func 0, vend:dev:s_vend:s_dev:rev 8086:1c46:1462:7673:05
class 06, sub_class 01 prog_if 00, hdr 0, flags <>, irq 0
  00: 86 80 46 1c 07 00 10 02 05 00 01 06 00 00 80 00  "..F............."
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 62 14 73 76  "............b.sv"
  30: 00 00 00 00 e0 00 00 00 00 00 00 00 00 00 00 00  "................"

bus 00, slot 1f, func 2, vend:dev:s_vend:s_dev:rev 8086:1c00:1462:7673:05
class 01, sub_class 01 prog_if 8a, hdr 0, flags <>, irq 19
  addr0 000001f0, size 00000008
  addr1 000003f6, size 00000001
  addr2 00000170, size 00000008
  addr3 00000376, size 00000001
  addr4 0000f090, size 00000010
  addr5 0000f080, size 00000010
  00: 86 80 00 1c 07 00 b0 02 05 8a 01 01 00 00 00 00  "................"
  10: d1 f0 00 00 c1 f0 00 00 b1 f0 00 00 a1 f0 00 00  "................"
  20: 91 f0 00 00 81 f0 00 00 00 00 00 00 62 14 73 76  "............b.sv"
  30: 00 00 00 00 70 00 00 00 00 00 00 00 0b 02 00 00  "....p..........."

bus 00, slot 1f, func 3, vend:dev:s_vend:s_dev:rev 8086:1c22:1462:7673:05
class 0c, sub_class 05 prog_if 00, hdr 0, flags <>, irq 5
  addr0 fa304000, size 00000100
  addr4 0000f000, size 00000020
  00: 86 80 22 1c 03 00 80 02 05 00 05 0c 00 00 00 00  ".."............."
  10: 04 40 30 fa 00 00 00 00 00 00 00 00 00 00 00 00  ".@0............."
  20: 01 f0 00 00 00 00 00 00 00 00 00 00 62 14 73 76  "............b.sv"
  30: 00 00 00 00 00 00 00 00 00 00 00 00 05 03 00 00  "................"

bus 00, slot 1f, func 5, vend:dev:s_vend:s_dev:rev 8086:1c08:1462:7673:05
class 01, sub_class 01 prog_if 85, hdr 0, flags <>, irq 19
  addr0 0000f070, size 00000008
  addr1 0000f060, size 00000004
  addr2 0000f050, size 00000008
  addr3 0000f040, size 00000004
  addr4 0000f030, size 00000010
  addr5 0000f020, size 00000010
  00: 86 80 08 1c 05 00 b0 02 05 85 01 01 00 00 00 00  "................"
  10: 71 f0 00 00 61 f0 00 00 51 f0 00 00 41 f0 00 00  "q...a...Q...A..."
  20: 31 f0 00 00 21 f0 00 00 00 00 00 00 62 14 73 76  "1...!.......b.sv"
  30: 00 00 00 00 70 00 00 00 00 00 00 00 0b 02 00 00  "....p..........."

bus 02, slot 00, func 0, vend:dev:s_vend:s_dev:rev 10de:1200:1462:2382:a1
class 03, sub_class 00 prog_if 00, hdr 0, flags <>, irq 17
  addr0 f8000000, size 02000000
  addr1 d0000000, size 08000000
  addr3 d8000000, size 04000000
  addr5 0000e000, size 00000080
  00: de 10 00 12 07 00 10 00 a1 00 00 03 00 00 80 00  "................"
  10: 00 00 00 f8 0c 00 00 d0 00 00 00 00 0c 00 00 d8  "................"
  20: 00 00 00 00 01 e0 00 00 00 00 00 00 62 14 82 23  "............b..#"
  30: 00 00 00 00 60 00 00 00 00 00 00 00 0a 01 00 00  "....`..........."

bus 02, slot 00, func 1, vend:dev:s_vend:s_dev:rev 10de:0e0c:1462:2382:a1
class 04, sub_class 03 prog_if 00, hdr 0, flags <>, irq 5
  addr0 fa080000, size 00004000
  00: de 10 0c 0e 06 00 10 00 a1 00 03 04 10 00 80 00  "................"
  10: 00 00 08 fa 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 62 14 82 23  "............b..#"
  30: 00 00 00 00 60 00 00 00 00 00 00 00 05 02 00 00  "....`..........."

bus 04->05, slot 00, func 0, vend:dev:s_vend:s_dev:rev 1b21:1080:0000:0000:01
class 06, sub_class 04 prog_if 00, hdr 1, flags <>, irq 16
  00: 21 1b 80 10 07 00 10 00 01 00 04 06 10 00 01 00  "!..............."
  10: 00 00 00 00 00 00 00 00 04 05 05 20 d1 d1 20 20  "........... ..  "
  20: 20 fa 20 fa f1 ff 01 00 00 00 00 00 00 00 00 00  " . ............."
  30: 00 00 00 00 50 00 00 00 00 00 00 00 0b 01 10 00  "....P..........."

bus 05, slot 01, func 0, vend:dev:s_vend:s_dev:rev 10ec:8139:10ec:8139:10
class 02, sub_class 00 prog_if 00, hdr 0, flags <>, irq 17
  addr0 0000d000, size 00000100
  addr1 fa220000, size 00000100
  00: ec 10 39 81 07 00 90 02 10 00 00 02 00 20 00 00  "..9.......... .."
  10: 01 d0 00 00 00 00 22 fa 00 00 00 00 00 00 00 00  "......"........."
  20: 00 00 00 00 00 00 00 00 00 00 00 00 ec 10 39 81  "..............9."
  30: 00 00 20 fa 50 00 00 00 00 00 00 00 0a 01 20 40  ".. .P......... @"

bus 07, slot 00, func 0, vend:dev:s_vend:s_dev:rev 1106:3403:1462:673d:01
class 0c, sub_class 00 prog_if 10, hdr 0, flags <>, irq 19
  addr0 fa100000, size 00000800
  addr2 0000c000, size 00000100
  00: 06 11 03 34 07 00 10 00 01 10 00 0c 10 00 00 00  "...4............"
  10: 04 00 10 fa 00 00 00 00 01 c0 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 62 14 3d 67  "............b.=g"
  30: 00 00 00 00 50 00 00 00 00 00 00 00 0b 01 00 00  "....P..........."
---------- PCI raw data end ----------
>> pci.4: build list
>> pci.3: macio
sysfs: no such bus: macio
>> pci.4: vio
sysfs: no such bus: vio
>> pci.5: xen
sysfs: no such bus: xen
>> pci.6: ps3
sysfs: no such bus: ps3_system_bus
>> pci.7: platform
  platform device: name = pcspkr
    path = /devices/platform/pcspkr
    type = "platform:pcspkr"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = serial8250
    path = /devices/platform/serial8250
    type = "platform:serial8250"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = Fixed MDIO bus.0
    path = /devices/platform/Fixed MDIO bus.0
    type = "platform:Fixed MDIO bus"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = i8042
    path = /devices/platform/i8042
    type = "platform:i8042"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = eisa.0
    path = /devices/platform/eisa.0
    type = "platform:eisa"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = vga16fb.0
    path = /devices/platform/vga16fb.0
    type = "platform:vga16fb"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
>> pci.8: of_platform
sysfs: no such bus: of_platform
>> pci.9: vm
sysfs: no such bus: vm
>> pci.10: virtio
sysfs: no such bus: virtio
>> pci.11: ibmebus
sysfs: no such bus: ibmebus
>> monitor.1: ddc
>> monitor.2: bios
>> monitor.3: pci
>> monitor.4: internal db
>> monitor.5: prom
>> isapnp.1: pnp devices
  pnp device: name = 00:00
    path = /devices/pnp0/00:00
    id = PNP 0a08
  pnp device: name = 00:01
    path = /devices/pnp0/00:01
    id = PNP 0c01
  pnp device: name = 00:02
    path = /devices/pnp0/00:02
    id = PNP 0c02
  pnp device: name = 00:03
    path = /devices/pnp0/00:03
    id = PNP 0501
  pnp device: name = 00:04
    path = /devices/pnp0/00:04
    id = PNP 0200
  pnp device: name = 00:05
    path = /devices/pnp0/00:05
    id = PNP 0b00
  pnp device: name = 00:06
    path = /devices/pnp0/00:06
    id = PNP 0800
  pnp device: name = 00:07
    path = /devices/pnp0/00:07
    id = PNP 0c02
  pnp device: name = 00:08
    path = /devices/pnp0/00:08
    id = PNP 0c04
  pnp device: name = 00:09
    path = /devices/pnp0/00:09
    id = PNP 0c01
  pnp device: name = 00:0a
    path = /devices/pnp0/00:0a
    id = INT 3f0d
  pnp device: name = 00:0b
    path = /devices/pnp0/00:0b
    id = PNP 0103
>> pcmcia.1: sysfs drivers
>> pcmcia.2: pcmcia
sysfs: no such bus: pcmcia
>> pcmcia.3: pcmcia ctrl
sysfs: no such class: pcmcia_socket
>> serial.1: read info
----- serial info -----
----- serial info end -----
>> serial.2: build list
>> misc.5: misc data
----- misc resources -----
i/o:1 0x0000 - 0x001f (0x20) "dma1"
i/o:1 0x0020 - 0x0021 (0x02) "pic1"
i/o:0 0x0040 - 0x0043 (0x04) "timer0"
i/o:0 0x0050 - 0x0053 (0x04) "timer1"
i/o:1 0x0060 - 0x0060 (0x01) "keyboard"
i/o:1 0x0064 - 0x0064 (0x01) "keyboard"
i/o:0 0x0070 - 0x0071 (0x02) "rtc0"
i/o:1 0x0080 - 0x008f (0x10) "dma page reg"
i/o:1 0x00a0 - 0x00a1 (0x02) "pic2"
i/o:1 0x00c0 - 0x00df (0x20) "dma2"
i/o:1 0x00f0 - 0x00ff (0x10) "fpu"
i/o:0 0x0170 - 0x0177 (0x08) "0000:00:1f.2"
i/o:0 0x0170 - 0x0177 (0x08) "ata_piix"
i/o:0 0x01f0 - 0x01f7 (0x08) "0000:00:1f.2"
i/o:0 0x01f0 - 0x01f7 (0x08) "ata_piix"
i/o:0 0x0376 - 0x0376 (0x01) "0000:00:1f.2"
i/o:0 0x0376 - 0x0376 (0x01) "ata_piix"
i/o:1 0x03c0 - 0x03df (0x20) "vga+"
i/o:0 0x03f6 - 0x03f6 (0x01) "0000:00:1f.2"
i/o:0 0x03f6 - 0x03f6 (0x01) "ata_piix"
i/o:1 0x03f8 - 0x03ff (0x08) "serial"
i/o:0 0x0400 - 0x0453 (0x54) "pnp 00:09"
i/o:0 0x0400 - 0x0403 (0x04) "ACPI PM1a_EVT_BLK"
i/o:0 0x0404 - 0x0405 (0x02) "ACPI PM1a_CNT_BLK"
i/o:0 0x0408 - 0x040b (0x04) "ACPI PM_TMR"
i/o:0 0x0410 - 0x0415 (0x06) "ACPI CPU throttle"
i/o:0 0x0420 - 0x042f (0x10) "ACPI GPE0_BLK"
i/o:0 0x0450 - 0x0450 (0x01) "ACPI PM2_CNT_BLK"
i/o:0 0x0454 - 0x0457 (0x04) "pnp 00:0a"
i/o:0 0x0458 - 0x047f (0x28) "pnp 00:09"
i/o:0 0x04d0 - 0x04d1 (0x02) "pnp 00:07"
i/o:0 0x0500 - 0x057f (0x80) "pnp 00:09"
i/o:0 0x0a00 - 0x0a0f (0x10) "pnp 00:02"
i/o:0 0x0cf8 - 0x0cff (0x08) "PCI conf1"
i/o:0 0x1180 - 0x119f (0x20) "pnp 00:09"
i/o:0 0xc000 - 0xcfff (0x1000) "PCI Bus 0000:07"
i/o:0 0xc000 - 0xc0ff (0x100) "0000:07:00.0"
i/o:0 0xd000 - 0xdfff (0x1000) "PCI Bus 0000:04"
i/o:0 0xd000 - 0xdfff (0x1000) "PCI Bus 0000:05"
i/o:0 0xd000 - 0xd0ff (0x100) "0000:05:01.0"
i/o:0 0xd000 - 0xd0ff (0x100) "8139too"
i/o:0 0xe000 - 0xefff (0x1000) "PCI Bus 0000:02"
i/o:0 0xe000 - 0xe07f (0x80) "0000:02:00.0"
i/o:0 0xf000 - 0xf01f (0x20) "0000:00:1f.3"
i/o:0 0xf020 - 0xf02f (0x10) "0000:00:1f.5"
i/o:0 0xf020 - 0xf02f (0x10) "ata_piix"
i/o:0 0xf030 - 0xf03f (0x10) "0000:00:1f.5"
i/o:0 0xf030 - 0xf03f (0x10) "ata_piix"
i/o:0 0xf040 - 0xf043 (0x04) "0000:00:1f.5"
i/o:0 0xf040 - 0xf043 (0x04) "ata_piix"
i/o:0 0xf050 - 0xf057 (0x08) "0000:00:1f.5"
i/o:0 0xf050 - 0xf057 (0x08) "ata_piix"
i/o:0 0xf060 - 0xf063 (0x04) "0000:00:1f.5"
i/o:0 0xf060 - 0xf063 (0x04) "ata_piix"
i/o:0 0xf070 - 0xf077 (0x08) "0000:00:1f.5"
i/o:0 0xf070 - 0xf077 (0x08) "ata_piix"
i/o:0 0xf080 - 0xf08f (0x10) "0000:00:1f.2"
i/o:0 0xf080 - 0xf08f (0x10) "ata_piix"
i/o:0 0xf090 - 0xf09f (0x10) "0000:00:1f.2"
i/o:0 0xf090 - 0xf09f (0x10) "ata_piix"
irq:1  0 (       74) "timer"
irq:0  1 (        2) "i8042"
irq:1  4 (        7) "serial"
irq:0  8 (        1) "rtc0"
irq:0  9 (        0) "acpi"
irq:0 12 (        4) "i8042"
irq:0 14 (   125729) "ata_piix"
irq:0 15 (    77991) "ata_piix"
irq:0 16 (   140763) "ehci_hcd:usb1"
irq:0 17 (   200036) "eth0" "nvidia"
irq:0 19 (        2) "ata_piix" "ohci1394"
irq:0 22 (      634) "HDA Intel"
irq:0 23 (    10938) "ehci_hcd:usb2"
dma:1 4 "cascade"
----- misc resources end -----
>> parallel.1: pp mod
----- exec: "/sbin/rmmod lp" -----
  ERROR: Removing 'lp': Operation not permitted
----- return code: ? -----
----- exec: "/sbin/modprobe parport_pc" -----
  FATAL: Error inserting parport_pc (/lib/modules/2.6.32-38-generic-pae/kernel/drivers/parport/parport_pc.ko): Operation not permitted
----- return code: ? -----
>> parallel.2.1: lp read info
>> parallel.2.2: lp read info
>> parallel.2.3: lp read info
----- parallel info -----
----- parallel info end -----
>> block.1: block modules
----- exec: "/sbin/modprobe ide-cd_mod " -----
  FATAL: Module ide_cd_mod not found.
----- return code: ? -----
----- exec: "/sbin/modprobe ide-disk " -----
  FATAL: Module ide_disk not found.
----- return code: ? -----
----- exec: "/sbin/modprobe sr_mod " -----
----- return code: ? -----
----- exec: "/sbin/modprobe sd_mod " -----
----- return code: ? -----
----- exec: "/sbin/modprobe st " -----
  FATAL: Error inserting st (/lib/modules/2.6.32-38-generic-pae/kernel/drivers/scsi/st.ko): Operation not permitted
----- return code: ? -----
>> block.2: sysfs drivers
>> block.3: cdrom
----- /proc/sys/dev/cdrom/info -----
drive name:		sr0
drive speed:		48
drive # of slots:	1
Can close tray:		1
Can open tray:		1
Can lock tray:		1
Can change speed:	1
Can select disk:	0
Can read multisession:	1
Can read MCN:		1
Reports media changed:	1
Can play audio:		1
Can write CD-R:		1
Can write CD-RW:	1
Can read DVD:		1
Can write DVD-R:	1
Can write DVD-RAM:	1
Can read MRW:		1
Can write MRW:		1
Can write RAM:		1
----- /proc/sys/dev/cdrom/info end -----
>> block.4: partition
----- /proc/partitions -----
     8        0  488386584 sda
     8        1     102400 sda1
     8        2  395483840 sda2
     8        3          1 sda3
     8        5     262144 sda5
     8        6   92533761 sda6
   251        0   92531741 dm-0
   251        1    3821568 dm-1
   251        2   88707072 dm-2
----- /proc/partitions end -----
disks:
  sda
partitions:
  sda1
  sda2
  sda3
  sda5
  sda6
>> block.5: get sysfs block dev data
-----  lsscsi -----
-----  lsscsi end -----
  block: name = ram0, path = /class/block/ram0
    dev = 1:0
    range = 1
  block: name = ram1, path = /class/block/ram1
    dev = 1:1
    range = 1
  block: name = ram2, path = /class/block/ram2
    dev = 1:2
    range = 1
  block: name = ram3, path = /class/block/ram3
    dev = 1:3
    range = 1
  block: name = ram4, path = /class/block/ram4
    dev = 1:4
    range = 1
  block: name = ram5, path = /class/block/ram5
    dev = 1:5
    range = 1
  block: name = ram6, path = /class/block/ram6
    dev = 1:6
    range = 1
  block: name = ram7, path = /class/block/ram7
    dev = 1:7
    range = 1
  block: name = ram8, path = /class/block/ram8
    dev = 1:8
    range = 1
  block: name = ram9, path = /class/block/ram9
    dev = 1:9
    range = 1
  block: name = ram10, path = /class/block/ram10
    dev = 1:10
    range = 1
  block: name = ram11, path = /class/block/ram11
    dev = 1:11
    range = 1
  block: name = ram12, path = /class/block/ram12
    dev = 1:12
    range = 1
  block: name = ram13, path = /class/block/ram13
    dev = 1:13
    range = 1
  block: name = ram14, path = /class/block/ram14
    dev = 1:14
    range = 1
  block: name = ram15, path = /class/block/ram15
    dev = 1:15
    range = 1
  block: name = loop0, path = /class/block/loop0
    dev = 7:0
    range = 1
  block: name = loop1, path = /class/block/loop1
    dev = 7:1
    range = 1
  block: name = loop2, path = /class/block/loop2
    dev = 7:2
    range = 1
  block: name = loop3, path = /class/block/loop3
    dev = 7:3
    range = 1
  block: name = loop4, path = /class/block/loop4
    dev = 7:4
    range = 1
  block: name = loop5, path = /class/block/loop5
    dev = 7:5
    range = 1
  block: name = loop6, path = /class/block/loop6
    dev = 7:6
    range = 1
  block: name = loop7, path = /class/block/loop7
    dev = 7:7
    range = 1
  block: name = sr0, path = /class/block/sr0
    dev = 11:0
    range = 1
    block device: bus = scsi, bus_id = 0:0:0:0 driver = sr
      path = /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0
    vendor = ATAPI
    model = iHAS124   B
    rev = AL0Q
    type = 5
>> block.5: /dev/sr0
>> block.5.1: /dev/sr0 cache
  scsi cache: 0x00
  block: name = sda, path = /class/block/sda
    dev = 8:0
    range = 16
    block device: bus = scsi, bus_id = 1:0:0:0 driver = sd
      path = /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0
    vendor = ATA
    model = WDC WD5000AAKX-0
    rev = 15.0
    type = 0
>> block.5: /dev/sda
  block: name = sda1, path = /class/block/sda1
    dev = 8:1
  block: name = sda2, path = /class/block/sda2
    dev = 8:2
  block: name = sda3, path = /class/block/sda3
    dev = 8:3
  block: name = sda5, path = /class/block/sda5
    dev = 8:5
  block: name = sda6, path = /class/block/sda6
    dev = 8:6
  block: name = dm-0, path = /class/block/dm-0
    dev = 251:0
    range = 1
  block: name = dm-1, path = /class/block/dm-1
    dev = 251:1
    range = 1
  block: name = dm-2, path = /class/block/dm-2
    dev = 251:2
    range = 1
>> scsi.1: scsi modules
----- exec: "/sbin/modprobe sg " -----
----- return code: ? -----
>> scsi.2: scsi tape
sysfs: no such class: scsi_tape
>> scsi.3: scsi generic
  scsi: name = sg0, path = /class/scsi_generic/sg0
    dev = 21:0
    scsi device: bus_id = 0:0:0:0 driver = sr
      path = /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0
  scsi: name = sg1, path = /class/scsi_generic/sg1
    dev = 21:1
    scsi device: bus_id = 1:0:0:0 driver = sd
      path = /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0
>> usb.1: sysfs drivers
>> usb.2: usb
  usb dev: /devices/pci0000:00/0000:00:1a.0/usb1
  usb dev: /devices/pci0000:00/0000:00:1d.0/usb2
  usb dev: /devices/pci0000:00/0000:00:1a.0/usb1/1-1
  usb dev: /devices/pci0000:00/0000:00:1d.0/usb2/2-1
  usb dev: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3
  usb dev: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6
  usb dev: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5
  usb dev: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6
  usb dev: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1
  usb dev: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3
  usb device: name = usb1
    path = /devices/pci0000:00/0000:00:1a.0/usb1
  usb device: name = 1-0:1.0
    path = /devices/pci0000:00/0000:00:1a.0/usb1/1-0:1.0
    modalias = "usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 1-0:1.0 @ /devices/pci0000:00/0000:00:1a.0/usb1
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x1d6b
    idProduct = 0x0002
    manufacturer = "Linux 2.6.32-38-generic-pae ehci_hcd"
    product = "EHCI Host Controller"
    serial = "0000:00:1a.0"
    bcdDevice = 0206
    speed = "480"
  usb device: name = usb2
    path = /devices/pci0000:00/0000:00:1d.0/usb2
  usb device: name = 2-0:1.0
    path = /devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0
    modalias = "usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 2-0:1.0 @ /devices/pci0000:00/0000:00:1d.0/usb2
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x1d6b
    idProduct = 0x0002
    manufacturer = "Linux 2.6.32-38-generic-pae ehci_hcd"
    product = "EHCI Host Controller"
    serial = "0000:00:1d.0"
    bcdDevice = 0206
    speed = "480"
  usb device: name = 1-1
    path = /devices/pci0000:00/0000:00:1a.0/usb1/1-1
  usb device: name = 1-1:1.0
    path = /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1:1.0
    modalias = "usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 1-1:1.0 @ /devices/pci0000:00/0000:00:1a.0/usb1/1-1
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 1
    idVendor = 0x8087
    idProduct = 0x0024
    bcdDevice = 0000
    speed = "480"
  usb device: name = 2-1
    path = /devices/pci0000:00/0000:00:1d.0/usb2/2-1
  usb device: name = 2-1:1.0
    path = /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0
    modalias = "usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 2-1:1.0 @ /devices/pci0000:00/0000:00:1d.0/usb2/2-1
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 1
    idVendor = 0x8087
    idProduct = 0x0024
    bcdDevice = 0000
    speed = "480"
  usb device: name = 1-1.3
    path = /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3
  usb device: name = 1-1.3:1.0
    path = /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0
    modalias = "usb:v05E3p0607d0801dc09dsc00dp02ic09isc00ip02"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 2
    if: 1-1.3:1.0 @ /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 2
    idVendor = 0x05e3
    idProduct = 0x0607
    product = "USB2.0 Hub"
    bcdDevice = 0801
    speed = "480"
  usb device: name = 1-1.6
    path = /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6
  usb device: name = 1-1.6:1.0
    path = /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0
    modalias = "usb:v04B4p121Fd0100dc00dsc00dp00ic03isc01ip02"
    bInterfaceNumber = 0
    bInterfaceClass = 3
    bInterfaceSubClass = 1
    bInterfaceProtocol = 2
    if: 1-1.6:1.0 @ /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6
    bDeviceClass = 0
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x04b4
    idProduct = 0x121f
    manufacturer = "SteelSeries ApS"
    product = "Ikari Laser"
    bcdDevice = 0100
    speed = "12"
  usb device: name = 2-1.5
    path = /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5
  usb device: name = 2-1.5:1.0
    path = /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0
    modalias = "usb:v03F0p9311d0100dc00dsc00dp00icFFiscCCip00"
    bInterfaceNumber = 0
    bInterfaceClass = 255
    bInterfaceSubClass = 204
    bInterfaceProtocol = 0
    if: 2-1.5:1.0 @ /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5
    bDeviceClass = 0
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x03f0
    idProduct = 0x9311
    manufacturer = "HP"
    product = "Deskjet 3050 J610 series"
    serial = "CN0BB3B48F05HX"
    bcdDevice = 0100
    speed = "480"
  usb device: name = 2-1.5:1.1
    path = /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.1
    modalias = "usb:v03F0p9311d0100dc00dsc00dp00ic07isc01ip02"
    bInterfaceNumber = 1
    bInterfaceClass = 7
    bInterfaceSubClass = 1
    bInterfaceProtocol = 2
    if: 2-1.5:1.1 @ /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5
    bDeviceClass = 0
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x03f0
    idProduct = 0x9311
    manufacturer = "HP"
    product = "Deskjet 3050 J610 series"
    serial = "CN0BB3B48F05HX"
    bcdDevice = 0100
    speed = "480"
  usb device: name = 2-1.5:1.2
    path = /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.2
    modalias = "usb:v03F0p9311d0100dc00dsc00dp00icFFisc04ip01"
    bInterfaceNumber = 2
    bInterfaceClass = 255
    bInterfaceSubClass = 4
    bInterfaceProtocol = 1
    if: 2-1.5:1.2 @ /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5
    bDeviceClass = 0
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x03f0
    idProduct = 0x9311
    manufacturer = "HP"
    product = "Deskjet 3050 J610 series"
    serial = "CN0BB3B48F05HX"
    bcdDevice = 0100
    speed = "480"
  usb device: name = 2-1.6
    path = /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6
  usb device: name = 2-1.6:1.0
    path = /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0
    modalias = "usb:v0C45p62E0d0100dcEFdsc02dp01ic0Eisc01ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 14
    bInterfaceSubClass = 1
    bInterfaceProtocol = 0
    if: 2-1.6:1.0 @ /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6
    bDeviceClass = 239
    bDeviceSubClass = 2
    bDeviceProtocol = 1
    idVendor = 0x0c45
    idProduct = 0x62e0
    manufacturer = "Sonix Technology Co., Ltd."
    product = "USB 2.0 Camera"
    bcdDevice = 0100
    speed = "480"
  usb device: name = 2-1.6:1.1
    path = /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.1
    modalias = "usb:v0C45p62E0d0100dcEFdsc02dp01ic0Eisc02ip00"
    bInterfaceNumber = 1
    bInterfaceClass = 14
    bInterfaceSubClass = 2
    bInterfaceProtocol = 0
    if: 2-1.6:1.1 @ /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6
    bDeviceClass = 239
    bDeviceSubClass = 2
    bDeviceProtocol = 1
    idVendor = 0x0c45
    idProduct = 0x62e0
    manufacturer = "Sonix Technology Co., Ltd."
    product = "USB 2.0 Camera"
    bcdDevice = 0100
    speed = "480"
  usb device: name = 2-1.6:1.2
    path = /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2
    modalias = "usb:v0C45p62E0d0100dcEFdsc02dp01ic01isc01ip00"
    bInterfaceNumber = 2
    bInterfaceClass = 1
    bInterfaceSubClass = 1
    bInterfaceProtocol = 0
    if: 2-1.6:1.2 @ /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6
    bDeviceClass = 239
    bDeviceSubClass = 2
    bDeviceProtocol = 1
    idVendor = 0x0c45
    idProduct = 0x62e0
    manufacturer = "Sonix Technology Co., Ltd."
    product = "USB 2.0 Camera"
    bcdDevice = 0100
    speed = "480"
  usb device: name = 2-1.6:1.3
    path = /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.3
    modalias = "usb:v0C45p62E0d0100dcEFdsc02dp01ic01isc02ip00"
    bInterfaceNumber = 3
    bInterfaceClass = 1
    bInterfaceSubClass = 2
    bInterfaceProtocol = 0
    if: 2-1.6:1.3 @ /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6
    bDeviceClass = 239
    bDeviceSubClass = 2
    bDeviceProtocol = 1
    idVendor = 0x0c45
    idProduct = 0x62e0
    manufacturer = "Sonix Technology Co., Ltd."
    product = "USB 2.0 Camera"
    bcdDevice = 0100
    speed = "480"
  usb device: name = 1-1.3.1
    path = /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1
  usb device: name = 1-1.3.1:1.0
    path = /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.0
    modalias = "usb:v046DpC22Bd0100dc00dsc00dp00ic03isc01ip01"
    bInterfaceNumber = 0
    bInterfaceClass = 3
    bInterfaceSubClass = 1
    bInterfaceProtocol = 1
    if: 1-1.3.1:1.0 @ /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1
    bDeviceClass = 0
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x046d
    idProduct = 0xc22b
    manufacturer = "LOGITECH"
    product = "G110 G-keys"
    bcdDevice = 0100
    speed = "1.5"
  usb device: name = 1-1.3.1:1.1
    path = /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.1
    modalias = "usb:v046DpC22Bd0100dc00dsc00dp00ic03isc00ip00"
    bInterfaceNumber = 1
    bInterfaceClass = 3
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 1-1.3.1:1.1 @ /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1
    bDeviceClass = 0
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x046d
    idProduct = 0xc22b
    manufacturer = "LOGITECH"
    product = "G110 G-keys"
    bcdDevice = 0100
    speed = "1.5"
  usb device: name = 1-1.3.3
    path = /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3
  usb device: name = 1-1.3.3:1.0
    path = /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.0
    modalias = "usb:v046DpC22Ad0100dc00dsc00dp00ic03isc01ip01"
    bInterfaceNumber = 0
    bInterfaceClass = 3
    bInterfaceSubClass = 1
    bInterfaceProtocol = 1
    if: 1-1.3.3:1.0 @ /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3
    bDeviceClass = 0
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x046d
    idProduct = 0xc22a
    product = "Gaming Keyboard G110"
    bcdDevice = 0100
    speed = "1.5"
  usb device: name = 1-1.3.3:1.1
    path = /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.1
    modalias = "usb:v046DpC22Ad0100dc00dsc00dp00ic03isc00ip00"
    bInterfaceNumber = 1
    bInterfaceClass = 3
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 1-1.3.3:1.1 @ /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3
    bDeviceClass = 0
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x046d
    idProduct = 0xc22a
    product = "Gaming Keyboard G110"
    bcdDevice = 0100
    speed = "1.5"
removed: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.2
removed: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.1
removed: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2
removed: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.3
>> usb.3.1: joydev mod
----- exec: "/sbin/modprobe joydev " -----
  FATAL: Error inserting joydev (/lib/modules/2.6.32-38-generic-pae/kernel/drivers/input/joydev.ko): Operation not permitted
----- return code: ? -----
>> usb.3.2: evdev mod
----- exec: "/sbin/modprobe evdev " -----
----- return code: ? -----
>> usb.3.3: input
  input: name = input0, path = /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
    no dev - ignored
  input: name = input1, path = /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
    no dev - ignored
  input: name = input2, path = /devices/virtual/input/input2
    no dev - ignored
  input: name = mice, path = /devices/virtual/input/mice
    dev = 13:63
  input: name = mouse0, path = /devices/virtual/input/input2/mouse0
    dev = 13:32
    input device: bus = input, bus_id = input2 driver = (null)
      path = /devices/virtual/input/input2
  input: name = event0, path = /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0
    dev = 13:64
    input device: bus = acpi, bus_id = PNP0C0C:00 driver = button
      path = /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00
  input: name = event1, path = /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1
    dev = 13:65
    input device: bus = acpi, bus_id = LNXPWRBN:00 driver = button
      path = /devices/LNXSYSTM:00/LNXPWRBN:00
  input: name = event2, path = /devices/virtual/input/input2/event2
    dev = 13:66
    input device: bus = input, bus_id = input2 driver = (null)
      path = /devices/virtual/input/input2
  input: name = input3, path = /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input3
    no dev - ignored
  input: name = mouse1, path = /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input3/mouse1
    dev = 13:33
    input device: bus = usb, bus_id = 1-1.6:1.0 driver = usbhid
      path = /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0
  input: name = event3, path = /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input3/event3
    dev = 13:67
    input device: bus = usb, bus_id = 1-1.6:1.0 driver = usbhid
      path = /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0
  input: name = input4, path = /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.0/input/input4
    no dev - ignored
  input: name = event4, path = /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.0/input/input4/event4
    dev = 13:68
    input device: bus = usb, bus_id = 1-1.3.1:1.0 driver = usbhid
      path = /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.0
  input: name = input5, path = /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.0/input/input5
    no dev - ignored
  input: name = event5, path = /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.0/input/input5/event5
    dev = 13:69
    input device: bus = usb, bus_id = 1-1.3.3:1.0 driver = usbhid
      path = /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.0
  input: name = input6, path = /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.1/input/input6
    no dev - ignored
  input: name = event6, path = /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.1/input/input6/event6
    dev = 13:70
    input device: bus = usb, bus_id = 1-1.3.3:1.1 driver = usbhid
      path = /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.1
  input: name = input7, path = /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input7
    no dev - ignored
  input: name = event7, path = /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input7/event7
    dev = 13:71
    input device: bus = usb, bus_id = 2-1.6:1.0 driver = uvcvideo
      path = /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0
>> usb.3.4: lp
  usb: name = lp0, path = /class/usb/lp0
    dev = 180:0
    usb device: bus = (null), bus_id = 2-1.5:1.1 driver = usblp
      path = /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.1
>> usb.3.5: serial
>> edd.1: edd mod
----- exec: "/sbin/modprobe edd " -----
----- return code: ? -----
>> edd.2: edd info
>> modem.1: serial
******  started child process 24683 (15s/120s)  ******
******  stopped child process 24683 (120s)  ******
>> mouse.2: serial
******  started child process 24684 (20s/20s)  ******
******  stopped child process 24684 (20s)  ******
>> input.1: joydev mod
----- exec: "/sbin/modprobe joydev " -----
  FATAL: Error inserting joydev (/lib/modules/2.6.32-38-generic-pae/kernel/drivers/input/joydev.ko): Operation not permitted
----- return code: ? -----
>> input.1.1: evdev mod
----- exec: "/sbin/modprobe evdev " -----
----- return code: ? -----
>> input.2: input
----- /proc/bus/input/devices -----
  I: Bus=0019 Vendor=0000 Product=0001 Version=0000
  N: Name="Power Button"
  P: Phys=PNP0C0C/button/input0
  S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
  U: Uniq=
  H: Handlers=kbd event0 
  B: EV=3
  B: KEY=100000 0 0 0
  
  I: Bus=0019 Vendor=0000 Product=0001 Version=0000
  N: Name="Power Button"
  P: Phys=LNXPWRBN/button/input0
  S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
  U: Uniq=
  H: Handlers=kbd event1 
  B: EV=3
  B: KEY=100000 0 0 0
  
  I: Bus=0017 Vendor=0001 Product=0001 Version=0100
  N: Name="Macintosh mouse button emulation"
  P: Phys=
  S: Sysfs=/devices/virtual/input/input2
  U: Uniq=
  H: Handlers=mouse0 event2 
  B: EV=7
  B: KEY=70000 0 0 0 0 0 0 0 0
  B: REL=3
  
  I: Bus=0003 Vendor=04b4 Product=121f Version=0111
  N: Name="SteelSeries ApS Ikari Laser"
  P: Phys=usb-0000:00:1a.0-1.6/input0
  S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input3
  U: Uniq=
  H: Handlers=kbd mouse1 event3 
  B: EV=120017
  B: KEY=7f0000 0 18000 68 c0010100 e08effdf 1cfffff ffffffff fffffffe
  B: REL=103
  B: MSC=10
  B: LED=1f
  
  I: Bus=0003 Vendor=046d Product=c22b Version=0100
  N: Name="LOGITECH G110 G-keys"
  P: Phys=usb-0000:00:1a.0-1.3.1/input0
  S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.0/input/input4
  U: Uniq=
  H: Handlers=kbd event4 
  B: EV=100013
  B: KEY=10000 7 ff980000 7ff febeffdf ffefffff ffffffff fffffffe
  B: MSC=10
  
  I: Bus=0003 Vendor=046d Product=c22a Version=0110
  N: Name="Gaming Keyboard G110"
  P: Phys=usb-0000:00:1a.0-1.3.3/input0
  S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.0/input/input5
  U: Uniq=
  H: Handlers=kbd event5 
  B: EV=120013
  B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
  B: MSC=10
  B: LED=1f
  
  I: Bus=0003 Vendor=046d Product=c22a Version=0110
  N: Name="Gaming Keyboard G110"
  P: Phys=usb-0000:00:1a.0-1.3.3/input1
  S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.1/input/input6
  U: Uniq=
  H: Handlers=kbd event6 
  B: EV=13
  B: KEY=78 0 e0000 0 0 0
  B: MSC=10
  
  I: Bus=0003 Vendor=0c45 Product=62e0 Version=0100
  N: Name="USB 2.0 Camera"
  P: Phys=usb-0000:00:1d.0-1.6/button
  S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input7
  U: Uniq=
  H: Handlers=kbd event7 
  B: EV=3
  B: KEY=100000 0 0 0 0 0 0
  
----- /proc/bus/input/devices end -----
bus = 25, name = Power Button
  handlers = kbd event0
  key = 00100000000000000000000000000000
  mouse buttons = 0
  mouse wheels = 0
bus = 25, name = Power Button
  handlers = kbd event1
  key = 00100000000000000000000000000000
  mouse buttons = 0
  mouse wheels = 0
bus = 23, name = Macintosh mouse button emulation
  handlers = mouse0 event2
  key = 000700000000000000000000000000000000000000000000000000000000000000000000
  rel = 00000003
  mouse buttons = 3
  mouse wheels = 0
bus = 3, name = SteelSeries ApS Ikari Laser
  handlers = kbd mouse1 event3
  key = 007f0000000000000001800000000068c0010100e08effdf01cffffffffffffffffffffe
  rel = 00000103
  mouse buttons = 7
  mouse wheels = 1
bus = 3, name = LOGITECH G110 G-keys
  handlers = kbd event4
  key = 0001000000000007ff980000000007fffebeffdfffeffffffffffffffffffffe
  mouse buttons = 0
  mouse wheels = 0
bus = 3, name = Gaming Keyboard G110
  handlers = kbd event5
  key = 0001000000000007ff800000000007fffebeffdfffeffffffffffffffffffffe
  mouse buttons = 0
  mouse wheels = 0
bus = 3, name = Gaming Keyboard G110
  handlers = kbd event6
  key = 0000007800000000000e0000000000000000000000000000
  mouse buttons = 0
  mouse wheels = 0
bus = 3, name = USB 2.0 Camera
  handlers = kbd event7
  key = 00100000000000000000000000000000000000000000000000000000
  mouse buttons = 0
  mouse wheels = 0
>> kbd.2: uml
>> cpu.1: cpuinfo
----- /proc/cpuinfo -----
  processor	: 0
  vendor_id	: GenuineIntel
  cpu family	: 6
  model		: 42
  model name	: Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz
  stepping	: 7
  cpu MHz		: 3301.000
  cache size	: 6144 KB
  physical id	: 0
  siblings	: 4
  core id		: 0
  cpu cores	: 4
  apicid		: 0
  initial apicid	: 0
  fdiv_bug	: no
  hlt_bug		: no
  f00f_bug	: no
  coma_bug	: no
  fpu		: yes
  fpu_exception	: yes
  cpuid level	: 13
  wp		: yes
  flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt aes xsave avx lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid
  bogomips	: 6584.49
  clflush size	: 64
  cache_alignment	: 64
  address sizes	: 36 bits physical, 48 bits virtual
  power management:
  
  processor	: 1
  vendor_id	: GenuineIntel
  cpu family	: 6
  model		: 42
  model name	: Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz
  stepping	: 7
  cpu MHz		: 1600.000
  cache size	: 6144 KB
  physical id	: 0
  siblings	: 4
  core id		: 1
  cpu cores	: 4
  apicid		: 2
  initial apicid	: 2
  fdiv_bug	: no
  hlt_bug		: no
  f00f_bug	: no
  coma_bug	: no
  fpu		: yes
  fpu_exception	: yes
  cpuid level	: 13
  wp		: yes
  flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt aes xsave avx lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid
  bogomips	: 6584.98
  clflush size	: 64
  cache_alignment	: 64
  address sizes	: 36 bits physical, 48 bits virtual
  power management:
  
  processor	: 2
  vendor_id	: GenuineIntel
  cpu family	: 6
  model		: 42
  model name	: Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz
  stepping	: 7
  cpu MHz		: 1600.000
  cache size	: 6144 KB
  physical id	: 0
  siblings	: 4
  core id		: 2
  cpu cores	: 4
  apicid		: 4
  initial apicid	: 4
  fdiv_bug	: no
  hlt_bug		: no
  f00f_bug	: no
  coma_bug	: no
  fpu		: yes
  fpu_exception	: yes
  cpuid level	: 13
  wp		: yes
  flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt aes xsave avx lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid
  bogomips	: 6585.00
  clflush size	: 64
  cache_alignment	: 64
  address sizes	: 36 bits physical, 48 bits virtual
  power management:
  
  processor	: 3
  vendor_id	: GenuineIntel
  cpu family	: 6
  model		: 42
  model name	: Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz
  stepping	: 7
  cpu MHz		: 1600.000
  cache size	: 6144 KB
  physical id	: 0
  siblings	: 4
  core id		: 3
  cpu cores	: 4
  apicid		: 6
  initial apicid	: 6
  fdiv_bug	: no
  hlt_bug		: no
  f00f_bug	: no
  coma_bug	: no
  fpu		: yes
  fpu_exception	: yes
  cpuid level	: 13
  wp		: yes
  flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt aes xsave avx lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid
  bogomips	: 6585.00
  clflush size	: 64
  cache_alignment	: 64
  address sizes	: 36 bits physical, 48 bits virtual
  power management:
  
----- /proc/cpuinfo end -----
>> kbd.3: serial console
>> fb.1: read info
>> net.1: get network data
  net interface: name = lo, path = /class/net/lo
    type = 772
    carrier = 1
    hw_addr = 00:00:00:00:00:00
    GDRVINFO ethtool error: Operation not supported
  net interface: name = eth0, path = /class/net/eth0
    type = 1
    carrier = 1
    hw_addr = 00:16:0a:07:ad:dd
    net device: path = /devices/pci0000:00/0000:00:1c.4/0000:04:00.0/0000:05:01.0
    net driver: name = 8139too, path = /bus/pci/drivers/8139too
  net interface: name = tun0, path = /class/net/tun0
    type = 65534
    carrier = 1
    hw_addr = 
    ethtool driver: tun
    ethtool    bus: tun
>> net.2: eeprom dump
>> net.2: eeprom dump
>> net.2: eeprom dump
>> pppoe.1: looking for pppoe
>> pppoe.2: discovery
eth0: socket failed: Operation not permitted
>> wlan.1: detecting wlan features
>> wlan.2: assign udi
>> isdn.1: list
>> dsl.1: list
>> int.2: cdrom
>> int.3: media
>> int.4.1: /dev/sda
  read_block0: open(/dev/sda) failed
>> int.4: floppy
>> int.5: edd
>> int.5.1: bios
  bios ctrl 0: 25
>> int.6: mouse
>> int.15: system info
  system type:
  acpi: 1
>> int.7: hdb
>> int.7.1: modules
>> int.8: usbscsi
>> int.9: hotplug
>> int.10: modem
>> int.11: wlan
>> int.12: udev
-----  udevinfo -----
  P: /devices/LNXSYSTM:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00
  E: MODALIAS=acpi:LNXSYSTM:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXCPU:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXCPU:00
  E: DRIVER=processor
  E: MODALIAS=acpi:LNXCPU:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXCPU:01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXCPU:01
  E: DRIVER=processor
  E: MODALIAS=acpi:LNXCPU:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXCPU:02
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXCPU:02
  E: DRIVER=processor
  E: MODALIAS=acpi:LNXCPU:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXCPU:03
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXCPU:03
  E: DRIVER=processor
  E: MODALIAS=acpi:LNXCPU:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXPWRBN:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXPWRBN:00
  E: DRIVER=button
  E: MODALIAS=acpi:LNXPWRBN:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
  E: PRODUCT=19/0/1/0
  E: NAME="Power Button"
  E: PHYS="LNXPWRBN/button/input0"
  E: EV==3
  E: KEY==100000 0 0 0
  E: MODALIAS=input:b0019v0000p0001e0000-e0,1,k74,ramlsfw
  E: SUBSYSTEM=input
  
  P: /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1
  N: input/event1
  S: char/13:65
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1
  E: MAJOR=13
  E: MINOR=65
  E: DEVNAME=/dev/input/event1
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: DEVLINKS=/dev/char/13:65
  E: XKBLAYOUT=gb
  E: DMI_VENDOR=MSI
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00
  E: MODALIAS=acpi:LNXSYBUS:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00
  E: DRIVER=pci_root
  E: MODALIAS=acpi:PNP0A08:PNP0A03:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/INT3F0D:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/INT3F0D:00
  E: MODALIAS=acpi:INT3F0D:PNP0C02:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/PNP0103:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/PNP0103:00
  E: MODALIAS=acpi:PNP0103:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/PNP0C01:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/PNP0C01:00
  E: MODALIAS=acpi:PNP0C01:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/PNP0C01:01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/PNP0C01:01
  E: MODALIAS=acpi:PNP0C01:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/PNP0000:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/PNP0000:00
  E: MODALIAS=acpi:PNP0000:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/PNP0100:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/PNP0100:00
  E: MODALIAS=acpi:PNP0100:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/PNP0200:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/PNP0200:00
  E: MODALIAS=acpi:PNP0200:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/PNP0501:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/PNP0501:00
  E: MODALIAS=acpi:PNP0501:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/PNP0800:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/PNP0800:00
  E: MODALIAS=acpi:PNP0800:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/PNP0B00:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/PNP0B00:00
  E: MODALIAS=acpi:PNP0B00:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/PNP0C02:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/PNP0C02:00
  E: MODALIAS=acpi:PNP0C02:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/PNP0C02:01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/PNP0C02:01
  E: MODALIAS=acpi:PNP0C02:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/PNP0C04:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/PNP0C04:00
  E: MODALIAS=acpi:PNP0C04:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02/device:03
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02/device:03
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02/device:03/device:04
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02/device:03/device:04
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02/device:03/device:05
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02/device:03/device:05
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02/device:06
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02/device:06
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02/device:06/device:07
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02/device:06/device:07
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02/device:06/device:08
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02/device:06/device:08
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:09
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:09
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:09/device:0a
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:09/device:0a
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:09/device:0a/device:0b
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:09/device:0a/device:0b
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:09/device:0a/device:0c
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:09/device:0a/device:0c
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:09/device:0d
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:09/device:0d
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:09/device:0d/device:0e
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:09/device:0d/device:0e
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:09/device:0d/device:0f
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:09/device:0d/device:0f
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:10
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:10
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:11
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:11
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:11/device:12
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:11/device:12
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:11/device:12/device:13
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:11/device:12/device:13
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:11/device:12/device:13/device:14
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:11/device:12/device:13/device:14
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:11/device:12/device:13/device:15
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:11/device:12/device:13/device:15
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:11/device:12/device:13/device:16
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:11/device:12/device:13/device:16
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:11/device:12/device:13/device:17
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:11/device:12/device:13/device:17
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:11/device:12/device:13/device:18
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:11/device:12/device:13/device:18
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:11/device:12/device:13/device:19
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:11/device:12/device:13/device:19
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:11/device:12/device:13/device:1a
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:11/device:12/device:13/device:1a
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:11/device:12/device:13/device:1b
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:11/device:12/device:13/device:1b
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1c
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1c
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1c/device:1d
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1c/device:1d
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1c/device:1d/device:1e
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1c/device:1d/device:1e
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1c/device:1d/device:1e/device:1f
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1c/device:1d/device:1e/device:1f
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1c/device:1d/device:1e/device:20
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1c/device:1d/device:1e/device:20
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1c/device:1d/device:1e/device:21
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1c/device:1d/device:1e/device:21
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1c/device:1d/device:1e/device:22
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1c/device:1d/device:1e/device:22
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1c/device:1d/device:1e/device:23
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1c/device:1d/device:1e/device:23
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1c/device:1d/device:1e/device:24
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1c/device:1d/device:1e/device:24
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:25
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:25
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:26
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:26
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:27
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:27
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:28
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:28
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:29
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:29
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2a
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2a
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2b
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2b
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2c
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2c
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2d
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2d
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2e
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2e
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2f
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2f
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:30
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:30
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:31
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:31
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:32
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:32
  E: MODALIAS=acpi:device:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/pnp0c14:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/pnp0c14:00
  E: DRIVER=wmi
  E: MODALIAS=acpi:pnp0c14:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C01:02
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C01:02
  E: MODALIAS=acpi:PNP0C01:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00
  E: DRIVER=button
  E: MODALIAS=acpi:PNP0C0C:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
  E: PRODUCT=19/0/1/0
  E: NAME="Power Button"
  E: PHYS="PNP0C0C/button/input0"
  E: EV==3
  E: KEY==100000 0 0 0
  E: MODALIAS=input:b0019v0000p0001e0000-e0,1,k74,ramlsfw
  E: SUBSYSTEM=input
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0
  N: input/event0
  S: char/13:64
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0
  E: MAJOR=13
  E: MINOR=64
  E: DEVNAME=/dev/input/event0
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: DEVLINKS=/dev/char/13:64
  E: XKBLAYOUT=gb
  E: DMI_VENDOR=MSI
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0F:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0F:00
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0F:01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0F:01
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0F:02
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0F:02
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0F:03
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0F:03
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0F:04
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0F:04
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0F:05
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0F:05
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0F:06
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0F:06
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0F:07
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0F:07
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXTHERM:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXTHERM:00
  E: MODALIAS=acpi:LNXTHERM:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/PNP0C02:02
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/PNP0C02:02
  E: MODALIAS=acpi:PNP0C02:
  E: SUBSYSTEM=acpi
  
  P: /devices/pci0000:00/0000:00:00.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:00.0
  E: PCI_CLASS=60000
  E: PCI_ID=8086:0100
  E: PCI_SUBSYS_ID=1462:7681
  E: PCI_SLOT_NAME=0000:00:00.0
  E: MODALIAS=pci:v00008086d00000100sv00001462sd00007681bc06sc00i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:01.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:01.0
  E: DRIVER=pcieport
  E: PCI_CLASS=60400
  E: PCI_ID=8086:0101
  E: PCI_SUBSYS_ID=0000:0000
  E: PCI_SLOT_NAME=0000:00:01.0
  E: MODALIAS=pci:v00008086d00000101sv00000000sd00000000bc06sc04i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:01.0/0000:00:01.0:pcie01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:01.0/0000:00:01.0:pcie01
  E: SUBSYSTEM=pci_express
  
  P: /devices/pci0000:00/0000:00:01.0/0000:00:01.0:pcie08
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:01.0/0000:00:01.0:pcie08
  E: SUBSYSTEM=pci_express
  
  P: /devices/pci0000:00/0000:00:01.0/pci_bus/0000:01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:01.0/pci_bus/0000:01
  E: SUBSYSTEM=pci_bus
  
  P: /devices/pci0000:00/0000:00:01.1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:01.1
  E: DRIVER=pcieport
  E: PCI_CLASS=60400
  E: PCI_ID=8086:0105
  E: PCI_SUBSYS_ID=0000:0000
  E: PCI_SLOT_NAME=0000:00:01.1
  E: MODALIAS=pci:v00008086d00000105sv00000000sd00000000bc06sc04i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:01.1/0000:00:01.1:pcie01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:01.1/0000:00:01.1:pcie01
  E: SUBSYSTEM=pci_express
  
  P: /devices/pci0000:00/0000:00:01.1/0000:00:01.1:pcie08
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:01.1/0000:00:01.1:pcie08
  E: SUBSYSTEM=pci_express
  
  P: /devices/pci0000:00/0000:00:01.1/0000:02:00.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:01.1/0000:02:00.0
  E: DRIVER=nvidia
  E: PCI_CLASS=30000
  E: PCI_ID=10DE:1200
  E: PCI_SUBSYS_ID=1462:2382
  E: PCI_SLOT_NAME=0000:02:00.0
  E: MODALIAS=pci:v000010DEd00001200sv00001462sd00002382bc03sc00i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:01.1/0000:02:00.0/i2c-0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:01.1/0000:02:00.0/i2c-0
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:01.1/0000:02:00.0/i2c-1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:01.1/0000:02:00.0/i2c-1
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:01.1/0000:02:00.0/i2c-2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:01.1/0000:02:00.0/i2c-2
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:01.1/0000:02:00.0/i2c-3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:01.1/0000:02:00.0/i2c-3
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:01.1/0000:02:00.1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:01.1/0000:02:00.1
  E: PCI_CLASS=40300
  E: PCI_ID=10DE:0E0C
  E: PCI_SUBSYS_ID=1462:2382
  E: PCI_SLOT_NAME=0000:02:00.1
  E: MODALIAS=pci:v000010DEd00000E0Csv00001462sd00002382bc04sc03i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:01.1/pci_bus/0000:02
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:01.1/pci_bus/0000:02
  E: SUBSYSTEM=pci_bus
  
  P: /devices/pci0000:00/0000:00:16.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:16.0
  E: PCI_CLASS=78000
  E: PCI_ID=8086:1C3A
  E: PCI_SUBSYS_ID=1462:7673
  E: PCI_SLOT_NAME=0000:00:16.0
  E: MODALIAS=pci:v00008086d00001C3Asv00001462sd00007673bc07sc80i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1a.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0
  E: DRIVER=ehci_hcd
  E: PCI_CLASS=C0320
  E: PCI_ID=8086:1C2D
  E: PCI_SUBSYS_ID=1462:7673
  E: PCI_SLOT_NAME=0000:00:1a.0
  E: MODALIAS=pci:v00008086d00001C2Dsv00001462sd00007673bc0Csc03i20
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1a.0/usb1
  N: bus/usb/001/001
  S: char/189:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1
  E: MAJOR=189
  E: MINOR=0
  E: DEVNAME=/dev/bus/usb/001/001
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=1d6b/2/206
  E: TYPE=9/0/0
  E: BUSNUM=001
  E: DEVNUM=001
  E: SUBSYSTEM=usb
  E: ID_VENDOR=Linux_2.6.32-38-generic-pae_ehci_hcd
  E: ID_VENDOR_ENC=Linux\x202.6.32-38-generic-pae\x20ehci_hcd
  E: ID_VENDOR_ID=1d6b
  E: ID_MODEL=EHCI_Host_Controller
  E: ID_MODEL_ENC=EHCI\x20Host\x20Controller
  E: ID_MODEL_ID=0002
  E: ID_REVISION=0206
  E: ID_SERIAL=Linux_2.6.32-38-generic-pae_ehci_hcd_EHCI_Host_Controller_0000:00:1a.0
  E: ID_SERIAL_SHORT=0000:00:1a.0
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:090000:
  E: DEVLINKS=/dev/char/189:0
  
  P: /devices/pci0000:00/0000:00:1a.0/usb1/1-0:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-0:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=hub
  E: PRODUCT=1d6b/2/206
  E: TYPE=9/0/0
  E: INTERFACE=9/0/0
  E: MODALIAS=usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1
  N: bus/usb/001/002
  S: char/189:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1
  E: MAJOR=189
  E: MINOR=1
  E: DEVNAME=/dev/bus/usb/001/002
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=8087/24/0
  E: TYPE=9/0/1
  E: BUSNUM=001
  E: DEVNUM=002
  E: SUBSYSTEM=usb
  E: ID_VENDOR=8087
  E: ID_VENDOR_ENC=8087
  E: ID_VENDOR_ID=8087
  E: ID_MODEL=0024
  E: ID_MODEL_ENC=0024
  E: ID_MODEL_ID=0024
  E: ID_REVISION=0000
  E: ID_SERIAL=8087_0024
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:090000:
  E: DEVLINKS=/dev/char/189:1
  
  P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3
  N: bus/usb/001/003
  S: char/189:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3
  E: MAJOR=189
  E: MINOR=2
  E: DEVNAME=/dev/bus/usb/001/003
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=5e3/607/801
  E: TYPE=9/0/2
  E: BUSNUM=001
  E: DEVNUM=003
  E: SUBSYSTEM=usb
  E: ID_VENDOR=05e3
  E: ID_VENDOR_ENC=05e3
  E: ID_VENDOR_ID=05e3
  E: ID_MODEL=USB2.0_Hub
  E: ID_MODEL_ENC=USB2.0\x20Hub
  E: ID_MODEL_ID=0607
  E: ID_REVISION=0801
  E: ID_SERIAL=05e3_USB2.0_Hub
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:090001:090002:
  E: DEVLINKS=/dev/char/189:2
  
  P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1
  N: bus/usb/001/005
  S: char/189:4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1
  E: MAJOR=189
  E: MINOR=4
  E: DEVNAME=/dev/bus/usb/001/005
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=46d/c22b/100
  E: TYPE=0/0/0
  E: BUSNUM=001
  E: DEVNUM=005
  E: SUBSYSTEM=usb
  E: ID_VENDOR=LOGITECH
  E: ID_VENDOR_ENC=LOGITECH
  E: ID_VENDOR_ID=046d
  E: ID_MODEL=G110_G-keys
  E: ID_MODEL_ENC=G110\x20G-keys
  E: ID_MODEL_ID=c22b
  E: ID_REVISION=0100
  E: ID_SERIAL=LOGITECH_G110_G-keys
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:030101:030000:
  E: UPOWER_VENDOR=Logitech, Inc.
  E: DEVLINKS=/dev/char/189:4
  
  P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=usbhid
  E: PRODUCT=46d/c22b/100
  E: TYPE=0/0/0
  E: INTERFACE=3/1/1
  E: MODALIAS=usb:v046DpC22Bd0100dc00dsc00dp00ic03isc01ip01
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.0/0003:046D:C22B.0002
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.0/0003:046D:C22B.0002
  E: DRIVER=generic-usb
  E: HID_ID=0003:0000046D:0000C22B
  E: HID_NAME=LOGITECH G110 G-keys
  E: HID_PHYS=usb-0000:00:1a.0-1.3.1/input0
  E: MODALIAS=hid:b0003v0000046Dp0000C22B
  E: SUBSYSTEM=hid
  
  P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.0/0003:046D:C22B.0002/hidraw/hidraw1
  N: hidraw1
  S: char/251:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.0/0003:046D:C22B.0002/hidraw/hidraw1
  E: MAJOR=251
  E: MINOR=1
  E: DEVNAME=/dev/hidraw1
  E: SUBSYSTEM=hidraw
  E: DEVLINKS=/dev/char/251:1
  
  P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.0/input/input4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.0/input/input4
  E: PRODUCT=3/46d/c22b/100
  E: NAME="LOGITECH G110 G-keys"
  E: PHYS="usb-0000:00:1a.0-1.3.1/input0"
  E: UNIQ=""
  E: EV==100013
  E: KEY==10000 7 ff980000 7ff febeffdf ffefffff ffffffff fffffffe
  E: MSC==10
  E: MODALIAS=input:b0003v046DpC22Be0100-e0,1,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,lsfw
  E: SUBSYSTEM=input
  
  P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.0/input/input4/event4
  N: input/event4
  S: char/13:68
  S: input/by-id/usb-LOGITECH_G110_G-keys-event-kbd
  S: input/by-path/pci-0000:00:1a.0-usb-0:1.3.1:1.0-event-kbd
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.0/input/input4/event4
  E: MAJOR=13
  E: MINOR=68
  E: DEVNAME=/dev/input/event4
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: ID_INPUT_KEYBOARD=1
  E: ID_VENDOR=LOGITECH
  E: ID_VENDOR_ENC=LOGITECH
  E: ID_VENDOR_ID=046d
  E: ID_MODEL=G110_G-keys
  E: ID_MODEL_ENC=G110\x20G-keys
  E: ID_MODEL_ID=c22b
  E: ID_REVISION=0100
  E: ID_SERIAL=LOGITECH_G110_G-keys
  E: ID_TYPE=hid
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:030101:030000:
  E: ID_USB_INTERFACE_NUM=00
  E: ID_USB_DRIVER=usbhid
  E: ID_PATH=pci-0000:00:1a.0-usb-0:1.3.1:1.0
  E: DEVLINKS=/dev/char/13:68 /dev/input/by-id/usb-LOGITECH_G110_G-keys-event-kbd /dev/input/by-path/pci-0000:00:1a.0-usb-0:1.3.1:1.0-event-kbd
  E: XKBLAYOUT=gb
  
  P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.0/usb/hiddev1
  N: usb/hiddev1
  S: char/180:97
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.0/usb/hiddev1
  E: MAJOR=180
  E: MINOR=97
  E: DEVNAME=/dev/usb/hiddev1
  E: SUBSYSTEM=usb
  E: DEVLINKS=/dev/char/180:97
  
  P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.1
  E: DEVTYPE=usb_interface
  E: PRODUCT=46d/c22b/100
  E: TYPE=0/0/0
  E: INTERFACE=3/0/0
  E: MODALIAS=usb:v046DpC22Bd0100dc00dsc00dp00ic03isc00ip00
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3
  N: bus/usb/001/006
  S: char/189:5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3
  E: MAJOR=189
  E: MINOR=5
  E: DEVNAME=/dev/bus/usb/001/006
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=46d/c22a/100
  E: TYPE=0/0/0
  E: BUSNUM=001
  E: DEVNUM=006
  E: SUBSYSTEM=usb
  E: ID_VENDOR=046d
  E: ID_VENDOR_ENC=046d
  E: ID_VENDOR_ID=046d
  E: ID_MODEL=Gaming_Keyboard_G110
  E: ID_MODEL_ENC=Gaming\x20Keyboard\x20G110
  E: ID_MODEL_ID=c22a
  E: ID_REVISION=0100
  E: ID_SERIAL=046d_Gaming_Keyboard_G110
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:030101:030000:
  E: UPOWER_VENDOR=Logitech, Inc.
  E: DEVLINKS=/dev/char/189:5
  
  P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=usbhid
  E: PRODUCT=46d/c22a/100
  E: TYPE=0/0/0
  E: INTERFACE=3/1/1
  E: MODALIAS=usb:v046DpC22Ad0100dc00dsc00dp00ic03isc01ip01
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.0/0003:046D:C22A.0003
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.0/0003:046D:C22A.0003
  E: DRIVER=generic-usb
  E: HID_ID=0003:0000046D:0000C22A
  E: HID_NAME=Gaming Keyboard G110
  E: HID_PHYS=usb-0000:00:1a.0-1.3.3/input0
  E: MODALIAS=hid:b0003v0000046Dp0000C22A
  E: SUBSYSTEM=hid
  
  P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.0/0003:046D:C22A.0003/hidraw/hidraw2
  N: hidraw2
  S: char/251:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.0/0003:046D:C22A.0003/hidraw/hidraw2
  E: MAJOR=251
  E: MINOR=2
  E: DEVNAME=/dev/hidraw2
  E: SUBSYSTEM=hidraw
  E: DEVLINKS=/dev/char/251:2
  
  P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.0/input/input5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.0/input/input5
  E: PRODUCT=3/46d/c22a/110
  E: NAME="Gaming Keyboard G110"
  E: PHYS="usb-0000:00:1a.0-1.3.3/input0"
  E: UNIQ=""
  E: EV==120013
  E: KEY==10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
  E: MSC==10
  E: LED==1f
  E: MODALIAS=input:b0003v046DpC22Ae0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw
  E: SUBSYSTEM=input
  
  P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.0/input/input5/event5
  N: input/event5
  S: char/13:69
  S: input/by-id/usb-046d_Gaming_Keyboard_G110-event-kbd
  S: input/by-path/pci-0000:00:1a.0-usb-0:1.3.3:1.0-event-kbd
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.0/input/input5/event5
  E: MAJOR=13
  E: MINOR=69
  E: DEVNAME=/dev/input/event5
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: ID_INPUT_KEYBOARD=1
  E: ID_VENDOR=046d
  E: ID_VENDOR_ENC=046d
  E: ID_VENDOR_ID=046d
  E: ID_MODEL=Gaming_Keyboard_G110
  E: ID_MODEL_ENC=Gaming\x20Keyboard\x20G110
  E: ID_MODEL_ID=c22a
  E: ID_REVISION=0100
  E: ID_SERIAL=046d_Gaming_Keyboard_G110
  E: ID_TYPE=hid
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:030101:030000:
  E: ID_USB_INTERFACE_NUM=00
  E: ID_USB_DRIVER=usbhid
  E: ID_PATH=pci-0000:00:1a.0-usb-0:1.3.3:1.0
  E: DEVLINKS=/dev/char/13:69 /dev/input/by-id/usb-046d_Gaming_Keyboard_G110-event-kbd /dev/input/by-path/pci-0000:00:1a.0-usb-0:1.3.3:1.0-event-kbd
  E: XKBLAYOUT=gb
  
  P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.1
  E: DEVTYPE=usb_interface
  E: DRIVER=usbhid
  E: PRODUCT=46d/c22a/100
  E: TYPE=0/0/0
  E: INTERFACE=3/0/0
  E: MODALIAS=usb:v046DpC22Ad0100dc00dsc00dp00ic03isc00ip00
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.1/0003:046D:C22A.0004
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.1/0003:046D:C22A.0004
  E: DRIVER=generic-usb
  E: HID_ID=0003:0000046D:0000C22A
  E: HID_NAME=Gaming Keyboard G110
  E: HID_PHYS=usb-0000:00:1a.0-1.3.3/input1
  E: MODALIAS=hid:b0003v0000046Dp0000C22A
  E: SUBSYSTEM=hid
  
  P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.1/0003:046D:C22A.0004/hidraw/hidraw3
  N: hidraw3
  S: char/251:3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.1/0003:046D:C22A.0004/hidraw/hidraw3
  E: MAJOR=251
  E: MINOR=3
  E: DEVNAME=/dev/hidraw3
  E: SUBSYSTEM=hidraw
  E: DEVLINKS=/dev/char/251:3
  
  P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.1/input/input6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.1/input/input6
  E: PRODUCT=3/46d/c22a/110
  E: NAME="Gaming Keyboard G110"
  E: PHYS="usb-0000:00:1a.0-1.3.3/input1"
  E: UNIQ=""
  E: EV==13
  E: KEY==78 0 e0000 0 0 0
  E: MSC==10
  E: MODALIAS=input:b0003v046DpC22Ae0110-e0,1,4,k71,72,73,A3,A4,A5,A6,ram4,lsfw
  E: SUBSYSTEM=input
  
  P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.1/input/input6/event6
  N: input/event6
  S: char/13:70
  S: input/by-id/usb-046d_Gaming_Keyboard_G110-event-if01
  S: input/by-path/pci-0000:00:1a.0-usb-0:1.3.3:1.1-event
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.1/input/input6/event6
  E: MAJOR=13
  E: MINOR=70
  E: DEVNAME=/dev/input/event6
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: ID_VENDOR=046d
  E: ID_VENDOR_ENC=046d
  E: ID_VENDOR_ID=046d
  E: ID_MODEL=Gaming_Keyboard_G110
  E: ID_MODEL_ENC=Gaming\x20Keyboard\x20G110
  E: ID_MODEL_ID=c22a
  E: ID_REVISION=0100
  E: ID_SERIAL=046d_Gaming_Keyboard_G110
  E: ID_TYPE=hid
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:030101:030000:
  E: ID_USB_INTERFACE_NUM=01
  E: ID_USB_DRIVER=usbhid
  E: ID_PATH=pci-0000:00:1a.0-usb-0:1.3.3:1.1
  E: DEVLINKS=/dev/char/13:70 /dev/input/by-id/usb-046d_Gaming_Keyboard_G110-event-if01 /dev/input/by-path/pci-0000:00:1a.0-usb-0:1.3.3:1.1-event
  E: XKBLAYOUT=gb
  
  P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.1/usb/hiddev2
  N: usb/hiddev2
  S: char/180:98
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.1/usb/hiddev2
  E: MAJOR=180
  E: MINOR=98
  E: DEVNAME=/dev/usb/hiddev2
  E: SUBSYSTEM=usb
  E: DEVLINKS=/dev/char/180:98
  
  P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=hub
  E: PRODUCT=5e3/607/801
  E: TYPE=9/0/2
  E: INTERFACE=9/0/2
  E: MODALIAS=usb:v05E3p0607d0801dc09dsc00dp02ic09isc00ip02
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6
  N: bus/usb/001/004
  S: char/189:3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6
  E: MAJOR=189
  E: MINOR=3
  E: DEVNAME=/dev/bus/usb/001/004
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=4b4/121f/100
  E: TYPE=0/0/0
  E: BUSNUM=001
  E: DEVNUM=004
  E: SUBSYSTEM=usb
  E: ID_VENDOR=SteelSeries_ApS
  E: ID_VENDOR_ENC=SteelSeries\x20ApS
  E: ID_VENDOR_ID=04b4
  E: ID_MODEL=Ikari_Laser
  E: ID_MODEL_ENC=Ikari\x20Laser
  E: ID_MODEL_ID=121f
  E: ID_REVISION=0100
  E: ID_SERIAL=SteelSeries_ApS_Ikari_Laser
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:030102:
  E: DEVLINKS=/dev/char/189:3
  
  P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=usbhid
  E: PRODUCT=4b4/121f/100
  E: TYPE=0/0/0
  E: INTERFACE=3/1/2
  E: MODALIAS=usb:v04B4p121Fd0100dc00dsc00dp00ic03isc01ip02
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/0003:04B4:121F.0001
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/0003:04B4:121F.0001
  E: DRIVER=generic-usb
  E: HID_ID=0003:000004B4:0000121F
  E: HID_NAME=SteelSeries ApS Ikari Laser
  E: HID_PHYS=usb-0000:00:1a.0-1.6/input0
  E: MODALIAS=hid:b0003v000004B4p0000121F
  E: SUBSYSTEM=hid
  
  P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/0003:04B4:121F.0001/hidraw/hidraw0
  N: hidraw0
  S: char/251:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/0003:04B4:121F.0001/hidraw/hidraw0
  E: MAJOR=251
  E: MINOR=0
  E: DEVNAME=/dev/hidraw0
  E: SUBSYSTEM=hidraw
  E: DEVLINKS=/dev/char/251:0
  
  P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input3
  E: PRODUCT=3/4b4/121f/111
  E: NAME="SteelSeries ApS Ikari Laser"
  E: PHYS="usb-0000:00:1a.0-1.6/input0"
  E: UNIQ=""
  E: EV==120017
  E: KEY==7f0000 0 18000 68 c0010100 e08effdf 1cfffff ffffffff fffffffe
  E: REL==103
  E: MSC==10
  E: LED==1f
  E: MODALIAS=input:b0003v04B4p121Fe0111-e0,1,2,4,11,14,k71,72,73,77,7D,7E,7F,88,90,9E,9F,A3,A5,A6,CF,D0,110,111,112,113,114,115,116,r0,1,8,am4,l0,1,2,3,4,sfw
  E: SUBSYSTEM=input
  
  P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input3/event3
  N: input/event3
  S: char/13:67
  S: input/by-id/usb-SteelSeries_ApS_Ikari_Laser-event-mouse
  S: input/by-path/pci-0000:00:1a.0-usb-0:1.6:1.0-event-mouse
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input3/event3
  E: MAJOR=13
  E: MINOR=67
  E: DEVNAME=/dev/input/event3
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_MOUSE=1
  E: ID_INPUT_KEY=1
  E: ID_INPUT_KEYBOARD=1
  E: ID_VENDOR=SteelSeries_ApS
  E: ID_VENDOR_ENC=SteelSeries\x20ApS
  E: ID_VENDOR_ID=04b4
  E: ID_MODEL=Ikari_Laser
  E: ID_MODEL_ENC=Ikari\x20Laser
  E: ID_MODEL_ID=121f
  E: ID_REVISION=0100
  E: ID_SERIAL=SteelSeries_ApS_Ikari_Laser
  E: ID_TYPE=hid
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:030102:
  E: ID_USB_INTERFACE_NUM=00
  E: ID_USB_DRIVER=usbhid
  E: ID_PATH=pci-0000:00:1a.0-usb-0:1.6:1.0
  E: DEVLINKS=/dev/char/13:67 /dev/input/by-id/usb-SteelSeries_ApS_Ikari_Laser-event-mouse /dev/input/by-path/pci-0000:00:1a.0-usb-0:1.6:1.0-event-mouse
  E: XKBLAYOUT=gb
  
  P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input3/mouse1
  N: input/mouse1
  S: char/13:33
  S: input/by-id/usb-SteelSeries_ApS_Ikari_Laser-mouse
  S: input/by-path/pci-0000:00:1a.0-usb-0:1.6:1.0-mouse
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input3/mouse1
  E: MAJOR=13
  E: MINOR=33
  E: DEVNAME=/dev/input/mouse1
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_MOUSE=1
  E: ID_INPUT_KEY=1
  E: ID_INPUT_KEYBOARD=1
  E: ID_VENDOR=SteelSeries_ApS
  E: ID_VENDOR_ENC=SteelSeries\x20ApS
  E: ID_VENDOR_ID=04b4
  E: ID_MODEL=Ikari_Laser
  E: ID_MODEL_ENC=Ikari\x20Laser
  E: ID_MODEL_ID=121f
  E: ID_REVISION=0100
  E: ID_SERIAL=SteelSeries_ApS_Ikari_Laser
  E: ID_TYPE=hid
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:030102:
  E: ID_USB_INTERFACE_NUM=00
  E: ID_USB_DRIVER=usbhid
  E: ID_PATH=pci-0000:00:1a.0-usb-0:1.6:1.0
  E: DEVLINKS=/dev/char/13:33 /dev/input/by-id/usb-SteelSeries_ApS_Ikari_Laser-mouse /dev/input/by-path/pci-0000:00:1a.0-usb-0:1.6:1.0-mouse
  
  P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/usb/hiddev0
  N: usb/hiddev0
  S: char/180:96
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/usb/hiddev0
  E: MAJOR=180
  E: MINOR=96
  E: DEVNAME=/dev/usb/hiddev0
  E: SUBSYSTEM=usb
  E: DEVLINKS=/dev/char/180:96
  
  P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=hub
  E: PRODUCT=8087/24/0
  E: TYPE=9/0/1
  E: INTERFACE=9/0/0
  E: MODALIAS=usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1a.0/usbmon/usbmon1
  N: usbmon1
  S: char/252:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usbmon/usbmon1
  E: MAJOR=252
  E: MINOR=1
  E: DEVNAME=/dev/usbmon1
  E: SUBSYSTEM=usbmon
  E: DEVLINKS=/dev/char/252:1
  
  P: /devices/pci0000:00/0000:00:1b.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0
  E: DRIVER=HDA Intel
  E: PCI_CLASS=40300
  E: PCI_ID=8086:1C20
  E: PCI_SUBSYS_ID=1462:7673
  E: PCI_SLOT_NAME=0000:00:1b.0
  E: MODALIAS=pci:v00008086d00001C20sv00001462sd00007673bc04sc03i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0
  E: SUBSYSTEM=sound
  E: SOUND_INITIALIZED=1
  E: ID_VENDOR_FROM_DATABASE=Intel Corporation
  E: ID_MODEL_FROM_DATABASE=Cougar Point High Definition Audio Controller
  E: ID_BUS=pci
  E: ID_VENDOR_ID=0x8086
  E: ID_MODEL_ID=0x1c20
  E: ID_PATH=pci-0000:00:1b.0
  E: SOUND_FORM_FACTOR=internal
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/audio
  N: audio
  S: char/14:4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/audio
  E: MAJOR=14
  E: MINOR=4
  E: DEVNAME=/dev/audio
  E: SUBSYSTEM=sound
  E: ACL_MANAGE=1
  E: DEVLINKS=/dev/char/14:4
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/dsp
  N: dsp
  S: char/14:3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/dsp
  E: MAJOR=14
  E: MINOR=3
  E: DEVNAME=/dev/dsp
  E: SUBSYSTEM=sound
  E: ACL_MANAGE=1
  E: DEVLINKS=/dev/char/14:3
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D1
  N: snd/hwC0D1
  S: char/116:6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D1
  E: MAJOR=116
  E: MINOR=6
  E: DEVNAME=/dev/snd/hwC0D1
  E: SUBSYSTEM=sound
  E: ACL_MANAGE=1
  E: DEVLINKS=/dev/char/116:6
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/mixer
  N: mixer
  S: char/14:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/mixer
  E: MAJOR=14
  E: MINOR=0
  E: DEVNAME=/dev/mixer
  E: SUBSYSTEM=sound
  E: ACL_MANAGE=1
  E: DEVLINKS=/dev/char/14:0
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0c
  N: snd/pcmC0D0c
  S: char/116:5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0c
  E: MAJOR=116
  E: MINOR=5
  E: DEVNAME=/dev/snd/pcmC0D0c
  E: SUBSYSTEM=sound
  E: ACL_MANAGE=1
  E: DEVLINKS=/dev/char/116:5
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0p
  N: snd/pcmC0D0p
  S: char/116:4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0p
  E: MAJOR=116
  E: MINOR=4
  E: DEVNAME=/dev/snd/pcmC0D0p
  E: SUBSYSTEM=sound
  E: ACL_MANAGE=1
  E: DEVLINKS=/dev/char/116:4
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/controlC0
  N: snd/controlC0
  S: char/116:7
  S: snd/by-path/pci-0000:00:1b.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/controlC0
  E: MAJOR=116
  E: MINOR=7
  E: DEVNAME=/dev/snd/controlC0
  E: SUBSYSTEM=sound
  E: ID_PATH=pci-0000:00:1b.0
  E: ACL_MANAGE=1
  E: DEVLINKS=/dev/char/116:7 /dev/snd/by-path/pci-0000:00:1b.0
  
  P: /devices/pci0000:00/0000:00:1c.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.0
  E: DRIVER=pcieport
  E: PCI_CLASS=60400
  E: PCI_ID=8086:1C10
  E: PCI_SUBSYS_ID=0000:0000
  E: PCI_SLOT_NAME=0000:00:1c.0
  E: MODALIAS=pci:v00008086d00001C10sv00000000sd00000000bc06sc04i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1c.0/0000:00:1c.0:pcie01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:00:1c.0:pcie01
  E: SUBSYSTEM=pci_express
  
  P: /devices/pci0000:00/0000:00:1c.0/pci_bus/0000:03
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.0/pci_bus/0000:03
  E: SUBSYSTEM=pci_bus
  
  P: /devices/pci0000:00/0000:00:1c.4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.4
  E: PCI_CLASS=60401
  E: PCI_ID=8086:244E
  E: PCI_SUBSYS_ID=0000:0000
  E: PCI_SLOT_NAME=0000:00:1c.4
  E: MODALIAS=pci:v00008086d0000244Esv00000000sd00000000bc06sc04i01
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1c.4/0000:04:00.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.4/0000:04:00.0
  E: PCI_CLASS=60400
  E: PCI_ID=1B21:1080
  E: PCI_SUBSYS_ID=0000:0000
  E: PCI_SLOT_NAME=0000:04:00.0
  E: MODALIAS=pci:v00001B21d00001080sv00000000sd00000000bc06sc04i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1c.4/0000:04:00.0/0000:05:01.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/0000:05:01.0
  E: DRIVER=8139too
  E: PCI_CLASS=20000
  E: PCI_ID=10EC:8139
  E: PCI_SUBSYS_ID=10EC:8139
  E: PCI_SLOT_NAME=0000:05:01.0
  E: MODALIAS=pci:v000010ECd00008139sv000010ECsd00008139bc02sc00i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1c.4/0000:04:00.0/0000:05:01.0/net/eth0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/0000:05:01.0/net/eth0
  E: INTERFACE=eth0
  E: IFINDEX=2
  E: SUBSYSTEM=net
  E: ID_VENDOR_FROM_DATABASE=Realtek Semiconductor Co., Ltd.
  E: ID_MODEL_FROM_DATABASE=RTL-8139/8139C/8139C+
  E: ID_BUS=pci
  E: ID_VENDOR_ID=0x10ec
  E: ID_MODEL_ID=0x8139
  
  P: /devices/pci0000:00/0000:00:1c.4/0000:04:00.0/pci_bus/0000:05
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/pci_bus/0000:05
  E: SUBSYSTEM=pci_bus
  
  P: /devices/pci0000:00/0000:00:1c.4/pci_bus/0000:04
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.4/pci_bus/0000:04
  E: SUBSYSTEM=pci_bus
  
  P: /devices/pci0000:00/0000:00:1c.6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.6
  E: DRIVER=pcieport
  E: PCI_CLASS=60400
  E: PCI_ID=8086:1C1C
  E: PCI_SUBSYS_ID=0000:0000
  E: PCI_SLOT_NAME=0000:00:1c.6
  E: MODALIAS=pci:v00008086d00001C1Csv00000000sd00000000bc06sc04i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1c.6/0000:00:1c.6:pcie01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.6/0000:00:1c.6:pcie01
  E: SUBSYSTEM=pci_express
  
  P: /devices/pci0000:00/0000:00:1c.6/pci_bus/0000:06
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.6/pci_bus/0000:06
  E: SUBSYSTEM=pci_bus
  
  P: /devices/pci0000:00/0000:00:1c.7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.7
  E: DRIVER=pcieport
  E: PCI_CLASS=60400
  E: PCI_ID=8086:1C1E
  E: PCI_SUBSYS_ID=0000:0000
  E: PCI_SLOT_NAME=0000:00:1c.7
  E: MODALIAS=pci:v00008086d00001C1Esv00000000sd00000000bc06sc04i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1c.7/0000:00:1c.7:pcie01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.7/0000:00:1c.7:pcie01
  E: SUBSYSTEM=pci_express
  
  P: /devices/pci0000:00/0000:00:1c.7/0000:07:00.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.7/0000:07:00.0
  E: DRIVER=ohci1394
  E: PCI_CLASS=C0010
  E: PCI_ID=1106:3403
  E: PCI_SUBSYS_ID=1462:673D
  E: PCI_SLOT_NAME=0000:07:00.0
  E: MODALIAS=pci:v00001106d00003403sv00001462sd0000673Dbc0Csc00i10
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1c.7/0000:07:00.0/fw-host0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.7/0000:07:00.0/fw-host0
  E: DRIVER=nodemgr
  E: SUBSYSTEM=ieee1394
  
  P: /devices/pci0000:00/0000:00:1c.7/0000:07:00.0/fw-host0/0010dc0001cbe8ae
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.7/0000:07:00.0/fw-host0/0010dc0001cbe8ae
  E: SUBSYSTEM=ieee1394
  
  P: /devices/pci0000:00/0000:00:1c.7/0000:07:00.0/fw-host0/0010dc0001cbe8ae/ieee1394_node/0010dc0001cbe8ae
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.7/0000:07:00.0/fw-host0/0010dc0001cbe8ae/ieee1394_node/0010dc0001cbe8ae
  E: SUBSYSTEM=ieee1394_node
  
  P: /devices/pci0000:00/0000:00:1c.7/0000:07:00.0/fw-host0/ieee1394_host/fw-host0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.7/0000:07:00.0/fw-host0/ieee1394_host/fw-host0
  E: SUBSYSTEM=ieee1394_host
  
  P: /devices/pci0000:00/0000:00:1c.7/pci_bus/0000:07
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.7/pci_bus/0000:07
  E: SUBSYSTEM=pci_bus
  
  P: /devices/pci0000:00/0000:00:1d.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0
  E: DRIVER=ehci_hcd
  E: PCI_CLASS=C0320
  E: PCI_ID=8086:1C26
  E: PCI_SUBSYS_ID=1462:7673
  E: PCI_SLOT_NAME=0000:00:1d.0
  E: MODALIAS=pci:v00008086d00001C26sv00001462sd00007673bc0Csc03i20
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2
  N: bus/usb/002/001
  S: char/189:128
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2
  E: MAJOR=189
  E: MINOR=128
  E: DEVNAME=/dev/bus/usb/002/001
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=1d6b/2/206
  E: TYPE=9/0/0
  E: BUSNUM=002
  E: DEVNUM=001
  E: SUBSYSTEM=usb
  E: ID_VENDOR=Linux_2.6.32-38-generic-pae_ehci_hcd
  E: ID_VENDOR_ENC=Linux\x202.6.32-38-generic-pae\x20ehci_hcd
  E: ID_VENDOR_ID=1d6b
  E: ID_MODEL=EHCI_Host_Controller
  E: ID_MODEL_ENC=EHCI\x20Host\x20Controller
  E: ID_MODEL_ID=0002
  E: ID_REVISION=0206
  E: ID_SERIAL=Linux_2.6.32-38-generic-pae_ehci_hcd_EHCI_Host_Controller_0000:00:1d.0
  E: ID_SERIAL_SHORT=0000:00:1d.0
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:090000:
  E: DEVLINKS=/dev/char/189:128
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=hub
  E: PRODUCT=1d6b/2/206
  E: TYPE=9/0/0
  E: INTERFACE=9/0/0
  E: MODALIAS=usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1
  N: bus/usb/002/002
  S: char/189:129
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1
  E: MAJOR=189
  E: MINOR=129
  E: DEVNAME=/dev/bus/usb/002/002
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=8087/24/0
  E: TYPE=9/0/1
  E: BUSNUM=002
  E: DEVNUM=002
  E: SUBSYSTEM=usb
  E: ID_VENDOR=8087
  E: ID_VENDOR_ENC=8087
  E: ID_VENDOR_ID=8087
  E: ID_MODEL=0024
  E: ID_MODEL_ENC=0024
  E: ID_MODEL_ID=0024
  E: ID_REVISION=0000
  E: ID_SERIAL=8087_0024
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:090000:
  E: DEVLINKS=/dev/char/189:129
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5
  N: bus/usb/002/003
  S: char/189:130
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5
  E: MAJOR=189
  E: MINOR=130
  E: DEVNAME=/dev/bus/usb/002/003
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=3f0/9311/100
  E: TYPE=0/0/0
  E: BUSNUM=002
  E: DEVNUM=003
  E: SUBSYSTEM=usb
  E: ID_HPLIP=1
  E: ID_VENDOR=HP
  E: ID_VENDOR_ENC=HP
  E: ID_VENDOR_ID=03f0
  E: ID_MODEL=Deskjet_3050_J610_series
  E: ID_MODEL_ENC=Deskjet\x203050\x20J610\x20series
  E: ID_MODEL_ID=9311
  E: ID_REVISION=0100
  E: ID_SERIAL=HP_Deskjet_3050_J610_series_CN0BB3B48F05HX
  E: ID_SERIAL_SHORT=CN0BB3B48F05HX
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:ffcc00:070102:ff0401:
  E: ACL_MANAGE=1
  E: DEVLINKS=/dev/char/189:130
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0
  E: DEVTYPE=usb_interface
  E: PRODUCT=3f0/9311/100
  E: TYPE=0/0/0
  E: INTERFACE=255/204/0
  E: MODALIAS=usb:v03F0p9311d0100dc00dsc00dp00icFFiscCCip00
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.1
  E: DEVTYPE=usb_interface
  E: DRIVER=usblp
  E: PRODUCT=3f0/9311/100
  E: TYPE=0/0/0
  E: INTERFACE=7/1/2
  E: MODALIAS=usb:v03F0p9311d0100dc00dsc00dp00ic07isc01ip02
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.1/usb/lp0
  N: usb/lp0
  S: char/180:0
  S: usblp0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.1/usb/lp0
  E: MAJOR=180
  E: MINOR=0
  E: DEVNAME=/dev/usb/lp0
  E: SUBSYSTEM=usb
  E: DEVLINKS=/dev/char/180:0 /dev/usblp0
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.2
  E: DEVTYPE=usb_interface
  E: PRODUCT=3f0/9311/100
  E: TYPE=0/0/0
  E: INTERFACE=255/4/1
  E: MODALIAS=usb:v03F0p9311d0100dc00dsc00dp00icFFisc04ip01
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6
  N: bus/usb/002/004
  S: char/189:131
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6
  E: MAJOR=189
  E: MINOR=131
  E: DEVNAME=/dev/bus/usb/002/004
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=c45/62e0/100
  E: TYPE=239/2/1
  E: BUSNUM=002
  E: DEVNUM=004
  E: SUBSYSTEM=usb
  E: ID_VENDOR=Sonix_Technology_Co.__Ltd.
  E: ID_VENDOR_ENC=Sonix\x20Technology\x20Co.\x2c\x20Ltd.
  E: ID_VENDOR_ID=0c45
  E: ID_MODEL=USB_2.0_Camera
  E: ID_MODEL_ENC=USB\x202.0\x20Camera
  E: ID_MODEL_ID=62e0
  E: ID_REVISION=0100
  E: ID_SERIAL=Sonix_Technology_Co.__Ltd._USB_2.0_Camera
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:0e0100:0e0200:010100:010200:
  E: DEVLINKS=/dev/char/189:131
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=uvcvideo
  E: PRODUCT=c45/62e0/100
  E: TYPE=239/2/1
  E: INTERFACE=14/1/0
  E: MODALIAS=usb:v0C45p62E0d0100dcEFdsc02dp01ic0Eisc01ip00
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input7
  E: PRODUCT=3/c45/62e0/100
  E: NAME="USB 2.0 Camera"
  E: PHYS="usb-0000:00:1d.0-1.6/button"
  E: EV==3
  E: KEY==100000 0 0 0 0 0 0
  E: MODALIAS=input:b0003v0C45p62E0e0100-e0,1,kD4,ramlsfw
  E: SUBSYSTEM=input
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input7/event7
  N: input/event7
  S: char/13:71
  S: input/by-id/usb-Sonix_Technology_Co.__Ltd._USB_2.0_Camera-event-if00
  S: input/by-path/pci-0000:00:1d.0-usb-0:1.6:1.0-event
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input7/event7
  E: MAJOR=13
  E: MINOR=71
  E: DEVNAME=/dev/input/event7
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: ID_VENDOR=Sonix_Technology_Co.__Ltd.
  E: ID_VENDOR_ENC=Sonix\x20Technology\x20Co.\x2c\x20Ltd.
  E: ID_VENDOR_ID=0c45
  E: ID_MODEL=USB_2.0_Camera
  E: ID_MODEL_ENC=USB\x202.0\x20Camera
  E: ID_MODEL_ID=62e0
  E: ID_REVISION=0100
  E: ID_SERIAL=Sonix_Technology_Co.__Ltd._USB_2.0_Camera
  E: ID_TYPE=video
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:0e0100:0e0200:010100:010200:
  E: ID_USB_INTERFACE_NUM=00
  E: ID_USB_DRIVER=uvcvideo
  E: ID_PATH=pci-0000:00:1d.0-usb-0:1.6:1.0
  E: DEVLINKS=/dev/char/13:71 /dev/input/by-id/usb-Sonix_Technology_Co.__Ltd._USB_2.0_Camera-event-if00 /dev/input/by-path/pci-0000:00:1d.0-usb-0:1.6:1.0-event
  E: XKBLAYOUT=gb
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/video4linux/video0
  N: video0
  S: char/81:0
  S: v4l/by-id/usb-Sonix_Technology_Co.__Ltd._USB_2.0_Camera-video-index0
  S: v4l/by-path/pci-0000:00:1d.0-usb-0:1.6:1.0-video-index0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/video4linux/video0
  E: MAJOR=81
  E: MINOR=0
  E: DEVNAME=/dev/video0
  E: SUBSYSTEM=video4linux
  E: ID_V4L_VERSION=2
  E: ID_V4L_PRODUCT=USB 2.0 Camera
  E: ID_V4L_CAPABILITIES=:capture:
  E: ID_VENDOR=Sonix_Technology_Co.__Ltd.
  E: ID_VENDOR_ENC=Sonix\x20Technology\x20Co.\x2c\x20Ltd.
  E: ID_VENDOR_ID=0c45
  E: ID_MODEL=USB_2.0_Camera
  E: ID_MODEL_ENC=USB\x202.0\x20Camera
  E: ID_MODEL_ID=62e0
  E: ID_REVISION=0100
  E: ID_SERIAL=Sonix_Technology_Co.__Ltd._USB_2.0_Camera
  E: ID_TYPE=video
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:0e0100:0e0200:010100:010200:
  E: ID_USB_INTERFACE_NUM=00
  E: ID_USB_DRIVER=uvcvideo
  E: ID_PATH=pci-0000:00:1d.0-usb-0:1.6:1.0
  E: ACL_MANAGE=1
  E: DEVLINKS=/dev/char/81:0 /dev/v4l/by-id/usb-Sonix_Technology_Co.__Ltd._USB_2.0_Camera-video-index0 /dev/v4l/by-path/pci-0000:00:1d.0-usb-0:1.6:1.0-video-index0
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.1
  E: DEVTYPE=usb_interface
  E: DRIVER=uvcvideo
  E: PRODUCT=c45/62e0/100
  E: TYPE=239/2/1
  E: INTERFACE=14/2/0
  E: MODALIAS=usb:v0C45p62E0d0100dcEFdsc02dp01ic0Eisc02ip00
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2
  E: DEVTYPE=usb_interface
  E: DRIVER=snd-usb-audio
  E: PRODUCT=c45/62e0/100
  E: TYPE=239/2/1
  E: INTERFACE=1/1/0
  E: MODALIAS=usb:v0C45p62E0d0100dcEFdsc02dp01ic01isc01ip00
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/sound/card1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/sound/card1
  E: SUBSYSTEM=sound
  E: SOUND_INITIALIZED=1
  E: ID_VENDOR=Sonix_Technology_Co.__Ltd.
  E: ID_VENDOR_ENC=Sonix\x20Technology\x20Co.\x2c\x20Ltd.
  E: ID_VENDOR_ID=0c45
  E: ID_MODEL=USB_2.0_Camera
  E: ID_MODEL_ENC=USB\x202.0\x20Camera
  E: ID_MODEL_ID=62e0
  E: ID_REVISION=0100
  E: ID_SERIAL=Sonix_Technology_Co.__Ltd._USB_2.0_Camera
  E: ID_TYPE=audio
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:0e0100:0e0200:010100:010200:
  E: ID_USB_INTERFACE_NUM=02
  E: ID_USB_DRIVER=snd-usb-audio
  E: ID_VENDOR_FROM_DATABASE=Microdia
  E: ID_MODEL_FROM_DATABASE=MSI Starcam Racer
  E: ID_IFACE=02
  E: ID_ID=usb-Sonix_Technology_Co.__Ltd._USB_2.0_Camera-02-Camera
  E: ID_PATH=pci-0000:00:1d.0-usb-0:1.6:1.2
  E: SOUND_FORM_FACTOR=webcam
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/sound/card1/audio1
  N: audio1
  S: char/14:20
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/sound/card1/audio1
  E: MAJOR=14
  E: MINOR=20
  E: DEVNAME=/dev/audio1
  E: SUBSYSTEM=sound
  E: ACL_MANAGE=1
  E: DEVLINKS=/dev/char/14:20
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/sound/card1/dsp1
  N: dsp1
  S: char/14:19
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/sound/card1/dsp1
  E: MAJOR=14
  E: MINOR=19
  E: DEVNAME=/dev/dsp1
  E: SUBSYSTEM=sound
  E: ACL_MANAGE=1
  E: DEVLINKS=/dev/char/14:19
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/sound/card1/mixer1
  N: mixer1
  S: char/14:16
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/sound/card1/mixer1
  E: MAJOR=14
  E: MINOR=16
  E: DEVNAME=/dev/mixer1
  E: SUBSYSTEM=sound
  E: ACL_MANAGE=1
  E: DEVLINKS=/dev/char/14:16
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/sound/card1/pcmC1D0c
  N: snd/pcmC1D0c
  S: char/116:8
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/sound/card1/pcmC1D0c
  E: MAJOR=116
  E: MINOR=8
  E: DEVNAME=/dev/snd/pcmC1D0c
  E: SUBSYSTEM=sound
  E: ACL_MANAGE=1
  E: DEVLINKS=/dev/char/116:8
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/sound/card1/controlC1
  N: snd/controlC1
  S: char/116:9
  S: snd/by-id/usb-Sonix_Technology_Co.__Ltd._USB_2.0_Camera-02
  S: snd/by-path/pci-0000:00:1d.0-usb-0:1.6:1.2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/sound/card1/controlC1
  E: MAJOR=116
  E: MINOR=9
  E: DEVNAME=/dev/snd/controlC1
  E: SUBSYSTEM=sound
  E: ID_VENDOR=Sonix_Technology_Co.__Ltd.
  E: ID_VENDOR_ENC=Sonix\x20Technology\x20Co.\x2c\x20Ltd.
  E: ID_VENDOR_ID=0c45
  E: ID_MODEL=USB_2.0_Camera
  E: ID_MODEL_ENC=USB\x202.0\x20Camera
  E: ID_MODEL_ID=62e0
  E: ID_REVISION=0100
  E: ID_SERIAL=Sonix_Technology_Co.__Ltd._USB_2.0_Camera
  E: ID_TYPE=audio
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:0e0100:0e0200:010100:010200:
  E: ID_USB_INTERFACE_NUM=02
  E: ID_USB_DRIVER=snd-usb-audio
  E: ID_IFACE=02
  E: ID_PATH=pci-0000:00:1d.0-usb-0:1.6:1.2
  E: ACL_MANAGE=1
  E: DEVLINKS=/dev/char/116:9 /dev/snd/by-id/usb-Sonix_Technology_Co.__Ltd._USB_2.0_Camera-02 /dev/snd/by-path/pci-0000:00:1d.0-usb-0:1.6:1.2
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.3
  E: DEVTYPE=usb_interface
  E: DRIVER=snd-usb-audio
  E: PRODUCT=c45/62e0/100
  E: TYPE=239/2/1
  E: INTERFACE=1/2/0
  E: MODALIAS=usb:v0C45p62E0d0100dcEFdsc02dp01ic01isc02ip00
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=hub
  E: PRODUCT=8087/24/0
  E: TYPE=9/0/1
  E: INTERFACE=9/0/0
  E: MODALIAS=usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1d.0/usbmon/usbmon2
  N: usbmon2
  S: char/252:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usbmon/usbmon2
  E: MAJOR=252
  E: MINOR=2
  E: DEVNAME=/dev/usbmon2
  E: SUBSYSTEM=usbmon
  E: DEVLINKS=/dev/char/252:2
  
  P: /devices/pci0000:00/0000:00:1f.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.0
  E: PCI_CLASS=60100
  E: PCI_ID=8086:1C46
  E: PCI_SUBSYS_ID=1462:7673
  E: PCI_SLOT_NAME=0000:00:1f.0
  E: MODALIAS=pci:v00008086d00001C46sv00001462sd00007673bc06sc01i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1f.2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2
  E: DRIVER=ata_piix
  E: PCI_CLASS=1018A
  E: PCI_ID=8086:1C00
  E: PCI_SUBSYS_ID=1462:7673
  E: PCI_SLOT_NAME=0000:00:1f.2
  E: MODALIAS=pci:v00008086d00001C00sv00001462sd00007673bc01sc01i8a
  E: SUBSYSTEM=pci
  E: ID_VENDOR_FROM_DATABASE=Intel Corporation
  E: ID_MODEL_FROM_DATABASE=Cougar Point 4 port SATA IDE Controller
  
  P: /devices/pci0000:00/0000:00:1f.2/host0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0
  E: DEVTYPE=scsi_host
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1f.2/host0/scsi_host/host0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/scsi_host/host0
  E: SUBSYSTEM=scsi_host
  
  P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0
  E: DEVTYPE=scsi_target
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0
  E: DEVTYPE=scsi_device
  E: DRIVER=sr
  E: MODALIAS=scsi:t-0x05
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sr0
  N: sr0
  S: block/11:0
  S: scd0
  S: disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0
  S: cdrom
  S: cdrw
  S: dvd
  S: dvdrw
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sr0
  E: MAJOR=11
  E: MINOR=0
  E: DEVNAME=/dev/sr0
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: ID_CDROM=1
  E: ID_CDROM_CD=1
  E: ID_CDROM_CD_R=1
  E: ID_CDROM_CD_RW=1
  E: ID_CDROM_DVD=1
  E: ID_CDROM_DVD_R=1
  E: ID_CDROM_DVD_RW=1
  E: ID_CDROM_DVD_RAM=1
  E: ID_CDROM_DVD_PLUS_R=1
  E: ID_CDROM_DVD_PLUS_RW=1
  E: ID_CDROM_DVD_PLUS_R_DL=1
  E: ID_CDROM_MRW=1
  E: ID_CDROM_MRW_W=1
  E: ID_SCSI=1
  E: ID_VENDOR=ATAPI
  E: ID_VENDOR_ENC=ATAPI\x20\x20\x20
  E: ID_MODEL=iHAS124_B
  E: ID_MODEL_ENC=iHAS124\x20\x20\x20B\x20\x20\x20\x20\x20
  E: ID_REVISION=AL0Q
  E: ID_TYPE=cd
  E: ID_BUS=scsi
  E: ID_PATH=pci-0000:00:1f.2-scsi-0:0:0:0
  E: ACL_MANAGE=1
  E: GENERATED=1
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: DEVLINKS=/dev/block/11:0 /dev/scd0 /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0 /dev/cdrom /dev/cdrw /dev/dvd /dev/dvdrw
  
  P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/bsg/0:0:0:0
  N: bsg/0:0:0:0
  S: char/253:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/bsg/0:0:0:0
  E: MAJOR=253
  E: MINOR=0
  E: DEVNAME=/dev/bsg/0:0:0:0
  E: SUBSYSTEM=bsg
  E: DEVLINKS=/dev/char/253:0
  
  P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_device/0:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_device/0:0:0:0
  E: SUBSYSTEM=scsi_device
  
  P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_generic/sg0
  N: sg0
  S: char/21:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_generic/sg0
  E: MAJOR=21
  E: MINOR=0
  E: DEVNAME=/dev/sg0
  E: SUBSYSTEM=scsi_generic
  E: DEVLINKS=/dev/char/21:0
  
  P: /devices/pci0000:00/0000:00:1f.2/host1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1
  E: DEVTYPE=scsi_host
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1f.2/host1/scsi_host/host1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1/scsi_host/host1
  E: SUBSYSTEM=scsi_host
  
  P: /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0
  E: DEVTYPE=scsi_target
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0
  E: DEVTYPE=scsi_device
  E: DRIVER=sd
  E: MODALIAS=scsi:t-0x00
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sda
  N: sda
  W: 53
  S: block/8:0
  S: disk/by-id/ata-WDC_WD5000AAKX-001CA0_WD-WCAYUR040248
  S: disk/by-id/scsi-SATA_WDC_WD5000AAKX-_WD-WCAYUR040248
  S: disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0
  S: disk/by-id/wwn-0x50014ee1ae9d87ac
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sda
  E: MAJOR=8
  E: MINOR=0
  E: DEVNAME=/dev/sda
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: ID_ATA=1
  E: ID_TYPE=disk
  E: ID_BUS=ata
  E: ID_MODEL=WDC_WD5000AAKX-001CA0
  E: ID_MODEL_ENC=WDC\x20WD5000AAKX-001CA0\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
  E: ID_REVISION=15.01H51
  E: ID_SERIAL=WDC_WD5000AAKX-001CA0_WD-WCAYUR040248
  E: ID_SERIAL_SHORT=WD-WCAYUR040248
  E: ID_ATA_WRITE_CACHE=1
  E: ID_ATA_WRITE_CACHE_ENABLED=1
  E: ID_ATA_FEATURE_SET_HPA=1
  E: ID_ATA_FEATURE_SET_HPA_ENABLED=1
  E: ID_ATA_FEATURE_SET_PM=1
  E: ID_ATA_FEATURE_SET_PM_ENABLED=1
  E: ID_ATA_FEATURE_SET_SECURITY=1
  E: ID_ATA_FEATURE_SET_SECURITY_ENABLED=0
  E: ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=88
  E: ID_ATA_FEATURE_SET_SECURITY_ENHANCED_ERASE_UNIT_MIN=88
  E: ID_ATA_FEATURE_SET_SECURITY_FROZEN=1
  E: ID_ATA_FEATURE_SET_SMART=1
  E: ID_ATA_FEATURE_SET_SMART_ENABLED=1
  E: ID_ATA_FEATURE_SET_PUIS=1
  E: ID_ATA_FEATURE_SET_PUIS_ENABLED=0
  E: ID_ATA_DOWNLOAD_MICROCODE=1
  E: ID_ATA_SATA=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN2=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
  E: ID_WWN=0x50014ee1ae9d87ac
  E: ID_WWN_WITH_EXTENSION=0x50014ee1ae9d87ac
  E: ID_SCSI_COMPAT=SATA_WDC_WD5000AAKX-_WD-WCAYUR040248
  E: ID_PATH=pci-0000:00:1f.2-scsi-1:0:0:0
  E: ID_PART_TABLE_TYPE=dos
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: UDISKS_PARTITION_TABLE=1
  E: UDISKS_PARTITION_TABLE_SCHEME=mbr
  E: UDISKS_PARTITION_TABLE_COUNT=5
  E: UDISKS_ATA_SMART_IS_AVAILABLE=1
  E: DEVLINKS=/dev/block/8:0 /dev/disk/by-id/ata-WDC_WD5000AAKX-001CA0_WD-WCAYUR040248 /dev/disk/by-id/scsi-SATA_WDC_WD5000AAKX-_WD-WCAYUR040248 /dev/disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0 /dev/disk/by-id/wwn-0x50014ee1ae9d87ac
  
  P: /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sda/sda1
  N: sda1
  W: 57
  S: block/8:1
  S: disk/by-id/ata-WDC_WD5000AAKX-001CA0_WD-WCAYUR040248-part1
  S: disk/by-id/scsi-SATA_WDC_WD5000AAKX-_WD-WCAYUR040248-part1
  S: disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0-part1
  S: disk/by-uuid/60C2F3B7C2F39010
  S: disk/by-label/System\x20Reserved
  S: disk/by-id/wwn-0x50014ee1ae9d87ac-part1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sda/sda1
  E: MAJOR=8
  E: MINOR=1
  E: DEVNAME=/dev/sda1
  E: DEVTYPE=partition
  E: SUBSYSTEM=block
  E: ID_ATA=1
  E: ID_TYPE=disk
  E: ID_BUS=ata
  E: ID_MODEL=WDC_WD5000AAKX-001CA0
  E: ID_MODEL_ENC=WDC\x20WD5000AAKX-001CA0\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
  E: ID_REVISION=15.01H51
  E: ID_SERIAL=WDC_WD5000AAKX-001CA0_WD-WCAYUR040248
  E: ID_SERIAL_SHORT=WD-WCAYUR040248
  E: ID_ATA_WRITE_CACHE=1
  E: ID_ATA_WRITE_CACHE_ENABLED=1
  E: ID_ATA_FEATURE_SET_HPA=1
  E: ID_ATA_FEATURE_SET_HPA_ENABLED=1
  E: ID_ATA_FEATURE_SET_PM=1
  E: ID_ATA_FEATURE_SET_PM_ENABLED=1
  E: ID_ATA_FEATURE_SET_SECURITY=1
  E: ID_ATA_FEATURE_SET_SECURITY_ENABLED=0
  E: ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=88
  E: ID_ATA_FEATURE_SET_SECURITY_ENHANCED_ERASE_UNIT_MIN=88
  E: ID_ATA_FEATURE_SET_SECURITY_FROZEN=1
  E: ID_ATA_FEATURE_SET_SMART=1
  E: ID_ATA_FEATURE_SET_SMART_ENABLED=1
  E: ID_ATA_FEATURE_SET_PUIS=1
  E: ID_ATA_FEATURE_SET_PUIS_ENABLED=0
  E: ID_ATA_DOWNLOAD_MICROCODE=1
  E: ID_ATA_SATA=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN2=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
  E: ID_WWN=0x50014ee1ae9d87ac
  E: ID_WWN_WITH_EXTENSION=0x50014ee1ae9d87ac
  E: ID_SCSI_COMPAT=SATA_WDC_WD5000AAKX-_WD-WCAYUR040248
  E: ID_PATH=pci-0000:00:1f.2-scsi-1:0:0:0
  E: ID_PART_TABLE_TYPE=dos
  E: ID_FS_LABEL=System_Reserved
  E: ID_FS_LABEL_ENC=System\x20Reserved
  E: ID_FS_UUID=60C2F3B7C2F39010
  E: ID_FS_UUID_ENC=60C2F3B7C2F39010
  E: ID_FS_TYPE=ntfs
  E: ID_FS_USAGE=filesystem
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: UDISKS_PARTITION=1
  E: UDISKS_PARTITION_SCHEME=mbr
  E: UDISKS_PARTITION_NUMBER=1
  E: UDISKS_PARTITION_TYPE=0x07
  E: UDISKS_PARTITION_SIZE=104857600
  E: UDISKS_PARTITION_FLAGS=boot
  E: UDISKS_PARTITION_SLAVE=/sys/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sda
  E: UDISKS_PARTITION_OFFSET=1048576
  E: UDISKS_PARTITION_ALIGNMENT_OFFSET=0
  E: DEVLINKS=/dev/block/8:1 /dev/disk/by-id/ata-WDC_WD5000AAKX-001CA0_WD-WCAYUR040248-part1 /dev/disk/by-id/scsi-SATA_WDC_WD5000AAKX-_WD-WCAYUR040248-part1 /dev/disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0-part1 /dev/disk/by-uuid/60C2F3B7C2F39010 /dev/disk/by-label/System\x20Reserved /dev/disk/by-id/wwn-0x50014ee1ae9d87ac-part1
  
  P: /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sda/sda2
  N: sda2
  W: 58
  S: block/8:2
  S: disk/by-id/ata-WDC_WD5000AAKX-001CA0_WD-WCAYUR040248-part2
  S: disk/by-id/scsi-SATA_WDC_WD5000AAKX-_WD-WCAYUR040248-part2
  S: disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0-part2
  S: disk/by-uuid/142CF4E82CF4C5B0
  S: disk/by-id/wwn-0x50014ee1ae9d87ac-part2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sda/sda2
  E: MAJOR=8
  E: MINOR=2
  E: DEVNAME=/dev/sda2
  E: DEVTYPE=partition
  E: SUBSYSTEM=block
  E: ID_ATA=1
  E: ID_TYPE=disk
  E: ID_BUS=ata
  E: ID_MODEL=WDC_WD5000AAKX-001CA0
  E: ID_MODEL_ENC=WDC\x20WD5000AAKX-001CA0\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
  E: ID_REVISION=15.01H51
  E: ID_SERIAL=WDC_WD5000AAKX-001CA0_WD-WCAYUR040248
  E: ID_SERIAL_SHORT=WD-WCAYUR040248
  E: ID_ATA_WRITE_CACHE=1
  E: ID_ATA_WRITE_CACHE_ENABLED=1
  E: ID_ATA_FEATURE_SET_HPA=1
  E: ID_ATA_FEATURE_SET_HPA_ENABLED=1
  E: ID_ATA_FEATURE_SET_PM=1
  E: ID_ATA_FEATURE_SET_PM_ENABLED=1
  E: ID_ATA_FEATURE_SET_SECURITY=1
  E: ID_ATA_FEATURE_SET_SECURITY_ENABLED=0
  E: ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=88
  E: ID_ATA_FEATURE_SET_SECURITY_ENHANCED_ERASE_UNIT_MIN=88
  E: ID_ATA_FEATURE_SET_SECURITY_FROZEN=1
  E: ID_ATA_FEATURE_SET_SMART=1
  E: ID_ATA_FEATURE_SET_SMART_ENABLED=1
  E: ID_ATA_FEATURE_SET_PUIS=1
  E: ID_ATA_FEATURE_SET_PUIS_ENABLED=0
  E: ID_ATA_DOWNLOAD_MICROCODE=1
  E: ID_ATA_SATA=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN2=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
  E: ID_WWN=0x50014ee1ae9d87ac
  E: ID_WWN_WITH_EXTENSION=0x50014ee1ae9d87ac
  E: ID_SCSI_COMPAT=SATA_WDC_WD5000AAKX-_WD-WCAYUR040248
  E: ID_PATH=pci-0000:00:1f.2-scsi-1:0:0:0
  E: ID_PART_TABLE_TYPE=dos
  E: ID_FS_UUID=142CF4E82CF4C5B0
  E: ID_FS_UUID_ENC=142CF4E82CF4C5B0
  E: ID_FS_TYPE=ntfs
  E: ID_FS_USAGE=filesystem
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: UDISKS_PARTITION=1
  E: UDISKS_PARTITION_SCHEME=mbr
  E: UDISKS_PARTITION_NUMBER=2
  E: UDISKS_PARTITION_TYPE=0x07
  E: UDISKS_PARTITION_SIZE=404975452160
  E: UDISKS_PARTITION_SLAVE=/sys/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sda
  E: UDISKS_PARTITION_OFFSET=105906176
  E: UDISKS_PARTITION_ALIGNMENT_OFFSET=0
  E: DEVLINKS=/dev/block/8:2 /dev/disk/by-id/ata-WDC_WD5000AAKX-001CA0_WD-WCAYUR040248-part2 /dev/disk/by-id/scsi-SATA_WDC_WD5000AAKX-_WD-WCAYUR040248-part2 /dev/disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0-part2 /dev/disk/by-uuid/142CF4E82CF4C5B0 /dev/disk/by-id/wwn-0x50014ee1ae9d87ac-part2
  
  P: /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sda/sda3
  N: sda3
  W: 56
  S: block/8:3
  S: disk/by-id/ata-WDC_WD5000AAKX-001CA0_WD-WCAYUR040248-part3
  S: disk/by-id/scsi-SATA_WDC_WD5000AAKX-_WD-WCAYUR040248-part3
  S: disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0-part3
  S: disk/by-id/wwn-0x50014ee1ae9d87ac-part3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sda/sda3
  E: MAJOR=8
  E: MINOR=3
  E: DEVNAME=/dev/sda3
  E: DEVTYPE=partition
  E: SUBSYSTEM=block
  E: ID_ATA=1
  E: ID_TYPE=disk
  E: ID_BUS=ata
  E: ID_MODEL=WDC_WD5000AAKX-001CA0
  E: ID_MODEL_ENC=WDC\x20WD5000AAKX-001CA0\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
  E: ID_REVISION=15.01H51
  E: ID_SERIAL=WDC_WD5000AAKX-001CA0_WD-WCAYUR040248
  E: ID_SERIAL_SHORT=WD-WCAYUR040248
  E: ID_ATA_WRITE_CACHE=1
  E: ID_ATA_WRITE_CACHE_ENABLED=1
  E: ID_ATA_FEATURE_SET_HPA=1
  E: ID_ATA_FEATURE_SET_HPA_ENABLED=1
  E: ID_ATA_FEATURE_SET_PM=1
  E: ID_ATA_FEATURE_SET_PM_ENABLED=1
  E: ID_ATA_FEATURE_SET_SECURITY=1
  E: ID_ATA_FEATURE_SET_SECURITY_ENABLED=0
  E: ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=88
  E: ID_ATA_FEATURE_SET_SECURITY_ENHANCED_ERASE_UNIT_MIN=88
  E: ID_ATA_FEATURE_SET_SECURITY_FROZEN=1
  E: ID_ATA_FEATURE_SET_SMART=1
  E: ID_ATA_FEATURE_SET_SMART_ENABLED=1
  E: ID_ATA_FEATURE_SET_PUIS=1
  E: ID_ATA_FEATURE_SET_PUIS_ENABLED=0
  E: ID_ATA_DOWNLOAD_MICROCODE=1
  E: ID_ATA_SATA=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN2=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
  E: ID_WWN=0x50014ee1ae9d87ac
  E: ID_WWN_WITH_EXTENSION=0x50014ee1ae9d87ac
  E: ID_SCSI_COMPAT=SATA_WDC_WD5000AAKX-_WD-WCAYUR040248
  E: ID_PATH=pci-0000:00:1f.2-scsi-1:0:0:0
  E: ID_PART_TABLE_TYPE=dos
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: UDISKS_PARTITION=1
  E: UDISKS_PARTITION_SCHEME=mbr
  E: UDISKS_PARTITION_NUMBER=3
  E: UDISKS_PARTITION_TYPE=0x05
  E: UDISKS_PARTITION_SIZE=95025103872
  E: UDISKS_PARTITION_SLAVE=/sys/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sda
  E: UDISKS_PARTITION_OFFSET=405081684992
  E: UDISKS_PARTITION_ALIGNMENT_OFFSET=0
  E: DEVLINKS=/dev/block/8:3 /dev/disk/by-id/ata-WDC_WD5000AAKX-001CA0_WD-WCAYUR040248-part3 /dev/disk/by-id/scsi-SATA_WDC_WD5000AAKX-_WD-WCAYUR040248-part3 /dev/disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0-part3 /dev/disk/by-id/wwn-0x50014ee1ae9d87ac-part3
  
  P: /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sda/sda5
  N: sda5
  W: 62
  S: block/8:5
  S: disk/by-id/ata-WDC_WD5000AAKX-001CA0_WD-WCAYUR040248-part5
  S: disk/by-id/scsi-SATA_WDC_WD5000AAKX-_WD-WCAYUR040248-part5
  S: disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0-part5
  S: disk/by-uuid/5de13091-a2a0-467d-a3af-577c9da25d1f
  S: disk/by-id/wwn-0x50014ee1ae9d87ac-part5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sda/sda5
  E: MAJOR=8
  E: MINOR=5
  E: DEVNAME=/dev/sda5
  E: DEVTYPE=partition
  E: SUBSYSTEM=block
  E: ID_ATA=1
  E: ID_TYPE=disk
  E: ID_BUS=ata
  E: ID_MODEL=WDC_WD5000AAKX-001CA0
  E: ID_MODEL_ENC=WDC\x20WD5000AAKX-001CA0\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
  E: ID_REVISION=15.01H51
  E: ID_SERIAL=WDC_WD5000AAKX-001CA0_WD-WCAYUR040248
  E: ID_SERIAL_SHORT=WD-WCAYUR040248
  E: ID_ATA_WRITE_CACHE=1
  E: ID_ATA_WRITE_CACHE_ENABLED=1
  E: ID_ATA_FEATURE_SET_HPA=1
  E: ID_ATA_FEATURE_SET_HPA_ENABLED=1
  E: ID_ATA_FEATURE_SET_PM=1
  E: ID_ATA_FEATURE_SET_PM_ENABLED=1
  E: ID_ATA_FEATURE_SET_SECURITY=1
  E: ID_ATA_FEATURE_SET_SECURITY_ENABLED=0
  E: ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=88
  E: ID_ATA_FEATURE_SET_SECURITY_ENHANCED_ERASE_UNIT_MIN=88
  E: ID_ATA_FEATURE_SET_SECURITY_FROZEN=1
  E: ID_ATA_FEATURE_SET_SMART=1
  E: ID_ATA_FEATURE_SET_SMART_ENABLED=1
  E: ID_ATA_FEATURE_SET_PUIS=1
  E: ID_ATA_FEATURE_SET_PUIS_ENABLED=0
  E: ID_ATA_DOWNLOAD_MICROCODE=1
  E: ID_ATA_SATA=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN2=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
  E: ID_WWN=0x50014ee1ae9d87ac
  E: ID_WWN_WITH_EXTENSION=0x50014ee1ae9d87ac
  E: ID_SCSI_COMPAT=SATA_WDC_WD5000AAKX-_WD-WCAYUR040248
  E: ID_PATH=pci-0000:00:1f.2-scsi-1:0:0:0
  E: ID_PART_TABLE_TYPE=dos
  E: ID_FS_UUID=5de13091-a2a0-467d-a3af-577c9da25d1f
  E: ID_FS_UUID_ENC=5de13091-a2a0-467d-a3af-577c9da25d1f
  E: ID_FS_VERSION=1.0
  E: ID_FS_TYPE=ext4
  E: ID_FS_USAGE=filesystem
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: UDISKS_PARTITION=1
  E: UDISKS_PARTITION_SCHEME=mbr
  E: UDISKS_PARTITION_NUMBER=5
  E: UDISKS_PARTITION_TYPE=0x83
  E: UDISKS_PARTITION_SIZE=268435456
  E: UDISKS_PARTITION_SLAVE=/sys/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sda
  E: UDISKS_PARTITION_OFFSET=405082733568
  E: UDISKS_PARTITION_ALIGNMENT_OFFSET=0
  E: DEVLINKS=/dev/block/8:5 /dev/disk/by-id/ata-WDC_WD5000AAKX-001CA0_WD-WCAYUR040248-part5 /dev/disk/by-id/scsi-SATA_WDC_WD5000AAKX-_WD-WCAYUR040248-part5 /dev/disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0-part5 /dev/disk/by-uuid/5de13091-a2a0-467d-a3af-577c9da25d1f /dev/disk/by-id/wwn-0x50014ee1ae9d87ac-part5
  
  P: /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sda/sda6
  N: sda6
  W: 54
  S: block/8:6
  S: disk/by-id/ata-WDC_WD5000AAKX-001CA0_WD-WCAYUR040248-part6
  S: disk/by-id/scsi-SATA_WDC_WD5000AAKX-_WD-WCAYUR040248-part6
  S: disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0-part6
  S: disk/by-uuid/1d541567-4b9a-441b-b8ac-c449be714fb0
  S: disk/by-id/wwn-0x50014ee1ae9d87ac-part6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sda/sda6
  E: MAJOR=8
  E: MINOR=6
  E: DEVNAME=/dev/sda6
  E: DEVTYPE=partition
  E: SUBSYSTEM=block
  E: ID_ATA=1
  E: ID_TYPE=disk
  E: ID_BUS=ata
  E: ID_MODEL=WDC_WD5000AAKX-001CA0
  E: ID_MODEL_ENC=WDC\x20WD5000AAKX-001CA0\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
  E: ID_REVISION=15.01H51
  E: ID_SERIAL=WDC_WD5000AAKX-001CA0_WD-WCAYUR040248
  E: ID_SERIAL_SHORT=WD-WCAYUR040248
  E: ID_ATA_WRITE_CACHE=1
  E: ID_ATA_WRITE_CACHE_ENABLED=1
  E: ID_ATA_FEATURE_SET_HPA=1
  E: ID_ATA_FEATURE_SET_HPA_ENABLED=1
  E: ID_ATA_FEATURE_SET_PM=1
  E: ID_ATA_FEATURE_SET_PM_ENABLED=1
  E: ID_ATA_FEATURE_SET_SECURITY=1
  E: ID_ATA_FEATURE_SET_SECURITY_ENABLED=0
  E: ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=88
  E: ID_ATA_FEATURE_SET_SECURITY_ENHANCED_ERASE_UNIT_MIN=88
  E: ID_ATA_FEATURE_SET_SECURITY_FROZEN=1
  E: ID_ATA_FEATURE_SET_SMART=1
  E: ID_ATA_FEATURE_SET_SMART_ENABLED=1
  E: ID_ATA_FEATURE_SET_PUIS=1
  E: ID_ATA_FEATURE_SET_PUIS_ENABLED=0
  E: ID_ATA_DOWNLOAD_MICROCODE=1
  E: ID_ATA_SATA=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN2=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
  E: ID_WWN=0x50014ee1ae9d87ac
  E: ID_WWN_WITH_EXTENSION=0x50014ee1ae9d87ac
  E: ID_SCSI_COMPAT=SATA_WDC_WD5000AAKX-_WD-WCAYUR040248
  E: ID_PATH=pci-0000:00:1f.2-scsi-1:0:0:0
  E: ID_PART_TABLE_TYPE=dos
  E: ID_FS_UUID=1d541567-4b9a-441b-b8ac-c449be714fb0
  E: ID_FS_UUID_ENC=1d541567-4b9a-441b-b8ac-c449be714fb0
  E: ID_FS_VERSION=256
  E: ID_FS_TYPE=crypto_LUKS
  E: ID_FS_USAGE=crypto
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: UDISKS_PARTITION=1
  E: UDISKS_PARTITION_SCHEME=mbr
  E: UDISKS_PARTITION_NUMBER=6
  E: UDISKS_PARTITION_TYPE=0x83
  E: UDISKS_PARTITION_SIZE=94754571264
  E: UDISKS_PARTITION_SLAVE=/sys/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sda
  E: UDISKS_PARTITION_OFFSET=405352217600
  E: UDISKS_PARTITION_ALIGNMENT_OFFSET=0
  E: DEVLINKS=/dev/block/8:6 /dev/disk/by-id/ata-WDC_WD5000AAKX-001CA0_WD-WCAYUR040248-part6 /dev/disk/by-id/scsi-SATA_WDC_WD5000AAKX-_WD-WCAYUR040248-part6 /dev/disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0-part6 /dev/disk/by-uuid/1d541567-4b9a-441b-b8ac-c449be714fb0 /dev/disk/by-id/wwn-0x50014ee1ae9d87ac-part6
  
  P: /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/bsg/1:0:0:0
  N: bsg/1:0:0:0
  S: char/253:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/bsg/1:0:0:0
  E: MAJOR=253
  E: MINOR=1
  E: DEVNAME=/dev/bsg/1:0:0:0
  E: SUBSYSTEM=bsg
  E: DEVLINKS=/dev/char/253:1
  
  P: /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/scsi_device/1:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/scsi_device/1:0:0:0
  E: SUBSYSTEM=scsi_device
  
  P: /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/scsi_disk/1:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/scsi_disk/1:0:0:0
  E: SUBSYSTEM=scsi_disk
  
  P: /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/scsi_generic/sg1
  N: sg1
  S: char/21:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/scsi_generic/sg1
  E: MAJOR=21
  E: MINOR=1
  E: DEVNAME=/dev/sg1
  E: SUBSYSTEM=scsi_generic
  E: DEVLINKS=/dev/char/21:1
  
  P: /devices/pci0000:00/0000:00:1f.3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.3
  E: PCI_CLASS=C0500
  E: PCI_ID=8086:1C22
  E: PCI_SUBSYS_ID=1462:7673
  E: PCI_SLOT_NAME=0000:00:1f.3
  E: MODALIAS=pci:v00008086d00001C22sv00001462sd00007673bc0Csc05i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1f.5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.5
  E: DRIVER=ata_piix
  E: PCI_CLASS=10185
  E: PCI_ID=8086:1C08
  E: PCI_SUBSYS_ID=1462:7673
  E: PCI_SLOT_NAME=0000:00:1f.5
  E: MODALIAS=pci:v00008086d00001C08sv00001462sd00007673bc01sc01i85
  E: SUBSYSTEM=pci
  E: ID_VENDOR_FROM_DATABASE=Intel Corporation
  E: ID_MODEL_FROM_DATABASE=Cougar Point 2 port SATA IDE Controller
  
  P: /devices/pci0000:00/0000:00:1f.5/host2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.5/host2
  E: DEVTYPE=scsi_host
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1f.5/host2/scsi_host/host2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.5/host2/scsi_host/host2
  E: SUBSYSTEM=scsi_host
  
  P: /devices/pci0000:00/0000:00:1f.5/host3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.5/host3
  E: DEVTYPE=scsi_host
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1f.5/host3/scsi_host/host3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.5/host3/scsi_host/host3
  E: SUBSYSTEM=scsi_host
  
  P: /devices/pci0000:00/pci_bus/0000:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/pci_bus/0000:00
  E: SUBSYSTEM=pci_bus
  
  P: /devices/platform/Fixed MDIO bus.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/Fixed MDIO bus.0
  E: MODALIAS=platform:Fixed MDIO bus
  E: SUBSYSTEM=platform
  
  P: /devices/platform/Fixed MDIO bus.0/mdio_bus/0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/Fixed MDIO bus.0/mdio_bus/0
  E: SUBSYSTEM=mdio_bus
  
  P: /devices/platform/eisa.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/eisa.0
  E: MODALIAS=platform:eisa
  E: SUBSYSTEM=platform
  
  P: /devices/platform/i8042
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/i8042
  E: DRIVER=i8042
  E: MODALIAS=platform:i8042
  E: SUBSYSTEM=platform
  
  P: /devices/platform/i8042/serio0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/i8042/serio0
  E: SERIO_TYPE=06
  E: SERIO_PROTO=00
  E: SERIO_ID=00
  E: SERIO_EXTRA=00
  E: MODALIAS=serio:ty06pr00id00ex00
  E: SUBSYSTEM=serio
  
  P: /devices/platform/i8042/serio1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/i8042/serio1
  E: SERIO_TYPE=01
  E: SERIO_PROTO=00
  E: SERIO_ID=00
  E: SERIO_EXTRA=00
  E: MODALIAS=serio:ty01pr00id00ex00
  E: SUBSYSTEM=serio
  
  P: /devices/platform/pcspkr
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/pcspkr
  E: MODALIAS=platform:pcspkr
  E: SUBSYSTEM=platform
  
  P: /devices/platform/serial8250
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250
  E: DRIVER=serial8250
  E: MODALIAS=platform:serial8250
  E: SUBSYSTEM=platform
  
  P: /devices/platform/serial8250/tty/ttyS1
  N: ttyS1
  S: char/4:65
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS1
  E: MAJOR=4
  E: MINOR=65
  E: DEVNAME=/dev/ttyS1
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:65
  
  P: /devices/platform/serial8250/tty/ttyS2
  N: ttyS2
  S: char/4:66
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS2
  E: MAJOR=4
  E: MINOR=66
  E: DEVNAME=/dev/ttyS2
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:66
  
  P: /devices/platform/serial8250/tty/ttyS3
  N: ttyS3
  S: char/4:67
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS3
  E: MAJOR=4
  E: MINOR=67
  E: DEVNAME=/dev/ttyS3
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:67
  
  P: /devices/platform/vga16fb.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/vga16fb.0
  E: DRIVER=vga16fb
  E: MODALIAS=platform:vga16fb
  E: SUBSYSTEM=platform
  
  P: /devices/platform/vga16fb.0/graphics/fb0
  N: fb0
  S: char/29:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/vga16fb.0/graphics/fb0
  E: MAJOR=29
  E: MINOR=0
  E: DEVNAME=/dev/fb0
  E: SUBSYSTEM=graphics
  E: PRIMARY_DEVICE_FOR_DISPLAY=1
  E: DEVLINKS=/dev/char/29:0
  
  P: /devices/pnp0/00:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:00
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:01
  E: DRIVER=system
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:02
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:02
  E: DRIVER=system
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:03
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:03
  E: DRIVER=serial
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:03/tty/ttyS0
  N: ttyS0
  S: char/4:64
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:03/tty/ttyS0
  E: MAJOR=4
  E: MINOR=64
  E: DEVNAME=/dev/ttyS0
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:64
  
  P: /devices/pnp0/00:04
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:04
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:05
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:05
  E: DRIVER=rtc_cmos
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:05/rtc/rtc0
  N: rtc0
  S: char/254:0
  S: rtc
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:05/rtc/rtc0
  E: MAJOR=254
  E: MINOR=0
  E: DEVNAME=/dev/rtc0
  E: SUBSYSTEM=rtc
  E: DEVLINKS=/dev/char/254:0 /dev/rtc
  
  P: /devices/pnp0/00:06
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:06
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:07
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:07
  E: DRIVER=system
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:08
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:08
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:09
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:09
  E: DRIVER=system
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:0a
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:0a
  E: DRIVER=system
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:0b
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:0b
  E: SUBSYSTEM=pnp
  
  P: /devices/virtual/bdi/0:21
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/0:21
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/11:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/11:0
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:0
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:1
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:10
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:10
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:11
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:11
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:12
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:12
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:13
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:13
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:14
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:14
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:15
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:15
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:2
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:3
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:4
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:5
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:6
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:7
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:8
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:8
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:9
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:9
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/251:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/251:0
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/251:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/251:1
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/251:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/251:2
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:0
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:1
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:2
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:3
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:4
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:5
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:6
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:7
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/8:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/8:0
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/default
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/default
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/block/loop0
  N: loop0
  W: 35
  S: block/7:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop0
  E: MAJOR=7
  E: MINOR=0
  E: DEVNAME=/dev/loop0
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: UDISKS_PRESENTATION_NOPOLICY=1
  E: DEVLINKS=/dev/block/7:0
  
  P: /devices/virtual/block/loop1
  N: loop1
  W: 36
  S: block/7:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop1
  E: MAJOR=7
  E: MINOR=1
  E: DEVNAME=/dev/loop1
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: UDISKS_PRESENTATION_NOPOLICY=1
  E: DEVLINKS=/dev/block/7:1
  
  P: /devices/virtual/block/loop2
  N: loop2
  W: 50
  S: block/7:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop2
  E: MAJOR=7
  E: MINOR=2
  E: DEVNAME=/dev/loop2
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: UDISKS_PRESENTATION_NOPOLICY=1
  E: DEVLINKS=/dev/block/7:2
  
  P: /devices/virtual/block/loop3
  N: loop3
  W: 49
  S: block/7:3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop3
  E: MAJOR=7
  E: MINOR=3
  E: DEVNAME=/dev/loop3
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: UDISKS_PRESENTATION_NOPOLICY=1
  E: DEVLINKS=/dev/block/7:3
  
  P: /devices/virtual/block/loop4
  N: loop4
  W: 29
  S: block/7:4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop4
  E: MAJOR=7
  E: MINOR=4
  E: DEVNAME=/dev/loop4
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: UDISKS_PRESENTATION_NOPOLICY=1
  E: DEVLINKS=/dev/block/7:4
  
  P: /devices/virtual/block/loop5
  N: loop5
  W: 28
  S: block/7:5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop5
  E: MAJOR=7
  E: MINOR=5
  E: DEVNAME=/dev/loop5
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: UDISKS_PRESENTATION_NOPOLICY=1
  E: DEVLINKS=/dev/block/7:5
  
  P: /devices/virtual/block/loop6
  N: loop6
  W: 51
  S: block/7:6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop6
  E: MAJOR=7
  E: MINOR=6
  E: DEVNAME=/dev/loop6
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: UDISKS_PRESENTATION_NOPOLICY=1
  E: DEVLINKS=/dev/block/7:6
  
  P: /devices/virtual/block/loop7
  N: loop7
  W: 34
  S: block/7:7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop7
  E: MAJOR=7
  E: MINOR=7
  E: DEVNAME=/dev/loop7
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: UDISKS_PRESENTATION_NOPOLICY=1
  E: DEVLINKS=/dev/block/7:7
  
  P: /devices/virtual/block/ram0
  N: ram0
  W: 38
  S: block/1:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram0
  E: MAJOR=1
  E: MINOR=0
  E: DEVNAME=/dev/ram0
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: DEVLINKS=/dev/block/1:0
  
  P: /devices/virtual/block/ram1
  N: ram1
  W: 32
  S: block/1:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram1
  E: MAJOR=1
  E: MINOR=1
  E: DEVNAME=/dev/ram1
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: DEVLINKS=/dev/block/1:1
  
  P: /devices/virtual/block/ram10
  N: ram10
  W: 30
  S: block/1:10
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram10
  E: MAJOR=1
  E: MINOR=10
  E: DEVNAME=/dev/ram10
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: DEVLINKS=/dev/block/1:10
  
  P: /devices/virtual/block/ram11
  N: ram11
  W: 33
  S: block/1:11
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram11
  E: MAJOR=1
  E: MINOR=11
  E: DEVNAME=/dev/ram11
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: DEVLINKS=/dev/block/1:11
  
  P: /devices/virtual/block/ram12
  N: ram12
  W: 39
  S: block/1:12
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram12
  E: MAJOR=1
  E: MINOR=12
  E: DEVNAME=/dev/ram12
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: DEVLINKS=/dev/block/1:12
  
  P: /devices/virtual/block/ram13
  N: ram13
  W: 48
  S: block/1:13
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram13
  E: MAJOR=1
  E: MINOR=13
  E: DEVNAME=/dev/ram13
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: DEVLINKS=/dev/block/1:13
  
  P: /devices/virtual/block/ram14
  N: ram14
  W: 37
  S: block/1:14
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram14
  E: MAJOR=1
  E: MINOR=14
  E: DEVNAME=/dev/ram14
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: DEVLINKS=/dev/block/1:14
  
  P: /devices/virtual/block/ram15
  N: ram15
  W: 44
  S: block/1:15
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram15
  E: MAJOR=1
  E: MINOR=15
  E: DEVNAME=/dev/ram15
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: DEVLINKS=/dev/block/1:15
  
  P: /devices/virtual/block/ram2
  N: ram2
  W: 40
  S: block/1:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram2
  E: MAJOR=1
  E: MINOR=2
  E: DEVNAME=/dev/ram2
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: DEVLINKS=/dev/block/1:2
  
  P: /devices/virtual/block/ram3
  N: ram3
  W: 46
  S: block/1:3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram3
  E: MAJOR=1
  E: MINOR=3
  E: DEVNAME=/dev/ram3
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: DEVLINKS=/dev/block/1:3
  
  P: /devices/virtual/block/ram4
  N: ram4
  W: 47
  S: block/1:4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram4
  E: MAJOR=1
  E: MINOR=4
  E: DEVNAME=/dev/ram4
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: DEVLINKS=/dev/block/1:4
  
  P: /devices/virtual/block/ram5
  N: ram5
  W: 31
  S: block/1:5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram5
  E: MAJOR=1
  E: MINOR=5
  E: DEVNAME=/dev/ram5
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: DEVLINKS=/dev/block/1:5
  
  P: /devices/virtual/block/ram6
  N: ram6
  W: 41
  S: block/1:6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram6
  E: MAJOR=1
  E: MINOR=6
  E: DEVNAME=/dev/ram6
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: DEVLINKS=/dev/block/1:6
  
  P: /devices/virtual/block/ram7
  N: ram7
  W: 42
  S: block/1:7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram7
  E: MAJOR=1
  E: MINOR=7
  E: DEVNAME=/dev/ram7
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: DEVLINKS=/dev/block/1:7
  
  P: /devices/virtual/block/ram8
  N: ram8
  W: 43
  S: block/1:8
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram8
  E: MAJOR=1
  E: MINOR=8
  E: DEVNAME=/dev/ram8
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: DEVLINKS=/dev/block/1:8
  
  P: /devices/virtual/block/ram9
  N: ram9
  W: 45
  S: block/1:9
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram9
  E: MAJOR=1
  E: MINOR=9
  E: DEVNAME=/dev/ram9
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: DEVLINKS=/dev/block/1:9
  
  P: /devices/virtual/dmi/id
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/dmi/id
  E: MODALIAS=dmi:bvnAmericanMegatrendsInc.:bvrV1.8:bd02/14/2011:svnMSI:pnMS-7673:pvr2.0:rvnMSI:rnP67A-G45(MS-7673):rvr2.0:cvnMSI:ct3:cvr2.0:
  E: SUBSYSTEM=dmi
  
  P: /devices/virtual/drm/ttm
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/drm/ttm
  E: DEVTYPE=ttm
  E: SUBSYSTEM=drm
  
  P: /devices/virtual/graphics/fbcon
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/graphics/fbcon
  E: SUBSYSTEM=graphics
  
  P: /devices/virtual/input/input2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/input/input2
  E: PRODUCT=17/1/1/100
  E: NAME="Macintosh mouse button emulation"
  E: EV==7
  E: KEY==70000 0 0 0 0 0 0 0 0
  E: REL==3
  E: MODALIAS=input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw
  E: SUBSYSTEM=input
  
  P: /devices/virtual/input/input2/event2
  N: input/event2
  S: char/13:66
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/input/input2/event2
  E: MAJOR=13
  E: MINOR=66
  E: DEVNAME=/dev/input/event2
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_MOUSE=1
  E: ID_SERIAL=noserial
  E: DMI_VENDOR=MSI
  E: DEVLINKS=/dev/char/13:66
  
  P: /devices/virtual/input/input2/mouse0
  N: input/mouse0
  S: char/13:32
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/input/input2/mouse0
  E: MAJOR=13
  E: MINOR=32
  E: DEVNAME=/dev/input/mouse0
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_MOUSE=1
  E: ID_SERIAL=noserial
  E: DEVLINKS=/dev/char/13:32
  
  P: /devices/virtual/input/mice
  N: input/mice
  S: char/13:63
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/input/mice
  E: MAJOR=13
  E: MINOR=63
  E: DEVNAME=/dev/input/mice
  E: SUBSYSTEM=input
  E: DEVLINKS=/dev/char/13:63
  
  P: /devices/virtual/mem/full
  N: full
  S: char/1:7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/full
  E: MAJOR=1
  E: MINOR=7
  E: DEVNAME=/dev/full
  E: DEVMODE=0666
  E: SUBSYSTEM=mem
  E: DEVLINKS=/dev/char/1:7
  
  P: /devices/virtual/mem/kmsg
  N: kmsg
  S: char/1:11
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/kmsg
  E: MAJOR=1
  E: MINOR=11
  E: DEVNAME=/dev/kmsg
  E: SUBSYSTEM=mem
  E: DEVLINKS=/dev/char/1:11
  
  P: /devices/virtual/mem/mem
  N: mem
  S: char/1:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/mem
  E: MAJOR=1
  E: MINOR=1
  E: DEVNAME=/dev/mem
  E: SUBSYSTEM=mem
  E: DEVLINKS=/dev/char/1:1
  
  P: /devices/virtual/mem/null
  N: null
  S: char/1:3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/null
  E: MAJOR=1
  E: MINOR=3
  E: DEVNAME=/dev/null
  E: DEVMODE=0666
  E: SUBSYSTEM=mem
  E: DEVLINKS=/dev/char/1:3
  
  P: /devices/virtual/mem/oldmem
  N: oldmem
  S: char/1:12
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/oldmem
  E: MAJOR=1
  E: MINOR=12
  E: DEVNAME=/dev/oldmem
  E: SUBSYSTEM=mem
  E: DEVLINKS=/dev/char/1:12
  
  P: /devices/virtual/mem/port
  N: port
  S: char/1:4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/port
  E: MAJOR=1
  E: MINOR=4
  E: DEVNAME=/dev/port
  E: SUBSYSTEM=mem
  E: DEVLINKS=/dev/char/1:4
  
  P: /devices/virtual/mem/random
  N: random
  S: char/1:8
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/random
  E: MAJOR=1
  E: MINOR=8
  E: DEVNAME=/dev/random
  E: DEVMODE=0666
  E: SUBSYSTEM=mem
  E: DEVLINKS=/dev/char/1:8
  
  P: /devices/virtual/mem/urandom
  N: urandom
  S: char/1:9
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/urandom
  E: MAJOR=1
  E: MINOR=9
  E: DEVNAME=/dev/urandom
  E: DEVMODE=0666
  E: SUBSYSTEM=mem
  E: DEVLINKS=/dev/char/1:9
  
  P: /devices/virtual/mem/zero
  N: zero
  S: char/1:5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/zero
  E: MAJOR=1
  E: MINOR=5
  E: DEVNAME=/dev/zero
  E: DEVMODE=0666
  E: SUBSYSTEM=mem
  E: DEVLINKS=/dev/char/1:5
  
  P: /devices/virtual/misc/cpu_dma_latency
  N: cpu_dma_latency
  S: char/10:58
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/cpu_dma_latency
  E: MAJOR=10
  E: MINOR=58
  E: DEVNAME=/dev/cpu_dma_latency
  E: SUBSYSTEM=misc
  E: DEVLINKS=/dev/char/10:58
  
  P: /devices/virtual/misc/device-mapper
  N: mapper/control
  S: char/10:59
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/device-mapper
  E: MAJOR=10
  E: MINOR=59
  E: DEVNAME=/dev/mapper/control
  E: SUBSYSTEM=misc
  E: DEVLINKS=/dev/char/10:59
  
  P: /devices/virtual/misc/ecryptfs
  N: ecryptfs
  S: char/10:61
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/ecryptfs
  E: MAJOR=10
  E: MINOR=61
  E: DEVNAME=/dev/ecryptfs
  E: SUBSYSTEM=misc
  E: DEVLINKS=/dev/char/10:61
  
  P: /devices/virtual/misc/fuse
  N: fuse
  S: char/10:229
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/fuse
  E: MAJOR=10
  E: MINOR=229
  E: DEVNAME=/dev/fuse
  E: SUBSYSTEM=misc
  E: DEVLINKS=/dev/char/10:229
  
  P: /devices/virtual/misc/hpet
  N: hpet
  S: char/10:228
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/hpet
  E: MAJOR=10
  E: MINOR=228
  E: DEVNAME=/dev/hpet
  E: SUBSYSTEM=misc
  E: DEVLINKS=/dev/char/10:228
  
  P: /devices/virtual/misc/mcelog
  N: mcelog
  S: char/10:227
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/mcelog
  E: MAJOR=10
  E: MINOR=227
  E: DEVNAME=/dev/mcelog
  E: SUBSYSTEM=misc
  E: DEVLINKS=/dev/char/10:227
  
  P: /devices/virtual/misc/network_latency
  N: network_latency
  S: char/10:57
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/network_latency
  E: MAJOR=10
  E: MINOR=57
  E: DEVNAME=/dev/network_latency
  E: SUBSYSTEM=misc
  E: DEVLINKS=/dev/char/10:57
  
  P: /devices/virtual/misc/network_throughput
  N: network_throughput
  S: char/10:56
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/network_throughput
  E: MAJOR=10
  E: MINOR=56
  E: DEVNAME=/dev/network_throughput
  E: SUBSYSTEM=misc
  E: DEVLINKS=/dev/char/10:56
  
  P: /devices/virtual/misc/pktcdvd
  N: pktcdvd/control
  S: char/10:60
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/pktcdvd
  E: MAJOR=10
  E: MINOR=60
  E: DEVNAME=/dev/pktcdvd/control
  E: SUBSYSTEM=misc
  E: DEVLINKS=/dev/char/10:60
  
  P: /devices/virtual/misc/psaux
  N: psaux
  S: char/10:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/psaux
  E: MAJOR=10
  E: MINOR=1
  E: DEVNAME=/dev/psaux
  E: SUBSYSTEM=misc
  E: DEVLINKS=/dev/char/10:1
  
  P: /devices/virtual/misc/rfkill
  N: rfkill
  S: char/10:62
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/rfkill
  E: MAJOR=10
  E: MINOR=62
  E: DEVNAME=/dev/rfkill
  E: SUBSYSTEM=misc
  E: ACL_MANAGE=1
  E: DEVLINKS=/dev/char/10:62
  
  P: /devices/virtual/misc/snapshot
  N: snapshot
  S: char/10:231
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/snapshot
  E: MAJOR=10
  E: MINOR=231
  E: DEVNAME=/dev/snapshot
  E: SUBSYSTEM=misc
  E: DEVLINKS=/dev/char/10:231
  
  P: /devices/virtual/misc/tun
  N: net/tun
  S: char/10:200
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/tun
  E: MAJOR=10
  E: MINOR=200
  E: DEVNAME=/dev/net/tun
  E: SUBSYSTEM=misc
  E: DEVLINKS=/dev/char/10:200
  
  P: /devices/virtual/misc/vga_arbiter
  N: vga_arbiter
  S: char/10:63
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/vga_arbiter
  E: MAJOR=10
  E: MINOR=63
  E: DEVNAME=/dev/vga_arbiter
  E: SUBSYSTEM=misc
  E: DEVLINKS=/dev/char/10:63
  
  P: /devices/virtual/net/lo
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/net/lo
  E: INTERFACE=lo
  E: IFINDEX=1
  E: SUBSYSTEM=net
  
  P: /devices/virtual/net/tun0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/net/tun0
  E: INTERFACE=tun0
  E: IFINDEX=4
  E: SUBSYSTEM=net
  
  P: /devices/virtual/ppp/ppp
  N: ppp
  S: char/108:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/ppp/ppp
  E: MAJOR=108
  E: MINOR=0
  E: DEVNAME=/dev/ppp
  E: SUBSYSTEM=ppp
  E: DEVLINKS=/dev/char/108:0
  
  P: /devices/virtual/sound/seq
  N: snd/seq
  S: char/116:3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/sound/seq
  E: MAJOR=116
  E: MINOR=3
  E: DEVNAME=/dev/snd/seq
  E: SUBSYSTEM=sound
  E: ACL_MANAGE=1
  E: DEVLINKS=/dev/char/116:3
  
  P: /devices/virtual/sound/sequencer
  N: sequencer
  S: char/14:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/sound/sequencer
  E: MAJOR=14
  E: MINOR=1
  E: DEVNAME=/dev/sequencer
  E: SUBSYSTEM=sound
  E: ACL_MANAGE=1
  E: DEVLINKS=/dev/char/14:1
  
  P: /devices/virtual/sound/sequencer2
  N: sequencer2
  S: char/14:8
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/sound/sequencer2
  E: MAJOR=14
  E: MINOR=8
  E: DEVNAME=/dev/sequencer2
  E: SUBSYSTEM=sound
  E: ACL_MANAGE=1
  E: DEVLINKS=/dev/char/14:8
  
  P: /devices/virtual/sound/timer
  N: snd/timer
  S: char/116:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/sound/timer
  E: MAJOR=116
  E: MINOR=2
  E: DEVNAME=/dev/snd/timer
  E: SUBSYSTEM=sound
  E: ACL_MANAGE=1
  E: DEVLINKS=/dev/char/116:2
  
  P: /devices/virtual/thermal/cooling_device0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/thermal/cooling_device0
  E: SUBSYSTEM=thermal
  
  P: /devices/virtual/thermal/cooling_device1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/thermal/cooling_device1
  E: SUBSYSTEM=thermal
  
  P: /devices/virtual/thermal/cooling_device2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/thermal/cooling_device2
  E: SUBSYSTEM=thermal
  
  P: /devices/virtual/thermal/cooling_device3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/thermal/cooling_device3
  E: SUBSYSTEM=thermal
  
  P: /devices/virtual/tty/console
  N: console
  S: char/5:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/console
  E: MAJOR=5
  E: MINOR=1
  E: DEVNAME=/dev/console
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/5:1
  
  P: /devices/virtual/tty/ptmx
  N: ptmx
  S: char/5:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/ptmx
  E: MAJOR=5
  E: MINOR=2
  E: DEVNAME=/dev/ptmx
  E: DEVMODE=0666
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/5:2
  
  P: /devices/virtual/tty/tty
  N: tty
  S: char/5:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty
  E: MAJOR=5
  E: MINOR=0
  E: DEVNAME=/dev/tty
  E: DEVMODE=0666
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/5:0
  
  P: /devices/virtual/tty/tty0
  N: tty0
  S: char/4:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty0
  E: MAJOR=4
  E: MINOR=0
  E: DEVNAME=/dev/tty0
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:0
  
  P: /devices/virtual/tty/tty1
  N: tty1
  S: char/4:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty1
  E: MAJOR=4
  E: MINOR=1
  E: DEVNAME=/dev/tty1
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:1
  
  P: /devices/virtual/tty/tty10
  N: tty10
  S: char/4:10
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty10
  E: MAJOR=4
  E: MINOR=10
  E: DEVNAME=/dev/tty10
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:10
  
  P: /devices/virtual/tty/tty11
  N: tty11
  S: char/4:11
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty11
  E: MAJOR=4
  E: MINOR=11
  E: DEVNAME=/dev/tty11
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:11
  
  P: /devices/virtual/tty/tty12
  N: tty12
  S: char/4:12
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty12
  E: MAJOR=4
  E: MINOR=12
  E: DEVNAME=/dev/tty12
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:12
  
  P: /devices/virtual/tty/tty13
  N: tty13
  S: char/4:13
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty13
  E: MAJOR=4
  E: MINOR=13
  E: DEVNAME=/dev/tty13
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:13
  
  P: /devices/virtual/tty/tty14
  N: tty14
  S: char/4:14
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty14
  E: MAJOR=4
  E: MINOR=14
  E: DEVNAME=/dev/tty14
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:14
  
  P: /devices/virtual/tty/tty15
  N: tty15
  S: char/4:15
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty15
  E: MAJOR=4
  E: MINOR=15
  E: DEVNAME=/dev/tty15
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:15
  
  P: /devices/virtual/tty/tty16
  N: tty16
  S: char/4:16
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty16
  E: MAJOR=4
  E: MINOR=16
  E: DEVNAME=/dev/tty16
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:16
  
  P: /devices/virtual/tty/tty17
  N: tty17
  S: char/4:17
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty17
  E: MAJOR=4
  E: MINOR=17
  E: DEVNAME=/dev/tty17
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:17
  
  P: /devices/virtual/tty/tty18
  N: tty18
  S: char/4:18
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty18
  E: MAJOR=4
  E: MINOR=18
  E: DEVNAME=/dev/tty18
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:18
  
  P: /devices/virtual/tty/tty19
  N: tty19
  S: char/4:19
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty19
  E: MAJOR=4
  E: MINOR=19
  E: DEVNAME=/dev/tty19
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:19
  
  P: /devices/virtual/tty/tty2
  N: tty2
  S: char/4:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty2
  E: MAJOR=4
  E: MINOR=2
  E: DEVNAME=/dev/tty2
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:2
  
  P: /devices/virtual/tty/tty20
  N: tty20
  S: char/4:20
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty20
  E: MAJOR=4
  E: MINOR=20
  E: DEVNAME=/dev/tty20
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:20
  
  P: /devices/virtual/tty/tty21
  N: tty21
  S: char/4:21
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty21
  E: MAJOR=4
  E: MINOR=21
  E: DEVNAME=/dev/tty21
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:21
  
  P: /devices/virtual/tty/tty22
  N: tty22
  S: char/4:22
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty22
  E: MAJOR=4
  E: MINOR=22
  E: DEVNAME=/dev/tty22
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:22
  
  P: /devices/virtual/tty/tty23
  N: tty23
  S: char/4:23
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty23
  E: MAJOR=4
  E: MINOR=23
  E: DEVNAME=/dev/tty23
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:23
  
  P: /devices/virtual/tty/tty24
  N: tty24
  S: char/4:24
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty24
  E: MAJOR=4
  E: MINOR=24
  E: DEVNAME=/dev/tty24
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:24
  
  P: /devices/virtual/tty/tty25
  N: tty25
  S: char/4:25
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty25
  E: MAJOR=4
  E: MINOR=25
  E: DEVNAME=/dev/tty25
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:25
  
  P: /devices/virtual/tty/tty26
  N: tty26
  S: char/4:26
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty26
  E: MAJOR=4
  E: MINOR=26
  E: DEVNAME=/dev/tty26
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:26
  
  P: /devices/virtual/tty/tty27
  N: tty27
  S: char/4:27
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty27
  E: MAJOR=4
  E: MINOR=27
  E: DEVNAME=/dev/tty27
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:27
  
  P: /devices/virtual/tty/tty28
  N: tty28
  S: char/4:28
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty28
  E: MAJOR=4
  E: MINOR=28
  E: DEVNAME=/dev/tty28
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:28
  
  P: /devices/virtual/tty/tty29
  N: tty29
  S: char/4:29
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty29
  E: MAJOR=4
  E: MINOR=29
  E: DEVNAME=/dev/tty29
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:29
  
  P: /devices/virtual/tty/tty3
  N: tty3
  S: char/4:3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty3
  E: MAJOR=4
  E: MINOR=3
  E: DEVNAME=/dev/tty3
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:3
  
  P: /devices/virtual/tty/tty30
  N: tty30
  S: char/4:30
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty30
  E: MAJOR=4
  E: MINOR=30
  E: DEVNAME=/dev/tty30
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:30
  
  P: /devices/virtual/tty/tty31
  N: tty31
  S: char/4:31
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty31
  E: MAJOR=4
  E: MINOR=31
  E: DEVNAME=/dev/tty31
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:31
  
  P: /devices/virtual/tty/tty32
  N: tty32
  S: char/4:32
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty32
  E: MAJOR=4
  E: MINOR=32
  E: DEVNAME=/dev/tty32
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:32
  
  P: /devices/virtual/tty/tty33
  N: tty33
  S: char/4:33
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty33
  E: MAJOR=4
  E: MINOR=33
  E: DEVNAME=/dev/tty33
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:33
  
  P: /devices/virtual/tty/tty34
  N: tty34
  S: char/4:34
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty34
  E: MAJOR=4
  E: MINOR=34
  E: DEVNAME=/dev/tty34
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:34
  
  P: /devices/virtual/tty/tty35
  N: tty35
  S: char/4:35
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty35
  E: MAJOR=4
  E: MINOR=35
  E: DEVNAME=/dev/tty35
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:35
  
  P: /devices/virtual/tty/tty36
  N: tty36
  S: char/4:36
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty36
  E: MAJOR=4
  E: MINOR=36
  E: DEVNAME=/dev/tty36
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:36
  
  P: /devices/virtual/tty/tty37
  N: tty37
  S: char/4:37
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty37
  E: MAJOR=4
  E: MINOR=37
  E: DEVNAME=/dev/tty37
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:37
  
  P: /devices/virtual/tty/tty38
  N: tty38
  S: char/4:38
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty38
  E: MAJOR=4
  E: MINOR=38
  E: DEVNAME=/dev/tty38
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:38
  
  P: /devices/virtual/tty/tty39
  N: tty39
  S: char/4:39
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty39
  E: MAJOR=4
  E: MINOR=39
  E: DEVNAME=/dev/tty39
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:39
  
  P: /devices/virtual/tty/tty4
  N: tty4
  S: char/4:4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty4
  E: MAJOR=4
  E: MINOR=4
  E: DEVNAME=/dev/tty4
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:4
  
  P: /devices/virtual/tty/tty40
  N: tty40
  S: char/4:40
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty40
  E: MAJOR=4
  E: MINOR=40
  E: DEVNAME=/dev/tty40
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:40
  
  P: /devices/virtual/tty/tty41
  N: tty41
  S: char/4:41
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty41
  E: MAJOR=4
  E: MINOR=41
  E: DEVNAME=/dev/tty41
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:41
  
  P: /devices/virtual/tty/tty42
  N: tty42
  S: char/4:42
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty42
  E: MAJOR=4
  E: MINOR=42
  E: DEVNAME=/dev/tty42
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:42
  
  P: /devices/virtual/tty/tty43
  N: tty43
  S: char/4:43
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty43
  E: MAJOR=4
  E: MINOR=43
  E: DEVNAME=/dev/tty43
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:43
  
  P: /devices/virtual/tty/tty44
  N: tty44
  S: char/4:44
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty44
  E: MAJOR=4
  E: MINOR=44
  E: DEVNAME=/dev/tty44
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:44
  
  P: /devices/virtual/tty/tty45
  N: tty45
  S: char/4:45
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty45
  E: MAJOR=4
  E: MINOR=45
  E: DEVNAME=/dev/tty45
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:45
  
  P: /devices/virtual/tty/tty46
  N: tty46
  S: char/4:46
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty46
  E: MAJOR=4
  E: MINOR=46
  E: DEVNAME=/dev/tty46
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:46
  
  P: /devices/virtual/tty/tty47
  N: tty47
  S: char/4:47
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty47
  E: MAJOR=4
  E: MINOR=47
  E: DEVNAME=/dev/tty47
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:47
  
  P: /devices/virtual/tty/tty48
  N: tty48
  S: char/4:48
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty48
  E: MAJOR=4
  E: MINOR=48
  E: DEVNAME=/dev/tty48
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:48
  
  P: /devices/virtual/tty/tty49
  N: tty49
  S: char/4:49
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty49
  E: MAJOR=4
  E: MINOR=49
  E: DEVNAME=/dev/tty49
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:49
  
  P: /devices/virtual/tty/tty5
  N: tty5
  S: char/4:5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty5
  E: MAJOR=4
  E: MINOR=5
  E: DEVNAME=/dev/tty5
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:5
  
  P: /devices/virtual/tty/tty50
  N: tty50
  S: char/4:50
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty50
  E: MAJOR=4
  E: MINOR=50
  E: DEVNAME=/dev/tty50
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:50
  
  P: /devices/virtual/tty/tty51
  N: tty51
  S: char/4:51
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty51
  E: MAJOR=4
  E: MINOR=51
  E: DEVNAME=/dev/tty51
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:51
  
  P: /devices/virtual/tty/tty52
  N: tty52
  S: char/4:52
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty52
  E: MAJOR=4
  E: MINOR=52
  E: DEVNAME=/dev/tty52
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:52
  
  P: /devices/virtual/tty/tty53
  N: tty53
  S: char/4:53
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty53
  E: MAJOR=4
  E: MINOR=53
  E: DEVNAME=/dev/tty53
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:53
  
  P: /devices/virtual/tty/tty54
  N: tty54
  S: char/4:54
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty54
  E: MAJOR=4
  E: MINOR=54
  E: DEVNAME=/dev/tty54
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:54
  
  P: /devices/virtual/tty/tty55
  N: tty55
  S: char/4:55
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty55
  E: MAJOR=4
  E: MINOR=55
  E: DEVNAME=/dev/tty55
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:55
  
  P: /devices/virtual/tty/tty56
  N: tty56
  S: char/4:56
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty56
  E: MAJOR=4
  E: MINOR=56
  E: DEVNAME=/dev/tty56
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:56
  
  P: /devices/virtual/tty/tty57
  N: tty57
  S: char/4:57
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty57
  E: MAJOR=4
  E: MINOR=57
  E: DEVNAME=/dev/tty57
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:57
  
  P: /devices/virtual/tty/tty58
  N: tty58
  S: char/4:58
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty58
  E: MAJOR=4
  E: MINOR=58
  E: DEVNAME=/dev/tty58
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:58
  
  P: /devices/virtual/tty/tty59
  N: tty59
  S: char/4:59
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty59
  E: MAJOR=4
  E: MINOR=59
  E: DEVNAME=/dev/tty59
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:59
  
  P: /devices/virtual/tty/tty6
  N: tty6
  S: char/4:6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty6
  E: MAJOR=4
  E: MINOR=6
  E: DEVNAME=/dev/tty6
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:6
  
  P: /devices/virtual/tty/tty60
  N: tty60
  S: char/4:60
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty60
  E: MAJOR=4
  E: MINOR=60
  E: DEVNAME=/dev/tty60
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:60
  
  P: /devices/virtual/tty/tty61
  N: tty61
  S: char/4:61
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty61
  E: MAJOR=4
  E: MINOR=61
  E: DEVNAME=/dev/tty61
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:61
  
  P: /devices/virtual/tty/tty62
  N: tty62
  S: char/4:62
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty62
  E: MAJOR=4
  E: MINOR=62
  E: DEVNAME=/dev/tty62
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:62
  
  P: /devices/virtual/tty/tty63
  N: tty63
  S: char/4:63
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty63
  E: MAJOR=4
  E: MINOR=63
  E: DEVNAME=/dev/tty63
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:63
  
  P: /devices/virtual/tty/tty7
  N: tty7
  S: char/4:7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty7
  E: MAJOR=4
  E: MINOR=7
  E: DEVNAME=/dev/tty7
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:7
  
  P: /devices/virtual/tty/tty8
  N: tty8
  S: char/4:8
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty8
  E: MAJOR=4
  E: MINOR=8
  E: DEVNAME=/dev/tty8
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:8
  
  P: /devices/virtual/tty/tty9
  N: tty9
  S: char/4:9
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty9
  E: MAJOR=4
  E: MINOR=9
  E: DEVNAME=/dev/tty9
  E: SUBSYSTEM=tty
  E: DEVLINKS=/dev/char/4:9
  
  P: /devices/virtual/usbmon/usbmon0
  N: usbmon0
  S: char/252:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/usbmon/usbmon0
  E: MAJOR=252
  E: MINOR=0
  E: DEVNAME=/dev/usbmon0
  E: SUBSYSTEM=usbmon
  E: DEVLINKS=/dev/char/252:0
  
  P: /devices/virtual/vc/vcs
  N: vcs
  S: char/7:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs
  E: MAJOR=7
  E: MINOR=0
  E: DEVNAME=/dev/vcs
  E: SUBSYSTEM=vc
  E: DEVLINKS=/dev/char/7:0
  
  P: /devices/virtual/vc/vcs1
  N: vcs1
  S: char/7:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs1
  E: MAJOR=7
  E: MINOR=1
  E: DEVNAME=/dev/vcs1
  E: SUBSYSTEM=vc
  E: DEVLINKS=/dev/char/7:1
  
  P: /devices/virtual/vc/vcs2
  N: vcs2
  S: char/7:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs2
  E: MAJOR=7
  E: MINOR=2
  E: DEVNAME=/dev/vcs2
  E: SUBSYSTEM=vc
  E: DEVLINKS=/dev/char/7:2
  
  P: /devices/virtual/vc/vcs3
  N: vcs3
  S: char/7:3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs3
  E: MAJOR=7
  E: MINOR=3
  E: DEVNAME=/dev/vcs3
  E: SUBSYSTEM=vc
  E: DEVLINKS=/dev/char/7:3
  
  P: /devices/virtual/vc/vcs4
  N: vcs4
  S: char/7:4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs4
  E: MAJOR=7
  E: MINOR=4
  E: DEVNAME=/dev/vcs4
  E: SUBSYSTEM=vc
  E: DEVLINKS=/dev/char/7:4
  
  P: /devices/virtual/vc/vcs5
  N: vcs5
  S: char/7:5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs5
  E: MAJOR=7
  E: MINOR=5
  E: DEVNAME=/dev/vcs5
  E: SUBSYSTEM=vc
  E: DEVLINKS=/dev/char/7:5
  
  P: /devices/virtual/vc/vcs6
  N: vcs6
  S: char/7:6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs6
  E: MAJOR=7
  E: MINOR=6
  E: DEVNAME=/dev/vcs6
  E: SUBSYSTEM=vc
  E: DEVLINKS=/dev/char/7:6
  
  P: /devices/virtual/vc/vcs7
  N: vcs7
  S: char/7:7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs7
  E: MAJOR=7
  E: MINOR=7
  E: DEVNAME=/dev/vcs7
  E: SUBSYSTEM=vc
  E: DEVLINKS=/dev/char/7:7
  
  P: /devices/virtual/vc/vcsa
  N: vcsa
  S: char/7:128
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa
  E: MAJOR=7
  E: MINOR=128
  E: DEVNAME=/dev/vcsa
  E: SUBSYSTEM=vc
  E: DEVLINKS=/dev/char/7:128
  
  P: /devices/virtual/vc/vcsa1
  N: vcsa1
  S: char/7:129
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa1
  E: MAJOR=7
  E: MINOR=129
  E: DEVNAME=/dev/vcsa1
  E: SUBSYSTEM=vc
  E: DEVLINKS=/dev/char/7:129
  
  P: /devices/virtual/vc/vcsa2
  N: vcsa2
  S: char/7:130
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa2
  E: MAJOR=7
  E: MINOR=130
  E: DEVNAME=/dev/vcsa2
  E: SUBSYSTEM=vc
  E: DEVLINKS=/dev/char/7:130
  
  P: /devices/virtual/vc/vcsa3
  N: vcsa3
  S: char/7:131
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa3
  E: MAJOR=7
  E: MINOR=131
  E: DEVNAME=/dev/vcsa3
  E: SUBSYSTEM=vc
  E: DEVLINKS=/dev/char/7:131
  
  P: /devices/virtual/vc/vcsa4
  N: vcsa4
  S: char/7:132
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa4
  E: MAJOR=7
  E: MINOR=132
  E: DEVNAME=/dev/vcsa4
  E: SUBSYSTEM=vc
  E: DEVLINKS=/dev/char/7:132
  
  P: /devices/virtual/vc/vcsa5
  N: vcsa5
  S: char/7:133
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa5
  E: MAJOR=7
  E: MINOR=133
  E: DEVNAME=/dev/vcsa5
  E: SUBSYSTEM=vc
  E: DEVLINKS=/dev/char/7:133
  
  P: /devices/virtual/vc/vcsa6
  N: vcsa6
  S: char/7:134
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa6
  E: MAJOR=7
  E: MINOR=134
  E: DEVNAME=/dev/vcsa6
  E: SUBSYSTEM=vc
  E: DEVLINKS=/dev/char/7:134
  
  P: /devices/virtual/vc/vcsa7
  N: vcsa7
  S: char/7:135
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa7
  E: MAJOR=7
  E: MINOR=135
  E: DEVNAME=/dev/vcsa7
  E: SUBSYSTEM=vc
  E: DEVLINKS=/dev/char/7:135
  
  P: /devices/virtual/vtconsole/vtcon0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vtconsole/vtcon0
  E: SUBSYSTEM=vtconsole
  
  P: /devices/virtual/vtconsole/vtcon1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vtconsole/vtcon1
  E: SUBSYSTEM=vtconsole
  
  P: /devices/virtual/block/dm-0
  N: mapper/lvm_crypt
  L: -100
  W: 59
  S: block/251:0
  S: dm-0
  S: disk/by-id/dm-name-lvm_crypt
  S: disk/by-id/dm-uuid-CRYPT-LUKS1-1d5415674b9a441bb8acc449be714fb0-lvm_crypt
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/dm-0
  E: MAJOR=251
  E: MINOR=0
  E: DEVNAME=/dev/mapper/lvm_crypt
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: DM_NAME=lvm_crypt
  E: DM_UUID=CRYPT-LUKS1-1d5415674b9a441bb8acc449be714fb0-lvm_crypt
  E: DM_SUSPENDED=0
  E: DM_UDEV_RULES=1
  E: ID_FS_UUID=DLs0nD-h19y-8Th5-2DHg-qYIb-sG1S-nuwY70
  E: ID_FS_UUID_ENC=DLs0nD-h19y-8Th5-2DHg-qYIb-sG1S-nuwY70
  E: ID_FS_VERSION=LVM2\x20001
  E: ID_FS_TYPE=LVM2_member
  E: ID_FS_USAGE=raid
  E: UDISKS_PRESENTATION_NOPOLICY=1
  E: DEVLINKS=/dev/block/251:0 /dev/dm-0 /dev/disk/by-id/dm-name-lvm_crypt /dev/disk/by-id/dm-uuid-CRYPT-LUKS1-1d5415674b9a441bb8acc449be714fb0-lvm_crypt
  
  P: /devices/virtual/block/dm-1
  N: mapper/ubuntu-swap
  L: -100
  W: 52
  S: block/251:1
  S: dm-1
  S: disk/by-id/dm-name-ubuntu-swap
  S: disk/by-id/dm-uuid-LVM-NIv4KW2v620OjmF8LfXMq7NplwhyVPG74S0GSgapmXUqZZT7SkDIZ9zXYnuggNwt
  S: disk/by-uuid/31543775-b938-4bb0-b939-e11600446d16
  S: ubuntu/swap
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/dm-1
  E: MAJOR=251
  E: MINOR=1
  E: DEVNAME=/dev/mapper/ubuntu-swap
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: DM_NAME=ubuntu-swap
  E: DM_UUID=LVM-NIv4KW2v620OjmF8LfXMq7NplwhyVPG74S0GSgapmXUqZZT7SkDIZ9zXYnuggNwt
  E: DM_SUSPENDED=0
  E: DM_UDEV_RULES=1
  E: DM_VG_NAME=ubuntu
  E: DM_LV_NAME=swap
  E: DEVLINKS=/dev/block/251:1 /dev/dm-1 /dev/disk/by-id/dm-name-ubuntu-swap /dev/disk/by-id/dm-uuid-LVM-NIv4KW2v620OjmF8LfXMq7NplwhyVPG74S0GSgapmXUqZZT7SkDIZ9zXYnuggNwt /dev/disk/by-uuid/31543775-b938-4bb0-b939-e11600446d16 /dev/ubuntu/swap
  E: ID_FS_UUID=31543775-b938-4bb0-b939-e11600446d16
  E: ID_FS_UUID_ENC=31543775-b938-4bb0-b939-e11600446d16
  E: ID_FS_VERSION=2
  E: ID_FS_TYPE=swap
  E: ID_FS_USAGE=other
  E: FSTAB_NAME=/dev/mapper/ubuntu-swap
  E: FSTAB_DIR=none
  E: FSTAB_TYPE=swap
  E: FSTAB_OPTS=sw
  E: FSTAB_FREQ=0
  E: FSTAB_PASSNO=0
  E: UDISKS_PRESENTATION_NOPOLICY=1
  
  P: /devices/virtual/block/dm-2
  N: mapper/ubuntu-root
  L: -100
  W: 61
  S: block/251:2
  S: dm-2
  S: disk/by-id/dm-name-ubuntu-root
  S: disk/by-id/dm-uuid-LVM-NIv4KW2v620OjmF8LfXMq7NplwhyVPG7UiF5m8jdWb9WwH4nDxOaZzTg34Zp38pE
  S: disk/by-uuid/44772f0e-1b73-4ade-b41e-7f8311f35266
  S: ubuntu/root
  S: root
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/dm-2
  E: MAJOR=251
  E: MINOR=2
  E: DEVNAME=/dev/mapper/ubuntu-root
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: DM_NAME=ubuntu-root
  E: DM_UUID=LVM-NIv4KW2v620OjmF8LfXMq7NplwhyVPG7UiF5m8jdWb9WwH4nDxOaZzTg34Zp38pE
  E: DM_SUSPENDED=0
  E: DM_UDEV_RULES=1
  E: DM_VG_NAME=ubuntu
  E: DM_LV_NAME=root
  E: DEVLINKS=/dev/block/251:2 /dev/dm-2 /dev/disk/by-id/dm-name-ubuntu-root /dev/disk/by-id/dm-uuid-LVM-NIv4KW2v620OjmF8LfXMq7NplwhyVPG7UiF5m8jdWb9WwH4nDxOaZzTg34Zp38pE /dev/disk/by-uuid/44772f0e-1b73-4ade-b41e-7f8311f35266 /dev/ubuntu/root /dev/root
  E: ID_FS_UUID=44772f0e-1b73-4ade-b41e-7f8311f35266
  E: ID_FS_UUID_ENC=44772f0e-1b73-4ade-b41e-7f8311f35266
  E: ID_FS_VERSION=1.0
  E: ID_FS_TYPE=ext4
  E: ID_FS_USAGE=filesystem
  E: UDISKS_PRESENTATION_NOPOLICY=1
  E: UDISKS_DM_TARGETS_COUNT=1
  E: UDISKS_DM_TARGETS_TYPE=linear
  E: UDISKS_DM_TARGETS_START=0
  E: UDISKS_DM_TARGETS_LENGTH=177414144
  E: UDISKS_DM_TARGETS_PARAMS=251:0\x207643520
  
-----  udevinfo end -----
/devices/LNXSYSTM:00
/devices/LNXSYSTM:00/LNXCPU:00
/devices/LNXSYSTM:00/LNXCPU:01
/devices/LNXSYSTM:00/LNXCPU:02
/devices/LNXSYSTM:00/LNXCPU:03
/devices/LNXSYSTM:00/LNXPWRBN:00
/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1
  name: /dev/input/event1
  links: /dev/char/13:65
/devices/LNXSYSTM:00/LNXSYBUS:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/INT3F0D:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/PNP0103:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/PNP0C01:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/PNP0C01:01
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/PNP0000:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/PNP0100:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/PNP0200:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/PNP0501:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/PNP0800:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/PNP0B00:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/PNP0C02:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/PNP0C02:01
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/PNP0C04:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02/device:03
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02/device:03/device:04
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02/device:03/device:05
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02/device:06
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02/device:06/device:07
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02/device:06/device:08
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:09
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:09/device:0a
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:09/device:0a/device:0b
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:09/device:0a/device:0c
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:09/device:0d
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:09/device:0d/device:0e
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:09/device:0d/device:0f
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:10
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:11
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:11/device:12
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:11/device:12/device:13
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:11/device:12/device:13/device:14
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:11/device:12/device:13/device:15
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:11/device:12/device:13/device:16
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:11/device:12/device:13/device:17
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:11/device:12/device:13/device:18
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:11/device:12/device:13/device:19
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:11/device:12/device:13/device:1a
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:11/device:12/device:13/device:1b
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1c
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1c/device:1d
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1c/device:1d/device:1e
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1c/device:1d/device:1e/device:1f
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1c/device:1d/device:1e/device:20
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1c/device:1d/device:1e/device:21
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1c/device:1d/device:1e/device:22
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1c/device:1d/device:1e/device:23
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1c/device:1d/device:1e/device:24
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:25
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:26
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:27
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:28
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:29
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2a
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2b
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2c
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2d
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2e
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2f
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:30
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:31
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:32
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/pnp0c14:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C01:02
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0
  name: /dev/input/event0
  links: /dev/char/13:64
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0F:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0F:01
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0F:02
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0F:03
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0F:04
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0F:05
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0F:06
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0F:07
/devices/LNXSYSTM:00/LNXTHERM:00
/devices/LNXSYSTM:00/PNP0C02:02
/devices/pci0000:00/0000:00:00.0
/devices/pci0000:00/0000:00:01.0
/devices/pci0000:00/0000:00:01.0/0000:00:01.0:pcie01
/devices/pci0000:00/0000:00:01.0/0000:00:01.0:pcie08
/devices/pci0000:00/0000:00:01.0/pci_bus/0000:01
/devices/pci0000:00/0000:00:01.1
/devices/pci0000:00/0000:00:01.1/0000:00:01.1:pcie01
/devices/pci0000:00/0000:00:01.1/0000:00:01.1:pcie08
/devices/pci0000:00/0000:00:01.1/0000:02:00.0
/devices/pci0000:00/0000:00:01.1/0000:02:00.0/i2c-0
/devices/pci0000:00/0000:00:01.1/0000:02:00.0/i2c-1
/devices/pci0000:00/0000:00:01.1/0000:02:00.0/i2c-2
/devices/pci0000:00/0000:00:01.1/0000:02:00.0/i2c-3
/devices/pci0000:00/0000:00:01.1/0000:02:00.1
/devices/pci0000:00/0000:00:01.1/pci_bus/0000:02
/devices/pci0000:00/0000:00:16.0
/devices/pci0000:00/0000:00:1a.0
/devices/pci0000:00/0000:00:1a.0/usb1
  name: /dev/bus/usb/001/001
  links: /dev/char/189:0
/devices/pci0000:00/0000:00:1a.0/usb1/1-0:1.0
/devices/pci0000:00/0000:00:1a.0/usb1/1-1
  name: /dev/bus/usb/001/002
  links: /dev/char/189:1
/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3
  name: /dev/bus/usb/001/003
  links: /dev/char/189:2
/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1
  name: /dev/bus/usb/001/005
  links: /dev/char/189:4
/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.0
/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.0/0003:046D:C22B.0002
/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.0/0003:046D:C22B.0002/hidraw/hidraw1
  name: /dev/hidraw1
  links: /dev/char/251:1
/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.0/input/input4
/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.0/input/input4/event4
  name: /dev/input/event4
  links: /dev/char/13:68, /dev/input/by-id/usb-LOGITECH_G110_G-keys-event-kbd, /dev/input/by-path/pci-0000:00:1a.0-usb-0:1.3.1:1.0-event-kbd
/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.0/usb/hiddev1
  name: /dev/usb/hiddev1
  links: /dev/char/180:97
/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.1
/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3
  name: /dev/bus/usb/001/006
  links: /dev/char/189:5
/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.0
/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.0/0003:046D:C22A.0003
/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.0/0003:046D:C22A.0003/hidraw/hidraw2
  name: /dev/hidraw2
  links: /dev/char/251:2
/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.0/input/input5
/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.0/input/input5/event5
  name: /dev/input/event5
  links: /dev/char/13:69, /dev/input/by-id/usb-046d_Gaming_Keyboard_G110-event-kbd, /dev/input/by-path/pci-0000:00:1a.0-usb-0:1.3.3:1.0-event-kbd
/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.1
/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.1/0003:046D:C22A.0004
/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.1/0003:046D:C22A.0004/hidraw/hidraw3
  name: /dev/hidraw3
  links: /dev/char/251:3
/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.1/input/input6
/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.1/input/input6/event6
  name: /dev/input/event6
  links: /dev/char/13:70, /dev/input/by-id/usb-046d_Gaming_Keyboard_G110-event-if01, /dev/input/by-path/pci-0000:00:1a.0-usb-0:1.3.3:1.1-event
/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.1/usb/hiddev2
  name: /dev/usb/hiddev2
  links: /dev/char/180:98
/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0
/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6
  name: /dev/bus/usb/001/004
  links: /dev/char/189:3
/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0
/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/0003:04B4:121F.0001
/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/0003:04B4:121F.0001/hidraw/hidraw0
  name: /dev/hidraw0
  links: /dev/char/251:0
/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input3
/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input3/event3
  name: /dev/input/event3
  links: /dev/char/13:67, /dev/input/by-id/usb-SteelSeries_ApS_Ikari_Laser-event-mouse, /dev/input/by-path/pci-0000:00:1a.0-usb-0:1.6:1.0-event-mouse
/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input3/mouse1
  name: /dev/input/mouse1
  links: /dev/char/13:33, /dev/input/by-id/usb-SteelSeries_ApS_Ikari_Laser-mouse, /dev/input/by-path/pci-0000:00:1a.0-usb-0:1.6:1.0-mouse
/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/usb/hiddev0
  name: /dev/usb/hiddev0
  links: /dev/char/180:96
/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1:1.0
/devices/pci0000:00/0000:00:1a.0/usbmon/usbmon1
  name: /dev/usbmon1
  links: /dev/char/252:1
/devices/pci0000:00/0000:00:1b.0
/devices/pci0000:00/0000:00:1b.0/sound/card0
/devices/pci0000:00/0000:00:1b.0/sound/card0/audio
  name: /dev/audio
  links: /dev/char/14:4
/devices/pci0000:00/0000:00:1b.0/sound/card0/dsp
  name: /dev/dsp
  links: /dev/char/14:3
/devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D1
  name: /dev/snd/hwC0D1
  links: /dev/char/116:6
/devices/pci0000:00/0000:00:1b.0/sound/card0/mixer
  name: /dev/mixer
  links: /dev/char/14:0
/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0c
  name: /dev/snd/pcmC0D0c
  links: /dev/char/116:5
/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0p
  name: /dev/snd/pcmC0D0p
  links: /dev/char/116:4
/devices/pci0000:00/0000:00:1b.0/sound/card0/controlC0
  name: /dev/snd/controlC0
  links: /dev/char/116:7, /dev/snd/by-path/pci-0000:00:1b.0
/devices/pci0000:00/0000:00:1c.0
/devices/pci0000:00/0000:00:1c.0/0000:00:1c.0:pcie01
/devices/pci0000:00/0000:00:1c.0/pci_bus/0000:03
/devices/pci0000:00/0000:00:1c.4
/devices/pci0000:00/0000:00:1c.4/0000:04:00.0
/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/0000:05:01.0
/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/0000:05:01.0/net/eth0
/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/pci_bus/0000:05
/devices/pci0000:00/0000:00:1c.4/pci_bus/0000:04
/devices/pci0000:00/0000:00:1c.6
/devices/pci0000:00/0000:00:1c.6/0000:00:1c.6:pcie01
/devices/pci0000:00/0000:00:1c.6/pci_bus/0000:06
/devices/pci0000:00/0000:00:1c.7
/devices/pci0000:00/0000:00:1c.7/0000:00:1c.7:pcie01
/devices/pci0000:00/0000:00:1c.7/0000:07:00.0
/devices/pci0000:00/0000:00:1c.7/0000:07:00.0/fw-host0
/devices/pci0000:00/0000:00:1c.7/0000:07:00.0/fw-host0/0010dc0001cbe8ae
/devices/pci0000:00/0000:00:1c.7/0000:07:00.0/fw-host0/0010dc0001cbe8ae/ieee1394_node/0010dc0001cbe8ae
/devices/pci0000:00/0000:00:1c.7/0000:07:00.0/fw-host0/ieee1394_host/fw-host0
/devices/pci0000:00/0000:00:1c.7/pci_bus/0000:07
/devices/pci0000:00/0000:00:1d.0
/devices/pci0000:00/0000:00:1d.0/usb2
  name: /dev/bus/usb/002/001
  links: /dev/char/189:128
/devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0
/devices/pci0000:00/0000:00:1d.0/usb2/2-1
  name: /dev/bus/usb/002/002
  links: /dev/char/189:129
/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5
  name: /dev/bus/usb/002/003
  links: /dev/char/189:130
/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0
/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.1
/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.1/usb/lp0
  name: /dev/usb/lp0
  links: /dev/char/180:0, /dev/usblp0
/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.2
/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6
  name: /dev/bus/usb/002/004
  links: /dev/char/189:131
/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0
/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input7
/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input7/event7
  name: /dev/input/event7
  links: /dev/char/13:71, /dev/input/by-id/usb-Sonix_Technology_Co.__Ltd._USB_2.0_Camera-event-if00, /dev/input/by-path/pci-0000:00:1d.0-usb-0:1.6:1.0-event
/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/video4linux/video0
  name: /dev/video0
  links: /dev/char/81:0, /dev/v4l/by-id/usb-Sonix_Technology_Co.__Ltd._USB_2.0_Camera-video-index0, /dev/v4l/by-path/pci-0000:00:1d.0-usb-0:1.6:1.0-video-index0
/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.1
/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2
/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/sound/card1
/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/sound/card1/audio1
  name: /dev/audio1
  links: /dev/char/14:20
/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/sound/card1/dsp1
  name: /dev/dsp1
  links: /dev/char/14:19
/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/sound/card1/mixer1
  name: /dev/mixer1
  links: /dev/char/14:16
/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/sound/card1/pcmC1D0c
  name: /dev/snd/pcmC1D0c
  links: /dev/char/116:8
/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/sound/card1/controlC1
  name: /dev/snd/controlC1
  links: /dev/char/116:9, /dev/snd/by-id/usb-Sonix_Technology_Co.__Ltd._USB_2.0_Camera-02, /dev/snd/by-path/pci-0000:00:1d.0-usb-0:1.6:1.2
/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.3
/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0
/devices/pci0000:00/0000:00:1d.0/usbmon/usbmon2
  name: /dev/usbmon2
  links: /dev/char/252:2
/devices/pci0000:00/0000:00:1f.0
/devices/pci0000:00/0000:00:1f.2
/devices/pci0000:00/0000:00:1f.2/host0
/devices/pci0000:00/0000:00:1f.2/host0/scsi_host/host0
/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0
/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0
/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sr0
  name: /dev/sr0
  links: /dev/block/11:0, /dev/scd0, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0, /dev/cdrom, /dev/cdrw, /dev/dvd, /dev/dvdrw
/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/bsg/0:0:0:0
  name: /dev/bsg/0:0:0:0
  links: /dev/char/253:0
/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_device/0:0:0:0
/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_generic/sg0
  name: /dev/sg0
  links: /dev/char/21:0
/devices/pci0000:00/0000:00:1f.2/host1
/devices/pci0000:00/0000:00:1f.2/host1/scsi_host/host1
/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0
/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0
/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sda
  name: /dev/sda
  links: /dev/block/8:0, /dev/disk/by-id/ata-WDC_WD5000AAKX-001CA0_WD-WCAYUR040248, /dev/disk/by-id/scsi-SATA_WDC_WD5000AAKX-_WD-WCAYUR040248, /dev/disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0, /dev/disk/by-id/wwn-0x50014ee1ae9d87ac
/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sda/sda1
  name: /dev/sda1
  links: /dev/block/8:1, /dev/disk/by-id/ata-WDC_WD5000AAKX-001CA0_WD-WCAYUR040248-part1, /dev/disk/by-id/scsi-SATA_WDC_WD5000AAKX-_WD-WCAYUR040248-part1, /dev/disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0-part1, /dev/disk/by-uuid/60C2F3B7C2F39010, /dev/disk/by-label/System\x20Reserved, /dev/disk/by-id/wwn-0x50014ee1ae9d87ac-part1
/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sda/sda2
  name: /dev/sda2
  links: /dev/block/8:2, /dev/disk/by-id/ata-WDC_WD5000AAKX-001CA0_WD-WCAYUR040248-part2, /dev/disk/by-id/scsi-SATA_WDC_WD5000AAKX-_WD-WCAYUR040248-part2, /dev/disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0-part2, /dev/disk/by-uuid/142CF4E82CF4C5B0, /dev/disk/by-id/wwn-0x50014ee1ae9d87ac-part2
/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sda/sda3
  name: /dev/sda3
  links: /dev/block/8:3, /dev/disk/by-id/ata-WDC_WD5000AAKX-001CA0_WD-WCAYUR040248-part3, /dev/disk/by-id/scsi-SATA_WDC_WD5000AAKX-_WD-WCAYUR040248-part3, /dev/disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0-part3, /dev/disk/by-id/wwn-0x50014ee1ae9d87ac-part3
/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sda/sda5
  name: /dev/sda5
  links: /dev/block/8:5, /dev/disk/by-id/ata-WDC_WD5000AAKX-001CA0_WD-WCAYUR040248-part5, /dev/disk/by-id/scsi-SATA_WDC_WD5000AAKX-_WD-WCAYUR040248-part5, /dev/disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0-part5, /dev/disk/by-uuid/5de13091-a2a0-467d-a3af-577c9da25d1f, /dev/disk/by-id/wwn-0x50014ee1ae9d87ac-part5
/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sda/sda6
  name: /dev/sda6
  links: /dev/block/8:6, /dev/disk/by-id/ata-WDC_WD5000AAKX-001CA0_WD-WCAYUR040248-part6, /dev/disk/by-id/scsi-SATA_WDC_WD5000AAKX-_WD-WCAYUR040248-part6, /dev/disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0-part6, /dev/disk/by-uuid/1d541567-4b9a-441b-b8ac-c449be714fb0, /dev/disk/by-id/wwn-0x50014ee1ae9d87ac-part6
/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/bsg/1:0:0:0
  name: /dev/bsg/1:0:0:0
  links: /dev/char/253:1
/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/scsi_device/1:0:0:0
/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/scsi_disk/1:0:0:0
/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/scsi_generic/sg1
  name: /dev/sg1
  links: /dev/char/21:1
/devices/pci0000:00/0000:00:1f.3
/devices/pci0000:00/0000:00:1f.5
/devices/pci0000:00/0000:00:1f.5/host2
/devices/pci0000:00/0000:00:1f.5/host2/scsi_host/host2
/devices/pci0000:00/0000:00:1f.5/host3
/devices/pci0000:00/0000:00:1f.5/host3/scsi_host/host3
/devices/pci0000:00/pci_bus/0000:00
/devices/platform/Fixed
/devices/platform/Fixed
/devices/platform/eisa.0
/devices/platform/i8042
/devices/platform/i8042/serio0
/devices/platform/i8042/serio1
/devices/platform/pcspkr
/devices/platform/serial8250
/devices/platform/serial8250/tty/ttyS1
  name: /dev/ttyS1
  links: /dev/char/4:65
/devices/platform/serial8250/tty/ttyS2
  name: /dev/ttyS2
  links: /dev/char/4:66
/devices/platform/serial8250/tty/ttyS3
  name: /dev/ttyS3
  links: /dev/char/4:67
/devices/platform/vga16fb.0
/devices/platform/vga16fb.0/graphics/fb0
  name: /dev/fb0
  links: /dev/char/29:0
/devices/pnp0/00:00
/devices/pnp0/00:01
/devices/pnp0/00:02
/devices/pnp0/00:03
/devices/pnp0/00:03/tty/ttyS0
  name: /dev/ttyS0
  links: /dev/char/4:64
/devices/pnp0/00:04
/devices/pnp0/00:05
/devices/pnp0/00:05/rtc/rtc0
  name: /dev/rtc0
  links: /dev/char/254:0, /dev/rtc
/devices/pnp0/00:06
/devices/pnp0/00:07
/devices/pnp0/00:08
/devices/pnp0/00:09
/devices/pnp0/00:0a
/devices/pnp0/00:0b
/devices/virtual/bdi/0:21
/devices/virtual/bdi/11:0
/devices/virtual/bdi/1:0
/devices/virtual/bdi/1:1
/devices/virtual/bdi/1:10
/devices/virtual/bdi/1:11
/devices/virtual/bdi/1:12
/devices/virtual/bdi/1:13
/devices/virtual/bdi/1:14
/devices/virtual/bdi/1:15
/devices/virtual/bdi/1:2
/devices/virtual/bdi/1:3
/devices/virtual/bdi/1:4
/devices/virtual/bdi/1:5
/devices/virtual/bdi/1:6
/devices/virtual/bdi/1:7
/devices/virtual/bdi/1:8
/devices/virtual/bdi/1:9
/devices/virtual/bdi/251:0
/devices/virtual/bdi/251:1
/devices/virtual/bdi/251:2
/devices/virtual/bdi/7:0
/devices/virtual/bdi/7:1
/devices/virtual/bdi/7:2
/devices/virtual/bdi/7:3
/devices/virtual/bdi/7:4
/devices/virtual/bdi/7:5
/devices/virtual/bdi/7:6
/devices/virtual/bdi/7:7
/devices/virtual/bdi/8:0
/devices/virtual/bdi/default
/devices/virtual/block/loop0
  name: /dev/loop0
  links: /dev/block/7:0
/devices/virtual/block/loop1
  name: /dev/loop1
  links: /dev/block/7:1
/devices/virtual/block/loop2
  name: /dev/loop2
  links: /dev/block/7:2
/devices/virtual/block/loop3
  name: /dev/loop3
  links: /dev/block/7:3
/devices/virtual/block/loop4
  name: /dev/loop4
  links: /dev/block/7:4
/devices/virtual/block/loop5
  name: /dev/loop5
  links: /dev/block/7:5
/devices/virtual/block/loop6
  name: /dev/loop6
  links: /dev/block/7:6
/devices/virtual/block/loop7
  name: /dev/loop7
  links: /dev/block/7:7
/devices/virtual/block/ram0
  name: /dev/ram0
  links: /dev/block/1:0
/devices/virtual/block/ram1
  name: /dev/ram1
  links: /dev/block/1:1
/devices/virtual/block/ram10
  name: /dev/ram10
  links: /dev/block/1:10
/devices/virtual/block/ram11
  name: /dev/ram11
  links: /dev/block/1:11
/devices/virtual/block/ram12
  name: /dev/ram12
  links: /dev/block/1:12
/devices/virtual/block/ram13
  name: /dev/ram13
  links: /dev/block/1:13
/devices/virtual/block/ram14
  name: /dev/ram14
  links: /dev/block/1:14
/devices/virtual/block/ram15
  name: /dev/ram15
  links: /dev/block/1:15
/devices/virtual/block/ram2
  name: /dev/ram2
  links: /dev/block/1:2
/devices/virtual/block/ram3
  name: /dev/ram3
  links: /dev/block/1:3
/devices/virtual/block/ram4
  name: /dev/ram4
  links: /dev/block/1:4
/devices/virtual/block/ram5
  name: /dev/ram5
  links: /dev/block/1:5
/devices/virtual/block/ram6
  name: /dev/ram6
  links: /dev/block/1:6
/devices/virtual/block/ram7
  name: /dev/ram7
  links: /dev/block/1:7
/devices/virtual/block/ram8
  name: /dev/ram8
  links: /dev/block/1:8
/devices/virtual/block/ram9
  name: /dev/ram9
  links: /dev/block/1:9
/devices/virtual/dmi/id
/devices/virtual/drm/ttm
/devices/virtual/graphics/fbcon
/devices/virtual/input/input2
/devices/virtual/input/input2/event2
  name: /dev/input/event2
  links: /dev/char/13:66
/devices/virtual/input/input2/mouse0
  name: /dev/input/mouse0
  links: /dev/char/13:32
/devices/virtual/input/mice
  name: /dev/input/mice
  links: /dev/char/13:63
/devices/virtual/mem/full
  name: /dev/full
  links: /dev/char/1:7
/devices/virtual/mem/kmsg
  name: /dev/kmsg
  links: /dev/char/1:11
/devices/virtual/mem/mem
  name: /dev/mem
  links: /dev/char/1:1
/devices/virtual/mem/null
  name: /dev/null
  links: /dev/char/1:3
/devices/virtual/mem/oldmem
  name: /dev/oldmem
  links: /dev/char/1:12
/devices/virtual/mem/port
  name: /dev/port
  links: /dev/char/1:4
/devices/virtual/mem/random
  name: /dev/random
  links: /dev/char/1:8
/devices/virtual/mem/urandom
  name: /dev/urandom
  links: /dev/char/1:9
/devices/virtual/mem/zero
  name: /dev/zero
  links: /dev/char/1:5
/devices/virtual/misc/cpu_dma_latency
  name: /dev/cpu_dma_latency
  links: /dev/char/10:58
/devices/virtual/misc/device-mapper
  name: /dev/mapper/control
  links: /dev/char/10:59
/devices/virtual/misc/ecryptfs
  name: /dev/ecryptfs
  links: /dev/char/10:61
/devices/virtual/misc/fuse
  name: /dev/fuse
  links: /dev/char/10:229
/devices/virtual/misc/hpet
  name: /dev/hpet
  links: /dev/char/10:228
/devices/virtual/misc/mcelog
  name: /dev/mcelog
  links: /dev/char/10:227
/devices/virtual/misc/network_latency
  name: /dev/network_latency
  links: /dev/char/10:57
/devices/virtual/misc/network_throughput
  name: /dev/network_throughput
  links: /dev/char/10:56
/devices/virtual/misc/pktcdvd
  name: /dev/pktcdvd/control
  links: /dev/char/10:60
/devices/virtual/misc/psaux
  name: /dev/psaux
  links: /dev/char/10:1
/devices/virtual/misc/rfkill
  name: /dev/rfkill
  links: /dev/char/10:62
/devices/virtual/misc/snapshot
  name: /dev/snapshot
  links: /dev/char/10:231
/devices/virtual/misc/tun
  name: /dev/net/tun
  links: /dev/char/10:200
/devices/virtual/misc/vga_arbiter
  name: /dev/vga_arbiter
  links: /dev/char/10:63
/devices/virtual/net/lo
/devices/virtual/net/tun0
/devices/virtual/ppp/ppp
  name: /dev/ppp
  links: /dev/char/108:0
/devices/virtual/sound/seq
  name: /dev/snd/seq
  links: /dev/char/116:3
/devices/virtual/sound/sequencer
  name: /dev/sequencer
  links: /dev/char/14:1
/devices/virtual/sound/sequencer2
  name: /dev/sequencer2
  links: /dev/char/14:8
/devices/virtual/sound/timer
  name: /dev/snd/timer
  links: /dev/char/116:2
/devices/virtual/thermal/cooling_device0
/devices/virtual/thermal/cooling_device1
/devices/virtual/thermal/cooling_device2
/devices/virtual/thermal/cooling_device3
/devices/virtual/tty/console
  name: /dev/console
  links: /dev/char/5:1
/devices/virtual/tty/ptmx
  name: /dev/ptmx
  links: /dev/char/5:2
/devices/virtual/tty/tty
  name: /dev/tty
  links: /dev/char/5:0
/devices/virtual/tty/tty0
  name: /dev/tty0
  links: /dev/char/4:0
/devices/virtual/tty/tty1
  name: /dev/tty1
  links: /dev/char/4:1
/devices/virtual/tty/tty10
  name: /dev/tty10
  links: /dev/char/4:10
/devices/virtual/tty/tty11
  name: /dev/tty11
  links: /dev/char/4:11
/devices/virtual/tty/tty12
  name: /dev/tty12
  links: /dev/char/4:12
/devices/virtual/tty/tty13
  name: /dev/tty13
  links: /dev/char/4:13
/devices/virtual/tty/tty14
  name: /dev/tty14
  links: /dev/char/4:14
/devices/virtual/tty/tty15
  name: /dev/tty15
  links: /dev/char/4:15
/devices/virtual/tty/tty16
  name: /dev/tty16
  links: /dev/char/4:16
/devices/virtual/tty/tty17
  name: /dev/tty17
  links: /dev/char/4:17
/devices/virtual/tty/tty18
  name: /dev/tty18
  links: /dev/char/4:18
/devices/virtual/tty/tty19
  name: /dev/tty19
  links: /dev/char/4:19
/devices/virtual/tty/tty2
  name: /dev/tty2
  links: /dev/char/4:2
/devices/virtual/tty/tty20
  name: /dev/tty20
  links: /dev/char/4:20
/devices/virtual/tty/tty21
  name: /dev/tty21
  links: /dev/char/4:21
/devices/virtual/tty/tty22
  name: /dev/tty22
  links: /dev/char/4:22
/devices/virtual/tty/tty23
  name: /dev/tty23
  links: /dev/char/4:23
/devices/virtual/tty/tty24
  name: /dev/tty24
  links: /dev/char/4:24
/devices/virtual/tty/tty25
  name: /dev/tty25
  links: /dev/char/4:25
/devices/virtual/tty/tty26
  name: /dev/tty26
  links: /dev/char/4:26
/devices/virtual/tty/tty27
  name: /dev/tty27
  links: /dev/char/4:27
/devices/virtual/tty/tty28
  name: /dev/tty28
  links: /dev/char/4:28
/devices/virtual/tty/tty29
  name: /dev/tty29
  links: /dev/char/4:29
/devices/virtual/tty/tty3
  name: /dev/tty3
  links: /dev/char/4:3
/devices/virtual/tty/tty30
  name: /dev/tty30
  links: /dev/char/4:30
/devices/virtual/tty/tty31
  name: /dev/tty31
  links: /dev/char/4:31
/devices/virtual/tty/tty32
  name: /dev/tty32
  links: /dev/char/4:32
/devices/virtual/tty/tty33
  name: /dev/tty33
  links: /dev/char/4:33
/devices/virtual/tty/tty34
  name: /dev/tty34
  links: /dev/char/4:34
/devices/virtual/tty/tty35
  name: /dev/tty35
  links: /dev/char/4:35
/devices/virtual/tty/tty36
  name: /dev/tty36
  links: /dev/char/4:36
/devices/virtual/tty/tty37
  name: /dev/tty37
  links: /dev/char/4:37
/devices/virtual/tty/tty38
  name: /dev/tty38
  links: /dev/char/4:38
/devices/virtual/tty/tty39
  name: /dev/tty39
  links: /dev/char/4:39
/devices/virtual/tty/tty4
  name: /dev/tty4
  links: /dev/char/4:4
/devices/virtual/tty/tty40
  name: /dev/tty40
  links: /dev/char/4:40
/devices/virtual/tty/tty41
  name: /dev/tty41
  links: /dev/char/4:41
/devices/virtual/tty/tty42
  name: /dev/tty42
  links: /dev/char/4:42
/devices/virtual/tty/tty43
  name: /dev/tty43
  links: /dev/char/4:43
/devices/virtual/tty/tty44
  name: /dev/tty44
  links: /dev/char/4:44
/devices/virtual/tty/tty45
  name: /dev/tty45
  links: /dev/char/4:45
/devices/virtual/tty/tty46
  name: /dev/tty46
  links: /dev/char/4:46
/devices/virtual/tty/tty47
  name: /dev/tty47
  links: /dev/char/4:47
/devices/virtual/tty/tty48
  name: /dev/tty48
  links: /dev/char/4:48
/devices/virtual/tty/tty49
  name: /dev/tty49
  links: /dev/char/4:49
/devices/virtual/tty/tty5
  name: /dev/tty5
  links: /dev/char/4:5
/devices/virtual/tty/tty50
  name: /dev/tty50
  links: /dev/char/4:50
/devices/virtual/tty/tty51
  name: /dev/tty51
  links: /dev/char/4:51
/devices/virtual/tty/tty52
  name: /dev/tty52
  links: /dev/char/4:52
/devices/virtual/tty/tty53
  name: /dev/tty53
  links: /dev/char/4:53
/devices/virtual/tty/tty54
  name: /dev/tty54
  links: /dev/char/4:54
/devices/virtual/tty/tty55
  name: /dev/tty55
  links: /dev/char/4:55
/devices/virtual/tty/tty56
  name: /dev/tty56
  links: /dev/char/4:56
/devices/virtual/tty/tty57
  name: /dev/tty57
  links: /dev/char/4:57
/devices/virtual/tty/tty58
  name: /dev/tty58
  links: /dev/char/4:58
/devices/virtual/tty/tty59
  name: /dev/tty59
  links: /dev/char/4:59
/devices/virtual/tty/tty6
  name: /dev/tty6
  links: /dev/char/4:6
/devices/virtual/tty/tty60
  name: /dev/tty60
  links: /dev/char/4:60
/devices/virtual/tty/tty61
  name: /dev/tty61
  links: /dev/char/4:61
/devices/virtual/tty/tty62
  name: /dev/tty62
  links: /dev/char/4:62
/devices/virtual/tty/tty63
  name: /dev/tty63
  links: /dev/char/4:63
/devices/virtual/tty/tty7
  name: /dev/tty7
  links: /dev/char/4:7
/devices/virtual/tty/tty8
  name: /dev/tty8
  links: /dev/char/4:8
/devices/virtual/tty/tty9
  name: /dev/tty9
  links: /dev/char/4:9
/devices/virtual/usbmon/usbmon0
  name: /dev/usbmon0
  links: /dev/char/252:0
/devices/virtual/vc/vcs
  name: /dev/vcs
  links: /dev/char/7:0
/devices/virtual/vc/vcs1
  name: /dev/vcs1
  links: /dev/char/7:1
/devices/virtual/vc/vcs2
  name: /dev/vcs2
  links: /dev/char/7:2
/devices/virtual/vc/vcs3
  name: /dev/vcs3
  links: /dev/char/7:3
/devices/virtual/vc/vcs4
  name: /dev/vcs4
  links: /dev/char/7:4
/devices/virtual/vc/vcs5
  name: /dev/vcs5
  links: /dev/char/7:5
/devices/virtual/vc/vcs6
  name: /dev/vcs6
  links: /dev/char/7:6
/devices/virtual/vc/vcs7
  name: /dev/vcs7
  links: /dev/char/7:7
/devices/virtual/vc/vcsa
  name: /dev/vcsa
  links: /dev/char/7:128
/devices/virtual/vc/vcsa1
  name: /dev/vcsa1
  links: /dev/char/7:129
/devices/virtual/vc/vcsa2
  name: /dev/vcsa2
  links: /dev/char/7:130
/devices/virtual/vc/vcsa3
  name: /dev/vcsa3
  links: /dev/char/7:131
/devices/virtual/vc/vcsa4
  name: /dev/vcsa4
  links: /dev/char/7:132
/devices/virtual/vc/vcsa5
  name: /dev/vcsa5
  links: /dev/char/7:133
/devices/virtual/vc/vcsa6
  name: /dev/vcsa6
  links: /dev/char/7:134
/devices/virtual/vc/vcsa7
  name: /dev/vcsa7
  links: /dev/char/7:135
/devices/virtual/vtconsole/vtcon0
/devices/virtual/vtconsole/vtcon1
/devices/virtual/block/dm-0
  name: /dev/mapper/lvm_crypt
  links: /dev/block/251:0, /dev/dm-0, /dev/disk/by-id/dm-name-lvm_crypt, /dev/disk/by-id/dm-uuid-CRYPT-LUKS1-1d5415674b9a441bb8acc449be714fb0-lvm_crypt
/devices/virtual/block/dm-1
  name: /dev/mapper/ubuntu-swap
  links: /dev/block/251:1, /dev/dm-1, /dev/disk/by-id/dm-name-ubuntu-swap, /dev/disk/by-id/dm-uuid-LVM-NIv4KW2v620OjmF8LfXMq7NplwhyVPG74S0GSgapmXUqZZT7SkDIZ9zXYnuggNwt, /dev/disk/by-uuid/31543775-b938-4bb0-b939-e11600446d16, /dev/ubuntu/swap
/devices/virtual/block/dm-2
  name: /dev/mapper/ubuntu-root
  links: /dev/block/251:2, /dev/dm-2, /dev/disk/by-id/dm-name-ubuntu-root, /dev/disk/by-id/dm-uuid-LVM-NIv4KW2v620OjmF8LfXMq7NplwhyVPG7UiF5m8jdWb9WwH4nDxOaZzTg34Zp38pE, /dev/disk/by-uuid/44772f0e-1b73-4ade-b41e-7f8311f35266, /dev/ubuntu/root, /dev/root
>> int.13: device names
>> int.14: soft raid
----- soft raid devices -----
----- soft raid devices end -----
>> int.15: geo
>> int.16: parent
  prop read: rdCR.lZF+r4EgHp4 (failed)
  old prop read: rdCR.lZF+r4EgHp4 (failed)
  prop read: rdCR.n_7QNeEnh23 (failed)
  old prop read: rdCR.n_7QNeEnh23 (failed)
  prop read: rdCR.EMpH5pjcahD (failed)
  old prop read: rdCR.EMpH5pjcahD (failed)
  prop read: rdCR.f5u1ucRm+H9 (failed)
  old prop read: rdCR.f5u1ucRm+H9 (failed)
  prop read: rdCR.8uRK7LxiIA2 (failed)
  old prop read: rdCR.8uRK7LxiIA2 (failed)
  prop read: rdCR.AJKleuxpiP0 (failed)
  old prop read: rdCR.AJKleuxpiP0 (failed)
  prop read: rdCR.9N+EecqykME (failed)
  old prop read: rdCR.9N+EecqykME (failed)
  prop read: rdCR.CxwsZFjVASF (failed)
  old prop read: rdCR.CxwsZFjVASF (failed)
  prop read: /org/freedesktop/Hal/devices/pci_8086_100 (failed)
  prop read: qLht.+ULmzmJCXV7 (failed)
  old prop read: qLht.+ULmzmJCXV7 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_8086_101 (failed)
  prop read: vSkL.5yyCfy3P7oD (failed)
  old prop read: vSkL.5yyCfy3P7oD (failed)
  prop read: /org/freedesktop/Hal/devices/pci_8086_105 (failed)
  prop read: mnDB.9ckCaEYDEKF (failed)
  old prop read: mnDB.9ckCaEYDEKF (failed)
  prop read: /org/freedesktop/Hal/devices/pci_8086_1c3a (failed)
  prop read: WnlC.QhUXsTuIvfC (failed)
  old prop read: WnlC.QhUXsTuIvfC (failed)
  prop read: /org/freedesktop/Hal/devices/pci_8086_1c2d (failed)
  prop read: pwJ7.M9stt1l6G5F (failed)
  old prop read: pwJ7.M9stt1l6G5F (failed)
  prop read: /org/freedesktop/Hal/devices/pci_8086_1c20 (failed)
  prop read: u1Nb.1uYeENZCMj3 (failed)
  old prop read: u1Nb.1uYeENZCMj3 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_8086_1c10 (failed)
  prop read: z8Q3.phesNusotdE (failed)
  old prop read: z8Q3.phesNusotdE (failed)
  prop read: /org/freedesktop/Hal/devices/pci_8086_244e (failed)
  prop read: QSNP.weqxSdahrgB (failed)
  old prop read: QSNP.weqxSdahrgB (failed)
  prop read: /org/freedesktop/Hal/devices/pci_8086_1c1c (failed)
  prop read: 96M4.+fzr8gdUCp1 (failed)
  old prop read: 96M4.+fzr8gdUCp1 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_8086_1c1e (failed)
  prop read: 0Rrv.1VsL6psuFa2 (failed)
  old prop read: 0Rrv.1VsL6psuFa2 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_8086_1c26 (failed)
  prop read: 1GTX.lFFeW2wAaPC (failed)
  old prop read: 1GTX.lFFeW2wAaPC (failed)
  prop read: /org/freedesktop/Hal/devices/pci_8086_1c46 (failed)
  prop read: BUZT.dAfW+yAcr+A (failed)
  old prop read: BUZT.dAfW+yAcr+A (failed)
  prop read: /org/freedesktop/Hal/devices/pci_8086_1c00 (failed)
  prop read: w7Y8.cfovWppbJa0 (failed)
  old prop read: w7Y8.cfovWppbJa0 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_8086_1c22 (failed)
  prop read: nS1_.D0mtqFziLH4 (failed)
  old prop read: nS1_.D0mtqFziLH4 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_8086_1c08 (failed)
  prop read: W60f.f1Y340iEp20 (failed)
  old prop read: W60f.f1Y340iEp20 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_10de_1200 (failed)
  prop read: B35A.B82sHPIFgb9 (failed)
  old prop read: B35A.B82sHPIFgb9 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_10de_e0c (failed)
  prop read: 2Oa+.Nh5sKK_2me5 (failed)
  old prop read: 2Oa+.Nh5sKK_2me5 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_1b21_1080 (failed)
  prop read: YmUS.HjlkpmuZ2lF (failed)
  old prop read: YmUS.HjlkpmuZ2lF (failed)
  prop read: /org/freedesktop/Hal/devices/pci_10ec_8139 (failed)
  prop read: rBUF.IQxIdIhhuH7 (failed)
  old prop read: rBUF.IQxIdIhhuH7 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_1106_3403 (failed)
  prop read: aK5u.9hCc9oO2Fu1 (failed)
  old prop read: aK5u.9hCc9oO2Fu1 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0a08 (failed)
  prop read: z9pp.+GmdJItMGB9 (failed)
  old prop read: z9pp.+GmdJItMGB9 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0c01 (failed)
  prop read: QL3u.gNN83gfynbD (failed)
  old prop read: QL3u.gNN83gfynbD (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0c02 (failed)
  prop read: tWJy.B+yZ9Ve8gC1 (failed)
  old prop read: tWJy.B+yZ9Ve8gC1 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0501 (failed)
  prop read: KiZ0.BuKI+1soRmD (failed)
  old prop read: KiZ0.BuKI+1soRmD (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0200 (failed)
  prop read: ntp4.ld94kxNGZf5 (failed)
  old prop read: ntp4.ld94kxNGZf5 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0b00 (failed)
  prop read: E349.WYwRElrJa93 (failed)
  old prop read: E349.WYwRElrJa93 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0800 (failed)
  prop read: hEKD.bvKf3UMzZfE (failed)
  old prop read: hEKD.bvKf3UMzZfE (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0c02_0 (failed)
  prop read: NhVi.B+yZ9Ve8gC1 (failed)
  old prop read: NhVi.B+yZ9Ve8gC1 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0c04 (failed)
  prop read: qslm.DE8RM9cWQQ8 (failed)
  old prop read: qslm.DE8RM9cWQQ8 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0c01_0 (failed)
  prop read: H20r.gNN83gfynbD (failed)
  old prop read: H20r.gNN83gfynbD (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_INT3f0d (failed)
  prop read: iT2w.fzmL0Yx8Ld7 (failed)
  old prop read: iT2w.fzmL0Yx8Ld7 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0103 (failed)
  prop read: 9fI_.fG36JLVNse9 (failed)
  old prop read: 9fI_.fG36JLVNse9 (failed)
  prop read: rdCR.7RG8lK_UzJ9 (failed)
  old prop read: rdCR.7RG8lK_UzJ9 (failed)
  prop read: /org/freedesktop/Hal/devices/storage_model_iHAS124___B (failed)
  prop read: KD9E.sO+2qu9J310 (failed)
  old prop read: KD9E.sO+2qu9J310 (failed)
  prop read: /org/freedesktop/Hal/devices/storage_serial_WDC_WD5000AAKX_001CA0_WD_WCAYUR040248 (failed)
  prop read: 3OOL.+OK3+s9JG5A (failed)
  old prop read: 3OOL.+OK3+s9JG5A (failed)
  prop read: /org/freedesktop/Hal/devices/volume_uuid_60C2F3B7C2F39010 (failed)
  prop read: bdUI.SE1wIdpsiiC (failed)
  old prop read: bdUI.SE1wIdpsiiC (failed)
  prop read: /org/freedesktop/Hal/devices/volume_uuid_142CF4E82CF4C5B0 (failed)
  prop read: 2pkM.SE1wIdpsiiC (failed)
  old prop read: 2pkM.SE1wIdpsiiC (failed)
  prop read: /org/freedesktop/Hal/devices/volume_part3_size_1024 (failed)
  prop read: W__Q.SE1wIdpsiiC (failed)
  old prop read: W__Q.SE1wIdpsiiC (failed)
  prop read: /org/freedesktop/Hal/devices/volume_uuid_5de13091_a2a0_467d_a3af_577c9da25d1f (failed)
  prop read: QLVZ.SE1wIdpsiiC (failed)
  old prop read: QLVZ.SE1wIdpsiiC (failed)
  prop read: /org/freedesktop/Hal/devices/volume_uuid_1d541567_4b9a_441b_b8ac_c449be714fb0 (failed)
  prop read: tWld.SE1wIdpsiiC (failed)
  old prop read: tWld.SE1wIdpsiiC (failed)
  prop read: /org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1a_0_if0 (failed)
  prop read: k4bc.FHd55n4xKo7 (failed)
  old prop read: k4bc.FHd55n4xKo7 (failed)
  prop read: /org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_0_if0 (failed)
  prop read: pBe4.oLWCeziExdF (failed)
  old prop read: pBe4.oLWCeziExdF (failed)
  prop read: /org/freedesktop/Hal/devices/usb_device_8087_24_noserial_if0 (failed)
  prop read: ADDn.4Nx_qoDfSd7 (failed)
  old prop read: ADDn.4Nx_qoDfSd7 (failed)
  prop read: /org/freedesktop/Hal/devices/usb_device_8087_24_noserial_0_if0 (failed)
  prop read: FKGF.4Nx_qoDfSd7 (failed)
  old prop read: FKGF.4Nx_qoDfSd7 (failed)
  prop read: /org/freedesktop/Hal/devices/usb_device_5e3_607_noserial_if0 (failed)
  prop read: dwDZ.6jITsy+OI9B (failed)
  old prop read: dwDZ.6jITsy+OI9B (failed)
  prop read: /org/freedesktop/Hal/devices/usb_device_4b4_121f_noserial_if0 (failed)
  prop read: xJ63.nK0zPgdfd0F (failed)
  old prop read: xJ63.nK0zPgdfd0F (failed)
  prop read: /org/freedesktop/Hal/devices/usb_device_3f0_9311_CN0BB3B48F05HX_if0 (failed)
  prop read: Bgjr.kdNv5fskka3 (failed)
  old prop read: Bgjr.kdNv5fskka3 (failed)
  prop read: /org/freedesktop/Hal/devices/usb_device_3f0_9311_CN0BB3B48F05HX_if1_printer_CN0BB3B48F05HX (failed)
  prop read: erzv.G215Op7PdVB (failed)
  old prop read: erzv.G215Op7PdVB (failed)
  prop read: /org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if0_logicaldev_input (failed)
  prop read: doL0.98QTdAHFEQ5 (failed)
  old prop read: doL0.98QTdAHFEQ5 (failed)
  prop read: /org/freedesktop/Hal/devices/usb_device_46d_c22b_noserial_if0_logicaldev_input (failed)
  prop read: fzDf.5FfQhZxjH+6 (failed)
  old prop read: fzDf.5FfQhZxjH+6 (failed)
  prop read: /org/freedesktop/Hal/devices/usb_device_46d_c22b_noserial_if1 (failed)
  prop read: 69Uj.qLka26lJC21 (failed)
  old prop read: 69Uj.qLka26lJC21 (failed)
  prop read: /org/freedesktop/Hal/devices/usb_device_46d_c22a_noserial_if0_logicaldev_input (failed)
  prop read: XEU_.aqigC+p0mc6 (failed)
  old prop read: XEU_.aqigC+p0mc6 (failed)
  prop read: /org/freedesktop/Hal/devices/usb_device_46d_c22a_noserial_if1_logicaldev_input (failed)
  prop read: _Pk2.JxnqZXdcgf0 (failed)
  old prop read: _Pk2.JxnqZXdcgf0 (failed)
  prop read: /org/freedesktop/Hal/devices/computer_logicaldev_input_1 (failed)
  prop read: kZYT.VdKNesd9pT6 (failed)
  old prop read: kZYT.VdKNesd9pT6 (failed)
  prop read: rdCR.j8NaKXDZtZ6 (failed)
  old prop read: rdCR.j8NaKXDZtZ6 (failed)
  prop read: wkFv.j8NaKXDZtZ6 (failed)
  old prop read: wkFv.j8NaKXDZtZ6 (failed)
  prop read: +rIN.j8NaKXDZtZ6 (failed)
  old prop read: +rIN.j8NaKXDZtZ6 (failed)
  prop read: 4zLr.j8NaKXDZtZ6 (failed)
  old prop read: 4zLr.j8NaKXDZtZ6 (failed)
  prop read: ZsBS.GQNx7L4uPNA (failed)
  old prop read: ZsBS.GQNx7L4uPNA (failed)
  prop read: usDW.ndpeucax6V1 (failed)
  old prop read: usDW.ndpeucax6V1 (failed)
  prop read: tovL.GSopYcFr9cF (failed)
  old prop read: tovL.GSopYcFr9cF (failed)
----- /proc/modules -----
  binfmt_misc 6587 1 - Live 0xf9b4d000
  ppdev 5259 0 - Live 0xf9b16000
  ipt_LOG 4542 2 - Live 0xf9121000
  ipt_REJECT 1928 1 - Live 0xf90cf000
  iptable_nat 4414 0 - Live 0xf8f9e000
  nf_nat 15735 1 iptable_nat, Live 0xf8f8b000
  nf_conntrack_ipv4 10672 5 iptable_nat,nf_nat, Live 0xf8768000
  nf_defrag_ipv4 1073 1 nf_conntrack_ipv4, Live 0xf8542000
  iptable_filter 2271 1 - Live 0xf852d000
  ip_tables 9991 2 iptable_nat,iptable_filter, Live 0xf847a000
  ip6t_LOG 4669 2 - Live 0xf8430000
  xt_limit 1382 4 - Live 0xf8425000
  ip6t_REJECT 2572 1 - Live 0xf841b000
  xt_tcpudp 2011 72 - Live 0xf8411000
  ip6t_ah 993 1 - Live 0xf8407000
  nf_conntrack_ipv6 10447 2 - Live 0xf83e9000
  xt_state 1098 4 - Live 0xf83bb000
  ip6table_filter 2343 1 - Live 0xf8248000
  ip6_tables 11227 3 ip6t_LOG,ip6t_ah,ip6table_filter, Live 0xf82bf000
  x_tables 14299 11 ipt_LOG,ipt_REJECT,iptable_nat,ip_tables,ip6t_LOG,xt_limit,ip6t_REJECT,xt_tcpudp,ip6t_ah,xt_state,ip6_tables, Live 0xf82ad000
  snd_hda_codec_realtek 203440 0 - Live 0xf843f000
  snd_hda_intel 22165 2 - Live 0xfa9f1000
  snd_hda_codec 74201 2 snd_hda_codec_realtek,snd_hda_intel, Live 0xfa9c4000
  snd_usb_audio 75861 1 - Live 0xfa993000
  snd_pcm_oss 35308 0 - Live 0xf9104000
  snd_mixer_oss 13746 1 snd_pcm_oss, Live 0xf8f82000
  snd_pcm 70918 4 snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss, Live 0xf90e3000
  snd_seq_dummy 1338 0 - Live 0xf833c000
  snd_usb_lib 15833 1 snd_usb_audio, Live 0xf874e000
  snd_seq_oss 26722 0 - Live 0xf8f95000
  snd_seq_midi 4557 0 - Live 0xf83bf000
  snd_seq_midi_event 6003 2 snd_seq_oss,snd_seq_midi, Live 0xf82e6000
  snd_seq 47263 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event, Live 0xf8482000
  snd_timer 19130 2 snd_pcm,snd_seq, Live 0xf825c000
  nvidia 10777633 42 - Live 0xf9ed2000 (P)
  snd_rawmidi 19056 2 snd_usb_lib,snd_seq_midi, Live 0xf8351000
  usblp 10481 0 - Live 0xf832c000
  uvcvideo 57470 0 - Live 0xf83d5000
  videodev 34425 1 uvcvideo, Live 0xf835e000
  v4l1_compat 13251 2 uvcvideo,videodev, Live 0xf82b4000
  snd_seq_device 5700 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi, Live 0xf82a9000
  snd_hwdep 5412 2 snd_hda_codec,snd_usb_audio, Live 0xf8253000
  shpchp 28899 0 - Live 0xf8322000
  psmouse 63677 0 - Live 0xf838c000
  snd 54244 19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_rawmidi,snd_seq_device,snd_hwdep, Live 0xf828d000
  serio_raw 3978 0 - Live 0xf824a000
  lp 7028 0 - Live 0xf9124000
  parport 32635 2 ppdev,lp, Live 0xf910f000
  soundcore 6620 1 snd, Live 0xf90f8000
  snd_page_alloc 7172 2 snd_hda_intel,snd_pcm, Live 0xf8fa1000
  nf_conntrack_ftp 5381 0 - Live 0xf875f000
  nf_conntrack 61615 6 iptable_nat,nf_nat,nf_conntrack_ipv4,nf_conntrack_ipv6,xt_state,nf_conntrack_ftp, Live 0xf90d1000
  aes_i586 7268 2 - Live 0xf8357000
  aes_generic 26863 1 aes_i586, Live 0xf8330000
  xts 2031 1 - Live 0xf831f000
  gf128mul 8015 1 xts, Live 0xf8314000
  dm_crypt 11331 1 - Live 0xf827a000
  dm_raid45 81647 0 - Live 0xf82c5000
  xor 15028 1 dm_raid45, Live 0xf824d000
  fbcon 35102 71 - Live 0xf8fa5000
  tileblit 1999 1 fbcon, Live 0xf8f92000
  font 7557 1 fbcon, Live 0xf8f87000
  bitblit 4707 1 fbcon, Live 0xf8778000
  softcursor 1189 1 bitblit, Live 0xf876e000
  vga16fb 11385 1 - Live 0xf8763000
  vgastate 8961 1 vga16fb, Live 0xf8754000
  8139too 18673 0 - Live 0xf853b000
  nouveau 467624 0 - Live 0xf8491000
  usbhid 36206 0 - Live 0xf83ed000
  ttm 49943 1 nouveau, Live 0xf83c6000
  drm_kms_helper 29329 1 nouveau, Live 0xf83a1000
  ohci1394 27238 0 - Live 0xf8383000
  8139cp 16602 0 - Live 0xf836b000
  mii 4381 2 8139too,8139cp, Live 0xf835a000
  hid 67288 1 usbhid, Live 0xf833e000
  drm 164436 3 nouveau,ttm,drm_kms_helper, Live 0xf82e9000
  agpgart 31788 3 nvidia,ttm,drm, Live 0xf829f000
  i2c_algo_bit 5028 1 nouveau, Live 0xf8289000
  ieee1394 81213 1 ohci1394, Live 0xf8264000
----- /proc/modules end -----
  used irqs: 0,1,4,5,8,9,11,12,14,15,16,17,19,22,23,24,25,26,27,28
=========== end debug info ============
01: None 00.0: 10105 BIOS
  [Created at bios.190]
  Unique ID: rdCR.lZF+r4EgHp4
  Hardware Class: bios
  BIOS Keyboard LED Status:
    Scroll Lock: off
    Num Lock: off
    Caps Lock: off
  Config Status: cfg=new, avail=yes, need=no, active=unknown

02: None 00.0: 10107 System
  [Created at sys.63]
  Unique ID: rdCR.n_7QNeEnh23
  Hardware Class: system
  Model: "System"
  Formfactor: "desktop"
  Driver Info #0:
    Driver Status: thermal,fan are not active
    Driver Activation Cmd: "modprobe thermal; modprobe fan"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

03: None 00.0: 10104 FPU
  [Created at misc.192]
  Unique ID: rdCR.EMpH5pjcahD
  Hardware Class: unknown
  Model: "FPU"
  I/O Ports: 0xf0-0xff (rw)
  Config Status: cfg=new, avail=yes, need=no, active=unknown

04: None 00.0: 0801 DMA controller (8237)
  [Created at misc.206]
  Unique ID: rdCR.f5u1ucRm+H9
  Hardware Class: unknown
  Model: "DMA controller"
  I/O Ports: 0x00-0x1f (rw)
  I/O Ports: 0xc0-0xdf (rw)
  I/O Ports: 0x80-0x8f (rw)
  DMA: 4
  Config Status: cfg=new, avail=yes, need=no, active=unknown

05: None 00.0: 0800 PIC (8259)
  [Created at misc.219]
  Unique ID: rdCR.8uRK7LxiIA2
  Hardware Class: unknown
  Model: "PIC"
  I/O Ports: 0x20-0x21 (rw)
  I/O Ports: 0xa0-0xa1 (rw)
  Config Status: cfg=new, avail=yes, need=no, active=unknown

06: None 00.0: 0802 Timer (8254)
  [Created at misc.230]
  Unique ID: rdCR.AJKleuxpiP0
  Hardware Class: unknown
  Model: "Timer"
  IRQ: 0 (74 events)
  Config Status: cfg=new, avail=yes, need=no, active=unknown

07: None 00.0: 0900 Keyboard controller
  [Created at misc.251]
  Unique ID: rdCR.9N+EecqykME
  Hardware Class: unknown
  Model: "Keyboard controller"
  I/O Port: 0x60 (rw)
  I/O Port: 0x64 (rw)
  Config Status: cfg=new, avail=yes, need=no, active=unknown

12: None 00.0: 10102 Main Memory
  [Created at memory.61]
  Unique ID: rdCR.CxwsZFjVASF
  Hardware Class: memory
  Model: "Main Memory"
  Memory Range: 0x00000000-0xfa4fafff (rw)
  Memory Size: 4 GB
  Config Status: cfg=new, avail=yes, need=no, active=unknown

13: PCI 00.0: 0600 Host bridge
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_100
  Unique ID: qLht.+ULmzmJCXV7
  SysFS ID: /devices/pci0000:00/0000:00:00.0
  SysFS BusID: 0000:00:00.0
  Hardware Class: bridge
  Model: "Intel Host bridge"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x0100 
  SubVendor: pci 0x1462 "Micro-Star International Co., Ltd."
  SubDevice: pci 0x7681 
  Revision: 0x09
  Module Alias: "pci:v00008086d00000100sv00001462sd00007681bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

14: PCI 01.0: 0604 PCI bridge (Normal decode)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_101
  Unique ID: vSkL.5yyCfy3P7oD
  SysFS ID: /devices/pci0000:00/0000:00:01.0
  SysFS BusID: 0000:00:01.0
  Hardware Class: bridge
  Model: "Intel PCI bridge"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x0101 
  Revision: 0x09
  Driver: "pcieport"
  IRQ: 24 (no events)
  Module Alias: "pci:v00008086d00000101sv00000000sd00000000bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

15: PCI 01.1: 0604 PCI bridge (Normal decode)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_105
  Unique ID: mnDB.9ckCaEYDEKF
  SysFS ID: /devices/pci0000:00/0000:00:01.1
  SysFS BusID: 0000:00:01.1
  Hardware Class: bridge
  Model: "Intel PCI bridge"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x0105 
  Revision: 0x09
  Driver: "pcieport"
  IRQ: 25 (no events)
  Module Alias: "pci:v00008086d00000105sv00000000sd00000000bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

16: PCI 16.0: 0780 Communication controller
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_1c3a
  Unique ID: WnlC.QhUXsTuIvfC
  SysFS ID: /devices/pci0000:00/0000:00:16.0
  SysFS BusID: 0000:00:16.0
  Hardware Class: unknown
  Model: "Intel Communication controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x1c3a 
  SubVendor: pci 0x1462 "Micro-Star International Co., Ltd."
  SubDevice: pci 0x7673 
  Revision: 0x04
  Memory Range: 0xfa307000-0xfa30700f (rw,non-prefetchable)
  IRQ: 11 (no events)
  Module Alias: "pci:v00008086d00001C3Asv00001462sd00007673bc07sc80i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

17: PCI 1a.0: 0c03 USB Controller (EHCI)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_1c2d
  Unique ID: pwJ7.M9stt1l6G5F
  SysFS ID: /devices/pci0000:00/0000:00:1a.0
  SysFS BusID: 0000:00:1a.0
  Hardware Class: usb controller
  Model: "Intel USB Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x1c2d 
  SubVendor: pci 0x1462 "Micro-Star International Co., Ltd."
  SubDevice: pci 0x7673 
  Revision: 0x05
  Driver: "ehci_hcd"
  Driver Modules: "ehci_hcd"
  Memory Range: 0xfa306000-0xfa3063ff (rw,non-prefetchable)
  IRQ: 16 (140763 events)
  Module Alias: "pci:v00008086d00001C2Dsv00001462sd00007673bc0Csc03i20"
  Driver Info #0:
    Driver Status: ehci-hcd is not active
    Driver Activation Cmd: "modprobe ehci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

18: PCI 1b.0: 0403 Audio device
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_1c20
  Unique ID: u1Nb.1uYeENZCMj3
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "Intel Audio device"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x1c20 
  SubVendor: pci 0x1462 "Micro-Star International Co., Ltd."
  SubDevice: pci 0x7673 
  Revision: 0x05
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfa300000-0xfa303fff (rw,non-prefetchable)
  IRQ: 22 (634 events)
  Module Alias: "pci:v00008086d00001C20sv00001462sd00007673bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

19: PCI 1c.0: 0604 PCI bridge (Normal decode)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_1c10
  Unique ID: z8Q3.phesNusotdE
  SysFS ID: /devices/pci0000:00/0000:00:1c.0
  SysFS BusID: 0000:00:1c.0
  Hardware Class: bridge
  Model: "Intel PCI bridge"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x1c10 
  Revision: 0xb5
  Driver: "pcieport"
  IRQ: 26 (no events)
  Module Alias: "pci:v00008086d00001C10sv00000000sd00000000bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

20: PCI 1c.4: 0604 PCI bridge (Subtractive decode)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_244e
  Unique ID: QSNP.weqxSdahrgB
  SysFS ID: /devices/pci0000:00/0000:00:1c.4
  SysFS BusID: 0000:00:1c.4
  Hardware Class: bridge
  Model: "Intel 82801 PCI Bridge"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x244e "82801 PCI Bridge"
  Revision: 0xb5
  IRQ: 17 (200036 events)
  Module Alias: "pci:v00008086d0000244Esv00000000sd00000000bc06sc04i01"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

21: PCI 1c.6: 0604 PCI bridge (Normal decode)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_1c1c
  Unique ID: 96M4.+fzr8gdUCp1
  SysFS ID: /devices/pci0000:00/0000:00:1c.6
  SysFS BusID: 0000:00:1c.6
  Hardware Class: bridge
  Model: "Intel PCI bridge"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x1c1c 
  Revision: 0xb5
  Driver: "pcieport"
  IRQ: 27 (no events)
  Module Alias: "pci:v00008086d00001C1Csv00000000sd00000000bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

22: PCI 1c.7: 0604 PCI bridge (Normal decode)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_1c1e
  Unique ID: 0Rrv.1VsL6psuFa2
  SysFS ID: /devices/pci0000:00/0000:00:1c.7
  SysFS BusID: 0000:00:1c.7
  Hardware Class: bridge
  Model: "Intel PCI bridge"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x1c1e 
  Revision: 0xb5
  Driver: "pcieport"
  IRQ: 28 (no events)
  Module Alias: "pci:v00008086d00001C1Esv00000000sd00000000bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

23: PCI 1d.0: 0c03 USB Controller (EHCI)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_1c26
  Unique ID: 1GTX.lFFeW2wAaPC
  SysFS ID: /devices/pci0000:00/0000:00:1d.0
  SysFS BusID: 0000:00:1d.0
  Hardware Class: usb controller
  Model: "Intel USB Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x1c26 
  SubVendor: pci 0x1462 "Micro-Star International Co., Ltd."
  SubDevice: pci 0x7673 
  Revision: 0x05
  Driver: "ehci_hcd"
  Driver Modules: "ehci_hcd"
  Memory Range: 0xfa305000-0xfa3053ff (rw,non-prefetchable)
  IRQ: 23 (10938 events)
  Module Alias: "pci:v00008086d00001C26sv00001462sd00007673bc0Csc03i20"
  Driver Info #0:
    Driver Status: ehci-hcd is not active
    Driver Activation Cmd: "modprobe ehci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

24: PCI 1f.0: 0601 ISA bridge
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_1c46
  Unique ID: BUZT.dAfW+yAcr+A
  SysFS ID: /devices/pci0000:00/0000:00:1f.0
  SysFS BusID: 0000:00:1f.0
  Hardware Class: bridge
  Model: "Intel ISA bridge"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x1c46 
  SubVendor: pci 0x1462 "Micro-Star International Co., Ltd."
  SubDevice: pci 0x7673 
  Revision: 0x05
  Module Alias: "pci:v00008086d00001C46sv00001462sd00007673bc06sc01i00"
  Driver Info #0:
    Driver Status: iTCO_wdt is not active
    Driver Activation Cmd: "modprobe iTCO_wdt"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

25: PCI 1f.2: 0101 IDE interface
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_1c00
  Unique ID: w7Y8.cfovWppbJa0
  SysFS ID: /devices/pci0000:00/0000:00:1f.2
  SysFS BusID: 0000:00:1f.2
  Hardware Class: storage
  Model: "Intel IDE interface"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x1c00 
  SubVendor: pci 0x1462 "Micro-Star International Co., Ltd."
  SubDevice: pci 0x7673 
  Revision: 0x05
  Driver: "ata_piix"
  I/O Ports: 0x1f0-0x1f7 (rw)
  I/O Port: 0x3f6 (rw)
  I/O Ports: 0x170-0x177 (rw)
  I/O Port: 0x376 (rw)
  I/O Ports: 0xf090-0xf09f (rw)
  I/O Ports: 0xf080-0xf08f (rw)
  IRQ: 19 (2 events)
  Module Alias: "pci:v00008086d00001C00sv00001462sd00007673bc01sc01i8a"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

26: PCI 1f.3: 0c05 SMBus
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_1c22
  Unique ID: nS1_.D0mtqFziLH4
  SysFS ID: /devices/pci0000:00/0000:00:1f.3
  SysFS BusID: 0000:00:1f.3
  Hardware Class: unknown
  Model: "Intel SMBus"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x1c22 
  SubVendor: pci 0x1462 "Micro-Star International Co., Ltd."
  SubDevice: pci 0x7673 
  Revision: 0x05
  Memory Range: 0xfa304000-0xfa3040ff (rw,non-prefetchable)
  I/O Ports: 0xf000-0xf01f (rw)
  IRQ: 5 (no events)
  Module Alias: "pci:v00008086d00001C22sv00001462sd00007673bc0Csc05i00"
  Driver Info #0:
    Driver Status: i2c_i801 is not active
    Driver Activation Cmd: "modprobe i2c_i801"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

27: PCI 1f.5: 0101 IDE interface
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_1c08
  Unique ID: W60f.f1Y340iEp20
  SysFS ID: /devices/pci0000:00/0000:00:1f.5
  SysFS BusID: 0000:00:1f.5
  Hardware Class: storage
  Model: "Intel IDE interface"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x1c08 
  SubVendor: pci 0x1462 "Micro-Star International Co., Ltd."
  SubDevice: pci 0x7673 
  Revision: 0x05
  Driver: "ata_piix"
  I/O Ports: 0xf070-0xf077 (rw)
  I/O Ports: 0xf060-0xf063 (rw)
  I/O Ports: 0xf050-0xf057 (rw)
  I/O Ports: 0xf040-0xf043 (rw)
  I/O Ports: 0xf030-0xf03f (rw)
  I/O Ports: 0xf020-0xf02f (rw)
  IRQ: 19 (2 events)
  Module Alias: "pci:v00008086d00001C08sv00001462sd00007673bc01sc01i85"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

28: PCI 200.0: 0300 VGA compatible controller (VGA)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10de_1200
  Unique ID: B35A.B82sHPIFgb9
  Parent ID: mnDB.9ckCaEYDEKF
  SysFS ID: /devices/pci0000:00/0000:00:01.1/0000:02:00.0
  SysFS BusID: 0000:02:00.0
  Hardware Class: graphics card
  Model: "nVidia VGA compatible controller"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x1200 
  SubVendor: pci 0x1462 "Micro-Star International Co., Ltd."
  SubDevice: pci 0x2382 
  Revision: 0xa1
  Driver: "nvidia"
  Driver Modules: "nvidia"
  Memory Range: 0xf8000000-0xf9ffffff (rw,non-prefetchable)
  Memory Range: 0xd0000000-0xd7ffffff (rw,prefetchable)
  Memory Range: 0xd8000000-0xdbffffff (rw,prefetchable)
  I/O Ports: 0xe000-0xefff (rw)
  Memory Range: 0xfa000000-0xfa07ffff (ro,prefetchable,disabled)
  IRQ: 17 (200036 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v000010DEd00001200sv00001462sd00002382bc03sc00i00"
  Driver Info #0:
    Driver Status: nouveau is active
    Driver Activation Cmd: "modprobe nouveau"
  Driver Info #1:
    Driver Status: nvidiafb is not active
    Driver Activation Cmd: "modprobe nvidiafb"
  Driver Info #2:
    Driver Status: nvidia is active
    Driver Activation Cmd: "modprobe nvidia"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #15 (PCI bridge)

29: PCI 200.1: 0403 Audio device
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10de_e0c
  Unique ID: 2Oa+.Nh5sKK_2me5
  Parent ID: mnDB.9ckCaEYDEKF
  SysFS ID: /devices/pci0000:00/0000:00:01.1/0000:02:00.1
  SysFS BusID: 0000:02:00.1
  Hardware Class: sound
  Model: "nVidia Audio device"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x0e0c 
  SubVendor: pci 0x1462 "Micro-Star International Co., Ltd."
  SubDevice: pci 0x2382 
  Revision: 0xa1
  Memory Range: 0xfa080000-0xfa083fff (rw,non-prefetchable)
  IRQ: 5 (no events)
  Module Alias: "pci:v000010DEd00000E0Csv00001462sd00002382bc04sc03i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #15 (PCI bridge)

30: PCI 400.0: 0604 PCI bridge (Normal decode)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1b21_1080
  Unique ID: YmUS.HjlkpmuZ2lF
  Parent ID: QSNP.weqxSdahrgB
  SysFS ID: /devices/pci0000:00/0000:00:1c.4/0000:04:00.0
  SysFS BusID: 0000:04:00.0
  Hardware Class: bridge
  Model: "PCI bridge"
  Vendor: pci 0x1b21 
  Device: pci 0x1080 
  Revision: 0x01
  IRQ: 16 (140763 events)
  Module Alias: "pci:v00001B21d00001080sv00000000sd00000000bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #20 (PCI bridge)

31: PCI 501.0: 0200 Ethernet controller
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10ec_8139
  Unique ID: rBUF.IQxIdIhhuH7
  Parent ID: YmUS.HjlkpmuZ2lF
  SysFS ID: /devices/pci0000:00/0000:00:1c.4/0000:04:00.0/0000:05:01.0
  SysFS BusID: 0000:05:01.0
  Hardware Class: network
  Model: "Realtek RT8139"
  Vendor: pci 0x10ec "Realtek Semiconductor Co., Ltd."
  Device: pci 0x8139 "RTL-8139/8139C/8139C+"
  SubVendor: pci 0x10ec "Realtek Semiconductor Co., Ltd."
  SubDevice: pci 0x8139 "RT8139"
  Revision: 0x10
  Driver: "8139too"
  Driver Modules: "8139too"
  Device File: eth0
  I/O Ports: 0xd000-0xdfff (rw)
  Memory Range: 0xfa220000-0xfa2200ff (rw,non-prefetchable)
  Memory Range: 0xfa200000-0xfa21ffff (ro,prefetchable,disabled)
  IRQ: 17 (200036 events)
  HW Address: 00:16:0a:07:ad:dd
  Link detected: yes
  Module Alias: "pci:v000010ECd00008139sv000010ECsd00008139bc02sc00i00"
  Driver Info #0:
    Driver Status: 8139too is active
    Driver Activation Cmd: "modprobe 8139too"
  Driver Info #1:
    Driver Status: 8139cp is active
    Driver Activation Cmd: "modprobe 8139cp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #30 (PCI bridge)

32: PCI 700.0: 0c00 FireWire (IEEE 1394) (OHCI)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1106_3403
  Unique ID: aK5u.9hCc9oO2Fu1
  Parent ID: 0Rrv.1VsL6psuFa2
  SysFS ID: /devices/pci0000:00/0000:00:1c.7/0000:07:00.0
  SysFS BusID: 0000:07:00.0
  Hardware Class: firewire controller
  Model: "VIA FireWire (IEEE 1394)"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x3403 
  SubVendor: pci 0x1462 "Micro-Star International Co., Ltd."
  SubDevice: pci 0x673d 
  Revision: 0x01
  Driver: "ohci1394"
  Driver Modules: "ohci1394"
  Memory Range: 0xfa100000-0xfa1007ff (rw,non-prefetchable)
  I/O Ports: 0xc000-0xcfff (rw)
  IRQ: 19 (2 events)
  Module Alias: "pci:v00001106d00003403sv00001462sd0000673Dbc0Csc00i10"
  Driver Info #0:
    Driver Status: ohci1394 is active
    Driver Activation Cmd: "modprobe ohci1394"
  Driver Info #1:
    Driver Status: firewire_ohci is not active
    Driver Activation Cmd: "modprobe firewire_ohci"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #22 (PCI bridge)

33: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0a08
  Unique ID: z9pp.+GmdJItMGB9
  SysFS ID: /devices/pnp0/00:00
  SysFS BusID: 00:00
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0a08 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

34: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0c01
  Unique ID: QL3u.gNN83gfynbD
  SysFS ID: /devices/pnp0/00:01
  SysFS BusID: 00:01
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c01 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

35: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0c02
  Unique ID: tWJy.B+yZ9Ve8gC1
  SysFS ID: /devices/pnp0/00:02
  SysFS BusID: 00:02
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c02 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

36: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0501
  Unique ID: KiZ0.BuKI+1soRmD
  SysFS ID: /devices/pnp0/00:03
  SysFS BusID: 00:03
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0501 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

37: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0200
  Unique ID: ntp4.ld94kxNGZf5
  SysFS ID: /devices/pnp0/00:04
  SysFS BusID: 00:04
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0200 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

38: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0b00
  Unique ID: E349.WYwRElrJa93
  SysFS ID: /devices/pnp0/00:05
  SysFS BusID: 00:05
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0b00 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

39: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0800
  Unique ID: hEKD.bvKf3UMzZfE
  SysFS ID: /devices/pnp0/00:06
  SysFS BusID: 00:06
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0800 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

40: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0c02_0
  Unique ID: NhVi.B+yZ9Ve8gC1
  SysFS ID: /devices/pnp0/00:07
  SysFS BusID: 00:07
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c02 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

41: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0c04
  Unique ID: qslm.DE8RM9cWQQ8
  SysFS ID: /devices/pnp0/00:08
  SysFS BusID: 00:08
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c04 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

42: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0c01_0
  Unique ID: H20r.gNN83gfynbD
  SysFS ID: /devices/pnp0/00:09
  SysFS BusID: 00:09
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c01 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

43: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_INT3f0d
  Unique ID: iT2w.fzmL0Yx8Ld7
  SysFS ID: /devices/pnp0/00:0a
  SysFS BusID: 00:0a
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: INT 
  SubDevice: eisa 0x3f0d 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

44: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0103
  Unique ID: 9fI_.fG36JLVNse9
  SysFS ID: /devices/pnp0/00:0b
  SysFS BusID: 00:0b
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0103 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

45: None 00.0: 0700 Serial controller
  [Created at misc.449]
  Unique ID: rdCR.7RG8lK_UzJ9
  Hardware Class: unknown
  Model: "Serial controller"
  I/O Ports: 0x3f8-0x3ff (rw)
  IRQ: 4 (7 events)
  Config Status: cfg=new, avail=yes, need=no, active=unknown

46: SCSI 00.0: 10602 CD-ROM
  [Created at block.247]
  UDI: /org/freedesktop/Hal/devices/storage_model_iHAS124___B
  Unique ID: KD9E.sO+2qu9J310
  Parent ID: w7Y8.cfovWppbJa0
  SysFS ID: /class/block/sr0
  SysFS BusID: 0:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0
  Hardware Class: cdrom
  Model: "ATAPI iHAS124   B"
  Vendor: "ATAPI"
  Device: "iHAS124   B"
  Revision: "AL0Q"
  Driver: "ata_piix", "sr"
  Device File: /dev/sr0 (/dev/sg0)
  Device Files: /dev/sr0, /dev/block/11:0, /dev/scd0, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0, /dev/cdrom, /dev/cdrw, /dev/dvd, /dev/dvdrw
  Device Number: block 11:0 (char 21:0)
  Features: CD-R, CD-RW, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+DL, DVDRAM
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #25 (IDE interface)
  Drive Speed: 48

47: IDE 100.0: 10600 Disk
  [Created at block.243]
  UDI: /org/freedesktop/Hal/devices/storage_serial_WDC_WD5000AAKX_001CA0_WD_WCAYUR040248
  Unique ID: 3OOL.+OK3+s9JG5A
  Parent ID: w7Y8.cfovWppbJa0
  SysFS ID: /class/block/sda
  SysFS BusID: 1:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0
  Hardware Class: disk
  Model: "WDC WD5000AAKX-0"
  Vendor: "WDC"
  Device: "WD5000AAKX-0"
  Revision: "15.0"
  Driver: "ata_piix", "sd"
  Device File: /dev/sda
  Device Files: /dev/sda, /dev/block/8:0, /dev/disk/by-id/ata-WDC_WD5000AAKX-001CA0_WD-WCAYUR040248, /dev/disk/by-id/scsi-SATA_WDC_WD5000AAKX-_WD-WCAYUR040248, /dev/disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0, /dev/disk/by-id/wwn-0x50014ee1ae9d87ac
  Device Number: block 8:0-8:15
  BIOS id: 0x80
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #25 (IDE interface)

48: None 00.0: 11300 Partition
  [Created at block.412]
  UDI: /org/freedesktop/Hal/devices/volume_uuid_60C2F3B7C2F39010
  Unique ID: bdUI.SE1wIdpsiiC
  Parent ID: 3OOL.+OK3+s9JG5A
  SysFS ID: /class/block/sda/sda1
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda1
  Device Files: /dev/sda1, /dev/block/8:1, /dev/disk/by-id/ata-WDC_WD5000AAKX-001CA0_WD-WCAYUR040248-part1, /dev/disk/by-id/scsi-SATA_WDC_WD5000AAKX-_WD-WCAYUR040248-part1, /dev/disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0-part1, /dev/disk/by-uuid/60C2F3B7C2F39010, /dev/disk/by-label/System\x20Reserved, /dev/disk/by-id/wwn-0x50014ee1ae9d87ac-part1
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #47 (Disk)

49: None 00.0: 11300 Partition
  [Created at block.412]
  UDI: /org/freedesktop/Hal/devices/volume_uuid_142CF4E82CF4C5B0
  Unique ID: 2pkM.SE1wIdpsiiC
  Parent ID: 3OOL.+OK3+s9JG5A
  SysFS ID: /class/block/sda/sda2
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda2
  Device Files: /dev/sda2, /dev/block/8:2, /dev/disk/by-id/ata-WDC_WD5000AAKX-001CA0_WD-WCAYUR040248-part2, /dev/disk/by-id/scsi-SATA_WDC_WD5000AAKX-_WD-WCAYUR040248-part2, /dev/disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0-part2, /dev/disk/by-uuid/142CF4E82CF4C5B0, /dev/disk/by-id/wwn-0x50014ee1ae9d87ac-part2
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #47 (Disk)

50: None 00.0: 11300 Partition
  [Created at block.412]
  UDI: /org/freedesktop/Hal/devices/volume_part3_size_1024
  Unique ID: W__Q.SE1wIdpsiiC
  Parent ID: 3OOL.+OK3+s9JG5A
  SysFS ID: /class/block/sda/sda3
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda3
  Device Files: /dev/sda3, /dev/block/8:3, /dev/disk/by-id/ata-WDC_WD5000AAKX-001CA0_WD-WCAYUR040248-part3, /dev/disk/by-id/scsi-SATA_WDC_WD5000AAKX-_WD-WCAYUR040248-part3, /dev/disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0-part3, /dev/disk/by-id/wwn-0x50014ee1ae9d87ac-part3
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #47 (Disk)

51: None 00.0: 11300 Partition
  [Created at block.412]
  UDI: /org/freedesktop/Hal/devices/volume_uuid_5de13091_a2a0_467d_a3af_577c9da25d1f
  Unique ID: QLVZ.SE1wIdpsiiC
  Parent ID: 3OOL.+OK3+s9JG5A
  SysFS ID: /class/block/sda/sda5
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda5
  Device Files: /dev/sda5, /dev/block/8:5, /dev/disk/by-id/ata-WDC_WD5000AAKX-001CA0_WD-WCAYUR040248-part5, /dev/disk/by-id/scsi-SATA_WDC_WD5000AAKX-_WD-WCAYUR040248-part5, /dev/disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0-part5, /dev/disk/by-uuid/5de13091-a2a0-467d-a3af-577c9da25d1f, /dev/disk/by-id/wwn-0x50014ee1ae9d87ac-part5
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #47 (Disk)

52: None 00.0: 11300 Partition
  [Created at block.412]
  UDI: /org/freedesktop/Hal/devices/volume_uuid_1d541567_4b9a_441b_b8ac_c449be714fb0
  Unique ID: tWld.SE1wIdpsiiC
  Parent ID: 3OOL.+OK3+s9JG5A
  SysFS ID: /class/block/sda/sda6
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda6
  Device Files: /dev/sda6, /dev/block/8:6, /dev/disk/by-id/ata-WDC_WD5000AAKX-001CA0_WD-WCAYUR040248-part6, /dev/disk/by-id/scsi-SATA_WDC_WD5000AAKX-_WD-WCAYUR040248-part6, /dev/disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0-part6, /dev/disk/by-uuid/1d541567-4b9a-441b-b8ac-c449be714fb0, /dev/disk/by-id/wwn-0x50014ee1ae9d87ac-part6
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #47 (Disk)

53: USB 00.0: 10a00 Hub
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1a_0_if0
  Unique ID: k4bc.FHd55n4xKo7
  Parent ID: pwJ7.M9stt1l6G5F
  SysFS ID: /devices/pci0000:00/0000:00:1a.0/usb1/1-0:1.0
  SysFS BusID: 1-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.32-38-generic-pae ehci_hcd EHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.32-38-generic-pae ehci_hcd"
  Device: usb 0x0002 "EHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:1a.0"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #17 (USB Controller)

54: USB 00.0: 10a00 Hub
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_0_if0
  Unique ID: pBe4.oLWCeziExdF
  Parent ID: 1GTX.lFFeW2wAaPC
  SysFS ID: /devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0
  SysFS BusID: 2-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.32-38-generic-pae ehci_hcd EHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.32-38-generic-pae ehci_hcd"
  Device: usb 0x0002 "EHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:1d.0"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #23 (USB Controller)

55: USB 00.0: 10a00 Hub
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_8087_24_noserial_if0
  Unique ID: ADDn.4Nx_qoDfSd7
  Parent ID: k4bc.FHd55n4xKo7
  SysFS ID: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1:1.0
  SysFS BusID: 1-1:1.0
  Hardware Class: hub
  Model: "Hub"
  Hotplug: USB
  Vendor: usb 0x8087 
  Device: usb 0x0024 
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #53 (Hub)

56: USB 00.0: 10a00 Hub
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_8087_24_noserial_0_if0
  Unique ID: FKGF.4Nx_qoDfSd7
  Parent ID: pBe4.oLWCeziExdF
  SysFS ID: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0
  SysFS BusID: 2-1:1.0
  Hardware Class: hub
  Model: "Hub"
  Hotplug: USB
  Vendor: usb 0x8087 
  Device: usb 0x0024 
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #54 (Hub)

57: USB 00.0: 10a00 Hub
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_5e3_607_noserial_if0
  Unique ID: dwDZ.6jITsy+OI9B
  Parent ID: ADDn.4Nx_qoDfSd7
  SysFS ID: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0
  SysFS BusID: 1-1.3:1.0
  Hardware Class: hub
  Model: "Genesys Logic USB2.0 Hub"
  Hotplug: USB
  Vendor: usb 0x05e3 "Genesys Logic, Inc."
  Device: usb 0x0607 "USB2.0 Hub"
  Revision: "8.01"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v05E3p0607d0801dc09dsc00dp02ic09isc00ip02"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #55 (Hub)

58: USB 00.0: 10503 USB Mouse
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_4b4_121f_noserial_if0
  Unique ID: xJ63.nK0zPgdfd0F
  Parent ID: ADDn.4Nx_qoDfSd7
  SysFS ID: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0
  SysFS BusID: 1-1.6:1.0
  Hardware Class: mouse
  Model: "Cypress Ikari Laser"
  Hotplug: USB
  Vendor: usb 0x04b4 "Cypress Semiconductor Corp."
  Device: usb 0x121f "Ikari Laser"
  Revision: "1.00"
  Compatible to: int 0x0210 0x0017
  Driver: "usbhid"
  Driver Modules: "usbhid"
  Device File: /dev/input/mice (/dev/input/mouse1)
  Device Files: /dev/input/mice, /dev/input/mouse1, /dev/input/event3, /dev/char/13:67, /dev/input/by-id/usb-SteelSeries_ApS_Ikari_Laser-event-mouse, /dev/input/by-path/pci-0000:00:1a.0-usb-0:1.6:1.0-event-mouse, /dev/char/13:33, /dev/input/by-id/usb-SteelSeries_ApS_Ikari_Laser-mouse, /dev/input/by-path/pci-0000:00:1a.0-usb-0:1.6:1.0-mouse, /dev/char/13:63
  Device Number: char 13:63 (char 13:33)
  Speed: 12 Mbps
  Module Alias: "usb:v04B4p121Fd0100dc00dsc00dp00ic03isc01ip02"
  Driver Info #0:
    Buttons: 7
    Wheels: 1
    XFree86 Protocol: explorerps/2
    GPM Protocol: exps2
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #55 (Hub)

59: USB 00.0: 0000 Unclassified device
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_3f0_9311_CN0BB3B48F05HX_if0
  Unique ID: Bgjr.kdNv5fskka3
  Parent ID: FKGF.4Nx_qoDfSd7
  SysFS ID: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0
  SysFS BusID: 2-1.5:1.0
  Hardware Class: unknown
  Model: "HP Deskjet 3050 J610 series"
  Hotplug: USB
  Vendor: usb 0x03f0 "HP"
  Device: usb 0x9311 "Deskjet 3050 J610 series"
  Revision: "1.00"
  Serial ID: "CN0BB3B48F05HX"
  Speed: 480 Mbps
  Module Alias: "usb:v03F0p9311d0100dc00dsc00dp00icFFiscCCip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #56 (Hub)

60: USB 00.1: 10900 Printer
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_3f0_9311_CN0BB3B48F05HX_if1_printer_CN0BB3B48F05HX
  Unique ID: erzv.G215Op7PdVB
  Parent ID: FKGF.4Nx_qoDfSd7
  SysFS ID: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.1
  SysFS BusID: 2-1.5:1.1
  Hardware Class: printer
  Model: "HP Deskjet 3050 J610 series"
  Hotplug: USB
  Vendor: usb 0x03f0 "HP"
  Device: usb 0x9311 "Deskjet 3050 J610 series"
  Revision: "1.00"
  Serial ID: "CN0BB3B48F05HX"
  Driver: "usblp"
  Driver Modules: "usblp"
  Device File: /dev/usb/lp0
  Device Files: /dev/usb/lp0, /dev/char/180:0, /dev/usblp0
  Device Number: char 180:0
  Speed: 480 Mbps
  Module Alias: "usb:v03F0p9311d0100dc00dsc00dp00ic07isc01ip02"
  Driver Info #0:
    Driver Status: usblp is active
    Driver Activation Cmd: "modprobe usblp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #56 (Hub)

62: USB 00.0: 0000 Unclassified device
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_c45_62e0_noserial_if0_logicaldev_input
  Unique ID: doL0.98QTdAHFEQ5
  Parent ID: FKGF.4Nx_qoDfSd7
  SysFS ID: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0
  SysFS BusID: 2-1.6:1.0
  Hardware Class: unknown
  Model: "Microdia USB 2.0 Camera"
  Hotplug: USB
  Vendor: usb 0x0c45 "Microdia"
  Device: usb 0x62e0 "USB 2.0 Camera"
  Revision: "1.00"
  Driver: "uvcvideo"
  Driver Modules: "uvcvideo"
  Device File: /dev/input/event7
  Device Files: /dev/input/event7, /dev/char/13:71, /dev/input/by-id/usb-Sonix_Technology_Co.__Ltd._USB_2.0_Camera-event-if00, /dev/input/by-path/pci-0000:00:1d.0-usb-0:1.6:1.0-event
  Device Number: char 13:71
  Speed: 480 Mbps
  Module Alias: "usb:v0C45p62E0d0100dcEFdsc02dp01ic0Eisc01ip00"
  Driver Info #0:
    Driver Status: uvcvideo is active
    Driver Activation Cmd: "modprobe uvcvideo"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #56 (Hub)

66: USB 00.0: 10800 Keyboard
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_46d_c22b_noserial_if0_logicaldev_input
  Unique ID: fzDf.5FfQhZxjH+6
  Parent ID: dwDZ.6jITsy+OI9B
  SysFS ID: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.0
  SysFS BusID: 1-1.3.1:1.0
  Hardware Class: keyboard
  Model: "Logitech G110 G-keys"
  Hotplug: USB
  Vendor: usb 0x046d "Logitech, Inc."
  Device: usb 0xc22b "G110 G-keys"
  Revision: "1.00"
  Driver: "usbhid"
  Driver Modules: "usbhid"
  Device File: /dev/input/event4
  Device Files: /dev/input/event4, /dev/char/13:68, /dev/input/by-id/usb-LOGITECH_G110_G-keys-event-kbd, /dev/input/by-path/pci-0000:00:1a.0-usb-0:1.3.1:1.0-event-kbd
  Device Number: char 13:68
  Speed: 1.5 Mbps
  Module Alias: "usb:v046DpC22Bd0100dc00dsc00dp00ic03isc01ip01"
  Driver Info #0:
    XkbRules: xfree86
    XkbModel: pc104
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #57 (Hub)

67: USB 00.1: 0000 Unclassified device
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_46d_c22b_noserial_if1
  Unique ID: 69Uj.qLka26lJC21
  Parent ID: dwDZ.6jITsy+OI9B
  SysFS ID: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.1
  SysFS BusID: 1-1.3.1:1.1
  Hardware Class: unknown
  Model: "Logitech G110 G-keys"
  Hotplug: USB
  Vendor: usb 0x046d "Logitech, Inc."
  Device: usb 0xc22b "G110 G-keys"
  Revision: "1.00"
  Speed: 1.5 Mbps
  Module Alias: "usb:v046DpC22Bd0100dc00dsc00dp00ic03isc00ip00"
  Driver Info #0:
    Driver Status: usbhid is active
    Driver Activation Cmd: "modprobe usbhid"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #57 (Hub)

68: USB 00.0: 10800 Keyboard
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_46d_c22a_noserial_if0_logicaldev_input
  Unique ID: XEU_.aqigC+p0mc6
  Parent ID: dwDZ.6jITsy+OI9B
  SysFS ID: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.0
  SysFS BusID: 1-1.3.3:1.0
  Hardware Class: keyboard
  Model: "Logitech Gaming Keyboard G110"
  Hotplug: USB
  Vendor: usb 0x046d "Logitech, Inc."
  Device: usb 0xc22a "Gaming Keyboard G110"
  Revision: "1.00"
  Driver: "usbhid"
  Driver Modules: "usbhid"
  Device File: /dev/input/event5
  Device Files: /dev/input/event5, /dev/char/13:69, /dev/input/by-id/usb-046d_Gaming_Keyboard_G110-event-kbd, /dev/input/by-path/pci-0000:00:1a.0-usb-0:1.3.3:1.0-event-kbd
  Device Number: char 13:69
  Speed: 1.5 Mbps
  Module Alias: "usb:v046DpC22Ad0100dc00dsc00dp00ic03isc01ip01"
  Driver Info #0:
    XkbRules: xfree86
    XkbModel: pc104
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #57 (Hub)

69: USB 00.1: 0000 Unclassified device
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_46d_c22a_noserial_if1_logicaldev_input
  Unique ID: _Pk2.JxnqZXdcgf0
  Parent ID: dwDZ.6jITsy+OI9B
  SysFS ID: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.1
  SysFS BusID: 1-1.3.3:1.1
  Hardware Class: unknown
  Model: "Logitech Gaming Keyboard G110"
  Hotplug: USB
  Vendor: usb 0x046d "Logitech, Inc."
  Device: usb 0xc22a "Gaming Keyboard G110"
  Revision: "1.00"
  Driver: "usbhid"
  Driver Modules: "usbhid"
  Device File: /dev/input/event6
  Device Files: /dev/input/event6, /dev/char/13:70, /dev/input/by-id/usb-046d_Gaming_Keyboard_G110-event-if01, /dev/input/by-path/pci-0000:00:1a.0-usb-0:1.3.3:1.1-event
  Device Number: char 13:70
  Speed: 1.5 Mbps
  Module Alias: "usb:v046DpC22Ad0100dc00dsc00dp00ic03isc00ip00"
  Driver Info #0:
    Driver Status: usbhid is active
    Driver Activation Cmd: "modprobe usbhid"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #57 (Hub)

70: ADB 00.0: 10502 Bus Mouse
  [Created at input.183]
  UDI: /org/freedesktop/Hal/devices/computer_logicaldev_input_1
  Unique ID: kZYT.VdKNesd9pT6
  Hardware Class: mouse
  Model: "Macintosh mouse button emulation"
  Vendor: 0x0001 
  Device: 0x0001 "Macintosh mouse button emulation"
  Compatible to: int 0x0210 0x0003
  Device File: /dev/input/mice (/dev/input/mouse0)
  Device Files: /dev/input/mice, /dev/input/mouse0, /dev/input/event2, /dev/char/13:66, /dev/char/13:32, /dev/char/13:63
  Device Number: char 13:63 (char 13:32)
  Driver Info #0:
    Buttons: 3
    Wheels: 0
    XFree86 Protocol: explorerps/2
    GPM Protocol: exps2
  Config Status: cfg=new, avail=yes, need=no, active=unknown

71: None 00.0: 10103 CPU
  [Created at cpu.304]
  Unique ID: rdCR.j8NaKXDZtZ6
  Hardware Class: cpu
  Arch: Intel
  Vendor: "GenuineIntel"
  Model: 6.42.7 "Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,sep,mtrr,pge,mca,cmov,pat,pse36,clflush,dts,acpi,mmx,fxsr,sse,sse2,ss,ht,tm,pbe,nx,rdtscp,lm,constant_tsc,arch_perfmon,pebs,bts,xtopology,nonstop_tsc,aperfmperf,pni,pclmulqdq,dtes64,monitor,ds_cpl,vmx,est,tm2,ssse3,
  Clock: 3300 MHz
  BogoMips: 6584.49
  Cache: 6144 kb
  Units/Processor: 16
  Config Status: cfg=new, avail=yes, need=no, active=unknown

72: None 01.0: 10103 CPU
  [Created at cpu.304]
  Unique ID: wkFv.j8NaKXDZtZ6
  Hardware Class: cpu
  Arch: Intel
  Vendor: "GenuineIntel"
  Model: 6.42.7 "Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,sep,mtrr,pge,mca,cmov,pat,pse36,clflush,dts,acpi,mmx,fxsr,sse,sse2,ss,ht,tm,pbe,nx,rdtscp,lm,constant_tsc,arch_perfmon,pebs,bts,xtopology,nonstop_tsc,aperfmperf,pni,pclmulqdq,dtes64,monitor,ds_cpl,vmx,est,tm2,ssse3,
  Clock: 1600 MHz
  BogoMips: 6584.98
  Cache: 6144 kb
  Units/Processor: 16
  Config Status: cfg=new, avail=yes, need=no, active=unknown

73: None 02.0: 10103 CPU
  [Created at cpu.304]
  Unique ID: +rIN.j8NaKXDZtZ6
  Hardware Class: cpu
  Arch: Intel
  Vendor: "GenuineIntel"
  Model: 6.42.7 "Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,sep,mtrr,pge,mca,cmov,pat,pse36,clflush,dts,acpi,mmx,fxsr,sse,sse2,ss,ht,tm,pbe,nx,rdtscp,lm,constant_tsc,arch_perfmon,pebs,bts,xtopology,nonstop_tsc,aperfmperf,pni,pclmulqdq,dtes64,monitor,ds_cpl,vmx,est,tm2,ssse3,
  Clock: 1600 MHz
  BogoMips: 6585.00
  Cache: 6144 kb
  Units/Processor: 16
  Config Status: cfg=new, avail=yes, need=no, active=unknown

74: None 03.0: 10103 CPU
  [Created at cpu.304]
  Unique ID: 4zLr.j8NaKXDZtZ6
  Hardware Class: cpu
  Arch: Intel
  Vendor: "GenuineIntel"
  Model: 6.42.7 "Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,sep,mtrr,pge,mca,cmov,pat,pse36,clflush,dts,acpi,mmx,fxsr,sse,sse2,ss,ht,tm,pbe,nx,rdtscp,lm,constant_tsc,arch_perfmon,pebs,bts,xtopology,nonstop_tsc,aperfmperf,pni,pclmulqdq,dtes64,monitor,ds_cpl,vmx,est,tm2,ssse3,
  Clock: 1600 MHz
  BogoMips: 6585.00
  Cache: 6144 kb
  Units/Processor: 16
  Config Status: cfg=new, avail=yes, need=no, active=unknown

75: None 00.0: 10700 Loopback
  [Created at net.124]
  Unique ID: ZsBS.GQNx7L4uPNA
  SysFS ID: /class/net/lo
  Hardware Class: network interface
  Model: "Loopback network interface"
  Device File: lo
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown

76: None 00.0: 10701 Ethernet
  [Created at net.124]
  Unique ID: usDW.ndpeucax6V1
  Parent ID: rBUF.IQxIdIhhuH7
  SysFS ID: /class/net/eth0
  SysFS Device Link: /devices/pci0000:00/0000:00:1c.4/0000:04:00.0/0000:05:01.0
  Hardware Class: network interface
  Model: "Ethernet network interface"
  Driver: "8139too"
  Driver Modules: "8139too"
  Device File: eth0
  HW Address: 00:16:0a:07:ad:dd
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #31 (Ethernet controller)

77: None 00.0: 10780 Network Interface
  [Created at net.124]
  Unique ID: tovL.GSopYcFr9cF
  SysFS ID: /class/net/tun0
  Hardware Class: network interface
  Model: "Network Interface"
  Driver: "tun"
  Device File: tun0
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```

PC is custom built.

---

### Post by renegadeandy on 2012-01-30
I run Windows 7 on the other partition - never had a problem with anything. Keyboard is a Logitech G110 USB. Ctrl + n ctrl + p did nothing - its a desktop pc not a laptop :)

Thanks for the help so far.

I believe the problem is related to this  guys : [http://ubuntuforums.org/showthread.php?t=1843969](http://ubuntuforums.org/showthread.php?t=1843969)

---

### Post by sudodus on 2012-01-30
You have a new system with powerful Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz. This means that Lucid might be too old to manage it. It has long time support, yes, but the kernel is basically old.

I suggest that you try some newer version, Ubuntu or Kubuntu 11.10 (or possibly 11.04). Make boot CD or USB drives and run them live to test how it works before you install anything to the hard drive!

---

### Post by WasMeHere on 2012-01-30
> **renegadeandy said:**
> I run Windows 7 on the other partition - never had a problem with anything. Keyboard is a Logitech G110 USB. Ctrl + n ctrl + p did nothing - its a desktop pc not a laptop :)

Thanks for the help so far.

I believe the problem is related to this  guys : [http://ubuntuforums.org/showthread.php?t=1843969](http://ubuntuforums.org/showthread.php?t=1843969)

I see, so once in Ubuntu, the keyboard works for ***area5x1***. Is it like that for you too? The problem is only in the grub menu? Can you navigate in your grub menu with another keyboard?

---

### Post by drs305 on 2012-01-30
Have you tried another keyboard?

The messages you posted indicate it's a usb keyboard. If you are able to access your system files (via LiveCD or otherwise), you could try to add the following to your /boot/grub/grub.cfg file to ensure the usb keyboard module is loaded. 

Search grub.cfg for the first 'insmod' command and add an additional line: > insmod usb_keyboard
Do not update-grub as this would remove the additional command.

---

### Post by sudodus on 2012-01-30
That is interesting! Maybe it will work with another version of grub. So changing to Ubuntu 11.10 might help you if the updated grub will manage that keyboard. Or maybe you should install the old legacy grub (using menu.lst)

---

### Post by renegadeandy on 2012-01-30
SO I did some release upgrades - got it working now with ubuntu 11.10 which I believe is a slightly newer version of the grub bootloader :popcorn:such a headache of a problem...

---

### Post by WasMeHere on 2012-01-31
> **renegadeandy said:**
> SO I did some release upgrades - got it working now with ubuntu 11.10 which I believe is a slightly newer version of the grub bootloader :popcorn:such a headache of a problem...
If it works for you now, please mark this thread SOLVED :-)

---

### Post by sudodus on 2012-01-31
Can you navigate in the grub menu now? Or is Ubuntu 11.10 working but still not the grub menu?

---

