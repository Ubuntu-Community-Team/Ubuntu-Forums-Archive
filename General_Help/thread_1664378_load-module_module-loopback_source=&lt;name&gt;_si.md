---
title: "load-module module-loopback source=&lt;name&gt; sink=&lt;name&gt;"
date: 2011-01-10
forum: General Help
---

### Post by mroussin51 on 2011-01-10
I want to stream audio from bluetooth to speakers. I am using pacmd. Here are my results. I am not sure where I have gone wrong but have spent significant time to stream audio over bluetoothe but can not here it on my speakers. 


```
user@mike:~$ pacmd
Welcome to PulseAudio! Use "help" for usage information.
>>> load-module module-loopback source=<bluez_source.BC_0D_A5_83_95_AE> sink=<alsa_output.pci-0000_00_1b.0.analog-stereo>
Module load failed.
>>> list-sources
2 source(s) available.
  * index: 0
	name: <alsa_input.usb-046d_09a4_36C49D50-02-U0x46d0x9a4.analog-mono>
	driver: <module-alsa-card.c>
	flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: SUSPENDED
	suspend cause: IDLE 
	priority: 9049
	volume: 0:  63%
	        0: -12.00 dB
	        balance 0.00
	base volume:  26%
	             -35.00 dB
	volume steps: 65537
	muted: no
	current latency: 0.00 ms
	max rewind: 0 KiB
	sample spec: s16le 1ch 16000Hz
	channel map: mono
	             Mono
	used by: 0
	linked by: 0
	configured latency: 0.00 ms; range is 0.50 .. 2000.00 ms
	card: 0 <alsa_card.usb-046d_09a4_36C49D50-02-U0x46d0x9a4>
	module: 4
	properties:
		alsa.resolution_bits = "16"
		device.api = "alsa"
		device.class = "sound"
		alsa.class = "generic"
		alsa.subclass = "generic-mix"
		alsa.name = "USB Audio"
		alsa.id = "USB Audio"
		alsa.subdevice = "0"
		alsa.subdevice_name = "subdevice #0"
		alsa.device = "0"
		alsa.card = "1"
		alsa.card_name = "USB Device 0x46d:0x9a4"
		alsa.long_card_name = "USB Device 0x46d:0x9a4 at usb-0000:00:1a.7-4, high speed"
		alsa.driver_name = "snd_usb_audio"
		device.bus_path = "pci-0000:00:1a.7-usb-0:4:1.2"
		sysfs.path = "/devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.2/sound/card1"
		udev.id = "usb-046d_09a4_36C49D50-02-U0x46d0x9a4"
		device.bus = "usb"
		device.vendor.id = "046d"
		device.vendor.name = "Logitech, Inc."
		device.product.id = "09a4"
		device.product.name = "QuickCam E 3500"
		device.serial = "046d_09a4_36C49D50"
		device.form_factor = "webcam"
		device.string = "hw:1"
		device.buffering.buffer_size = "64000"
		device.buffering.fragment_size = "32000"
		device.access_mode = "mmap+timer"
		device.profile.name = "analog-mono"
		device.profile.description = "Analog Mono"
		device.description = "QuickCam E 3500 Analog Mono"
		alsa.mixer_name = "USB Mixer"
		alsa.components = "USB046d:09a4"
		module-udev-detect.discovered = "1"
		device.icon_name = "camera-web-usb"
    index: 1
	name: <alsa_output.pci-0000_00_1b.0.analog-stereo.monitor>
	driver: <module-alsa-card.c>
	flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: SUSPENDED
	suspend cause: IDLE 
	priority: 1950
	volume: 0: 100% 1: 100%
	        0: 0.00 dB 1: 0.00 dB
	        balance 0.00
	base volume: 100%
	             0.00 dB
	volume steps: 65537
	muted: no
	current latency: 0.00 ms
	max rewind: 0 KiB
	sample spec: s16le 2ch 44100Hz
	channel map: front-left,front-right
	             Stereo
	used by: 0
	linked by: 0
	configured latency: 0.00 ms; range is 0.50 .. 1999.82 ms
	monitor_of: 0
	card: 1 <alsa_card.pci-0000_00_1b.0>
	module: 5
	properties:
		device.description = "Monitor of Internal Audio Analog Stereo"
		device.class = "monitor"
		alsa.card = "0"
		alsa.card_name = "HDA Intel"
		alsa.long_card_name = "HDA Intel at 0xe3220000 irq 42"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:1b.0"
		sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
		device.bus = "pci"
		device.vendor.id = "8086"
		device.vendor.name = "Intel Corporation"
		device.product.id = "3a3e"
		device.product.name = "82801JI (ICH10 Family) HD Audio Controller"
		device.form_factor = "internal"
		device.string = "0"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
>>> list-sinks
1 sink(s) available.
  * index: 0
	name: <alsa_output.pci-0000_00_1b.0.analog-stereo>
	driver: <module-alsa-card.c>
	flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: SUSPENDED
	suspend cause: IDLE 
	priority: 9959
	volume: 0:  50% 1:  50%
	        0: -18.06 dB 1: -18.06 dB
	        balance 0.00
	base volume: 100%
	             0.00 dB
	volume steps: 65537
	muted: no
	current latency: 0.00 ms
	max request: 0 KiB
	max rewind: 0 KiB
	monitor source: 1
	sample spec: s16le 2ch 44100Hz
	channel map: front-left,front-right
	             Stereo
	used by: 0
	linked by: 0
	configured latency: 0.00 ms; range is 0.50 .. 1999.82 ms
	card: 1 <alsa_card.pci-0000_00_1b.0>
	module: 5
	properties:
		alsa.resolution_bits = "16"
		device.api = "alsa"
		device.class = "sound"
		alsa.class = "generic"
		alsa.subclass = "generic-mix"
		alsa.name = "STAC92xx Analog"
		alsa.id = "STAC92xx Analog"
		alsa.subdevice = "0"
		alsa.subdevice_name = "subdevice #0"
		alsa.device = "0"
		alsa.card = "0"
		alsa.card_name = "HDA Intel"
		alsa.long_card_name = "HDA Intel at 0xe3220000 irq 42"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:1b.0"
		sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
		device.bus = "pci"
		device.vendor.id = "8086"
		device.vendor.name = "Intel Corporation"
		device.product.id = "3a3e"
		device.product.name = "82801JI (ICH10 Family) HD Audio Controller"
		device.form_factor = "internal"
		device.string = "front:0"
		device.buffering.buffer_size = "352768"
		device.buffering.fragment_size = "176384"
		device.access_mode = "mmap+timer"
		device.profile.name = "analog-stereo"
		device.profile.description = "Analog Stereo"
		device.description = "Internal Audio Analog Stereo"
		alsa.mixer_name = "IDT 92HD73E1X5"
		alsa.components = "HDA:111d7676,80865001,00100202"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	ports:
		analog-output: Analog Output (priority 9900)
		analog-output-speaker: Analog Speakers (priority 10000)
		analog-output-headphones: Analog Headphones (priority 9000)
	active port: <analog-output-speaker>
>>> load-module module-loopback source=<bluez_source.BC_0D_A5_83_95_AE> sink=<alsa_output.pci-0000_00_1b.0.analog-stereo>
Module load failed.
>>> 
```

