---
title: "Logitech USB mouse through PS/2 KVM switch"
date: 2010-06-01
forum: General Help
---

### Post by usdogi on 2010-06-01
Hi, I'm kinda new to Ubuntu, switched from Wnidows xp.
My PC is sharing i/o with another PC running WinXP via a cheap justcom PS/2 KVM switch. I plugged a Logitech M-RAU95 cordless mouse through a USB-PS/2 adapter to the KVM, and it works fine on the Windows PC, and also on the Ubuntu PC, but just until I switch from one to the other. Then it stops scrolling using the tracking wheel on the Ubuntu machine. I tried replacing the mouse with another USB mouse (a corded one, A4Tech), and am having no such problem - but I want to use the cordless one. Help will be much appreciated.

UriSh

---

### Post by happyhamster on 2010-06-01
- Hello. Could you perhaps show the output of the commands:

dmesg | grep input

uname -a

- To run a command, open a terminal (Applications-->Accessories-->Terminal), and type (or copy & paste) the command into it. (N.B. in a terminal, you can paste with ctrl-shift-v).

- For clarification: the first command looks in your log for input-related messages, and the second shows which ubuntu version you're using.

- It would also be useful to see the output of the first command when the mouse is working correctly and when it isn't. Good luck.

---

### Post by happyhamster on 2010-06-01
BTW, to copy the output *from* the terminal, highlight the text to be copied, and press ctrl-shift-c.

---

### Post by usdogi on 2010-06-01
Hi

This is with the cordless mouse:

dmesg | grep input
[    0.317553] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.317678] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.526448] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.579220] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[   23.807864] input: PS2++ Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input4

and this is with the corded A4Tech mouse:

dmesg | grep input
[    0.317553] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.317678] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.526448] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.579220] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[   23.807864] input: PS2++ Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[10722.197257] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input5

and the second command:

uname -a
Linux Uri 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

Thank you 

UriSh

---

### Post by happyhamster on 2010-06-01
- Could you perhaps also show the output of:

lsmod

- It will show which modules are loaded (and if they are in use). Thanks.

---

### Post by usdogi on 2010-06-01
sure:

lsmod
Module                  Size  Used by
saa7134_alsa           10380  1 
binfmt_misc             6587  1 
tda827x                 9240  1 
tda8290                12092  1 
tuner                  20412  1 
snd_ice1712            55129  0 
snd_ice17xx_ak4xxx      2547  1 snd_ice1712
snd_ak4xxx_adda         7364  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_cs8427              6522  1 snd_ice1712
snd_pcm_oss            35308  0 
snd_intel8x0           25588  2 
snd_ac97_codec        100646  2 snd_ice1712,snd_intel8x0
snd_mixer_oss          13746  1 snd_pcm_oss
snd_seq_dummy           1338  0 
snd_pcm                70662  5 saa7134_alsa,snd_ice1712,snd_pcm_oss,snd_intel8x0,snd_ac97_codec
ac97_bus                1002  1 snd_ac97_codec
snd_i2c                 4398  2 snd_ice1712,snd_cs8427
snd_seq_oss            26726  0 
snd_mpu401_uart         5617  1 snd_ice1712
snd_seq_midi            4557  0 
snd_rawmidi            19056  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
saa7134               143391  1 saa7134_alsa
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ir_common              38875  1 saa7134
v4l2_common            15431  2 tuner,saa7134
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
ppdev                   5259  0 
videodev               34361  3 tuner,saa7134,v4l2_common
v4l1_compat            13251  1 videodev
snd                    54148  23 saa7134_alsa,snd_ice1712,snd_ak4xxx_adda,snd_cs8427,snd_pcm_oss,snd_intel8x0,snd_ac97_codec,snd_mixer_oss,snd_pcm,snd_i2c,snd_seq_oss,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nvidia               4701243  32 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
videobuf_dma_sg        10782  2 saa7134_alsa,saa7134
usblp                  10481  0 
videobuf_core          16356  2 saa7134,videobuf_dma_sg
tveeprom               11102  1 saa7134
intel_agp              24177  1 
parport_pc             25962  1 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
psmouse                63245  0 
serio_raw               3978  0 
agpgart                31724  2 nvidia,intel_agp
shpchp                 28820  0 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
floppy                 53016  0 
8139too                18545  0 
8139cp                 16186  0 
mii                     4381  2 8139too,8139cp



thank you

---

### Post by happyhamster on 2010-06-01
> **usdogi said:**
> 
psmouse                63245  0
- This should be the module for your mouse. To test this, run:

sudo modprobe -r psmouse

- This will unload the module (if it doesn't work, could you show the error message here?). The mouse should stop working. Now reload the module:

sudo modprobe psmouse proto=imps

- And test if the mouse works (also if the mouse works any better after doing a kvm-switch to the XP machine). Good luck.

---

### Post by usdogi on 2010-06-01
Well, it kinda worked,

when I did as you suggested happyhamster, it worked great when I switched back and forth with the KVM, but after a restart I did for the check, then another KVM switch, it's back to the same problem / I suppose it rebooted  with the same module.

Is there anything I can do to lock the module?

---

### Post by happyhamster on 2010-06-01
> **usdogi said:**
> Well, it kinda worked,

when I did as you suggested happyhamster, it worked great when I switched back and forth with the KVM,
That's good news.

>  but after a restart I did for the check, then another KVM switch, it's back to the same problem / I suppose it rebooted  with the same module.
Yes, exactly.

> 
Is there anything I can do to lock the module?
- Yes; one way of making the change permanent is to create a new file in the /etc/modprobe.d/ folder:

gksudo gedit /etc/modprobe.d/psmouse

- This should launch your text editor. There should be no text yet, because we're creating a new file. Now, copy & paste these 2 lines:

# Get KVM switch and mouse to get along
options psmouse proto=imps

- Note that, outside of a terminal, copy = ctrl-c, and paste = ctrl-v (just as in winXP). Anyway, the first line is just a comment that will be ignored, the second line sets the proto=imps option.
Save the file (ctrl-s) and exit the editor. Reboot. Good luck.

---

### Post by usdogi on 2010-06-01
It works!

Thanks for all the help happyhamster, I guess that's agood way to get to know Ubuntu.

Urish

---

