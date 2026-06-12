---
title: "How to map action to key"
date: 2011-09-17
forum: General Help
---

### Post by krumpy on 2011-09-17
I have a usb headset, so whenever I want to change to external speakers I have to click the sound preferences icon and change the output.  Is there a way to map this process to a key combination or at the very least a command line equivalent.

---

### Post by papibe on 2011-09-17
There's a command to control pulseaudio that could allow you to change preferences very similarly to 'Sound Preferences'. It's called pacmd

To get the list of output devices run:
```
$ pacmd list-sinks
```
They are organized by index. You should have at least 2 devices (regular speakers and USB). Check the output carefully to see which one is the USB headphones (it should be very clear on the list of properties). Let's assume is 2.

Once you have the correct index, you can change it by running:
```
# pacmd set-default-sink 2
```
That should be it. With that you can write a script, and create a shortcut if you want.

Tell me if you need help with that.
Regards.

---

### Post by krumpy on 2011-09-17
```

pacmd set-default-sink 2
```

The cmd above doesn't do anything for me.  Three different indices were listed when I ran the list cmd, but nothing happens when I try changing back to my speakers (I tried all three even though it was pretty clear, what was what).

---

### Post by papibe on 2011-09-17
Could you post the result of the listing?
```
$ pacmd list-sinks
```
Regards.

---

### Post by tgalati4 on 2011-09-17
You can add a custom hot-key short cut to a command.  To bring up the preference window, you need to find out the name of the dialog box.  For instance to bring up the keyboard shortcut dialog box:

gnome-keybinding-properties

many are found in /usr/bin

ls /usr/bin/gnome*

Some of the dialog boxes take commandline arguments, so you can probably set your headset with the correct parameters (known as magic).  Now when you press your hotkey, your headset will work automagically.

And if you are going through all of this effort, you might as well spend some time to debug your headset behavior and fix it.  For instance if you only use your headset with Skype, then you could write a script that switches to USB headset, starts skype, switches back to speakers when skype session is finished.

A forum search for skype usb headset script brings up lots of suggestions.

---

### Post by krumpy on 2011-09-18
Here's the output of the list.  The gnome keybinding route sounds promising.  I'll make sure to check that out.

