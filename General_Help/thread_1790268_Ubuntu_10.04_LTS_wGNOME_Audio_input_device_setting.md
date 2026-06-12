---
title: "Ubuntu 10.04 LTS w/GNOME: Audio input device setting always reverts to default"
date: 2011-06-24
forum: General Help
---

### Post by Broshea on 2011-06-24
$ uname -a
Linux boshea-wsl 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:52:38 UTC 2011 x86_64 GNU/Linux

I use a Logitech USB headset with microphone at work for phone conferencing, and for some reason whenever I restart Ubuntu (and sometimes seemingly at random times), the settings for the audio input device revert to the defaults (the internal audio hardware).

I can always reset it back to the USB headset by going to the sound configuration menu (Preferences -> Sound -> Input), but if any applications that use a microphone are already running, they will need to be restarted in order to make use of the newly configured input device.

It would be really nice if there were some way to make my USB headset the default audio input device, at least while it is plugged in, but I don't see a way to do this.  I've searched around for this and not found any solutions.

Any help is much appreciated!
-Broshea

---

### Post by tomyl on 2011-07-20
You could try to run something like

```
pacmd set-default-source alsa_input.usb-046d_0819_9F13DC90-02-U0x46d0x819.analog-mono

```at startup. Find the source name using "pacmd list-source".

---

### Post by nmfralich on 2011-07-31
I tried that, but with no success. Below is a terminal output of what I tried...


