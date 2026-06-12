---
title: "No Audio on Ubuntu"
date: 2012-04-12
forum: General Help
---

### Post by MaximB on 2012-04-12
Hello !

I'm using Ubuntu latest 64-bit, and I was using Alsa till today, some programs had no audio but generally most things worked.
Today I've installed Pulseaudio and not I get no sound at all.

```
maximb@MaximB-HQ:~/Games/trine$ ./trine-bin64 
ALSA lib conf.c:2700:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
maximb@MaximB-HQ:~/Games/trine$ locate libasound_module_conf_pulse.so
/usr/lib/x86_64-linux-gnu/alsa-lib/libasound_module_conf_pulse.so
/usr/lib32/alsa-lib/libasound_module_conf_pulse.so
maximb@MaximB-HQ:~/Games/trine$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Set [C-Media USB Headphone Set], device 0: USB Audio [USB Audio]                                                                                              
  Subdevices: 1/1                                                                                                                                                     
  Subdevice #0: subdevice #0                                                                                                                                          
maximb@MaximB-HQ:~/Games/trine$ lspci -v
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)                                                                             
        Subsystem: Giga-byte Technology Device 5000                                                                                                                   
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: f4000000-f7ffffff
        Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology Device 5004
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at e100 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology Device 5004
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at e200 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology Device 5004
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at e000 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Giga-byte Technology Device 5006
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at fa104000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
        Subsystem: Giga-byte Technology Device a002
        Flags: bus master, fast devsel, latency 0, IRQ 45
        Memory at fa100000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: fa400000-fa5fffff
        Prefetchable memory behind bridge: 00000000fa600000-00000000fa7fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fa000000-fa0fffff
        Prefetchable memory behind bridge: 00000000fa200000-00000000fa3fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: f8000000-f9ffffff
        Prefetchable memory behind bridge: 00000000dff00000-00000000dfffffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology Device 5004
        Flags: bus master, medium devsel, latency 0, IRQ 23
        I/O ports at e300 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology Device 5004
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at e400 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology Device 5004
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at e500 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Giga-byte Technology Device 5006
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at fa105000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
        I/O behind bridge: 0000a000-0000afff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
        Subsystem: Giga-byte Technology Device 5001
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>
        Kernel modules: iTCO_wdt

00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Giga-byte Technology Device b002
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at f000 [size=16]
        I/O ports at fc00 [size=16]
        Capabilities: <access denied>
        Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
        Subsystem: Giga-byte Technology Device 5001
        Flags: medium devsel, IRQ 9
        Memory at fa106000 (64-bit, non-prefetchable) [size=256]
        I/O ports at 0500 [size=32]
        Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02) (prog-if 85 [Master SecO PriO])
        Subsystem: Giga-byte Technology Device b002
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at e700 [size=8]
        I/O ports at e800 [size=4]
        I/O ports at e900 [size=8]
        I/O ports at ea00 [size=4]
        I/O ports at eb00 [size=16]
        I/O ports at ec00 [size=16]
        Capabilities: <access denied>
        Kernel driver in use: ata_piix

01:00.0 VGA compatible controller: nVidia Corporation GT200b [GeForce GTX 275] (rev a1) (prog-if 00 [VGA controller])
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at f4000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at b000 [size=128]
        [virtual] Expansion ROM at f7000000 [disabled] [size=512K]
        Capabilities: <access denied>
        Kernel driver in use: nvidia
        Kernel modules: nvidia_current_updates, nvidia_current, nouveau, nvidiafb

03:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02) (prog-if 01 [AHCI 1.0])
        Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at fa000000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: ahci
        Kernel modules: ahci

03:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02) (prog-if 85 [Master SecO PriO])
        Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
        Flags: bus master, fast devsel, latency 0, IRQ 16
        I/O ports at c000 [size=8]
        I/O ports at c100 [size=4]
        I/O ports at c200 [size=8]
        I/O ports at c300 [size=4]
        I/O ports at c400 [size=16]
        Capabilities: <access denied>
        Kernel driver in use: pata_jmicron
        Kernel modules: pata_jmicron

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
        Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
        Flags: bus master, fast devsel, latency 0, IRQ 44
        I/O ports at d000 [size=256]
        Memory at f9000000 (64-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at dff00000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: r8169
        Kernel modules: r8169

```

/etc/openal/alsoft.conf