```

Welcome to PulseAudio! Use "help" for usage information.
>>> 3 sink(s) available.
    index: 0
        name: <alsa_output.pci-0000_01_00.1.hdmi-stereo>
        driver: <module-alsa-card.c>
        flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
        state: SUSPENDED
        suspend cause: IDLE 
        priority: 9050
        volume: 0: 100% 1: 100%
                0: 0.00 dB 1: 0.00 dB
                balance 0.00
        base volume: 100%
                     0.00 dB
        volume steps: 65537
        muted: no
        current latency: 0.00 ms
        max request: 0 KiB
        max rewind: 0 KiB
        monitor source: 0
        sample spec: s16le 2ch 48000Hz
        channel map: front-left,front-right
                     Stereo
        used by: 0
        linked by: 0
        configured latency: 0.00 ms; range is 0.50 .. 2000.00 ms
        card: 0 <alsa_card.pci-0000_01_00.1>
        module: 4
        properties:
                alsa.resolution_bits = "16"
                device.api = "alsa"
                device.class = "sound"
                alsa.class = "generic"
                alsa.subclass = "generic-mix"
                alsa.name = "ATI HDMI"
                alsa.id = "ATI HDMI"
                alsa.subdevice = "0"
                alsa.subdevice_name = "subdevice #0"
                alsa.device = "3"
                alsa.card = "2"
                alsa.card_name = "HDA ATI HDMI"
                alsa.long_card_name = "HDA ATI HDMI at 0xfe9ec000 irq 46"
                alsa.driver_name = "snd_hda_intel"
                device.bus_path = "pci-0000:01:00.1"
                sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2"
                device.bus = "pci"
                device.vendor.id = "1002"
                device.vendor.name = "ATI Technologies Inc"
                device.product.id = "aa20"
                device.product.name = "RV635 Audio device [Radeon HD 3600 Series]"
                device.string = "hdmi:2"
                device.buffering.buffer_size = "384000"
                device.buffering.fragment_size = "192000"
                device.access_mode = "mmap+timer"
                device.profile.name = "hdmi-stereo"
                device.profile.description = "Digital Stereo (HDMI)"
                device.description = "RV635 Audio device [Radeon HD 3600 Series] Digital Stereo (HDMI)"
                alsa.mixer_name = "ATI R6xx HDMI"
                alsa.components = "HDA:1002aa01,00aa0100,00100000"
                module-udev-detect.discovered = "1"
                device.icon_name = "audio-card-pci"
    index: 1
        name: <alsa_output.usb-Sennheiser_Communications_Sennheiser_USB_Headset-00-Headset.analog-stereo>
        driver: <module-alsa-card.c>
        flags: HARDWARE HW_MUTE_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
        state: SUSPENDED
        suspend cause: IDLE 
        priority: 9049
        volume: 0:  63% 1:  63%
                0: -11.94 dB 1: -11.94 dB
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
        configured latency: 0.00 ms; range is 0.50 .. 2000.00 ms
        card: 1 <alsa_card.usb-Sennheiser_Communications_Sennheiser_USB_Headset-00-Headset>
        module: 5
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
                alsa.card_name = "Sennheiser USB Headset"
                alsa.long_card_name = "Sennheiser Communications Sennheiser USB Headset at usb-0000:00:1a.7-1.4.3, ful"
                alsa.driver_name = "snd_usb_audio"
                device.bus_path = "pci-0000:00:1a.7-usb-0:1.4.3:1.0"
                sysfs.path = "/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1.4/1-1.4.3/1-1.4.3:1.0/sound/card1"
                udev.id = "usb-Sennheiser_Communications_Sennheiser_USB_Headset-00-Headset"
                device.bus = "usb"
                device.vendor.id = "1395"
                device.vendor.name = "Sennheiser Communications"
                device.product.id = "0002"
                device.product.name = "Sennheiser USB Headset"
                device.serial = "Sennheiser_Communications_Sennheiser_USB_Headset"
                device.form_factor = "headset"
                device.string = "front:1"
                device.buffering.buffer_size = "352800"
                device.buffering.fragment_size = "176400"
                device.access_mode = "mmap+timer"
                device.profile.name = "analog-stereo"
                device.profile.description = "Analog Stereo"
                device.description = "Sennheiser USB Headset Analog Stereo"
                alsa.mixer_name = "USB Mixer"
                alsa.components = "USB1395:0002"
                module-udev-detect.discovered = "1"
                device.icon_name = "audio-headset-usb"      
ports:
                analog-output;output-bass-boost-on: Analog Output / Bass Boost (priority 9900)
                analog-output;output-bass-boost-off: Analog Output / No Bass Boost (priority 9910)
                analog-output-speaker;output-bass-boost-on: Analog Speakers / Bass Boost (priority 10000)
                analog-output-speaker;output-bass-boost-off: Analog Speakers / No Bass Boost (priority 10010)
        active port: <analog-output-speaker;output-bass-boost-off>
  * index: 2
        name: <alsa_output.pci-0000_00_1b.0.analog-stereo>
        driver: <module-alsa-card.c>
        flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
        state: SUSPENDED
        suspend cause: IDLE 
        priority: 9959
        volume: 0:  59% 1:  59%
                0: -13.95 dB 1: -13.95 dB
                balance 0.00
        base volume: 100%
                     0.00 dB
        volume steps: 65537
        muted: no
        current latency: 0.00 ms
        max request: 0 KiB
        max rewind: 0 KiB
        monitor source: 3
        sample spec: s16le 2ch 44100Hz
        channel map: front-left,front-right
                     Stereo
        used by: 0
        linked by: 0
        configured latency: 0.00 ms; range is 0.50 .. 1999.82 ms
        card: 2 <alsa_card.pci-0000_00_1b.0>
        module: 6
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
                alsa.long_card_name = "HDA Intel at 0xfebdc000 irq 45"
                alsa.driver_name = "snd_hda_intel"
                device.bus_path = "pci-0000:00:1b.0"
                sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
device.bus = "pci"
                device.vendor.id = "8086"
                device.vendor.name = "Intel Corporation"
                device.product.id = "293e"
                device.product.name = "82801I (ICH9 Family) HD Audio Controller"
                device.form_factor = "internal"
                device.string = "front:0"
                device.buffering.buffer_size = "352768"
                device.buffering.fragment_size = "176384"
                device.access_mode = "mmap+timer"
                device.profile.name = "analog-stereo"
                device.profile.description = "Analog Stereo"
                device.description = "Internal Audio Analog Stereo"
                alsa.mixer_name = "SigmaTel STAC9227"
                alsa.components = "HDA:83847618,10280215,00100201"
                module-udev-detect.discovered = "1"
                device.icon_name = "audio-card-pci"


```

---

### Post by papibe on 2011-09-18
If I understand correctly you can successfully change the sound to your USB headphone by doing:
```
$ pacmd set-default-sink 1
``` 
but you are not able to change it back with:
```
$ pacmd set-default-sink 2
``` 
Is that correct?

Regards.

---

### Post by krumpy on 2011-09-18
Yeah - that is right.  I works if run 

```

pacmd exit
pacmd set-default-sink 1
pacmd exit
pacmd set-default-sink 2

```

which i think is ok.  I might mess around with this and the gnome keybindings.  Thanks for the help.

---

### Post by krumpy on 2011-09-18
I think setting the default sink isn't enough to change the output preference.  I think you also have to move the sink input for each application currently in use.  This thread illustrates how to do it [http://ubuntuforums.org/showthread.php?t=1370383](http://ubuntuforums.org/showthread.php?t=1370383).

---

### Post by papibe on 2011-09-19
Interensting. I didn't know that. I usually change mics before initiating a chat in Skype, so I've never noticed it.

:P Good to know, thanks!
Regards.

---

