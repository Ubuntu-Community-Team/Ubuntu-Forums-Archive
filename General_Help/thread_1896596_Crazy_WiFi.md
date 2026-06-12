---
title: "Crazy WiFi"
date: 2011-12-17
forum: General Help
---

### Post by snovik on 2011-12-17
I have a crazy wifi problem. It works so slow that it does not work. But it is even more weird. When I connect a mobile phone which works through the same wifi network then ubuntu picks it up and the speed is ok. When I disconnect the phone I get a feeling that wifi still works but the quality quickly degrades to the "usual" non-workingly slow state.

---

### Post by kurt18947 on 2011-12-17
A good place to start might be with which wifi adapter (not phone) you have.  If your WiFi adapter is built into your machine, type into a terminal 
```
lspci
```If you're using a plug-in USB device type into a terminal
```
lsusb
```Perhaps post the output of this as well:
```
lsmod
```
There are people on this forum far better versed in this stuff than I am but the above should be a good place to start.  I would suspect some sort of bad or conflicting drivers with your WiFi adapter.  Connecting via your phone takes the PC's WiFi adapter out of the process.

---

### Post by snovik on 2011-12-17
it is Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

and it is brand new fujitsu lifebook ah530 laptop

as usb adapter i am using samsung galaxy s2 and it works perfectly

---

### Post by snovik on 2011-12-17
and here is lsmod output while connected via phone.

```
Module                  Size  Used by
rndis_wlan             37554  0 
rndis_host             13848  1 rndis_wlan
cdc_ether              13536  1 rndis_host
usbnet                 26212  3 rndis_wlan,rndis_host,cdc_ether
usb_storage            57901  0 
cdc_acm                22761  0 
uas                    18027  0 
rfcomm                 47946  8 
bnep                   18436  2 
vmnet                  55617  12 
vsock                  52475  0 
vmci                   86575  1 vsock
vmmon                  89424  0 
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
arc4                   12529  2 
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ath9k                 127538  0 
joydev                 17693  0 
snd_seq_midi           13324  0 
mac80211              462092  1 ath9k
ath9k_common           13839  1 ath9k
ath9k_hw              312914  2 ath9k,ath9k_common
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
i915                  566827  3 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
btusb                  18600  1 
bluetooth             166112  23 rfcomm,bnep,btusb
ath                    24067  2 ath9k,ath9k_hw
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         42558  1 i915
drm                   236290  4 i915,drm_kms_helper
psmouse                73882  0 
serio_raw              13166  0 
uvcvideo               72711  0 
cfg80211              199587  4 rndis_wlan,ath9k,mac80211,ath
videodev               92992  1 uvcvideo
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l2_compat_ioctl32    17083  1 videodev
i2c_algo_bit           13423  1 i915
mei                    41480  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
intel_ips              18089  0 
video                  19412  1 i915
fujitsu_laptop         18992  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
r8169                  52788  0 
ahci                   26002  2 
libahci                26861  1 ahci
```

---

### Post by snovik on 2011-12-17
and lsmod when connected through wifi


```
Module                  Size  Used by
rndis_wlan             37554  0 
rndis_host             13848  1 rndis_wlan
cdc_ether              13536  1 rndis_host
usbnet                 26212  3 rndis_wlan,rndis_host,cdc_ether
usb_storage            57901  0 
cdc_acm                22761  0 
uas                    18027  0 
rfcomm                 47946  8 
bnep                   18436  2 
vmnet                  55617  13 
vsock                  52475  0 
vmci                   86575  1 vsock
vmmon                  89424  0 
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
arc4                   12529  2 
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ath9k                 127538  0 
joydev                 17693  0 
snd_seq_midi           13324  0 
mac80211              462092  1 ath9k
ath9k_common           13839  1 ath9k
ath9k_hw              312914  2 ath9k,ath9k_common
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
i915                  566827  3 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
btusb                  18600  1 
bluetooth             166112  23 rfcomm,bnep,btusb
ath                    24067  2 ath9k,ath9k_hw
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         42558  1 i915
drm                   236290  4 i915,drm_kms_helper
psmouse                73882  0 
serio_raw              13166  0 
uvcvideo               72711  0 
cfg80211              199587  4 rndis_wlan,ath9k,mac80211,ath
videodev               92992  1 uvcvideo
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l2_compat_ioctl32    17083  1 videodev
i2c_algo_bit           13423  1 i915
mei                    41480  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
intel_ips              18089  0 
video                  19412  1 i915
fujitsu_laptop         18992  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
r8169                  52788  0 
ahci                   26002  2 
libahci                26861  1 ahci
```

---

### Post by kurt18947 on 2011-12-17
Here is something to try:
[http://ubuntuforums.org/showthread.php?t=1746326&highlight=ar9285](http://ubuntuforums.org/showthread.php?t=1746326&highlight=ar9285)
It sounds like others have had a problem similar to yours with that chipset.

---

### Post by snovik on 2011-12-17
tnx. it seems to work for me

---

