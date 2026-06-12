---
title: "No sound"
date: 2010-02-28
forum: General Help
---

### Post by satimis on 2010-02-28
Hi folks,

Ubuntu 9.10 64bit
Mobo - Asus M4A78T-E
onboard sound card
Display - Samsung 2494


No sound

Mobo Spec
[http://www.asus.com/product.aspx?P_ID=cf8IZzbU4m6GHKnW](http://www.asus.com/product.aspx?P_ID=cf8IZzbU4m6GHKnW)

Audio```

VIA® VT1708S 8 -Channel High Definition Audio CODEC
DTS Surround Sensation UltraPC
- Supports Jack-Detection, Multi-Streaming, and Front Panel Jack-Retasking
- Optical S/PDIF Out ports at back I/O
- ASUS Noise Filtering

```


$ sudo lspci | grep Audio```

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller

```


$ sudo lsmod```

Module                  Size  Used by
binfmt_misc            10220  1 
ipt_MASQUERADE          2944  1 
iptable_nat             6656  1 
nf_nat                 22164  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      16376  4 iptable_nat,nf_nat
nf_defrag_ipv4          2400  1 nf_conntrack_ipv4
xt_state                2432  1 
nf_conntrack           80832  5 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4,xt_state
ppdev                   8232  0 
ipt_REJECT              3584  2 
xt_tcpudp               3616  4 
bridge                 56384  0 
stp                     3012  1 bridge
kvm_amd                41556  0 
kvm                   190648  1 kvm_amd
snd_hda_codec_atihdmi     4320  1 
snd_hda_codec_via      35456  1 
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_hda_intel          31880  3 
snd_seq_midi            8192  0 
snd_hda_codec          87584  3 snd_hda_codec_atihdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
iptable_filter          3872  1 
ip_tables              21200  2 iptable_nat,iptable_filter
x_tables               25832  6 ipt_MASQUERADE,iptable_nat,xt_state,ipt_REJECT,xt_tcpudp,ip_tables
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
asus_atk0110            9472  0 
snd_pcm                93160  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
amd64_edac_mod         26688  0 
edac_core              48876  1 amd64_edac_mod
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lp                     11908  0 
i2c_piix4              11728  0 
parport                40528  2 ppdev,lp
shpchp                 37756  0 
snd                    77096  16 snd_seq_oss,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
ohci1394               33780  0 
radeon                684512  1 
ttm                    43056  1 radeon
drm                   193856  3 radeon,ttm
i2c_algo_bit            7076  1 radeon
usbhid                 43968  0 
ieee1394              100896  1 ohci1394
floppy                 65192  0 
atl1e                  37780  0 

```


Gmone
System -> Preferences -> Sound
Hardware;```

Internal Audo
1 Input
Analog Stereo Input

RS780 Azalia controller
1 Output
Digital Stereo (HDMI) Output

```


Output:```

RS780 Azalia controller Digital Stereo (HDMI)
Stereo

```


No Linux sound driver on the CD coming with the mobo.  Please help.  TIA


B.R.
satimis

---

### Post by xXxTHADDEUSxXx on 2010-02-28
i just built a system yesterday and loaded ubuntu 9.10 64bit on it. im also using my motherboards sound and at first did not have sound and also no linux drivers. turns out it was just all muted. go to applications->accessories->terminal. then type alsamixer.   a graphical equalizer will show up and thats where all mine was muted.

---

### Post by satimis on 2010-02-28
> **xXxTHADDEUSxXx said:**
> i just built a system yesterday and loaded ubuntu 9.10 64bit on it. im also using my motherboards sound and at first did not have sound and also no linux drivers. turns out it was just all muted. go to applications->accessories->terminal. then type alsamixer.   a graphical equalizer will show up and thats where all mine was muted.

Hi xXxTHADDEUSxXx,

I solved my problem as follows;

On terminal started alsamixer

$ alsamixer
Master - not mute, but 00.  I could not adjust its volume
Front Center - not mute, but 00.  Also I couldn't adjust its volume

Installed gnome-alsamixer

$ gnome-alsamixer

Now I could adjust the volume of Master and Front Center.  Also I could adjust the volume of Master and Front Center on alsamixer.  But still there was no sound.

On terminal again;

$ sudo apt-get remove pulseaudion
$ sudo apt-get install esound

Then I have sound back on external speakers.  But still I couldn't have sound on Display speakers.


Gmone
System -> Preferences -> Sound
Hardware;```


Internal Audo
1 Input
Analog Stereo Input

RS780 Azalia controller
1 Output
Digital Stereo (HDMI) Output

```


Output:```


RS780 Azalia controller Digital Stereo (HDMI)
Stereo

```


Any advice?  TIA


B.R.
satimis

---

