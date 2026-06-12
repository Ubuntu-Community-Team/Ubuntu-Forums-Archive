---
title: "Beginner, Problem with sound on Ubuntu 10.04, Sony Vaio VPC-EB1M1E"
date: 2010-05-01
forum: General Help
---

### Post by marclol on 2010-05-01
Hello Everyone!

New to Ubuntu and on this forum! :)

I've used Ubuntu 8.04 LTS before for a couple of weeks until I changed back to Windows. This time though I really want to stay with Ubuntu and I'm willing to do the job to make this work. I even choose to put ubuntu on the whole harddrive

I installed 10.04 LTS yesterday and everything seems really good except my sound. I googled alot and couldn't find anything at all with my level of skill.

```

marc@marc-laptop:~$ aplay -l
aplay: device_list:223: no soundcards found...

```

I'm guessing that my soundcard has no drivers for linux. It's around 3 month old in the store. I'm using Sony Vaio VPC-EB1M1E.

Can anyone guide me? What can i do to make sure that there isn't a driver out there?

Best Regards,
Marc

---

### Post by P4man on 2010-05-01
Can you provide the output of

```
lspci
```

and 

```
lsusb
```

(that is LSPCI and LSUSB in lowercase)

---

### Post by marclol on 2010-05-01
```

lspci

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series]
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 SD Host controller: Ricoh Co Ltd Device e822
03:00.1 System peripheral: Ricoh Co Ltd Device e230
03:00.4 SD Host controller: Ricoh Co Ltd Device e822
04:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4381 (rev 11)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```
```

lsusb

Bus 002 Device 004: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 002 Device 003: ID 1532:0007 Razer USA, Ltd DeathAdder Mouse
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:6409 Microdia 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by P4man on 2010-05-01
Hmm odd. SHouldnt need a driver. I found someone with the same onboard sound with a workaround here:

[http://www.linuxquestions.org/questions/linux-newbie-8/no-sound-in-dell-1558-a-797064/](http://www.linuxquestions.org/questions/linux-newbie-8/no-sound-in-dell-1558-a-797064/)

No idea if it will work for you, but its worth a shot.

open a terminal and copy/paste this command:

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

and add this line at the bottom:

```
options snd-hda-intel model=dell-m6
```

Save the file, and log out and in again (or reboot).

Even though its for a dell, try anyway.
See if aplay -l shows a soundcard after that.

---

### Post by marclol on 2010-05-01
Thanks for the replies, I appreciate it very much!

I tried adding the line to the file and rebooted my comp, aplay -l still doesn't recognize any soundcard. :(

Any more suggestions?

Best Regards,
Marc

---

### Post by marclol on 2010-05-01
[http://bbs.archlinux.org/viewtopic.php?pid=749888](http://bbs.archlinux.org/viewtopic.php?pid=749888)

I found this threat, but i dont really know what to do.

Can anyone guide me?

Best Regards,
Marc

---

### Post by P4man on 2010-05-01
there is no solution in there, and a somewhat different problem.
I suggest you file a bug report on launchpad:

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

 and meanwhile hope someone provides a workaround. maybe remove that line you just added so it doesnt interfere with any future fix.

---

### Post by marclol on 2010-05-01
I followed the Ubuntu SoundTroubleshootingGuide until i came to: ( I guess this is for 9.04, I use 10.04 )

**Do you have the sound  modules installed?**

 Open a  terminal window, and type 
```
find /lib/modules/`uname -r` | grep snd
```You should see a  whole list of items come up.  If you don't, it means that the upgrade  process missed installing the kernel modules for sound.  To fix this,  type this at the command line: 

I got this:

```

marc@marc-laptop:~$ find /lib/modules/`uname -r` | grep snd
/lib/modules/2.6.32-21-generic/kernel/sound/isa/msnd
/lib/modules/2.6.32-21-generic/kernel/sound/oss/msnd_pinnacle.ko
/lib/modules/2.6.32-21-generic/kernel/sound/oss/msnd.ko
/lib/modules/2.6.32-21-generic/kernel/sound/oss/msnd_classic.ko

