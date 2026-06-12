---
title: "lm-sensors will not detect any sensors on HP desktop"
date: 2011-03-03
forum: General Help
---

### Post by xkalibur on 2011-03-03
Hey Guys,

I can't for the life of me get the xsensors to work. I installed lm-sensors, the applet and also xsensors.

I followed everything on this guide: [http://techthrob.com/2009/03/02/enabling-hardware-sensors-in-linux/](http://techthrob.com/2009/03/02/enabling-hardware-sensors-in-linux/). Went through it more than twice and a couple of restarts. I just can't figure out what's wrong.

When I run "sensors" nothing is found. I ran the sensors configuration and it only found one device to add to /etc/modules. Please see the trace below, I would be very grateful if you can help me find the fix for this! 

The desktop is an HP Pavilion a730n with a Pentium4 processor.

Here is the trace
```
rayes@pavilion:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
rayes@pavilion:~$ sudo apt-get install sensor-applet
[sudo] password for rayes: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package sensor-applet
rayes@pavilion:~$ sudo sensors-detect
# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# System: HP Pavilion 061 PJ510AA-ABA a730n
# Board: ASUSTeK Computer INC. Grouper

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): y
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
Intel Core family thermal sensor...                         No
Intel Atom thermal sensor...                                No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     Yes
Found `SMSC DME1737 Super IO'                               
    (hardware monitoring capabilities accessible via SMBus only)
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We first try to get the information from SMBIOS. If we don't find it
there, we have to read from arbitrary I/O ports to probe for such
interfaces. This is normally safe. Do you want to scan for IPMI
interfaces? (YES/no): y
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (yes/NO): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): y
Using driver `i2c-i801' for device 0000:00:1f.3: Intel 82801FB ICH6
Module i2c-i801 loaded successfully.
Module i2c-dev loaded successfully.

Next adapter: intel drm CRTDDC_A (i2c-0)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x4a
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Analog Devices ADT7411'...                     No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `National Semiconductor LM73'...                No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x4b
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Analog Devices ADT7411'...                     No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `Maxim MAX6650/MAX6651'...                      Success!
    (confidence 2, driver `max6650')
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Probing for `Analog Devices ADT7481'...                     No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `max6650':
  * Bus `intel drm CRTDDC_A'
    Busdriver `drm', I2C address 0x4b
    Chip `Maxim MAX6650/MAX6651' (confidence: 2)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
max6650
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)

```


Here is my list of modules loaded:
```

rayes@pavilion:~$ cat /proc/modules
binfmt_misc 6599 1 - Live 0xf8461000
snd_hda_codec_realtek 218492 1 - Live 0xf881a000
snd_usb_audio 86544 1 - Live 0xf8802000
snd_hda_intel 22299 2 - Live 0xf8475000
snd_hda_codec 87552 2 snd_hda_codec_realtek,snd_hda_intel, Live 0xf86cf000
snd_pcm 71603 3 snd_hda_intel,snd_hda_codec,snd_usb_audio, Live 0xf8d1e000
snd_hwdep 5040 2 snd_usb_audio,snd_hda_codec, Live 0xf8c79000
snd_usbmidi_lib 17413 1 snd_usb_audio, Live 0xf8c68000
snd_seq_midi 4588 0 - Live 0xf8a4f000
i915 296139 4 - Live 0xf8991000
snd_rawmidi 17783 2 snd_usbmidi_lib,snd_seq_midi, Live 0xf8a29000
snd_seq_midi_event 6047 1 snd_seq_midi, Live 0xf8a18000
snd_seq 47174 2 snd_seq_midi,snd_seq_midi_event, Live 0xf891b000
drm_kms_helper 30200 1 i915, Live 0xf88fd000
drm 168732 4 i915,drm_kms_helper, Live 0xf8750000
snd_timer 19067 2 snd_pcm,snd_seq, Live 0xf8875000
ppdev 5556 0 - Live 0xf86b2000
usbhid 36978 0 - Live 0xf885e000
snd_seq_device 5744 3 snd_seq_midi,snd_rawmidi,snd_seq, Live 0xf86cb000
usb_storage 40236 0 - Live 0xf86f4000
uvcvideo 55847 0 - Live 0xf8740000
parport_pc 26378 1 - Live 0xf8493000
usblp 10651 0 - Live 0xf848c000
hid 67742 1 usbhid, Live 0xf869a000
snd 49038 17 snd_hda_codec_realtek,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0xf84a6000
i2c_i801 8340 0 - Live 0xf8603000
intel_agp 26926 2 i915, Live 0xf8703000
videodev 43098 1 uvcvideo, Live 0xf842f000
i2c_dev 5077 0 - Live 0xf8429000
v4l1_compat 13359 2 uvcvideo,videodev, Live 0xf86c5000
i2c_algo_bit 5168 1 i915, Live 0xf86b7000
video 18712 1 i915, Live 0xf8667000
soundcore 880 1 snd, Live 0xf8676000
max6650 6784 0 - Live 0xf8636000
output 1883 1 video, Live 0xf8612000
agpgart 32075 2 drm,intel_agp, Live 0xf864c000
snd_page_alloc 7216 2 snd_hda_intel,snd_pcm, Live 0xf8629000
lp 7342 0 - Live 0xf8607000
parport 31492 3 ppdev,parport_pc,lp, Live 0xf85f1000
8139too 19709 0 - Live 0xf849f000
8139cp 17350 0 - Live 0xf846e000
firewire_ohci 21554 0 - Live 0xf8484000
firewire_core 46675 1 firewire_ohci, Live 0xf8445000
mii 4425 2 8139too,8139cp, Live 0xf845d000
crc_itu_t 1383 1 firewire_core, Live 0xf842c000

```


/etc/modules/
```


# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

# Generated by sensors-detect on Wed Mar  2 22:15:41 2011
# Chip drivers
max6650
i2c-dev
i2c-i801

```

---

### Post by xkalibur on 2011-03-05
*bump* please..

---

### Post by gandaran on 2011-03-05
most new laptops don't have any sensors that lm-sensors can detect, on this old desktop I have lm-sensors installed and can get cpu, motherboard temperature and fans speed, on my Toshiba netbook lm-sensors doesn't detect anything and I don't install it anymore as I can still get the cpu and motherboard temperature readings without it, only the fan speed is missing.
hope this clear things.

---

### Post by Mark Phelps on 2011-03-05
I regularly use KrellM to do hardware monitoring, and for it to work, LM-sensors must have been built using the Libsensors option -- and as of 10.10, the one coming with the distro STILL does NOT use that option.

Which means, on my PC, it displays no temp or fan info.

You have to download the source for LM-sensors and build it yourself with the libsensors option.

Actually ... I could be wrong there ... maybe libsensors is builtin now.  Read the link below for details:

[http://www.lm-sensors.org/]("http://www.lm-sensors.org/")

If libsensors is NOW builtin, my answer won't help you.  Sorry.

---

