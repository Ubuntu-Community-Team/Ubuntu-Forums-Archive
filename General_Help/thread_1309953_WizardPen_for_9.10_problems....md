---
title: "WizardPen for 9.10 problems..."
date: 2009-11-01
forum: General Help
---

### Post by Silvenium on 2009-11-01
I'm having a problem with my Genius Mousepen 8x6 tablet. I went to [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen) and downloaded the .deb package for 9.10 / Karmic Koala. I updated from Jaunty to Karmic because of the problem that my tablet was not working and I was hoping it would work in the update. Anyway, installing the .deb package, I get this  message (exactly): ----- Unpacking geniusmousepen-driver (from .../GeniusMousePen-Driver_0.7.0_i386.deb) ... dpkg: error processing /tmp/GeniusMousePen-Driver_0.7.0_i386.deb (--install): trying to overwrite 'usr/lib/xorg/modules/input/wizardpen_drv.so', which is also in package wizardpen 0:0.7.0-alpha2  Removing configuration files...  Please reboot your system  OK  Errors were encountering while processing:  /tmp/GeniusMousePen-Driver_0.7.0_i386.deb -----  Any way to fix this? I have been without my tablet for months...I really really want to use it again.

---

### Post by Favux on 2009-11-01
Hi Silvenium,

It sounds like it doesn't like encountering a previously installed wizardpen_drv.so.  Which is a little strange.  So just rename it or move it.  Instead of:
```
usr/lib/xorg/modules/input/wizardpen_drv.so
```
call it say:
```
usr/lib/xorg/modules/input/wizardpen_drv.so.bak
```
and then see if the deb package installs.

---

### Post by Silvenium on 2009-11-01
I went to the Package Manager, uninstalled it completely, and tried using the .deb package again. So far so good--no problems so far. Let's see if the tablet actually works.    It did work---for a very very short while. Without pressure sensitivity. How am I going to get it to work again? Everything installed fine...help?

---

### Post by Favux on 2009-11-02
Hi Silvenium,

Sorry, I can't see you've posted again when you edit a post.  Sounds like we need to look at the wizardpen.fdi.  And a few more details would help.  How did it work for a short while?

In a terminal what does:
```
xinput --list
```
give?

---

### Post by Silvenium on 2009-11-02
You know, for some reason I plugged it in and it's working this morning.       I will tell you, though, it usually only 'works' randomly. It tends to only work when not conntected to the internet. .... "Virtual core pointer"	id=0	[XPointer] 	Num_buttons is 32 	Num_axes is 2 	Mode is Relative 	Motion_buffer is 256 	Axis 0 : 		Min_value is -1 		Max_value is -1 		Resolution is 0 	Axis 1 : 		Min_value is -1 		Max_value is -1 		Resolution is 0 "Virtual core keyboard"	id=1	[XKeyboard] 	Num_keys is 248 	Min_keycode is 8 	Max_keycode is 255 "Power Button"	id=3	[XExtensionKeyboard] 	Type is KEYBOARD 	Num_keys is 248 	Min_keycode is 8 	Max_keycode is 255 "Power Button"	id=4	[XExtensionKeyboard] 	Type is KEYBOARD 	Num_keys is 248 	Min_keycode is 8 	Max_keycode is 255 "Macintosh mouse button emulation"	id=5	[XExtensionPointer] 	Type is MOUSE 	Num_buttons is 5 	Num_axes is 2 	Mode is Relative 	Motion_buffer is 256 	Axis 0 : 		Min_value is -1 		Max_value is -1 		Resolution is 1 	Axis 1 : 		Min_value is -1 		Max_value is -1 		Resolution is 1 "Logitech Logitech USB Keyboard"	id=2	[XExtensionKeyboard] 	Type is KEYBOARD 	Num_keys is 248 	Min_keycode is 8 	Max_keycode is 255 "UC-LOGIC Tablet WP8060U"	id=6	[XExtensionPointer] 	Type is WizardPen Tablet 	Num_buttons is 6 	Num_axes is 3 	Mode is Absolute 	Motion_buffer is 256 	Axis 0 : 		Min_value is 0 		Max_value is 1024 		Resolution is 1000 	Axis 1 : 		Min_value is 0 		Max_value is 768 		Resolution is 1000 	Axis 2 : 		Min_value is 0 		Max_value is 1023 		Resolution is 1000 "Logitech USB RECEIVER"	id=7	[XExtensionPointer] 	Type is MOUSE 	Num_buttons is 24 	Num_axes is 2 	Mode is Relative 	Motion_buffer is 256 	Axis 0 : 		Min_value is -1 		Max_value is -1 		Resolution is 1 	Axis 1 : 		Min_value is -1 		Max_value is -1 		Resolution is 1 ..... By the way, how do you get pressure sensitivity to work on here? I do a lot of artwork, so it would be highly appreciated.