```I'm guessing i should have some ALSA modules there?

There were two lines to install the alsa modules but none of them worked:

```
[FONT=monospace]
[/FONT]sudo aptitude install linux-ubuntu-modules-`uname -r` linux-generic[FONT=monospace]
[/FONT]
``````
[FONT=monospace]
[/FONT]sudo aptitude install linux-restricted-modules-`uname -r`  linux-generic[FONT=monospace]
[/FONT]
```I then did:

**Is ALSA using the correct  model?**

 If you are  experiencing problems with your sound card after upgrading to Ubuntu  9.04, it might be because ALSA is using the wrong model for your  chipset. 
To figure out your chipset  you can run this command: 
```
wget -O alsa-info.sh http://alsa-project.org/alsa-info.sh && bash ./alsa-info.sh
```This will provide you with a URL to a webpage with lots  of information about your sound setup. Open it up, and keep it open;  you'll need it as a reference.

I got a link and this is the result: (no driver and no ALSA modules loaded from what i can see)

```


!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Sat May  1 20:24:59 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.04 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"


!!DMI Information
!!---------------

Manufacturer:      Sony Corporation
Product Name:      VPCEB1M1E


!!Kernel Information
!!------------------

Kernel release:    2.6.32-21-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.22
Utilities version:  1.0.22


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------



!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:3b56 (rev 05)
    Subsystem: 104d:9071
--
01:00.1 0403: 1002:aa60
    Subsystem: 104d:9071


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------



!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:223: no soundcards found...

ARECORD

arecord: device_list:223: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
nls_iso8859_1
nls_cp437
vfat
fat
ums_cypress
usb_storage
binfmt_misc
ppdev
joydev
arc4
fbcon
ath9k
tileblit
font
mac80211
ath
bitblit
uvcvideo
softcursor
videodev
v4l1_compat
fglrx
vga16fb
intel_agp
psmouse
cfg80211
serio_raw
vgastate
sdhci_pci
sdhci
led_class
agpgart
sony_laptop
video
output
lp
parport
usbhid
hid
sky2
ahci


!!ALSA/HDA dmesg
!!------------------

```

---

### Post by P4man on 2010-05-01
Nice self help you are doing there! But dont go any futher following that how to, its too old and you may mess things up.

See if this helps:

```
sudo apt-get install linux-backports-modules-alsa-2.6.32-21-generic
```

You will need to reboot

also a tip: select the command above, click it with your middle mouse. In the terminal, click again with middle mouse. Just so you understand why we love using command line here, as its just quicker to explain and quicker for you. 

But if you dont like command lines, you can install the package through synaptic package manager with a nice (and difficult to describe) gui :)

---

### Post by marclol on 2010-05-01
Alright! Thank you alot!

I got sound but it is very low. Any suggestions what might be the cause of that?

I've tried to turn everything up to max but it is still really low.

Best Regards,
Marc

---

### Post by P4man on 2010-05-01
progress:)

Try installing gnome-alsamixer 

```
sudo apt-get install gnome-alsamixer 
```

Launch it from apps > sound and video > gnome alsamixer

Turn up all sliders that might be relevant (even ones that dont look it like surround or whatever)

---

### Post by lidex on 2010-05-02
Try running the alsa-info script again to see what's changed and what codec is being loaded.

---

### Post by marclol on 2010-05-02
Alright, I did some more research and it seems that only my speakers or headphones work when i plug them in. My speakers on the actuall laptop doesn't make a sound. The Volume though is extremly low and if I max things up its like listening to someone whispering. I have been in alsamixer and everything is up at max, I've tried all the different combinations in Sound Preference. I dont have a hardware for input sound, I'd really like if my mic worked aswell. *EDIT* Got my mic working when i choose Analog Sterio Duplex. Still no luck with the speakers and the low sound. *EDIT*


Here is my new Alsa info:

```

!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Sun May  2 06:28:52 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.04 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"


!!DMI Information
!!---------------

Manufacturer:      Sony Corporation
Product Name:      VPCEB1M1E


!!Kernel Information
!!------------------

Kernel release:    2.6.32-21-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.22.1
Library version:    1.0.22
Utilities version:  1.0.22


!!Loaded ALSA modules
!!-------------------

snd_hda_intel
snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf5e00000 irq 36
 1 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xf0040000 irq 38


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:3b56 (rev 05)
    Subsystem: 104d:9071
--
01:00.1 0403: 1002:aa60
    Subsystem: 104d:9071


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
    bdl_pos_adj : 1,32,-1,-1,-1,-1,-1,-1
    beep_mode : 1,1,1,1,1,1,1,1
    enable : Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    index : -1,-1,-1,-1,-1,-1,-1,-1
    model : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    patch : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    position_fix : 0,0,0,0,0,0,0,0
    power_save : 0
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1
    probe_only : N,N,N,N,N,N,N,N
    single_cmd : N

