---
title: "hwinfo is something wrong here???"
date: 2009-10-23
forum: General Help
---

### Post by logikz on 2009-10-23
```

                                                                
> hal.1: read hal data
                                                                
> floppy.1: get nvram
                                                                
> floppy.2: klog info
                                                                
> bios.1: cmdline
                                                                
> bios.1.1: apm
                                                                
> bios.2: ram
                                                                
> bios.2: rom
                                                                
> bios.3: smp
                                                                
> bios.4: vbe
                                                                
> bios.4.1: vbe info
                                                                
> bios.5: 32
                                                                
> bios.6: acpi
                                                                
> sys.1: cpu
                                                                
> misc.9: kernel log
                                                                
> misc.1: misc data
                                                                
> misc.1.1: open serial
                                                                
> misc.1.2: open parallel
                                                                
> misc.2.1: io
                                                                
> misc.2.2: dma
                                                                
> misc.2.3: irq
                                                                
> misc.3: FPU
                                                                
> misc.3.1: DMA
                                                                
> misc.3.2: PIC
                                                                
> misc.3.3: timer
                                                                
> misc.3.4: RTC
                                                                
> cpu.1: cpuinfo
                                                                
> memory.1: main memory size
                                                                
> pci.1: sysfs drivers
                                                                
> pci.2: get sysfs pci data
                                                                
> pci.4: build list
                                                                
> pci.3: macio
                                                                
> pci.4: vio
                                                                
> pci.5: xen
                                                                
> pci.6: ps3
                                                                
> pci.7: platform
                                                                
> pci.8: of_platform
                                                                
> pci.9: vm
                                                                
> pci.10: virtio
                                                                
> monitor.1: ddc
                                                                
> monitor.2: bios
                                                                
> monitor.3: pci
                                                                
> monitor.4: internal db
                                                                
> monitor.5: prom
                                                                
> isapnp.1: pnp devices
                                                                
> pcmcia.1: sysfs drivers
                                                                
> pcmcia.2: pcmcia
                                                                
> pcmcia.3: pcmcia ctrl
                                                                
> serial.1: read info
                                                                
> serial.2: build list
                                                                
> misc.5: misc data
                                                                
> parallel.1: pp mod
                                                                
> parallel.2.1: lp read info
                                                                
> parallel.2.2: lp read info
                                                                
> parallel.2.3: lp read info
                                                                
> block.1: block modules
                                                                
> block.2: sysfs drivers
                                                                
> block.3: cdrom
                                                                
> block.4: partition
                                                                
> block.5: get sysfs block dev data
                                                                
> block.5: /dev/sr0
                                                                
> block.5.1: /dev/sr0 cache
                                                                
> block.5: /dev/sda
                                                                
> block.5.1: /dev/sda geo
                                                                
> block.5.2: /dev/sda serial
                                                                
> scsi.1: scsi modules
                                                                
> scsi.2: scsi tape
                                                                
> scsi.3: scsi generic
                                                                
> usb.1: sysfs drivers
                                                                
> usb.2: usb
                                                                
> usb.3.1: joydev mod
                                                                
> usb.3.2: evdev mod
                                                                
> usb.3.3: input
                                                                
> usb.3.4: lp
                                                                
> usb.3.5: serial
                                                                
> edd.1: edd mod
                                                                
> edd.2: edd info
                                                                
> modem.1: serial
                                                                
> mouse.2: serial
                                                                
> input.1: joydev mod
                                                                
> input.1.1: evdev mod
                                                                
> input.2: input
                                                                
> kbd.2: uml
                                                                
> cpu.1: cpuinfo
                                                                
> kbd.3: serial console
                                                                
> fb.1: read info
                                                                
> net.1: get network data
                                                                
> pppoe.1: looking for pppoe
                                                                
> pppoe.2: discovery
                                                                
> wlan.1: detecting wlan features
                                                                
> wlan.2: assign udi
                                                                
> isdn.1: list
                                                                
> dsl.1: list
                                                                
> int.2: cdrom
                                                                
> int.3: media
                                                                
> int.4.1: /dev/sda
                                                                
> int.4: floppy
                                                                
> int.5: edd
                                                                
> int.5.1: bios
                                                                
> int.6: mouse
                                                                
> int.15: system info
                                                                
> int.7: hdb
                                                                
> int.7.1: modules
                                                                
> int.8: usbscsi
                                                                
> int.9: hotplug
                                                                
> int.10: modem
                                                                
> int.11: wlan
                                                                
> int.12: udev
                                                                
> int.13: device names
                                                                
> int.14: soft raid
                                                                
> int.15: geo
                                                                
> int.16: parent
                                                                
============ start debug info ============
libhd version 15.3 (ia32)
using /var/lib/hardware
kernel version is 2.6
----- /proc/cmdline -----
  
----- /proc/cmdline end -----
debug = 0xff7ffff7
probe = 0x0000138fc4aa17fcf9fffe (+memory +pci +isapnp +net +floppy +misc +misc.serial +misc.par +misc.floppy +serial +cpu +bios +monitor +mouse +scsi +usb -usb.mods +modem +modem.usb +parallel +parallel.lp +parallel.zip -isa -isa.isdn +isdn +kbd +prom +sbus +int +braille +braille.alva +braille.fhp +braille.ht -ignx11 +sys -bios.vbe -isapnp.old -isapnp.new -isapnp.mod +braille.baum -manual +fb +pppoe -scan +pcmcia -fork -parallel.imm +s390 -cpuemu -sysfs -s390disks +udev +block +block.cdrom +block.part +edd +edd.mod -bios.ddc -bios.fb -bios.mode +input +block.mods +bios.vesa -cpuemu.debug -scsi.noserial +wlan -bios.crc -hal -bios.vram -bios.acpi -bios.ddc.ports=1 -bios.ddc.ports=2 -bios.ddc.ports=3 -bios.ddc.ports=4 -modules.pata -max -lxrc)
shm: attached segment 6488068 at 0xb7ad6000
>> hal.1: read hal data
  hal: connected to: :1.169
----- hal device list -----
  0: udi = '/org/freedesktop/Hal/devices/computer'
  power_management.is_powersave_set = false
  info.capabilities = { 'cpufreq_control' }
  info.callouts.add = { 'hal-acl-tool --remove-all', 'hal-storage-cleanup-all-mountpoints' }
  power_management.type = 'acpi'
  power_management.acpi.linux.version = '20080926'
  info.product = 'Computer'
  info.subsystem = 'unknown'
  system.kernel.name = 'Linux'
  info.udi = '/org/freedesktop/Hal/devices/computer'
  system.kernel.version.major = 2 (0x2)
  system.kernel.version = '2.6.28-16-generic'
  system.kernel.version.micro = 28 (0x1c)
  system.kernel.version.minor = 6 (0x6)
  power_management.can_suspend = true
  system.kernel.machine = 'i686'
  power_management.can_hibernate = true
  power_management.can_suspend_hybrid = false
  system.hardware.primary_video.product = 38422 (0x9616)
  system.hardware.primary_video.vendor = 4098 (0x1002)
  system.board.serial = 'MF7097G00401355'
  system.firmware.vendor = 'American Megatrends Inc.'
  system.firmware.version = '0801'
  system.firmware.release_date = '06/02/2009'
  system.hardware.vendor = 'System manufacturer'
  system.hardware.product = 'System Product Name'
  system.hardware.version = 'System Version'
  system.chassis.manufacturer = 'Chassis Manufacture'
  system.board.product = 'M3A76-CM'
  system.board.version = 'Rev X.0x'
  system.board.vendor = 'ASUSTeK Computer INC.'
  system.chassis.type = 'Desktop'
  system.formfactor = 'desktop'
  system.hardware.serial = 'System Serial Number'
  system.hardware.uuid = '00B1E405-8EFE-D511-B234-002618B8DA07'
  power_management.quirk.dpms_on = true
  power_management.quirk.vbestate_restore = true
  power_management.quirk.vbemode_restore = true
  power_management.quirk.dpms_suspend = true
  power_management.quirk.vga_mode_3 = true
  info.addons = { 'hald-addon-cpufreq', 'hald-addon-acpi' }
  org.freedesktop.Hal.Device.SystemPowerManagement.method_names = { 'Suspend', 'SuspendHybrid', 'Hibernate', 'Shutdown', 'Reboot', 'SetPowerSave' }
  power_management.quirk.vbe_post = true
  org.freedesktop.Hal.Device.SystemPowerManagement.method_argnames = { 'num_seconds_to_sleep', 'num_seconds_to_sleep', '', '', '', 'enable_power_save' }
  org.freedesktop.Hal.Device.SystemPowerManagement.method_execpaths = { 'hal-system-power-suspend', 'hal-system-power-suspend-hybrid', 'hal-system-power-hibernate', 'hal-system-power-shutdown', 'hal-system-power-reboot', 'hal-system-power-set-power-save' }
  info.interfaces = { 'org.freedesktop.Hal.Device.SystemPowerManagement', 'org.freedesktop.Hal.Device.CPUFreq' }
  info.callouts.session_add = { 'hal-acl-tool --reconfigure' }
  info.callouts.session_remove = { 'hal-acl-tool --reconfigure' }
  info.callouts.session_active = { 'hal-acl-tool --reconfigure' }
  info.callouts.session_inactive = { 'hal-acl-tool --reconfigure' }
  org.freedesktop.Hal.Device.SystemPowerManagement.method_signatures = { 'i', 'i', '', '', '', 'b' }

  1: udi = '/org/freedesktop/Hal/devices/volume_uuid_3773c8ab_bc4b_48c0_9613_05934ff5e3e0'
  info.capabilities = { 'volume', 'block' }
  volume.partition.media_size = 320072933376ull (0x4a85d56000ull)
  volume.block_size = 512 (0x200)
  volume.num_blocks = 18137322ull (0x114c0eaull)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_3773c8ab_bc4b_48c0_9613_05934ff5e3e0'
  volume.fstype = 'swap'
  volume.fsusage = 'other'
  volume.fsversion = '2'
  volume.uuid = '3773c8ab-bc4b-48c0-9613-05934ff5e3e0'
  volume.label = ''
  volume.mount_point = ''
  volume.is_mounted = false
  volume.is_mounted_read_only = false
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host0/target0:0:0/0:0:0:0/block/sda/sda5'
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200AAKS__WD_WCAV24661468'
  info.product = 'Volume (swap)'
  volume.linux.is_device_mapper = false
  volume.is_disc = false
  volume.is_partition = true
  volume.partition.number = 5 (0x5)
  info.category = 'volume'
  block.device = '/dev/sda5'
  block.major = 8 (0x8)
  block.minor = 5 (0x5)
  block.is_volume = true
  volume.size = 9286308864ull (0x22981d400ull)
  volume.partition.start = 310784011776ull (0x485c2bae00ull)
  linux.hotplug_type = 3 (0x3)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200AAKS__WD_WCAV24661468'

  2: udi = '/org/freedesktop/Hal/devices/volume_part2_size_1024'
  linux.hotplug_type = 3 (0x3)
  info.capabilities = { 'volume', 'block' }
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200AAKS__WD_WCAV24661468'
  info.category = 'volume'
  volume.fstype = ''
  volume.fsusage = 'partitiontable'
  volume.fsversion = ''
  volume.uuid = ''
  volume.label = ''
  volume.mount_point = ''
  volume.is_mounted = false
  volume.is_mounted_read_only = false
  info.product = 'Volume'
  volume.linux.is_device_mapper = false
  volume.is_disc = false
  volume.is_partition = true
  volume.block_size = 512 (0x200)
  volume.num_blocks = 2ull (0x2ull)
  volume.partition.number = 2 (0x2)
  block.device = '/dev/sda2'
  volume.partition.media_size = 320072933376ull (0x4a85d56000ull)
  volume.partition.scheme = 'mbr'
  block.major = 8 (0x8)
  volume.partition.label = ''
  block.is_volume = true
  volume.partition.start = 310783979520ull (0x485c2b3000ull)
  block.minor = 2 (0x2)
  volume.partition.uuid = ''
  volume.size = 1024ull (0x400ull)
  volume.partition.flags = {  }
  volume.partition.type = '0x05'
  info.udi = '/org/freedesktop/Hal/devices/volume_part2_size_1024'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host0/target0:0:0/0:0:0:0/block/sda/sda2'
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200AAKS__WD_WCAV24661468'

  3: udi = '/org/freedesktop/Hal/devices/volume_uuid_10f79e5c_10ad_4f71_8b60_e828d5299810'
  linux.hotplug_type = 3 (0x3)
  info.capabilities = { 'volume', 'block' }
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200AAKS__WD_WCAV24661468'
  info.category = 'volume'
  volume.fstype = 'ext3'
  volume.fsusage = 'filesystem'
  volume.fsversion = '1.0'
  volume.uuid = '10f79e5c-10ad-4f71-8b60-e828d5299810'
  volume.label = ''
  volume.mount_point = '/'
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_10f79e5c_10ad_4f71_8b60_e828d5299810'
  volume.is_mounted = true
  volume.is_mounted_read_only = false
  info.interfaces = { 'org.freedesktop.Hal.Device.Volume' }
  volume.is_disc = false
  info.product = 'Volume (ext3)'
  volume.block_size = 512 (0x200)
  volume.num_blocks = 606999897ull (0x242e1559ull)
  volume.linux.is_device_mapper = false
  block.device = '/dev/sda1'
  volume.partition.media_size = 320072933376ull (0x4a85d56000ull)
  volume.partition.number = 1 (0x1)
  block.major = 8 (0x8)
  block.minor = 1 (0x1)
  volume.is_partition = true
  volume.partition.start = 32256ull (0x7e00ull)
  volume.ignore = false
  block.is_volume = true
  volume.size = 310783947264ull (0x485c2ab200ull)
  org.freedesktop.Hal.Device.Volume.method_signatures = { 'ssas', 'as', 'as' }
  org.freedesktop.Hal.Device.Volume.method_names = { 'Mount', 'Unmount', 'Eject' }
  org.freedesktop.Hal.Device.Volume.method_execpaths = { 'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject' }
  org.freedesktop.Hal.Device.Volume.method_argnames = { 'mount_point fstype extra_options', 'extra_options', 'extra_options' }
  volume.unmount.valid_options = { 'lazy' }
  volume.mount.valid_options = { 'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'acl', 'user_xattr', 'data=' }
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host0/target0:0:0/0:0:0:0/block/sda/sda1'
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200AAKS__WD_WCAV24661468'

  4: udi = '/org/freedesktop/Hal/devices/storage_model_DVD_Writer_1040d'
  info.callouts.add = { 'hal-acl-tool --add-device' }
  info.callouts.remove = { 'hal-acl-tool --remove-device' }
  info.category = 'storage'
  info.addons = { 'hald-addon-storage' }
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
  storage.cdrom.read_speed = 8467 (0x2113)
  storage.cdrom.write_speed = 8467 (0x2113)
  storage.cdrom.write_speeds = { '8467', '7056', '5645', '4234', '2822', '2112', '1764', '1411', '706' }
  block.storage_device = '/org/freedesktop/Hal/devices/storage_model_DVD_Writer_1040d'
  org.freedesktop.Hal.Device.Storage.method_names = { 'Eject', 'CloseTray' }
  org.freedesktop.Hal.Device.Storage.method_signatures = { 'as', 'as' }
  org.freedesktop.Hal.Device.Storage.method_argnames = { 'extra_options', 'extra_options' }
  org.freedesktop.Hal.Device.Storage.method_execpaths = { 'hal-storage-eject', 'hal-storage-closetray' }
  storage.partitioning_scheme = ''
  info.interfaces = { 'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage.Removable' }
  info.product = 'DVD Writer 1040d'
  info.udi = '/org/freedesktop/Hal/devices/storage_model_DVD_Writer_1040d'
  block.device = '/dev/sr0'
  block.major = 11 (0xb)
  block.minor = 0 (0x0)
  block.is_volume = false
  storage.bus = 'pci'
  storage.no_partitions_hint = true
  storage.media_check_enabled = true
  storage.automount_enabled_hint = true
  storage.drive_type = 'cdrom'
  storage.model = 'DVD Writer 1040d'
  storage.vendor = 'HP'
  storage.firmware_version = 'EH24'
  storage.lun = 0 (0x0)
  storage.originating_device = '/org/freedesktop/Hal/devices/computer'
  storage.removable.media_available = false
  storage.removable = true
  storage.size = 0ull (0x0ull)
  storage.hotpluggable = false
  storage.requires_eject = true
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.1/host4/target4:0:0/4:0:0:0/block/sr0'
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_439c_scsi_host_scsi_device_lun0'
  storage.removable.support_async_notification = false
  info.vendor = 'HP'
  linux.hotplug_type = 3 (0x3)
  info.capabilities = { 'storage', 'block', 'storage.cdrom', 'access_control' }
  access_control.file = '/dev/sr0'
  access_control.type = 'cdrom'

  5: udi = '/org/freedesktop/Hal/devices/computer_alsa_timer'
  alsa.device_file = '/dev/snd/timer'
  info.capabilities = { 'alsa', 'access_control' }
  access_control.file = '/dev/snd/timer'
  alsa.type = 'timer'
  info.callouts.add = { 'hal-acl-tool --add-device' }
  linux.device_file = '/dev/snd/timer'
  info.category = 'alsa'
  access_control.type = 'sound'
  info.callouts.remove = { 'hal-acl-tool --remove-device' }
  linux.sysfs_path = '/sys/devices/virtual/sound/timer'
  info.product = 'ALSA Timer Device'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.subsystem = 'sound'
  info.udi = '/org/freedesktop/Hal/devices/computer_alsa_timer'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'

  6: udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'
  info.capabilities = { 'oss', 'access_control' }
  access_control.file = '/dev/sequencer2'
  access_control.type = 'sound'
  info.callouts.add = { 'hal-acl-tool --add-device' }
  info.callouts.remove = { 'hal-acl-tool --remove-device' }
  linux.device_file = '/dev/sequencer2'
  info.category = 'oss'
  linux.sysfs_path = '/sys/devices/virtual/sound/sequencer2'
  info.product = 'OSS Sequencer Device'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.subsystem = 'sound'
  info.udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'
  oss.device_file = '/dev/sequencer2'
  linux.hotplug_type = 2 (0x2)
  oss.type = 'sequencer'
  linux.subsystem = 'sound'

  7: udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer'
  info.capabilities = { 'oss', 'access_control' }
  access_control.file = '/dev/sequencer'
  access_control.type = 'sound'
  info.callouts.add = { 'hal-acl-tool --add-device' }
  info.callouts.remove = { 'hal-acl-tool --remove-device' }
  linux.device_file = '/dev/sequencer'
  info.category = 'oss'
  linux.sysfs_path = '/sys/devices/virtual/sound/sequencer'
  info.product = 'OSS Sequencer Device'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.subsystem = 'sound'
  info.udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer'
  oss.device_file = '/dev/sequencer'
  linux.hotplug_type = 2 (0x2)
  oss.type = 'sequencer'
  linux.subsystem = 'sound'

  8: udi = '/org/freedesktop/Hal/devices/computer_alsa_sequencer'
  alsa.device_file = '/dev/snd/seq'
  info.capabilities = { 'alsa', 'access_control' }
  access_control.file = '/dev/snd/seq'
  alsa.type = 'sequencer'
  info.callouts.add = { 'hal-acl-tool --add-device' }
  linux.device_file = '/dev/snd/seq'
  info.category = 'alsa'
  access_control.type = 'sound'
  info.callouts.remove = { 'hal-acl-tool --remove-device' }
  linux.sysfs_path = '/sys/devices/virtual/sound/seq'
  info.product = 'ALSA Sequencer Device'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.subsystem = 'sound'
  info.udi = '/org/freedesktop/Hal/devices/computer_alsa_sequencer'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'

  9: udi = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200AAKS__WD_WCAV24661468'
  linux.hotplug_type = 3 (0x3)
  info.capabilities = { 'storage', 'block' }
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200AAKS__WD_WCAV24661468'
  info.category = 'storage'
  storage.removable.media_size = 320072933376ull (0x4a85d56000ull)
  storage.partitioning_scheme = 'mbr'
  info.product = 'WDC WD3200AAKS-0'
  info.udi = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200AAKS__WD_WCAV24661468'
  block.device = '/dev/sda'
  block.major = 8 (0x8)
  block.minor = 0 (0x0)
  block.is_volume = false
  storage.bus = 'pci'
  storage.no_partitions_hint = false
  storage.media_check_enabled = false
  storage.automount_enabled_hint = false
  storage.drive_type = 'disk'
  storage.model = 'WDC WD3200AAKS-0'
  storage.vendor = 'ATA'
  storage.serial = 'SATA_WDC_WD3200AAKS-_WD-WCAV24661468'
  storage.firmware_version = '01.0'
  storage.lun = 0 (0x0)
  storage.originating_device = '/org/freedesktop/Hal/devices/computer'
  storage.removable.media_available = true
  storage.removable = false
  storage.size = 320072933376ull (0x4a85d56000ull)
  storage.hotpluggable = false
  storage.requires_eject = false
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host0/target0:0:0/0:0:0:0/block/sda'
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_scsi_device_lun0'
  info.vendor = 'ATA'

  10: udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'
  info.capabilities = { 'input', 'input.mouse', 'access_control' }
  access_control.file = '/dev/input/event2'
  access_control.type = 'mouse'
  info.callouts.add = { 'hal-acl-tool --add-device' }
  info.callouts.remove = { 'hal-acl-tool --remove-device' }
  linux.device_file = '/dev/input/event2'
  info.category = 'input'
  input.product = 'Macintosh mouse button emulation'
  input.device = '/dev/input/event2'
  input.x11_driver = 'evdev'
  linux.sysfs_path = '/sys/devices/virtual/input/input2/event2'
  info.product = 'Macintosh mouse button emulation'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.subsystem = 'input'
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'input'

  11: udi = '/org/freedesktop/Hal/devices/usb_device_46e_5542_noserial_if1_logicaldev_input'
  info.capabilities = { 'input', 'input.keys', 'button' }
  info.callouts.add = { 'debian-setup-keyboard' }
  input.xkb.options = 'lv3:ralt_switch'
  linux.device_file = '/dev/input/event6'
  info.category = 'input'
  input.product = 'BTC USB Multimedia Keyboard'
  input.device = '/dev/input/event6'
  info.addons.singleton = { 'hald-addon-input' }
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_46e_5542_noserial_if1'
  input.x11_driver = 'evdev'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.1/input/input6/event6'
  info.product = 'BTC USB Multimedia Keyboard'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_46e_5542_noserial_if1'
  info.subsystem = 'input'
  input.xkb.rules = 'evdev'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46e_5542_noserial_if1_logicaldev_input'
  input.xkb.layout = 'us'
  input.xkb.variant = 'intl'
  input.xkb.model = 'pc105'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'input'

  12: udi = '/org/freedesktop/Hal/devices/usb_device_46e_5542_noserial_if0_logicaldev_input'
  info.capabilities = { 'input', 'input.keyboard', 'input.keypad', 'input.keys', 'button' }
  info.callouts.add = { 'debian-setup-keyboard' }
  input.xkb.options = 'lv3:ralt_switch'
  linux.device_file = '/dev/input/event5'
  info.category = 'input'
  input.product = 'BTC USB Multimedia Keyboard'
  input.device = '/dev/input/event5'
  info.addons.singleton = { 'hald-addon-input' }
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_46e_5542_noserial_if0'
  input.x11_driver = 'evdev'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0/input/input5/event5'
  info.product = 'BTC USB Multimedia Keyboard'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_46e_5542_noserial_if0'
  info.subsystem = 'input'
  input.xkb.rules = 'evdev'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46e_5542_noserial_if0_logicaldev_input'
  input.xkb.layout = 'us'
  input.xkb.variant = 'intl'
  input.xkb.model = 'pc105'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'input'

  13: udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_playback_1'
  alsa.device_file = '/dev/snd/pcmC0D1p'
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'
  alsa.card = 0 (0x0)
  info.capabilities = { 'alsa', 'access_control' }
  alsa.card_id = 'HDA ATI SB'
  alsa.device = 1 (0x1)
  alsa.pcm_class = 'generic'
  info.category = 'alsa'
  alsa.device_id = 'VT1708B Digital'
  alsa.type = 'playback'
  info.callouts.remove = { 'hal-acl-tool --remove-device' }
  linux.device_file = '/dev/snd/pcmC0D1p'
  access_control.type = 'sound'
  info.callouts.add = { 'hal-acl-tool --add-device' }
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2/sound/card0/pcmC0D1p'
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'
  info.product = 'VT1708B Digital ALSA Playback Device'
  info.subsystem = 'sound'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_playback_1'
  access_control.file = '/dev/snd/pcmC0D1p'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'

  14: udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_playback_0'
  alsa.device_file = '/dev/snd/pcmC0D0p'
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'
  alsa.card = 0 (0x0)
  info.capabilities = { 'alsa', 'access_control' }
  alsa.card_id = 'HDA ATI SB'
  alsa.device = 0 (0x0)
  alsa.pcm_class = 'generic'
  info.category = 'alsa'
  alsa.device_id = 'VT1708B Analog'
  alsa.type = 'playback'
  info.callouts.remove = { 'hal-acl-tool --remove-device' }
  linux.device_file = '/dev/snd/pcmC0D0p'
  access_control.type = 'sound'
  info.callouts.add = { 'hal-acl-tool --add-device' }
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2/sound/card0/pcmC0D0p'
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'
  info.product = 'VT1708B Analog ALSA Playback Device'
  info.subsystem = 'sound'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_playback_0'
  access_control.file = '/dev/snd/pcmC0D0p'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'

  15: udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_capture_0'
  alsa.device_file = '/dev/snd/pcmC0D0c'
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'
  alsa.card = 0 (0x0)
  info.capabilities = { 'alsa', 'access_control' }
  alsa.card_id = 'HDA ATI SB'
  alsa.device = 0 (0x0)
  alsa.pcm_class = 'generic'
  info.category = 'alsa'
  alsa.device_id = 'VT1708B Analog'
  alsa.type = 'capture'
  info.callouts.remove = { 'hal-acl-tool --remove-device' }
  linux.device_file = '/dev/snd/pcmC0D0c'
  access_control.type = 'sound'
  info.callouts.add = { 'hal-acl-tool --add-device' }
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2/sound/card0/pcmC0D0c'
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'
  info.product = 'VT1708B Analog ALSA Capture Device'
  info.subsystem = 'sound'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_capture_0'
  access_control.file = '/dev/snd/pcmC0D0c'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'

  16: udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_oss_pcm_0'
  info.capabilities = { 'oss', 'access_control' }
  access_control.file = '/dev/audio'
  access_control.type = 'sound'
  linux.hotplug_type = 2 (0x2)
  info.callouts.add = { 'hal-acl-tool --add-device' }
  linux.device_file = '/dev/audio'
  info.category = 'oss'
  info.callouts.remove = { 'hal-acl-tool --remove-device' }
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2/sound/card0/audio'
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'
  info.product = 'VT1708B Analog OSS PCM Device'
  info.subsystem = 'sound'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_oss_pcm_0'
  oss.device_file = '/dev/audio'
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'
  oss.card = 0 (0x0)
  oss.card_id = 'HDA ATI SB'
  oss.device_id = 'VT1708B Analog'
  oss.device = 0 (0x0)
  oss.type = 'pcm'
  linux.subsystem = 'sound'

  17: udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_oss_mixer__1'
  info.capabilities = { 'oss', 'access_control' }
  access_control.file = '/dev/mixer'
  access_control.type = 'sound'
  info.callouts.add = { 'hal-acl-tool --add-device' }
  info.callouts.remove = { 'hal-acl-tool --remove-device' }
  linux.device_file = '/dev/mixer'
  info.category = 'oss'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2/sound/card0/mixer'
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'
  info.product = 'VT1708B Analog OSS Control Device'
  info.subsystem = 'sound'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_oss_mixer__1'
  oss.device_file = '/dev/mixer'
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'
  oss.card = 0 (0x0)
  oss.card_id = 'HDA ATI SB'
  oss.device_id = 'VT1708B Analog'
  linux.hotplug_type = 2 (0x2)
  oss.type = 'mixer'
  linux.subsystem = 'sound'

  18: udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_oss_pcm_0_0'
  info.capabilities = { 'oss', 'access_control' }
  access_control.file = '/dev/dsp'
  access_control.type = 'sound'
  linux.hotplug_type = 2 (0x2)
  info.callouts.add = { 'hal-acl-tool --add-device' }
  linux.device_file = '/dev/dsp'
  info.category = 'oss'
  info.callouts.remove = { 'hal-acl-tool --remove-device' }
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2/sound/card0/dsp'
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'
  info.product = 'VT1708B Analog OSS PCM Device'
  info.subsystem = 'sound'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_oss_pcm_0_0'
  oss.device_file = '/dev/dsp'
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'
  oss.card = 0 (0x0)
  oss.card_id = 'HDA ATI SB'
  oss.device_id = 'VT1708B Analog'
  oss.device = 0 (0x0)
  oss.type = 'pcm'
  linux.subsystem = 'sound'

  19: udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_control__1'
  alsa.device_file = '/dev/snd/controlC0'
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'
  alsa.card = 0 (0x0)
  alsa.type = 'control'
  alsa.card_id = 'HDA ATI SB'
  linux.device_file = '/dev/snd/controlC0'
  info.capabilities = { 'alsa', 'access_control' }
  info.category = 'alsa'
  access_control.type = 'sound'
  info.callouts.add = { 'hal-acl-tool --add-device' }
  info.callouts.remove = { 'hal-acl-tool --remove-device' }
  access_control.file = '/dev/snd/controlC0'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2/sound/card0/controlC0'
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'
  info.product = 'HDA ATI SB ALSA Control Device'
  info.subsystem = 'sound'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_control__1'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'

  20: udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_oss_pcm_1'
  info.capabilities = { 'oss', 'access_control' }
  access_control.file = '/dev/adsp'
  access_control.type = 'sound'
  linux.hotplug_type = 2 (0x2)
  info.callouts.add = { 'hal-acl-tool --add-device' }
  linux.device_file = '/dev/adsp'
  info.category = 'oss'
  info.callouts.remove = { 'hal-acl-tool --remove-device' }
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2/sound/card0/adsp'
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'
  info.product = 'VT1708B Analog OSS PCM Device'
  info.subsystem = 'sound'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_oss_pcm_1'
  oss.device_file = '/dev/adsp'
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'
  oss.card = 0 (0x0)
  oss.card_id = 'HDA ATI SB'
  oss.device_id = 'VT1708B Analog'
  oss.device = 1 (0x1)
  oss.type = 'pcm'
  linux.subsystem = 'sound'

  21: udi = '/org/freedesktop/Hal/devices/pci_1002_439c_scsi_host_scsi_device_lun0_scsi_generic'
  info.capabilities = { 'scsi_generic', 'access_control' }
  access_control.file = '/dev/sg1'
  access_control.type = 'cdrom'
  info.callouts.add = { 'hal-acl-tool --add-device' }
  info.callouts.remove = { 'hal-acl-tool --remove-device' }
  linux.device_file = '/dev/sg1'
  info.category = 'scsi_generic'
  scsi_generic.device = '/dev/sg1'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.1/host4/target4:0:0/4:0:0:0/scsi_generic/sg1'
  info.product = 'SCSI Generic Interface'
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_439c_scsi_host_scsi_device_lun0'
  info.subsystem = 'scsi_generic'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_439c_scsi_host_scsi_device_lun0_scsi_generic'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi_generic'

  22: udi = '/org/freedesktop/Hal/devices/usb_device_46d_c049_noserial_if0_logicaldev_input'
  info.capabilities = { 'input', 'input.mouse', 'access_control' }
  access_control.file = '/dev/input/event3'
  access_control.type = 'mouse'
  info.callouts.add = { 'hal-acl-tool --add-device' }
  info.callouts.remove = { 'hal-acl-tool --remove-device' }
  linux.device_file = '/dev/input/event3'
  info.category = 'input'
  input.product = 'Logitech USB Gaming Mouse'
  input.device = '/dev/input/event3'
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_46d_c049_noserial_if0'
  input.x11_driver = 'evdev'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0/input/input3/event3'
  info.product = 'Logitech USB Gaming Mouse'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_46d_c049_noserial_if0'
  info.subsystem = 'input'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c049_noserial_if0_logicaldev_input'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'input'

  23: udi = '/org/freedesktop/Hal/devices/fuse'
  info.capabilities = { 'access_control' }
  access_control.file = '/dev/fuse'
  access_control.type = 'camera'
  info.callouts.add = { 'hal-acl-tool --add-device' }
  info.callouts.remove = { 'hal-acl-tool --remove-device' }
  info.subsystem = 'unknown'
  info.parent = '/org/freedesktop/Hal/devices/pci_1022_9600'
  info.udi = '/org/freedesktop/Hal/devices/fuse'

  24: udi = '/org/freedesktop/Hal/devices/kvm'
  info.capabilities = { 'access_control' }
  access_control.file = '/dev/kvm'
  access_control.type = 'virt-hardware'
  info.callouts.add = { 'hal-acl-tool --add-device' }
  info.callouts.remove = { 'hal-acl-tool --remove-device' }
  info.subsystem = 'unknown'
  info.parent = '/org/freedesktop/Hal/devices/fuse'
  info.udi = '/org/freedesktop/Hal/devices/kvm'

  25: udi = '/org/freedesktop/Hal/devices/acpi_P001'
  info.capabilities = { 'processor' }
  processor.number = 0 (0x0)
  processor.can_throttle = true
  linux.acpi_type = 1 (0x1)
  info.category = 'processor'
  info.product = 'AMD Athlon(tm) II X4 620 Processor'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.udi = '/org/freedesktop/Hal/devices/acpi_P001'
  linux.hotplug_type = 4 (0x4)
  linux.acpi_path = '/proc/acpi/processor/P001'

  26: udi = '/org/freedesktop/Hal/devices/acpi_P002'
  info.capabilities = { 'processor' }
  processor.number = 1 (0x1)
  processor.can_throttle = false
  linux.acpi_type = 1 (0x1)
  info.category = 'processor'
  info.product = 'AMD Athlon(tm) II X4 620 Processor'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.udi = '/org/freedesktop/Hal/devices/acpi_P002'
  linux.hotplug_type = 4 (0x4)
  linux.acpi_path = '/proc/acpi/processor/P002'

  27: udi = '/org/freedesktop/Hal/devices/acpi_P003'
  info.capabilities = { 'processor' }
  processor.number = 2 (0x2)
  processor.can_throttle = false
  linux.acpi_type = 1 (0x1)
  info.category = 'processor'
  info.product = 'AMD Athlon(tm) II X4 620 Processor'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.udi = '/org/freedesktop/Hal/devices/acpi_P003'
  linux.hotplug_type = 4 (0x4)
  linux.acpi_path = '/proc/acpi/processor/P003'

  28: udi = '/org/freedesktop/Hal/devices/acpi_P004'
  info.capabilities = { 'processor' }
  processor.number = 3 (0x3)
  processor.can_throttle = false
  linux.acpi_type = 1 (0x1)
  info.category = 'processor'
  info.product = 'AMD Athlon(tm) II X4 620 Processor'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.udi = '/org/freedesktop/Hal/devices/acpi_P004'
  linux.hotplug_type = 4 (0x4)
  linux.acpi_path = '/proc/acpi/processor/P004'

  29: udi = '/org/freedesktop/Hal/devices/net_computer_loopback'
  info.capabilities = { 'net', 'net.loopback' }
  info.category = 'net.loopback'
  net.originating_device = '/org/freedesktop/Hal/devices/computer'
  net.interface = 'lo'
  net.address = '00:00:00:00:00:00'
  net.linux.ifindex = 1 (0x1)
  linux.sysfs_path = '/sys/devices/virtual/net/lo'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.subsystem = 'net'
  net.arp_proto_hw_id = 772 (0x304)
  info.udi = '/org/freedesktop/Hal/devices/net_computer_loopback'
  info.product = 'Loopback device Interface'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'net'

  30: udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'
  info.capabilities = { 'sound' }
  info.category = 'sound'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2/sound/card0'
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4383'
  info.product = 'HDA ATI SB Sound Card'
  info.subsystem = 'sound'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'
  sound.originating_device = '/org/freedesktop/Hal/devices/pci_1002_4383'
  sound.card = 0 (0x0)
  sound.card_id = 'HDA ATI SB'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'

  31: udi = '/org/freedesktop/Hal/devices/pci_1002_439c_scsi_host_0'
  info.capabilities = { 'scsi_host' }
  scsi_host.host = 5 (0x5)
  info.category = 'scsi_host'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.1/host5/scsi_host/host5'
  info.product = 'SCSI Host Adapter'
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_439c'
  info.subsystem = 'scsi_host'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_439c_scsi_host_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi_host'

  32: udi = '/org/freedesktop/Hal/devices/pci_1002_439c_scsi_host_scsi_host'
  info.capabilities = { 'scsi_host' }
  scsi_host.host = 4 (0x4)
  info.category = 'scsi_host'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.1/host4/scsi_host/host4'
  info.product = 'SCSI Host Adapter'
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_439c_scsi_host'
  info.subsystem = 'scsi_host'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_439c_scsi_host_scsi_host'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi_host'

  33: udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_2'
  info.capabilities = { 'scsi_host' }
  scsi_host.host = 3 (0x3)
  info.category = 'scsi_host'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host3/scsi_host/host3'
  info.product = 'SCSI Host Adapter'
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4390'
  info.subsystem = 'scsi_host'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_2'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi_host'

  34: udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_1'
  info.capabilities = { 'scsi_host' }
  scsi_host.host = 2 (0x2)
  info.category = 'scsi_host'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host2/scsi_host/host2'
  info.product = 'SCSI Host Adapter'
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4390'
  info.subsystem = 'scsi_host'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_1'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi_host'

  35: udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_0'
  info.capabilities = { 'scsi_host' }
  scsi_host.host = 1 (0x1)
  info.category = 'scsi_host'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host1/scsi_host/host1'
  info.product = 'SCSI Host Adapter'
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4390'
  info.subsystem = 'scsi_host'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi_host'

  36: udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_scsi_device_lun0_scsi_generic'
  info.capabilities = { 'scsi_generic' }
  linux.device_file = '/dev/sg0'
  info.category = 'scsi_generic'
  scsi_generic.device = '/dev/sg0'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host0/target0:0:0/0:0:0:0/scsi_generic/sg0'
  info.product = 'SCSI Generic Interface'
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_scsi_device_lun0'
  info.subsystem = 'scsi_generic'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_scsi_device_lun0_scsi_generic'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi_generic'

  37: udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_scsi_host'
  info.capabilities = { 'scsi_host' }
  scsi_host.host = 0 (0x0)
  info.category = 'scsi_host'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host0/scsi_host/host0'
  info.product = 'SCSI Host Adapter'
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host'
  info.subsystem = 'scsi_host'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_scsi_host'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi_host'

  38: udi = '/org/freedesktop/Hal/devices/net_00_26_18_b8_da_07'
  info.capabilities = { 'net', 'net.80203', 'wake_on_lan' }
  info.category = 'net.80203'
  net.originating_device = '/org/freedesktop/Hal/devices/pci_10ec_8168'
  net.interface = 'eth0'
  net.address = '00:26:18:b8:da:07'
  net.linux.ifindex = 2 (0x2)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:06.0/0000:02:00.0/net/eth0'
  info.parent = '/org/freedesktop/Hal/devices/pci_10ec_8168'
  net.80203.mac_address = 163623524871ull (0x2618b8da07ull)
  net.arp_proto_hw_id = 1 (0x1)
  info.udi = '/org/freedesktop/Hal/devices/net_00_26_18_b8_da_07'
  info.subsystem = 'net'
  info.product = 'Networking Interface'
  org.freedesktop.Hal.Device.WakeOnLan.method_signatures = { '', '', 'b' }
  info.interfaces = { 'org.freedesktop.Hal.Device.WakeOnLan' }
  org.freedesktop.Hal.Device.WakeOnLan.method_names = { 'GetSupported', 'GetEnabled', 'SetEnabled' }
  org.freedesktop.Hal.Device.WakeOnLan.method_argnames = { '', '', 'enable' }
  org.freedesktop.Hal.Device.WakeOnLan.method_execpaths = { 'hal-system-wol-supported', 'hal-system-wol-enabled', 'hal-system-wol-enable' }
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'net'

  39: udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'
  info.capabilities = { 'input', 'button' }
  linux.device_file = '/dev/input/event1'
  info.category = 'input'
  input.product = 'Power Button (CM)'
  button.has_state = false
  input.device = '/dev/input/event1'
  button.type = 'power'
  info.addons.singleton = { 'hald-addon-input' }
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1'
  info.product = 'Power Button (CM)'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.subsystem = 'input'
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'input'

  40: udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'
  info.capabilities = { 'input', 'button' }
  linux.device_file = '/dev/input/event0'
  info.category = 'input'
  input.product = 'Power Button (FF)'
  button.has_state = false
  input.device = '/dev/input/event0'
  button.type = 'power'
  info.addons.singleton = { 'hald-addon-input' }
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0/event0'
  info.product = 'Power Button (FF)'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.subsystem = 'input'
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'input'

  41: udi = '/org/freedesktop/Hal/devices/pnp_PNP0c01'
  pnp.id = 'PNP0c01'
  pnp.description = 'System Board'
  info.linux.driver = 'system'
  linux.sysfs_path = '/sys/devices/pnp0/00:0e'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.product = 'System Board'
  info.subsystem = 'pnp'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c01'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'

  42: udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_3'
  pnp.id = 'PNP0c02'
  pnp.description = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'
  info.linux.driver = 'system'
  linux.sysfs_path = '/sys/devices/pnp0/00:0d'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'
  info.subsystem = 'pnp'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_3'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'

  43: udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_2'
  pnp.id = 'PNP0c02'
  pnp.description = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'
  info.linux.driver = 'system'
  linux.sysfs_path = '/sys/devices/pnp0/00:0c'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'
  info.subsystem = 'pnp'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_2'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'

  44: udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_1'
  pnp.id = 'PNP0c02'
  pnp.description = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'
  info.linux.driver = 'system'
  linux.sysfs_path = '/sys/devices/pnp0/00:0b'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'
  info.subsystem = 'pnp'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_1'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'

  45: udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_0'
  pnp.id = 'PNP0c02'
  pnp.description = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'
  info.linux.driver = 'system'
  linux.sysfs_path = '/sys/devices/pnp0/00:0a'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'
  info.subsystem = 'pnp'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'

  46: udi = '/org/freedesktop/Hal/devices/pnp_PNP0103'
  pnp.id = 'PNP0103'
  info.subsystem = 'pnp'
  info.product = 'PnP Device (PNP0103)'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  linux.sysfs_path = '/sys/devices/pnp0/00:09'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0103'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'

  47: udi = '/org/freedesktop/Hal/devices/pnp_PNP0700'
  pnp.id = 'PNP0700'
  pnp.description = 'PC standard floppy disk controller'
  info.subsystem = 'pnp'
  info.product = 'PC standard floppy disk controller'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  linux.sysfs_path = '/sys/devices/pnp0/00:08'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0700'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'

  48: udi = '/org/freedesktop/Hal/devices/pnp_PNP0c04'
  pnp.id = 'PNP0c04'
  pnp.description = 'Math Coprocessor'
  info.subsystem = 'pnp'
  info.product = 'Math Coprocessor'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  linux.sysfs_path = '/sys/devices/pnp0/00:07'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c04'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'

  49: udi = '/org/freedesktop/Hal/devices/pnp_PNP0800'
  pnp.id = 'PNP0800'
  pnp.description = 'AT-style speaker sound'
  info.subsystem = 'pnp'
  info.product = 'AT-style speaker sound'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  linux.sysfs_path = '/sys/devices/pnp0/00:06'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0800'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'

  50: udi = '/org/freedesktop/Hal/devices/pnp_PNP0b00'
  pnp.id = 'PNP0b00'
  pnp.description = 'AT Real-Time Clock'
  info.linux.driver = 'rtc_cmos'
  linux.sysfs_path = '/sys/devices/pnp0/00:05'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.product = 'AT Real-Time Clock'
  info.subsystem = 'pnp'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0b00'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'

  51: udi = '/org/freedesktop/Hal/devices/pnp_PNP0200'
  pnp.id = 'PNP0200'
  pnp.description = 'AT DMA Controller'
  info.subsystem = 'pnp'
  info.product = 'AT DMA Controller'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  linux.sysfs_path = '/sys/devices/pnp0/00:04'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0200'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'

  52: udi = '/org/freedesktop/Hal/devices/pnp_PNP0f03'
  pnp.id = 'PNP0f03'
  pnp.description = 'Microsoft PS/2-style Mouse'
  info.linux.driver = 'i8042 aux'
  linux.sysfs_path = '/sys/devices/pnp0/00:03'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.product = 'Microsoft PS/2-style Mouse'
  info.subsystem = 'pnp'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0f03'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'

  53: udi = '/org/freedesktop/Hal/devices/pnp_PNP0303'
  pnp.id = 'PNP0303'
  pnp.description = 'IBM Enhanced (101/102-key, PS/2 mouse support)'
  info.linux.driver = 'i8042 kbd'
  linux.sysfs_path = '/sys/devices/pnp0/00:02'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.product = 'IBM Enhanced (101/102-key, PS/2 mouse support)'
  info.subsystem = 'pnp'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0303'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'

  54: udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02'
  pnp.id = 'PNP0c02'
  pnp.description = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'
  info.linux.driver = 'system'
  linux.sysfs_path = '/sys/devices/pnp0/00:01'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'
  info.subsystem = 'pnp'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'

  55: udi = '/org/freedesktop/Hal/devices/pnp_PNP0a03'
  pnp.id = 'PNP0a03'
  pnp.description = 'PCI Bus'
  info.subsystem = 'pnp'
  info.product = 'PCI Bus'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  linux.sysfs_path = '/sys/devices/pnp0/00:00'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0a03'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'

  56: udi = '/org/freedesktop/Hal/devices/platform_serial8250'
  platform.id = 'serial8250'
  info.linux.driver = 'serial8250'
  info.subsystem = 'platform'
  info.product = 'Platform Device (serial8250)'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  linux.sysfs_path = '/sys/devices/platform/serial8250'
  info.udi = '/org/freedesktop/Hal/devices/platform_serial8250'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'platform'

  57: udi = '/org/freedesktop/Hal/devices/platform_pcspkr'
  platform.id = 'pcspkr'
  info.linux.driver = 'pcspkr'
  info.subsystem = 'platform'
  info.product = 'Platform Device (pcspkr)'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  linux.sysfs_path = '/sys/devices/platform/pcspkr'
  info.udi = '/org/freedesktop/Hal/devices/platform_pcspkr'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'platform'

  58: udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'
  serio.id = 'serio1'
  serio.description = 'i8042 AUX port'
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1'
  info.product = 'i8042 AUX port'
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'
  info.subsystem = 'serio'
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'serio'

  59: udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'
  serio.id = 'serio0'
  serio.description = 'i8042 KBD port'
  linux.sysfs_path = '/sys/devices/platform/i8042/serio0'
  info.product = 'i8042 KBD port'
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'
  info.subsystem = 'serio'
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'serio'

  60: udi = '/org/freedesktop/Hal/devices/platform_i8042'
  platform.id = 'i8042'
  info.linux.driver = 'i8042'
  info.subsystem = 'platform'
  info.product = 'Platform Device (i8042)'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  linux.sysfs_path = '/sys/devices/platform/i8042'
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'platform'

  61: udi = '/org/freedesktop/Hal/devices/platform_eisa_0'
  platform.id = 'eisa.0'
  info.subsystem = 'platform'
  info.product = 'Platform Device (eisa.0)'
  info.udi = '/org/freedesktop/Hal/devices/platform_eisa_0'
  linux.sysfs_path = '/sys/devices/platform/eisa.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'platform'

  62: udi = '/org/freedesktop/Hal/devices/platform_Fixed_MDIO_bus_0'
  platform.id = 'Fixed MDIO bus.0'
  info.subsystem = 'platform'
  info.product = 'Platform Device (Fixed MDIO bus.0)'
  info.udi = '/org/freedesktop/Hal/devices/platform_Fixed_MDIO_bus_0'
  linux.sysfs_path = '/sys/devices/platform/Fixed MDIO bus.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'platform'

  63: udi = '/org/freedesktop/Hal/devices/pci_1022_1204'
  info.udi = '/org/freedesktop/Hal/devices/pci_1022_1204'
  info.subsystem = 'pci'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.4'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.4'
  pci.product_id = 4612 (0x1204)
  pci.vendor_id = 4130 (0x1022)
  pci.subsys_product_id = 0 (0x0)
  pci.subsys_vendor_id = 0 (0x0)
  pci.device_class = 6 (0x6)
  pci.device_subclass = 0 (0x0)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Advanced Micro Devices [AMD]'
  info.vendor = 'Advanced Micro Devices [AMD]'
  pci.product = 'Family 10h [Opteron, Athlon64, Sempron] Link Control'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.product = 'Family 10h [Opteron, Athlon64, Sempron] Link Control'

  64: udi = '/org/freedesktop/Hal/devices/pci_1022_1203'
  info.udi = '/org/freedesktop/Hal/devices/pci_1022_1203'
  info.subsystem = 'pci'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.3'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.3'
  pci.product_id = 4611 (0x1203)
  pci.vendor_id = 4130 (0x1022)
  pci.subsys_product_id = 0 (0x0)
  pci.subsys_vendor_id = 0 (0x0)
  pci.device_class = 6 (0x6)
  pci.device_subclass = 0 (0x0)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Advanced Micro Devices [AMD]'
  info.vendor = 'Advanced Micro Devices [AMD]'
  pci.product = 'Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.product = 'Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control'

  65: udi = '/org/freedesktop/Hal/devices/pci_1022_1202'
  info.udi = '/org/freedesktop/Hal/devices/pci_1022_1202'
  info.subsystem = 'pci'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.2'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.2'
  pci.product_id = 4610 (0x1202)
  pci.vendor_id = 4130 (0x1022)
  pci.subsys_product_id = 0 (0x0)
  pci.subsys_vendor_id = 0 (0x0)
  pci.device_class = 6 (0x6)
  pci.device_subclass = 0 (0x0)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Advanced Micro Devices [AMD]'
  info.vendor = 'Advanced Micro Devices [AMD]'
  pci.product = 'Family 10h [Opteron, Athlon64, Sempron] DRAM Controller'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.product = 'Family 10h [Opteron, Athlon64, Sempron] DRAM Controller'

  66: udi = '/org/freedesktop/Hal/devices/pci_1022_1201'
  info.udi = '/org/freedesktop/Hal/devices/pci_1022_1201'
  info.subsystem = 'pci'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.1'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.1'
  pci.product_id = 4609 (0x1201)
  pci.vendor_id = 4130 (0x1022)
  pci.subsys_product_id = 0 (0x0)
  pci.subsys_vendor_id = 0 (0x0)
  pci.device_class = 6 (0x6)
  pci.device_subclass = 0 (0x0)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Advanced Micro Devices [AMD]'
  info.vendor = 'Advanced Micro Devices [AMD]'
  pci.product = 'Family 10h [Opteron, Athlon64, Sempron] Address Map'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.product = 'Family 10h [Opteron, Athlon64, Sempron] Address Map'

  67: udi = '/org/freedesktop/Hal/devices/pci_1022_1200'
  info.udi = '/org/freedesktop/Hal/devices/pci_1022_1200'
  info.subsystem = 'pci'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.0'
  pci.product_id = 4608 (0x1200)
  pci.vendor_id = 4130 (0x1022)
  pci.subsys_product_id = 0 (0x0)
  pci.subsys_vendor_id = 0 (0x0)
  pci.device_class = 6 (0x6)
  pci.device_subclass = 0 (0x0)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Advanced Micro Devices [AMD]'
  info.vendor = 'Advanced Micro Devices [AMD]'
  pci.product = 'Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.product = 'Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration'

  68: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_14_5_if0'
  linux.hotplug_type = 2 (0x2)
  usb.interface.subclass = 0 (0x0)
  usb.interface.protocol = 0 (0x0)
  usb.interface.class = 9 (0x9)
  linux.subsystem = 'usb'
  info.linux.driver = 'hub'
  info.subsystem = 'usb'
  info.product = 'USB Hub Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_14_5_if0'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.device_class = 9 (0x9)
  usb.device_subclass = 0 (0x0)
  usb.num_interfaces = 1 (0x1)
  usb.device_protocol = 0 (0x0)
  usb.product_id = 1 (0x1)
  usb.vendor = 'Linux Foundation'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5/usb7/7-0:1.0'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5/usb7/7-0:1.0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_14_5'
  usb.max_power = 0 (0x0)
  usb.device_revision_bcd = 518 (0x206)
  usb.linux.device_number = 1 (0x1)
  usb.num_ports = 2 (0x2)
  usb.speed = 12.0000
  usb.serial = '0000:00:14.5'
  usb.is_self_powered = true
  usb.version = 1.10000
  usb.bus_number = 7 (0x7)
  usb.can_wake_up = true
  usb.product = 'USB Hub Interface'
  usb.vendor_id = 7531 (0x1d6b)
  usb.interface.number = 0 (0x0)

  69: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_14_5'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'usb'
  info.subsystem = 'usb_device'
  info.product = '1.1 root hub'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_14_5'
  usb_device.configuration_value = 1 (0x1)
  usb_device.num_configurations = 1 (0x1)
  usb_device.device_class = 9 (0x9)
  usb_device.device_subclass = 0 (0x0)
  usb_device.num_interfaces = 1 (0x1)
  usb_device.device_protocol = 0 (0x0)
  usb_device.product_id = 1 (0x1)
  usb_device.vendor = 'Linux Foundation'
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5/usb7'
  usb_device.device_revision_bcd = 518 (0x206)
  usb_device.max_power = 0 (0x0)
  usb_device.num_ports = 2 (0x2)
  usb_device.linux.device_number = 1 (0x1)
  usb_device.serial = '0000:00:14.5'
  usb_device.speed = 12.0000
  usb_device.version = 1.10000
  usb_device.is_self_powered = true
  usb_device.can_wake_up = true
  usb_device.bus_number = 7 (0x7)
  linux.device_file = '/dev/bus/usb/007/001'
  usb_device.vendor_id = 7531 (0x1d6b)
  usb_device.product = '1.1 root hub'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5/usb7'
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4399'
  info.vendor = 'Linux Foundation'

  70: udi = '/org/freedesktop/Hal/devices/pci_1002_4399'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4399'
  info.subsystem = 'pci'
  info.linux.driver = 'ohci_hcd'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5'
  pci.product_id = 17305 (0x4399)
  pci.vendor_id = 4098 (0x1002)
  pci.subsys_product_id = 33673 (0x8389)
  pci.subsys_vendor_id = 4163 (0x1043)
  pci.device_class = 12 (0xc)
  pci.device_subclass = 3 (0x3)
  pci.device_protocol = 16 (0x10)
  pci.vendor = 'ATI Technologies Inc'
  info.vendor = 'ATI Technologies Inc'
  pci.product = 'SB700/SB800 USB OHCI2 Controller'
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.product = 'SB700/SB800 USB OHCI2 Controller'

  71: udi = '/org/freedesktop/Hal/devices/pci_1002_4384'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4384'
  info.subsystem = 'pci'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.4'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.4'
  pci.product_id = 17284 (0x4384)
  pci.vendor_id = 4098 (0x1002)
  pci.subsys_product_id = 0 (0x0)
  pci.subsys_vendor_id = 0 (0x0)
  pci.device_class = 6 (0x6)
  pci.device_subclass = 4 (0x4)
  pci.device_protocol = 1 (0x1)
  pci.vendor = 'ATI Technologies Inc'
  info.vendor = 'ATI Technologies Inc'
  pci.product = 'SBx00 PCI to PCI Bridge'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.product = 'SBx00 PCI to PCI Bridge'

  72: udi = '/org/freedesktop/Hal/devices/pci_1002_439d'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_439d'
  info.subsystem = 'pci'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.3'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.3'
  pci.product_id = 17309 (0x439d)
  pci.vendor_id = 4098 (0x1002)
  pci.subsys_product_id = 33673 (0x8389)
  pci.subsys_vendor_id = 4163 (0x1043)
  pci.device_class = 6 (0x6)
  pci.device_subclass = 1 (0x1)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'ATI Technologies Inc'
  info.vendor = 'ATI Technologies Inc'
  pci.product = 'SB700/SB800 LPC host controller'
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.product = 'SB700/SB800 LPC host controller'

  73: udi = '/org/freedesktop/Hal/devices/pci_1002_4383'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383'
  info.subsystem = 'pci'
  info.linux.driver = 'HDA Intel'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2'
  pci.product_id = 17283 (0x4383)
  pci.vendor_id = 4098 (0x1002)
  pci.subsys_product_id = 33514 (0x82ea)
  pci.subsys_vendor_id = 4163 (0x1043)
  pci.device_class = 4 (0x4)
  pci.device_subclass = 3 (0x3)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'ATI Technologies Inc'
  info.vendor = 'ATI Technologies Inc'
  pci.product = 'SBx00 Azalia (Intel HDA)'
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.product = 'SBx00 Azalia (Intel HDA)'

  74: udi = '/org/freedesktop/Hal/devices/pci_1002_439c_scsi_host_scsi_device_lun0'
  info.linux.driver = 'sr'
  scsi.host = 4 (0x4)
  scsi.bus = 0 (0x0)
  scsi.target = 0 (0x0)
  scsi.lun = 0 (0x0)
  scsi.model = 'DVD Writer 1040d'
  scsi.vendor = 'HP'
  scsi.type = 'cdrom'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.1/host4/target4:0:0/4:0:0:0'
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_439c_scsi_host'
  info.product = 'SCSI Device'
  info.subsystem = 'scsi'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_439c_scsi_host_scsi_device_lun0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi'

  75: udi = '/org/freedesktop/Hal/devices/pci_1002_439c_scsi_host'
  info.capabilities = { 'scsi_host' }
  scsi_host.host = 4 (0x4)
  info.category = 'scsi_host'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.1/host4'
  info.product = 'SCSI Host Adapter'
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_439c'
  info.subsystem = 'scsi_host'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_439c_scsi_host'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi_host'

  76: udi = '/org/freedesktop/Hal/devices/pci_1002_439c'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_439c'
  info.subsystem = 'pci'
  info.linux.driver = 'pata_atiixp'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.1'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.1'
  pci.product_id = 17308 (0x439c)
  pci.vendor_id = 4098 (0x1002)
  pci.subsys_product_id = 33673 (0x8389)
  pci.subsys_vendor_id = 4163 (0x1043)
  pci.device_class = 1 (0x1)
  pci.device_subclass = 1 (0x1)
  pci.device_protocol = 138 (0x8a)
  pci.vendor = 'ATI Technologies Inc'
  info.vendor = 'ATI Technologies Inc'
  pci.product = 'SB700/SB800 IDE Controller'
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.product = 'SB700/SB800 IDE Controller'

  77: udi = '/org/freedesktop/Hal/devices/pci_1002_4385'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4385'
  info.subsystem = 'pci'
  info.linux.driver = 'piix4_smbus'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.0'
  pci.product_id = 17285 (0x4385)
  pci.vendor_id = 4098 (0x1002)
  pci.subsys_product_id = 33673 (0x8389)
  pci.subsys_vendor_id = 4163 (0x1043)
  pci.device_class = 12 (0xc)
  pci.device_subclass = 5 (0x5)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'ATI Technologies Inc'
  info.vendor = 'ATI Technologies Inc'
  pci.product = 'SBx00 SMBus Controller'
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.product = 'SBx00 SMBus Controller'

  78: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_13_2_if0'
  linux.hotplug_type = 2 (0x2)
  usb.interface.subclass = 0 (0x0)
  usb.interface.protocol = 0 (0x0)
  usb.interface.class = 9 (0x9)
  linux.subsystem = 'usb'
  info.linux.driver = 'hub'
  info.subsystem = 'usb'
  info.product = 'USB Hub Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_13_2_if0'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.device_class = 9 (0x9)
  usb.device_subclass = 0 (0x0)
  usb.num_interfaces = 1 (0x1)
  usb.device_protocol = 0 (0x0)
  usb.product_id = 2 (0x2)
  usb.vendor = 'Linux Foundation'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.2/usb2/2-0:1.0'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.2/usb2/2-0:1.0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_13_2'
  usb.max_power = 0 (0x0)
  usb.device_revision_bcd = 518 (0x206)
  usb.linux.device_number = 1 (0x1)
  usb.num_ports = 6 (0x6)
  usb.speed = 480.000
  usb.serial = '0000:00:13.2'
  usb.is_self_powered = true
  usb.version = 2.00000
  usb.bus_number = 2 (0x2)
  usb.can_wake_up = true
  usb.product = 'USB Hub Interface'
  usb.vendor_id = 7531 (0x1d6b)
  usb.interface.number = 0 (0x0)

  79: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_13_2'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'usb'
  info.subsystem = 'usb_device'
  info.product = '2.0 root hub'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_13_2'
  usb_device.configuration_value = 1 (0x1)
  usb_device.num_configurations = 1 (0x1)
  usb_device.device_class = 9 (0x9)
  usb_device.device_subclass = 0 (0x0)
  usb_device.num_interfaces = 1 (0x1)
  usb_device.device_protocol = 0 (0x0)
  usb_device.product_id = 2 (0x2)
  usb_device.vendor = 'Linux Foundation'
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.2/usb2'
  usb_device.device_revision_bcd = 518 (0x206)
  usb_device.max_power = 0 (0x0)
  usb_device.num_ports = 6 (0x6)
  usb_device.linux.device_number = 1 (0x1)
  usb_device.serial = '0000:00:13.2'
  usb_device.speed = 480.000
  usb_device.version = 2.00000
  usb_device.is_self_powered = true
  usb_device.can_wake_up = true
  usb_device.bus_number = 2 (0x2)
  linux.device_file = '/dev/bus/usb/002/001'
  usb_device.vendor_id = 7531 (0x1d6b)
  usb_device.product = '2.0 root hub'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.2/usb2'
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4396_0'
  info.vendor = 'Linux Foundation'

  80: udi = '/org/freedesktop/Hal/devices/pci_1002_4396_0'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4396_0'
  info.subsystem = 'pci'
  info.linux.driver = 'ehci_hcd'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.2'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.2'
  pci.product_id = 17302 (0x4396)
  pci.vendor_id = 4098 (0x1002)
  pci.subsys_product_id = 33673 (0x8389)
  pci.subsys_vendor_id = 4163 (0x1043)
  pci.device_class = 12 (0xc)
  pci.device_subclass = 3 (0x3)
  pci.device_protocol = 32 (0x20)
  pci.vendor = 'ATI Technologies Inc'
  info.vendor = 'ATI Technologies Inc'
  pci.product = 'SB700/SB800 USB EHCI Controller'
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.product = 'SB700/SB800 USB EHCI Controller'

  81: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_1_if0'
  linux.hotplug_type = 2 (0x2)
  usb.interface.subclass = 0 (0x0)
  usb.interface.protocol = 0 (0x0)
  usb.interface.class = 9 (0x9)
  linux.subsystem = 'usb'
  info.linux.driver = 'hub'
  info.subsystem = 'usb'
  info.product = 'USB Hub Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_1_if0'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.device_class = 9 (0x9)
  usb.device_subclass = 0 (0x0)
  usb.num_interfaces = 1 (0x1)
  usb.device_protocol = 0 (0x0)
  usb.product_id = 1 (0x1)
  usb.vendor = 'Linux Foundation'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.1/usb6/6-0:1.0'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.1/usb6/6-0:1.0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_1'
  usb.max_power = 0 (0x0)
  usb.device_revision_bcd = 518 (0x206)
  usb.linux.device_number = 1 (0x1)
  usb.num_ports = 3 (0x3)
  usb.speed = 12.0000
  usb.serial = '0000:00:13.1'
  usb.is_self_powered = true
  usb.version = 1.10000
  usb.bus_number = 6 (0x6)
  usb.can_wake_up = true
  usb.product = 'USB Hub Interface'
  usb.vendor_id = 7531 (0x1d6b)
  usb.interface.number = 0 (0x0)

  82: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_1'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'usb'
  info.subsystem = 'usb_device'
  info.product = '1.1 root hub'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_1'
  usb_device.configuration_value = 1 (0x1)
  usb_device.num_configurations = 1 (0x1)
  usb_device.device_class = 9 (0x9)
  usb_device.device_subclass = 0 (0x0)
  usb_device.num_interfaces = 1 (0x1)
  usb_device.device_protocol = 0 (0x0)
  usb_device.product_id = 1 (0x1)
  usb_device.vendor = 'Linux Foundation'
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.1/usb6'
  usb_device.device_revision_bcd = 518 (0x206)
  usb_device.max_power = 0 (0x0)
  usb_device.num_ports = 3 (0x3)
  usb_device.linux.device_number = 1 (0x1)
  usb_device.serial = '0000:00:13.1'
  usb_device.speed = 12.0000
  usb_device.version = 1.10000
  usb_device.is_self_powered = true
  usb_device.can_wake_up = true
  usb_device.bus_number = 6 (0x6)
  linux.device_file = '/dev/bus/usb/006/001'
  usb_device.vendor_id = 7531 (0x1d6b)
  usb_device.product = '1.1 root hub'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.1/usb6'
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4398_0'
  info.vendor = 'Linux Foundation'

  83: udi = '/org/freedesktop/Hal/devices/pci_1002_4398_0'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4398_0'
  info.subsystem = 'pci'
  info.linux.driver = 'ohci_hcd'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.1'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.1'
  pci.product_id = 17304 (0x4398)
  pci.vendor_id = 4098 (0x1002)
  pci.subsys_product_id = 33673 (0x8389)
  pci.subsys_vendor_id = 4163 (0x1043)
  pci.device_class = 12 (0xc)
  pci.device_subclass = 3 (0x3)
  pci.device_protocol = 16 (0x10)
  pci.vendor = 'ATI Technologies Inc'
  info.vendor = 'ATI Technologies Inc'
  pci.product = 'SB700 USB OHCI1 Controller'
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.product = 'SB700 USB OHCI1 Controller'

  84: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_0_if0'
  linux.hotplug_type = 2 (0x2)
  usb.interface.subclass = 0 (0x0)
  usb.interface.protocol = 0 (0x0)
  usb.interface.class = 9 (0x9)
  linux.subsystem = 'usb'
  info.linux.driver = 'hub'
  info.subsystem = 'usb'
  info.product = 'USB Hub Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_0_if0'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.device_class = 9 (0x9)
  usb.device_subclass = 0 (0x0)
  usb.num_interfaces = 1 (0x1)
  usb.device_protocol = 0 (0x0)
  usb.product_id = 1 (0x1)
  usb.vendor = 'Linux Foundation'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.0/usb5/5-0:1.0'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.0/usb5/5-0:1.0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_0'
  usb.max_power = 0 (0x0)
  usb.device_revision_bcd = 518 (0x206)
  usb.linux.device_number = 1 (0x1)
  usb.num_ports = 3 (0x3)
  usb.speed = 12.0000
  usb.serial = '0000:00:13.0'
  usb.is_self_powered = true
  usb.version = 1.10000
  usb.bus_number = 5 (0x5)
  usb.can_wake_up = true
  usb.product = 'USB Hub Interface'
  usb.vendor_id = 7531 (0x1d6b)
  usb.interface.number = 0 (0x0)

  85: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'usb'
  info.subsystem = 'usb_device'
  info.product = '1.1 root hub'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_0'
  usb_device.configuration_value = 1 (0x1)
  usb_device.num_configurations = 1 (0x1)
  usb_device.device_class = 9 (0x9)
  usb_device.device_subclass = 0 (0x0)
  usb_device.num_interfaces = 1 (0x1)
  usb_device.device_protocol = 0 (0x0)
  usb_device.product_id = 1 (0x1)
  usb_device.vendor = 'Linux Foundation'
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.0/usb5'
  usb_device.device_revision_bcd = 518 (0x206)
  usb_device.max_power = 0 (0x0)
  usb_device.num_ports = 3 (0x3)
  usb_device.linux.device_number = 1 (0x1)
  usb_device.serial = '0000:00:13.0'
  usb_device.speed = 12.0000
  usb_device.version = 1.10000
  usb_device.is_self_powered = true
  usb_device.can_wake_up = true
  usb_device.bus_number = 5 (0x5)
  linux.device_file = '/dev/bus/usb/005/001'
  usb_device.vendor_id = 7531 (0x1d6b)
  usb_device.product = '1.1 root hub'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.0/usb5'
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4397_0'
  info.vendor = 'Linux Foundation'

  86: udi = '/org/freedesktop/Hal/devices/pci_1002_4397_0'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4397_0'
  info.subsystem = 'pci'
  info.linux.driver = 'ohci_hcd'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.0'
  pci.product_id = 17303 (0x4397)
  pci.vendor_id = 4098 (0x1002)
  pci.subsys_product_id = 33673 (0x8389)
  pci.subsys_vendor_id = 4163 (0x1043)
  pci.device_class = 12 (0xc)
  pci.device_subclass = 3 (0x3)
  pci.device_protocol = 16 (0x10)
  pci.vendor = 'ATI Technologies Inc'
  info.vendor = 'ATI Technologies Inc'
  pci.product = 'SB700/SB800 USB OHCI0 Controller'
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.product = 'SB700/SB800 USB OHCI0 Controller'

  87: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_12_2_if0'
  linux.hotplug_type = 2 (0x2)
  usb.interface.subclass = 0 (0x0)
  usb.interface.protocol = 0 (0x0)
  usb.interface.class = 9 (0x9)
  linux.subsystem = 'usb'
  info.linux.driver = 'hub'
  info.subsystem = 'usb'
  info.product = 'USB Hub Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_12_2_if0'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.device_class = 9 (0x9)
  usb.device_subclass = 0 (0x0)
  usb.num_interfaces = 1 (0x1)
  usb.device_protocol = 0 (0x0)
  usb.product_id = 2 (0x2)
  usb.vendor = 'Linux Foundation'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-0:1.0'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-0:1.0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_12_2'
  usb.max_power = 0 (0x0)
  usb.device_revision_bcd = 518 (0x206)
  usb.linux.device_number = 1 (0x1)
  usb.num_ports = 6 (0x6)
  usb.speed = 480.000
  usb.serial = '0000:00:12.2'
  usb.is_self_powered = true
  usb.version = 2.00000
  usb.bus_number = 1 (0x1)
  usb.can_wake_up = true
  usb.product = 'USB Hub Interface'
  usb.vendor_id = 7531 (0x1d6b)
  usb.interface.number = 0 (0x0)

  88: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_12_2'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'usb'
  info.subsystem = 'usb_device'
  info.product = '2.0 root hub'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_12_2'
  usb_device.configuration_value = 1 (0x1)
  usb_device.num_configurations = 1 (0x1)
  usb_device.device_class = 9 (0x9)
  usb_device.device_subclass = 0 (0x0)
  usb_device.num_interfaces = 1 (0x1)
  usb_device.device_protocol = 0 (0x0)
  usb_device.product_id = 2 (0x2)
  usb_device.vendor = 'Linux Foundation'
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1'
  usb_device.device_revision_bcd = 518 (0x206)
  usb_device.max_power = 0 (0x0)
  usb_device.num_ports = 6 (0x6)
  usb_device.linux.device_number = 1 (0x1)
  usb_device.serial = '0000:00:12.2'
  usb_device.speed = 480.000
  usb_device.version = 2.00000
  usb_device.is_self_powered = true
  usb_device.can_wake_up = true

  88: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_12_2'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'usb'
  info.subsystem = 'usb_device'
  info.product = '2.0 root hub'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_12_2'
  usb_device.configuration_value = 1 (0x1)
  usb_device.num_configurations = 1 (0x1)
  usb_device.device_class = 9 (0x9)
  usb_device.device_subclass = 0 (0x0)
  usb_device.num_interfaces = 1 (0x1)
  usb_device.device_protocol = 0 (0x0)
  usb_device.product_id = 2 (0x2)
  usb_device.vendor = 'Linux Foundation'
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1'
  usb_device.device_revision_bcd = 518 (0x206)
  usb_device.max_power = 0 (0x0)
  usb_device.num_ports = 6 (0x6)
  usb_device.linux.device_number = 1 (0x1)
  usb_device.serial = '0000:00:12.2'
  usb_device.speed = 480.000
  usb_device.version = 2.00000
  usb_device.is_self_powered = true
  usb_device.can_wake_up = true
  usb_device.bus_number = 1 (0x1)
  linux.device_file = '/dev/bus/usb/001/001'
  usb_device.vendor_id = 7531 (0x1d6b)
  usb_device.product = '2.0 root hub'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1'
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4396'
  info.vendor = 'Linux Foundation'

  89: udi = '/org/freedesktop/Hal/devices/pci_1002_4396'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4396'
  info.subsystem = 'pci'
  info.linux.driver = 'ehci_hcd'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2'
  pci.product_id = 17302 (0x4396)
  pci.vendor_id = 4098 (0x1002)
  pci.subsys_product_id = 33673 (0x8389)
  pci.subsys_vendor_id = 4163 (0x1043)
  pci.device_class = 12 (0xc)
  pci.device_subclass = 3 (0x3)
  pci.device_protocol = 32 (0x20)
  pci.vendor = 'ATI Technologies Inc'
  info.vendor = 'ATI Technologies Inc'
  pci.product = 'SB700/SB800 USB EHCI Controller'
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.product = 'SB700/SB800 USB EHCI Controller'

  90: udi = '/org/freedesktop/Hal/devices/usb_device_46e_5542_noserial_if1'
  linux.hotplug_type = 2 (0x2)
  usb.interface.subclass = 0 (0x0)
  usb.interface.protocol = 0 (0x0)
  usb.interface.class = 3 (0x3)
  usb.configuration = 'HOLTEK UH05'
  info.linux.driver = 'usbhid'
  linux.subsystem = 'usb'
  info.subsystem = 'usb'
  info.product = 'USB HID Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46e_5542_noserial_if1'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.device_class = 0 (0x0)
  usb.device_subclass = 0 (0x0)
  usb.num_interfaces = 2 (0x2)
  usb.device_protocol = 0 (0x0)
  usb.product_id = 21826 (0x5542)
  usb.vendor = 'Behavior Tech. Computer Corp.'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.1'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.1'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_46e_5542_noserial'
  usb.max_power = 100 (0x64)
  usb.device_revision_bcd = 272 (0x110)
  usb.linux.device_number = 3 (0x3)
  usb.num_ports = 0 (0x0)
  usb.version = 1.10000
  usb.is_self_powered = false
  usb.speed = 1.50000
  usb.can_wake_up = true
  usb.vendor_id = 1134 (0x46e)
  usb.product = 'USB HID Interface'
  usb.bus_number = 4 (0x4)
  usb.interface.number = 1 (0x1)

  91: udi = '/org/freedesktop/Hal/devices/usb_device_46e_5542_noserial_if0'
  linux.hotplug_type = 2 (0x2)
  usb.interface.subclass = 1 (0x1)
  usb.interface.protocol = 1 (0x1)
  usb.interface.class = 3 (0x3)
  usb.configuration = 'HOLTEK UH05'
  info.linux.driver = 'usbhid'
  linux.subsystem = 'usb'
  info.subsystem = 'usb'
  info.product = 'USB HID Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46e_5542_noserial_if0'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.device_class = 0 (0x0)
  usb.device_subclass = 0 (0x0)
  usb.num_interfaces = 2 (0x2)
  usb.device_protocol = 0 (0x0)
  usb.product_id = 21826 (0x5542)
  usb.vendor = 'Behavior Tech. Computer Corp.'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_46e_5542_noserial'
  usb.max_power = 100 (0x64)
  usb.device_revision_bcd = 272 (0x110)
  usb.linux.device_number = 3 (0x3)
  usb.num_ports = 0 (0x0)
  usb.version = 1.10000
  usb.is_self_powered = false
  usb.speed = 1.50000
  usb.can_wake_up = true
  usb.vendor_id = 1134 (0x46e)
  usb.product = 'USB HID Interface'
  usb.bus_number = 4 (0x4)
  usb.interface.number = 0 (0x0)

  92: udi = '/org/freedesktop/Hal/devices/usb_device_46e_5542_noserial'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  usb_device.configuration = 'HOLTEK UH05'
  info.linux.driver = 'usb'
  info.subsystem = 'usb_device'
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4/4-3'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46e_5542_noserial'
  usb_device.configuration_value = 1 (0x1)
  usb_device.num_configurations = 1 (0x1)
  usb_device.device_class = 0 (0x0)
  usb_device.device_subclass = 0 (0x0)
  usb_device.device_protocol = 0 (0x0)
  usb_device.vendor_id = 1134 (0x46e)
  usb_device.product_id = 21826 (0x5542)
  usb_device.num_interfaces = 2 (0x2)
  usb_device.vendor = 'Behavior Tech. Computer Corp.'
  usb_device.device_revision_bcd = 272 (0x110)
  usb_device.max_power = 100 (0x64)
  usb_device.num_ports = 0 (0x0)
  usb_device.linux.device_number = 3 (0x3)
  info.product = 'USB Multimedia Keyboard'
  usb_device.speed = 1.50000
  usb_device.version = 1.10000
  usb_device.is_self_powered = false
  usb_device.can_wake_up = true
  usb_device.bus_number = 4 (0x4)
  linux.device_file = '/dev/bus/usb/004/003'
  usb_device.product = 'USB Multimedia Keyboard'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4/4-3'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_1'
  info.vendor = 'Behavior Tech. Computer Corp.'

  93: udi = '/org/freedesktop/Hal/devices/usb_device_46d_c049_noserial_if1'
  linux.hotplug_type = 2 (0x2)
  usb.interface.subclass = 0 (0x0)
  usb.interface.protocol = 0 (0x0)
  usb.interface.class = 3 (0x3)
  usb.configuration = 'U52.0 B0005'
  info.linux.driver = 'usbhid'
  linux.subsystem = 'usb'
  info.subsystem = 'usb'
  info.product = 'USB HID Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c049_noserial_if1'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.device_class = 0 (0x0)
  usb.device_subclass = 0 (0x0)
  usb.num_interfaces = 2 (0x2)
  usb.device_protocol = 0 (0x0)
  usb.product_id = 49225 (0xc049)
  usb.vendor = 'Logitech, Inc.'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.1'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.1'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_46d_c049_noserial'
  usb.max_power = 98 (0x62)
  usb.device_revision_bcd = 20992 (0x5200)
  usb.linux.device_number = 2 (0x2)
  usb.num_ports = 0 (0x0)
  usb.version = 2.00000
  usb.is_self_powered = false
  usb.speed = 12.0000
  usb.can_wake_up = true
  usb.vendor_id = 1133 (0x46d)
  usb.product = 'USB HID Interface'
  usb.bus_number = 4 (0x4)
  usb.interface.number = 1 (0x1)

  94: udi = '/org/freedesktop/Hal/devices/usb_device_46d_c049_noserial_if0'
  linux.hotplug_type = 2 (0x2)
  usb.interface.subclass = 1 (0x1)
  usb.interface.protocol = 2 (0x2)
  usb.interface.class = 3 (0x3)
  usb.configuration = 'U52.0 B0005'
  info.linux.driver = 'usbhid'
  linux.subsystem = 'usb'
  info.subsystem = 'usb'
  info.product = 'USB HID Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c049_noserial_if0'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.device_class = 0 (0x0)
  usb.device_subclass = 0 (0x0)
  usb.num_interfaces = 2 (0x2)
  usb.device_protocol = 0 (0x0)
  usb.product_id = 49225 (0xc049)
  usb.vendor = 'Logitech, Inc.'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_46d_c049_noserial'
  usb.max_power = 98 (0x62)
  usb.device_revision_bcd = 20992 (0x5200)
  usb.linux.device_number = 2 (0x2)
  usb.num_ports = 0 (0x0)
  usb.version = 2.00000
  usb.is_self_powered = false
  usb.speed = 12.0000
  usb.can_wake_up = true
  usb.vendor_id = 1133 (0x46d)
  usb.product = 'USB HID Interface'
  usb.bus_number = 4 (0x4)
  usb.interface.number = 0 (0x0)

  95: udi = '/org/freedesktop/Hal/devices/usb_device_46d_c049_noserial'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  usb_device.configuration = 'U52.0 B0005'
  info.linux.driver = 'usb'
  info.subsystem = 'usb_device'
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4/4-2'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c049_noserial'
  usb_device.configuration_value = 1 (0x1)
  usb_device.num_configurations = 1 (0x1)
  usb_device.device_class = 0 (0x0)
  usb_device.device_subclass = 0 (0x0)
  usb_device.device_protocol = 0 (0x0)
  usb_device.vendor_id = 1133 (0x46d)
  usb_device.product_id = 49225 (0xc049)
  usb_device.num_interfaces = 2 (0x2)
  usb_device.vendor = 'Logitech, Inc.'
  usb_device.device_revision_bcd = 20992 (0x5200)
  usb_device.max_power = 98 (0x62)
  usb_device.num_ports = 0 (0x0)
  usb_device.linux.device_number = 2 (0x2)
  info.product = 'G5 Laser Mouse'
  usb_device.speed = 12.0000
  usb_device.version = 2.00000
  usb_device.is_self_powered = false
  usb_device.can_wake_up = true
  usb_device.bus_number = 4 (0x4)
  linux.device_file = '/dev/bus/usb/004/002'
  usb_device.product = 'G5 Laser Mouse'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4/4-2'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_1'
  info.vendor = 'Logitech, Inc.'

  96: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_1_if0'
  linux.hotplug_type = 2 (0x2)
  usb.interface.subclass = 0 (0x0)
  usb.interface.protocol = 0 (0x0)
  usb.interface.class = 9 (0x9)
  linux.subsystem = 'usb'
  info.linux.driver = 'hub'
  info.subsystem = 'usb'
  info.product = 'USB Hub Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_1_if0'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.device_class = 9 (0x9)
  usb.device_subclass = 0 (0x0)
  usb.num_interfaces = 1 (0x1)
  usb.device_protocol = 0 (0x0)
  usb.product_id = 1 (0x1)
  usb.vendor = 'Linux Foundation'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4/4-0:1.0'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4/4-0:1.0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_1'
  usb.max_power = 0 (0x0)
  usb.device_revision_bcd = 518 (0x206)
  usb.linux.device_number = 1 (0x1)
  usb.num_ports = 3 (0x3)
  usb.speed = 12.0000
  usb.serial = '0000:00:12.1'
  usb.is_self_powered = true
  usb.version = 1.10000
  usb.bus_number = 4 (0x4)
  usb.can_wake_up = true
  usb.product = 'USB Hub Interface'
  usb.vendor_id = 7531 (0x1d6b)
  usb.interface.number = 0 (0x0)

  97: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_1'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'usb'
  info.subsystem = 'usb_device'
  info.product = '1.1 root hub'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_1'
  usb_device.configuration_value = 1 (0x1)
  usb_device.num_configurations = 1 (0x1)
  usb_device.device_class = 9 (0x9)
  usb_device.device_subclass = 0 (0x0)
  usb_device.num_interfaces = 1 (0x1)
  usb_device.device_protocol = 0 (0x0)
  usb_device.product_id = 1 (0x1)
  usb_device.vendor = 'Linux Foundation'
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4'
  usb_device.device_revision_bcd = 518 (0x206)
  usb_device.max_power = 0 (0x0)
  usb_device.num_ports = 3 (0x3)
  usb_device.linux.device_number = 1 (0x1)
  usb_device.serial = '0000:00:12.1'
  usb_device.speed = 12.0000
  usb_device.version = 1.10000
  usb_device.is_self_powered = true
  usb_device.can_wake_up = true
  usb_device.bus_number = 4 (0x4)
  linux.device_file = '/dev/bus/usb/004/001'
  usb_device.vendor_id = 7531 (0x1d6b)
  usb_device.product = '1.1 root hub'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4'
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4398'
  info.vendor = 'Linux Foundation'

  98: udi = '/org/freedesktop/Hal/devices/pci_1002_4398'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4398'
  info.subsystem = 'pci'
  info.linux.driver = 'ohci_hcd'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1'
  pci.product_id = 17304 (0x4398)
  pci.vendor_id = 4098 (0x1002)
  pci.subsys_product_id = 33673 (0x8389)
  pci.subsys_vendor_id = 4163 (0x1043)
  pci.device_class = 12 (0xc)
  pci.device_subclass = 3 (0x3)
  pci.device_protocol = 16 (0x10)
  pci.vendor = 'ATI Technologies Inc'
  info.vendor = 'ATI Technologies Inc'
  pci.product = 'SB700 USB OHCI1 Controller'
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.product = 'SB700 USB OHCI1 Controller'

  99: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_0_if0'
  linux.hotplug_type = 2 (0x2)
  usb.interface.subclass = 0 (0x0)
  usb.interface.protocol = 0 (0x0)
  usb.interface.class = 9 (0x9)
  linux.subsystem = 'usb'
  info.linux.driver = 'hub'
  info.subsystem = 'usb'
  info.product = 'USB Hub Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_0_if0'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.device_class = 9 (0x9)
  usb.device_subclass = 0 (0x0)
  usb.num_interfaces = 1 (0x1)
  usb.device_protocol = 0 (0x0)
  usb.product_id = 1 (0x1)
  usb.vendor = 'Linux Foundation'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.0/usb3/3-0:1.0'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.0/usb3/3-0:1.0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_0'
  usb.max_power = 0 (0x0)
  usb.device_revision_bcd = 518 (0x206)
  usb.linux.device_number = 1 (0x1)
  usb.num_ports = 3 (0x3)
  usb.speed = 12.0000
  usb.serial = '0000:00:12.0'
  usb.is_self_powered = true
  usb.version = 1.10000
  usb.bus_number = 3 (0x3)
  usb.can_wake_up = true
  usb.product = 'USB Hub Interface'
  usb.vendor_id = 7531 (0x1d6b)
  usb.interface.number = 0 (0x0)

  100: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'usb'
  info.subsystem = 'usb_device'
  info.product = '1.1 root hub'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_0'
  usb_device.configuration_value = 1 (0x1)
  usb_device.num_configurations = 1 (0x1)
  usb_device.device_class = 9 (0x9)
  usb_device.device_subclass = 0 (0x0)
  usb_device.num_interfaces = 1 (0x1)
  usb_device.device_protocol = 0 (0x0)
  usb_device.product_id = 1 (0x1)
  usb_device.vendor = 'Linux Foundation'
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.0/usb3'
  usb_device.device_revision_bcd = 518 (0x206)
  usb_device.max_power = 0 (0x0)
  usb_device.num_ports = 3 (0x3)
  usb_device.linux.device_number = 1 (0x1)
  usb_device.serial = '0000:00:12.0'
  usb_device.speed = 12.0000
  usb_device.version = 1.10000
  usb_device.is_self_powered = true
  usb_device.can_wake_up = true
  usb_device.bus_number = 3 (0x3)
  linux.device_file = '/dev/bus/usb/003/001'
  usb_device.vendor_id = 7531 (0x1d6b)
  usb_device.product = '1.1 root hub'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.0/usb3'
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4397'
  info.vendor = 'Linux Foundation'

  101: udi = '/org/freedesktop/Hal/devices/pci_1002_4397'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4397'
  info.subsystem = 'pci'
  info.linux.driver = 'ohci_hcd'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.0'
  pci.product_id = 17303 (0x4397)
  pci.vendor_id = 4098 (0x1002)
  pci.subsys_product_id = 33673 (0x8389)
  pci.subsys_vendor_id = 4163 (0x1043)
  pci.device_class = 12 (0xc)
  pci.device_subclass = 3 (0x3)
  pci.device_protocol = 16 (0x10)
  pci.vendor = 'ATI Technologies Inc'
  info.vendor = 'ATI Technologies Inc'
  pci.product = 'SB700/SB800 USB OHCI0 Controller'
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.product = 'SB700/SB800 USB OHCI0 Controller'

  102: udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_scsi_device_lun0'
  info.linux.driver = 'sd'
  scsi.host = 0 (0x0)
  scsi.bus = 0 (0x0)
  scsi.target = 0 (0x0)
  scsi.lun = 0 (0x0)
  scsi.model = 'WDC WD3200AAKS-0'
  scsi.vendor = 'ATA'
  scsi.type = 'disk'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host0/target0:0:0/0:0:0:0'
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host'
  info.product = 'SCSI Device'
  info.subsystem = 'scsi'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_scsi_device_lun0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi'

  103: udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host'
  info.capabilities = { 'scsi_host' }
  scsi_host.host = 0 (0x0)
  info.category = 'scsi_host'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host0'
  info.product = 'SCSI Host Adapter'
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4390'
  info.subsystem = 'scsi_host'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi_host'

  104: udi = '/org/freedesktop/Hal/devices/pci_1002_4390'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4390'
  info.subsystem = 'pci'
  info.linux.driver = 'ahci'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0'
  pci.product_id = 17296 (0x4390)
  pci.vendor_id = 4098 (0x1002)
  pci.subsys_product_id = 33673 (0x8389)
  pci.subsys_vendor_id = 4163 (0x1043)
  pci.device_class = 1 (0x1)
  pci.device_subclass = 6 (0x6)
  pci.device_protocol = 1 (0x1)
  pci.vendor = 'ATI Technologies Inc'
  info.vendor = 'ATI Technologies Inc'
  pci.product = 'SB700/SB800 SATA Controller [IDE mode]'
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.product = 'SB700/SB800 SATA Controller [IDE mode]'

  105: udi = '/org/freedesktop/Hal/devices/pci_10ec_8168'
  info.udi = '/org/freedesktop/Hal/devices/pci_10ec_8168'
  info.subsystem = 'pci'
  info.linux.driver = 'r8169'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:06.0/0000:02:00.0'
  info.parent = '/org/freedesktop/Hal/devices/pci_1022_9606'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:06.0/0000:02:00.0'
  pci.product_id = 33128 (0x8168)
  pci.vendor_id = 4332 (0x10ec)
  pci.subsys_product_id = 33639 (0x8367)
  pci.subsys_vendor_id = 4163 (0x1043)
  pci.device_class = 2 (0x2)
  pci.device_subclass = 0 (0x0)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Realtek Semiconductor Co., Ltd.'
  info.vendor = 'Realtek Semiconductor Co., Ltd.'
  pci.product = 'RTL8111/8168B PCI Express Gigabit Ethernet controller'
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.product = 'RTL8111/8168B PCI Express Gigabit Ethernet controller'

  106: udi = '/org/freedesktop/Hal/devices/pci_1022_9606'
  info.udi = '/org/freedesktop/Hal/devices/pci_1022_9606'
  info.subsystem = 'pci'
  info.linux.driver = 'pcieport-driver'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:06.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:06.0'
  pci.product_id = 38406 (0x9606)
  pci.vendor_id = 4130 (0x1022)
  pci.subsys_product_id = 0 (0x0)
  pci.subsys_vendor_id = 0 (0x0)
  pci.device_class = 6 (0x6)
  pci.device_subclass = 4 (0x4)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Advanced Micro Devices [AMD]'
  info.vendor = 'Advanced Micro Devices [AMD]'
  pci.product = 'RS780 PCI to PCI bridge (PCIE port 2)'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.product = 'RS780 PCI to PCI bridge (PCIE port 2)'

  107: udi = '/org/freedesktop/Hal/devices/pci_1002_9616'
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_9616'
  info.subsystem = 'pci'
  info.linux.driver = 'fglrx_pci'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0/0000:01:05.0'
  info.parent = '/org/freedesktop/Hal/devices/pci_1043_9602'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0/0000:01:05.0'
  pci.product_id = 38422 (0x9616)
  pci.vendor_id = 4098 (0x1002)
  pci.subsys_product_id = 33672 (0x8388)
  pci.subsys_vendor_id = 4163 (0x1043)
  pci.device_class = 3 (0x3)
  pci.device_subclass = 0 (0x0)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'ATI Technologies Inc'
  info.vendor = 'ATI Technologies Inc'
  pci.product = '760G [Radeon 3000]'
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.product = '760G [Radeon 3000]'

  108: udi = '/org/freedesktop/Hal/devices/pci_1043_9602'
  info.subsystem = 'pci'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0'
  pci.product_id = 38402 (0x9602)
  pci.vendor_id = 4163 (0x1043)
  pci.subsys_product_id = 0 (0x0)
  pci.subsys_vendor_id = 0 (0x0)
  pci.device_class = 6 (0x6)
  pci.device_subclass = 4 (0x4)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'ASUSTeK Computer Inc.'
  info.vendor = 'ASUSTeK Computer Inc.'
  info.udi = '/org/freedesktop/Hal/devices/pci_1043_9602'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.product = 'Unknown (0x9602)'

  109: udi = '/org/freedesktop/Hal/devices/pci_1022_9600'
  info.udi = '/org/freedesktop/Hal/devices/pci_1022_9600'
  info.subsystem = 'pci'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:00.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:00.0'
  pci.product_id = 38400 (0x9600)
  pci.vendor_id = 4130 (0x1022)
  pci.subsys_product_id = 33672 (0x8388)
  pci.subsys_vendor_id = 4163 (0x1043)
  pci.device_class = 6 (0x6)
  pci.device_subclass = 0 (0x0)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Advanced Micro Devices [AMD]'
  info.vendor = 'Advanced Micro Devices [AMD]'
  pci.product = 'RS780 Host Bridge'
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.product = 'RS780 Host Bridge'
----- hal device list end -----
>> floppy.1: get nvram
>> floppy.2: klog info
>> bios.1: cmdline
>> bios.1.1: apm
>> bios.2: ram
/dev/mem[0x400, 256]: mmap(, 4096,,,, 0x0) ok
/dev/mem[0xc0000, 262144]: mmap(, 262144,,,, 0xc0000) ok
  bios: 1 disks
  bios: 635k low mem
/dev/mem[0x9ec00, 1]: mmap(, 4096,,,, 0x9e000) ok
/dev/mem[0x9ec00, 1024]: mmap(, 4096,,,, 0x9e000) ok
  bios: EBDA 0x00400 bytes at 0x9ec00
>> bios.2: rom
----- SMBIOS Entry Point 0xfbb50 - 0xfbb6e -----
  fbb50  5f 53 4d 5f c3 1f 02 05 b9 00 00 00 00 00 00 00  "_SM_............"
  fbb60  5f 44 4d 49 5f 00 23 09 00 f0 09 00 43 00 00  "_DMI_.#.....C.."
----- SMBIOS Entry Point end -----
/dev/mem[0x9f000, 2339]: mmap(, 4096,,,, 0x9f000) ok
----- SMBIOS Structure Table 0x9f000 - 0x9f922 -----
  9f000  00 18 00 00 01 02 00 f0 03 0f 90 de 8b 7f 01 00  "................"
  9f010  00 00 33 05 08 0e ff ff 41 6d 65 72 69 63 61 6e  "..3.....American"
  9f020  20 4d 65 67 61 74 72 65 6e 64 73 20 49 6e 63 2e  " Megatrends Inc."
  9f030  00 30 38 30 31 20 20 20 00 30 36 2f 30 32 2f 32  ".0801   .06/02/2"
  9f040  30 30 39 00 00 01 1b 01 00 01 02 03 04 00 b1 e4  "009............."
  9f050  05 8e fe d5 11 b2 34 00 26 18 b8 da 07 06 05 06  "......4.&......."
  9f060  53 79 73 74 65 6d 20 6d 61 6e 75 66 61 63 74 75  "System manufactu"
  9f070  72 65 72 00 53 79 73 74 65 6d 20 50 72 6f 64 75  "rer.System Produ"
  9f080  63 74 20 4e 61 6d 65 00 53 79 73 74 65 6d 20 56  "ct Name.System V"
  9f090  65 72 73 69 6f 6e 00 53 79 73 74 65 6d 20 53 65  "ersion.System Se"
  9f0a0  72 69 61 6c 20 4e 75 6d 62 65 72 00 54 6f 20 42  "rial Number.To B"
  9f0b0  65 20 46 69 6c 6c 65 64 20 42 79 20 4f 2e 45 2e  "e Filled By O.E."
  9f0c0  4d 2e 00 54 6f 20 42 65 20 46 69 6c 6c 65 64 20  "M..To Be Filled "
  9f0d0  42 79 20 4f 2e 45 2e 4d 2e 00 00 02 0f 02 00 01  "By O.E.M........"
  9f0e0  02 03 04 05 09 06 03 00 0a 00 41 53 55 53 54 65  "..........ASUSTe"
  9f0f0  4b 20 43 6f 6d 70 75 74 65 72 20 49 4e 43 2e 00  "K Computer INC.."
  9f100  4d 33 41 37 36 2d 43 4d 00 52 65 76 20 58 2e 30  "M3A76-CM.Rev X.0"
  9f110  78 00 4d 46 37 30 39 37 47 30 30 34 30 31 33 35  "x.MF7097G0040135"
  9f120  35 00 54 6f 20 42 65 20 46 69 6c 6c 65 64 20 42  "5.To Be Filled B"
  9f130  79 20 4f 2e 45 2e 4d 2e 00 54 6f 20 42 65 20 46  "y O.E.M..To Be F"
  9f140  69 6c 6c 65 64 20 42 79 20 4f 2e 45 2e 4d 2e 00  "illed By O.E.M.."
  9f150  00 03 15 03 00 01 03 02 03 04 03 03 03 03 01 00  "................"
  9f160  00 00 00 01 00 00 43 68 61 73 73 69 73 20 4d 61  "......Chassis Ma"
  9f170  6e 75 66 61 63 74 75 72 65 00 43 68 61 73 73 69  "nufacture.Chassi"
  9f180  73 20 56 65 72 73 69 6f 6e 00 43 68 61 73 73 69  "s Version.Chassi"
  9f190  73 20 53 65 72 69 61 6c 20 4e 75 6d 62 65 72 00  "s Serial Number."
  9f1a0  41 73 73 65 74 2d 31 32 33 34 35 36 37 38 39 30  "Asset-1234567890"
  9f1b0  00 00 04 28 04 00 01 03 ed 02 52 0f 10 00 ff fb  "...(......R....."
  9f1c0  8b 17 03 8f c8 00 80 0c 28 0a 41 01 05 00 06 00  "........(.A....."
  9f1d0  07 00 04 05 06 04 04 00 04 00 41 4d 32 00 41 4d  "..........AM2.AM"
  9f1e0  44 20 20 20 20 20 20 20 20 20 20 20 20 20 20 00  "D              ."
  9f1f0  41 4d 44 20 41 74 68 6c 6f 6e 28 74 6d 29 20 49  "AMD Athlon(tm) I"
  9f200  49 20 58 34 20 36 32 30 20 50 72 6f 63 65 73 73  "I X4 620 Process"
  9f210  6f 72 20 20 20 20 20 20 20 20 20 20 20 20 20 20  "or              "
  9f220  20 20 20 20 00 54 6f 20 42 65 20 46 69 6c 6c 65  "    .To Be Fille"
  9f230  64 20 42 79 20 4f 2e 45 2e 4d 2e 00 54 6f 20 42  "d By O.E.M..To B"
  9f240  65 20 46 69 6c 6c 65 64 20 42 79 20 4f 2e 45 2e  "e Filled By O.E."
  9f250  4d 2e 00 54 6f 20 42 65 20 46 69 6c 6c 65 64 20  "M..To Be Filled "
  9f260  42 79 20 4f 2e 45 2e 4d 2e 00 00 07 13 05 00 01  "By O.E.M........"
  9f270  80 02 00 02 00 02 10 00 10 00 00 05 04 05 4c 31  "..............L1"
  9f280  2d 43 61 63 68 65 00 00 07 13 06 00 01 81 02 00  "-Cache.........."
  9f290  08 00 08 10 00 10 00 00 05 05 05 4c 32 2d 43 61  "...........L2-Ca"
  9f2a0  63 68 65 00 00 07 13 07 00 01 02 03 00 00 00 00  "che............."
  9f2b0  02 00 02 00 00 02 02 02 4c 33 2d 43 61 63 68 65  "........L3-Cache"
  9f2c0  00 00 08 09 08 00 01 00 02 0f 0d 50 53 2f 32 20  "...........PS/2 "
  9f2d0  4b 42 2f 4d 53 00 50 53 2f 32 20 4b 42 2f 4d 53  "KB/MS.PS/2 KB/MS"
  9f2e0  00 00 08 09 09 00 01 00 02 12 10 55 53 42 31 00  "...........USB1."
  9f2f0  55 53 42 31 00 00 08 09 0a 00 01 00 02 12 10 55  "USB1...........U"
  9f300  53 42 32 00 55 53 42 32 00 00 08 09 0b 00 01 00  "SB2.USB2........"
  9f310  02 12 10 55 53 42 33 00 55 53 42 33 00 00 08 09  "...USB3.USB3...."
  9f320  0c 00 01 00 02 12 10 55 53 42 34 00 55 53 42 34  ".......USB4.USB4"
  9f330  00 00 08 09 0d 00 01 00 02 12 10 55 53 42 35 00  "...........USB5."
  9f340  55 53 42 35 00 00 08 09 0e 00 01 00 02 12 10 55  "USB5...........U"
  9f350  53 42 36 00 55 53 42 36 00 00 08 09 0f 00 01 00  "SB6.USB6........"
  9f360  02 04 05 4c 50 54 20 31 00 4c 50 54 20 31 00 00  "...LPT 1.LPT 1.."
  9f370  08 09 10 00 01 00 02 08 09 43 4f 4d 20 31 00 43  ".........COM 1.C"
  9f380  4f 4d 20 31 00 00 08 09 11 00 01 00 02 0b 1f 4c  "OM 1...........L"
  9f390  41 4e 00 4c 41 4e 00 00 08 09 12 00 01 00 02 1f  "AN.LAN.........."
  9f3a0  1d 41 75 64 69 6f 5f 4c 69 6e 65 5f 49 6e 00 41  ".Audio_Line_In.A"
  9f3b0  75 64 69 6f 5f 4c 69 6e 65 5f 49 6e 00 00 08 09  "udio_Line_In...."
  9f3c0  13 00 01 00 02 1f 1d 41 75 64 69 6f 5f 4c 69 6e  ".......Audio_Lin"
  9f3d0  65 5f 4f 75 74 00 41 75 64 69 6f 5f 4c 69 6e 65  "e_Out.Audio_Line"
  9f3e0  5f 4f 75 74 00 00 08 09 14 00 01 00 02 1f 1d 41  "_Out...........A"
  9f3f0  75 64 69 6f 5f 4d 69 63 5f 49 6e 00 41 75 64 69  "udio_Mic_In.Audi"
  9f400  6f 5f 4d 69 63 5f 49 6e 00 00 08 09 15 00 01 00  "o_Mic_In........"
  9f410  02 1f 1d 41 75 64 69 6f 5f 43 65 6e 74 65 72 2f  "...Audio_Center/"
  9f420  53 75 62 00 41 75 64 69 6f 5f 43 65 6e 74 65 72  "Sub.Audio_Center"
  9f430  2f 53 75 62 00 00 08 09 16 00 01 00 02 1f 1d 41  "/Sub...........A"
  9f440  75 64 69 6f 5f 52 65 61 72 00 41 75 64 69 6f 5f  "udio_Rear.Audio_"
  9f450  52 65 61 72 00 00 08 09 17 00 01 00 02 1f 1d 41  "Rear...........A"
  9f460  75 64 69 6f 5f 53 69 64 65 00 41 75 64 69 6f 5f  "udio_Side.Audio_"
  9f470  53 69 64 65 00 00 08 09 18 00 01 00 02 ff ff 44  "Side...........D"
  9f480  56 49 00 44 56 49 20 70 6f 72 74 00 00 08 09 19  "VI.DVI port....."
  9f490  00 01 16 00 00 ff 50 52 49 20 49 44 45 00 00 08  "......PRI IDE..."
  9f4a0  09 1a 00 01 ff 00 00 ff 53 42 5f 53 41 54 41 31  "........SB_SATA1"
  9f4b0  00 00 08 09 1b 00 01 ff 00 00 ff 53 42 5f 53 41  "...........SB_SA"
  9f4c0  54 41 32 00 00 08 09 1c 00 01 ff 00 00 ff 53 42  "TA2...........SB"
  9f4d0  5f 53 41 54 41 33 00 00 08 09 1d 00 01 ff 00 00  "_SATA3.........."
  9f4e0  ff 53 42 5f 53 41 54 41 34 00 00 08 09 1e 00 01  ".SB_SATA4......."
  9f4f0  ff 00 00 ff 53 42 5f 53 41 54 41 35 00 00 08 09  "....SB_SATA5...."
  9f500  1f 00 01 ff 00 00 ff 53 42 5f 53 41 54 41 36 00  ".......SB_SATA6."
  9f510  00 08 09 20 00 01 ff 00 00 ff 43 50 55 20 46 41  "... ......CPU FA"
  9f520  4e 00 00 08 09 21 00 01 ff 00 00 ff 43 48 41 20  "N....!......CHA "
  9f530  46 41 4e 00 00 08 09 22 00 01 12 00 00 10 55 53  "FAN...."......US"
  9f540  42 37 00 00 08 09 23 00 01 12 00 00 10 55 53 42  "B7....#......USB"
  9f550  38 00 00 08 09 24 00 01 12 00 00 10 55 53 42 39  "8....$......USB9"
  9f560  00 00 08 09 25 00 01 12 00 00 10 55 53 42 31 30  "....%......USB10"
  9f570  00 00 08 09 26 00 01 12 00 00 10 55 53 42 31 31  "....&......USB11"
  9f580  00 00 08 09 27 00 01 12 00 00 10 55 53 42 31 32  "....'......USB12"
  9f590  00 00 08 09 28 00 01 ff 00 00 ff 50 41 4e 45 4c  "....(......PANEL"
  9f5a0  00 00 08 09 29 00 01 ff 00 00 ff 53 50 44 49 46  "....)......SPDIF"
  9f5b0  20 4f 55 54 00 00 08 09 2a 00 01 ff 00 00 ff 41  " OUT....*......A"
  9f5c0  41 46 50 00 00 08 09 2b 00 01 1c 00 00 1d 43 44  "AFP....+......CD"
  9f5d0  00 00 09 0d 2c 00 01 a5 05 04 03 04 00 0c 01 50  "....,..........P"
  9f5e0  43 49 45 31 58 00 00 09 0d 2d 00 01 a5 05 03 03  "CIE1X....-......"
  9f5f0  02 00 0c 01 50 43 49 45 31 36 58 00 00 09 0d 2e  "....PCIE16X....."
  9f600  00 01 06 05 03 03 03 00 0c 01 50 43 49 31 00 00  "..........PCI1.."
  9f610  09 0d 2f 00 01 06 05 03 03 01 00 0c 01 50 43 49  "../..........PCI"
  9f620  32 00 00 0a 06 30 00 81 01 20 20 54 6f 20 42 65  "2....0...  To Be"
  9f630  20 46 69 6c 6c 65 64 20 42 79 20 4f 2e 45 2e 4d  " Filled By O.E.M"
  9f640  2e 00 00 0a 06 31 00 85 01 54 6f 20 42 65 20 46  ".....1...To Be F"
  9f650  69 6c 6c 65 64 20 42 79 20 4f 2e 45 2e 4d 2e 00  "illed By O.E.M.."
  9f660  00 0a 06 32 00 87 01 54 6f 20 42 65 20 46 69 6c  "...2...To Be Fil"
  9f670  6c 65 64 20 42 79 20 4f 2e 45 2e 4d 2e 00 00 0a  "led By O.E.M...."
  9f680  06 33 00 81 01 54 6f 20 42 65 20 46 69 6c 6c 65  ".3...To Be Fille"
  9f690  64 20 42 79 20 4f 2e 45 2e 4d 2e 00 00 0b 05 34  "d By O.E.M.....4"
  9f6a0  00 04 30 30 32 36 31 38 42 38 44 41 30 37 00 54  "..002618B8DA07.T"
  9f6b0  6f 20 42 65 20 46 69 6c 6c 65 64 20 42 79 20 4f  "o Be Filled By O"
  9f6c0  2e 45 2e 4d 2e 00 54 6f 20 42 65 20 46 69 6c 6c  ".E.M..To Be Fill"
  9f6d0  65 64 20 42 79 20 4f 2e 45 2e 4d 2e 00 54 6f 20  "ed By O.E.M..To "
  9f6e0  42 65 20 46 69 6c 6c 65 64 20 42 79 20 4f 2e 45  "Be Filled By O.E"
  9f6f0  2e 4d 2e 00 00 0d 16 35 00 01 ff 00 00 00 00 00  ".M.....5........"
  9f700  00 00 00 00 00 00 00 00 00 00 01 65 6e 7c 55 53  "...........en|US"
  9f710  7c 69 73 6f 38 38 35 39 2d 31 00 00 0f 23 36 00  "|iso8859-1...#6."
  9f720  04 00 00 00 02 00 02 00 00 00 00 00 6a 04 6c 04  "............j.l."
  9f730  00 06 02 ff ff ff ff ff ff ff ff ff ff ff ff 00  "................"
  9f740  00 10 0f 37 00 03 03 03 00 00 80 00 fe ff 04 00  "...7............"
  9f750  00 00 13 0f 38 00 00 00 00 00 ff ff 33 00 37 00  "....8.......3.7."
  9f760  01 00 00 11 1b 39 00 37 00 fe ff 40 00 40 00 00  ".....9.7...@.@.."
  9f770  08 09 00 01 02 13 80 00 20 03 03 04 05 06 44 49  "........ .....DI"
  9f780  4d 4d 30 00 42 41 4e 4b 30 00 4d 61 6e 75 66 61  "MM0.BANK0.Manufa"
  9f790  63 74 75 72 65 72 30 00 53 65 72 4e 75 6d 30 00  "cturer0.SerNum0."
  9f7a0  41 73 73 65 74 54 61 67 4e 75 6d 30 00 50 61 72  "AssetTagNum0.Par"
  9f7b0  74 4e 75 6d 30 00 00 14 13 3a 00 00 00 00 00 ff  "tNum0....:......"
  9f7c0  ff 1f 00 39 00 38 00 01 00 00 00 00 11 1b 3b 00  "...9.8........;."
  9f7d0  37 00 fe ff 40 00 40 00 00 08 09 00 01 02 13 80  "7...@.@........."
  9f7e0  00 20 03 03 04 05 06 44 49 4d 4d 31 00 42 41 4e  ". .....DIMM1.BAN"
  9f7f0  4b 31 00 4d 61 6e 75 66 61 63 74 75 72 65 72 31  "K1.Manufacturer1"
  9f800  00 53 65 72 4e 75 6d 31 00 41 73 73 65 74 54 61  ".SerNum1.AssetTa"
  9f810  67 4e 75 6d 31 00 50 61 72 74 4e 75 6d 31 00 00  "gNum1.PartNum1.."
  9f820  14 13 3c 00 00 00 20 00 ff ff 3f 00 3b 00 38 00  "..<... ...?.;.8."
  9f830  01 00 00 00 00 11 1b 3d 00 37 00 fe ff ff ff ff  ".......=.7......"
  9f840  ff 00 00 09 00 01 02 02 00 00 00 00 03 04 05 06  "................"
  9f850  44 49 4d 4d 32 00 42 41 4e 4b 32 00 4d 61 6e 75  "DIMM2.BANK2.Manu"
  9f860  66 61 63 74 75 72 65 72 32 00 53 65 72 4e 75 6d  "facturer2.SerNum"
  9f870  32 00 41 73 73 65 74 54 61 67 4e 75 6d 32 00 50  "2.AssetTagNum2.P"
  9f880  61 72 74 4e 75 6d 32 00 00 7e 13 3e 00 00 00 00  "artNum2..~.>...."
  9f890  00 00 00 00 00 3d 00 38 00 01 00 00 00 00 11 1b  ".....=.8........"
  9f8a0  3f 00 37 00 fe ff ff ff ff ff 00 00 09 00 01 02  "?.7............."
  9f8b0  02 00 00 00 00 03 04 05 06 44 49 4d 4d 33 00 42  ".........DIMM3.B"
  9f8c0  41 4e 4b 33 00 4d 61 6e 75 66 61 63 74 75 72 65  "ANK3.Manufacture"
  9f8d0  72 33 00 53 65 72 4e 75 6d 33 00 41 73 73 65 74  "r3.SerNum3.Asset"
  9f8e0  54 61 67 4e 75 6d 33 00 50 61 72 74 4e 75 6d 33  "TagNum3.PartNum3"
  9f8f0  00 00 7e 13 40 00 00 00 00 00 00 00 00 00 3f 00  "..~.@.........?."
  9f900  38 00 01 00 00 00 00 20 14 41 00 00 00 00 00 00  "8...... .A......"
  9f910  00 00 00 00 00 00 00 00 00 00 00 00 00 7f 04 42  "...............B"
  9f920  00 00 00  "..."
----- SMBIOS Structure Table end -----
  type 0x00 [0x0000]: 00 18 00 00 01 02 00 f0 03 0f 90 de 8b 7f 01 00 00 00 33 05 08 0e ff ff
       str1: "American Megatrends Inc."
       str2: "0801"
       str3: "06/02/2009"
  type 0x01 [0x0001]: 01 1b 01 00 01 02 03 04 00 b1 e4 05 8e fe d5 11 b2 34 00 26 18 b8 da 07 06 05 06
       str1: "System manufacturer"
       str2: "System Product Name"
       str3: "System Version"
       str4: "System Serial Number"
       str5: "To Be Filled By O.E.M."
       str6: "To Be Filled By O.E.M."
  type 0x02 [0x0002]: 02 0f 02 00 01 02 03 04 05 09 06 03 00 0a 00
       str1: "ASUSTeK Computer INC."
       str2: "M3A76-CM"
       str3: "Rev X.0x"
       str4: "MF7097G00401355"
       str5: "To Be Filled By O.E.M."
       str6: "To Be Filled By O.E.M."
  type 0x03 [0x0003]: 03 15 03 00 01 03 02 03 04 03 03 03 03 01 00 00 00 00 01 00 00
       str1: "Chassis Manufacture"
       str2: "Chassis Version"
       str3: "Chassis Serial Number"
       str4: "Asset-1234567890"
  type 0x04 [0x0004]: 04 28 04 00 01 03 ed 02 52 0f 10 00 ff fb 8b 17 03 8f c8 00 80 0c 28 0a 41 01 05 00 06 00 07 00 04 05 06 04 04 00 04 00
       str1: "AM2"
       str2: "AMD"
       str3: "AMD Athlon(tm) II X4 620 Processor"
       str4: "To Be Filled By O.E.M."
       str5: "To Be Filled By O.E.M."
       str6: "To Be Filled By O.E.M."
  type 0x07 [0x0005]: 07 13 05 00 01 80 02 00 02 00 02 10 00 10 00 00 05 04 05
       str1: "L1-Cache"
  type 0x07 [0x0006]: 07 13 06 00 01 81 02 00 08 00 08 10 00 10 00 00 05 05 05
       str1: "L2-Cache"
  type 0x07 [0x0007]: 07 13 07 00 01 02 03 00 00 00 00 02 00 02 00 00 02 02 02
       str1: "L3-Cache"
  type 0x08 [0x0008]: 08 09 08 00 01 00 02 0f 0d
       str1: "PS/2 KB/MS"
       str2: "PS/2 KB/MS"
  type 0x08 [0x0009]: 08 09 09 00 01 00 02 12 10
       str1: "USB1"
       str2: "USB1"
  type 0x08 [0x000a]: 08 09 0a 00 01 00 02 12 10
       str1: "USB2"
       str2: "USB2"
  type 0x08 [0x000b]: 08 09 0b 00 01 00 02 12 10
       str1: "USB3"
       str2: "USB3"
  type 0x08 [0x000c]: 08 09 0c 00 01 00 02 12 10
       str1: "USB4"
       str2: "USB4"
  type 0x08 [0x000d]: 08 09 0d 00 01 00 02 12 10
       str1: "USB5"
       str2: "USB5"
  type 0x08 [0x000e]: 08 09 0e 00 01 00 02 12 10
       str1: "USB6"
       str2: "USB6"
  type 0x08 [0x000f]: 08 09 0f 00 01 00 02 04 05
       str1: "LPT 1"
       str2: "LPT 1"
  type 0x08 [0x0010]: 08 09 10 00 01 00 02 08 09
       str1: "COM 1"
       str2: "COM 1"
  type 0x08 [0x0011]: 08 09 11 00 01 00 02 0b 1f
       str1: "LAN"
       str2: "LAN"
  type 0x08 [0x0012]: 08 09 12 00 01 00 02 1f 1d
       str1: "Audio_Line_In"
       str2: "Audio_Line_In"
  type 0x08 [0x0013]: 08 09 13 00 01 00 02 1f 1d
       str1: "Audio_Line_Out"
       str2: "Audio_Line_Out"
  type 0x08 [0x0014]: 08 09 14 00 01 00 02 1f 1d
       str1: "Audio_Mic_In"
       str2: "Audio_Mic_In"
  type 0x08 [0x0015]: 08 09 15 00 01 00 02 1f 1d
       str1: "Audio_Center/Sub"
       str2: "Audio_Center/Sub"
  type 0x08 [0x0016]: 08 09 16 00 01 00 02 1f 1d
       str1: "Audio_Rear"
       str2: "Audio_Rear"
  type 0x08 [0x0017]: 08 09 17 00 01 00 02 1f 1d
       str1: "Audio_Side"
       str2: "Audio_Side"
  type 0x08 [0x0018]: 08 09 18 00 01 00 02 ff ff
       str1: "DVI"
       str2: "DVI port"
  type 0x08 [0x0019]: 08 09 19 00 01 16 00 00 ff
       str1: "PRI IDE"
  type 0x08 [0x001a]: 08 09 1a 00 01 ff 00 00 ff
       str1: "SB_SATA1"
  type 0x08 [0x001b]: 08 09 1b 00 01 ff 00 00 ff
       str1: "SB_SATA2"
  type 0x08 [0x001c]: 08 09 1c 00 01 ff 00 00 ff
       str1: "SB_SATA3"
  type 0x08 [0x001d]: 08 09 1d 00 01 ff 00 00 ff
       str1: "SB_SATA4"
  type 0x08 [0x001e]: 08 09 1e 00 01 ff 00 00 ff
       str1: "SB_SATA5"
  type 0x08 [0x001f]: 08 09 1f 00 01 ff 00 00 ff
       str1: "SB_SATA6"
  type 0x08 [0x0020]: 08 09 20 00 01 ff 00 00 ff
       str1: "CPU FAN"
  type 0x08 [0x0021]: 08 09 21 00 01 ff 00 00 ff
       str1: "CHA FAN"
  type 0x08 [0x0022]: 08 09 22 00 01 12 00 00 10
       str1: "USB7"
  type 0x08 [0x0023]: 08 09 23 00 01 12 00 00 10
       str1: "USB8"
  type 0x08 [0x0024]: 08 09 24 00 01 12 00 00 10
       str1: "USB9"
  type 0x08 [0x0025]: 08 09 25 00 01 12 00 00 10
       str1: "USB10"
  type 0x08 [0x0026]: 08 09 26 00 01 12 00 00 10
       str1: "USB11"
  type 0x08 [0x0027]: 08 09 27 00 01 12 00 00 10
       str1: "USB12"
  type 0x08 [0x0028]: 08 09 28 00 01 ff 00 00 ff
       str1: "PANEL"
  type 0x08 [0x0029]: 08 09 29 00 01 ff 00 00 ff
       str1: "SPDIF OUT"
  type 0x08 [0x002a]: 08 09 2a 00 01 ff 00 00 ff
       str1: "AAFP"
  type 0x08 [0x002b]: 08 09 2b 00 01 1c 00 00 1d
       str1: "CD"
  type 0x09 [0x002c]: 09 0d 2c 00 01 a5 05 04 03 04 00 0c 01
       str1: "PCIE1X"
  type 0x09 [0x002d]: 09 0d 2d 00 01 a5 05 03 03 02 00 0c 01
       str1: "PCIE16X"
  type 0x09 [0x002e]: 09 0d 2e 00 01 06 05 03 03 03 00 0c 01
       str1: "PCI1"
  type 0x09 [0x002f]: 09 0d 2f 00 01 06 05 03 03 01 00 0c 01
       str1: "PCI2"
  type 0x0a [0x0030]: 0a 06 30 00 81 01
       str1: "To Be Filled By O.E.M."
  type 0x0a [0x0031]: 0a 06 31 00 85 01
       str1: "To Be Filled By O.E.M."
  type 0x0a [0x0032]: 0a 06 32 00 87 01
       str1: "To Be Filled By O.E.M."
  type 0x0a [0x0033]: 0a 06 33 00 81 01
       str1: "To Be Filled By O.E.M."
  type 0x0b [0x0034]: 0b 05 34 00 04
       str1: "002618B8DA07"
       str2: "To Be Filled By O.E.M."
       str3: "To Be Filled By O.E.M."
       str4: "To Be Filled By O.E.M."
  type 0x0d [0x0035]: 0d 16 35 00 01 ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 01
       str1: "en|US|iso8859-1"
  type 0x0f [0x0036]: 0f 23 36 00 04 00 00 00 02 00 02 00 00 00 00 00 6a 04 6c 04 00 06 02 ff ff ff ff ff ff ff ff ff ff ff ff
  type 0x10 [0x0037]: 10 0f 37 00 03 03 03 00 00 80 00 fe ff 04 00
  type 0x13 [0x0038]: 13 0f 38 00 00 00 00 00 ff ff 33 00 37 00 01
  type 0x11 [0x0039]: 11 1b 39 00 37 00 fe ff 40 00 40 00 00 08 09 00 01 02 13 80 00 20 03 03 04 05 06
       str1: "DIMM0"
       str2: "BANK0"
       str3: "Manufacturer0"
       str4: "SerNum0"
       str5: "AssetTagNum0"
       str6: "PartNum0"
  type 0x14 [0x003a]: 14 13 3a 00 00 00 00 00 ff ff 1f 00 39 00 38 00 01 00 00
  type 0x11 [0x003b]: 11 1b 3b 00 37 00 fe ff 40 00 40 00 00 08 09 00 01 02 13 80 00 20 03 03 04 05 06
       str1: "DIMM1"
       str2: "BANK1"
       str3: "Manufacturer1"
       str4: "SerNum1"
       str5: "AssetTagNum1"
       str6: "PartNum1"
  type 0x14 [0x003c]: 14 13 3c 00 00 00 20 00 ff ff 3f 00 3b 00 38 00 01 00 00
  type 0x11 [0x003d]: 11 1b 3d 00 37 00 fe ff ff ff ff ff 00 00 09 00 01 02 02 00 00 00 00 03 04 05 06
       str1: "DIMM2"
       str2: "BANK2"
       str3: "Manufacturer2"
       str4: "SerNum2"
       str5: "AssetTagNum2"
       str6: "PartNum2"
  type 0x7e [0x003e]: 7e 13 3e 00 00 00 00 00 00 00 00 00 3d 00 38 00 01 00 00
  type 0x11 [0x003f]: 11 1b 3f 00 37 00 fe ff ff ff ff ff 00 00 09 00 01 02 02 00 00 00 00 03 04 05 06
       str1: "DIMM3"
       str2: "BANK3"
       str3: "Manufacturer3"
       str4: "SerNum3"
       str5: "AssetTagNum3"
       str6: "PartNum3"
  type 0x7e [0x0040]: 7e 13 40 00 00 00 00 00 00 00 00 00 3f 00 38 00 01 00 00
  type 0x20 [0x0041]: 20 14 41 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  type 0x7f [0x0042]: 7f 04 42 00
  smbios: stopped at end tag
>> bios.3: smp
  smp: valid MP FP at 0xff780 (size 0x10, rev 4), MP config at 0xf06a0
/dev/mem[0xf06a0, 64]: mmap(, 4096,,,, 0xf0000) ok
  MP config table size: 488
/dev/mem[0xf06a0, 488]: mmap(, 4096,,,, 0xf0000) ok
  base MP config table (34 entries):
  type 0, len 20
    00 00 10 03 52 0f 10 00 ff fb 8b 17 00 00 00 00 00 00 00 00  "....R..............."
  type 0, len 20
    00 01 10 01 52 0f 10 00 ff fb 8b 17 00 00 00 00 00 00 00 00  "....R..............."
  type 0, len 20
    00 02 10 01 52 0f 10 00 ff fb 8b 17 00 00 00 00 00 00 00 00  "....R..............."
  type 0, len 20
    00 03 10 01 52 0f 10 00 ff fb 8b 17 00 00 00 00 00 00 00 00  "....R..............."
  type 1, len 8
    01 00 50 43 49 20 20 20  "..PCI   "
  type 1, len 8
    01 01 50 43 49 20 20 20  "..PCI   "
  type 1, len 8
    01 02 50 43 49 20 20 20  "..PCI   "
  type 1, len 8
    01 03 50 43 49 20 20 20  "..PCI   "
  type 1, len 8
    01 04 49 53 41 20 20 20  "..ISA   "
  type 2, len 8
    02 04 21 01 00 00 c0 fe  "..!....."
  type 3, len 8
    03 03 00 00 04 00 04 00  "........"
  type 3, len 8
    03 00 00 00 04 01 04 01  "........"
  type 3, len 8
    03 00 00 00 04 00 04 02  "........"
  type 3, len 8
    03 00 00 00 04 03 04 03  "........"
  type 3, len 8
    03 00 00 00 04 05 04 05  "........"
  type 3, len 8
    03 00 00 00 04 06 04 06  "........"
  type 3, len 8
    03 00 05 00 04 08 04 08  "........"
  type 3, len 8
    03 00 00 00 04 09 04 09  "........"
  type 3, len 8
    03 00 00 00 04 0c 04 0c  "........"
  type 3, len 8
    03 00 00 00 04 0d 04 0d  "........"
  type 3, len 8
    03 00 00 00 04 0e 04 0e  "........"
  type 3, len 8
    03 00 00 00 04 0f 04 0f  "........"
  type 3, len 8
    03 00 0f 00 01 14 04 12  "........"
  type 3, len 8
    03 00 0f 00 00 18 04 12  "........"
  type 3, len 8
    03 00 0f 00 02 00 04 12  "........"
  type 3, len 8
    03 00 0f 00 00 50 04 10  ".....P.."
  type 3, len 8
    03 00 0f 00 00 52 04 12  ".....R.."
  type 3, len 8
    03 00 0f 00 00 48 04 10  ".....H.."
  type 3, len 8
    03 00 0f 00 00 49 04 11  ".....I.."
  type 3, len 8
    03 00 0f 00 00 4c 04 12  ".....L.."
  type 3, len 8
    03 00 0f 00 00 4d 04 13  ".....M.."
  type 3, len 8
    03 00 0f 00 00 44 04 16  ".....D.."
  type 4, len 8
    04 03 00 00 00 00 ff 00  "........"
  type 4, len 8
    04 01 00 00 00 00 ff 01  "........"
  extended MP config table:
  type 128, len 20
    80 14 00 00 00 80 00 00 00 00 00 00 00 70 00 00 00 00 00 00  ".............p......"
  type 128, len 20
    80 14 00 00 00 00 00 00 00 00 00 00 00 01 00 00 00 00 00 00  "...................."
  type 128, len 20
    80 14 00 01 00 00 0a 00 00 00 00 00 00 00 02 00 00 00 00 00  "...................."
  type 128, len 20
    80 14 00 01 00 00 00 fb 00 00 00 00 00 00 00 01 00 00 00 00  "...................."
  type 128, len 20
    80 14 00 02 00 00 00 d0 00 00 00 00 00 00 00 2b 00 00 00 00  "...............+...."
  type 129, len 8
    81 08 04 01 00 00 00 00  "........"
  type 130, len 8
    82 08 00 00 00 00 00 00  "........"
  type 130, len 8
    82 08 00 00 01 00 00 00  "........"
----- BIOS data 0x00400 - 0x004ff -----
  400  00 00 00 00 00 00 00 00 00 00 00 00 00 00 c0 9e  "................"
  410  26 00 20 7b 02 91 00 00 00 00 2a 00 2a 00 0d 1c  "&. {......*.*..."
  420  62 30 6f 18 6f 18 74 14 0d 1c e0 4b e0 4b e0 4b  "b0o.o.t....K.K.K"
  430  e0 4b e0 4b e0 4b e0 4d e0 4d 08 0e 2d 0c 80 00  ".K.K.K.M.M..-..."
  440  21 20 00 00 00 00 00 00 00 03 50 00 00 10 00 00  "! ........P....."
  450  00 12 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  460  00 20 00 d4 03 29 30 00 00 00 00 00 cd 65 09 00  ". ...)0......e.."
  470  00 00 00 00 00 01 08 00 14 14 14 14 01 01 01 01  "................"
  480  1e 00 3e 00 18 10 00 60 f9 11 0b 00 50 01 00 00  "..>....`....P..."
  490  00 00 00 00 00 00 10 a0 00 00 00 00 00 00 00 00  "................"
  4a0  00 00 00 00 00 00 00 00 62 66 00 c0 00 00 00 00  "........bf......"
  4b0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  4c0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  4d0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  4e0  04 c8 00 00 00 00 00 00 00 00 60 00 00 00 00 00  "..........`....."
  4f0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