---

### Post by Favux on 2009-11-02
Hi Silvenium,

Ouch, that hurt my eyes.  Use the Code tags ('#' top right of post) next time please.  This is what we're interested in:
```
"UC-LOGIC Tablet WP8060U" id=6 [XExtensionPointer]
 Type is WizardPen Tablet
 Num_buttons is 6
 Num_axes is 3
 Mode is Absolute
 Motion_buffer is 256
 Axis 0 : Min_value is 0
 Max_value is 1024
 Resolution is 1000
 Axis 1 : Min_value is 0
 Max_value is 768
 Resolution is 1000
 Axis 2 : Min_value is 0
 Max_value is 1023
 Resolution is 1000
```
And we want to look at the wizardpen.fdi too.

---

### Post by Silvenium on 2009-11-02
Would this be it? ```
<?xml version="1.0" encoding="ISO-8859-1" ?>
 <deviceinfo version="0.2">
 <device>
 <!-- This MUST match with the name of your tablet -->
 <match key="info.product" contains="UC-LOGIC Tablet WP8060U">
 <merge key="input.x11_driver" type="string">wizardpen</merge>
 <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
 <merge key="input.x11_options.TopX" type="string">5619</merge>
 <merge key="input.x11_options.TopY" type="string">6554</merge>
 <merge key="input.x11_options.BottomX" type="string">29405</merge>
 <merge key="input.x11_options.BottomY" type="string">29671</merge>
 <merge key="input.x11_options.MaxX" type="string">29405</merge>
 <merge key="input.x11_options.MaxY" type="string">29671</merge>
 </match>
 </device>
</deviceinfo>
```

---

### Post by Favux on 2009-11-02
Hi Silvenium,

Nice job.  That's it.  What's it called and where is it located?

I'll take a look at it and your xinput and see if there's something we can do.

---

### Post by Silvenium on 2009-11-02
What's what called? 
The Wizardpen file? It's called '99-x11-wizardpen.fdi' and located in /etc/hal/fdi/policy.

My tablet however is a Genius 8x6 MousePen.

---

### Post by Favux on 2009-11-03
Hi Silvenium,

I'm guessing you've seen this [site]("http://www.jpbouza.com.ar/ESP2/tutoriales/gnulinux/genius-tablet/id/en").

The .fdi seems to be missing a line I would think it should have:
```
      <merge key="input.x11_options.Type" type="string">stylus</merge>
```
so
```
<?xml version="1.0" encoding="ISO-8859-1" ?>

<deviceinfo version="0.2">
  <device>
        <!-- This MUST match with the name of your tablet -->
    <match key="info.product" contains="UC-LOGIC Tablet WP8060U">
      <merge key="input.x11_driver" type="string">wizardpen</merge>
      <merge key="input.x11_options.Type" type="string">stylus</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
      <merge key="input.x11_options.TopX" type="string">5619</merge>
      <merge key="input.x11_options.TopY" type="string">6554</merge>
      <merge key="input.x11_options.BottomX" type="string">29405</merge>
      <merge key="input.x11_options.BottomY" type="string">29671</merge>
      <merge key="input.x11_options.MaxX" type="string">29405</merge>
      <merge key="input.x11_options.MaxY" type="string">29671</merge>
    </match>
  </device>
</deviceinfo>
```
Let's see if that keeps it working now.  There's a couple other things we can try too.

---

### Post by Silvenium on 2009-11-03
The tablet's been working, but pressure still doesn't work on Gimp. Works on Inkscape, but not Gimp--which is what I use for my drawings.

---

### Post by Favux on 2009-11-03
Hi Silvenium,

Alright.  See post #33 here:  [http://ubuntuforums.org/showthread.php?t=1151464](http://ubuntuforums.org/showthread.php?t=1151464)  And instructions near the bottom of this [Wacom wiki]("https://help.ubuntu.com/community/Wacom").

---

### Post by Silvenium on 2009-11-04
Unfortunately, man, I have tried that many times.  For...some reason this time it worked. I don't know WHY it decided to randomly work... but I'm not questioning it.   Thanks again. You've really helped a lot of us Ubuntu users (I've only been at this OS for about 6 months now) so you have my gratitude. =)

---

### Post by Favux on 2009-11-04
Hi Silvenium,

> Unfortunately, man, I have tried that many times. For...some reason this time it worked. I don't know WHY it decided to randomly work... but I'm not questioning it.
Hah!  :p  Your welcome, glad it's working.

---

### Post by Favux on 2009-11-14
Hi Silvenium,

We can sure give it a try.  Did anything happen before it stopped working this time?  Some updates or something?  Did you try rebooting a few times?  And unplugging and replugging, etc?