I have tried everything I can think of. Please tell me what I have done wrong.

Thanks,

Mike

sorry, wrong sources:


```
>>> list-sources
3 source(s) available.
  * index: 0
	name: <alsa_input.usb-046d_09a4_36C49D50-02-U0x46d0x9a4.analog-mono>
	driver: <module-alsa-card.c>
	flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: SUSPENDED
	suspend cause: IDLE 
	priority: 9049
	volume: 0:  63%
	        0: -12.00 dB
	        balance 0.00
	base volume:  26%
	             -35.00 dB
	volume steps: 65537
	muted: no
	current latency: 0.00 ms
	max rewind: 0 KiB
	sample spec: s16le 1ch 16000Hz
	channel map: mono
	             Mono
	used by: 0
	linked by: 0
	configured latency: 0.00 ms; range is 0.50 .. 2000.00 ms
	card: 0 <alsa_card.usb-046d_09a4_36C49D50-02-U0x46d0x9a4>
	module: 4
	properties:
		alsa.resolution_bits = "16"
		device.api = "alsa"
		device.class = "sound"
		alsa.class = "generic"
		alsa.subclass = "generic-mix"
		alsa.name = "USB Audio"
		alsa.id = "USB Audio"
		alsa.subdevice = "0"
		alsa.subdevice_name = "subdevice #0"
		alsa.device = "0"
		alsa.card = "1"
		alsa.card_name = "USB Device 0x46d:0x9a4"
		alsa.long_card_name = "USB Device 0x46d:0x9a4 at usb-0000:00:1a.7-4, high speed"
		alsa.driver_name = "snd_usb_audio"
		device.bus_path = "pci-0000:00:1a.7-usb-0:4:1.2"
		sysfs.path = "/devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.2/sound/card1"
		udev.id = "usb-046d_09a4_36C49D50-02-U0x46d0x9a4"
		device.bus = "usb"
		device.vendor.id = "046d"
		device.vendor.name = "Logitech, Inc."
		device.product.id = "09a4"
		device.product.name = "QuickCam E 3500"
		device.serial = "046d_09a4_36C49D50"
		device.form_factor = "webcam"
		device.string = "hw:1"
		device.buffering.buffer_size = "64000"
		device.buffering.fragment_size = "32000"
		device.access_mode = "mmap+timer"
		device.profile.name = "analog-mono"
		device.profile.description = "Analog Mono"
		device.description = "QuickCam E 3500 Analog Mono"
		alsa.mixer_name = "USB Mixer"
		alsa.components = "USB046d:09a4"
		module-udev-detect.discovered = "1"
		device.icon_name = "camera-web-usb"
    index: 1
	name: <alsa_output.pci-0000_00_1b.0.analog-stereo.monitor>
	driver: <module-alsa-card.c>
	flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: SUSPENDED
	suspend cause: IDLE 
	priority: 1950
	volume: 0: 100% 1: 100%
	        0: 0.00 dB 1: 0.00 dB
	        balance 0.00
	base volume: 100%
	             0.00 dB
	volume steps: 65537
	muted: no
	current latency: 0.00 ms
	max rewind: 0 KiB
	sample spec: s16le 2ch 44100Hz
	channel map: front-left,front-right
	             Stereo
	used by: 0
	linked by: 0
	configured latency: 0.00 ms; range is 0.50 .. 1999.82 ms
	monitor_of: 0
	card: 1 <alsa_card.pci-0000_00_1b.0>
	module: 5
	properties:
		device.description = "Monitor of Internal Audio Analog Stereo"
		device.class = "monitor"
		alsa.card = "0"
		alsa.card_name = "HDA Intel"
		alsa.long_card_name = "HDA Intel at 0xe3220000 irq 42"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:1b.0"
		sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
		device.bus = "pci"
		device.vendor.id = "8086"
		device.vendor.name = "Intel Corporation"
		device.product.id = "3a3e"
		device.product.name = "82801JI (ICH10 Family) HD Audio Controller"
		device.form_factor = "internal"
		device.string = "0"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
    index: 4
	name: <bluez_source.BC_0D_A5_83_95_AE>
	driver: <module-bluetooth-device.c>
	flags: HARDWARE DECIBEL_VOLUME LATENCY 
	state: SUSPENDED
	suspend cause: IDLE 
	priority: 9030
	volume: 0: 100% 1: 100%
	        0: 0.00 dB 1: 0.00 dB
	        balance 0.00
	base volume: 100%
	             0.00 dB
	volume steps: 65537
	muted: no
	current latency: 0.00 ms
	max rewind: 0 KiB
	sample spec: s16le 2ch 44100Hz
	channel map: front-left,front-right
	             Stereo
	used by: 0
	linked by: 0
	fixed latency: 39.51 ms
	card: 4 <bluez_card.BC_0D_A5_83_95_AE>
	module: 25
	properties:
		bluetooth.protocol = "a2dp_source"
		device.description = "MIKE'S DROIDX"
		device.string = "BC:0D:A5:83:95:AE"
		device.api = "bluez"
		device.class = "sound"
		device.bus = "bluetooth"
		bluez.path = "/org/bluez/1498/hci0/dev_BC_0D_A5_83_95_AE"
		bluez.class = "0x5a020c"
		bluez.name = "MIKE'S DROIDX"
		device.icon_name = "audio-card-bluetooth"
```

---