----- BIOS data end -----
----- EBDA 0x9ec00 - 0x9efff -----
  9ec00  01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ec10  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ec20  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ec30  00 00 00 00 00 00 00 00 00 00 00 00 00 13 0f ff  "................"
  9ec40  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ec50  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ec60  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ec70  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ec80  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ec90  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9eca0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ecb0  00 00 00 92 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ecc0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ecd0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ece0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ecf0  00 00 00 00 00 00 00 00 02 00 00 00 00 00 00 00  "................"
  9ed00  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ed10  00 7e 00 00 00 00 00 00 00 70 00 00 11 00 01 00  ".~.......p......"
  9ed20  00 00 07 00 00 7e 00 80 00 00 00 00 00 00 00 00  ".....~.........."
  9ed30  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ed40  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ed50  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ed60  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ed70  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ed80  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ed90  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9eda0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9edb0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9edc0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9edd0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ede0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9edf0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ee00  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ee10  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ee20  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ee30  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ee40  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ee50  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ee60  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ee70  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ee80  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ee90  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9eea0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9eeb0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9eec0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9eed0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9eee0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9eef0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ef00  00 c0 02 b0 e0 00 0b 10 00 04 95 00 00 00 11 e9  "................"
  9ef10  00 80 19 13 b3 b0 ea 42 25 00 00 88 00 00 00 00  ".......B%......."
  9ef20  00 04 ff a0 3f 80 00 00 08 ff 3f 10 ff 3f 3f cb  "....?.....?..??."
  9ef30  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ef40  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ef50  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ef60  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ef70  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ef80  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9ef90  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9efa0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9efb0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9efc0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9efd0  00 00 00 00 00 00 00 00 00 00 00 00 00 c0 85 00  "................"
  9efe0  80 f2 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  9eff0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
