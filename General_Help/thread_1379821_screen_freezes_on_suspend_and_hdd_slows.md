---
title: "screen freezes on suspend and hdd slows"
date: 2010-01-13
forum: General Help
---

### Post by rileyp on 2010-01-13
Hi all
 When ever I choose suspend to shutdown the hard drive slows and  the picture on the screen freezes
The mouse and kb are disabled and the cpu fan keeps running.
My hardware in in my sig below
I have turned off automaitic updates straight after installing from disc as the last time I had it switched on after a few updates I got repeated ata drive read errors and the pc would freeze for a while being unable to read from the hdd. I have run wd diagnostics on the drive and it works fine.
To fix this problem I did a  clean install after messing round for 3 days and achieving nothing.
 I have an arch partition that works fine as well although I have not attempted to get suspend working with it. ( hal error)
I have read a few thread on the net and tried entering the swap disks uuid into grub.
This has not helped
Where do I start?
cheers rileyp

system specs
Mythbuntu front end asrock ion 320gsata 1gig ddr2 Karmic 2.6.31.14
Mythbuntu backend gagc230d 500g wd 1g ddr2 karmic 2.6.31.14
2 tuners:visionplus dvb and leadtek gold usb

---

### Post by rileyp on 2010-01-13
the suspend log looks like this ```

Wed Jan 13 13:16:52 EST 2010: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000record suspend suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk suspend suspend: Adding quirks from HAL: --quirk-dpms-on --quirk-dpms-suspend --quirk-vbe-post --quirk-vbemode-restore --quirk-vbestate-restore --quirk-vga-mode-3 
success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: Linux mythserver 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
Module                  Size  Used by
nfsd                  241100  9 
nfs                   271912  0 
lockd                  67724  2 nfsd,nfs
nfs_acl                 2844  2 nfsd,nfs
auth_rpcgss            36576  2 nfsd,nfs
sunrpc                191712  10 nfsd,nfs,lockd,nfs_acl,auth_rpcgss
snd_hda_codec_realtek   203328  1 
dst                    27716  1 
dvb_bt8xx              15072  1 
iptable_filter          3100  0 
snd_hda_intel          26920  1 
ip_tables              11692  1 iptable_filter
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
tda18271               35556  1 
snd_pcm_oss            37920  0 
bt878                   9992  2 dst,dvb_bt8xx
bttv                  118996  2 dvb_bt8xx,bt878
snd_mixer_oss          16028  1 snd_pcm_oss
ir_common              48512  1 bttv
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
af9013                 20608  1 
v4l2_common            17500  1 bttv
x_tables               16544  1 ip_tables
snd_seq_dummy           2656  0 
videodev               36736  2 bttv,v4l2_common
snd_seq_oss            28576  0 
v4l1_compat            14496  1 videodev
snd_seq_midi            6432  0 
videobuf_dma_sg        12544  1 bttv
snd_rawmidi            22208  1 snd_seq_midi
videobuf_core          17952  2 bttv,videobuf_dma_sg
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
xfs                   512064  2 
exportfs                4412  2 nfsd,xfs
psmouse                56180  0 
dvb_usb_af9015         25308  12 
btcx_risc               4740  1 bttv
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
tveeprom               11872  1 bttv
ppdev                   6688  0 
dvb_usb                16200  1 dvb_usb_af9015
dvb_core               87364  3 dst,dvb_bt8xx,dvb_usb
parport_pc             31940  1 
serio_raw               5280  0 
lp                      8964  0 
snd                    59204  14 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport                35340  3 ppdev,parport_pc,lp
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
usbhid                 38208  0 
i915                  221064  2 
drm                   159584  2 i915
i2c_algo_bit            5760  2 bttv,i915
video                  19380  1 i915
output                  2780  1 video
r8169                  32064  0 
mii                     5212  1 r8169
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
             total       used       free     shared    buffers     cached
Mem:       1018436    1004796      13640          0       6532     721560
-/+ buffers/cache:     276704     741732
Swap:      1951856          0    1951856
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
/etc/pm/sleep.d/10_grub-common suspend suspend: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode suspend suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend: kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend: success.
Wed Jan 13 13:16:54 EST 2010: performing suspend

```

---

