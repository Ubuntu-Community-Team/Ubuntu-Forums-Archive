---
title: "WiFi driver"
date: 2011-09-17
forum: General Help
---

### Post by DanielFGray on 2011-09-17
I'm generally reluctant to post my own threads but after extensive Googling, I'm at a loss.
I've never had a problem with drivers in Ubuntu, but today I decided to try my hand at a netinst just for the hell of it; it was going okay, but I couldn't get wireless drivers installed. I could connect on eth0 but never on wlan..
In the end I gave up, and used the same CD to install 11.04 as I did before trying the netinst.
Now I'm having the same problem.
Ubuntu [re]installed the proprietary Broadcom STA driver, same one that was working fine before the netinst, but in the networking applet at the top it just says wireless is disconnected.

Any ideas?
Thanks.

---

### Post by DanielFGray on 2011-09-18
Here's some text dumpage that may help

lsmod
```
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_idt      60537  1 
snd_hda_intel          28209  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
ir_lirc_codec          12770  0 
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
lirc_dev               18720  1 ir_lirc_codec
snd_seq_midi           13132  0 
ir_sony_decoder        12493  0 
lib80211_crypt_tkip    17203  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
wl                   2642531  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ir_jvc_decoder         12490  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ir_rc6_decoder         12490  0 
ir_rc5_decoder         12490  0 
rc_rc6_mce             12454  0 
ir_nec_decoder         12490  0 
i915                  451068  3 
drm_kms_helper         40745  1 i915
uvcvideo               66851  0 
joydev                 17322  0 
videodev               75143  1 uvcvideo
drm                   184164  4 i915,drm_kms_helper
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13184  1 i915
hp_accel               21632  0 
lis3lv02d              19285  1 hp_accel
video                  18951  1 i915
lp                     13349  0 
ene_ir                 22309  0 
rc_core                25760  9 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,rc_rc6_mce,ir_nec_decoder,ene_ir
psmouse                59039  0 
soundcore              12600  1 snd
input_polldev          13735  1 lis3lv02d
serio_raw              12990  0 
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lib80211               14570  2 lib80211_crypt_tkip,wl
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  1 
uas                    17676  0 
ahci                   21591  2 
libahci                25548  1 ahci
r8169                  46630  0
```

lspci
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr **:**:**:**:**:**  
          inet addr:*.*.*.* Bcast:*.*.*.*  Mask:255.255.255.0
          inet6 addr: *::*:*:*:* Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:89731 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53795 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:108402653 (108.4 MB)  TX bytes:7104832 (7.1 MB)
          Interrupt:45 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr *:*:*:*:*:*  
          inet6 addr: *::*:*:*:* Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:2888
          TX packets:0 errors:181 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:560 errors:0 dropped:0 overruns:0 frame:0
          TX packets:560 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:43792 (43.7 KB)  TX bytes:43792 (43.7 KB)
```

---

### Post by mikewhatever on 2011-09-18
The applet will not auto-connect to networks after a fresh install. It would only autoconnet to networks you had connected previously.

---

### Post by DanielFGray on 2011-09-18
I'm aware of this, my problem isn't the networks autoconnecting
It's that there's, no networks showing up to connect to
I can't even add a hidden ssid and specify the encryption and pass keys, and have it connect it, just doesn't do anything

Normally, I believe, there is a wlan0 interface in iwconfig
But now there isn't
And honestly I don't know how to go about adding one

---

### Post by gandaran on 2011-09-18
are you sure you have the right broadcom driver installed?
use this thread for troubleshooting
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

### Post by DanielFGray on 2011-09-18
> **gandaran said:**
> are you sure you have the right broadcom driver installed
well as you can see in the lspci dump it's a Broadcom 4312, which is covered by the Broadcom STA driver, which Ubuntu picked up on and installed right away, as it usually does.

But, with my luck, I play around with some drivers and it decides to stop scanning.
But shouldn't that be fixed with a reinstall? I'm going to try another install and see how it goes.

---

### Post by gandaran on 2011-09-18
> well as you can see in the lspci dump it's a Broadcom 4312, which is covered by the Broadcom STA driver, which Ubuntu picked up on and installed right away, as it usually does.
proprietary broadcom drivers don't install on ubuntu by default, you have to first enable them in additional drivers.

---

### Post by DanielFGray on 2011-09-18
solved

fresh install fixed it

---

