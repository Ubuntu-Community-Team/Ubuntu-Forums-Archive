---
title: "A little audio problem became huge when I tried to fix it."
date: 2011-04-16
forum: General Help
---

### Post by colobix on 2011-04-16
Hey. Usually I try to fix things on my own, which btw always ends up failing :)
So the other day I got an update of some packages, I installed them and restarted the pc. When I was back in ubuntu, the speaker icon on my panel was gone, and so was the audio settings for pulse too.
When I went to system > pref > sound I got an error.
So now I decided to ditch pulse. Pulse have always given me problems btw.
I installed alsa, but couldn't get the shortcuts for up, down and mute to work. This is important to me because idk where the audio button on my laptop is (ASUS).
So I tweaked around for awhile and decided to go for OSS since it's the only option that will allow me to record both out and ingoing audio, which is an option I use a lot.
So I tweaked around and all that stuff, and now I'm very frustrated.

I have come to the conclusion that my audio card is unrecognized now.
I think I have every single ALSA / OSS driver, plugin and codec installed. 
Ok here's the audio card info I got from the command lspci | grep Audio
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
01:00.1 Audio device: nVidia Corporation Device 0be9 (rev a1)

So the card is some how recognized by the system but not according to gstreamer-properties.

Please help me here. I want OSS to work since OSS work perfectly with Audacity. Thanks in advance for all your help.

---

### Post by scott-ian on 2011-04-16
I'm not an expert, but I think you might want to uninstall the extra drivers.

---

### Post by Julian Luna on 2011-04-16
I'm really new but I would choice ALSA, it supports also output/input. Pulse has a nice name but it sucks... I deleted all the libraries that had the word "Pulse" and now I need to boot from the CD cause when I loggin normally; it asks me for the pass I used to use, and I enter it and the **** says it's not correct lol... you had luck, try Alsa it's really good

---

### Post by colobix on 2011-04-16
I'll go for ALSA.
@scott-ia i have no idea what drivers I have or not.
Well, I have the alsa driver module to the kernel I'm using now (28).
So I guess the driver should be fine. But whatever I try, it will not recognize my sound card.
I tried with both alsaconf and gstreamer-properties to see if it would at least be able to recognize something.

---

### Post by K_45 on 2011-04-16
Try here before something else breaks:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by colobix on 2011-04-16
Thanks but if I follow an outdated guide from 06, I'll most likely end up having more problems than I have now.
Even the updated version is down.

---

### Post by K_45 on 2011-04-16
With nearly 1900 posts, I think you can give it a shot.

---

### Post by colobix on 2011-04-16
I have actually tried some of these steps but with no luck. I really don't wanna experiment here. I want this to work.
When I read most of the newer posts there, all I can see is error reports and such. 
The fact is that many things have changed since 06, and following a guide like that is not only very experimental but the drivers they tried this out with are most likely not even available anymore.
So, I will rather get some expert help here or maybe I will send the pc in for service in a couple of days if it I can't fix it myself.

---

### Post by K_45 on 2011-04-16
Try the documentation here:

[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)

---

### Post by colobix on 2011-04-16
Thanks but most of these tweaks are either basics, or I have already tried them. When I try to recognize the card using "cat /proc/asound/card0/codec#* | grep Codec" I get an error that says file or directory do not exist. Which again falls back to what I said about old guides. Since that method worked on version 9.10.
Because first of all I Need to do something so that my pc will recognize the sound card again. When it says "unrecognized" it is most likely more than just a driver being gone or whatever.

---

### Post by K_45 on 2011-04-16
Did you try this:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by colobix on 2011-04-16
No I didn't try that one. Thanks.
Ok here's the longest post ever. The output with all the driver and module info regarding this sound problem thing.
It could however not find the sound card.
So please take a look and see if there is something I Need to install or uninstall here.