```
# OpenAL config file. Options that are not under a block or are under the
# [general] block are for general, non-backend-specific options. Blocks may
# appear multiple times, and duplicated options will take the last value
# specified.
# The system-wide settings can be put in /etc/openal/alsoft.conf and user-
# specific override settings in ~/.alsoftrc.
# For Windows, these settings should go into %AppData%\alsoft.ini
# The environment variable ALSOFT_CONF can be used to specify another config
# override

# Option and block names are case-insenstive. The supplied values are only
# hints and may not be honored (though generally it'll try to get as close as
# possible). Note: options that are left unset may default to app- or system-
# specified values. These are the current available settings:

## format:
#  Sets the output format. Can be one of:
#  AL_FORMAT_MONO8    (8-bit mono)
#  AL_FORMAT_STEREO8  (8-bit stereo)
#  AL_FORMAT_QUAD8    (8-bit 4-channel)
#  AL_FORMAT_51CHN8   (8-bit 5.1 output)
#  AL_FORMAT_61CHN8   (8-bit 6.1 output)
#  AL_FORMAT_71CHN8   (8-bit 7.1 output)
#  AL_FORMAT_MONO16   (16-bit mono)
#  AL_FORMAT_STEREO16 (16-bit stereo)
#  AL_FORMAT_QUAD16   (16-bit 4-channel)
#  AL_FORMAT_51CHN16  (16-bit 5.1 output)
#  AL_FORMAT_61CHN16  (16-bit 6.1 output)
#  AL_FORMAT_71CHN16  (16-bit 7.1 output)
#  AL_FORMAT_MONO32   (32-bit float mono)
#  AL_FORMAT_STEREO32 (32-bit float stereo)
#  AL_FORMAT_QUAD32   (32-bit float 4-channel)
#  AL_FORMAT_51CHN32  (32-bit float 5.1 output)
#  AL_FORMAT_61CHN32  (32-bit float 6.1 output)
#  AL_FORMAT_71CHN32  (32-bit float 7.1 output)
#format = AL_FORMAT_STEREO16

## cf_level:
#  Sets the crossfeed level for stereo output. Valid values are:
#  0 - No crossfeed
#  1 - Low crossfeed
#  2 - Middle crossfeed
#  3 - High crossfeed (virtual speakers are closer to itself)
#  4 - Low easy crossfeed
#  5 - Middle easy crossfeed
#  6 - High easy crossfeed
#  Users of headphones may want to try various settings. Has no effect on non-
#  stereo modes.
#cf_level = 0

## head_dampen:
#  Sets the amount of dampening on sounds emanating from behind the listener.
#  This is used to simulate the natural occlusion of the head, which is
#  typically missing with mono and stereo output, and as such, only works on
#  mono and stereo output modes. Valid values range from 0 to 1 (inclusive),
#  and higher values provide a stronger effect.
#head_dampen = 0.25

## frequency:
#  Sets the output frequency.
#frequency = 44100

## resampler:
#  Selects the resampler used when mixing sources. Valid values are:
#  0 - None (nearest sample, no interpolation)
#  1 - Linear (extrapolates samples using a linear slope between samples)
#  2 - Cubic (extrapolates samples using a Catmull-Rom spline)
#  Specifying other values will result in using the default (linear).
#resampler = 1

## rt-prio:
#  Sets real-time priority for the mixing thread. Not all drivers may use this
#  (eg. PortAudio) as they already control the priority of the mixing thread.
#  0 and negative values will disable it. Note that this may constitute a
#  security risk since a real-time priority thread can indefinitely block
#  normal-priority threads if it fails to wait. As such, the default is
#  disabled.
#rt-prio = 0

## period_size:
#  Sets the update period size, in frames. This is the number of frames needed
#  for each mixing update.
#period_size = 1024

## periods:
#  Sets the number of update periods. Higher values create a larger mix ahead,
#  which helps protect against skips when the CPU is under load, but increases
#  the delay between a sound getting mixed and being heard.
#periods = 4

## sources:
#  Sets the maximum number of allocatable sources. Lower values may help for
#  systems with apps that try to play more sounds than the CPU can handle.
#sources = 256

## stereodup:
#  Sets whether to duplicate stereo sounds on the rear and side speakers for 4+
#  channel output. This provides a "fuller" playback quality for 4+ channel
#  output modes, although each individual speaker will have a slight reduction
#  in volume to compensate for the extra output speakers. True, yes, on, and
#  non-0 values will duplicate stereo sources. 0 and anything else will cause
#  stereo sounds to only play out the front speakers. This only has an effect
#  when a suitable output format is used (ie. those that contain side and/or
#  rear speakers).
#stereodup = true

## scalemix:
#  Sets whether to scale the remixed output. When the final mix is written to
#  the device, the multi-channel data is remixed so pure-virtual channels (eg.
#  front-center on stereo output) are remixed and added to available channels
#  (eg. front-left and front-right). Scaling helps ensure that no single source
#  will put out more than 100% on a given physical channel. This can cause a
#  noticeable reduction in overall volume, however, so it is off by default.
#scalemix = false

## drivers:
#  Sets the backend driver list order, comma-seperated. Unknown backends and
#  duplicated names are ignored. Unlisted backends won't be considered for use
#  unless the list is ended with a comma (eg. 'oss,' will list OSS first
#  followed by all other available backends, while 'oss' will list OSS only).
#  Backends prepended with - won't be available for use (eg. '-oss,' will allow
#  all available backends except OSS). An empty list means the default.
drivers = pulse,alsa,oss,solaris,dsound,winmm,port,null,wave

## excludefx:
#  Sets which effects to exclude, preventing apps from using them. This can
#  help for apps that try to use effects which are too CPU intensive for the
#  system to handle. Available effects are: eaxreverb,reverb,echo,modulator
#excludefx =

## slots:
#  Sets the maximum number of Auxiliary Effect Slots an app can create. A slot
#  can use a non-negligible amount of CPU time if an effect is set on it even
#  if no sources are feeding it, so this may help when apps use more than the
#  system can handle.
#slots = 4

## sends:
#  Sets the number of auxiliary sends per source. When not specified (default),
#  it allows the app to request how many it wants. The maximum value currently
#  possible is 4.
#sends =

## layout:
#  Sets the virtual speaker layout. Values are specified in degrees, where 0 is
#  straight in front, negative goes left, and positive goes right. Unspecified
#  speakers will remain at their default positions (which are dependant on the
#  output format). Available speakers are back-left(bl), side-left(sl), front-
#  left(fl), front-center(fc), front-right(fr), side-right(sr), back-right(br),
#  and back-center(bc).
#layout =

## layout_*:
#  Channel-specific layouts may be specified to override the layout option. The
#  same speakers as the layout option are available, and the default settings
#  are shown below.
#layout_STEREO = fl=-90, fr=90
#layout_QUAD   = fl=-45, fr=45, bl=-135, br=135
#layout_51CHN  = fl=-30, fr=30, fc=0, bl=-110, br=110
#layout_61CHN  = fl=-30, fr=30, fc=0, sl=-90, sr=90, bc=180
#layout_71CHN  = fl=-30, fr=30, fc=0, sl=-90, sr=90, bl=-150, br=150

##
## ALSA backend stuff
##
[alsa]

## device:
#  Sets the device name for the default playback device.
#device = default

## capture:
#  Sets the device name for the default capture device.
#capture = default

## mmap:
#  Sets whether to try using mmap mode (helps reduce latencies and CPU
#  consumption). If mmap isn't available, it will automatically fall back to
#  non-mmap mode. True, yes, on, and non-0 values will attempt to use mmap. 0
#  and anything else will force mmap off.
#mmap = true

##
## OSS backend stuff
##
[oss]

## device:
#  Sets the device name for OSS output.
#device = /dev/dsp

## capture:
#  Sets the device name for OSS capture.
#capture = /dev/dsp

##
## Solaris backend stuff
##
[solaris]

## device:
#  Sets the device name for Solaris output.
#device = /dev/audio

##
## DirectSound backend stuff
##
[dsound]

##
## Windows Multimedia backend stuff
##
[winmm]

##
## PortAudio backend stuff
##
[port]

## device:
#  Sets the device index for output. Negative values will use the default as
#  given by PortAudio itself.
#device = -1

## capture:
#  Sets the device index for capture. Negative values will use the default as
#  given by PortAudio itself.
#capture = -1

##
## PulseAudio backend stuff
##
[pulse]

## spawn-server:
#  Attempts to spawn a PulseAudio server when requesting to open a PulseAudio
#  device. Note that some apps may open and probe all enumerated devices on
#  startup, causing a server to spawn even if a PulseAudio device is not
#  actually selected. Setting autospawn to false in Pulse's client.conf will
#  still prevent autospawning even if this is set to true.
spawn-server = true

##
## Wave File Writer stuff
##
[wave]

## file:
#  Sets the filename of the wave file to write to. An empty name prevents the
#  backend from opening, even when explicitly requested.
#  THIS WILL OVERWRITE EXISTING FILES WITHOUT QUESTION!
#file =

```

Please help me solve this issue.

---

### Post by alex2e1gzy on 2012-04-12
Could be on the wrong track here... but doesn't Pulseaudio require an ALSA plugin to work with (aplay -l) ALSA?

Have you had a look at [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)?

---

### Post by MaximB on 2012-04-13
I get : 

ALSA lib conf.c:2700:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so

But I do have libasound_module_conf_pulse.so at :

/usr/lib/x86_64-linux-gnu/alsa-lib/libasound_module_conf_pulse.so
/usr/lib32/alsa-lib/libasound_module_conf_pulse.so

---