!!Module: snd_hda_intel
    bdl_pos_adj : 1,32,-1,-1,-1,-1,-1,-1
    beep_mode : 1,1,1,1,1,1,1,1
    enable : Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    index : -1,-1,-1,-1,-1,-1,-1,-1
    model : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    patch : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    position_fix : 0,0,0,0,0,0,0,0
    power_save : 0
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1
    probe_only : N,N,N,N,N,N,N,N
    single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC269
Address: 0
Function Id: 0x1
Vendor Id: 0x10ec0269
Subsystem Id: 0x104d4600
Revision Id: 0x100004
No Modem Function Group found
Default PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x1d: Stereo Amp-Out
  Control: name="Speaker Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="ALC269 Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x3f, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x1d: Stereo Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x3f, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x3f 0x3f]
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x04 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x05 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x07 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x11, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x24
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=0, device=0
  Control: name="Capture Volume", index=0, device=0
  Device: name="ALC269 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x11, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x22 0x22]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0a [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Control: name="Beep Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x11 0x11]
  Connection: 5
     0x18 0x19 0x1a 0x1b 0x1d
Node 0x0c [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010a: Mono Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00] [0x00]
  Connection: 2
     0x0c 0x0d
Node 0x0f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x10 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x11 [Pin Complex] wcaps 0x400380: Mono Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x10
Node 0x12 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x90a60920: [Fixed] Mic at Int N/A
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40010d: Stereo Amp-Out
  Control: name="Speaker Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00010050: OUT EAPD Balanced
  EAPD 0x2: EAPD
  Pin Default 0x90170110: [Fixed] Speaker at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Connection: 2
     0x0c* 0x0d
Node 0x15 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001001c: OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x0221101f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=04, enabled=1
  Connection: 2
     0x0c 0x0d*
Node 0x16 [Pin Complex] wcaps 0x40010c: Mono Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80]
  Pincap 0x00000010: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x0e
Node 0x17 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Front Mic Boost", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x03 0x03]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003734: IN OUT Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02a15830: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Red
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=08, enabled=1
  Connection: 2
     0x0c* 0x0d
