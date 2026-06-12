---
title: "random &quot;Zebra stripe&quot; attack"
date: 2010-05-08
forum: General Help
---

### Post by comp3820 on 2010-05-08
I'm running 10.04, with default themes and no extra graphics turned on, but I randomly get a black screen with white stripes on the top half that freezes the entire computer. No shortcut keys work, pressing ctrl-alt-del and enter won't shut it down, and time doesn't help anything.

All the updates are installed, and booting off of the "old" kernel doesn't help.

I can't seem to correlate this to any program in particular, or to a certain time after startup.

Any ideas?

---

### Post by TwoToneSpirit on 2010-05-16
I have a computer with exactly the same issue.

---

### Post by comp3820 on 2010-05-17
The problem is still happening with me, much to the annoyance of anyone in our family who uses that computer. 

I've found the section in the system log about the crashes, and it records of cycle of things I can't remember right now, but what caught my eye was the constant repetition of "GPU hung" during the times that the computer was frozen. 

I'll post back later today with the exact log text.

---

### Post by comp3820 on 2010-05-17
Ok, this is the text form syslog (crashing appears to have started at 20:04:11

```
May 10 17:00:29 Weeda-Family AptDaemon: INFO: Initializing daemon
May 10 17:06:29 Weeda-Family AptDaemon: INFO: Quiting due to inactivity
May 10 17:06:29 Weeda-Family AptDaemon: INFO: Shutdown was requested
May 10 17:17:01 Weeda-Family CRON[1559]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 10 18:17:01 Weeda-Family CRON[2017]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 10 19:17:01 Weeda-Family CRON[2562]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 10 20:04:11 Weeda-Family kernel: [11108.380023] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
May 10 20:04:11 Weeda-Family kernel: [11108.380041] render error detected, EIR: 0x00000000
May 10 20:04:11 Weeda-Family kernel: [11108.380066] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 1630910 at 1630909)
May 10 20:04:13 Weeda-Family kernel: [11110.232040] [drm:i915_gem_idle] *ERROR* hardware wedged
May 10 20:04:13 Weeda-Family gnome-session[986]: WARNING: Detected that screensaver has left the bus
May 10 20:04:14 Weeda-Family acpid: client 870[0:0] has disconnected
May 10 20:04:14 Weeda-Family acpid: client connected from 2863[0:0]
May 10 20:04:14 Weeda-Family acpid: 1 client rule loaded
May 10 20:04:14 Weeda-Family pulseaudio[2860]: pid.c: Stale PID file, overwriting.
May 10 20:04:14 Weeda-Family pulseaudio[2860]: main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-jdl26tWLV5: Connection refused
May 10 20:04:14 Weeda-Family pulseaudio[2869]: pid.c: Daemon already running.
May 10 20:04:15 Weeda-Family kernel: [11112.327727] [drm:i915_gem_entervt_ioctl] *ERROR* Reenabling wedged hardware, good luck
May 10 20:04:15 Weeda-Family kernel: [11112.660013] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
May 10 20:04:15 Weeda-Family kernel: [11112.660025] render error detected, EIR: 0x00000000
May 10 20:04:15 Weeda-Family kernel: [11112.660935] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 1630914 at 1630909)
May 10 20:04:17 Weeda-Family kernel: [11114.716016] [drm:i915_gem_idle] *ERROR* hardware wedged
May 10 20:04:18 Weeda-Family acpid: client 2863[0:0] has disconnected
May 10 20:04:18 Weeda-Family acpid: client connected from 2874[0:0]
May 10 20:04:18 Weeda-Family acpid: 1 client rule loaded
May 10 20:04:19 Weeda-Family kernel: [11115.888952] [drm:i915_gem_entervt_ioctl] *ERROR* Reenabling wedged hardware, good luck
May 10 20:04:19 Weeda-Family kernel: [11116.224017] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
May 10 20:04:19 Weeda-Family kernel: [11116.224029] render error detected, EIR: 0x00000000
May 10 20:04:19 Weeda-Family kernel: [11116.224963] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 1630916 at 1630909)
May 10 20:04:21 Weeda-Family kernel: [11118.284016] [drm:i915_gem_idle] *ERROR* hardware wedged
May 10 20:04:21 Weeda-Family acpid: client 2874[0:0] has disconnected
May 10 20:04:21 Weeda-Family acpid: client connected from 2882[0:0]
May 10 20:04:21 Weeda-Family acpid: 1 client rule loaded
```

I don't have any idea what any of this means, but it seems interesting to me that it mentions the GPU - maybe its a graphics incompatibility.

This is on a Dell Dimension 2350 with integrated graphics.

---

### Post by soltanis on 2010-05-17
Post an lspci please?

```

lspci

```

In the terminal.
Also, not sure how you could determine this, but do you know what graphics driver you are running? It sounds like you would be using an Intel Integrated chipset, but knowing exactly the model would help.

EDIT:
Ah, I remember now, please also post the output of

```

lsmod

```

So that we can see which kernel modules you have running.

---

### Post by comp3820 on 2010-05-17
output of lspci:
```

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
```

output of lsmod:
```

Module                  Size  Used by
binfmt_misc             6587  1 
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_timer              19098  2 snd_pcm,snd_seq
vga16fb                11385  1 
vgastate                8961  1 vga16fb
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  282354  1 
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         29297  1 i915
dell_wmi                1793  0 
ppdev                   5259  0 
dcdbas                  5422  0 
drm                   162471  3 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
intel_agp              24177  2 i915
soundcore               6620  1 snd
parport_pc             25962  1 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
video                  17375  1 i915
agpgart                31724  3 drm,intel_agp
shpchp                 28820  0 
output                  1871  1 video
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
b44                    25542  0 
usbhid                 36110  0 
ssb                    37336  1 b44
mii                     4381  1 b44
floppy                 53016  0 
hid                    67032  1 usbhid
```


As for as the graphics goes, Dell says 
[SIZE=1]**Video**[/SIZE]
             [SIZE=1]Video controller[/SIZE]
      [SIZE=1]integrated Intel 3D  Extreme Graphics[/SIZE]

if the system chipset is the same as the graphics chipset, then Dell says

[SIZE=1]**System  Information**[/SIZE]
             [SIZE=1]System chip set[/SIZE]
      [SIZE=1]Intel 845GL[/SIZE]


Thanks for your help!

---

### Post by ph0852 on 2010-07-05
I seem to be having a similar problem.  My lspci and lsmod output are different, they are below.  I believe my graphics card is an Intel i915.  My syslog has a good number of message sets like the following:

Jul  5 09:30:05 ty-desktop kernel: [262845.837955] [drm:i915_gem_entervt_ioctl] *ERROR* Reenabling wedged hardware, good luck
Jul  5 09:30:05 ty-desktop kernel: [262846.172013] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Jul  5 09:30:05 ty-desktop kernel: [262846.172026] render error detected, EIR: 0x00000000
Jul  5 09:30:05 ty-desktop kernel: [262846.173352] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 164137 at 164123)
Jul  5 09:30:07 ty-desktop kernel: [262848.244020] [drm:i915_gem_idle] *ERROR* hardware wedged


