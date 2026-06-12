---
title: "IvmConfigActions.xml"
date: 2011-01-01
forum: General Help
---

### Post by tetebueno on 2011-01-01
Hi, I'm trying to configure an Acer Aspire 4520 to behave in a certain way when connecting different devices, for this I'm configuring ivman to open an application upon mounting of a device.
First I run lshal and identified the device once connected, this is the information displayed:

```
udi = '/org/freedesktop/Hal/devices/storage_serial_0x9c20019b'
  block.device = '/dev/mmcblk0'  (string)
  block.is_volume = false  (bool)
  block.major = 179  (0xb3)  (int)
  block.minor = 0  (0x0)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_0x9c20019b'  (string)
  info.capabilities = {'storage', 'block'} (string list)
  info.category = 'storage'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host_mmc_card_rca4660'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_serial_0x9c20019b'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0/0000:01:09.1/mmc_host/mmc0/mmc0:1234/block/mmcblk0'  (string)
  storage.automount_enabled_hint = true  (bool)
  storage.bus = 'mmc'  (string)
  storage.drive_type = 'sd_mmc'  (string)
  storage.hotpluggable = true  (bool)
  storage.media_check_enabled = false  (bool)
  storage.model = ''  (string)
  storage.no_partitions_hint = false  (bool)
  storage.originating_device = '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host_mmc_card_rca4660'  (string)
  storage.partitioning_scheme = 'none'  (string)
  storage.removable = false  (bool)
  storage.removable.media_available = true  (bool)
  storage.removable.media_size = 7952400384  (0x1da000000)  (uint64)
  storage.requires_eject = false  (bool)
  storage.serial = '0x9c20019b'  (string)
  storage.size = 7952400384  (0x1da000000)  (uint64)
  storage.vendor = ''  (string)

```

... so in /etc/ivman/IvmConfigActions.xml I just add as the last child of the <ivm:ActionsConfig> element:

```
	<ivm:Match name="hal.info.udi" value="/org/freedesktop/Hal/devices/storage_serial_0x9c20019b">
		<ivm:Option name="exec" value="rhythmbox" />
	</ivm:Match>

```

... so using the info.udi to recognize the device ivman opens rhythmbox.

All of this sounds great... if it only worked...

Anybody has an idea what could I be missing here?
Thanks.

---

### Post by tetebueno on 2011-01-01
Forgot to mention, this is on a Karmic.

---