Do you know if there is something like a wizardpen.ko?  If it's in:
```
lsmod
```
when the tablet works and not when the tablet doesn't we may be able to fix that.  You could do a find on it or try:
```
modinfo -d wizardpen
```
Course that depends on us knowing the name.

---

### Post by Silvenium on 2009-11-14
I'm not seeing anything--you can try looking:

```
silvenium@silvenium-desktop:~$ lsmod
Module                  Size  Used by
joydev                 10272  0 
xt_limit                2176  8 
xt_tcpudp               2780  12 
ipt_LOG                 5344  8 
ipt_MASQUERADE          2204  0 
xt_DSCP                 2844  0 
ipt_REJECT              2812  1 
nf_conntrack_irc        4992  0 
nf_conntrack_ftp        6880  0 
xt_state                1820  6 
arc4                    1660  2 
ecb                     2524  2 
rt73usb                26336  0 
crc_itu_t               1852  1 rt73usb
rt2x00usb              11548  1 rt73usb
rt2x00lib              29756  2 rt73usb,rt2x00usb
led_class               4096  1 rt2x00lib
input_polldev           3716  1 rt2x00lib
mac80211              181236  2 rt2x00usb,rt2x00lib
cfg80211               93052  2 rt2x00lib,mac80211
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
iptable_nat             5500  0 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
nf_nat                 17808  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      13352  9 iptable_nat,nf_nat
snd_hwdep               7200  1 snd_hda_codec
nf_conntrack           67608  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
nf_defrag_ipv4          1756  1 nf_conntrack_ipv4
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
iptable_mangle          3452  0 
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iptable_filter          3100  1 
soundcore               7264  1 snd
nvidia               9586440  36 
i2c_nforce2             6784  0 
ip_tables              11692  3 iptable_nat,iptable_mangle,iptable_filter
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
psmouse                56180  0 
agpgart                34988  1 nvidia
lp                      8964  0 
k8temp                  4188  0 
serio_raw               5280  0 
x_tables               16544  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,ip_tables
parport                35340  2 ppdev,lp
usbhid                 38208  0 
forcedeth              54152  0 

```

Back in the day (when my tablet picked up) I remember it having a 'uc logic' name. 
As for the second code...

```
silvenium@silvenium-desktop:~$ modinfo -d wizardpen
ERROR: modinfo: could not find module wizardpen

```

---

### Post by Favux on 2009-11-14
Hi Silvenium,

Well the tablet isn't working so it wouldn't be in lsmod right now.  Maybe we have the name wrong, or there isn't one.  It could be the usbhid(.ko) is it and that's what feeds Xinput/Xserver where wizardpen_drv.so (the X driver) picks it up.

What does:
```
xinput --list
```
show?

---

### Post by Silvenium on 2009-11-14
```
"Virtual core pointer"    id=0    [XPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
"Virtual core keyboard"    id=1    [XKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Logitech Logitech USB Keyboard"    id=2    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Power Button"    id=3    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Power Button"    id=4    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Macintosh mouse button emulation"    id=5    [XExtensionPointer]
    Type is MOUSE
    Num_buttons is 5
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"Logitech USB RECEIVER"    id=6    [XExtensionPointer]
    Type is MOUSE
    Num_buttons is 24
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1

```

---

### Post by Favux on 2009-11-14
Hi Silvenium,

You could be right.  Another .fdi/driver like evdev may be grabbing it.  We need to look at Xorg.0.log and see what's happening after a fresh reboot.

---

### Post by Silvenium on 2009-11-14
Here's that log.