----- EBDA end -----
/dev/mem[0xff780, 16]: mmap(, 4096,,,, 0xff000) ok
----- MP FP 0xff780 - 0xff78f -----
  ff780  5f 4d 50 5f a0 06 0f 00 01 04 eb 00 00 00 00 00  "_MP_............"
----- MP FP end -----
/dev/mem[0xf06a0, 488]: mmap(, 4096,,,, 0xf0000) ok
----- MP config table 0xf06a0 - 0xf0887 -----
  f06a0  50 43 4d 50 6c 01 04 f0 41 53 55 53 20 20 20 20  "PCMPl...ASUS    "
  f06b0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  f06c0  00 00 22 00 00 00 e0 fe 7c 00 81 00 00 00 10 03  "..".....|......."
  f06d0  52 0f 10 00 ff fb 8b 17 00 00 00 00 00 00 00 00  "R..............."
  f06e0  00 01 10 01 52 0f 10 00 ff fb 8b 17 00 00 00 00  "....R..........."
  f06f0  00 00 00 00 00 02 10 01 52 0f 10 00 ff fb 8b 17  "........R......."
  f0700  00 00 00 00 00 00 00 00 00 03 10 01 52 0f 10 00  "............R..."
  f0710  ff fb 8b 17 00 00 00 00 00 00 00 00 01 00 50 43  "..............PC"
  f0720  49 20 20 20 01 01 50 43 49 20 20 20 01 02 50 43  "I   ..PCI   ..PC"
  f0730  49 20 20 20 01 03 50 43 49 20 20 20 01 04 49 53  "I   ..PCI   ..IS"
  f0740  41 20 20 20 02 04 21 01 00 00 c0 fe 03 03 00 00  "A   ..!........."
  f0750  04 00 04 00 03 00 00 00 04 01 04 01 03 00 00 00  "................"
  f0760  04 00 04 02 03 00 00 00 04 03 04 03 03 00 00 00  "................"
  f0770  04 05 04 05 03 00 00 00 04 06 04 06 03 00 05 00  "................"
  f0780  04 08 04 08 03 00 00 00 04 09 04 09 03 00 00 00  "................"
  f0790  04 0c 04 0c 03 00 00 00 04 0d 04 0d 03 00 00 00  "................"
  f07a0  04 0e 04 0e 03 00 00 00 04 0f 04 0f 03 00 0f 00  "................"
  f07b0  01 14 04 12 03 00 0f 00 00 18 04 12 03 00 0f 00  "................"
  f07c0  02 00 04 12 03 00 0f 00 00 50 04 10 03 00 0f 00  ".........P......"
  f07d0  00 52 04 12 03 00 0f 00 00 48 04 10 03 00 0f 00  ".R.......H......"
  f07e0  00 49 04 11 03 00 0f 00 00 4c 04 12 03 00 0f 00  ".I.......L......"
  f07f0  00 4d 04 13 03 00 0f 00 00 44 04 16 04 03 00 00  ".M.......D......"
  f0800  00 00 ff 00 04 01 00 00 00 00 ff 01 80 14 00 00  "................"
  f0810  00 80 00 00 00 00 00 00 00 70 00 00 00 00 00 00  ".........p......"
  f0820  80 14 00 00 00 00 00 00 00 00 00 00 00 01 00 00  "................"
  f0830  00 00 00 00 80 14 00 01 00 00 0a 00 00 00 00 00  "................"
  f0840  00 00 02 00 00 00 00 00 80 14 00 01 00 00 00 fb  "................"
  f0850  00 00 00 00 00 00 00 01 00 00 00 00 80 14 00 02  "................"
  f0860  00 00 00 d0 00 00 00 00 00 00 00 2b 00 00 00 00  "...........+...."
  f0870  81 08 04 01 00 00 00 00 82 08 00 00 00 00 00 00  "................"
  f0880  82 08 00 00 01 00 00 00  "........"
