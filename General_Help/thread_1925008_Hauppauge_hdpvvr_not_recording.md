---
title: "Hauppauge hdpvvr not recording"
date: 2012-02-13
forum: General Help
---

### Post by tomgra73 on 2012-02-13
Hello All, 

I am hoping someone can help me with a recording issue I am having. So I have the hauppauge hd pvr connected to my media center and tv. When I try to configure the cards on the backend nothing happens I cannot get any cards to work. Although I can see that the HDPVR is showing in several sections below. 

For Example if I try to set the card up as H.264 encoder I get an error, with V4L support to query audio reports. Or if I set it up as a USB MPEG 4 encoder box I get a failed to open card error. What am I doing wrong??? I have done the steps for ./build and sudo make install. When I go to dev/v4L I can see the Hauppauge HD PVR recording of live tv. I just cannot schedule any tv shows on the front end. What do I need to do to fix this?



```
mediasvr:~$ lsmod
Module                  Size  Used by
nfsd                  252397  13 
exportfs               12870  1 nfsd
nfs                   282952  0 
lockd                  74292  2 nfsd,nfs
fscache                50364  1 nfs
nfs_acl                12771  2 nfsd,nfs
auth_rpcgss            39173  2 nfsd,nfs
sunrpc                199096  14 nfsd,nfs,lockd,nfs_acl,auth_rpcgss
tda18271               57528  2 
s5h1411                18184  2 
snd_hda_codec_analog    75442  1 
snd_hda_intel          24113  0 
snd_hda_codec          90901  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
i915                  451053  2 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
hdpvr                  27722  0 
ppdev                  12849  0 
saa7164               114375  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
usbhid                 41704  0 
dvb_core               90587  1 saa7164
snd_timer              28659  2 snd_pcm,snd_seq
hid                    77084  1 usbhid
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         40971  1 i915
tpm_tis                13993  0 
v4l2_common            16757  2 hdpvr,saa7164
drm                   184164  3 i915,drm_kms_helper
parport_pc             32111  1 
psmouse                73312  0 
tpm                    21251  1 tpm_tis
tpm_bios               13460  1 tpm
snd                    55295  9 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13184  1 i915
serio_raw              12990  0 
video                  18951  1 i915
soundcore              12600  1 snd
videodev               75143  3 hdpvr,saa7164,v4l2_common
tveeprom               17009  1 saa7164
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usb_storage            43946  0 
uas                    17676  0 
floppy                 60032  0 

```

---