```
 bash alsa-info.sh --stdout
cat: /proc/asound/version: No such file or directory
grep: /proc/asound/cards: No such file or directory
cat: /proc/asound/cards: No such file or directory
cat: /proc/asound/modules: No such file or directory
ls: cannot access /dev/snd/*: No such file or directory
grep: /proc/asound/cards: No such file or directory
/usr/sbin/alsactl: save_state:1504: No soundcards found...
cat: /tmp/alsa-info.hBYl51T5B0/alsactl.tmp: No such file or directory
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Sun Apr 17 03:36:28 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu


!!DMI Information
!!---------------

Manufacturer:      ASUSTeK Computer Inc.
Product Name:      G73Sw
Product Version:   1.0       


!!Kernel Information
!!------------------

Kernel release:    2.6.35-28-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.23
Utilities version:  1.0.23


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Jack:
      Installed - Yes (/usr/bin/jackd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------



!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
01:00.1 Audio device: nVidia Corporation Device 0be9 (rev a1)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:1c20 (rev 05)
	Subsystem: 1043:1a13
--
01:00.1 0403: 10de:0be9 (rev a1)
	Subsystem: 1043:2044


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------



!!ALSA configuration files
!!------------------------

!!User specific config file (~/.asoundrc)

pcm.!default
 {
   type oss
   device /dev/dsp
 }
 mixer.!default
 {
   type oss
   device /dev/dsp
 }


!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:235: no soundcards found...

ARECORD

arecord: device_list:235: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
cryptd
aes_x86_64
aes_generic
rfcomm
binfmt_misc
sco
bnep
l2cap
oss_usb
osscore
nls_iso8859_1
nls_cp437
btrfs
zlib_deflate
crc32c
libcrc32c
ufs
qnx4
hfsplus
hfs
minix
ntfs
vfat
msdos
fat
jfs
xfs
exportfs
reiserfs
parport_pc
ppdev
dm_crypt
arc4
ath9k
ath9k_common
ath9k_hw
ath
mac80211
nvidia
usbhid
uvcvideo
videodev
v4l1_compat
cfg80211
v4l2_compat_ioctl32
hid
btusb
bluetooth
sparse_keymap
psmouse
serio_raw
led_class
xhci_hcd
lp
parport
dm_raid45
xor
ahci
video
r8169
libahci
output
mii
intel_agp
ramzswap
lzo_compress


!!ALSA/HDA dmesg
!!------------------




chris@chris-G73Sw:~$ bash alsa-info.sh --stdout
cat: /proc/asound/version: No such file or directory
grep: /proc/asound/cards: No such file or directory
cat: /proc/asound/cards: No such file or directory
cat: /proc/asound/modules: No such file or directory
ls: cannot access /dev/snd/*: No such file or directory
grep: /proc/asound/cards: No such file or directory
/usr/sbin/alsactl: save_state:1504: No soundcards found...
cat: /tmp/alsa-info.9WJwkKK8KN/alsactl.tmp: No such file or directory
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Sun Apr 17 03:36:40 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu


!!DMI Information
!!---------------

Manufacturer:      ASUSTeK Computer Inc.
Product Name:      G73Sw
Product Version:   1.0       


!!Kernel Information
!!------------------

Kernel release:    2.6.35-28-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.23
Utilities version:  1.0.23


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Jack:
      Installed - Yes (/usr/bin/jackd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------



!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
01:00.1 Audio device: nVidia Corporation Device 0be9 (rev a1)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:1c20 (rev 05)
	Subsystem: 1043:1a13
--
01:00.1 0403: 10de:0be9 (rev a1)
	Subsystem: 1043:2044


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------



!!ALSA configuration files
!!------------------------

!!User specific config file (~/.asoundrc)

pcm.!default
 {
   type oss
   device /dev/dsp
 }
 mixer.!default
 {
   type oss
   device /dev/dsp
 }


!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:235: no soundcards found...

ARECORD

arecord: device_list:235: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
cryptd
aes_x86_64
aes_generic
rfcomm
binfmt_misc
sco
bnep
l2cap
oss_usb
osscore
nls_iso8859_1
nls_cp437
btrfs
zlib_deflate
crc32c
libcrc32c
ufs
qnx4
hfsplus
hfs
minix
ntfs
vfat
msdos
fat
jfs
xfs
exportfs
reiserfs
parport_pc
ppdev
dm_crypt
arc4
ath9k
ath9k_common
ath9k_hw
ath
mac80211
nvidia
usbhid
uvcvideo
videodev
v4l1_compat
cfg80211
v4l2_compat_ioctl32
hid
btusb
bluetooth
sparse_keymap
psmouse
serio_raw
led_class
xhci_hcd
lp
parport
dm_raid45
xor
ahci
video
r8169
libahci
output
mii
intel_agp
ramzswap
lzo_compress


!!ALSA/HDA dmesg
!!------------------

```