ty@ty-desktop:~$ lspci 
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:05.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

ty@ty-desktop:~$ lsmod 
Module                  Size  Used by
binfmt_misc             6587  1 
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
arc4                    1153  2 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
rt2500usb              18141  0 
rt2x00usb               9703  1 rt2500usb
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
vga16fb                11385  1 
vgastate                8961  1 vga16fb
rt2x00lib              27509  2 rt2500usb,rt2x00usb
led_class               2864  1 rt2x00lib
i915                  282354  1 
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              204922  2 rt2x00usb,rt2x00lib
dell_wmi                1793  0 
drm_kms_helper         29297  1 i915
ppdev                   5259  0 
dcdbas                  5422  0 
cfg80211              126485  2 rt2x00lib,mac80211
soundcore               6620  1 snd
drm                   162471  3 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
parport_pc             25962  1 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
intel_agp              24177  2 i915
shpchp                 28820  0 
video                  17375  1 i915
output                  1871  1 video
agpgart                31724  3 drm,intel_agp
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36110  0 
hid                    67032  1 usbhid
b44                    25542  0 
ssb                    37336  1 b44
mii                     4381  1 b44
floppy                 53016  0

---

### Post by coldraven on 2010-07-05
My guess is that 10.04 does not like your Intel graphic card.
Last week I installed 10.04 on a machine that ran 8.04 perfectly and got exactly the same results as you have.
Any screensaver that uses open GL will trigger it. For example the Ant Spotlight.
If you cannot open the screensaver dialogue utility without causing a crash then 
press Alt+F2,
type "gconf-editor"
select "apps"
then "gnome-screensaver"
then make sure that mode is set to "blank-only" and themes to "[]"

