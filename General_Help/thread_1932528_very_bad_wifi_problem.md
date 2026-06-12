---
title: "very bad wifi problem"
date: 2012-02-27
forum: General Help
---

### Post by zeez on 2012-02-27
Hello lads,

I am with a serious problem on wifi reception on my system, here is some information i colected from my system


```

root@zeez-desktop:~# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 003 Device 002: ID 045e:0732 Microsoft Corp. 
[COLOR="Red"]Bus 003 Device 003: ID 2001:3c00 D-Link Corp. AirPlus G DWL-G122 Wireless Adapter(rev.B1) [Ralink RT2500USB][/COLOR]
Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver

```

```

root@zeez-desktop:~# cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux zeez-desktop 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
root@zeez-desktop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"zeezNetwork"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:04:E2:D0:89:32   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=35/70  Signal level=-75 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3079  Invalid misc:2570   Missed beacon:0

root@zeez-desktop:~# rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
root@rui-desktop:~# lsmod
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
joydev                 17693  0 
ppdev                  17113  0 
snd_hda_codec_realtek   330769  1 
arc4                   12529  2 
rt2500usb              27294  0 
rt2x00usb              20830  1 rt2500usb
rt2x00lib              50325  2 rt2500usb,rt2x00usb
mac80211              310872  2 rt2x00usb,rt2x00lib
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
cfg80211              199587  2 rt2x00lib,mac80211
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
binfmt_misc            17540  1 
snd_seq_midi           13324  0 
usbhid                 47198  0 
hid                    95463  1 usbhid
snd_rawmidi            30547  1 snd_seq_midi
psmouse                73882  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
serio_raw              13166  0 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  566711  3 
parport_pc             36962  1 
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
soundcore              12680  1 snd
i2c_algo_bit           13423  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
r8169                  52788  0 
root@zeez-desktop:~# ^C
root@zeez-desktop:~# 


```

---

### Post by Paddy Landau on 2012-02-28
> **zeez said:**
> I am with a serious problem on wifi reception on my system
You will have to be far more specific than that!

What happens when you try to connect... The icon doesn't show? Your computer crashes? It overheats? It connects then disconnects? It won't ask for the password? It connects to the wrong wireless point? It doesn't recognise your card? It connects but the speed is slow? It connects but there is no Internet connectivity?

Please help us help you by explaining the problem, what you have tried to do about it, and what happened when you tried.

We also need to know what version of Ubuntu you are running. If you are running WUBI, we need to know that too.

---

### Post by epajarre on 2012-03-10
I can provide some more information.

I am pretty sure the described USB WIFI worked ok on Ubuntu 11.04 and previous versions.

It does not work well on 11.10
It looks like the connection disconnects and connects frequently
Ping results look like that packets are only delivered once per 5 seconds
(I am putting this message together on the affected computer so it suffers from the web browser behaviour...)

here is some kern.log output:

ar 10 19:31:40 eero-fujitsu kernel: [12962.888092] phy2 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Mar 10 19:31:40 eero-fujitsu kernel: [12962.888102] phy2 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Mar 10 19:31:44 eero-fujitsu kernel: [12966.836077] phy2 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Mar 10 19:31:44 eero-fujitsu kernel: [12966.836088] phy2 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Mar 10 19:31:48 eero-fujitsu kernel: [12970.780031] phy2 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Mar 10 19:31:48 eero-fujitsu kernel: [12970.780039] phy2 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Mar 10 19:31:52 eero-fujitsu kernel: [12974.720035] phy2 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Mar 10 19:31:52 eero-fujitsu kernel: [12974.720043] phy2 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Mar 10 19:31:57 eero-fujitsu kernel: [12979.636032] phy2 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Mar 10 19:31:57 eero-fujitsu kernel: [12979.636040] phy2 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.

---

### Post by kirusoft on 2012-03-14
If you got slow connexion, difficult connexion, slow speed etc.
Here is the command to fix it.

My card was : Intel Corporation Centrino Wireless-N 1030
My Distro : Ubuntu 11.04
Kernel : 2.6.38-13-generic x86_64

So how to fix ?

first test if its work :
**sudo rmmod -f iwlagn**
[B]sudo modprobe iwlagn 11n_disable=1
sudo iwconfig wlan0 power off[/B]

It’s work? Then how to make it permanent? 
**gksudo gedit /etc/modprobe.d/iwlagn.conf**
Add this to the file :
```
options iwlagn 11n_disable=1
```
Save & Close Gedit
Then :
**gksudo gedit /etc/pm/power.d/wireless**
Add this to the file :
```
#!/bin/sh
iwconfig wlan0 power off
```
Save and quit gedit
You need to make the script executable :
**sudo chmod +x /etc/pm/power.d/wireless**

Hope it’s help. It’s helped me a lot my Wifi working fine now. :)

---

### Post by epajarre on 2012-03-19
> **kirusoft said:**
> If you got slow connexion, difficult connexion, slow speed etc.
Here is the command to fix it.

My card was : Intel Corporation Centrino Wireless-N 1030
My Distro : Ubuntu 11.04
Kernel : 2.6.38-13-generic x86_64

So how to fix ?

first test if its work :
**sudo rmmod -f iwlagn**
[B]sudo modprobe iwlagn 11n_disable=1
sudo iwconfig wlan0 power off[/B]

.... see the rest of the advice from the original message ....



I have different hardware, and different kernel modules related to it, so I don't think that the rmmod/modprobe would work.

But, the ** iwconfig wlan0 power off**   seems to make a difference.

I will see if the effect is real, or am I just lucky at the moment, but it looks like that the wlan started to work normally. The iwconfig turned power management off for the wlan interface?

  Thanks a lot for the help!

    Eero

---

