---
title: "Problem with USB audio"
date: 2012-01-17
forum: General Help
---

### Post by spanishconnector on 2012-01-17
Hi there,

I installed Lubuntu 64 bit 11.04 and upgraded right away to 11.10 on a desktop computer, with a N68S3+ motherboard and AMD Sempron processor.

Audio works fine with the non-USB outputs, but the USB connectors do some things I don't understand: they detect and read USB flash drives, they even let me hear audio with Skype and Logitech headset (low volume that can not be controlled by the volume icon), but they will not let me hear audio from the web (YouTube, Pandora, etc. using Chromium) nor mp3 files.

So even though I can not control USB volume on Skype, I can hear it with my USB Logitech headset. I don't understand why I can not hear anything from web or mp3 files using my USB Logitech headset.

I am new to Lubuntu and Ubuntu. 

Please help. Thank you in advance.

---

### Post by imachavel on 2012-01-17
type this in:

lsmod

my lsmod output:

Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39549  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               251814  3 vboxpci,vboxnetadp,vboxnetflt
vesafb                 13489  1 
ppdev                  12849  0 
joydev                 17393  0 
snd_usb_audio         100880  1 
snd_usbmidi_lib        24558  1 snd_usb_audio
gspca_sonixj           32391  0 
gspca_main             27610  1 gspca_sonixj
dcdbas                 14098  0 
videodev               85626  1 gspca_main
ip6t_LOG               16846  4 
xt_hl                  12465  6 
ip6t_rt                12473  3 
nf_conntrack_ipv6      13581  7 
nf_defrag_ipv6         13139  1 nf_conntrack_ipv6
ipt_REJECT             12512  1 
ipt_LOG                12783  5 
xt_limit               12541  12 
psmouse                73673  0 
xt_tcpudp              12531  19 
xt_addrtype            12596  4 
serio_raw              12990  0 
xt_state               12514  14 
ip6table_filter        12711  1 
ip6_tables             22528  3 ip6t_LOG,ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_nat_ftp             12595  0 
nf_nat                 24958  1 nf_nat_ftp
nf_conntrack_ipv4      19084  9 nf_nat
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
nf_conntrack_ftp       13183  1 nf_nat_ftp
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
nf_conntrack           70103  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12706  1 
fglrx                2595537  170 
snd_hda_codec_hdmi     31426  1 
parport_pc             32114  1 
snd_hda_intel          24262  1 
snd_hda_codec          91754  2 snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13276  2 snd_usb_audio,snd_hda_codec
snd_pcm                80435  6 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ip_tables              18106  1 iptable_filter
x_tables               21975  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd_timer              28932  2 snd_pcm,snd_seq
binfmt_misc            17292  1 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  21 snd_usb_audio,snd_usbmidi_lib,snd_intel8x0,snd_ac97_codec,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  3 snd_intel8x0,snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
e100                   36289  0 
floppy                 60310  0 

also this:

less /proc/modules

my less /proc/modules output:

less /proc/modules:

nls_utf8 12493 1 - Live 0x00000000
isofs 39549 1 - Live 0x00000000
bnep 17923 2 - Live 0x00000000
rfcomm 38408 0 - Live 0x00000000
bluetooth 148839 10 bnep,rfcomm, Live 0x00000000
pci_stub 12550 1 - Live 0x00000000
vboxpci 22882 0 - Live 0x00000000
vboxnetadp 13328 0 - Live 0x00000000
vboxnetflt 27211 0 - Live 0x00000000
vboxdrv 251814 3 vboxpci,vboxnetadp,vboxnetflt, Live 0x00000000
vesafb 13489 1 - Live 0x00000000
ppdev 12849 0 - Live 0x00000000
joydev 17393 0 - Live 0x00000000
snd_usb_audio 100880 1 - Live 0x00000000
snd_usbmidi_lib 24558 1 snd_usb_audio, Live 0x00000000
gspca_sonixj 32391 0 - Live 0x00000000
gspca_main 27610 1 gspca_sonixj, Live 0x00000000
dcdbas 14098 0 - Live 0x00000000
videodev 85626 1 gspca_main, Live 0x00000000
ip6t_LOG 16846 4 - Live 0x00000000
xt_hl 12465 6 - Live 0x00000000
ip6t_rt 12473 3 - Live 0x00000000
nf_conntrack_ipv6 13581 7 - Live 0x00000000


anyway there is also a list of things to do upon a fresh install:

[http://blog.sudobits.com/2011/09/08/10-things-to-do-after-installing-ubuntu-11-10/](http://blog.sudobits.com/2011/09/08/10-things-to-do-after-installing-ubuntu-11-10/)

look through that, what do you see? Have you tried everything, installing decoders the whole routine?? Just some ideas. I'm guessing you need a specific driver for your usb or audio i/o or both to allow you to hear through the head phones. Can't say I'm an expert just some ideas

---

### Post by spanishconnector on 2012-01-19
I tested the computer with Windows XP and the USB headset worked fine. I installed Lubuntu 11.10 again (this time 32 bit) and did the to-do list from [http://blog.sudobits.com/2011/09/08/10-things-to-do-after-installing-ubuntu-11-10/]("http://blog.sudobits.com/2011/09/08/10-things-to-do-after-installing-ubuntu-11-10/") . I also did the lsmod and less /proc/modules from the Terminal.

_I am not getting any USB audio from Lubuntu yet_. I noticed your output for lsmod contains "*snd_usb_audio 100880 1*" but mine contains "*snd_usb_audio 100880  0*". I am wondering what does it mean. I don't want to think this computer's USB audio (this is the first computer I build myself) will work with XP but not with Lubuntu. Everything else works just perfect, even the regular headphone output works fine, but not the USB audio, which is the one I need to work. Please help. Thank you in advance. Following is the detailed outputs I got:

My output for lsmod is the following:

Module                  Size  Used by
rfcomm                 38408  0 
vesafb                 13489  1 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
snd_hda_codec_realtek   254125  1 
nvidia              10390874  30 
snd_usb_audio         100880  0 
ppdev                  12849  0 
snd_hda_intel          28358  4 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  2 snd_usb_audio,snd_hda_codec
snd_usbmidi_lib        24558  1 snd_usb_audio
snd_pcm                80435  4 snd_usb_audio,snd_hda_intel,snd_hda_codec
psmouse                63474  0 
snd_seq_midi           13132  0 
serio_raw              12990  0 
snd_seq_midi_event     14475  1 snd_seq_midi
uvcvideo               67271  0 
parport_pc             32114  1 
snd_rawmidi            25241  2 snd_usbmidi_lib,snd_seq_midi
videodev               85626  1 uvcvideo
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  3 snd_pcm,snd_seq
k10temp                12990  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  17 snd_hda_codec_realtek,snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_usbmidi_lib,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
i2c_nforce2            12906  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
floppy                 60310  0 
sata_nv                23379  2 
forcedeth              58103  0 
pata_amd               13753  0 

My output for less /proc/modules is the following:

rfcomm 38408 0 - Live 0x00000000
vesafb 13489 1 - Live 0x00000000
bnep 17923 2 - Live 0x00000000
bluetooth 148839 10 rfcomm,bnep, Live 0x00000000
snd_hda_codec_realtek 254125 1 - Live 0x00000000
nvidia 10390874 30 - Live 0x00000000 (P)
snd_usb_audio 100880 0 - Live 0x00000000
ppdev 12849 0 - Live 0x00000000
snd_hda_intel 28358 1 - Live 0x00000000
snd_hda_codec 91754 2 snd_hda_codec_realtek,snd_hda_intel, Live 0x00000000
snd_hwdep 13276 2 snd_usb_audio,snd_hda_codec, Live 0x00000000
snd_usbmidi_lib 24558 1 snd_usb_audio, Live 0x00000000
snd_pcm 80435 3 snd_usb_audio,snd_hda_intel,snd_hda_codec, Live 0x00000000
psmouse 63474 0 - Live 0x00000000
snd_seq_midi 13132 0 - Live 0x00000000
serio_raw 12990 0 - Live 0x00000000
snd_seq_midi_event 14475 1 snd_seq_midi, Live 0x00000000
uvcvideo 67271 0 - Live 0x00000000
parport_pc 32114 1 - Live 0x00000000
snd_rawmidi 25241 2 snd_usbmidi_lib,snd_seq_midi, Live 0x00000000
videodev 85626 1 uvcvideo, Live 0x00000000
snd_seq 51567 2 snd_seq_midi,snd_seq_midi_event, Live 0x00000000
snd_timer 28932 2 snd_pcm,snd_seq, Live 0x00000000
k10temp 12990 0 - Live 0x00000000
snd_seq_device 14172 3 snd_seq_midi,snd_rawmidi,snd_seq, Live 0x00000000
snd 55902 13 snd_hda_codec_realtek,snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_usbmidi_lib,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0x00000000
soundcore 12600 1 snd, Live 0x00000000
snd_page_alloc 14108 2 snd_hda_intel,snd_pcm, Live 0x00000000
i2c_nforce2 12906 0 - Live 0x00000000
lp 17455 0 - Live 0x00000000
parport 40930 3 ppdev,parport_pc,lp, Live 0x00000000
usbhid 41905 0 - Live 0x00000000
hid 77367 1 usbhid, Live 0x00000000
floppy 60310 0 - Live 0x00000000
sata_nv 23379 2 - Live 0x00000000
forcedeth 58103 0 - Live 0x00000000
/proc/modules

---

### Post by spanishconnector on 2012-01-20
If this happens to be a driver issue, like it appears to be, what should I do? Is there any website or forum that can provide the Biostar N68S3+ Motherboard USB audio drivers for Linux? Or should I give up on this hardware?

Thank you in advance for any help.

---