see my screenshot for details

---

### Post by Pappasan on 2010-07-05
I too suffer from the same issue.  My syslog gives the following errors:
Jul  5 20:39:57 MrSmith kernel: [ 7636.341625] [drm:i915_gem_entervt_ioctl] *ERROR* Reenabling wedged hardware, good luck
Jul  5 20:39:57 MrSmith kernel: [ 7636.676014] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Jul  5 20:39:57 MrSmith kernel: [ 7636.676027] render error detected, EIR: 0x00000000
Jul  5 20:39:57 MrSmith kernel: [ 7636.676965] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 341513 at 341489)
Jul  5 20:39:59 MrSmith kernel: [ 7638.732017] [drm:i915_gem_idle] *ERROR* hardware wedged
Jul  5 20:40:00 MrSmith acpid: client 7759[0:0] has disconnected
Jul  5 20:40:00 MrSmith acpid: client connected from 7767[0:0]
Jul  5 20:40:00 MrSmith acpid: 1 client rule loaded
Jul  5 20:40:01 MrSmith kernel: [ 7639.885949] [drm:i915_gem_entervt_ioctl] *ERROR* Reenabling wedged hardware, good luck
Jul  5 20:40:01 MrSmith kernel: [ 7640.220011] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Jul  5 20:40:01 MrSmith kernel: [ 7640.220023] render error detected, EIR: 0x00000000
Jul  5 20:40:01 MrSmith kernel: [ 7640.220961] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 341515 at 341489)
Jul  5 20:40:03 MrSmith kernel: [ 7642.272014] [drm:i915_gem_idle] *ERROR* hardware wedged
Jul  5 20:40:03 MrSmith acpid: client 7767[0:0] has disconnected
will@MrSmith:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:02.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 82)

will@MrSmith:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
vboxnetadp              6390  0 
vboxnetflt             12740  0 
vboxdrv               168753  2 vboxnetadp,vboxnetflt
dm_crypt               11331  0 
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
arc4                    1153  2 
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rtl8187                50680  0 
snd                    54148  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                   5259  0 
mac80211              204922  1 rtl8187
led_class               2864  1 rtl8187
parport_pc             25962  1 
psmouse                63245  0 
soundcore               6620  1 snd
serio_raw               3978  0 
cfg80211              126485  2 rtl8187,mac80211
eeprom_93cx6            1333  1 rtl8187
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
shpchp                 28820  0 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
dm_raid45              81647  0 
xor                    15028  1 dm_raid45
usbhid                 36110  0 
hid                    67032  1 usbhid
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  1 
vgastate                8961  1 vga16fb
i915                  282354  1 
drm_kms_helper         29297  1 i915
drm                   162471  3 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
intel_agp              24177  2 i915
video                  17375  1 i915
e100                   28211  0 
mii                     4381  1 e100
output                  1871  1 video
floppy                 53016  0 
agpgart                31724  3 drm,intel_agp
ramzswap                6362  1 
xvmalloc                4074  1 ramzswap
lzo_decompress          2189  1 ramzswap
lzo_compress            1853  1 ramzswap

I have disabled all desktop effects and screensavers.  does this have to be a video issue or could it be audio?

---

### Post by steveneddy on 2010-07-05
What happens when you run

```
intel-gpu-tools
```

??

---

### Post by Johnny B on 2010-07-05
i have had this problem in the past... it drove me nuts for a few days. i was troubleshooting everything, it turned out to be my graphics card, as soon as it would heat up the computer crashed. possibly caused by some bad nvidia drivers released, i don't know how to prove that. I'm not sure this is your problem, but i hope this helps, good luck.

---

### Post by ph0852 on 2010-07-06
I'm very optimistic about this suggestion.  I don't have concrete evidence, but the screensaver very well could be related.  I think the system has been more stable since I up-ed the screen-saver timeout, and I had set the screensaver to be the ant-spotlight.  I implemented the suggestions and I'm crossing my fingers and toes.

---