---

### Post by K_45 on 2011-04-16
This should load the Intel module:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by colobix on 2011-04-17
Already tried that one. How can I find the model ? As I said, the "cat /proc/asound/card0/codec#* | grep Codec" doesn't work for me.

---

### Post by K_45 on 2011-04-17
Try these commands one by one until you get a result, then we can force load the module to restore the sound:

```
lspci | grep "HDA"
```

```
lspci | grep "Azalia"
```

```
lspci | grep "Intel"
```

```
lspci | grep "Realtek"
```

---

### Post by colobix on 2011-04-17
Ah nice. The 3rd one worked.
```
00:00.0 Host bridge: Intel Corporation Sandy Bridge DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b5)
00:1c.5 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 6 (rev b5)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Cougar Point LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 05)
```
So now what do we do?

---

### Post by K_45 on 2011-04-17
OK, one more command:

```
aplay -l
```

Output?

If we get the module we can load it . . .

---

### Post by colobix on 2011-04-17
it says no sound card was found.

---

### Post by 3177 on 2011-04-17
how bout re-installing pulse?

---

### Post by K_45 on 2011-04-17
What is the output of this:

```
find /lib/modules/`uname -r` | grep snd
```

Also try here:

[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

---

### Post by colobix on 2011-04-17
@3177 If it could only be that easy.
But if it was that easy I would probably not ask for help.
If you read the first post you will see that there are at least two reasons why I can't just reinstall pulse.
And that was the first thing I tried btw.

> **K_45 said:**
> What is the output of this:

```
find /lib/modules/`uname -r` | grep snd
```

Also try here:

[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

No output there.
I added the repository and installed that kernel update, and rebooted, but still no luck.

---

### Post by K_45 on 2011-04-17
Before we try to start adding modules, can you try out the latest Beta of 11.04? It has a new kernel which may work with your laptop:

[http://mirror.anl.gov/pub/ubuntu-iso/CDs//natty/](http://mirror.anl.gov/pub/ubuntu-iso/CDs//natty/)

Boot the live CD (64-bit probably) and - ?

---

### Post by colobix on 2011-04-17
No I have never been able to upgrade from a ubuntu version to another. I really can't understand why they even have that feature.
I think that feature makes people leave ubuntu.
Plus, leaving a stable version for a beta? no thanks. not even if the upgrade process went well.
Is is possible to upgrade the kernel from this version?

---

### Post by K_45 on 2011-04-17
I meant try it out, not install it. Its coming out by the end of the month officially anyway. If the live CD works, then you can install it when its released.  

For kernels look here:  [https://wiki.ubuntu.com/Kernel/MainlineBuilds?action=show&redirect=KernelTeam%2FMainlineBuilds]("https://wiki.ubuntu.com/Kernel/MainlineBuilds?action=show&redirect=KernelTeam%2FMainlineBuilds") 

An updated kernel may work. You can find out your kernel by running  ```
uname -r
```

---

### Post by colobix on 2011-04-17
Sure, but I will probably not install it. 
I hate installing all the software and games all over again, plus I REALLY hate the new unity thing. Yes I know they will include gnome two for this one, but after this version. No more good old panels and menus. Sorry, I'm getting off track here.
Isn't there anything we can do to fix this problem other than reinstalling or something crazy like that?
I mean, this happened after I first upgraded something and then started to tweak around like a hero :)
There must be something. Right?
OH and my kernel is 2.6.35-28-generic.
I thought that was the newest kernel.

EDIT: I used my brain now, which means I purged the OSS repository I had. I forgot all about it.
It removed and downgraded or upgraded things, and now I was able to run this find /lib/modules/`uname -r` | grep snd
 command.

```
2.6.35-28-generic
chris@chris-G73Sw:~$ 
chris@chris-G73Sw:~$ 
chris@chris-G73Sw:~$ 
chris@chris-G73Sw:~$ find /lib/modules/`uname -r` | grep snd
/lib/modules/2.6.35-28-generic/updates/alsa/snd-gina20.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-hda-codec-realtek.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-emu10k1-synth.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-es1968.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-echo3g.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-bt87x.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-korg1212.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-emu10k1x.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-ua101.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-hda-codec-cirrus.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-azt3328.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-indigoiox.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-atiixp-modem.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-hda-codec-si3054.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-portman2x4.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-lx6464es.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-timer.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-page-alloc.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-pcm.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-seq-midi-emul.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-seq-dummy.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-sb-common.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-hda-codec-analog.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-ca0106.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-vxpocket.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-mixart.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-oxygen-lib.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-hda-codec-idt.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-mpu401-uart.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-seq-device.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-au8820.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-tea575x-tuner.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-seq-virmidi.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-vx222.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-rme96.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-hda-intel.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-mona.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-i2c.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-opl3-synth.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-pt2258.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-als300.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-pcxhr.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-hrtimer.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-hwdep.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-intel8x0.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-cs8427.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-sonicvibes.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-ak4xxx-adda.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-cs4281.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-layla20.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-hda-codec-cmedia.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-usb-caiaq.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-aloop.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-hda-codec-via.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-cmipci.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-ice1712.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-mtpav.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-aw2.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-hdspm.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-indigodjx.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-mts64.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-cs46xx.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-soc-core.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-cs5530.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-gina24.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-ak4113.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-seq.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-intel8x0m.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-riptide.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-ak4114.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-seq-midi-event.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-via82xx.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-vx-lib.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-opl3-lib.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-virtuoso.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-ad1889.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-cs5535audio.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-seq-midi.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-sb16-dsp.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-ac97-codec.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-virmidi.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-fm801.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-ymfpci.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-darla20.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-hda-codec-conexant.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-pdplus.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-oxygen.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-util-mem.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-soc-wm-hubs.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-asihpi.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-hdsp.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-atiixp.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-darla24.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-ens1370.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-au8810.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-indigodj.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-serial-u16550.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-dummy.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-emu10k1.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-mia.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-rme32.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-ctxfi.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-layla24.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-trident.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-rawmidi.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-mpu401.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-nm256.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-pcsp.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-usb-us122l.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-hda-codec-nvhdmi.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-usb-6fire.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-emux-synth.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-rme9652.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-usb-usx2y.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-es1938.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-indigoio.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-pdaudiocf.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-usbmidi-lib.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-hda-codec-intelhdmi.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-maestro3.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-hda-codec-atihdmi.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-als4000.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-ak4117.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-ali5451.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-hda-codec.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-ens1371.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-hda-codec-ca0110.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-usb-audio.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-via82xx-modem.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-hda-codec-hdmi.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-indigo.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-au8830.ko
/lib/modules/2.6.35-28-generic/updates/alsa/snd-ice1724.ko

```

---

### Post by K_45 on 2011-04-17
OK. Try this:

```
gksu gedit /etc/modprobe.d/alsa-base.conf
```

then add this after the last options entry

```
snd-hda-codec-nvhdmi
```

and this next

```
snd-intel8x0m
```

and this next

```
snd-hda-intel
```

then save and reboot.

---

### Post by colobix on 2011-04-17
Before I reboot. Is this correct:

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
snd-hda-codec-nvhdmi
snd-intel8x0m
snd-hda-intel
```

---

### Post by K_45 on 2011-04-17
Add the extra stuff here

```

# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
*add extra modules here*

```

---

### Post by colobix on 2011-04-17
Here we go:
```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
snd-hda-codec-nvhdmi
snd-intel8x0m
snd-hda-intel
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
```

So, this is the document for all the supported hardware?

---

### Post by K_45 on 2011-04-17
Add options before all of them too, like the others (options snd-hda-codec-nvhdmi). My mistake, its late over here.

---

### Post by colobix on 2011-04-17
**Like this?**

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
snd-hda-codec-nvhdmi
snd-intel8x0m
snd-hda-intel
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
snd-hda-codec-nvhdmi
snd-intel8x0m
snd-hda-intel
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2

---

### Post by K_45 on 2011-04-17
This, then save and reboot:

# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-hda-codec-nvhdmi
options snd-intel8x0m
options snd-hda-intel

---

### Post by colobix on 2011-04-17
**OK Here. if this isn't correct, please post the correct one**.

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
snd-hda-codec-nvhdmi
snd-intel8x0m
snd-hda-intel
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
snd-hda-codec-nvhdmi
snd-intel8x0m
snd-hda-intel

---

### Post by K_45 on 2011-04-17
Exactly this, no changes, save and reboot:

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }

# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-hda-codec-nvhdmi
options snd-intel8x0m
options snd-hda-intel
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2]
```

Save and reboot.

---

### Post by colobix on 2011-04-17
Ok done. Now what do I do next?

---

### Post by K_45 on 2011-04-17
Well, does audio work?

```
aplay -l
```

---

### Post by colobix on 2011-04-17
Nope, couldn't find the sound card.

---

### Post by K_45 on 2011-04-17
Some of the remaining options are to manually compile the alsa drivers, a fresh reinstall, or install a newer kernel:

Option 1: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) - Scroll down

Option 2: Self-explanatory

Option 3: [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")

You'll find some guides for the 3rd option, but I won't be available till tomorrow. 

Well at least we had fun so far.:p

---

### Post by colobix on 2011-04-17
Option 1: TRied
Option 2: No way!
Option 3: I think I already have the latest kernel version.
I think version 28 is the newest. If not, it's at least the newest stable kernel. However, I also installed the version 27 and 26 with the alsa driver models that belongs to these kernels, but still no luck. So it can't be a kernel bug I think.
And a new kernel wouldn't work now anyway since the latest alsa module is the one that ends with 28.
Damn I will never ever update a package again in my whole life. When it works, I should just let it stay that way and disable the update manager.
I hate all these problems I get all the time. I just want everything to work as it should.
Isn't there anything I can do to fix this thing?

---

### Post by K_45 on 2011-04-17
No, updating is important. Seeing as your laptop is Sandy Bridge I don't think 10.10 has proper support for it. I'd clean install 11.04 when its released, then watch when updates I let through.

---

### Post by colobix on 2011-04-17
Sandy BRidge?
No it's an ASUS laptop.
Also, what you said about not supported is simply not true. As I said, everything worked fine.
But the audio stopped working after I tweaked around after I lost the volume control button after an idiotic update I did for two days ago or something.
So it basically happened because of something I did, and not because it has supporting hardware drivers.
I actually bought this pc for less than a month ago, and the guy who recommended this pc said it was a perfect linux pc with the most supportive hardware you can find out there. And I agree. Everything works fine and all. Well, now the audio is gone but that's not because of bad linux support. That's for sure. So are you sure you know what you are talking about here?
I Hope you do know. Because I came here for help and support so I can fix this problem, so I depending on you know to be honest with me.
Because reinstalling or upgrading to another version does not sound like a very legit solution to me.
I came here because I don't want to pay a lot of money for pc service crap.
So if I can do this myself, awesome. If not, then too bad.
And I want to point out something. People with no or little knowledge of what they are talking about should really not try to help.
I know the help is free and all, but following guides on random links when I don't even know where the problem is or when, how and why.
See what I mean? Finding random links and guides is something even I can do. I came here because I have seen all these guides and sites already, so I need help from a linux expert or something here, and not a newbie. 
And when you start to guess things and what not, that is when you should tell yourself to back out.
Because this is not a freaking game to me. Do you think I enjoy doing all this geek stuff while I could be using my time for something more important than sitting on a pc trying out million things? No I don't. So again, I need help from someone who can tell me exactly what to do and how to do it.

---

### Post by colobix on 2011-04-19
You said this was a kernel issue.
I tried v2.6.36-rc8 and v2.6.37-rc1.
So no, this is clearly not a kernel issue.
THe weird thing is though. WHen I checked gstreamer-properties, it worked on the first test, but not like 3 seconds later. Then when I clicked the test button it said it couldn't find any sound device.
So, I can't really see the logic here.

Are there any Linux distors where ALSA or OSS are the default sound system instead of PulseAudio?

---

### Post by K_45 on 2011-04-19
I'd try Debian. I've switched to it for a cleaner (not bloated) XFCE install. Seeing as you don't want to reinstall, I'd run the Debian XFCE live CD. It does use ALSA.

---

### Post by colobix on 2011-04-19
you mean it uses OSS?
Also, why would I wanna run a system from the live cd? Thank you anyway.
Do you have an explanation why the sound card worked with all the kernels I have upgraded to but only for like a few secords the first time I booted with them?

---

### Post by K_45 on 2011-04-19
ALSA, and the live CD will let you see if sound works. The other seems to have something to with the wrong modules being loaded.

---

### Post by colobix on 2011-04-19
Wrong models yes, I thought it had to do with something like that.
So, is there something I can do to remove and install the right models? Now I'm running the Kernel version 36 r8.
Btw, I really appreciated you helping me with this.

---

### Post by K_45 on 2011-04-19
Not sure, but you could try adding different modules from a few pages back until you have the right one.

---

### Post by colobix on 2011-04-19
What do you mean a few pages back?
You mean a few days back? Idk what version that was.

---

### Post by K_45 on 2011-04-19
Try running a Debian live CD, newer kernel, and your sound may work out of the box:

[http://live.debian.net/cdimage/daily-builds/squeeze/current/amd64/iso-hybrid/](http://live.debian.net/cdimage/daily-builds/squeeze/current/amd64/iso-hybrid/)

This is an updated daily build.

---

### Post by colobix on 2011-04-20
Thanks. 
It seams I found the root of this problem.
I ran lsmod, and it told me that both the osscoure and oss:usb modules are in use.
No wonder alsa gets ignored by the system.
Damn I wish these things was less complicated.

So, how do I remove the oss modules?
I have searched synaptic with no luck.

---

### Post by K_45 on 2011-04-20
This has instructions:  [http://ubuntuforums.org/showthread.php?t=649569](http://ubuntuforums.org/showthread.php?t=649569)

---

### Post by colobix on 2011-04-20
THey are still appearing in the lsmod list,
That thread showed you how to remove all oss packages, but when I typed in the command to get all the packages, I got this list over all oss packages. Not only installed packages, so I had to guess what I could or couldn't remove. All these krosspython and other packages that are not oss related came up.
But also, isn't this problem due to a configuration thing and not a package thing?

---

### Post by K_45 on 2011-04-20
You'll need to choose which packages to get rid off. This looks like a configuration error.

---

### Post by colobix on 2011-04-20
Ok so I could either try to find the configuration file or I could blacklist the OSS Module.
I have no idea how to do that.
So how do I fix this now?
But wait, if I remove the oss module file, that should fix it, right? How am I suppose to know what package it is?
Or maybe this will be solved if I remove everything alsa related and instead go for OSS.?
Damn I want this to be fixed now. I ******* hate these problems.

---

### Post by K_45 on 2011-04-20
I'd reinstall the OS you want rather than waste any more time. If you want alsa by default I'd install a Debian net install and choose what you want to install:  [http://www.debian.org/CD/netinst/](http://www.debian.org/CD/netinst/)  which is around 160MB.

---

### Post by colobix on 2011-04-20
Is that something you say because you don't know how to do this?
I can't reinstall every single time something happens. Something always happens in linux, so If I had to reinstall every single time, I wouldn't have time to use it for anything.
Also, if I can fix this know I will know what to do for future situations like this.
And these are the reasons why I start to think that maybe Linux is too advanced for me.
I never had these type of problems in Windows. And if I had problems there it was usually just viruses or spyware. Easy to get rid of.
So if I decide to reinstall ubuntu I would probably just quit using it.
BUt I don't want to give up linux, because I like it. So I guess that's why I give it new chances over and over again.

---

### Post by colobix on 2011-04-22
Yey I finally fixed the sound. I deleted all the conf files regarding oss and alsa, and then I reinstalled all the alsa packages.

Now to the last step. You said I should choose ALSA instead of OSS.
You said I can record both in and outgoing sound at the same time using audacity.
So how do I setup alsamixer?
Ok when I'm in the terminal, I type in alsamixer.
Then I go to the "capture" tab.
There I have Front Mic | Mic Boost | Capture | Capture 1 | Digital.
As I said, I want to record from mic and pc at the same time.
So again, how do I set it up? What am I suppose to mute / unmute etc?

---

### Post by colobix on 2011-04-23
Bump. Please help me with this

---

### Post by colobix on 2011-04-24
BUMP
This is important to me.

---

### Post by colobix on 2011-04-25
bump

---

### Post by K_45 on 2011-04-25
Mute digital and mic boost. Keep Front Mic and experiment with the Capture options.

---