----- MP config table end -----
>> bios.4: vbe
/dev/mem[0xc0000, 3]: mmap(, 4096,,,, 0xc0000) ok
/dev/mem[0xc0000, 59904]: mmap(, 61440,,,, 0xc0000) ok
/dev/mem[0x0, 4096]: mmap(, 4096,,,, 0x0) ok
  vbe: int 10h points to c000:03c8: e8 dc 0b e8 10 14 74 10
>> bios.4.1: vbe info
vm86: using CPU emulation
>> bios.5: 32
  bios32: valid SD header at 0xf0000 (size 0x10, rev 0), SD at 0xf0010
>> bios.6: acpi
>> sys.1: cpu
  vm check: vm_1 = 0, vm_2 = 0
  is_vmware = 0, has_vmware_mouse = 0
>> misc.9: kernel log
----- kernel log -----
  <4>[ 6145.387632] REJECTED IN= OUT=eth0 SRC=10.223.223.100 DST=205.188.251.43 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=41341 DF PROTO=TCP SPT=2765 DPT=5050 SEQ=1129639199 ACK=0 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40101040201030307) 
  <4>[ 6145.568377] REJECTED IN= OUT=eth0 SRC=10.223.223.100 DST=205.188.251.43 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=31026 DF PROTO=TCP SPT=2766 DPT=5050 SEQ=1144468898 ACK=0 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40101040201030307) 
  <4>[ 6145.749255] REJECTED IN= OUT=eth0 SRC=10.223.223.100 DST=205.188.251.43 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=62092 DF PROTO=TCP SPT=2767 DPT=5050 SEQ=1132510769 ACK=0 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40101040201030307) 
  <4>[ 6472.220762] REJECTED IN= OUT=eth0 SRC=10.223.223.100 DST=64.12.202.116 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=16193 DF PROTO=TCP SPT=1837 DPT=5050 SEQ=1960424654 ACK=0 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40101040201030307) 
  <4>[ 6472.657198] REJECTED IN= OUT=eth0 SRC=10.223.223.100 DST=64.12.202.116 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=58986 DF PROTO=TCP SPT=1838 DPT=5050 SEQ=1970236817 ACK=0 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40101040201030307) 
  <4>[ 6472.882314] REJECTED IN= OUT=eth0 SRC=10.223.223.100 DST=64.12.202.116 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=33804 DF PROTO=TCP SPT=1839 DPT=5050 SEQ=1978796088 ACK=0 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40101040201030307) 
  <4>[ 6473.071134] REJECTED IN= OUT=eth0 SRC=10.223.223.100 DST=64.12.202.116 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=39493 DF PROTO=TCP SPT=1840 DPT=5050 SEQ=1968510502 ACK=0 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40101040201030307) 
  <4>[ 6473.259589] REJECTED IN= OUT=eth0 SRC=10.223.223.100 DST=64.12.202.116 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=5164 DF PROTO=TCP SPT=1841 DPT=5050 SEQ=1978570942 ACK=0 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40101040201030307) 
  <4>[ 6473.432337] REJECTED IN= OUT=eth0 SRC=10.223.223.100 DST=64.12.202.116 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=44316 DF PROTO=TCP SPT=1842 DPT=5050 SEQ=1974608290 ACK=0 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40101040201030307) 
  <4>[ 6473.613109] REJECTED IN= OUT=eth0 SRC=10.223.223.100 DST=64.12.202.116 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=28547 DF PROTO=TCP SPT=1843 DPT=5050 SEQ=1980556136 ACK=0 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40101040201030307) 
  <4>[ 6473.769469] REJECTED IN= OUT=eth0 SRC=10.223.223.100 DST=64.12.202.116 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=52842 DF PROTO=TCP SPT=1844 DPT=5050 SEQ=1985102712 ACK=0 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40101040201030307) 
  <4>[ 6473.934613] REJECTED IN= OUT=eth0 SRC=10.223.223.100 DST=64.12.202.116 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=22030 DF PROTO=TCP SPT=1845 DPT=5050 SEQ=1990122293 ACK=0 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40101040201030307) 
  <4>[ 6474.093638] REJECTED IN= OUT=eth0 SRC=10.223.223.100 DST=64.12.202.116 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=17428 DF PROTO=TCP SPT=1846 DPT=5050 SEQ=1994377591 ACK=0 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40101040201030307) 
  <4>[ 6474.255450] REJECTED IN= OUT=eth0 SRC=10.223.223.100 DST=64.12.202.116 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=55206 DF PROTO=TCP SPT=1847 DPT=5050 SEQ=2003261997 ACK=0 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40101040201030307) 
  <4>[ 6571.672326] REJECTED IN= OUT=eth0 SRC=10.223.223.100 DST=64.12.202.116 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=27186 DF PROTO=TCP SPT=1714 DPT=5190 SEQ=3509749404 ACK=0 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40101040201030307) 
  <4>[ 6574.022718] REJECTED IN= OUT=eth0 SRC=10.223.223.100 DST=64.12.202.116 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=63933 DF PROTO=TCP SPT=1715 DPT=5190 SEQ=3557824324 ACK=0 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40101040201030307) 
  <4>[ 6574.239134] REJECTED IN= OUT=eth0 SRC=10.223.223.100 DST=64.12.202.116 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=50247 DF PROTO=TCP SPT=1716 DPT=5190 SEQ=3549965160 ACK=0 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40101040201030307) 
  <4>[ 6574.408648] REJECTED IN= OUT=eth0 SRC=10.223.223.100 DST=64.12.202.116 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=42576 DF PROTO=TCP SPT=1717 DPT=5190 SEQ=3566618890 ACK=0 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40101040201030307) 
  <4>[ 6574.587160] REJECTED IN= OUT=eth0 SRC=10.223.223.100 DST=64.12.202.116 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=31823 DF PROTO=TCP SPT=1718 DPT=5190 SEQ=3556611017 ACK=0 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40101040201030307) 
  <4>[ 6574.771130] REJECTED IN= OUT=eth0 SRC=10.223.223.100 DST=64.12.202.116 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=4737 DF PROTO=TCP SPT=1719 DPT=5190 SEQ=3566468405 ACK=0 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40101040201030307) 
  <4>[ 6574.953614] REJECTED IN= OUT=eth0 SRC=10.223.223.100 DST=64.12.202.116 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=49239 DF PROTO=TCP SPT=1720 DPT=5190 SEQ=3575328693 ACK=0 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40101040201030307) 
  <4>[ 6575.114790] REJECTED IN= OUT=eth0 SRC=10.223.223.100 DST=64.12.202.116 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=31624 DF PROTO=TCP SPT=1721 DPT=5190 SEQ=3577645954 ACK=0 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40101040201030307) 
  <4>[ 6575.279977] REJECTED IN= OUT=eth0 SRC=10.223.223.100 DST=64.12.202.116 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=49103 DF PROTO=TCP SPT=1722 DPT=5190 SEQ=3569766396 ACK=0 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40101040201030307) 
  <4>[ 6575.472814] REJECTED IN= OUT=eth0 SRC=10.223.223.100 DST=64.12.202.116 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=3561 DF PROTO=TCP SPT=1723 DPT=5190 SEQ=3578592650 ACK=0 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40101040201030307) 
  <4>[ 6749.415144] ABORTED IN=eth0 OUT= MAC=00:26:18:b8:da:07:00:25:9c:19:56:f4:08:00 SRC=216.34.181.60 DST=10.223.223.100 LEN=40 TOS=0x00 PREC=0x80 TTL=245 ID=41898 DF PROTO=TCP SPT=80 DPT=2523 SEQ=2066938576 ACK=1812821133 WINDOW=150 RES=0x00 ACK RST URGP=0 
  <4>[ 6749.415483] ABORTED IN=eth0 OUT= MAC=00:26:18:b8:da:07:00:25:9c:19:56:f4:08:00 SRC=216.34.181.60 DST=10.223.223.100 LEN=40 TOS=0x00 PREC=0x80 TTL=245 ID=41900 DF PROTO=TCP SPT=80 DPT=2524 SEQ=1321988642 ACK=1814916433 WINDOW=150 RES=0x00 ACK RST URGP=0 
  <4>[ 6761.486947] ABORTED IN=eth0 OUT= MAC=00:26:18:b8:da:07:00:25:9c:19:56:f4:08:00 SRC=216.34.181.96 DST=10.223.223.100 LEN=40 TOS=0x00 PREC=0x80 TTL=245 ID=19430 DF PROTO=TCP SPT=80 DPT=2908 SEQ=1824135940 ACK=1812849325 WINDOW=5213 RES=0x00 ACK RST URGP=0 
  <4>[ 6868.891148] ABORTED IN=eth0 OUT= MAC=00:26:18:b8:da:07:00:25:9c:19:56:f4:08:00 SRC=216.34.181.71 DST=10.223.223.100 LEN=40 TOS=0x00 PREC=0x80 TTL=245 ID=51560 DF PROTO=TCP SPT=80 DPT=5627 SEQ=3998579516 ACK=3761369567 WINDOW=150 RES=0x00 ACK RST URGP=0 
  <4>[ 6868.891418] ABORTED IN=eth0 OUT= MAC=00:26:18:b8:da:07:00:25:9c:19:56:f4:08:00 SRC=216.34.181.71 DST=10.223.223.100 LEN=40 TOS=0x00 PREC=0x80 TTL=245 ID=51562 DF PROTO=TCP SPT=80 DPT=5628 SEQ=475773896 ACK=3747268879 WINDOW=151 RES=0x00 ACK RST URGP=0 
  <4>[ 6868.891961] ABORTED IN=eth0 OUT= MAC=00:26:18:b8:da:07:00:25:9c:19:56:f4:08:00 SRC=216.34.181.71 DST=10.223.223.100 LEN=40 TOS=0x00 PREC=0x80 TTL=245 ID=51564 DF PROTO=TCP SPT=80 DPT=5629 SEQ=4292776402 ACK=3759991608 WINDOW=150 RES=0x00 ACK RST URGP=0 
  <4>[ 6883.464874] ABORTED IN=eth0 OUT= MAC=00:26:18:b8:da:07:00:25:9c:19:56:f4:08:00 SRC=216.34.181.60 DST=10.223.223.100 LEN=40 TOS=0x00 PREC=0x80 TTL=245 ID=23162 DF PROTO=TCP SPT=80 DPT=2564 SEQ=1382350518 ACK=3848699822 WINDOW=176 RES=0x00 ACK RST URGP=0 
  <4>[ 6885.567211] ABORTED IN=eth0 OUT= MAC=00:26:18:b8:da:07:00:25:9c:19:56:f4:08:00 SRC=216.34.181.65 DST=10.223.223.100 LEN=40 TOS=0x00 PREC=0x80 TTL=245 ID=15175 DF PROTO=TCP SPT=80 DPT=3968 SEQ=3518774152 ACK=3746818392 WINDOW=6358 RES=0x00 ACK RST URGP=0 
  <6>[ 7971.954628] ppdev: user-space parallel port driver
  <6>[ 7972.155237] lp: driver loaded but no devices found
  <6>[ 7972.212678] st: Version 20080504, fixed bufsize 32768, s/g segs 256
  <4>[ 7972.212707] Driver 'st' needs updating - please use bus_type methods
----- kernel log end -----
>> misc.1: misc data
>> misc.1.1: open serial
>> misc.1.2: open parallel
----- exec: "/sbin/rmmod lp" -----
----- return code: ? -----
----- exec: "/sbin/rmmod parport_pc" -----
----- return code: ? -----
----- exec: "/sbin/rmmod parport" -----
  ERROR: Module parport is in use by ppdev
----- return code: ? -----
----- exec: "/sbin/modprobe parport_pc " -----
  WARNING: All config files need .conf: /etc/modprobe.d/vmxnet, it will be ignored in a future release.
  WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
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
  0170-0177 : 0000:00:14.1
    0170-0177 : pata_atiixp
  01f0-01f7 : 0000:00:14.1
    01f0-01f7 : pata_atiixp
  0230-023f : pnp 00:0c
  0290-029f : pnp 00:0c
  0300-030f : pnp 00:0c
  0376-0376 : 0000:00:14.1
    0376-0376 : pata_atiixp
  03c0-03df : vga+
  03f6-03f6 : 0000:00:14.1
    03f6-03f6 : pata_atiixp
  040b-040b : pnp 00:0b
  04d0-04d1 : pnp 00:0b
  04d6-04d6 : pnp 00:0b
  0800-089f : pnp 00:0b
    0800-0803 : ACPI PM1a_EVT_BLK
    0804-0805 : ACPI PM1a_CNT_BLK
    0808-080b : ACPI PM_TMR
    0810-0815 : ACPI CPU throttle
    0820-0827 : ACPI GPE0_BLK
  08ff-08ff : ACPI PM2_CNT_BLK
  0900-090f : pnp 00:0b
  0910-091f : pnp 00:0b
  0a30-0a3f : pnp 00:0c
  0b00-0b3f : pnp 00:0b
    0b00-0b07 : piix4_smbus
    0b20-0b2f : pnp 00:0b
  0c00-0c01 : pnp 00:0b
  0c14-0c14 : pnp 00:0b
  0c50-0c51 : pnp 00:0b
  0c52-0c52 : pnp 00:0b
  0c6c-0c6c : pnp 00:0b
  0c6f-0c6f : pnp 00:0b
  0cd0-0cd1 : pnp 00:0b
  0cd2-0cd3 : pnp 00:0b
  0cd4-0cd5 : pnp 00:0b
  0cd6-0cd7 : pnp 00:0b
  0cd8-0cdf : pnp 00:0b
  0cf8-0cff : PCI conf1
  8000-800f : 0000:00:11.0
    8000-800f : ahci
  9000-9003 : 0000:00:11.0
    9000-9003 : ahci
  a000-a007 : 0000:00:11.0
    a000-a007 : ahci
  b000-b003 : 0000:00:11.0
    b000-b003 : ahci
  c000-c007 : 0000:00:11.0
    c000-c007 : ahci
  d000-dfff : PCI Bus 0000:01
    d000-d0ff : 0000:01:05.0
  e000-efff : PCI Bus 0000:02
    e800-e8ff : 0000:02:00.0
      e800-e8ff : r8169
  fe00-fefe : pnp 00:0b
  ff00-ff0f : 0000:00:14.1
    ff00-ff0f : pata_atiixp
----- /proc/ioports end -----
----- /proc/interrupts -----
    0:         46          1          1         25   IO-APIC-edge      timer
    1:          0          0          0          2   IO-APIC-edge      i8042
    8:          0          0          0          1   IO-APIC-edge      rtc0
    9:          0          0          0          0   IO-APIC-fasteoi   acpi
   12:          0          0          0          4   IO-APIC-edge      i8042
   14:          0          3        374      54910   IO-APIC-edge      pata_atiixp
   15:          0          0          0          0   IO-APIC-edge      pata_atiixp
   16:          0          0        480     752409   IO-APIC-fasteoi   ohci_hcd:usb3, ohci_hcd:usb4, HDA Intel
   17:          0          0          0          3   IO-APIC-fasteoi   ehci_hcd:usb1
   18:          0          0          0          3   IO-APIC-fasteoi   ohci_hcd:usb5, ohci_hcd:usb6, ohci_hcd:usb7
   19:          0          0          0          0   IO-APIC-fasteoi   ehci_hcd:usb2
  2299:          0          0          0          0   PCI-MSI-edge      fglrx[0]@PCI:1:5:0
  2300:          0          1        504      98634   PCI-MSI-edge      eth0
  2301:          0          3        619     105355   PCI-MSI-edge      ahci
  2303:     651159          0          0          0  HPET_MSI-edge      hpet2
  NMI:          0          0          0          0   Non-maskable interrupts
  LOC:         81     418648     295398     815451   Local timer interrupts
  RES:     384848     212436     147858     208808   Rescheduling interrupts
  CAL:        183        210        216        102   Function call interrupts
  TLB:       8612       7361       7804       6067   TLB shootdowns
  SPU:          0          0          0          0   Spurious interrupts
  ERR:          4
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
  vendor_id	: AuthenticAMD
  cpu family	: 16
  model		: 5
  model name	: AMD Athlon(tm) II X4 620 Processor
  stepping	: 2
  cpu MHz		: 800.000
  cache size	: 512 KB
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
  cpuid level	: 5
  wp		: yes
  flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc pni monitor cx16 lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
  bogomips	: 5223.37
  clflush size	: 64
  power management: ts ttp tm stc 100mhzsteps hwpstate
  
  processor	: 1
  vendor_id	: AuthenticAMD
  cpu family	: 16
  model		: 5
  model name	: AMD Athlon(tm) II X4 620 Processor
  stepping	: 2
  cpu MHz		: 800.000
  cache size	: 512 KB
  physical id	: 0
  siblings	: 4
  core id		: 1
  cpu cores	: 4
  apicid		: 1
  initial apicid	: 1
  fdiv_bug	: no
  hlt_bug		: no
  f00f_bug	: no
  coma_bug	: no
  fpu		: yes
  fpu_exception	: yes
  cpuid level	: 5
  wp		: yes
  flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc pni monitor cx16 lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
  bogomips	: 5209.90
  clflush size	: 64
  power management: ts ttp tm stc 100mhzsteps hwpstate
  
  processor	: 2
  vendor_id	: AuthenticAMD
  cpu family	: 16
  model		: 5
  model name	: AMD Athlon(tm) II X4 620 Processor
  stepping	: 2
  cpu MHz		: 800.000
  cache size	: 512 KB
  physical id	: 0
  siblings	: 4
  core id		: 2
  cpu cores	: 4
  apicid		: 2
  initial apicid	: 2
  fdiv_bug	: no
  hlt_bug		: no
  f00f_bug	: no
  coma_bug	: no
  fpu		: yes
  fpu_exception	: yes
  cpuid level	: 5
  wp		: yes
  flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc pni monitor cx16 lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
  bogomips	: 5209.89
  clflush size	: 64
  power management: ts ttp tm stc 100mhzsteps hwpstate
  
  processor	: 3
  vendor_id	: AuthenticAMD
  cpu family	: 16
  model		: 5
  model name	: AMD Athlon(tm) II X4 620 Processor
  stepping	: 2
  cpu MHz		: 2600.000
  cache size	: 512 KB
  physical id	: 0
  siblings	: 4
  core id		: 3
  cpu cores	: 4
  apicid		: 3
  initial apicid	: 3
  fdiv_bug	: no
  hlt_bug		: no
  f00f_bug	: no
  coma_bug	: no
  fpu		: yes
  fpu_exception	: yes
  cpuid level	: 5
  wp		: yes
  flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc pni monitor cx16 lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
  bogomips	: 5209.89
  clflush size	: 64
  power management: ts ttp tm stc 100mhzsteps hwpstate
  