### Post by ph0852 on 2010-07-06
The system made it through the night--big improvement.  But early on this morning it crashed again, without the zebra stripes, but the graphics went black.  
I'm not sure if this is related, but there are several message sets like the following in syslog
Jul  6 09:54:24 ty-desktop acpid: client connected from 5074[0:0]
Jul  6 09:54:24 ty-desktop acpid: 1 client rule loaded
Jul  6 09:54:25 ty-desktop kernel: [66081.460871] [drm:i915_gem_entervt_ioctl] *ERROR* Reenabling wedged hardware, good luck
Jul  6 09:54:25 ty-desktop kernel: [66081.792023] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Jul  6 09:54:25 ty-desktop kernel: [66081.792037] render error detected, EIR: 0x00000000
Jul  6 09:54:25 ty-desktop kernel: [66081.793358] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 649215 at 648548)
Jul  6 09:54:27 ty-desktop kernel: [66083.844023] [drm:i915_gem_idle] *ERROR* hardware wedged
Jul  6 09:54:28 ty-desktop acpid: client 5074[0:0] has disconnected

---

### Post by portsmouth7 on 2010-09-02
I am also having the random Zebra Stripe attack (exactly the same symptoms - freezes etc.). I have 10.04.1 installed on my Dell Dimension 2350.
 
Would an earlier version of Ubuntu be more stable? I absolutely love Ubuntu in all other areas but this random freeze happens every day for some reason.
 
Regards
 
Dave

---

### Post by Rasa1111 on 2010-09-02
> **portsmouth7 said:**
> I am also having the random Zebra Stripe attack (exactly the same symptoms - freezes etc.). I have 10.04.1 installed on my Dell Dimension 2350. w/1GB RAM
 
Would an earlier version of Ubuntu be more stable? I absolutely love Ubuntu in all other areas but this random freeze happens every day for some reason.
 
Regards
 
Dave

Hey Dave, 
 I have the same exact tower. 
Dimension 2350. 

 For the first month or (maybe a little more) of my using 10.04,
my PC would do the exact same thing. 
 Nothing would work to recover it but using the 'magic keys".
*reisub*
I learned that one quick, had to do it numerous times a day, most every day.  lol

 Then, one day, it just stopped doing it. 

It has only done it twice since then at totally random times.
in the span of 5-6 months. 

 The only thing I can think of was that I ran 
"sudo apt-get update" into terminal, and that's when it stopped...
but that is probably not true, 
it is just all I can think of that i did different from normal, before it stopped. lol

Ive wondered from time to time, if people were still having this issue,  
like i said, I havent seen it in months, and wondered if it just stopped happening on every bodies. 

 But i guess not....

dang..

 it was every day to, like you say, sometimes multiple times in a day, very annoying. 

 oh, in regards to 9.10,
That never did this to me when i had it installed, but, it would sometimes freeze up on me, and I couldnt recover it with any keys. 
I think thats when i may have had to learn reisub. lol

---

### Post by garethfoxwilliams on 2010-11-09
Sounds like the same issue here....

My parents' ( the are 80 and 78 y/o ) Dell Dimension 2350  has been running WinXP for years.

As I have just got them onto broadband, I have clean installed 10.04 Lucid.

During the post-install upgrade, there was a graphics crash ( I assume)  giving slightly slanted black/white stripes across the screen. this  persisted after an immediate restart, so I re-installed immediately.

Now, several weeks later, they are experiencing similar crashes on an occasional basis. 

Apparently things are usually OK after a restart, but recently, it was still bad after several restarts.

The next day, things were fine for a while and crashed later.

Sadly, they live several hours drive from me and so I can't get access  to the machine till December. However I'm looking for clues in the  meantime - any ideas?

---

### Post by comp3820 on 2010-11-09
I'm convinced that it was an incompatibility with my graphics card. 

However, since they were onboard graphics and the computer doesn't have a PCI-e or AGP slot, it's now sitting on the bottom shelf below the printer, gathering dust, there to stay for an undetermined amount of time (or until I get really really bored).

If this does ever get resolved I'll probably pull it back out again, but at this point it would be too much work, since I've transfered the HD over to another computer as well...

---

### Post by Rasa1111 on 2010-11-09
Just so you know...

10.10 doesnt seem to have this "zebra stripe attack" issue at all. 

 Not seen one graphics card issue with 10.10 on my Dell dimension 2350.
and Ive been using it for at least 2 months. possibly 3.

> However I'm looking for clues in the meantime - any ideas?

 Yes, install 10.10

---

### Post by garethfoxwilliams on 2010-11-10
Thanks.

All replies and research points towards a clean install of 10.10 being  the best option, which I can do for them in a month's time.

Cheers

---