Node 0x19 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003734: IN OUT Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003734: IN OUT Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x1c [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x40138205: [N/A] Speaker at Ext N/A
    Conn = ATAPI, Color = Purple
    DefAssociation = 0x0, Sequence = 0x5
  Pin-ctls: 0x20: IN
Node 0x1e [Pin Complex] wcaps 0x400380: Mono Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x06
Node 0x1f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=33
  Processing Coefficient: 0xbbcc
  Coefficient Index: 0x06
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x23 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 7
     0x18 0x19 0x1a 0x1b 0x1d 0x12* 0x0b
Node 0x24 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 6
     0x18 0x19 0x1a 0x1b 0x1d 0x0b
Codec: ATI R6xx HDMI
Address: 0
Function Id: 0x1
Vendor Id: 0x1002aa01
Subsystem Id: 0x104d4600
Revision Id: 0x100200
No Modem Function Group found
Default PCM:
    rates [0x70]: 32000 44100 48000
    bits [0x2]: 16
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x201: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Device: name="ATI HDMI", type="HDMI", device=3
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x02
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  0 May  2 08:13 /dev/snd/controlC0
crw-rw----  1 root audio 116, 32 May  2 08:13 /dev/snd/controlC1
crw-rw----  1 root audio 116,  4 May  2 08:13 /dev/snd/hwC0D0
crw-rw----  1 root audio 116, 36 May  2 08:13 /dev/snd/hwC1D0
crw-rw----  1 root audio 116, 24 May  2 08:20 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116, 16 May  2 08:21 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116, 51 May  2 08:22 /dev/snd/pcmC1D3p
crw-rw----  1 root audio 116,  1 May  2 08:13 /dev/snd/seq
crw-rw----  1 root audio 116, 33 May  2 08:13 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 May  2 08:13 .
drwxr-xr-x 3 root root 240 May  2 08:13 ..
lrwxrwxrwx 1 root root  12 May  2 08:13 pci-0000:00:1b.0 -> ../controlC0
lrwxrwxrwx 1 root root  12 May  2 08:13 pci-0000:01:00.1 -> ../controlC1


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xf5e00000 irq 36'
  Mixer name    : 'Realtek ALC269'
  Components    : 'HDA:10ec0269,104d4600,00100004'
  Controls      : 12
  Simple ctrls  : 7
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 63 [98%] [0.00dB] [on]
  Front Right: Playback 63 [98%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [1.00dB] [on]
  Front Right: Playback 64 [100%] [1.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 3 [100%]
  Front Right: 3 [100%]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 17 [55%] [-9.00dB] [on]
  Front Right: Playback 17 [55%] [-9.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 34 [74%] [17.00dB] [on]
  Front Right: Capture 34 [74%] [17.00dB] [on]

!!-------Mixer controls for card 1 [Generic]

Card hw:1 'Generic'/'HD-Audio Generic at 0xf0040000 irq 38'
  Mixer name    : 'ATI R6xx HDMI'
  Components    : 'HDA:1002aa01,104d4600,00100200'
  Controls      : 4
  Simple ctrls  : 1
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
    control.1 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 64'
        comment.dbmin -6300
        comment.dbmax 100
        iface MIXER
        name 'Speaker Playback Volume'
        value.0 64
        value.1 64
    }
    control.2 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Speaker Playback Switch'
        value.0 true
        value.1 true
    }
    control.3 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 64'
        comment.dbmin -6300
        comment.dbmax 100
        iface MIXER
        name 'Headphone Playback Volume'
        value.0 63
        value.1 63
    }
    control.4 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Headphone Playback Switch'
        value.0 true
        value.1 true
    }
    control.5 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 3'
        comment.dbmin 0
        comment.dbmax 3000
        iface MIXER
        name 'Front Mic Boost'
        value.0 3
        value.1 3
    }
    control.6 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Capture Switch'
        value.0 true
        value.1 true
    }
    control.7 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 46'
        comment.dbmin -1700
        comment.dbmax 2900
        iface MIXER
        name 'Capture Volume'
        value.0 34
        value.1 34
    }
    control.8 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Beep Playback Volume'
        value.0 17
        value.1 17
    }
    control.9 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Beep Playback Switch'
        value.0 true
        value.1 true
    }
    control.10 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 64'
        comment.dbmin -6400
        comment.dbmax 0
        iface MIXER
        name 'Master Playback Volume'
        value 64
    }
    control.11 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Master Playback Switch'
        value true
    }
    control.12 {
        comment.access 'read write user'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        comment.tlv '0000000100000008ffffec1400000014'
        comment.dbmin -5100
        comment.dbmax 0
        iface MIXER
        name 'PCM Playback Volume'
        value.0 255
        value.1 255
    }
}
state.Generic {
    control.1 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.2 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.3 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Default'
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.4 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Switch'
        value false
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
snd_hda_codec_atihdmi
snd_hda_codec_realtek
binfmt_misc
snd_hda_intel
ppdev
snd_hda_codec
snd_hwdep
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
snd
joydev
soundcore
arc4
uvcvideo
fbcon
tileblit
font
bitblit
ath9k
videodev
v4l1_compat
video
softcursor
mac80211
output
ath
sony_laptop
lp
snd_page_alloc
intel_agp
fglrx
vga16fb
vgastate
psmouse
serio_raw
sdhci_pci
sdhci
cfg80211
led_class
agpgart
parport
usbhid
hid
ahci
sky2


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x11 0x411111f0
0x12 0x90a60920
0x14 0x90170110
0x15 0x0221101f
0x16 0x411111f0
0x18 0x02a15830
0x19 0x411111f0
0x1a 0x411111f0
0x1b 0x411111f0
0x1d 0x40138205
0x1e 0x411111f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC1D0/init_pin_configs:
0x03 0x18560010

/sys/class/sound/hwC1D0/driver_pin_configs:

/sys/class/sound/hwC1D0/user_pin_configs:

/sys/class/sound/hwC1D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   26.610108]   alloc kstat_irqs on node -1
[   26.610115] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   26.610193]   alloc irq_desc for 36 on node -1
[   26.610194]   alloc kstat_irqs on node -1
[   26.610207] HDA Intel 0000:00:1b.0: irq 36 for MSI/MSI-X
[   26.610240] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   27.191545]   alloc irq_desc for 37 on node -1
--
[   27.248177] CPU3 attaching NULL sched-domain.
[   27.269742] hda_codec: ALC269: BIOS auto-probing.
[   27.270423] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input12
[   27.273876] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   27.273932]   alloc irq_desc for 38 on node -1
[   27.273934]   alloc kstat_irqs on node -1
[   27.273945] HDA Intel 0000:01:00.1: irq 38 for MSI/MSI-X
[   27.273974] HDA Intel 0000:01:00.1: setting latency timer to 64
[   27.285408] CPU0 attaching sched-domain:
--
[   30.643434]    groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[   30.865422] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   38.604111] eth0: no IPv6 routers present
[   50.960040] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.

