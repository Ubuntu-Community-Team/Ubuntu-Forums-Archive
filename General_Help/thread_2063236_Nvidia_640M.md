---
title: "Nvidia 640M"
date: 2012-09-26
forum: General Help
---

### Post by set4812 on 2012-09-26
I have problem witch my nvidia 640M
> You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.
my error now i have resolution 640x480 how i can install my driver?
I resets xorg.conf but not help my ubuntu.
My xorg.0.log
[http://pastebin.com/fhvRRN3g]("http://pastebin.com/fhvRRN3g")
Thx for help
set4812

---

### Post by Sanitylost on 2012-09-27
I'm having the same problem. I've tried all the usual uninstall-reinstall, but everytime i get the fact that my config file isn't up to date even after a reboot....

Any thoughts?

---

### Post by Rexilion on 2012-09-27
@set4812 That is a generic error, it could be a different issue than what is described here. I suggest you open a new thread and post there:

```
cat /var/log/Xorg.0.log
lsmod
dmesg
```

@Sanitylost

Do you have one of these new laptops that come with two video chips? I see that intel is detecting and driving 'something' in there.

Try placing this in your xorg.conf (overwriting other instances of this section):

> Section "Device"
	Identifier	"nVidia Card"
	Driver		"nvidia"
EndSection

---

### Post by GeForce 9500GT on 2012-09-27
Try installing the latest Nvidia drivers as well. Open a terminal and execute the [COLOR=black]following commands:[/COLOR]

[COLOR=black]```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates[/COLOR][COLOR=black]
```[/COLOR]
[COLOR=black]```
sudo apt-get update[/COLOR][COLOR=black]
```[/COLOR]
[COLOR=black]```
sudo apt-get install nvidia-current nvidia-settings[/COLOR][COLOR=black]
```[/COLOR]

---

### Post by set4812 on 2012-09-27
lsmod 
> snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224173  1 
parport_pc             32866  0 
ppdev                  17113  0 
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
binfmt_misc            17540  1 
nvidia              11262536  0 
joydev                 17693  0 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
acer_wmi               28418  0 
sparse_keymap          13890  1 acer_wmi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    19256  1 acer_wmi
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
arc4                   12529  2 
i915                  473240  2 
drm_kms_helper         46978  1 i915
psmouse                97362  0 
drm                   242038  3 i915,drm_kms_helper
uvcvideo               72627  0 
ath9k                 132390  0 
mac80211              506816  1 ath9k
mac_hid                13253  0 
ath9k_common           14053  1 ath9k
ath9k_hw              411151  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
mei                    41616  0 
cfg80211              205544  3 ath9k,mac80211,ath
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
serio_raw              13211  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
uas                    18180  0 
usb_storage            49198  1 
hid_a4tech             12678  0 
usbhid                 47199  0 
hid                    99559  2 hid_a4tech,usbhid
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
tg3                   152032  0 

I have intel hd 400 maybe intel graphic have problem. 
on xorg.conf sections monitor i think see small problem
> Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

i have new driver dont need reinstall

---

### Post by GeForce 9500GT on 2012-09-27
> **set4812 said:**
> lsmod 

I have intel hd 400 maybe intel graphic have problem. 
on xorg.conf sections monitor i think see small problem



What do you have?? Intel or Nvidia????
Your first post here says you have a Nvidia:> I have problem witch my nvidia 640M and now you say you have intel?

---

### Post by set4812 on 2012-09-27
Intel from processor and nvidia . On windows nvidia say first instal intel graphic driver maybe some problem is on linux

---

### Post by maku14 on 2012-12-09
Is there any solution to installation of 640m on Ubuntu? I'm pretty greenhorn so accurate explanation would be great.

---