----- /proc/cpuinfo end -----
>> memory.1: main memory size
  kcore mem:  0x373fe000
  klog mem 0: 0x0
  klog mem 1: 0x0
  klog mem:   0x0
  bios mem:   0x0
  meminfo:    0xbd00d000
>> pci.1: sysfs drivers
----- sysfs driver list (id 0x7386ef0b584aaf4f) -----
      serial8250: /devices/platform/serial8250
           i8042: /devices/platform/i8042
      parport_pc: module = parport_pc
 pcieport-driver: /devices/pci0000:00/0000:00:06.0
            ahci: /devices/pci0000:00/0000:00:11.0
            ahci: module = ahci
        sata_sil: module = sata_sil
         sata_nv: module = sata_nv
        pata_ali: module = pata_ali
     pata_atiixp: /devices/pci0000:00/0000:00:14.1
     pata_cs5536: module = pata_cs5536
     pata_it821x: module = pata_it821x
        ehci_hcd: /devices/pci0000:00/0000:00:12.2
        ehci_hcd: /devices/pci0000:00/0000:00:13.2
        ehci_hcd: module = ehci_hcd
        ohci_hcd: /devices/pci0000:00/0000:00:12.0
        ohci_hcd: /devices/pci0000:00/0000:00:12.1
        ohci_hcd: /devices/pci0000:00/0000:00:13.0
        ohci_hcd: /devices/pci0000:00/0000:00:13.1
        ohci_hcd: /devices/pci0000:00/0000:00:14.5
        uhci_hcd: module = uhci_hcd
      parport_pc: module = parport_pc
          shpchp: module = shpchp
     piix4_smbus: /devices/pci0000:00/0000:00:14.0
     piix4_smbus: module = i2c_piix4
           r8169: /devices/pci0000:00/0000:00:06.0/0000:02:00.0
           r8169: module = r8169
       HDA Intel: /devices/pci0000:00/0000:00:14.2
       HDA Intel: module = snd_hda_intel
       fglrx_pci: /devices/pci0000:00/0000:00:01.0/0000:01:05.0
       fglrx_pci: module = fglrx
        pci_root: /devices/LNXSYSTM:00/device:00/PNP0A03:00
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0C0F:00
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0C0F:01
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0C0F:02
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0C0F:03
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0C0F:04
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0C0F:05
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0C0F:06
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0C0F:07
             wmi: /devices/LNXSYSTM:00/PNP0C14:00
          button: /devices/LNXSYSTM:00/LNXPWRBN:00
          button: /devices/LNXSYSTM:00/device:00/PNP0C0C:00
       processor: /devices/LNXSYSTM:00/ACPI_CPU:00
       processor: /devices/LNXSYSTM:00/ACPI_CPU:01
       processor: /devices/LNXSYSTM:00/ACPI_CPU:02
       processor: /devices/LNXSYSTM:00/ACPI_CPU:03
          system: /devices/pnp0/00:01
          system: /devices/pnp0/00:0a
          system: /devices/pnp0/00:0b
          system: /devices/pnp0/00:0c
          system: /devices/pnp0/00:0d
          system: /devices/pnp0/00:0e
       i8042 kbd: /devices/pnp0/00:02
       i8042 aux: /devices/pnp0/00:03
        rtc_cmos: /devices/pnp0/00:05
              sd: /devices/pci0000:00/0000:00:11.0/host0/target0:0:0/0:0:0:0
              sr: /devices/pci0000:00/0000:00:14.1/host4/target4:0:0/4:0:0:0
           usbfs: module = usbcore
             hub: module = usbcore
             hub: /devices/pci0000:00/0000:00:12.2/usb1/1-0:1.0
             hub: /devices/pci0000:00/0000:00:13.2/usb2/2-0:1.0
             hub: /devices/pci0000:00/0000:00:12.0/usb3/3-0:1.0
             hub: /devices/pci0000:00/0000:00:12.1/usb4/4-0:1.0
             hub: /devices/pci0000:00/0000:00:13.0/usb5/5-0:1.0
             hub: /devices/pci0000:00/0000:00:13.1/usb6/6-0:1.0
             hub: /devices/pci0000:00/0000:00:14.5/usb7/7-0:1.0
             usb: /devices/pci0000:00/0000:00:12.2/usb1
             usb: /devices/pci0000:00/0000:00:13.2/usb2
             usb: /devices/pci0000:00/0000:00:12.0/usb3
             usb: /devices/pci0000:00/0000:00:12.1/usb4
             usb: /devices/pci0000:00/0000:00:13.0/usb5
             usb: /devices/pci0000:00/0000:00:13.1/usb6
             usb: /devices/pci0000:00/0000:00:14.5/usb7
             usb: /devices/pci0000:00/0000:00:12.1/usb4/4-2
             usb: /devices/pci0000:00/0000:00:12.1/usb4/4-3
          hiddev: module = usbhid
          usbhid: /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0
          usbhid: /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.1
          usbhid: /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0
          usbhid: /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.1
          usbhid: module = usbhid
         psmouse: module = psmouse
     generic-usb: module = usbhid
     generic-usb: /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0/0003:046D:C049.0001
     generic-usb: /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.1/0003:046D:C049.0002
     generic-usb: /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0/0003:046E:5542.0003
     generic-usb: /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.1/0003:046E:5542.0004
----- sysfs driver list end -----
>> pci.2: get sysfs pci data
  pci device: name = 0000:02:00.0
    path = /devices/pci0000:00/0000:00:06.0/0000:02:00.0
    modalias = "pci:v000010ECd00008168sv00001043sd00008367bc02sc00i00"
    class = 0x20000
    vendor = 0x10ec
    device = 0x8168
    subvendor = 0x1043
    subdevice = 0x8367
    irq = 2300
    res[0] = 0xe800 0xe8ff 0x20101
    res[2] = 0xfafff000 0xfaffffff 0x2120c
    res[4] = 0xfafe0000 0xfafeffff 0x2120c
    res[6] = 0xfbff0000 0xfbffffff 0x27200
    config[64]
  pci device: name = 0000:01:05.0
    path = /devices/pci0000:00/0000:00:01.0/0000:01:05.0
    modalias = "pci:v00001002d00009616sv00001043sd00008388bc03sc00i00"
    class = 0x30000
    vendor = 0x1002
    device = 0x9616
    subvendor = 0x1043
    subdevice = 0x8388
    irq = 2299
    res[0] = 0xd0000000 0xdfffffff 0x21208
    res[1] = 0xd000 0xd0ff 0x20101
    res[2] = 0xfbef0000 0xfbefffff 0x20200
    res[5] = 0xfbd00000 0xfbdfffff 0x20200
    config[64]
  pci device: name = 0000:00:18.4
    path = /devices/pci0000:00/0000:00:18.4
    modalias = "pci:v00001022d00001204sv00000000sd00000000bc06sc00i00"
    class = 0x60000
    vendor = 0x1022
    device = 0x1204
    subvendor = 0x0
    subdevice = 0x0
    irq = 0
    config[64]
  pci device: name = 0000:00:18.3
    path = /devices/pci0000:00/0000:00:18.3
    modalias = "pci:v00001022d00001203sv00000000sd00000000bc06sc00i00"
    class = 0x60000
    vendor = 0x1022
    device = 0x1203
    subvendor = 0x0
    subdevice = 0x0
    irq = 0
    config[64]
  pci device: name = 0000:00:18.2
    path = /devices/pci0000:00/0000:00:18.2
    modalias = "pci:v00001022d00001202sv00000000sd00000000bc06sc00i00"
    class = 0x60000
    vendor = 0x1022
    device = 0x1202
    subvendor = 0x0
    subdevice = 0x0
    irq = 0
    config[64]
  pci device: name = 0000:00:18.1
    path = /devices/pci0000:00/0000:00:18.1
    modalias = "pci:v00001022d00001201sv00000000sd00000000bc06sc00i00"
    class = 0x60000
    vendor = 0x1022
    device = 0x1201
    subvendor = 0x0
    subdevice = 0x0
    irq = 0
    config[64]
  pci device: name = 0000:00:18.0
    path = /devices/pci0000:00/0000:00:18.0
    modalias = "pci:v00001022d00001200sv00000000sd00000000bc06sc00i00"
    class = 0x60000
    vendor = 0x1022
    device = 0x1200
    subvendor = 0x0
    subdevice = 0x0
    irq = 0
    config[64]
  pci device: name = 0000:00:14.5
    path = /devices/pci0000:00/0000:00:14.5
    modalias = "pci:v00001002d00004399sv00001043sd00008389bc0Csc03i10"
    class = 0xc0310
    vendor = 0x1002
    device = 0x4399
    subvendor = 0x1043
    subdevice = 0x8389
    irq = 18
    res[0] = 0xfbcf9000 0xfbcf9fff 0x20200
    config[64]
  pci device: name = 0000:00:14.4
    path = /devices/pci0000:00/0000:00:14.4
    modalias = "pci:v00001002d00004384sv00000000sd00000000bc06sc04i01"
    class = 0x60401
    vendor = 0x1002
    device = 0x4384
    subvendor = 0x0
    subdevice = 0x0
    irq = 0
    config[64]
  pci device: name = 0000:00:14.3
    path = /devices/pci0000:00/0000:00:14.3
    modalias = "pci:v00001002d0000439Dsv00001043sd00008389bc06sc01i00"
    class = 0x60100
    vendor = 0x1002
    device = 0x439d
    subvendor = 0x1043
    subdevice = 0x8389
    irq = 0
    config[64]
  pci device: name = 0000:00:14.2
    path = /devices/pci0000:00/0000:00:14.2
    modalias = "pci:v00001002d00004383sv00001043sd000082EAbc04sc03i00"
    class = 0x40300
    vendor = 0x1002
    device = 0x4383
    subvendor = 0x1043
    subdevice = 0x82ea
    irq = 16
    res[0] = 0xfbcf4000 0xfbcf7fff 0x20204
    config[64]
  pci device: name = 0000:00:14.1
    path = /devices/pci0000:00/0000:00:14.1
    modalias = "pci:v00001002d0000439Csv00001043sd00008389bc01sc01i8a"
    class = 0x1018a
    vendor = 0x1002
    device = 0x439c
    subvendor = 0x1043
    subdevice = 0x8389
    irq = 16
    res[0] = 0x1f0 0x1f7 0x110
    res[1] = 0x3f6 0x3f6 0x110
    res[2] = 0x170 0x177 0x110
    res[3] = 0x376 0x376 0x110
    res[4] = 0xff00 0xff0f 0x20101
    config[64]
  pci device: name = 0000:00:14.0
    path = /devices/pci0000:00/0000:00:14.0
    modalias = "pci:v00001002d00004385sv00001043sd00008389bc0Csc05i00"
    class = 0xc0500
    vendor = 0x1002
    device = 0x4385
    subvendor = 0x1043
    subdevice = 0x8389
    irq = 0
    config[64]
  pci device: name = 0000:00:13.2
    path = /devices/pci0000:00/0000:00:13.2
    modalias = "pci:v00001002d00004396sv00001043sd00008389bc0Csc03i20"
    class = 0xc0320
    vendor = 0x1002
    device = 0x4396
    subvendor = 0x1043
    subdevice = 0x8389
    irq = 19
    res[0] = 0xfbcfa800 0xfbcfa8ff 0x20200
    config[64]
  pci device: name = 0000:00:13.1
    path = /devices/pci0000:00/0000:00:13.1
    modalias = "pci:v00001002d00004398sv00001043sd00008389bc0Csc03i10"
    class = 0xc0310
    vendor = 0x1002
    device = 0x4398
    subvendor = 0x1043
    subdevice = 0x8389
    irq = 18
    res[0] = 0xfbcfb000 0xfbcfbfff 0x20200
    config[64]
  pci device: name = 0000:00:13.0
    path = /devices/pci0000:00/0000:00:13.0
    modalias = "pci:v00001002d00004397sv00001043sd00008389bc0Csc03i10"
    class = 0xc0310
    vendor = 0x1002
    device = 0x4397
    subvendor = 0x1043
    subdevice = 0x8389
    irq = 18
    res[0] = 0xfbcfc000 0xfbcfcfff 0x20200
    config[64]
  pci device: name = 0000:00:12.2
    path = /devices/pci0000:00/0000:00:12.2
    modalias = "pci:v00001002d00004396sv00001043sd00008389bc0Csc03i20"
    class = 0xc0320
    vendor = 0x1002
    device = 0x4396
    subvendor = 0x1043
    subdevice = 0x8389
    irq = 17
    res[0] = 0xfbcff000 0xfbcff0ff 0x20200
    config[64]
  pci device: name = 0000:00:12.1
    path = /devices/pci0000:00/0000:00:12.1
    modalias = "pci:v00001002d00004398sv00001043sd00008389bc0Csc03i10"
    class = 0xc0310
    vendor = 0x1002
    device = 0x4398
    subvendor = 0x1043
    subdevice = 0x8389
    irq = 16
    res[0] = 0xfbcfd000 0xfbcfdfff 0x20200
    config[64]
  pci device: name = 0000:00:12.0
    path = /devices/pci0000:00/0000:00:12.0
    modalias = "pci:v00001002d00004397sv00001043sd00008389bc0Csc03i10"
    class = 0xc0310
    vendor = 0x1002
    device = 0x4397
    subvendor = 0x1043
    subdevice = 0x8389
    irq = 16
    res[0] = 0xfbcfe000 0xfbcfefff 0x20200
    config[64]
  pci device: name = 0000:00:11.0
    path = /devices/pci0000:00/0000:00:11.0
    modalias = "pci:v00001002d00004390sv00001043sd00008389bc01sc06i01"
    class = 0x10601
    vendor = 0x1002
    device = 0x4390
    subvendor = 0x1043
    subdevice = 0x8389
    irq = 2301
    res[0] = 0xc000 0xc007 0x20101
    res[1] = 0xb000 0xb003 0x20101
    res[2] = 0xa000 0xa007 0x20101
    res[3] = 0x9000 0x9003 0x20101
    res[4] = 0x8000 0x800f 0x20101
    res[5] = 0xfbcff800 0xfbcffbff 0x20200
    config[64]
  pci device: name = 0000:00:06.0
    path = /devices/pci0000:00/0000:00:06.0
    modalias = "pci:v00001022d00009606sv00000000sd00000000bc06sc04i00"
    class = 0x60400
    vendor = 0x1022
    device = 0x9606
    subvendor = 0x0
    subdevice = 0x0
    irq = 2302
    config[64]
  pci device: name = 0000:00:01.0
    path = /devices/pci0000:00/0000:00:01.0
    modalias = "pci:v00001043d00009602sv00000000sd00000000bc06sc04i00"
    class = 0x60400
    vendor = 0x1043
    device = 0x9602
    subvendor = 0x0
    subdevice = 0x0
    irq = 0
    config[64]
  pci device: name = 0000:00:00.0
    path = /devices/pci0000:00/0000:00:00.0
    modalias = "pci:v00001022d00009600sv00001043sd00008388bc06sc00i00"
    class = 0x60000
    vendor = 0x1022
    device = 0x9600
    subvendor = 0x1043
    subdevice = 0x8388
    irq = 0
    config[64]
---------- PCI raw data ----------
bus 02, slot 00, func 0, vend:dev:s_vend:s_dev:rev 10ec:8168:1043:8367:02
class 02, sub_class 00 prog_if 00, hdr 0, flags <pm>, irq 2300
  addr0 0000e800, size 00000100
  addr2 fafff000, size 00001000
  addr4 fafe0000, size 00010000
  00: ec 10 68 81 07 05 10 00 02 00 00 02 10 00 00 00  "..h............."
  10: 01 e8 00 00 00 00 00 00 0c f0 ff fa 00 00 00 00  "................"
  20: 0c 00 fe fa 00 00 00 00 00 00 00 00 43 10 67 83  "............C.g."
  30: 00 00 ff fb 40 00 00 00 00 00 00 00 0a 01 00 00  "....@..........."
  40: 01 50 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ".P.............."
  50: 05 70 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ".p.............."
  60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  70: 10 b0 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  b0: 11 d0 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  d0: 03 00  ".."

bus 01, slot 05, func 0, vend:dev:s_vend:s_dev:rev 1002:9616:1043:8388:00
class 03, sub_class 00 prog_if 00, hdr 0, flags <pm>, irq 2299
  addr0 d0000000, size 10000000
  addr1 0000d000, size 00000100
  addr2 fbef0000, size 00010000
  addr5 fbd00000, size 00100000
  00: 02 10 16 96 07 05 10 00 00 00 00 03 10 00 00 00  "................"
  10: 08 00 00 d0 01 d0 00 00 00 00 ef fb 00 00 00 00  "................"
  20: 00 00 00 00 00 00 d0 fb 00 00 00 00 43 10 88 83  "............C..."
  30: 00 00 00 00 50 00 00 00 00 00 00 00 0a 01 00 00  "....P..........."
  40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  50: 01 a0 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  a0: 05 00  ".."

bus 00, slot 18, func 4, vend:dev:s_vend:s_dev:rev 1022:1204:0000:0000:00
class 06, sub_class 00 prog_if 00, hdr 0, flags <>, irq 0
  00: 22 10 04 12 00 00 00 00 00 00 00 06 00 00 80 00  ""..............."
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"

bus 00, slot 18, func 3, vend:dev:s_vend:s_dev:rev 1022:1203:0000:0000:00
class 06, sub_class 00 prog_if 00, hdr 0, flags <>, irq 0
  00: 22 10 03 12 00 00 10 00 00 00 00 06 00 00 80 00  ""..............."
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  30: 00 00 00 00 f0 00 00 00 00 00 00 00 00 00 00 00  "................"
  40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  f0: 0f 00  ".."

bus 00, slot 18, func 2, vend:dev:s_vend:s_dev:rev 1022:1202:0000:0000:00
class 06, sub_class 00 prog_if 00, hdr 0, flags <>, irq 0
  00: 22 10 02 12 00 00 00 00 00 00 00 06 00 00 80 00  ""..............."
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"

bus 00, slot 18, func 1, vend:dev:s_vend:s_dev:rev 1022:1201:0000:0000:00
class 06, sub_class 00 prog_if 00, hdr 0, flags <>, irq 0
  00: 22 10 01 12 00 00 00 00 00 00 00 06 00 00 80 00  ""..............."
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"

bus 00, slot 18, func 0, vend:dev:s_vend:s_dev:rev 1022:1200:0000:0000:00
class 06, sub_class 00 prog_if 00, hdr 0, flags <>, irq 0
  00: 22 10 00 12 00 00 10 00 00 00 00 06 00 00 80 00  ""..............."
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  30: 00 00 00 00 80 00 00 00 00 00 00 00 00 00 00 00  "................"
  40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  80: 08 00  ".."

bus 00, slot 14, func 5, vend:dev:s_vend:s_dev:rev 1002:4399:1043:8389:00
class 0c, sub_class 03 prog_if 10, hdr 0, flags <>, irq 18
  addr0 fbcf9000, size 00001000
  00: 02 10 99 43 06 01 a0 02 00 10 03 0c 10 40 00 00  "...C.........@.."
  10: 00 90 cf fb 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 43 10 89 83  "............C..."
  30: 00 00 00 00 00 00 00 00 00 00 00 00 0a 03 00 00  "................"

bus 00->03, slot 14, func 4, vend:dev:s_vend:s_dev:rev 1002:4384:0000:0000:00
class 06, sub_class 04 prog_if 01, hdr 1, flags <>, irq 0
  00: 02 10 84 43 05 01 a0 02 00 01 04 06 00 40 81 00  "...C.........@.."
  10: 00 00 00 00 00 00 00 00 00 03 03 40 f0 00 80 22  "...........@...""
  20: f0 ff 00 00 f0 ff 00 00 00 00 00 00 00 00 00 00  "................"
  30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 03 00  "................"

bus 00, slot 14, func 3, vend:dev:s_vend:s_dev:rev 1002:439d:1043:8389:00
class 06, sub_class 01 prog_if 00, hdr 0, flags <>, irq 0
  00: 02 10 9d 43 0f 00 20 02 00 00 01 06 00 00 80 00  "...C.. ........."
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 43 10 89 83  "............C..."
  30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"

bus 00, slot 14, func 2, vend:dev:s_vend:s_dev:rev 1002:4383:1043:82ea:00
class 04, sub_class 03 prog_if 00, hdr 0, flags <pm>, irq 16
  addr0 fbcf4000, size 00004000
  00: 02 10 83 43 06 00 10 04 00 00 03 04 10 40 00 00  "...C.........@.."
  10: 04 40 cf fb 00 00 00 00 00 00 00 00 00 00 00 00  ".@.............."
  20: 00 00 00 00 00 00 00 00 00 00 00 00 43 10 ea 82  "............C..."
  30: 00 00 00 00 50 00 00 00 00 00 00 00 07 00 00 00  "....P..........."
  40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  50: 01 00  ".."

bus 00, slot 14, func 1, vend:dev:s_vend:s_dev:rev 1002:439c:1043:8389:00
class 01, sub_class 01 prog_if 8a, hdr 0, flags <>, irq 16
  addr0 000001f0, size 00000008
  addr1 000003f6, size 00000001
  addr2 00000170, size 00000008
  addr3 00000376, size 00000001
  addr4 0000ff00, size 00000010
  00: 02 10 9c 43 05 00 30 02 00 8a 01 01 00 40 00 00  "...C..0......@.."
  10: 01 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00  "................"
  20: 01 ff 00 00 00 00 00 00 00 00 00 00 43 10 89 83  "............C..."
  30: 00 00 00 00 70 00 00 00 00 00 00 00 00 01 00 00  "....p..........."
  40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  70: 05 00  ".."

bus 00, slot 14, func 0, vend:dev:s_vend:s_dev:rev 1002:4385:1043:8389:3c
class 0c, sub_class 05 prog_if 00, hdr 0, flags <>, irq 0
  00: 02 10 85 43 03 04 30 02 3c 00 05 0c 00 00 80 00  "...C..0.<......."
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 43 10 89 83  "............C..."
  30: 00 00 00 00 b0 00 00 00 00 00 00 00 00 00 00 00  "................"
  40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  b0: 08 00  ".."

bus 00, slot 13, func 2, vend:dev:s_vend:s_dev:rev 1002:4396:1043:8389:00
class 0c, sub_class 03 prog_if 20, hdr 0, flags <pm>, irq 19
  addr0 fbcfa800, size 00000100
  00: 02 10 96 43 16 01 b0 02 00 20 03 0c 10 40 00 00  "...C..... ...@.."
  10: 00 a8 cf fb 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 43 10 89 83  "............C..."
  30: 00 00 00 00 c0 00 00 00 00 00 00 00 0a 02 00 00  "................"
  40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  c0: 01 e4 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  e0: 00 00 00 00 0a 00  "......"

bus 00, slot 13, func 1, vend:dev:s_vend:s_dev:rev 1002:4398:1043:8389:00
class 0c, sub_class 03 prog_if 10, hdr 0, flags <>, irq 18
  addr0 fbcfb000, size 00001000
  00: 02 10 98 43 17 01 a0 02 00 10 03 0c 10 40 00 00  "...C.........@.."
  10: 00 b0 cf fb 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 43 10 89 83  "............C..."
  30: 00 00 00 00 00 00 00 00 00 00 00 00 0a 01 00 00  "................"

bus 00, slot 13, func 0, vend:dev:s_vend:s_dev:rev 1002:4397:1043:8389:00
class 0c, sub_class 03 prog_if 10, hdr 0, flags <>, irq 18
  addr0 fbcfc000, size 00001000
  00: 02 10 97 43 06 01 a0 02 00 10 03 0c 10 40 80 00  "...C.........@.."
  10: 00 c0 cf fb 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 43 10 89 83  "............C..."
  30: 00 00 00 00 00 00 00 00 00 00 00 00 0a 01 00 00  "................"

bus 00, slot 12, func 2, vend:dev:s_vend:s_dev:rev 1002:4396:1043:8389:00
class 0c, sub_class 03 prog_if 20, hdr 0, flags <pm>, irq 17
  addr0 fbcff000, size 00000100
  00: 02 10 96 43 16 01 b0 02 00 20 03 0c 10 40 00 00  "...C..... ...@.."
  10: 00 f0 cf fb 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 43 10 89 83  "............C..."
  30: 00 00 00 00 c0 00 00 00 00 00 00 00 04 02 00 00  "................"
  40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  c0: 01 e4 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  e0: 00 00 00 00 0a 00  "......"

bus 00, slot 12, func 1, vend:dev:s_vend:s_dev:rev 1002:4398:1043:8389:00
class 0c, sub_class 03 prog_if 10, hdr 0, flags <>, irq 16
  addr0 fbcfd000, size 00001000
  00: 02 10 98 43 17 01 a0 02 00 10 03 0c 10 40 00 00  "...C.........@.."
  10: 00 d0 cf fb 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 43 10 89 83  "............C..."
  30: 00 00 00 00 00 00 00 00 00 00 00 00 07 01 00 00  "................"

bus 00, slot 12, func 0, vend:dev:s_vend:s_dev:rev 1002:4397:1043:8389:00
class 0c, sub_class 03 prog_if 10, hdr 0, flags <>, irq 16
  addr0 fbcfe000, size 00001000
  00: 02 10 97 43 06 01 a0 02 00 10 03 0c 10 40 80 00  "...C.........@.."
  10: 00 e0 cf fb 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 43 10 89 83  "............C..."
  30: 00 00 00 00 00 00 00 00 00 00 00 00 07 01 00 00  "................"

bus 00, slot 11, func 0, vend:dev:s_vend:s_dev:rev 1002:4390:1043:8389:00
class 01, sub_class 06 prog_if 01, hdr 0, flags <pm>, irq 2301
  addr0 0000c000, size 00000008
  addr1 0000b000, size 00000004
  addr2 0000a000, size 00000008
  addr3 00009000, size 00000004
  addr4 00008000, size 00000010
  addr5 fbcff800, size 00000400
  00: 02 10 90 43 07 05 30 02 00 01 06 01 10 40 00 00  "...C..0......@.."
  10: 01 c0 00 00 01 b0 00 00 01 a0 00 00 01 90 00 00  "................"
  20: 01 80 00 00 00 f8 cf fb 00 00 00 00 43 10 89 83  "............C..."
  30: 00 00 00 00 60 00 00 00 00 00 00 00 0b 01 00 00  "....`..........."
  40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  50: 05 70 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ".p.............."
  60: 01 50 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ".P.............."
  70: 12 00  ".."

bus 00->02, slot 06, func 0, vend:dev:s_vend:s_dev:rev 1022:9606:0000:0000:00
class 06, sub_class 04 prog_if 00, hdr 1, flags <>, irq 2302
  00: 22 10 06 96 07 05 10 00 00 00 04 06 10 00 01 00  ""..............."
  10: 00 00 00 00 00 00 00 00 00 02 02 00 e1 e1 00 00  "................"
  20: f0 fb f0 fb f1 fa f1 fa 00 00 00 00 00 00 00 00  "................"
  30: 00 00 00 00 50 00 00 00 00 00 00 00 0a 01 03 00  "....P..........."

bus 00->01, slot 01, func 0, vend:dev:s_vend:s_dev:rev 1043:9602:0000:0000:00
class 06, sub_class 04 prog_if 00, hdr 1, flags <>, irq 0
  00: 43 10 02 96 07 01 30 02 00 00 04 06 00 40 01 00  "C.....0......@.."
  10: 00 00 00 00 00 00 00 00 00 01 01 40 d1 d1 20 22  "...........@.. ""
  20: d0 fb e0 fb 01 d0 f1 df 00 00 00 00 00 00 00 00  "................"
  30: 00 00 00 00 44 00 00 00 00 00 00 00 00 00 1a 00  "....D..........."

bus 00, slot 00, func 0, vend:dev:s_vend:s_dev:rev 1022:9600:1043:8388:00
class 06, sub_class 00 prog_if 00, hdr 0, flags <>, irq 0
  00: 22 10 00 96 06 00 30 22 00 00 00 06 00 00 00 00  "".....0"........"
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 43 10 88 83  "............C..."
  30: 00 00 00 00 c4 00 00 00 00 00 00 00 00 00 00 00  "................"
  40: 08 9c 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  50: 00 00 00 00 08 40 00 00 00 00 00 00 00 00 00 00  ".....@.........."
  60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  90: 00 00 00 00 00 00 00 00 00 00 00 00 08 f8 00 00  "................"
  a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  c0: 00 00 00 00 08 54 00 00 00 00 00 00 00 00 00 00  ".....T.........."
  d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  f0: 00 00 00 00 00 00 00 00 08 00  ".........."
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
  platform device: name = eisa.0
    path = /devices/platform/eisa.0
    type = "platform:eisa"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = i8042
    path = /devices/platform/i8042
    type = "platform:i8042"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = Fixed MDIO bus.0
    path = /devices/platform/Fixed MDIO bus.0
    type = "platform:Fixed MDIO bus"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = serial8250
    path = /devices/platform/serial8250
    type = "platform:serial8250"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = pcspkr
    path = /devices/platform/pcspkr
    type = "platform:pcspkr"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
>> pci.8: of_platform
sysfs: no such bus: of_platform
>> pci.9: vm
sysfs: no such bus: vm
>> pci.10: virtio
sysfs: no such bus: virtio
>> monitor.1: ddc
>> monitor.2: bios
>> monitor.3: pci
>> monitor.4: internal db
>> monitor.5: prom
>> isapnp.1: pnp devices
  pnp device: name = 00:0e
    path = /devices/pnp0/00:0e
    id = PNP 0c01
  pnp device: name = 00:0d
    path = /devices/pnp0/00:0d
    id = PNP 0c02
  pnp device: name = 00:0c
    path = /devices/pnp0/00:0c
    id = PNP 0c02
  pnp device: name = 00:0b
    path = /devices/pnp0/00:0b
    id = PNP 0c02
  pnp device: name = 00:0a
    path = /devices/pnp0/00:0a
    id = PNP 0c02
  pnp device: name = 00:09
    path = /devices/pnp0/00:09
    id = PNP 0103
  pnp device: name = 00:08
    path = /devices/pnp0/00:08
    id = PNP 0700
  pnp device: name = 00:07
    path = /devices/pnp0/00:07
    id = PNP 0c04
  pnp device: name = 00:06
    path = /devices/pnp0/00:06
    id = PNP 0800
  pnp device: name = 00:05
    path = /devices/pnp0/00:05
    id = PNP 0b00
  pnp device: name = 00:04
    path = /devices/pnp0/00:04
    id = PNP 0200
  pnp device: name = 00:03
    path = /devices/pnp0/00:03
    id = PNP 0f03
  pnp device: name = 00:02
    path = /devices/pnp0/00:02
    id = PNP 0303
  pnp device: name = 00:01
    path = /devices/pnp0/00:01
    id = PNP 0c02
  pnp device: name = 00:00
    path = /devices/pnp0/00:00
    id = PNP 0a03
>> pcmcia.1: sysfs drivers
>> pcmcia.2: pcmcia
sysfs: no such bus: pcmcia
>> pcmcia.3: pcmcia ctrl
sysfs: no such class: pcmcia_socket
>> serial.1: read info
----- /proc/tty/driver/serial -----
  0: uart:unknown port:000003F8 irq:4
  1: uart:unknown port:000002F8 irq:3
  2: uart:unknown port:000003E8 irq:4
  3: uart:unknown port:000002E8 irq:3
----- /proc/tty/driver/serial end -----
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
i/o:0 0x0170 - 0x0177 (0x08) "0000:00:14.1"
i/o:0 0x0170 - 0x0177 (0x08) "pata_atiixp"
i/o:0 0x01f0 - 0x01f7 (0x08) "0000:00:14.1"
i/o:0 0x01f0 - 0x01f7 (0x08) "pata_atiixp"
i/o:0 0x0230 - 0x023f (0x10) "pnp 00:0c"
i/o:0 0x0290 - 0x029f (0x10) "pnp 00:0c"
i/o:0 0x0300 - 0x030f (0x10) "pnp 00:0c"
i/o:0 0x0376 - 0x0376 (0x01) "0000:00:14.1"
i/o:0 0x0376 - 0x0376 (0x01) "pata_atiixp"
i/o:1 0x03c0 - 0x03df (0x20) "vga+"
i/o:0 0x03f6 - 0x03f6 (0x01) "0000:00:14.1"
i/o:0 0x03f6 - 0x03f6 (0x01) "pata_atiixp"
i/o:0 0x040b - 0x040b (0x01) "pnp 00:0b"
i/o:0 0x04d0 - 0x04d1 (0x02) "pnp 00:0b"
i/o:0 0x04d6 - 0x04d6 (0x01) "pnp 00:0b"
i/o:0 0x0800 - 0x089f (0xa0) "pnp 00:0b"
i/o:0 0x0800 - 0x0803 (0x04) "ACPI PM1a_EVT_BLK"
i/o:0 0x0804 - 0x0805 (0x02) "ACPI PM1a_CNT_BLK"
i/o:0 0x0808 - 0x080b (0x04) "ACPI PM_TMR"
i/o:0 0x0810 - 0x0815 (0x06) "ACPI CPU throttle"
i/o:0 0x0820 - 0x0827 (0x08) "ACPI GPE0_BLK"
i/o:0 0x08ff - 0x08ff (0x01) "ACPI PM2_CNT_BLK"
i/o:0 0x0900 - 0x090f (0x10) "pnp 00:0b"
i/o:0 0x0910 - 0x091f (0x10) "pnp 00:0b"
i/o:0 0x0a30 - 0x0a3f (0x10) "pnp 00:0c"
i/o:0 0x0b00 - 0x0b3f (0x40) "pnp 00:0b"
i/o:0 0x0b00 - 0x0b07 (0x08) "piix4_smbus"
i/o:0 0x0b20 - 0x0b2f (0x10) "pnp 00:0b"
i/o:0 0x0c00 - 0x0c01 (0x02) "pnp 00:0b"
i/o:0 0x0c14 - 0x0c14 (0x01) "pnp 00:0b"
i/o:0 0x0c50 - 0x0c51 (0x02) "pnp 00:0b"
i/o:0 0x0c52 - 0x0c52 (0x01) "pnp 00:0b"
i/o:0 0x0c6c - 0x0c6c (0x01) "pnp 00:0b"
i/o:0 0x0c6f - 0x0c6f (0x01) "pnp 00:0b"
i/o:0 0x0cd0 - 0x0cd1 (0x02) "pnp 00:0b"
i/o:0 0x0cd2 - 0x0cd3 (0x02) "pnp 00:0b"
i/o:0 0x0cd4 - 0x0cd5 (0x02) "pnp 00:0b"
i/o:0 0x0cd6 - 0x0cd7 (0x02) "pnp 00:0b"
i/o:0 0x0cd8 - 0x0cdf (0x08) "pnp 00:0b"
i/o:0 0x0cf8 - 0x0cff (0x08) "PCI conf1"
i/o:0 0x8000 - 0x800f (0x10) "0000:00:11.0"
i/o:0 0x8000 - 0x800f (0x10) "ahci"
i/o:0 0x9000 - 0x9003 (0x04) "0000:00:11.0"
i/o:0 0x9000 - 0x9003 (0x04) "ahci"
i/o:0 0xa000 - 0xa007 (0x08) "0000:00:11.0"
i/o:0 0xa000 - 0xa007 (0x08) "ahci"
i/o:0 0xb000 - 0xb003 (0x04) "0000:00:11.0"
i/o:0 0xb000 - 0xb003 (0x04) "ahci"
i/o:0 0xc000 - 0xc007 (0x08) "0000:00:11.0"
i/o:0 0xc000 - 0xc007 (0x08) "ahci"
i/o:0 0xd000 - 0xdfff (0x1000) "PCI Bus 0000:01"
i/o:0 0xd000 - 0xd0ff (0x100) "0000:01:05.0"
i/o:0 0xe000 - 0xefff (0x1000) "PCI Bus 0000:02"
i/o:0 0xe800 - 0xe8ff (0x100) "0000:02:00.0"
i/o:0 0xe800 - 0xe8ff (0x100) "r8169"
i/o:0 0xfe00 - 0xfefe (0xff) "pnp 00:0b"
i/o:0 0xff00 - 0xff0f (0x10) "0000:00:14.1"
i/o:0 0xff00 - 0xff0f (0x10) "pata_atiixp"
irq:1  0 (       73) "timer"
irq:0  1 (        2) "i8042"
irq:0  8 (        1) "rtc0"
irq:0  9 (        0) "acpi"
irq:0 12 (        4) "i8042"
irq:0 14 (    55287) "pata_atiixp"
irq:0 15 (        0) "pata_atiixp"
irq:0 16 (   752889) "ohci_hcd:usb3" "ohci_hcd:usb4" "HDA Intel"
irq:0 17 (        3) "ehci_hcd:usb1"
irq:0 18 (        3) "ohci_hcd:usb5" "ohci_hcd:usb6" "ohci_hcd:usb7"
irq:0 19 (        0) "ehci_hcd:usb2"
irq:0 2299 (        0) "fglrx[0]@PCI:1:5:0"
irq:0 2300 (    99139) "eth0"
irq:0 2301 (   105977) "ahci"
irq:0 2303 (   651159) "hpet2"
dma:1 4 "cascade"
----- misc resources end -----
>> parallel.1: pp mod
----- exec: "/sbin/rmmod parport_pc" -----
----- return code: ? -----
----- exec: "/sbin/modprobe parport_pc" -----
  WARNING: All config files need .conf: /etc/modprobe.d/vmxnet, it will be ignored in a future release.
  WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
