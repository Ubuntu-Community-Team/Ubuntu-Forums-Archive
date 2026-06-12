---
title: "Ubuntu not detecting higher resolution!!"
date: 2012-10-02
forum: General Help
---

### Post by momin90909 on 2012-10-02
I checked displays and it shows 1024*768 maximum resolution. But in windows I have used 1280*1024 resolution. I have googled lot. But can not find permanent solution. Thanks.

---

### Post by 2F4U on 2012-10-02
What are your hardware specs and what version of Ubuntu are you running?

---

### Post by cortman on 2012-10-02
The outputs of

```
lspci
```

and

```
xrandr
```

would also be helpful. As well as 

```
lsmod
```

---

### Post by momin90909 on 2012-10-03
xrandr


Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  





lspci

00:00.0 Host bridge: Intel Corporation 82Q963/Q965 Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)
00:03.0 Communication controller: Intel Corporation 82Q963/Q965 HECI Controller (rev 02)
00:03.2 IDE interface: Intel Corporation 82Q963/Q965 PT IDER Controller (rev 02)
00:03.3 Serial controller: Intel Corporation 82Q963/Q965 KT Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DM Gigabit Network Connection (rev 02)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HO (ICH8DO) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA Controller [IDE mode] (rev 02)



lsmod

Module                  Size  Used by
tpm_infineon           17296  0 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
hp_wmi                 13652  0 
ppdev                  12849  0 
sparse_keymap          13658  1 hp_wmi
binfmt_misc            17292  1 
snd_hda_codec_realtek   174055  1 
dm_multipath           22710  0 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
psmouse                72919  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
serio_raw              13027  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
tpm_tis                18308  0 
mac_hid                13077  0 
parport_pc             32114  1 
mei                    36570  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
i915                  414672  4 
floppy                 60310  0 
drm_kms_helper         45466  1 i915
usbhid                 41906  0 
wmi                    18744  1 hp_wmi
hid                    77367  1 usbhid
drm                   197692  5 i915,drm_kms_helper
e1000e                140005  0 
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
zram                   18193  1 


i am using precise pangolin
And my hardware is standard hp dc7700 with q965/963 graphics.

---

### Post by raja.genupula on 2012-10-03
use this to set custom resolutions
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by momin90909 on 2012-10-09
I tried out above page, when i set up xorg.conf, now i cant even get 1024*768, i am stuck at 800*600.

---

### Post by raja.genupula on 2012-10-09
> **momin90909 said:**
> I tried out above page, when i set up xorg.conf, now i cant even get 1024*768, i am stuck at 800*600.


have you backup your old xorg file ?

---

### Post by momin90909 on 2012-10-11
I didn't have any xorg.conf file. I reinstalled ubuntu. Still any help would be appreciated.

---

### Post by raja.genupula on 2012-10-11
[http://askubuntu.com/questions/109282/tried-every-solution-but-my-monitor-resolution-is-still-stuck-at-640x480](http://askubuntu.com/questions/109282/tried-every-solution-but-my-monitor-resolution-is-still-stuck-at-640x480)

[http://askubuntu.com/questions/174453/i-am-not-able-to-set-resolution-at-1280-x-1024](http://askubuntu.com/questions/174453/i-am-not-able-to-set-resolution-at-1280-x-1024)

---