```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux silvenium-desktop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
Kernel command line: root=UUID=5fe0e33f-21bd-480e-b008-e3246233ec62 ro quiet splash 
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov 14 17:40:11 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:0:5:0) 10de:0241:103c:2a45 nVidia Corporation C51 [GeForce 6150 LE] rev 162, Mem @ 0xfc000000/16777216, 0xe0000000/268435456, 0xfb000000/16777216, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [17] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [18] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [19] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [21] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [23] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  185.18.36  Fri Aug 14 17:50:12 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  185.18.36  Fri Aug 14 17:24:40 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 00@00:05:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [17] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [18] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [19] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [21] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [23] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6150 LE (C51) at PCI:0:5:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.51.28.39.24
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6150 LE at PCI:0:5:0:
(--) NVIDIA(0):     hp vx74 (CRT-0)
(--) NVIDIA(0): hp vx74 (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(--) NVIDIA(0): DPI set to (81, 81); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [17] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [18] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [19] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [21] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [23] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) config/hal: Adding input device Logitech Logitech USB Keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) Logitech Logitech USB Keyboard: always reports core events
(**) Logitech Logitech USB Keyboard: Device: "/dev/input/event3"
(II) Logitech Logitech USB Keyboard: Found keys
(II) Logitech Logitech USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech Logitech USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device Logitech USB RECEIVER
(**) Logitech USB RECEIVER: always reports core events
(**) Logitech USB RECEIVER: Device: "/dev/input/event4"
(II) Logitech USB RECEIVER: Found 20 mouse buttons
(II) Logitech USB RECEIVER: Found x and y relative axes
(II) Logitech USB RECEIVER: Found scroll wheel(s)
(II) Logitech USB RECEIVER: Configuring as mouse
(**) Logitech USB RECEIVER: YAxisMapping: buttons 4 and 5
(**) Logitech USB RECEIVER: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB RECEIVER" (type: MOUSE)
(**) Logitech USB RECEIVER: (accel) keeping acceleration scheme 1
(**) Logitech USB RECEIVER: (accel) filter chain progression: 2.00
(**) Logitech USB RECEIVER: (accel) filter stage 0: 20.00 ms
(**) Logitech USB RECEIVER: (accel) set acceleration profile 0
(II) Logitech USB RECEIVER: initialized for relative axes.
(II) config/hal: Adding input device UC-LOGIC Tablet WP8060U
(II) LoadModule: "wizardpen"
(II) Loading /usr/lib/xorg/modules/input//wizardpen_drv.so
(II) Module wizardpen: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) UC-LOGIC Tablet WP8060U: TopX = 5619
(**) UC-LOGIC Tablet WP8060U: TopY = 6554
(**) UC-LOGIC Tablet WP8060U: BottomX = 29405
(**) UC-LOGIC Tablet WP8060U: BottomY = 29671
(**) Option "Device" "/dev/input/event6"
(--) Wizardpen Tablet MaxX:0 MaxY:0 MaxZ:0
(**) UC-LOGIC Tablet WP8060U is in absolute mode
(**) Option "SendCoreEvents" "true"
(**) UC-LOGIC Tablet WP8060U: always reports core events
(II) XINPUT: Adding extended input device "UC-LOGIC Tablet WP8060U" (type: WizardPen Tablet)
(II) UC-LOGIC Tablet WP8060U Increment: 1
(EE) UC-LOGIC Tablet WP8060U: error reading device /dev/input/event6: No such device
(II) config/hal: removing device UC-LOGIC Tablet WP8060U
(II) UnloadModule: "wizardpen"
```Look! UC logic--my tablet--is on it(the bottom)...

---

### Post by Favux on 2009-11-14
Hi Silvenium,

It looks like everything is working right to start with:
```
(II) config/hal: Adding input device UC-LOGIC Tablet WP8060U
(II) LoadModule: "wizardpen"
(II) Loading /usr/lib/xorg/modules/input//wizardpen_drv.so
(II) Module wizardpen: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) UC-LOGIC Tablet WP8060U: TopX = 5619
(**) UC-LOGIC Tablet WP8060U: TopY = 6554
(**) UC-LOGIC Tablet WP8060U: BottomX = 29405
(**) UC-LOGIC Tablet WP8060U: BottomY = 29671
(**) Option "Device" "/dev/input/event6"
(--) Wizardpen Tablet MaxX:0 MaxY:0 MaxZ:0
(**) UC-LOGIC Tablet WP8060U is in absolute mode
(**) Option "SendCoreEvents" "true"
(**) UC-LOGIC Tablet WP8060U: always reports core events
(II) XINPUT: Adding extended input device "UC-LOGIC Tablet WP8060U" (type: WizardPen Tablet)
(II) UC-LOGIC Tablet WP8060U Increment: 1
(EE) UC-LOGIC Tablet WP8060U: error reading device /dev/input/event6: No such device
(II) config/hal: removing device UC-LOGIC Tablet WP8060U
(II) UnloadModule: "wizardpen"
```
And then this happens:
```
II) XINPUT: Adding extended input device "UC-LOGIC Tablet WP8060U" (type: WizardPen Tablet)
(II) UC-LOGIC Tablet WP8060U Increment: 1
(EE) UC-LOGIC Tablet WP8060U: error reading device /dev/input/event6: No such device
(II) config/hal: removing device UC-LOGIC Tablet WP8060U
(II) UnloadModule: "wizardpen"
```
Not sure what's happening.  It may be the usb signal dropping and it trying to reacquire but nothing is on /event6 anymore.  Could the usb port be bad?  Not enough power to power the tablet.  You don't seem to be on a hub.  The usb cable from the tablet is good?

---

### Post by Silvenium on 2009-11-14
Oh, thank you so much! It was a bit loose where the cable plugged into the actual tablet; I pushed it in and it works...for now. I'll let you know in the future if things become troublesome again.

Fauvx, you have been such a help for me and others, I hope you know that! You definitely have my respect!

---

### Post by Favux on 2009-11-14
Hi Silvenium,

Good, working again!  You're welcome.

---