----- return code: ? -----
----- exec: "/sbin/modprobe lp" -----
  WARNING: All config files need .conf: /etc/modprobe.d/vmxnet, it will be ignored in a future release.
  WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
----- return code: ? -----
>> parallel.2.1: lp read info
>> parallel.2.2: lp read info
>> parallel.2.3: lp read info
----- parallel info -----
----- parallel info end -----
>> block.1: block modules
----- exec: "/sbin/modprobe ide-cd_mod " -----
  WARNING: All config files need .conf: /etc/modprobe.d/vmxnet, it will be ignored in a future release.
  WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
  FATAL: Module ide_cd_mod not found.
----- return code: ? -----
----- exec: "/sbin/modprobe ide-disk " -----
  WARNING: All config files need .conf: /etc/modprobe.d/vmxnet, it will be ignored in a future release.
  WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
  FATAL: Module ide_disk not found.
----- return code: ? -----
----- exec: "/sbin/modprobe sr_mod " -----
  WARNING: All config files need .conf: /etc/modprobe.d/vmxnet, it will be ignored in a future release.
  WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
  FATAL: Module sr_mod not found.
----- return code: ? -----
----- exec: "/sbin/modprobe sd_mod " -----
  WARNING: All config files need .conf: /etc/modprobe.d/vmxnet, it will be ignored in a future release.
  WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
  FATAL: Module sd_mod not found.
----- return code: ? -----
>> block.2: sysfs drivers
----- sysfs driver list (id 0xbc92404d59f9bce6) -----
      serial8250: /devices/platform/serial8250
           i8042: /devices/platform/i8042
      parport_pc: module = parport_pc
 pcieport-driver: /devices/pci0000:00/0000:00:06.0
            ahci: /devices/pci0000:00/0000:00:11.0
            ahci: module = ahci
        sata_sil: module = sata_sil
         sata_nv: module = sata_nv
        pata_ali: module = pata_ali
     pata_atiixp: /devices/pci0000:00/0000:00:14.1
     pata_cs5536: module = pata_cs5536
     pata_it821x: module = pata_it821x
        ehci_hcd: /devices/pci0000:00/0000:00:12.2
        ehci_hcd: /devices/pci0000:00/0000:00:13.2
        ehci_hcd: module = ehci_hcd
        ohci_hcd: /devices/pci0000:00/0000:00:12.0
        ohci_hcd: /devices/pci0000:00/0000:00:12.1
        ohci_hcd: /devices/pci0000:00/0000:00:13.0
        ohci_hcd: /devices/pci0000:00/0000:00:13.1
        ohci_hcd: /devices/pci0000:00/0000:00:14.5
        uhci_hcd: module = uhci_hcd
      parport_pc: module = parport_pc
          shpchp: module = shpchp
     piix4_smbus: /devices/pci0000:00/0000:00:14.0
     piix4_smbus: module = i2c_piix4
           r8169: /devices/pci0000:00/0000:00:06.0/0000:02:00.0
           r8169: module = r8169
       HDA Intel: /devices/pci0000:00/0000:00:14.2
       HDA Intel: module = snd_hda_intel
       fglrx_pci: /devices/pci0000:00/0000:00:01.0/0000:01:05.0
       fglrx_pci: module = fglrx
        pci_root: /devices/LNXSYSTM:00/device:00/PNP0A03:00
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0C0F:00
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0C0F:01
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0C0F:02
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0C0F:03
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0C0F:04
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0C0F:05
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0C0F:06
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0C0F:07
             wmi: /devices/LNXSYSTM:00/PNP0C14:00
          button: /devices/LNXSYSTM:00/LNXPWRBN:00
          button: /devices/LNXSYSTM:00/device:00/PNP0C0C:00
       processor: /devices/LNXSYSTM:00/ACPI_CPU:00
       processor: /devices/LNXSYSTM:00/ACPI_CPU:01
       processor: /devices/LNXSYSTM:00/ACPI_CPU:02
       processor: /devices/LNXSYSTM:00/ACPI_CPU:03
          system: /devices/pnp0/00:01
          system: /devices/pnp0/00:0a
          system: /devices/pnp0/00:0b
          system: /devices/pnp0/00:0c
          system: /devices/pnp0/00:0d
          system: /devices/pnp0/00:0e
       i8042 kbd: /devices/pnp0/00:02
       i8042 aux: /devices/pnp0/00:03
        rtc_cmos: /devices/pnp0/00:05
              sd: /devices/pci0000:00/0000:00:11.0/host0/target0:0:0/0:0:0:0
              sr: /devices/pci0000:00/0000:00:14.1/host4/target4:0:0/4:0:0:0
           usbfs: module = usbcore
             hub: module = usbcore
             hub: /devices/pci0000:00/0000:00:12.2/usb1/1-0:1.0
             hub: /devices/pci0000:00/0000:00:13.2/usb2/2-0:1.0
             hub: /devices/pci0000:00/0000:00:12.0/usb3/3-0:1.0
             hub: /devices/pci0000:00/0000:00:12.1/usb4/4-0:1.0
             hub: /devices/pci0000:00/0000:00:13.0/usb5/5-0:1.0
             hub: /devices/pci0000:00/0000:00:13.1/usb6/6-0:1.0
             hub: /devices/pci0000:00/0000:00:14.5/usb7/7-0:1.0
             usb: /devices/pci0000:00/0000:00:12.2/usb1
             usb: /devices/pci0000:00/0000:00:13.2/usb2
             usb: /devices/pci0000:00/0000:00:12.0/usb3
             usb: /devices/pci0000:00/0000:00:12.1/usb4
             usb: /devices/pci0000:00/0000:00:13.0/usb5
             usb: /devices/pci0000:00/0000:00:13.1/usb6
             usb: /devices/pci0000:00/0000:00:14.5/usb7
             usb: /devices/pci0000:00/0000:00:12.1/usb4/4-2
             usb: /devices/pci0000:00/0000:00:12.1/usb4/4-3
          hiddev: module = usbhid
          usbhid: /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0
          usbhid: /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.1
          usbhid: /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0
          usbhid: /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.1
          usbhid: module = usbhid
         psmouse: module = psmouse
     generic-usb: module = usbhid
     generic-usb: /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0/0003:046D:C049.0001
     generic-usb: /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.1/0003:046D:C049.0002
     generic-usb: /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0/0003:046E:5542.0003
     generic-usb: /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.1/0003:046E:5542.0004
----- sysfs driver list end -----
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
     8        0  312571224 sda
     8        1  303499948 sda1
     8        2          1 sda2
     8        5    9068661 sda5
----- /proc/partitions end -----
disks:
  sda
partitions:
  sda1
  sda2
  sda5
>> block.5: get sysfs block dev data
-----  lsscsi -----
-----  lsscsi end -----
  block: name = md0, path = /class/block/md0
    dev = 9:0
    range = 1
  block: name = sr0, path = /class/block/sr0
    dev = 11:0
    range = 1
    block device: bus = scsi, bus_id = 4:0:0:0 driver = sr
      path = /devices/pci0000:00/0000:00:14.1/host4/target4:0:0/4:0:0:0
    vendor = HP
    model = DVD Writer 1040d
    rev = EH24
    type = 5
>> block.5: /dev/sr0
>> block.5.1: /dev/sr0 cache
  scsi cache: 0x00
  block: name = sda5, path = /class/block/sda5
    dev = 8:5
  block: name = sda2, path = /class/block/sda2
    dev = 8:2
  block: name = sda1, path = /class/block/sda1
    dev = 8:1
  block: name = sda, path = /class/block/sda
    dev = 8:0
    range = 16
    block device: bus = scsi, bus_id = 0:0:0:0 driver = sd
      path = /devices/pci0000:00/0000:00:11.0/host0/target0:0:0/0:0:0:0
    vendor = ATA
    model = WDC WD3200AAKS-0
    rev = 01.0
    type = 0
>> block.5: /dev/sda
>> block.5.1: /dev/sda geo
  dev = /dev/sda, fd = 4
  open ok, fd = 4
/dev/sda: ioctl(geo) ok
/dev/sda: ioctl(block size) ok
/dev/sda: ioctl(disk size) ok
>> block.5.2: /dev/sda serial
  serial id len: 20
  block: name = loop7, path = /class/block/loop7
    dev = 7:7
    range = 1
  block: name = loop6, path = /class/block/loop6
    dev = 7:6
    range = 1
  block: name = loop5, path = /class/block/loop5
    dev = 7:5
    range = 1
  block: name = loop4, path = /class/block/loop4
    dev = 7:4
    range = 1
  block: name = loop3, path = /class/block/loop3
    dev = 7:3
    range = 1
  block: name = loop2, path = /class/block/loop2
    dev = 7:2
    range = 1
  block: name = loop1, path = /class/block/loop1
    dev = 7:1
    range = 1
  block: name = loop0, path = /class/block/loop0
    dev = 7:0
    range = 1
  block: name = ram15, path = /class/block/ram15
    dev = 1:15
    range = 1
  block: name = ram14, path = /class/block/ram14
    dev = 1:14
    range = 1
  block: name = ram13, path = /class/block/ram13
    dev = 1:13
    range = 1
  block: name = ram12, path = /class/block/ram12
    dev = 1:12
    range = 1
  block: name = ram11, path = /class/block/ram11
    dev = 1:11
    range = 1
  block: name = ram10, path = /class/block/ram10
    dev = 1:10
    range = 1
  block: name = ram9, path = /class/block/ram9
    dev = 1:9
    range = 1
  block: name = ram8, path = /class/block/ram8
    dev = 1:8
    range = 1
  block: name = ram7, path = /class/block/ram7
    dev = 1:7
    range = 1
  block: name = ram6, path = /class/block/ram6
    dev = 1:6
    range = 1
  block: name = ram5, path = /class/block/ram5
    dev = 1:5
    range = 1
  block: name = ram4, path = /class/block/ram4
    dev = 1:4
    range = 1
  block: name = ram3, path = /class/block/ram3
    dev = 1:3
    range = 1
  block: name = ram2, path = /class/block/ram2
    dev = 1:2
    range = 1
  block: name = ram1, path = /class/block/ram1
    dev = 1:1
    range = 1
  block: name = ram0, path = /class/block/ram0
    dev = 1:0
    range = 1
>> scsi.1: scsi modules
----- exec: "/sbin/modprobe sg " -----
  WARNING: All config files need .conf: /etc/modprobe.d/vmxnet, it will be ignored in a future release.
  WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
  FATAL: Module sg not found.
----- return code: ? -----
>> scsi.2: scsi tape
sysfs: no such class: scsi_tape
>> scsi.3: scsi generic
  scsi: name = sg1, path = /class/scsi_generic/sg1
    dev = 21:1
    scsi device: bus_id = 4:0:0:0 driver = sr
      path = /devices/pci0000:00/0000:00:14.1/host4/target4:0:0/4:0:0:0
  scsi: name = sg0, path = /class/scsi_generic/sg0
    dev = 21:0
    scsi device: bus_id = 0:0:0:0 driver = sd
      path = /devices/pci0000:00/0000:00:11.0/host0/target0:0:0/0:0:0:0
>> usb.1: sysfs drivers
>> usb.2: usb
  usb dev: /devices/pci0000:00/0000:00:12.1/usb4/4-3
  usb dev: /devices/pci0000:00/0000:00:12.1/usb4/4-2
  usb dev: /devices/pci0000:00/0000:00:14.5/usb7
  usb dev: /devices/pci0000:00/0000:00:13.1/usb6
  usb dev: /devices/pci0000:00/0000:00:13.0/usb5
  usb dev: /devices/pci0000:00/0000:00:12.1/usb4
  usb dev: /devices/pci0000:00/0000:00:12.0/usb3
  usb dev: /devices/pci0000:00/0000:00:13.2/usb2
  usb dev: /devices/pci0000:00/0000:00:12.2/usb1
  usb device: name = 4-3:1.1
    path = /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.1
    modalias = "usb:v046Ep5542d0110dc00dsc00dp00ic03isc00ip00"
    bInterfaceNumber = 1
    bInterfaceClass = 3
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 4-3:1.1 @ /devices/pci0000:00/0000:00:12.1/usb4/4-3
    bDeviceClass = 0
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x046e
    idProduct = 0x5542
    manufacturer = "BTC"
    product = "USB Multimedia Keyboard"
    bcdDevice = 0110
    speed = "1.5"
  usb device: name = 4-3:1.0
    path = /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0
    modalias = "usb:v046Ep5542d0110dc00dsc00dp00ic03isc01ip01"
    bInterfaceNumber = 0
    bInterfaceClass = 3
    bInterfaceSubClass = 1
    bInterfaceProtocol = 1
    if: 4-3:1.0 @ /devices/pci0000:00/0000:00:12.1/usb4/4-3
    bDeviceClass = 0
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x046e
    idProduct = 0x5542
    manufacturer = "BTC"
    product = "USB Multimedia Keyboard"
    bcdDevice = 0110
    speed = "1.5"
  usb device: name = 4-3
    path = /devices/pci0000:00/0000:00:12.1/usb4/4-3
  usb device: name = 4-2:1.1
    path = /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.1
    modalias = "usb:v046DpC049d5200dc00dsc00dp00ic03isc00ip00"
    bInterfaceNumber = 1
    bInterfaceClass = 3
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 4-2:1.1 @ /devices/pci0000:00/0000:00:12.1/usb4/4-2
    bDeviceClass = 0
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x046d
    idProduct = 0xc049
    manufacturer = "Logitech"
    product = "USB Gaming Mouse"
    bcdDevice = 5200
    speed = "12"
  usb device: name = 4-2:1.0
    path = /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0
    modalias = "usb:v046DpC049d5200dc00dsc00dp00ic03isc01ip02"
    bInterfaceNumber = 0
    bInterfaceClass = 3
    bInterfaceSubClass = 1
    bInterfaceProtocol = 2
    if: 4-2:1.0 @ /devices/pci0000:00/0000:00:12.1/usb4/4-2
    bDeviceClass = 0
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x046d
    idProduct = 0xc049
    manufacturer = "Logitech"
    product = "USB Gaming Mouse"
    bcdDevice = 5200
    speed = "12"
  usb device: name = 4-2
    path = /devices/pci0000:00/0000:00:12.1/usb4/4-2
  usb device: name = 7-0:1.0
    path = /devices/pci0000:00/0000:00:14.5/usb7/7-0:1.0
    modalias = "usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 7-0:1.0 @ /devices/pci0000:00/0000:00:14.5/usb7
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x1d6b
    idProduct = 0x0001
    manufacturer = "Linux 2.6.28-16-generic ohci_hcd"
    product = "OHCI Host Controller"
    serial = "0000:00:14.5"
    bcdDevice = 0206
    speed = "12"
  usb device: name = usb7
    path = /devices/pci0000:00/0000:00:14.5/usb7
  usb device: name = 6-0:1.0
    path = /devices/pci0000:00/0000:00:13.1/usb6/6-0:1.0
    modalias = "usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 6-0:1.0 @ /devices/pci0000:00/0000:00:13.1/usb6
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x1d6b
    idProduct = 0x0001
    manufacturer = "Linux 2.6.28-16-generic ohci_hcd"
    product = "OHCI Host Controller"
    serial = "0000:00:13.1"
    bcdDevice = 0206
    speed = "12"
  usb device: name = usb6
    path = /devices/pci0000:00/0000:00:13.1/usb6
  usb device: name = 5-0:1.0
    path = /devices/pci0000:00/0000:00:13.0/usb5/5-0:1.0
    modalias = "usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 5-0:1.0 @ /devices/pci0000:00/0000:00:13.0/usb5
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x1d6b
    idProduct = 0x0001
    manufacturer = "Linux 2.6.28-16-generic ohci_hcd"
    product = "OHCI Host Controller"
    serial = "0000:00:13.0"
    bcdDevice = 0206
    speed = "12"
  usb device: name = usb5
    path = /devices/pci0000:00/0000:00:13.0/usb5
  usb device: name = 4-0:1.0
    path = /devices/pci0000:00/0000:00:12.1/usb4/4-0:1.0
    modalias = "usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 4-0:1.0 @ /devices/pci0000:00/0000:00:12.1/usb4
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x1d6b
    idProduct = 0x0001
    manufacturer = "Linux 2.6.28-16-generic ohci_hcd"
    product = "OHCI Host Controller"
    serial = "0000:00:12.1"
    bcdDevice = 0206
    speed = "12"
  usb device: name = usb4
    path = /devices/pci0000:00/0000:00:12.1/usb4
  usb device: name = 3-0:1.0
    path = /devices/pci0000:00/0000:00:12.0/usb3/3-0:1.0
    modalias = "usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 3-0:1.0 @ /devices/pci0000:00/0000:00:12.0/usb3
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x1d6b
    idProduct = 0x0001
    manufacturer = "Linux 2.6.28-16-generic ohci_hcd"
    product = "OHCI Host Controller"
    serial = "0000:00:12.0"
    bcdDevice = 0206
    speed = "12"
  usb device: name = usb3
    path = /devices/pci0000:00/0000:00:12.0/usb3
  usb device: name = 2-0:1.0
    path = /devices/pci0000:00/0000:00:13.2/usb2/2-0:1.0
    modalias = "usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 2-0:1.0 @ /devices/pci0000:00/0000:00:13.2/usb2
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x1d6b
    idProduct = 0x0002
    manufacturer = "Linux 2.6.28-16-generic ehci_hcd"
    product = "EHCI Host Controller"
    serial = "0000:00:13.2"
    bcdDevice = 0206
    speed = "480"
  usb device: name = usb2
    path = /devices/pci0000:00/0000:00:13.2/usb2
  usb device: name = 1-0:1.0
    path = /devices/pci0000:00/0000:00:12.2/usb1/1-0:1.0
    modalias = "usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 1-0:1.0 @ /devices/pci0000:00/0000:00:12.2/usb1
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x1d6b
    idProduct = 0x0002
    manufacturer = "Linux 2.6.28-16-generic ehci_hcd"
    product = "EHCI Host Controller"
    serial = "0000:00:12.2"
    bcdDevice = 0206
    speed = "480"
  usb device: name = usb1
    path = /devices/pci0000:00/0000:00:12.2/usb1
>> usb.3.1: joydev mod
>> usb.3.2: evdev mod
----- exec: "/sbin/modprobe evdev " -----
  WARNING: All config files need .conf: /etc/modprobe.d/vmxnet, it will be ignored in a future release.
  WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
  FATAL: Module evdev not found.
----- return code: ? -----
>> usb.3.3: input
  input: name = event6, path = /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.1/input/input6/event6
    dev = 13:70
    input device: bus = (null), bus_id = 4-3:1.1 driver = usbhid
      path = /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.1
  input: name = input6, path = /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.1/input/input6
    input device: bus = (null), bus_id = 4-3:1.1 driver = usbhid
      path = /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.1
  input: name = event5, path = /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0/input/input5/event5
    dev = 13:69
    input device: bus = (null), bus_id = 4-3:1.0 driver = usbhid
      path = /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0
  input: name = input5, path = /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0/input/input5
    input device: bus = (null), bus_id = 4-3:1.0 driver = usbhid
      path = /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0
  input: name = event3, path = /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0/input/input3/event3
    dev = 13:67
    input device: bus = (null), bus_id = 4-2:1.0 driver = usbhid
      path = /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0
  input: name = mouse1, path = /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0/input/input3/mouse1
    dev = 13:33
    input device: bus = (null), bus_id = 4-2:1.0 driver = usbhid
      path = /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0
  input: name = input3, path = /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0/input/input3
    input device: bus = (null), bus_id = 4-2:1.0 driver = usbhid
      path = /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0
  input: name = event2, path = /devices/virtual/input/input2/event2
    dev = 13:66
    input device: bus = (null), bus_id = input2 driver = (null)
      path = /devices/virtual/input/input2
  input: name = event1, path = /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1
    dev = 13:65
    input device: bus = (null), bus_id = PNP0C0C:00 driver = button
      path = /devices/LNXSYSTM:00/device:00/PNP0C0C:00
  input: name = event0, path = /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0/event0
    dev = 13:64
    input device: bus = (null), bus_id = LNXPWRBN:00 driver = button
      path = /devices/LNXSYSTM:00/LNXPWRBN:00
  input: name = mouse0, path = /devices/virtual/input/input2/mouse0
    dev = 13:32
    input device: bus = (null), bus_id = input2 driver = (null)
      path = /devices/virtual/input/input2
  input: name = mice, path = /devices/virtual/input/mice
    dev = 13:63
  input: name = input2, path = /devices/virtual/input/input2
  input: name = input1, path = /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
    input device: bus = (null), bus_id = PNP0C0C:00 driver = button
      path = /devices/LNXSYSTM:00/device:00/PNP0C0C:00
  input: name = input0, path = /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
    input device: bus = (null), bus_id = LNXPWRBN:00 driver = button
      path = /devices/LNXSYSTM:00/LNXPWRBN:00
>> usb.3.4: lp
>> usb.3.5: serial
>> edd.1: edd mod
----- exec: "/sbin/modprobe edd " -----
  WARNING: All config files need .conf: /etc/modprobe.d/vmxnet, it will be ignored in a future release.
  WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
  FATAL: Module edd not found.
----- return code: ? -----
>> edd.2: edd info
>> modem.1: serial
******  started child process 27406 (15s/120s)  ******
******  stopped child process 27406 (120s)  ******
>> mouse.2: serial
******  started child process 27407 (20s/20s)  ******
******  stopped child process 27407 (20s)  ******
>> input.1: joydev mod
>> input.1.1: evdev mod
----- exec: "/sbin/modprobe evdev " -----
  WARNING: All config files need .conf: /etc/modprobe.d/vmxnet, it will be ignored in a future release.
  WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
  FATAL: Module evdev not found.
----- return code: ? -----
>> input.2: input
----- /proc/bus/input/devices -----
  I: Bus=0019 Vendor=0000 Product=0002 Version=0000
  N: Name="Power Button (FF)"
  P: Phys=LNXPWRBN/button/input0
  S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
  U: Uniq=
  H: Handlers=kbd event0 
  B: EV=3
  B: KEY=100000 0 0 0
  
  I: Bus=0019 Vendor=0000 Product=0001 Version=0000
  N: Name="Power Button (CM)"
  P: Phys=PNP0C0C/button/input0
  S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
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
  
  I: Bus=0003 Vendor=046d Product=c049 Version=0111
  N: Name="Logitech USB Gaming Mouse"
  P: Phys=usb-0000:00:12.1-2/input0
  S: Sysfs=/devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0/input/input3
  U: Uniq=
  H: Handlers=mouse1 event3 
  B: EV=17
  B: KEY=ffff0000 0 0 0 0 0 0 0 0
  B: REL=143
  B: MSC=10
  
  I: Bus=0003 Vendor=046e Product=5542 Version=0110
  N: Name="BTC USB Multimedia Keyboard"
  P: Phys=usb-0000:00:12.1-3/input0
  S: Sysfs=/devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0/input/input5
  U: Uniq=
  H: Handlers=kbd event5 
  B: EV=120013
  B: KEY=10000 7 ff800000 7ff febeffdf f3cfffff ffffffff fffffffe
  B: MSC=10
  B: LED=7
  
  I: Bus=0003 Vendor=046e Product=5542 Version=0110
  N: Name="BTC USB Multimedia Keyboard"
  P: Phys=usb-0000:00:12.1-3/input1
  S: Sysfs=/devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.1/input/input6
  U: Uniq=
  H: Handlers=kbd event6 
  B: EV=13
  B: KEY=2000000 387a d801d6a1 1e0000 0 0 0
  B: MSC=10
  
----- /proc/bus/input/devices end -----
bus = 25, name = Power Button (FF)
  handlers = kbd event0
  key = 00100000000000000000000000000000
  mouse buttons = 0
  mouse wheels = 0
bus = 25, name = Power Button (CM)
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
bus = 3, name = Logitech USB Gaming Mouse
  handlers = mouse1 event3
  key = ffff00000000000000000000000000000000000000000000000000000000000000000000
  rel = 00000143
  mouse buttons = 8
  mouse wheels = 2
bus = 3, name = BTC USB Multimedia Keyboard
  handlers = kbd event5
  key = 0001000000000007ff800000000007fffebeffdff3cffffffffffffffffffffe
  mouse buttons = 0
  mouse wheels = 0
bus = 3, name = BTC USB Multimedia Keyboard
  handlers = kbd event6
  key = 020000000000387ad801d6a1001e0000000000000000000000000000
  mouse buttons = 0
  mouse wheels = 0
>> kbd.2: uml
>> cpu.1: cpuinfo
----- /proc/cpuinfo -----
  processor	: 0
  vendor_id	: AuthenticAMD
  cpu family	: 16
  model		: 5
  model name	: AMD Athlon(tm) II X4 620 Processor
  stepping	: 2
  cpu MHz		: 800.000
  cache size	: 512 KB
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
  cpuid level	: 5
  wp		: yes
  flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc pni monitor cx16 lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
  bogomips	: 5223.37
  clflush size	: 64
  power management: ts ttp tm stc 100mhzsteps hwpstate
  
  processor	: 1
  vendor_id	: AuthenticAMD
  cpu family	: 16
  model		: 5
  model name	: AMD Athlon(tm) II X4 620 Processor
  stepping	: 2
  cpu MHz		: 800.000
  cache size	: 512 KB
  physical id	: 0
  siblings	: 4
  core id		: 1
  cpu cores	: 4
  apicid		: 1
  initial apicid	: 1
  fdiv_bug	: no
  hlt_bug		: no
  f00f_bug	: no
  coma_bug	: no
  fpu		: yes
  fpu_exception	: yes
  cpuid level	: 5
  wp		: yes
  flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc pni monitor cx16 lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
  bogomips	: 5209.90
  clflush size	: 64
  power management: ts ttp tm stc 100mhzsteps hwpstate
  
  processor	: 2
  vendor_id	: AuthenticAMD
  cpu family	: 16
  model		: 5
  model name	: AMD Athlon(tm) II X4 620 Processor
  stepping	: 2
  cpu MHz		: 800.000
  cache size	: 512 KB
  physical id	: 0
  siblings	: 4
  core id		: 2
  cpu cores	: 4
  apicid		: 2
  initial apicid	: 2
  fdiv_bug	: no
  hlt_bug		: no
  f00f_bug	: no
  coma_bug	: no
  fpu		: yes
  fpu_exception	: yes
  cpuid level	: 5
  wp		: yes
  flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc pni monitor cx16 lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
  bogomips	: 5209.89
  clflush size	: 64
  power management: ts ttp tm stc 100mhzsteps hwpstate
  
  processor	: 3
  vendor_id	: AuthenticAMD
  cpu family	: 16
  model		: 5
  model name	: AMD Athlon(tm) II X4 620 Processor
  stepping	: 2
  cpu MHz		: 1400.000
  cache size	: 512 KB
  physical id	: 0
  siblings	: 4
  core id		: 3
  cpu cores	: 4
  apicid		: 3
  initial apicid	: 3
  fdiv_bug	: no
  hlt_bug		: no
  f00f_bug	: no
  coma_bug	: no
  fpu		: yes
  fpu_exception	: yes
  cpuid level	: 5
  wp		: yes
  flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc pni monitor cx16 lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
  bogomips	: 5209.89
  clflush size	: 64
  power management: ts ttp tm stc 100mhzsteps hwpstate
  
----- /proc/cpuinfo end -----
>> kbd.3: serial console
>> fb.1: read info
>> net.1: get network data
  net interface: name = eth0, path = /class/net/eth0
    type = 1
    carrier = 1
    hw_addr = 00:26:18:b8:da:07
    net device: path = /devices/pci0000:00/0000:00:06.0/0000:02:00.0
    net driver: name = r8169, path = /bus/pci/drivers/r8169
  net interface: name = lo, path = /class/net/lo
    type = 772
    carrier = 1
    hw_addr = 00:00:00:00:00:00
    GDRVINFO ethtool error: Operation not supported
>> pppoe.1: looking for pppoe
>> pppoe.2: discovery
Attempt number 1
eth0: Sending PADI packet
Timeout waiting for PADO packets
Attempt number 2
eth0: Sending PADI packet
Timeout waiting for PADO packets
>> wlan.1: detecting wlan features
>> wlan.2: assign udi
>> isdn.1: list
>> dsl.1: list
>> int.2: cdrom
>> int.3: media
>> int.4.1: /dev/sda
  read_block0: 512 bytes (4s, 999995us)
  mbr sig: 0x00013202
