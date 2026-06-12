---
title: "Sound Problems"
date: 2012-01-08
forum: General Help
---

### Post by Treyonator56 on 2012-01-08
Hey guys. I didn't think I would have to post here again, but I ran into another problem. I tried running Skype on Ubuntu 11.10. It works fine except for the microphone. I used the recorder to check to see if it was a Skype problem and it didn't work either. I downloaded PulseAudio Volume Control and I managed to get the recorder to work temporarily. I had to make the recording work out of the front-right side or the front-left side. If both sides were turned on, the microphone wouldn't work. So, I slid the bar down on the front-left side and it worked. But, the recorder would slowly push it back to 100%. I readjusted it and wanted to see if it worked in Skype. No such luck. Is there any way I can fix this? I have already unchecked the box in Skype so it shouldn't change my volume levels. This is really starting to bug me...lol

Here are my system specs:

```
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```

Not sure if that's what you need to see...=)

---

### Post by Treyonator56 on 2012-01-08
Can anyone help with this problem?

---

### Post by kinghiram on 2012-01-08
I'm having almost the same problem, man. Have you tried:
```
alsa suspend
```
I think we might be asking in the wrong place, maybe.

---

### Post by Treyonator56 on 2012-01-09
That isn't a working code for me. I probably don't have that package installed. I wonder where we should post then. This *is* General Help...Maybe its a reoccurring problem no one has the answer to?

---

### Post by Treyonator56 on 2012-01-09
Anyone know how to fix this? =(

---

### Post by imachavel on 2012-01-09
before you get into drivers and gnome and all this, I want to ask a question. Have you noticed that fresh linux installs almost always have the sound muted? This is a common problem, try looking for different sound managers to un mute, often times in ubuntu there are more then one, I don't know why.

ww.murga-linux.com/puppy/viewtopic.php?t=18550

[http://www.ehow.com/how_8095373_check-linux-drivers-installed.html](http://www.ehow.com/how_8095373_check-linux-drivers-installed.html)

will show you this:

lsmod | more
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
dm_crypt               22565  0 
lp                     17455  0 
snd_hda_codec_hdmi     31426  1 
snd_hda_intel          24262  1 
snd_hda_codec          91754  2 snd_hda_codec_hdmi,snd_hda_intel
snd_usb_audio         100880  1 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  6 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,s
nd_usb_audio,snd_intel8x0,snd_ac97_codec
snd_hwdep              13276  2 snd_hda_codec,snd_usb_audio
snd_usbmidi_lib        24558  1 snd_usb_audio
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_rawmidi            25241  2 snd_usbmidi_lib,snd_seq_midi
ppdev                  12849  0 
snd_seq_device         14172  3 snd_seq_midi,snd_seq,snd_rawmidi
gspca_sonixj           32391  0 
parport_pc             32114  1 
gspca_main             27610  1 gspca_sonixj
videodev               85626  1 gspca_main
parport                40930  3 lp,ppdev,parport_pc
snd                    55902  21 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,
snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_
seq,snd_timer,snd_rawmidi,snd_seq_device
joydev                 17393  0 
soundcore              12600  1 snd
psmouse                73673  0 
snd_page_alloc         14115  3 snd_hda_intel,snd_intel8x0,snd_pcm
serio_raw              12990  0 
dcdbas                 14098  0 
binfmt_misc            17292  1 
squashfs               36095  1 
overlayfs              27481  1 
nls_utf8               12493  1 
isofs                  39549  1 
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622589  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
radeon                925020  3 
usbhid                 41905  0 
hid                    77367  1 usbhid
ttm                    65224  1 radeon
floppy                 60310  0 
e100                   36289  0 
drm_kms_helper         32889  1 radeon
drm                   192226  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13199  1 radeon




that is my output. I'm surprised many drivers aren't installed as all devices are working correctly. But then I am booted to a live cd also, as my partition table is messed up. I don't know if that effects anything :confused:

---

### Post by Treyonator56 on 2012-01-10
Yes, I checked and all my sound bars are unmuted. Still doesn't work. And that code also doesn't work in terminal.

---