XXXX@XXXXXXX:~$ pacmd list-sources
Welcome to PulseAudio! Use "help" for usage information.
>>> 4 source(s) available.
    index: 0
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
	configured latency: 0.00 ms; range is 2.00 .. 1999.82 ms
	monitor_of: 0
	card: 0 <alsa_card.pci-0000_00_1b.0>
	module: 4
	properties:
		device.description = "Monitor of Internal Audio Analog Stereo"
		device.class = "monitor"
		alsa.card = "0"
		alsa.card_name = "HDA Intel"
		alsa.long_card_name = "HDA Intel at 0xfeaf8000 irq 22"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:1b.0"
		sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
		device.bus = "pci"
		device.vendor.id = "8086"
		device.vendor.name = "Intel Corporation"
		device.product.id = "284b"
		device.product.name = "82801H (ICH8 Family) HD Audio Controller"
		device.form_factor = "internal"
		device.string = "0"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
    index: 1
	name: <alsa_input.pci-0000_00_1b.0.analog-stereo>
	driver: <module-alsa-card.c>
	flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: SUSPENDED
	suspend cause: IDLE 
	priority: 9959
	volume: 0: 109% 1: 109%
	        0: 2.31 dB 1: 2.31 dB
	        balance 0.00
	base volume:  32%
	             -30.00 dB
	volume steps: 65537
	muted: no
	current latency: 0.00 ms
	max rewind: 0 KiB
	sample spec: s16le 2ch 44100Hz
	channel map: front-left,front-right
	             Stereo
	used by: 0
	linked by: 0
	configured latency: 0.00 ms; range is 26.00 .. 1999.82 ms
	card: 0 <alsa_card.pci-0000_00_1b.0>
	module: 4
	properties:
		alsa.resolution_bits = "16"
		device.api = "alsa"
		device.class = "sound"
		alsa.class = "generic"
		alsa.subclass = "generic-mix"
		alsa.name = "ALC888 Analog"
		alsa.id = "ALC888 Analog"
		alsa.subdevice = "0"
		alsa.subdevice_name = "subdevice #0"
		alsa.device = "0"
		alsa.card = "0"
		alsa.card_name = "HDA Intel"
		alsa.long_card_name = "HDA Intel at 0xfeaf8000 irq 22"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:1b.0"
		sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
		device.bus = "pci"
		device.vendor.id = "8086"
		device.vendor.name = "Intel Corporation"
		device.product.id = "284b"
		device.product.name = "82801H (ICH8 Family) HD Audio Controller"
		device.form_factor = "internal"
		device.string = "front:0"
		device.buffering.buffer_size = "352768"
		device.buffering.fragment_size = "176384"
		device.access_mode = "mmap+timer"
		device.profile.name = "analog-stereo"
		device.profile.description = "Analog Stereo"
		device.description = "Internal Audio Analog Stereo"
		alsa.mixer_name = "Realtek ALC888"
		alsa.components = "HDA:10ec0888,17aa3d7c,00100001 HDA:10573055,17aa3d7d,00100700"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	ports:
		input-microphone-1: Microphone 1 (priority 20)
		input-microphone-2: Microphone 2 (priority 19)
		input-linein: Line-In (priority 18)
	active port: <input-microphone-2>
  * index: 20
	name: <alsa_output.usb-Logitech_Logitech_USB_Headset-00-Headset.analog-stereo.monitor>
	driver: <module-alsa-card.c>
	flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: IDLE
	suspend cause: 
	priority: 1040
	volume: 0: 100% 1: 100%
	        0: 0.00 dB 1: 0.00 dB
	        balance 0.00
	base volume: 100%
	             0.00 dB
	volume steps: 65537
	muted: no
	current latency: 0.00 ms
	max rewind: 344 KiB
	sample spec: s16le 2ch 44100Hz
	channel map: front-left,front-right
	             Stereo
	used by: 0
	linked by: 0
	configured latency: 2000.00 ms; range is 26.00 .. 2000.00 ms
	monitor_of: 9
	card: 11 <alsa_card.usb-Logitech_Logitech_USB_Headset-00-Headset>
	module: 32
	properties:
		device.description = "Monitor of Logitech USB Headset Analog Stereo"
		device.class = "monitor"
		alsa.card = "1"
		alsa.card_name = "Logitech USB Headset"
		alsa.long_card_name = "Logitech Logitech USB Headset at usb-0000:00:1d.0-1, full speed"
		alsa.driver_name = "snd_usb_audio"
		device.bus_path = "pci-0000:00:1d.0-usb-0:1:1.0"
		sysfs.path = "/devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/sound/card1"
		udev.id = "usb-Logitech_Logitech_USB_Headset-00-Headset"
		device.bus = "usb"
		device.vendor.id = "046d"
		device.vendor.name = "Logitech, Inc."
		device.product.id = "0a0c"
		device.product.name = "Logitech USB Headset"
		device.serial = "Logitech_Logitech_USB_Headset"
		device.form_factor = "headset"
		device.string = "1"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-headset-usb"
    index: 21
	name: <alsa_input.usb-Logitech_Logitech_USB_Headset-00-Headset.analog-mono>
	driver: <module-alsa-card.c>
	flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: SUSPENDED
	suspend cause: IDLE 
	priority: 9049
	volume: 0:  78%
	        0: -6.46 dB
	        balance 0.00
	base volume:  33%
	             -29.00 dB
	volume steps: 65537
	muted: no
	current latency: 0.00 ms
	max rewind: 0 KiB
	sample spec: s16le 1ch 44100Hz
	channel map: mono
	             Mono
	used by: 0
	linked by: 0
	configured latency: 0.00 ms; range is 16.00 .. 2000.00 ms
	card: 11 <alsa_card.usb-Logitech_Logitech_USB_Headset-00-Headset>
	module: 32
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
		alsa.card_name = "Logitech USB Headset"
		alsa.long_card_name = "Logitech Logitech USB Headset at usb-0000:00:1d.0-1, full speed"
		alsa.driver_name = "snd_usb_audio"
		device.bus_path = "pci-0000:00:1d.0-usb-0:1:1.0"
		sysfs.path = "/devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/sound/card1"
		udev.id = "usb-Logitech_Logitech_USB_Headset-00-Headset"
		device.bus = "usb"
		device.vendor.id = "046d"
		device.vendor.name = "Logitech, Inc."
		device.product.id = "0a0c"
		device.product.name = "Logitech USB Headset"
		device.serial = "Logitech_Logitech_USB_Headset"
		device.form_factor = "headset"
		device.string = "hw:1"
		device.buffering.buffer_size = "176400"
		device.buffering.fragment_size = "88200"
		device.access_mode = "mmap+timer"
		device.profile.name = "analog-mono"
		device.profile.description = "Analog Mono"
		device.description = "Logitech USB Headset Analog Mono"
		alsa.mixer_name = "USB Mixer"
		alsa.components = "USB046d:0a0c"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-headset-usb"
>>> XXXX@XXXXXXX:~$ pacmd set-default-source alsa_output.usb-Logitech_LogiteSB_Headset-00-Headset.analog-stereo.monitor
Welcome to PulseAudio! Use "help" for usage information.

Any suggestions????

---