>> int.4: floppy
>> int.5: edd
>> int.5.1: bios
  bios ctrl 0: 33
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
-----  udevinfo end -----
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
  prop read: rdCR.DziBbWO85o5 (failed)
  old prop read: rdCR.DziBbWO85o5 (failed)
  prop read: rdCR.CxwsZFjVASF (failed)
  old prop read: rdCR.CxwsZFjVASF (failed)
  prop read: /org/freedesktop/Hal/devices/pci_10ec_8168 (failed)
  prop read: rBUF.grmZBEFhCxF (failed)
  old prop read: rBUF.grmZBEFhCxF (failed)
  prop read: /org/freedesktop/Hal/devices/pci_1002_9616 (failed)
  prop read: ul7N.Bj7y3mEqNmD (failed)
  old prop read: ul7N.Bj7y3mEqNmD (failed)
  prop read: /org/freedesktop/Hal/devices/pci_1022_1204 (failed)
  prop read: 60BX.Ww2F_h1WA4B (failed)
  old prop read: 60BX.Ww2F_h1WA4B (failed)
  prop read: /org/freedesktop/Hal/devices/pci_1022_1203 (failed)
  prop read: Fhhh.+V6VV7woehA (failed)
  old prop read: Fhhh.+V6VV7woehA (failed)
  prop read: /org/freedesktop/Hal/devices/pci_1022_1202 (failed)
  prop read: OMCs.U5Al0Zo57JA (failed)
  old prop read: OMCs.U5Al0Zo57JA (failed)
  prop read: /org/freedesktop/Hal/devices/pci_1022_1201 (failed)
  prop read: W1j0.zgD+X_gObw9 (failed)
  old prop read: W1j0.zgD+X_gObw9 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_1022_1200 (failed)
  prop read: fiDB.SGHF3QZh3Y9 (failed)
  old prop read: fiDB.SGHF3QZh3Y9 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_1002_4399 (failed)
  prop read: hB6S.0fuWihmxabA (failed)
  old prop read: hB6S.0fuWihmxabA (failed)
  prop read: /org/freedesktop/Hal/devices/pci_1002_4384 (failed)
  prop read: qscc.ULOo3yhA66C (failed)
  old prop read: qscc.ULOo3yhA66C (failed)
  prop read: /org/freedesktop/Hal/devices/pci_1002_439d (failed)
  prop read: yX7n.izfWtCFZk16 (failed)
  old prop read: yX7n.izfWtCFZk16 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_1002_4383 (failed)
  prop read: 5Dex.gK2Bvf1HDkE (failed)
  old prop read: 5Dex.gK2Bvf1HDkE (failed)
  prop read: /org/freedesktop/Hal/devices/pci_1002_439c (failed)
  prop read: Eu86.G2ybYGkeYC3 (failed)
  old prop read: Eu86.G2ybYGkeYC3 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_1002_4385 (failed)
  prop read: MZfG.Q0RvM63dRR3 (failed)
  old prop read: MZfG.Q0RvM63dRR3 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_1002_4396_0 (failed)
  prop read: 06bT.jPsMPYxld01 (failed)
  old prop read: 06bT.jPsMPYxld01 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_1002_4398_0 (failed)
  prop read: 9n5e.VEymD7fE3DA (failed)
  old prop read: 9n5e.VEymD7fE3DA (failed)
  prop read: /org/freedesktop/Hal/devices/pci_1002_4397_0 (failed)
  prop read: HSco._p+0lYXXXq9 (failed)
  old prop read: HSco._p+0lYXXXq9 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_1002_4396 (failed)
  prop read: x_X+.jPsMPYxld01 (failed)
  old prop read: x_X+.jPsMPYxld01 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_1002_4398 (failed)
  prop read: 4g2A.VEymD7fE3DA (failed)
  old prop read: 4g2A.VEymD7fE3DA (failed)
  prop read: /org/freedesktop/Hal/devices/pci_1002_4397 (failed)
  prop read: CLZK._p+0lYXXXq9 (failed)
  old prop read: CLZK._p+0lYXXXq9 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_1002_4390 (failed)
  prop read: 7EWs.WPBK7Mqox0D (failed)
  old prop read: 7EWs.WPBK7Mqox0D (failed)
  prop read: /org/freedesktop/Hal/devices/pci_1022_9606 (failed)
  prop read: H0_h.AQdh0Ungjl1 (failed)
  old prop read: H0_h.AQdh0Ungjl1 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_1043_9602 (failed)
  prop read: vSkL.d9cgQeHt+59 (failed)
  old prop read: vSkL.d9cgQeHt+59 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_1022_9600 (failed)
  prop read: qLht.OZzcKVFLBQA (failed)
  old prop read: qLht.OZzcKVFLBQA (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0c01 (failed)
  prop read: XB3B.gNN83gfynbD (failed)
  old prop read: XB3B.gNN83gfynbD (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0c02_3 (failed)
  prop read: 30p6.B+yZ9Ve8gC1 (failed)
  old prop read: 30p6.B+yZ9Ve8gC1 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0c02_2 (failed)
  prop read: cqY2.B+yZ9Ve8gC1 (failed)
  old prop read: cqY2.B+yZ9Ve8gC1 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0c02_1 (failed)
  prop read: 9fI_.B+yZ9Ve8gC1 (failed)
  old prop read: 9fI_.B+yZ9Ve8gC1 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0c02_0 (failed)
  prop read: iT2w.B+yZ9Ve8gC1 (failed)
  old prop read: iT2w.B+yZ9Ve8gC1 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0103 (failed)
  prop read: H20r.fG36JLVNse9 (failed)
  old prop read: H20r.fG36JLVNse9 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0700 (failed)
  prop read: qslm.yhTOLOXWEq7 (failed)
  old prop read: qslm.yhTOLOXWEq7 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0c04 (failed)
  prop read: NhVi.DE8RM9cWQQ8 (failed)
  old prop read: NhVi.DE8RM9cWQQ8 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0800 (failed)
  prop read: hEKD.bvKf3UMzZfE (failed)
  old prop read: hEKD.bvKf3UMzZfE (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0b00 (failed)
  prop read: E349.WYwRElrJa93 (failed)
  old prop read: E349.WYwRElrJa93 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0200 (failed)
  prop read: ntp4.ld94kxNGZf5 (failed)
  old prop read: ntp4.ld94kxNGZf5 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0f03 (failed)
  prop read: KiZ0.dF8oQb6hYJ9 (failed)
  old prop read: KiZ0.dF8oQb6hYJ9 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0303 (failed)
  prop read: tWJy.xhndlW9HXJ7 (failed)
  old prop read: tWJy.xhndlW9HXJ7 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0c02 (failed)
  prop read: QL3u.B+yZ9Ve8gC1 (failed)
  old prop read: QL3u.B+yZ9Ve8gC1 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0a03 (failed)
  prop read: z9pp.QBqTp8zQt87 (failed)
  old prop read: z9pp.QBqTp8zQt87 (failed)
  prop read: /org/freedesktop/Hal/devices/storage_model_DVD_Writer_1040d (failed)
  prop read: KD9E.bpnezxH_8DF (failed)
  old prop read: KD9E.bpnezxH_8DF (failed)
  prop read: /org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200AAKS__WD_WCAV24661468 (failed)
  prop read: 3OOL.mLwm7uOw48B (failed)
  old prop read: 3OOL.mLwm7uOw48B (failed)
  prop read: /org/freedesktop/Hal/devices/volume_uuid_10f79e5c_10ad_4f71_8b60_e828d5299810 (failed)
  prop read: bdUI.SE1wIdpsiiC (failed)
  old prop read: bdUI.SE1wIdpsiiC (failed)
  prop read: /org/freedesktop/Hal/devices/volume_part2_size_1024 (failed)
  prop read: 2pkM.SE1wIdpsiiC (failed)
  old prop read: 2pkM.SE1wIdpsiiC (failed)
  prop read: /org/freedesktop/Hal/devices/volume_uuid_3773c8ab_bc4b_48c0_9613_05934ff5e3e0 (failed)
  prop read: QLVZ.SE1wIdpsiiC (failed)
  old prop read: QLVZ.SE1wIdpsiiC (failed)
  prop read: /org/freedesktop/Hal/devices/usb_device_46e_5542_noserial_if1_logicaldev_input (failed)
  prop read: k_sa.tohDqUAqyUD (failed)
  old prop read: k_sa.tohDqUAqyUD (failed)
  prop read: /org/freedesktop/Hal/devices/usb_device_46e_5542_noserial_if0_logicaldev_input (failed)
  prop read: HpcW.8ic3TyME2S3 (failed)
  old prop read: HpcW.8ic3TyME2S3 (failed)
  prop read: /org/freedesktop/Hal/devices/usb_device_46d_c049_noserial_if1 (failed)
  prop read: IsEQ.00_XidZfc3E (failed)
  old prop read: IsEQ.00_XidZfc3E (failed)
  prop read: /org/freedesktop/Hal/devices/usb_device_46d_c049_noserial_if0 (failed)
  prop read: rg_L.3XHwq2zBd0B (failed)
  old prop read: rg_L.3XHwq2zBd0B (failed)
  prop read: /org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_14_5_if0 (failed)
  prop read: BSFT._WUAGn1cSY8 (failed)
  old prop read: BSFT._WUAGn1cSY8 (failed)
  prop read: /org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_1_if0 (failed)
  prop read: 7eqy.PaupGMfzSp8 (failed)
  old prop read: 7eqy.PaupGMfzSp8 (failed)
  prop read: /org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_0_if0 (failed)
  prop read: 2XnU.erpEvbsFWX1 (failed)
  old prop read: 2XnU.erpEvbsFWX1 (failed)
  prop read: /org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_1_if0 (failed)
  prop read: zPk0.uYbnlyRCGC6 (failed)
  old prop read: zPk0.uYbnlyRCGC6 (failed)
  prop read: /org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_0_if0 (failed)
  prop read: uIhY.7qWCOCfUJwE (failed)
  old prop read: uIhY.7qWCOCfUJwE (failed)
  prop read: /org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_13_2_if0 (failed)
  prop read: pBe4.3f5c44ENLJ9 (failed)
  old prop read: pBe4.3f5c44ENLJ9 (failed)
  prop read: /org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_12_2_if0 (failed)
  prop read: k4bc.YdoZZg0c8i6 (failed)
  old prop read: k4bc.YdoZZg0c8i6 (failed)
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
  prop read: usDW.ndpeucax6V1 (failed)
  old prop read: usDW.ndpeucax6V1 (failed)
  prop read: ZsBS.GQNx7L4uPNA (failed)
  old prop read: ZsBS.GQNx7L4uPNA (failed)
----- /proc/modules -----
  lp 17156 0 - Live 0xf7e59000
  parport_pc 40100 0 - Live 0xf842c000
  joydev 18368 0 - Live 0xf816b000
  st 44956 0 - Live 0xf845a000
  ppdev 15620 0 - Live 0xf7d99000
  parport 42220 3 lp,parport_pc,ppdev, Live 0xf7f73000
  binfmt_misc 16776 1 - Live 0xf7e39000
  ipmi_msghandler 42200 0 - Live 0xf9e5a000
  kvm_amd 33292 0 - Live 0xf9e40000
  kvm 153280 1 kvm_amd, Live 0xf9e0b000
  lock_dlm 22564 0 - Live 0xf92de000
  gfs2 363692 1 lock_dlm, Live 0xf9279000
  dlm 125200 1 lock_dlm, Live 0xf9212000
  configfs 33304 2 dlm, Live 0xf91dd000
  xt_tcpudp 11008 385 - Live 0xf850e000
  nf_conntrack_ipv4 21388 255 - Live 0xf8467000
  nf_defrag_ipv4 9984 1 nf_conntrack_ipv4, Live 0xf8455000
  xt_state 10112 255 - Live 0xf8448000
  ipt_REJECT 11136 4 - Live 0xf8387000
  xt_limit 10116 6 - Live 0xf7e7c000
  ipt_LOG 13700 6 - Live 0xf7e53000
  nf_conntrack_irc 13220 0 - Live 0xf7da0000
  nf_conntrack 72008 3 nf_conntrack_ipv4,xt_state,nf_conntrack_irc, Live 0xf7e3f000
  iptable_filter 10752 1 - Live 0xf7ce6000
  ip_tables 19600 1 iptable_filter, Live 0xf7cc7000
  x_tables 23044 6 xt_tcpudp,xt_state,ipt_REJECT,xt_limit,ipt_LOG,ip_tables, Live 0xf7c64000
  fglrx 2081668 59 - Live 0xf8173000 (P)
  snd_hda_intel 435252 3 - Live 0xf7ea2000
  snd_pcm_oss 46336 0 - Live 0xf7e06000
  snd_mixer_oss 22656 1 snd_pcm_oss, Live 0xf7dc8000
  agpgart 42696 1 fglrx, Live 0xf7db5000
  snd_pcm 83076 2 snd_hda_intel,snd_pcm_oss, Live 0xf7d5f000
  snd_seq_dummy 10756 0 - Live 0xf7d34000
  snd_seq_oss 37760 0 - Live 0xf7d05000
  snd_seq_midi 14336 0 - Live 0xf7ced000
  snd_rawmidi 29696 1 snd_seq_midi, Live 0xf7cdc000
  snd_seq_midi_event 15104 2 snd_seq_oss,snd_seq_midi, Live 0xf7cc1000
  snd_seq 56880 7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event, Live 0xf7cb1000
  snd_timer 29704 2 snd_pcm,snd_seq, Live 0xf7c84000
  snd_seq_device 14988 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq, Live 0xf7c5b000
  r8169 40836 0 - Live 0xf7ddb000
  i2c_piix4 18448 0 - Live 0xf7dc1000
  shpchp 40212 0 - Live 0xf7da9000
  mii 13312 1 r8169, Live 0xf7d93000
  snd 62756 16 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0xf7d78000
  soundcore 15200 1 snd, Live 0xf7d59000
  snd_page_alloc 16904 2 snd_hda_intel,snd_pcm, Live 0xf7d2d000
  psmouse 61972 0 - Live 0xf7d10000
  usbhid 42336 0 - Live 0xf7c6b000
----- /proc/modules end -----
  used irqs: 0,1,8,9,12,14,15,16,17,18,19,59,60,61,62,63
=========== end debug info ============
01: None 00.0: 10105 BIOS
  [Created at bios.176]
  Unique ID: rdCR.lZF+r4EgHp4
  Hardware Class: bios
  BIOS Keyboard LED Status:
    Scroll Lock: off
    Num Lock: off
    Caps Lock: off
  Base Memory: 635 kB
  PnP BIOS: @@@0000
  MP spec rev 1.4 info:
    OEM id: "ASUS"
    Product id: ""
    4 CPUs (0 disabled)
  BIOS32 Service Directory Entry: 0xf0010
  SMBIOS Version: 2.5
  BIOS Info: #0
    Vendor: "American Megatrends Inc."
    Version: "0801"
    Date: "06/02/2009"
    Start Address: 0xf0000
    ROM Size: 1024 kB
    Features: 0x0533000000017f8bde90
      ISA supported
      PCI supported
      PnP supported
      APM supported
      BIOS flashable
      BIOS shadowing allowed
      ESCD supported
      CD boot supported
      Selectable boot supported
      BIOS ROM socketed
      EDD spec supported
      1.2MB Floppy supported
      720kB Floppy supported
      2.88MB Floppy supported
      Print Screen supported
      8042 Keyboard Services supported
      Serial Services supported
      Printer Services supported
      CGA/Mono Video supported
      ACPI supported
      USB Legacy supported
      LS-120 boot supported
      ATAPI ZIP boot supported
      BIOS Boot Spec supported
  System Info: #1
    Manufacturer: "System manufacturer"
    Product: "System Product Name"
    Version: "System Version"
    Serial: "System Serial Number"
    UUID: undefined, but settable
    Wake-up: 0x06 (Power Switch)
  Board Info: #2
    Manufacturer: "ASUSTeK Computer INC."
    Product: "M3A76-CM"
    Version: "Rev X.0x"
    Serial: "MF7097G00401355"
    Asset Tag: "To Be Filled By O.E.M."
    Type: 0x0a (Motherboard)
    Features: 0x09
      Hosting Board
      Replaceable
    Location: "To Be Filled By O.E.M."
    Chassis: #3
  Chassis Info: #3
    Manufacturer: "Chassis Manufacture"
    Version: "Chassis Version"
    Serial: "Chassis Serial Number"
    Asset Tag: "Asset-1234567890"
    Type: 0x03 (Desktop)
    Bootup State: 0x03 (Safe)
    Power Supply State: 0x03 (Safe)
    Thermal State: 0x03 (Safe)
    Security Status: 0x03 (None)
    OEM Info: 0x00000001
  Processor Info: #4
    Socket: "AM2"
    Socket Type: 0x01 (Other)
    Socket Status: Populated
    Type: 0x03 (CPU)
    Family: 0xed (Other)
    Manufacturer: "AMD"
    Version: "AMD Athlon(tm) II X4 620 Processor"
    Serial: "To Be Filled By O.E.M."
    Asset Tag: "To Be Filled By O.E.M."
    Part Number: "To Be Filled By O.E.M."
    Processor ID: 0x178bfbff00100f52
    Status: 0x01 (Enabled)
    Voltage: 1.5 V
    External Clock: 200 MHz
    Max. Speed: 3200 MHz
    Current Speed: 2600 MHz
    L1 Cache: #5
    L2 Cache: #6
    L3 Cache: #7
  Cache Info: #5
    Designation: "L1-Cache"
    Level: L1
    State: Enabled
    Mode: 0x02 (Varies with Memory Address)
    Location: 0x00 (Internal, Not Socketed)
    ECC: 0x05 (Single-bit)
    Type: 0x04 (Data)
    Associativity: 0x05 (4-way Set-Associative)
    Max. Size: 512 kB
    Current Size: 512 kB
    Supported SRAM Types: 0x0010 (Pipeline Burst)
    Current SRAM Type: 0x0010 (Pipeline Burst)
  Cache Info: #6
    Designation: "L2-Cache"
    Level: L2
    State: Enabled
    Mode: 0x02 (Varies with Memory Address)
    Location: 0x00 (Internal, Not Socketed)
    ECC: 0x05 (Single-bit)
    Type: 0x05 (Unified)
    Associativity: 0x05 (4-way Set-Associative)
    Max. Size: 2048 kB
    Current Size: 2048 kB
    Supported SRAM Types: 0x0010 (Pipeline Burst)
    Current SRAM Type: 0x0010 (Pipeline Burst)
  Cache Info: #7
    Designation: "L3-Cache"
    Level: L3
    State: Disabled
    Mode: 0x03 (Unknown)
    Location: 0x00 (Internal, Not Socketed)
    ECC: 0x02 (Unknown)
    Type: 0x02 (Unknown)
    Associativity: 0x02 (Unknown)
    Supported SRAM Types: 0x0002 (Unknown)
    Current SRAM Type: 0x0002 (Unknown)
  Port Connector: #8
    Type: 0x0d (Keyboard Port)
    Internal Designator: "PS/2 KB/MS"
    External Designator: "PS/2 KB/MS"
    External Connector: 0x0f (PS/2)
  Port Connector: #9
    Type: 0x10 (USB)
    Internal Designator: "USB1"
    External Designator: "USB1"
    External Connector: 0x12 (Access Bus [USB])
  Port Connector: #10
    Type: 0x10 (USB)
    Internal Designator: "USB2"
    External Designator: "USB2"
    External Connector: 0x12 (Access Bus [USB])
  Port Connector: #11
    Type: 0x10 (USB)
    Internal Designator: "USB3"
    External Designator: "USB3"
    External Connector: 0x12 (Access Bus [USB])
  Port Connector: #12
    Type: 0x10 (USB)
    Internal Designator: "USB4"
    External Designator: "USB4"
    External Connector: 0x12 (Access Bus [USB])
  Port Connector: #13
    Type: 0x10 (USB)
    Internal Designator: "USB5"
    External Designator: "USB5"
    External Connector: 0x12 (Access Bus [USB])
  Port Connector: #14
    Type: 0x10 (USB)
    Internal Designator: "USB6"
    External Designator: "USB6"
    External Connector: 0x12 (Access Bus [USB])
  Port Connector: #15
    Type: 0x05 (Parallel Port ECP/EPP)
    Internal Designator: "LPT 1"
    External Designator: "LPT 1"
    External Connector: 0x04 (DB-25 pin male)
  Port Connector: #16
    Type: 0x09 (Serial Port 16550A Compatible)
    Internal Designator: "COM 1"
    External Designator: "COM 1"
    External Connector: 0x08 (DB-9 pin male)
  Port Connector: #17
    Type: 0x1f (Network Port)
    Internal Designator: "LAN"
    External Designator: "LAN"
    External Connector: 0x0b (RJ-45)
  Port Connector: #18
    Type: 0x1d (Audio Port)
    Internal Designator: "Audio_Line_In"
    External Designator: "Audio_Line_In"
    External Connector: 0x1f (Mini-jack [headphones])
  Port Connector: #19
    Type: 0x1d (Audio Port)
    Internal Designator: "Audio_Line_Out"
    External Designator: "Audio_Line_Out"
    External Connector: 0x1f (Mini-jack [headphones])
  Port Connector: #20
    Type: 0x1d (Audio Port)
    Internal Designator: "Audio_Mic_In"
    External Designator: "Audio_Mic_In"
    External Connector: 0x1f (Mini-jack [headphones])
  Port Connector: #21
    Type: 0x1d (Audio Port)
    Internal Designator: "Audio_Center/Sub"
    External Designator: "Audio_Center/Sub"
    External Connector: 0x1f (Mini-jack [headphones])
  Port Connector: #22
    Type: 0x1d (Audio Port)
    Internal Designator: "Audio_Rear"
    External Designator: "Audio_Rear"
    External Connector: 0x1f (Mini-jack [headphones])
  Port Connector: #23
    Type: 0x1d (Audio Port)
    Internal Designator: "Audio_Side"
    External Designator: "Audio_Side"
    External Connector: 0x1f (Mini-jack [headphones])
  Port Connector: #24
    Type: 0xff (Other)
    Internal Designator: "DVI"
    External Designator: "DVI port"
    External Connector: 0xff (Other)
  Port Connector: #25
    Type: 0xff (Other)
    Internal Designator: "PRI IDE"
    Internal Connector: 0x16 (On Board IDE)
  Port Connector: #26
    Type: 0xff (Other)
    Internal Designator: "SB_SATA1"
    Internal Connector: 0xff (Other)
  Port Connector: #27
    Type: 0xff (Other)
    Internal Designator: "SB_SATA2"
    Internal Connector: 0xff (Other)
  Port Connector: #28
    Type: 0xff (Other)
    Internal Designator: "SB_SATA3"
    Internal Connector: 0xff (Other)
  Port Connector: #29
    Type: 0xff (Other)
    Internal Designator: "SB_SATA4"
    Internal Connector: 0xff (Other)
  Port Connector: #30
    Type: 0xff (Other)
    Internal Designator: "SB_SATA5"
    Internal Connector: 0xff (Other)
  Port Connector: #31
    Type: 0xff (Other)
    Internal Designator: "SB_SATA6"
    Internal Connector: 0xff (Other)
  Port Connector: #32
    Type: 0xff (Other)
    Internal Designator: "CPU FAN"
    Internal Connector: 0xff (Other)
  Port Connector: #33
    Type: 0xff (Other)
    Internal Designator: "CHA FAN"
    Internal Connector: 0xff (Other)
  Port Connector: #34
    Type: 0x10 (USB)
    Internal Designator: "USB7"
    Internal Connector: 0x12 (Access Bus [USB])
  Port Connector: #35
    Type: 0x10 (USB)
    Internal Designator: "USB8"
    Internal Connector: 0x12 (Access Bus [USB])
  Port Connector: #36
    Type: 0x10 (USB)
    Internal Designator: "USB9"
    Internal Connector: 0x12 (Access Bus [USB])
  Port Connector: #37
    Type: 0x10 (USB)
    Internal Designator: "USB10"
    Internal Connector: 0x12 (Access Bus [USB])
  Port Connector: #38
    Type: 0x10 (USB)
    Internal Designator: "USB11"
    Internal Connector: 0x12 (Access Bus [USB])
  Port Connector: #39
    Type: 0x10 (USB)
    Internal Designator: "USB12"
    Internal Connector: 0x12 (Access Bus [USB])
  Port Connector: #40
    Type: 0xff (Other)
    Internal Designator: "PANEL"
    Internal Connector: 0xff (Other)
  Port Connector: #41
    Type: 0xff (Other)
    Internal Designator: "SPDIF OUT"
    Internal Connector: 0xff (Other)
  Port Connector: #42
    Type: 0xff (Other)
    Internal Designator: "AAFP"
    Internal Connector: 0xff (Other)
  Port Connector: #43
    Type: 0x1d (Audio Port)
    Internal Designator: "CD"
    Internal Connector: 0x1c (On Board Sound Input from CD-ROM)
  System Slot: #44
    Designation: "PCIE1X"
    Type: 0xa5 (Other)
    Bus Width: 0x05 (32 bit)
    Status: 0x04 (In Use)
    Length: 0x03 (Short)
    Slot ID: 4
    Characteristics: 0x010c (3.3 V, Shared, PME#)
  System Slot: #45
    Designation: "PCIE16X"
    Type: 0xa5 (Other)
    Bus Width: 0x05 (32 bit)
    Status: 0x03 (Available)
    Length: 0x03 (Short)
    Slot ID: 2
    Characteristics: 0x010c (3.3 V, Shared, PME#)
  System Slot: #46
    Designation: "PCI1"
    Type: 0x06 (PCI)
    Bus Width: 0x05 (32 bit)
    Status: 0x03 (Available)
    Length: 0x03 (Short)
    Slot ID: 3
    Characteristics: 0x010c (3.3 V, Shared, PME#)
  System Slot: #47
    Designation: "PCI2"
    Type: 0x06 (PCI)
    Bus Width: 0x05 (32 bit)
    Status: 0x03 (Available)
    Length: 0x03 (Short)
    Slot ID: 1
    Characteristics: 0x010c (3.3 V, Shared, PME#)
  On Board Devices: #48
    Other: "To Be Filled By O.E.M."
  On Board Devices: #49
    Ethernet: "To Be Filled By O.E.M."
  On Board Devices: #50
    Sound: "To Be Filled By O.E.M."
  On Board Devices: #51
    Other: "To Be Filled By O.E.M."
  OEM Strings: #52
    002618B8DA07
    To Be Filled By O.E.M.
    To Be Filled By O.E.M.
    To Be Filled By O.E.M.
  Language Info: #53
    Languages: en|US|iso8859-1
    Current: en|US|iso8859-1
  Type 15 Record: #54
    Data 00: 0f 23 36 00 04 00 00 00 02 00 02 00 00 00 00 00
    Data 10: 6a 04 6c 04 00 06 02 ff ff ff ff ff ff ff ff ff
    Data 20: ff ff ff
  Physical Memory Array: #55
    Use: 0x03 (System memory)
    Location: 0x03 (Motherboard)
    Slots: 4
    Max. Size: 8 GB
    ECC: 0x03 (None)
  Memory Array Mapping: #56
    Memory Array: #55
    Partition Width: 1
    Start Address: 0x00000000
    End Address: 0xd0000000
  Memory Device: #57
    Location: "DIMM0"
    Bank: "BANK0"
    Manufacturer: "Manufacturer0"
    Serial: "SerNum0"
    Asset Tag: "AssetTagNum0"
    Part Number: "PartNum0"
    Memory Array: #55
    Form Factor: 0x09 (DIMM)
    Type: 0x13 (Other)
    Type Detail: 0x0080 (Synchronous)
    Data Width: 64 bits
    Size: 2 GB
    Speed: 800 MHz
  Memory Device Mapping: #58
    Memory Device: #57
    Array Mapping: #56
    Row: 1
    Interleave Pos: 0
    Interleaved Depth: 0
    Start Address: 0x00000000
    End Address: 0x80000000
  Memory Device: #59
    Location: "DIMM1"
    Bank: "BANK1"
    Manufacturer: "Manufacturer1"
    Serial: "SerNum1"
    Asset Tag: "AssetTagNum1"
    Part Number: "PartNum1"
    Memory Array: #55
    Form Factor: 0x09 (DIMM)
    Type: 0x13 (Other)
    Type Detail: 0x0080 (Synchronous)
    Data Width: 64 bits
    Size: 2 GB
    Speed: 800 MHz
  Memory Device Mapping: #60
    Memory Device: #59
    Array Mapping: #56
    Row: 1
    Interleave Pos: 0
    Interleaved Depth: 0
    Start Address: 0x0000000080000000
    End Address: 0x0000000100000000
  Memory Device: #61
    Location: "DIMM2"
    Bank: "BANK2"
    Manufacturer: "Manufacturer2"
    Serial: "SerNum2"
    Asset Tag: "AssetTagNum2"
    Part Number: "PartNum2"
    Memory Array: #55
    Form Factor: 0x09 (DIMM)
    Type: 0x02 (Unknown)
    Data Width: 0 bits
    Size: No Memory Installed
  Inactive Record: #62
    Data 00: 7e 13 3e 00 00 00 00 00 00 00 00 00 3d 00 38 00
    Data 10: 01 00 00
  Memory Device: #63
    Location: "DIMM3"
    Bank: "BANK3"
    Manufacturer: "Manufacturer3"
    Serial: "SerNum3"
    Asset Tag: "AssetTagNum3"
    Part Number: "PartNum3"
    Memory Array: #55
    Form Factor: 0x09 (DIMM)
    Type: 0x02 (Unknown)
    Data Width: 0 bits
    Size: No Memory Installed
  Inactive Record: #64
    Data 00: 7e 13 40 00 00 00 00 00 00 00 00 00 3f 00 38 00
    Data 10: 01 00 00
  Type 32 Record: #65
    Data 00: 20 14 41 00 00 00 00 00 00 00 00 00 00 00 00 00
    Data 10: 00 00 00 00
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
  IRQ: 0 (73 events)
  Config Status: cfg=new, avail=yes, need=no, active=unknown

07: None 00.0: 0900 Keyboard controller
  [Created at misc.251]
  Unique ID: rdCR.9N+EecqykME
  Hardware Class: unknown
  Model: "Keyboard controller"
  I/O Port: 0x60 (rw)
  I/O Port: 0x64 (rw)
  Config Status: cfg=new, avail=yes, need=no, active=unknown

08: None 00.0: 10400 PS/2 Controller
  [Created at misc.304]
  Unique ID: rdCR.DziBbWO85o5
  Hardware Class: unknown
  Model: "PS/2 Controller"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

13: None 00.0: 10102 Main Memory
  [Created at memory.61]
  Unique ID: rdCR.CxwsZFjVASF
  Hardware Class: memory
  Model: "Main Memory"
  Memory Range: 0x00000000-0xbd00cfff (rw)
  Memory Size: 3 GB
  Config Status: cfg=new, avail=yes, need=no, active=unknown

14: PCI 200.0: 0200 Ethernet controller
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_10ec_8168
  Unique ID: rBUF.grmZBEFhCxF
  Parent ID: H0_h.AQdh0Ungjl1
  SysFS ID: /devices/pci0000:00/0000:00:06.0/0000:02:00.0
  SysFS BusID: 0000:02:00.0
  Hardware Class: network
  Model: "Realtek RTL8111/8168B PCI Express Gigabit Ethernet controller"
  Vendor: pci 0x10ec "Realtek Semiconductor Co., Ltd."
  Device: pci 0x8168 "RTL8111/8168B PCI Express Gigabit Ethernet controller"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x8367 
  Revision: 0x02
  Driver: "r8169"
  Driver Modules: "r8169"
  Device File: eth0
  I/O Ports: 0xe800-0xe8ff (rw)
  Memory Range: 0xfafff000-0xfaffffff (rw,prefetchable)
  Memory Range: 0xfafe0000-0xfafeffff (rw,prefetchable)
  Memory Range: 0xfbff0000-0xfbffffff (ro,prefetchable,disabled)
  IRQ: 2300 (99139 events)
  HW Address: 00:26:18:b8:da:07
  Link detected: yes
  Module Alias: "pci:v000010ECd00008168sv00001043sd00008367bc02sc00i00"
  Driver Info #0:
    Driver Status: r8169 is active
    Driver Activation Cmd: "modprobe r8169"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #34 (PCI bridge)

15: PCI 105.0: 0300 VGA compatible controller (VGA)
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_1002_9616
  Unique ID: ul7N.Bj7y3mEqNmD
  Parent ID: vSkL.d9cgQeHt+59
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:05.0
  SysFS BusID: 0000:01:05.0
  Hardware Class: graphics card
  Model: "ATI VGA compatible controller"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x9616 
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x8388 
  Driver: "fglrx_pci"
  Driver Modules: "fglrx"
  Memory Range: 0xd0000000-0xdfffffff (rw,prefetchable)
  I/O Ports: 0xd000-0xdfff (rw)
  Memory Range: 0xfbef0000-0xfbefffff (rw,non-prefetchable)
  Memory Range: 0xfbd00000-0xfbdfffff (rw,non-prefetchable)
  IRQ: 2299 (no events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00001002d00009616sv00001043sd00008388bc03sc00i00"
  Driver Info #0:
    Driver Status: fglrx is active
    Driver Activation Cmd: "modprobe fglrx"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #35 (PCI bridge)

16: PCI 18.4: 0600 Host bridge
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_1022_1204
  Unique ID: 60BX.Ww2F_h1WA4B
  SysFS ID: /devices/pci0000:00/0000:00:18.4
  SysFS BusID: 0000:00:18.4
  Hardware Class: bridge
  Model: "AMD Family 10h [Opteron, Athlon64, Sempron] Link Control"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x1204 "Family 10h [Opteron, Athlon64, Sempron] Link Control"
  Module Alias: "pci:v00001022d00001204sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

17: PCI 18.3: 0600 Host bridge
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_1022_1203
  Unique ID: Fhhh.+V6VV7woehA
  SysFS ID: /devices/pci0000:00/0000:00:18.3
  SysFS BusID: 0000:00:18.3
  Hardware Class: bridge
  Model: "AMD Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x1203 "Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control"
  Module Alias: "pci:v00001022d00001203sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

18: PCI 18.2: 0600 Host bridge
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_1022_1202
  Unique ID: OMCs.U5Al0Zo57JA
  SysFS ID: /devices/pci0000:00/0000:00:18.2
  SysFS BusID: 0000:00:18.2
  Hardware Class: bridge
  Model: "AMD Family 10h [Opteron, Athlon64, Sempron] DRAM Controller"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x1202 "Family 10h [Opteron, Athlon64, Sempron] DRAM Controller"
  Module Alias: "pci:v00001022d00001202sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

19: PCI 18.1: 0600 Host bridge
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_1022_1201
  Unique ID: W1j0.zgD+X_gObw9
  SysFS ID: /devices/pci0000:00/0000:00:18.1
  SysFS BusID: 0000:00:18.1
  Hardware Class: bridge
  Model: "AMD Family 10h [Opteron, Athlon64, Sempron] Address Map"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x1201 "Family 10h [Opteron, Athlon64, Sempron] Address Map"
  Module Alias: "pci:v00001022d00001201sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

20: PCI 18.0: 0600 Host bridge
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_1022_1200
  Unique ID: fiDB.SGHF3QZh3Y9
  SysFS ID: /devices/pci0000:00/0000:00:18.0
  SysFS BusID: 0000:00:18.0
  Hardware Class: bridge
  Model: "AMD Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x1200 "Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration"
  Module Alias: "pci:v00001022d00001200sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

21: PCI 14.5: 0c03 USB Controller (OHCI)
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_1002_4399
  Unique ID: hB6S.0fuWihmxabA
  SysFS ID: /devices/pci0000:00/0000:00:14.5
  SysFS BusID: 0000:00:14.5
  Hardware Class: usb controller
  Model: "ATI SB700/SB800 USB OHCI2 Controller"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x4399 "SB700/SB800 USB OHCI2 Controller"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x8389 
  Driver: "ohci_hcd"
  Memory Range: 0xfbcf9000-0xfbcf9fff (rw,non-prefetchable)
  IRQ: 18 (3 events)
  Module Alias: "pci:v00001002d00004399sv00001043sd00008389bc0Csc03i10"
  Driver Info #0:
    Driver Status: ohci-hcd is not active
    Driver Activation Cmd: "modprobe ohci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

22: PCI 14.4: 0604 PCI bridge (Subtractive decode)
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_1002_4384
  Unique ID: qscc.ULOo3yhA66C
  SysFS ID: /devices/pci0000:00/0000:00:14.4
  SysFS BusID: 0000:00:14.4
  Hardware Class: bridge
  Model: "ATI SBx00 PCI to PCI Bridge"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x4384 "SBx00 PCI to PCI Bridge"
  Module Alias: "pci:v00001002d00004384sv00000000sd00000000bc06sc04i01"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

23: PCI 14.3: 0601 ISA bridge
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_1002_439d
  Unique ID: yX7n.izfWtCFZk16
  SysFS ID: /devices/pci0000:00/0000:00:14.3
  SysFS BusID: 0000:00:14.3
  Hardware Class: bridge
  Model: "ATI SB700/SB800 LPC host controller"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x439d "SB700/SB800 LPC host controller"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x8389 
  Module Alias: "pci:v00001002d0000439Dsv00001043sd00008389bc06sc01i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

24: PCI 14.2: 0403 Audio device
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_1002_4383
  Unique ID: 5Dex.gK2Bvf1HDkE
  SysFS ID: /devices/pci0000:00/0000:00:14.2
  SysFS BusID: 0000:00:14.2
  Hardware Class: sound
  Model: "ATI SBx00 Azalia"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x4383 "SBx00 Azalia"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x82ea 
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfbcf4000-0xfbcf7fff (rw,non-prefetchable)
  IRQ: 16 (752889 events)
  Module Alias: "pci:v00001002d00004383sv00001043sd000082EAbc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

25: PCI 14.1: 0101 IDE interface
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_1002_439c
  Unique ID: Eu86.G2ybYGkeYC3
  SysFS ID: /devices/pci0000:00/0000:00:14.1
  SysFS BusID: 0000:00:14.1
  Hardware Class: storage
  Model: "ATI SB700/SB800 IDE Controller"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x439c "SB700/SB800 IDE Controller"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x8389 
  Driver: "pata_atiixp"
  I/O Ports: 0x1f0-0x1f7 (rw)
  I/O Port: 0x3f6 (rw)
  I/O Ports: 0x170-0x177 (rw)
  I/O Port: 0x376 (rw)
  I/O Ports: 0xff00-0xff0f (rw)
  IRQ: 16 (752889 events)
  Module Alias: "pci:v00001002d0000439Csv00001043sd00008389bc01sc01i8a"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

26: PCI 14.0: 0c05 SMBus
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_1002_4385
  Unique ID: MZfG.Q0RvM63dRR3
  SysFS ID: /devices/pci0000:00/0000:00:14.0
  SysFS BusID: 0000:00:14.0
  Hardware Class: unknown
  Model: "ATI SBx00 SMBus Controller"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x4385 "SBx00 SMBus Controller"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x8389 
  Revision: 0x3c
  Driver: "piix4_smbus"
  Driver Modules: "i2c_piix4"
  Module Alias: "pci:v00001002d00004385sv00001043sd00008389bc0Csc05i00"
  Driver Info #0:
    Driver Status: i2c_piix4 is active
    Driver Activation Cmd: "modprobe i2c_piix4"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

27: PCI 13.2: 0c03 USB Controller (EHCI)
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_1002_4396_0
  Unique ID: 06bT.jPsMPYxld01
  SysFS ID: /devices/pci0000:00/0000:00:13.2
  SysFS BusID: 0000:00:13.2
  Hardware Class: usb controller
  Model: "ATI SB700/SB800 USB EHCI Controller"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x4396 "SB700/SB800 USB EHCI Controller"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x8389 
  Driver: "ehci_hcd"
  Driver Modules: "ehci_hcd"
  Memory Range: 0xfbcfa800-0xfbcfa8ff (rw,non-prefetchable)
  IRQ: 19 (no events)
  Module Alias: "pci:v00001002d00004396sv00001043sd00008389bc0Csc03i20"
  Driver Info #0:
    Driver Status: ehci-hcd is not active
    Driver Activation Cmd: "modprobe ehci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

28: PCI 13.1: 0c03 USB Controller (OHCI)
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_1002_4398_0
  Unique ID: 9n5e.VEymD7fE3DA
  SysFS ID: /devices/pci0000:00/0000:00:13.1
  SysFS BusID: 0000:00:13.1
  Hardware Class: usb controller
  Model: "ATI SB700/SB800 USB OHCI1 Controller"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x4398 "SB700/SB800 USB OHCI1 Controller"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x8389 
  Driver: "ohci_hcd"
  Memory Range: 0xfbcfb000-0xfbcfbfff (rw,non-prefetchable)
  IRQ: 18 (3 events)
  Module Alias: "pci:v00001002d00004398sv00001043sd00008389bc0Csc03i10"
  Driver Info #0:
    Driver Status: ohci-hcd is not active
    Driver Activation Cmd: "modprobe ohci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

29: PCI 13.0: 0c03 USB Controller (OHCI)
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_1002_4397_0
  Unique ID: HSco._p+0lYXXXq9
  SysFS ID: /devices/pci0000:00/0000:00:13.0
  SysFS BusID: 0000:00:13.0
  Hardware Class: usb controller
  Model: "ATI SB700/SB800 USB OHCI0 Controller"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x4397 "SB700/SB800 USB OHCI0 Controller"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x8389 
  Driver: "ohci_hcd"
  Memory Range: 0xfbcfc000-0xfbcfcfff (rw,non-prefetchable)
  IRQ: 18 (3 events)
  Module Alias: "pci:v00001002d00004397sv00001043sd00008389bc0Csc03i10"
  Driver Info #0:
    Driver Status: ohci-hcd is not active
    Driver Activation Cmd: "modprobe ohci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

30: PCI 12.2: 0c03 USB Controller (EHCI)
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_1002_4396
  Unique ID: x_X+.jPsMPYxld01
  SysFS ID: /devices/pci0000:00/0000:00:12.2
  SysFS BusID: 0000:00:12.2
  Hardware Class: usb controller
  Model: "ATI SB700/SB800 USB EHCI Controller"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x4396 "SB700/SB800 USB EHCI Controller"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x8389 
  Driver: "ehci_hcd"
  Driver Modules: "ehci_hcd"
  Memory Range: 0xfbcff000-0xfbcff0ff (rw,non-prefetchable)
  IRQ: 17 (3 events)
  Module Alias: "pci:v00001002d00004396sv00001043sd00008389bc0Csc03i20"
  Driver Info #0:
    Driver Status: ehci-hcd is not active
    Driver Activation Cmd: "modprobe ehci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

31: PCI 12.1: 0c03 USB Controller (OHCI)
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_1002_4398
  Unique ID: 4g2A.VEymD7fE3DA
  SysFS ID: /devices/pci0000:00/0000:00:12.1
  SysFS BusID: 0000:00:12.1
  Hardware Class: usb controller
  Model: "ATI SB700/SB800 USB OHCI1 Controller"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x4398 "SB700/SB800 USB OHCI1 Controller"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x8389 
  Driver: "ohci_hcd"
  Memory Range: 0xfbcfd000-0xfbcfdfff (rw,non-prefetchable)
  IRQ: 16 (752889 events)
  Module Alias: "pci:v00001002d00004398sv00001043sd00008389bc0Csc03i10"
  Driver Info #0:
    Driver Status: ohci-hcd is not active
    Driver Activation Cmd: "modprobe ohci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

32: PCI 12.0: 0c03 USB Controller (OHCI)
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_1002_4397
  Unique ID: CLZK._p+0lYXXXq9
  SysFS ID: /devices/pci0000:00/0000:00:12.0
  SysFS BusID: 0000:00:12.0
  Hardware Class: usb controller
  Model: "ATI SB700/SB800 USB OHCI0 Controller"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x4397 "SB700/SB800 USB OHCI0 Controller"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x8389 
  Driver: "ohci_hcd"
  Memory Range: 0xfbcfe000-0xfbcfefff (rw,non-prefetchable)
  IRQ: 16 (752889 events)
  Module Alias: "pci:v00001002d00004397sv00001043sd00008389bc0Csc03i10"
  Driver Info #0:
    Driver Status: ohci-hcd is not active
    Driver Activation Cmd: "modprobe ohci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

33: PCI 11.0: 0106 SATA controller (AHCI 1.0)
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_1002_4390
  Unique ID: 7EWs.WPBK7Mqox0D
  SysFS ID: /devices/pci0000:00/0000:00:11.0
  SysFS BusID: 0000:00:11.0
  Hardware Class: storage
  Model: "ATI SB700/SB800 SATA Controller [IDE mode]"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x4390 "SB700/SB800 SATA Controller [IDE mode]"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x8389 
  Driver: "ahci"
  Driver Modules: "ahci"
  I/O Ports: 0xc000-0xc007 (rw)
  I/O Ports: 0xb000-0xb003 (rw)
  I/O Ports: 0xa000-0xa007 (rw)
  I/O Ports: 0x9000-0x9003 (rw)
  I/O Ports: 0x8000-0x800f (rw)
  Memory Range: 0xfbcff800-0xfbcffbff (rw,non-prefetchable)
  IRQ: 2301 (105977 events)
  Module Alias: "pci:v00001002d00004390sv00001043sd00008389bc01sc06i01"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

34: PCI 06.0: 0604 PCI bridge (Normal decode)
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_1022_9606
  Unique ID: H0_h.AQdh0Ungjl1
  SysFS ID: /devices/pci0000:00/0000:00:06.0
  SysFS BusID: 0000:00:06.0
  Hardware Class: bridge
  Model: "AMD RS780 PCI to PCI bridge (PCIE port 2)"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x9606 "RS780 PCI to PCI bridge (PCIE port 2)"
  Driver: "pcieport-driver"
  IRQ: 2302 (no events)
  Module Alias: "pci:v00001022d00009606sv00000000sd00000000bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

35: PCI 01.0: 0604 PCI bridge (Normal decode)
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_1043_9602
  Unique ID: vSkL.d9cgQeHt+59
  SysFS ID: /devices/pci0000:00/0000:00:01.0
  SysFS BusID: 0000:00:01.0
  Hardware Class: bridge
  Model: "ASUSTeK PCI bridge"
  Vendor: pci 0x1043 "ASUSTeK Computer Inc."
  Device: pci 0x9602 
  Module Alias: "pci:v00001043d00009602sv00000000sd00000000bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

36: PCI 00.0: 0600 Host bridge
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_1022_9600
  Unique ID: qLht.OZzcKVFLBQA
  SysFS ID: /devices/pci0000:00/0000:00:00.0
  SysFS BusID: 0000:00:00.0
  Hardware Class: bridge
  Model: "AMD RS780 Host Bridge"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x9600 "RS780 Host Bridge"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x8388 
  Module Alias: "pci:v00001022d00009600sv00001043sd00008388bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

37: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0c01
  Unique ID: XB3B.gNN83gfynbD
  SysFS ID: /devices/pnp0/00:0e
  SysFS BusID: 00:0e
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c01 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

38: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0c02_3
  Unique ID: 30p6.B+yZ9Ve8gC1
  SysFS ID: /devices/pnp0/00:0d
  SysFS BusID: 00:0d
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c02 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

39: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0c02_2
  Unique ID: cqY2.B+yZ9Ve8gC1
  SysFS ID: /devices/pnp0/00:0c
  SysFS BusID: 00:0c
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c02 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

40: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0c02_1
  Unique ID: 9fI_.B+yZ9Ve8gC1
  SysFS ID: /devices/pnp0/00:0b
  SysFS BusID: 00:0b
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c02 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

41: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0c02_0
  Unique ID: iT2w.B+yZ9Ve8gC1
  SysFS ID: /devices/pnp0/00:0a
  SysFS BusID: 00:0a
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c02 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

42: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0103
  Unique ID: H20r.fG36JLVNse9
  SysFS ID: /devices/pnp0/00:09
  SysFS BusID: 00:09
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0103 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

43: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0700
  Unique ID: qslm.yhTOLOXWEq7
  SysFS ID: /devices/pnp0/00:08
  SysFS BusID: 00:08
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0700 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

44: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0c04
  Unique ID: NhVi.DE8RM9cWQQ8
  SysFS ID: /devices/pnp0/00:07
  SysFS BusID: 00:07
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c04 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

45: ISA(PnP) 00.0: 0000 Unclassified device
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

46: ISA(PnP) 00.0: 0000 Unclassified device
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

47: ISA(PnP) 00.0: 0000 Unclassified device
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

48: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0f03
  Unique ID: KiZ0.dF8oQb6hYJ9
  SysFS ID: /devices/pnp0/00:03
  SysFS BusID: 00:03
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0f03 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

49: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0303
  Unique ID: tWJy.xhndlW9HXJ7
  SysFS ID: /devices/pnp0/00:02
  SysFS BusID: 00:02
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0303 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

50: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0c02
  Unique ID: QL3u.B+yZ9Ve8gC1
  SysFS ID: /devices/pnp0/00:01
  SysFS BusID: 00:01
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c02 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

51: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0a03
  Unique ID: z9pp.QBqTp8zQt87
  SysFS ID: /devices/pnp0/00:00
  SysFS BusID: 00:00
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0a03 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

52: SCSI 400.0: 10602 CD-ROM (DVD)
  [Created at block.247]
  UDI: /org/freedesktop/Hal/devices/storage_model_DVD_Writer_1040d
  Unique ID: KD9E.bpnezxH_8DF
  Parent ID: Eu86.G2ybYGkeYC3
  SysFS ID: /class/block/sr0
  SysFS BusID: 4:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:14.1/host4/target4:0:0/4:0:0:0
  Hardware Class: cdrom
  Model: "HP DVD Writer 1040d"
  Vendor: "HP"
  Device: "DVD Writer 1040d"
  Revision: "EH24"
  Driver: "pata_atiixp", "sr"
  Device File: /dev/sr0 (/dev/sg1)
  Device Number: block 11:0 (char 21:1)
  Features: CD-R, CD-RW, DVD, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+DL, DVDRAM
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #25 (IDE interface)
  Drive Speed: 48

53: IDE 00.0: 10600 Disk
  [Created at block.243]
  UDI: /org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD3200AAKS__WD_WCAV24661468
  Unique ID: 3OOL.mLwm7uOw48B
  Parent ID: 7EWs.WPBK7Mqox0D
  SysFS ID: /class/block/sda
  SysFS BusID: 0:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:11.0/host0/target0:0:0/0:0:0:0
  Hardware Class: disk
  Model: "WDC WD3200AAKS-0"
  Vendor: "WDC"
  Device: "WD3200AAKS-0"
  Revision: "01.0"
  Serial ID: "WD-WCAV24661468"
  Driver: "ahci", "sd"
  Driver Modules: "ahci"
  Device File: /dev/sda
  Device Number: block 8:0-8:15
  BIOS id: 0x80
  Geometry (Logical): CHS 38913/255/63
  Size: 625142448 sectors a 512 bytes
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #33 (SATA controller)

54: None 00.0: 11300 Partition
  [Created at block.412]
  UDI: /org/freedesktop/Hal/devices/volume_uuid_10f79e5c_10ad_4f71_8b60_e828d5299810
  Unique ID: bdUI.SE1wIdpsiiC
  Parent ID: 3OOL.mLwm7uOw48B
  SysFS ID: /class/block/sda/sda1
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda1
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #53 (Disk)

55: None 00.0: 11300 Partition
  [Created at block.412]
  UDI: /org/freedesktop/Hal/devices/volume_part2_size_1024
  Unique ID: 2pkM.SE1wIdpsiiC
  Parent ID: 3OOL.mLwm7uOw48B
  SysFS ID: /class/block/sda/sda2
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda2
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #53 (Disk)

56: None 00.0: 11300 Partition
  [Created at block.412]
  UDI: /org/freedesktop/Hal/devices/volume_uuid_3773c8ab_bc4b_48c0_9613_05934ff5e3e0
  Unique ID: QLVZ.SE1wIdpsiiC
  Parent ID: 3OOL.mLwm7uOw48B
  SysFS ID: /class/block/sda/sda5
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda5
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #53 (Disk)

57: USB 00.1: 0000 Unclassified device
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_46e_5542_noserial_if1_logicaldev_input
  Unique ID: k_sa.tohDqUAqyUD
  Parent ID: zPk0.uYbnlyRCGC6
  SysFS ID: /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.1
  SysFS BusID: 4-3:1.1
  Hardware Class: unknown
  Model: "Behavior Tech USB Multimedia Keyboard"
  Hotplug: USB
  Vendor: usb 0x046e "Behavior Tech. Computer Corp."
  Device: usb 0x5542 "USB Multimedia Keyboard"
  Revision: "1.10"
  Driver: "usbhid"
  Driver Modules: "usbhid"
  Device File: /dev/input/event6
  Device Number: char 13:70
  Speed: 1.5 Mbps
  Module Alias: "usb:v046Ep5542d0110dc00dsc00dp00ic03isc00ip00"
  Driver Info #0:
    Driver Status: usbhid is active
    Driver Activation Cmd: "modprobe usbhid"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #64 (Hub)

58: USB 00.0: 10800 Keyboard
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_46e_5542_noserial_if0_logicaldev_input
  Unique ID: HpcW.8ic3TyME2S3
  Parent ID: zPk0.uYbnlyRCGC6
  SysFS ID: /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0
  SysFS BusID: 4-3:1.0
  Hardware Class: keyboard
  Model: "Behavior Tech USB Multimedia Keyboard"
  Hotplug: USB
  Vendor: usb 0x046e "Behavior Tech. Computer Corp."
  Device: usb 0x5542 "USB Multimedia Keyboard"
  Revision: "1.10"
  Driver: "usbhid"
  Driver Modules: "usbhid"
  Device File: /dev/input/event5
  Device Number: char 13:69
  Speed: 1.5 Mbps
  Module Alias: "usb:v046Ep5542d0110dc00dsc00dp00ic03isc01ip01"
  Driver Info #0:
    XkbRules: xfree86
    XkbModel: pc104
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #64 (Hub)

59: USB 00.1: 0000 Unclassified device
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_46d_c049_noserial_if1
  Unique ID: IsEQ.00_XidZfc3E
  Parent ID: zPk0.uYbnlyRCGC6
  SysFS ID: /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.1
  SysFS BusID: 4-2:1.1
  Hardware Class: unknown
  Model: "Logitech USB Gaming Mouse"
  Hotplug: USB
  Vendor: usb 0x046d "Logitech, Inc."
  Device: usb 0xc049 "USB Gaming Mouse"
  Revision: "52.00"
  Driver: "usbhid"
  Driver Modules: "usbhid"
  Speed: 12 Mbps
  Module Alias: "usb:v046DpC049d5200dc00dsc00dp00ic03isc00ip00"
  Driver Info #0:
    Driver Status: usbhid is active
    Driver Activation Cmd: "modprobe usbhid"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #64 (Hub)

60: USB 00.0: 10503 USB Mouse
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_46d_c049_noserial_if0
  Unique ID: rg_L.3XHwq2zBd0B
  Parent ID: zPk0.uYbnlyRCGC6
  SysFS ID: /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0
  SysFS BusID: 4-2:1.0
  Hardware Class: mouse
  Model: "Logitech USB Gaming Mouse"
  Hotplug: USB
  Vendor: usb 0x046d "Logitech, Inc."
  Device: usb 0xc049 "USB Gaming Mouse"
  Revision: "52.00"
  Compatible to: int 0x0210 0x0028
  Driver: "usbhid"
  Driver Modules: "usbhid"
  Device File: /dev/input/mice (/dev/input/mouse1)
  Device Files: /dev/input/mice, /dev/input/mouse1, /dev/input/event3
  Device Number: char 13:63 (char 13:33)
  Speed: 12 Mbps
  Module Alias: "usb:v046DpC049d5200dc00dsc00dp00ic03isc01ip02"
  Driver Info #0:
    Buttons: 8
    Wheels: 2
    XFree86 Protocol: explorerps/2
    GPM Protocol: exps2
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #64 (Hub)

61: USB 00.0: 10a00 Hub
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_14_5_if0
  Unique ID: BSFT._WUAGn1cSY8
  Parent ID: hB6S.0fuWihmxabA
  SysFS ID: /devices/pci0000:00/0000:00:14.5/usb7/7-0:1.0
  SysFS BusID: 7-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.28-16-generic ohci_hcd OHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.28-16-generic ohci_hcd"
  Device: usb 0x0001 "OHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:14.5"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #21 (USB Controller)

62: USB 00.0: 10a00 Hub
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_1_if0
  Unique ID: 7eqy.PaupGMfzSp8
  Parent ID: 9n5e.VEymD7fE3DA
  SysFS ID: /devices/pci0000:00/0000:00:13.1/usb6/6-0:1.0
  SysFS BusID: 6-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.28-16-generic ohci_hcd OHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.28-16-generic ohci_hcd"
  Device: usb 0x0001 "OHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:13.1"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #28 (USB Controller)

63: USB 00.0: 10a00 Hub
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_0_if0
  Unique ID: 2XnU.erpEvbsFWX1
  Parent ID: HSco._p+0lYXXXq9
  SysFS ID: /devices/pci0000:00/0000:00:13.0/usb5/5-0:1.0
  SysFS BusID: 5-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.28-16-generic ohci_hcd OHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.28-16-generic ohci_hcd"
  Device: usb 0x0001 "OHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:13.0"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #29 (USB Controller)

64: USB 00.0: 10a00 Hub
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_1_if0
  Unique ID: zPk0.uYbnlyRCGC6
  Parent ID: 4g2A.VEymD7fE3DA
  SysFS ID: /devices/pci0000:00/0000:00:12.1/usb4/4-0:1.0
  SysFS BusID: 4-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.28-16-generic ohci_hcd OHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.28-16-generic ohci_hcd"
  Device: usb 0x0001 "OHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:12.1"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #31 (USB Controller)

65: USB 00.0: 10a00 Hub
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_0_if0
  Unique ID: uIhY.7qWCOCfUJwE
  Parent ID: CLZK._p+0lYXXXq9
  SysFS ID: /devices/pci0000:00/0000:00:12.0/usb3/3-0:1.0
  SysFS BusID: 3-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.28-16-generic ohci_hcd OHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.28-16-generic ohci_hcd"
  Device: usb 0x0001 "OHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:12.0"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #32 (USB Controller)

66: USB 00.0: 10a00 Hub
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_13_2_if0
  Unique ID: pBe4.3f5c44ENLJ9
  Parent ID: 06bT.jPsMPYxld01
  SysFS ID: /devices/pci0000:00/0000:00:13.2/usb2/2-0:1.0
  SysFS BusID: 2-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.28-16-generic ehci_hcd EHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.28-16-generic ehci_hcd"
  Device: usb 0x0002 "EHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:13.2"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #27 (USB Controller)

67: USB 00.0: 10a00 Hub
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_12_2_if0
  Unique ID: k4bc.YdoZZg0c8i6
  Parent ID: x_X+.jPsMPYxld01
  SysFS ID: /devices/pci0000:00/0000:00:12.2/usb1/1-0:1.0
  SysFS BusID: 1-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.28-16-generic ehci_hcd EHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.28-16-generic ehci_hcd"
  Device: usb 0x0002 "EHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:12.2"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #30 (USB Controller)

68: ADB 00.0: 10502 Bus Mouse
  [Created at input.183]
  UDI: /org/freedesktop/Hal/devices/computer_logicaldev_input_1
  Unique ID: kZYT.VdKNesd9pT6
  Hardware Class: mouse
  Model: "Macintosh mouse button emulation"
  Vendor: 0x0001 
  Device: 0x0001 "Macintosh mouse button emulation"
  Compatible to: int 0x0210 0x0003
  Device File: /dev/input/mice (/dev/input/mouse0)
  Device Files: /dev/input/mice, /dev/input/mouse0, /dev/input/event2
  Device Number: char 13:63 (char 13:32)
  Driver Info #0:
    Buttons: 3
    Wheels: 0
    XFree86 Protocol: explorerps/2
    GPM Protocol: exps2
  Config Status: cfg=new, avail=yes, need=no, active=unknown

69: None 00.0: 10103 CPU
  [Created at cpu.304]
  Unique ID: rdCR.j8NaKXDZtZ6
  Hardware Class: cpu
  Arch: Intel
  Vendor: "AuthenticAMD"
  Model: 16.5.2 "AMD Athlon(tm) II X4 620 Processor"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,sep,mtrr,pge,mca,cmov,pat,pse36,clflush,mmx,fxsr,sse,sse2,ht,syscall,nx,mmxext,fxsr_opt,pdpe1gb,rdtscp,lm,3dnowext,3dnow,constant_tsc,pni,monitor,cx16,lahf_lm,cmp_legacy,svm,extapic,cr8_legacy,abm,sse4a,misalignsse,
  Clock: 800 MHz
  BogoMips: 5223.37
  Cache: 512 kb
  Units/Processor: 4
  Config Status: cfg=new, avail=yes, need=no, active=unknown

70: None 01.0: 10103 CPU
  [Created at cpu.304]
  Unique ID: wkFv.j8NaKXDZtZ6
  Hardware Class: cpu
  Arch: Intel
  Vendor: "AuthenticAMD"
  Model: 16.5.2 "AMD Athlon(tm) II X4 620 Processor"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,sep,mtrr,pge,mca,cmov,pat,pse36,clflush,mmx,fxsr,sse,sse2,ht,syscall,nx,mmxext,fxsr_opt,pdpe1gb,rdtscp,lm,3dnowext,3dnow,constant_tsc,pni,monitor,cx16,lahf_lm,cmp_legacy,svm,extapic,cr8_legacy,abm,sse4a,misalignsse,
  Clock: 800 MHz
  BogoMips: 5209.90
  Cache: 512 kb
  Units/Processor: 4
  Config Status: cfg=new, avail=yes, need=no, active=unknown

71: None 02.0: 10103 CPU
  [Created at cpu.304]
  Unique ID: +rIN.j8NaKXDZtZ6
  Hardware Class: cpu
  Arch: Intel
  Vendor: "AuthenticAMD"
  Model: 16.5.2 "AMD Athlon(tm) II X4 620 Processor"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,sep,mtrr,pge,mca,cmov,pat,pse36,clflush,mmx,fxsr,sse,sse2,ht,syscall,nx,mmxext,fxsr_opt,pdpe1gb,rdtscp,lm,3dnowext,3dnow,constant_tsc,pni,monitor,cx16,lahf_lm,cmp_legacy,svm,extapic,cr8_legacy,abm,sse4a,misalignsse,
  Clock: 800 MHz
  BogoMips: 5209.89
  Cache: 512 kb
  Units/Processor: 4
  Config Status: cfg=new, avail=yes, need=no, active=unknown

72: None 03.0: 10103 CPU
  [Created at cpu.304]
  Unique ID: 4zLr.j8NaKXDZtZ6
  Hardware Class: cpu
  Arch: Intel
  Vendor: "AuthenticAMD"
  Model: 16.5.2 "AMD Athlon(tm) II X4 620 Processor"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,sep,mtrr,pge,mca,cmov,pat,pse36,clflush,mmx,fxsr,sse,sse2,ht,syscall,nx,mmxext,fxsr_opt,pdpe1gb,rdtscp,lm,3dnowext,3dnow,constant_tsc,pni,monitor,cx16,lahf_lm,cmp_legacy,svm,extapic,cr8_legacy,abm,sse4a,misalignsse,
  Clock: 1400 MHz
  BogoMips: 5209.89
  Cache: 512 kb
  Units/Processor: 4
  Config Status: cfg=new, avail=yes, need=no, active=unknown

73: None 00.0: 10701 Ethernet
  [Created at net.124]
  Unique ID: usDW.ndpeucax6V1
  Parent ID: rBUF.grmZBEFhCxF
  SysFS ID: /class/net/eth0
  SysFS Device Link: /devices/pci0000:00/0000:00:06.0/0000:02:00.0
  Hardware Class: network interface
  Model: "Ethernet network interface"
  Driver: "r8169"
  Driver Modules: "r8169"
  Device File: eth0
  HW Address: 00:26:18:b8:da:07
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #14 (Ethernet controller)

74: None 00.0: 10700 Loopback
  [Created at net.124]
  Unique ID: ZsBS.GQNx7L4uPNA
  SysFS ID: /class/net/lo
  Hardware Class: network interface
  Model: "Loopback network interface"
  Device File: lo
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

---

### Post by az on 2009-10-23
What are you worried about?

---

### Post by ukripper on 2009-10-23
It is a very long output, if can you tell us what you think is wrong then we can help you?

---

### Post by cariboo on 2009-10-23
This really has nothing to do with security, you provided more info than most of us want to go through without a specific question.

The only thing that stuck out doing a quick scan was that you seem to have a triple core cpu and the clock speeds look a little weird.

Moved to General Help

---

### Post by logikz on 2009-10-24
Ok the problem is.  I buy a new hard drive, motherboard, ram, router.  I install linux and I still get the SAME config from my past system.  I have listed like 20 USB ports, when i have 6 total, listed 68 loop drives, all block devices.  I can never view my hard drive, just sda block devices.  I configure my system to use sda1 and sda5 one for root, one for swap.  Then when i boot it up all of a sudden i have sda2 which is only 2 megs.  On my first boot I was told that my bios was corrupt and it would work around it, then it proceeded to disregard the BIOS completely, loading apic, usb etc..  I just need help on how to install a system that is clean!  The only things i reused were, my graphics card, my mouse and keyboard, my monitor, my powersupply and my cdrom drive.  everything else was brand spankin'new.  

My computer seems to have the traits of a slug system for some reason after reading about it.
[http://www.nslu2-linux.org/wiki/MSSII/HomePage](http://www.nslu2-linux.org/wiki/MSSII/HomePage)

Is it possible to have something pass from graphics card firmware?  maybe the monitor?  I just dont know.

(in response)
It is a quad-core cpu brand new.  I didnt touch the clock speeds.  I have no clue how all this stuff gets all screwy.  I am trying to just run a single workstation which no one has remote access to, and I can use the internet.  How would i set this up?  How would i disable this blocksystem of devices?  It all started from a french vista install that was corrupted, obviously, and ive been having nothing but trouble ever since.

---

### Post by az on 2009-10-24
> **logikz said:**
> Ok the problem is.  I buy a new hard drive, motherboard, ram, router.  I install linux and I still get the SAME config from my past system.  I have listed like 20 USB ports, when i have 6 total, listed 68 loop drives, all block devices.  I can never view my hard drive, just sda block devices.  I configure my system to use sda1 and sda5 one for root, one for swap.  Then when i boot it up all of a sudden i have sda2 which is only 2 megs.  On my first boot I was told that my bios was corrupt and it would work around it, then it proceeded to disregard the BIOS completely, loading apic, usb etc..  I just need help on how to install a system that is clean!  The only things i reused were, my graphics card, my mouse and keyboard, my monitor, my powersupply and my cdrom drive.  everything else was brand spankin'new.  

My computer seems to have the traits of a slug system for some reason after reading about it.
[http://www.nslu2-linux.org/wiki/MSSII/HomePage](http://www.nslu2-linux.org/wiki/MSSII/HomePage)

Is it possible to have something pass from graphics card firmware?  maybe the monitor?  I just dont know.

(in response)
It is a quad-core cpu brand new.  I didnt touch the clock speeds.  I have no clue how all this stuff gets all screwy.  I am trying to just run a single workstation which no one has remote access to, and I can use the internet.  How would i set this up?  How would i disable this blocksystem of devices?  It all started from a french vista install that was corrupted, obviously, and ive been having nothing but trouble ever since.
Other than what hwinfo is telling you, do you have any real problem?  Like is there a performance issue?

Hwinfo is not even an Ubuntu tool.  Unless you are using it to troubleshoot some hardware that is not working properly, don't install it and don't worry about it's output.  Your motherboard USB chipset is telling the kernel that it can handle 20 nodes.  Big deal.  This is not a bug.  The kernel has a slew of loop devices.  That's a good thing.  You are probably not using a single one of them, but there are 68 available.  What's the problem here?

What does

cat /proc/partitions 

say?

That will show you what your partitions are.

Exactly what message about your BIOS did you get?  Because if you removed the Motherboard's battery, it can complain upon first boot that the memory is corrupt and that it will restore its BIOS settings to default - this is normal.

---

### Post by logikz on 2009-10-26
I know i sound slow, but work with me here.  The symptoms is an ever changing file environment.  On EVERY single install, i get a message that my bios is corrupted and that it will work around it.  And i have installed many times.  It seems like things are getting different however.  I installed today, the new version of Kubuntu.  It didnt give the BIOS error, udev said it couldnt setup.  Then it gave me only 7 loop drives!  but it gave me 63 tty and 63 vcsa drives!  Now everything is slow and laggy.  It also gave me this message, i would post the exact thing but for some reason ubuntu by default logs every single packet into the system log?  So it got overwritten.  it was like this, i wrote it down.  Radeon dig0 transmitter coherent mode enabled.  Output dig0 transmitter setup success.  Dont know what it means.  My cat looks normal.  I guess i'll try installing redhat or something.

---

### Post by logikz on 2009-10-28
i mean you claim that this cat /proc/partitions lists all partitions.  Well, now i found this out.  I have 1 harddrive connected, thats it.  I have it configured as a SATA drive with 2 partitions, 1 swap 1 root.  So it should be sda1, sda2, sda5.  Thats it right?

```
Showing information for /org/freedesktop/DeviceKit/Disks/devices/dm_2d0 
  native-path:                 /sys/devices/virtual/block/dm-0          
  device:                      252:0                                    
  device-file:                 /dev/mapper/1ATA_WDC_WD3200AAKS-00L9A0_WD-WCAV24661468                                                                   
    by-id:                     /dev/disk/by-id/dm-name-1ATA_WDC_WD3200AAKS-00L9A0_WD-WCAV24661468                                                       
    by-id:                     /dev/disk/by-id/dm-uuid-mpath-1ATA_WDC_WD3200AAKS-00L9A0_WD-WCAV24661468                                                 
    by-id:                     /dev/disk/by-id/scsi-1ATA_WDC_WD3200AAKS-00L9A0_WD-WCAV24661468                                                          
  detected at:                 Tue 27 Oct 2009 11:04:13 PM CDT              
  system internal:             1                                            
  removable:                   0                                            
  has media:                   1 (detected at Tue 27 Oct 2009 11:04:13 PM CDT)                                                                          
    detects change:            0                                            
    detection by polling:      0                                            
    detection inhibitable:     0                                            
    detection inhibited:       0                                            
  is read only:                0                                            
  is mounted:                  0                                            
  mount paths:                                                              
  mounted by uid:              0                                            
  presentation hide:           0                                            
  presentation nopolicy:       1                                            
  presentation name:                                                        
  presentation icon:                                                        
  size:                        320072933376                                 
  block size:                  512                                          
  job underway:                no                                           
  usage:                                                                    
  type:                                                                     
  version:                                                                  
  uuid:                                                                     
  label:                                                                    
  partition table:                                                          
    scheme:                    mbr                                          
    count:                     0                                            
  drive:                                                                    
    vendor:                                                                 
    model:                                                                  
    revision:                                                               
    serial:                                                                 
    detachable:                0                                            
    can spindown:              0                                            
    rotational media:          1                                            
    ejectable:                 0                                            
    media:                                                                  
      compat:                                                               
    interface:                 (unknown)                                    
    if speed:                  (unknown)                                    
    ATA SMART:                 not available                                

========================================================================
Showing information for /org/freedesktop/DeviceKit/Disks/devices/dm_2d1 
  native-path:                 /sys/devices/virtual/block/dm-1          
  device:                      252:1                                    
  device-file:                 /dev/mapper/1ATA_WDC_WD3200AAKS-00L9A0_WD-WCAV24661468-part1                                                             
    by-id:                     /dev/disk/by-id/dm-name-1ATA_WDC_WD3200AAKS-00L9A0_WD-WCAV24661468-part1                                                 
    by-id:                     /dev/disk/by-id/dm-uuid-part1-mpath-1ATA_WDC_WD3200AAKS-00L9A0_WD-WCAV24661468                                           
    by-id:                     /dev/disk/by-id/scsi-1ATA_WDC_WD3200AAKS-00L9A0_WD-WCAV24661468-part1                                                    
    by-id:                     /dev/disk/by-uuid/db813507-caa7-4002-b7f9-5597efc22399                                                                   
  detected at:                 Tue 27 Oct 2009 11:04:13 PM CDT              
  system internal:             1                                            
  removable:                   0                                            
  has media:                   1 (detected at Tue 27 Oct 2009 11:04:13 PM CDT)                                                                          
    detects change:            0                                            
    detection by polling:      0                                            
    detection inhibitable:     0                                            
    detection inhibited:       0                                            
  is read only:                0                                            
  is mounted:                  1                                            
  mount paths:             /                                                
  mounted by uid:              0                                            
  presentation hide:           0                                            
  presentation nopolicy:       1                                            
  presentation name:                                                        
  presentation icon:                                                        
  size:                        307896873984                                 
  block size:                  512                                          
  job underway:                no                                           
  usage:                       filesystem                                   
  type:                        ext4                                         
  version:                     1.0                                          
  uuid:                        db813507-caa7-4002-b7f9-5597efc22399         
  label:                                                                    
  drive:                                                                    
    vendor:                                                                 
    model:                                                                  
    revision:                                                               
    serial:                                                                 
    detachable:                0                                            
    can spindown:              0                                            
    rotational media:          1                                            
    ejectable:                 0                                            
    media:                                                                  
      compat:                                                               
    interface:                 (unknown)                                    
    if speed:                  (unknown)                                    
    ATA SMART:                 not available                                

========================================================================
Showing information for /org/freedesktop/DeviceKit/Disks/devices/dm_2d2 
  native-path:                 /sys/devices/virtual/block/dm-2          
  device:                      252:2                                    
  device-file:                 /dev/mapper/1ATA_WDC_WD3200AAKS-00L9A0_WD-WCAV24661468-part2                                                             
    by-id:                     /dev/disk/by-id/dm-name-1ATA_WDC_WD3200AAKS-00L9A0_WD-WCAV24661468-part2                                                 
    by-id:                     /dev/disk/by-id/dm-uuid-part2-mpath-1ATA_WDC_WD3200AAKS-00L9A0_WD-WCAV24661468                                           
    by-id:                     /dev/disk/by-id/scsi-1ATA_WDC_WD3200AAKS-00L9A0_WD-WCAV24661468-part2                                                    
  detected at:                 Tue 27 Oct 2009 11:04:13 PM CDT              
  system internal:             1                                            
  removable:                   0                                            
  has media:                   1 (detected at Tue 27 Oct 2009 11:04:13 PM CDT)                                                                          
    detects change:            0                                            
    detection by polling:      0                                            
    detection inhibitable:     0                                            
    detection inhibited:       0                                            
  is read only:                0                                            
  is mounted:                  0                                            
  mount paths:                                                              
  mounted by uid:              0                                            
  presentation hide:           0                                            
  presentation nopolicy:       1                                            
  presentation name:                                                        
  presentation icon:                                                        
  size:                        12173414400                                  
  block size:                  512                                          
  job underway:                no                                           
  usage:                                                                    
  type:                                                                     
  version:                                                                  
  uuid:                                                                     
  label:                                                                    
  partition table:                                                          
    scheme:                    mbr                                          
    count:                     0                                            
  drive:                                                                    
    vendor:                                                                 
    model:                                                                  
    revision:                                                               
    serial:                                                                 
    detachable:                0                                            
    can spindown:              0                                            
    rotational media:          1                                            
    ejectable:                 0                                            
    media:                                                                  
      compat:                                                               
    interface:                 (unknown)                                    
    if speed:                  (unknown)                                    
    ATA SMART:                 not available                                

========================================================================
Showing information for /org/freedesktop/DeviceKit/Disks/devices/sda    
  native-path:                 /sys/devices/pci0000:00/0000:00:11.0/host0/target0:0:0/0:0:0:0/block/sda                                                 
  device:                      8:0                                          
  device-file:                 /dev/sda                                     
    by-id:                     /dev/disk/by-id/ata-WDC_WD3200AAKS-00L9A0_WD-WCAV24661468                                                                
    by-id:                     /dev/disk/by-id/scsi-SATA_WDC_WD3200AAKS-_WD-WCAV24661468                                                                
    by-path:                   /dev/disk/by-path/pci-0000:00:11.0-scsi-0:0:0:0                                                                          
  detected at:                 Tue 27 Oct 2009 11:04:13 PM CDT              
  system internal:             1                                            
  removable:                   0                                            
  has media:                   1 (detected at Tue 27 Oct 2009 11:04:13 PM CDT)                                                                          
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
  size:                        320072933376                                 
  block size:                  512                                          
  job underway:                no                                           
  usage:                                                                    
  type:                                                                     
  version:                                                                  
  uuid:                                                                     
  label:                                                                    
  partition table:                                                          
    scheme:                    mbr                                          
    count:                     2                                            
  drive:                                                                    
    vendor:                    ATA                                          
    model:                     WDC WD3200AAKS-00L9A0                        
    revision:                  01.03E01                                     
    serial:                    WD-WCAV24661468                              
    detachable:                0                                            
    can spindown:              1                                            
    rotational media:          1                                            
    ejectable:                 0                                            
    media:                                                                  
      compat:                                                               
    interface:                 ata                                          
    if speed:                  (unknown)                                    
    ATA SMART:                 Data not collected                           

========================================================================
Showing information for /org/freedesktop/DeviceKit/Disks/devices/sda1   
  native-path:                 /sys/devices/pci0000:00/0000:00:11.0/host0/target0:0:0/0:0:0:0/block/sda/sda1                                            
  device:                      8:1                                          
  device-file:                 /dev/sda1                                    
    by-id:                     /dev/disk/by-id/ata-WDC_WD3200AAKS-00L9A0_WD-WCAV24661468-part1                                                          
    by-id:                     /dev/disk/by-id/scsi-SATA_WDC_WD3200AAKS-_WD-WCAV24661468-part1                                                          
    by-id:                     /dev/disk/by-uuid/db813507-caa7-4002-b7f9-5597efc22399                                                                   
    by-path:                   /dev/disk/by-path/pci-0000:00:11.0-scsi-0:0:0:0-part1                                                                    
  detected at:                 Tue 27 Oct 2009 11:04:13 PM CDT              
  system internal:             1                                            
  removable:                   0                                            
  has media:                   1 (detected at Tue 27 Oct 2009 11:04:13 PM CDT)                                                                          
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
  size:                        307896873984                                 
  block size:                  512                                          
  job underway:                no                                           
  usage:                       filesystem                                   
  type:                        ext4                                         
  version:                     1.0                                          
  uuid:                        db813507-caa7-4002-b7f9-5597efc22399         
  label:                                                                    
  partition:                                                                
    part of:                   /org/freedesktop/DeviceKit/Disks/devices/sda 
    scheme:                    mbr                                          
    number:                    1                                            
    type:                      0x83                                         
    flags:                 boot                                             
    offset:                    32256                                        
    size:                      307896873984                                 
    label:                                                                  
    uuid:                                                                   

========================================================================
Showing information for /org/freedesktop/DeviceKit/Disks/devices/sda2   
  native-path:                 /sys/devices/pci0000:00/0000:00:11.0/host0/target0:0:0/0:0:0:0/block/sda/sda2                                            
  device:                      8:2                                          
  device-file:                 /dev/sda2                                    
    by-id:                     /dev/disk/by-id/ata-WDC_WD3200AAKS-00L9A0_WD-WCAV24661468-part2                                                          
    by-id:                     /dev/disk/by-id/scsi-SATA_WDC_WD3200AAKS-_WD-WCAV24661468-part2                                                          
    by-path:                   /dev/disk/by-path/pci-0000:00:11.0-scsi-0:0:0:0-part2                                                                    
  detected at:                 Tue 27 Oct 2009 11:04:13 PM CDT              
  system internal:             1                                            
  removable:                   0                                            
  has media:                   1 (detected at Tue 27 Oct 2009 11:04:13 PM CDT)                                                                          
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
  size:                        1024                                         
  block size:                  512                                          
  job underway:                no                                           
  usage:                                                                    
  type:                                                                     
  version:                                                                  
  uuid:                                                                     
  label:                                                                    
  partition:                                                                
    part of:                   /org/freedesktop/DeviceKit/Disks/devices/sda 
    scheme:                    mbr                                          
    number:                    2                                            
    type:                      0x05                                         
    flags:                                                                  
    offset:                    307896906240                                 
    size:                      12173414400                                  
    label:                                                                  
    uuid:                                                                   

========================================================================
root@online:/dev/mapper# devkit-disks --enumerate-device-files
/dev/mapper/1ATA_WDC_WD3200AAKS-00L9A0_WD-WCAV24661468        
/dev/disk/by-id/dm-name-1ATA_WDC_WD3200AAKS-00L9A0_WD-WCAV24661468
/dev/disk/by-id/dm-uuid-mpath-1ATA_WDC_WD3200AAKS-00L9A0_WD-WCAV24661468
/dev/disk/by-id/scsi-1ATA_WDC_WD3200AAKS-00L9A0_WD-WCAV24661468         
/dev/mapper/1ATA_WDC_WD3200AAKS-00L9A0_WD-WCAV24661468-part1            
/dev/disk/by-id/dm-name-1ATA_WDC_WD3200AAKS-00L9A0_WD-WCAV24661468-part1
/dev/disk/by-id/dm-uuid-part1-mpath-1ATA_WDC_WD3200AAKS-00L9A0_WD-WCAV24661468                                                                          
/dev/disk/by-id/scsi-1ATA_WDC_WD3200AAKS-00L9A0_WD-WCAV24661468-part1       
/dev/disk/by-uuid/db813507-caa7-4002-b7f9-5597efc22399                      
/dev/sda                                                                    
/dev/disk/by-id/ata-WDC_WD3200AAKS-00L9A0_WD-WCAV24661468                   
/dev/disk/by-id/scsi-SATA_WDC_WD3200AAKS-_WD-WCAV24661468                   
/dev/disk/by-path/pci-0000:00:11.0-scsi-0:0:0:0                             
/dev/sda1                                                                   
/dev/disk/by-id/ata-WDC_WD3200AAKS-00L9A0_WD-WCAV24661468-part1             
/dev/disk/by-id/scsi-SATA_WDC_WD3200AAKS-_WD-WCAV24661468-part1             
/dev/disk/by-uuid/db813507-caa7-4002-b7f9-5597efc22399                      
/dev/disk/by-path/pci-0000:00:11.0-scsi-0:0:0:0-part1                       
/dev/sda2                                                                   
/dev/disk/by-id/ata-WDC_WD3200AAKS-00L9A0_WD-WCAV24661468-part2             
/dev/disk/by-id/scsi-SATA_WDC_WD3200AAKS-_WD-WCAV24661468-part2             
/dev/disk/by-path/pci-0000:00:11.0-scsi-0:0:0:0-part2                       
/dev/mapper/1ATA_WDC_WD3200AAKS-00L9A0_WD-WCAV24661468-part2                
/dev/disk/by-id/dm-name-1ATA_WDC_WD3200AAKS-00L9A0_WD-WCAV24661468-part2    
/dev/disk/by-id/dm-uuid-part2-mpath-1ATA_WDC_WD3200AAKS-00L9A0_WD-WCAV24661468                                                                          
/dev/disk/by-id/scsi-1ATA_WDC_WD3200AAKS-00L9A0_WD-WCAV24661468-part2 


```

how is it that it is also configured as a raid disk?  Is this normal?

---

### Post by az on 2009-10-29
> **logikz said:**
> I know i sound slow, but work with me here.  The symptoms is an ever changing file environment.  

What does that mean?

> **logikz said:**
> 
On EVERY single install, i get a message that my bios is corrupted and that it will work around it.  And i have installed many times. 

Corrupted or buggy?  What is the exact message?  Because there are some motherboards with buggy BIOSes and the normal way to work around that is to work around that.  The kernel should work around that by itself.

> **logikz said:**
> 
 It seems like things are getting different however.  I installed today, the new version of Kubuntu.  It didnt give the BIOS error, udev said it couldnt setup.  Then it gave me only 7 loop drives!  but it gave me 63 tty and 63 vcsa drives!  Now everything is slow and laggy.  It also gave me this message, i would post the exact thing but for some reason ubuntu by default logs every single packet into the system log?  So it got overwritten.  it was like this, i wrote it down.  Radeon dig0 transmitter coherent mode enabled.  Output dig0 transmitter setup success.  Dont know what it means.  My cat looks normal.  I guess i'll try installing redhat or something.

If your computer is crashing unpredictably like that, I would suspect hardware problems like bad (or mismatched) ram, a disk with bad blocks or an overheating or otherwise faulty CPU or motherboard.  Have you ran memtest from the live cd?


> **logikz said:**
> i mean you claim that this cat /proc/partitions lists all partitions.  
...
how is it that it is also configured as a raid disk?  Is this normal?

Hwinfo is not an Ubuntu tool.  Since it is not directly supported, it can show you lots of things.  What does cat /proc/partitions show?

---