```Any ideas?

Best Regards
Marc

---

### Post by lidex on 2010-05-02
OK, try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=vaio  
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default.

---

### Post by dino99 on 2010-05-02
paprefs is needed to

---

### Post by marclol on 2010-05-02
Thanks for the replies!

I've done what Lidex told me without any improvement. Everything in alsamixer is max. My soundcard is "Internal Audio" with 1 output and 1 input. I'm using "Analog Sterio Duplex". I have sound only in my external speakers/headphones, nothing from speakers on the actuall laptop.

I've googled alot and came across something that made me install this: 

Open a Terminal window. 
Type the following: 
```
sudo apt-get install libasound2-plugins "pulseaudio-*" paman padevchooser paprefs pavucontrol pavumeter
```This will install  the ALSA Pulse plugin, the PulseAudio daemons and the PulseAudio tools.  

I hope i didn't do something stupid. Anyway.. my sound is still very low and i dont have any sound on my laptop speakers, Can i provide you with any information to make the errorsearching easier?

Best Regards,
Marc

---

### Post by lidex on 2010-05-02
OK, thought I'd seen this before. I would upgrade to latest version of alsa referencing this post to get 1.0.23:
[http://ubuntuforums.org/showpost.php?p=9136618&postcount=2]("http://ubuntuforums.org/showpost.php?p=9136618&postcount=2")
If that isn't enough go to this thread for fix:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1440444]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1440444")
And make sure to add your info to alsa bug report so they'll fix it.

EDIT: The alsa bug report states this is fixed in 1.0.23

---

### Post by marclol on 2010-05-04
Ok, Now i've done it all and it starts to get on my nerves...

Somehow the Alsa driver wont update. I deleted the alsa folder and did this guide

[http://tldp.org/HOWTO/Alsa-sound-4.html](http://tldp.org/HOWTO/Alsa-sound-4.html)

Then I checked this command afterwords

```
cat /proc/asound/version
```

and it was still 1.0.22.1 even though i wget the 1.0.23 packages and installed them.

I've been following about 20 guides now on how to make my sound work, rebooted and hoping to get sound without any luck. I have sound in my headphones which I can barley hear and nothing from laptop speakers.

Best Regards,
Marc

---

### Post by marclol on 2010-05-04
I reinstalled Ubuntu. Ubuntu regonized my aplay -l from the beginning this time but still very low sound. I followed this guide 

[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

And it worked very good.

Thanks alot everyone! Aspecially Lidex!

Best Regards,
Marc

---

### Post by ben72 on 2010-05-09
Before I got sound to work on a Sony Vaio VPC-EB1M1E/W I had to install a new kernel as well... I'll check my exact steps when I install another machine tomorrow..

sudo apt-get install 2.6.34-1-generic-pae

And to install alsa 1.0.23 I added the PPA here..
[https://launchpad.net/~ricotz/+archive/unstable](https://launchpad.net/~ricotz/+archive/unstable)

---

### Post by vishnujyothi on 2010-05-19
I  solved this issue by increasing all relevant levels in alsamixer

Type alsamixer in Terminal or try to get gnome-alsamixer from synaptic manger


:guitar:

---

### Post by vladimirprieto on 2010-10-03
just wanted to say that this post helped me to get sound on my vaio VPCEE27FL as well!!

so thank you very much.

the things i did until get it working:

- update alsa to 1.0.23 by compiling.  then i got sound, but it was too low, even with volumes at the top (same as posted on this thread).  gnome-alsmixer didn't help with the low sound, until...

- then i update alsa with:

[https://launchpad.net/~ricotz/+archive/unstable](https://launchpad.net/~ricotz/+archive/unstable) 

the same version, but this way is with a repository.  i also notice that other packages get updated.

THANK YOU VERY MUCH!

---

