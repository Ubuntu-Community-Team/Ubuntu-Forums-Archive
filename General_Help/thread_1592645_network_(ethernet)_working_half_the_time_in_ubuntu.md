---
title: "network (ethernet) working half the time in ubuntu 10.10"
date: 2010-10-10
forum: General Help
---

### Post by extendedping on 2010-10-10
I have to keep rebooting and its a crapshoot. sometimes it works fine and other times I do not even get a light on my linksys router. that is using 

brad@ubnuntu:~$ uname -a
Linux ubnuntu 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64 GNU/Linux
brad@ubnuntu:~$ 

If I use the previous kernel (presumably from 10.04) there is no connectivity issue. 

where would I begin troubleshooting this issue? here is the output of lsmod if that helps...

brad@ubnuntu:~$ lsmod 
Module                  Size  Used by
ip6table_filter         1719  0 
ip6_tables             20633  1 ip6table_filter
ib_iser                30995  0 
rdma_cm                31125  1 ib_iser
ib_cm                  40222  1 rdma_cm
iw_cm                   9409  1 rdma_cm
ib_sa                  22268  2 rdma_cm,ib_cm
ib_mad                 41002  2 ib_cm,ib_sa
ib_core                65247  6 ib_iser,rdma_cm,ib_cm,iw_cm,ib_sa,ib_mad
ib_addr                 6349  1 rdma_cm
iscsi_tcp              10404  0 
libiscsi_tcp           17292  1 iscsi_tcp
libiscsi               48545  3 ib_iser,iscsi_tcp,libiscsi_tcp
scsi_transport_iscsi    39315  4 ib_iser,iscsi_tcp,libiscsi
ipt_MASQUERADE          1919  6 
iptable_nat             4593  1 
nf_nat                 20067  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      13143  5 iptable_nat,nf_nat
nf_defrag_ipv4          1569  1 nf_conntrack_ipv4
xt_state                1386  2 
nf_conntrack           75238  5 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4,xt_state
ipt_REJECT              2440  4 
xt_tcpudp               2627  8 
iptable_filter          1778  1 
ip_tables              19107  2 iptable_nat,iptable_filter
x_tables               24423  9 ip6table_filter,ip6_tables,ipt_MASQUERADE,iptable_nat,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,ip_tables
binfmt_misc             7984  1 
bridge                 79668  0 
stp                     2195  1 bridge
kvm_intel              49247  0 
snd_usb_audio         105727  1 
snd_usbmidi_lib        21313  1 snd_usb_audio
kvm                   298550  1 kvm_intel
snd_hda_codec_idt      64667  1 
snd_emu10k1_synth       6028  0 
snd_emux_synth         34336  1 snd_emu10k1_synth
snd_seq_virmidi         5165  1 snd_emux_synth
snd_seq_midi_emul       6999  1 snd_emux_synth
snd_emu10k1           149854  3 snd_emu10k1_synth
snd_ac97_codec        125227  1 snd_emu10k1
ac97_bus                1474  1 snd_ac97_codec
snd_util_mem            3842  2 snd_emux_synth,snd_emu10k1
snd_hda_intel          26019  2 
snd_hda_codec         100919  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6660  4 snd_usb_audio,snd_emux_synth,snd_emu10k1,snd_hda_codec
snd_pcm                89104  5 snd_usb_audio,snd_emu10k1,snd_ac97_codec,snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  4 snd_usbmidi_lib,snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      7291  2 snd_seq_virmidi,snd_seq_midi
snd_seq                57512  6 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event
i915                  330089  2 
snd_timer              23850  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          6912  5 snd_emu10k1_synth,snd_emu10k1,snd_seq_midi,snd_rawmidi,snd_seq
raw1394                25814  0 
gspca_zc3xx            47258  0 
drm_kms_helper         32836  1 i915
ppdev                   6804  0 
psmouse                62080  0 
emu10k1_gp              2020  0 
ieee1394               95219  1 raw1394
tpm_tis                 9894  0 
tpm                    16013  1 tpm_tis
gspca_main             27688  1 gspca_zc3xx
videodev               49359  1 gspca_main
v4l1_compat            15519  1 videodev
tpm_bios                6426  1 tpm
gameport               11224  2 emu10k1_gp
v4l2_compat_ioctl32    12646  1 videodev
snd                    64117  26 snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_idt,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               4910  0 
parport_pc             30086  1 
drm                   206161  3 i915,drm_kms_helper
i2c_algo_bit            6208  1 i915
soundcore               1240  1 snd
lp                     10201  0 
snd_page_alloc          8588  3 snd_emu10k1,snd_hda_intel,snd_pcm
video                  22176  1 i915
output                  2527  1 video
parport                37032  3 ppdev,parport_pc,lp
intel_agp              32080  2 i915
usbhid                 42062  0 
hid                    84678  1 usbhid
firewire_ohci          24679  0 
firewire_core          54327  1 firewire_ohci
crc_itu_t               1739  1 firewire_core
ahci                   21857  0 
libahci                26167  3 ahci
pata_marvell            3345  0 
e1000e                151787  0 


 Thanks for listening...

---

### Post by extendedping on 2010-10-19
Ok since it still happens %50 of the time...I guess I will back up and wait to see how the fedora 14 acts, will do live cd to check it.

---

