---
title: "Ubuntu 11.04 Wireless just stopped working"
date: 2011-09-28
forum: General Help
---

### Post by SeaHawk22 on 2011-09-28
I am running Ubuntu 11.04 on a Dell 1545, and the wireless card just stopped working. When I came home from work it no longer connected to my wireless network. Just to be clear, the card was connecting prior to today :)

Please help, thank you

---

### Post by wildmanne39 on 2011-09-28
Hi, please post the results of these commands:
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
sudo iwlist scan
```
```
nm-tool
```
```
lsmod
```
```
dmesg | egrep 'b43|firm|wl|wlan0|eth1'
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by SeaHawk22 on 2011-09-28
# guhang@Guhang:~$ lspci -nnk | grep -iA2 net
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
	Subsystem: Dell Device [1028:02aa]
	Kernel driver in use: sky2
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
	Kernel driver in use: wl
guhang@Guhang:~$
#

#
guhang@Guhang:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

guhang@Guhang:~$ 
#

#
guhang@Guhang:~$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
guhang@Guhang:~$ 
#

#
guhang@Guhang:~$ sudo iwlist scan
[sudo] password for guhang: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument

guhang@Guhang:~$ 
#

#
guhang@Guhang:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             unavailable
  Default:           no
  HW Address:        C4:17:FE:12:BE:9D

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           yes
  HW Address:        A4:BA:DB:99:1D:F0

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.104
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             68.105.28.12
    DNS:             68.105.29.12
    DNS:             68.105.28.11


guhang@Guhang:~$ 
#

#
guhang@Guhang:~$ lsmod
Module                  Size  Used by
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_idt      71137  1 
snd_hda_intel          33176  2 
snd_hda_codec         103804  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
i915                  515121  3 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         42136  1 i915
joydev                 17606  0 
lib80211_crypt_tkip    17387  0 
drm                   227534  4 i915,drm_kms_helper
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
wl                   2568244  0 
snd                    67382  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dell_wmi               12681  0 
uvcvideo               72195  0 
soundcore              12680  1 snd
i2c_algo_bit           13400  1 i915
sparse_keymap          13898  1 dell_wmi
videodev               82052  1 uvcvideo
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
v4l2_compat_ioctl32    17078  1 videodev
video                  19438  1 i915
psmouse                73535  0 
dell_laptop            13827  0 
dcdbas                 14438  1 dell_laptop
serio_raw              13166  0 
lib80211               14991  2 lib80211_crypt_tkip,wl
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usb_storage            53538  0 
uas                    17996  0 
sky2                   58509  0 
ahci                   25951  2 
libahci                26642  1 ahci
guhang@Guhang:~$ 
#

#
guhang@Guhang:~$ dmesg | egrep 'b43|firm|wl|wlan0|eth1'
[   13.129240] wl: module license 'MIXED/Proprietary' taints kernel.
[   13.142489] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.142504] wl 0000:0c:00.0: setting latency timer to 64
[   13.204508] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.100.82.38
guhang@Guhang:~$ 
#


Thank you very much!

---

### Post by wildmanne39 on 2011-09-28
Hi, you are soft blocked and hard blocked try this please.
```
sudo rmmod -f dell-laptop
```
and see if it comes on if not run this command again.
```
rfkill list all
```
Thank you

---

### Post by SeaHawk22 on 2011-09-28
Still not working I got this response from last command.

```
guhang@Guhang:~$ rfkill list all
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```

Thank you :)

---

### Post by wildmanne39 on 2011-09-28
Hi, that removed the soft block, now see if your wireless switch is off it is fn f5 or one of the those key combinations like that or a switch that slides.

The command that removed the soft block we will have to make that permanent when we are done.
Thank you

---

### Post by SeaHawk22 on 2011-09-28
Thank you, I understand what you are saying about the hardblock, I did some searching to find out more about it. It is suppose to be F2, maybe I am holding it down too long, not long enough.. I am not sure.

---

### Post by SeaHawk22 on 2011-09-28
> **SeaHawk22 said:**
> Thank you, I understand what you are saying about the hardblock, I did some searching to find out more about it. It is suppose to be F2, maybe I am holding it down too long, not long enough.. I am not sure.

PS I tried FN + F2 as well

EDIT

I shut it down and did a cold boot (not sure if that even matters with Ubuntu) but it works now!   Thank you!  :)

---

### Post by wildmanne39 on 2011-09-28
Hi let's make this permanent.
```
sudo su
echo "blacklist dell-laptop" >> /etc/modprobe.d/blacklist.conf
exit
```
Now if the button is not working then try this please:
```
rfkill unblock all
```
Thank you

---

### Post by SeaHawk22 on 2011-09-28
> **wildmanne39 said:**
> Hi let's make this permanent.
```
sudo su
echo "blacklist dell-laptop" >> /etc/modprobe.d/blacklist.conf
exit
```
Now if the button is not working then try this please:
```
rfkill unblock all
```
Thank you

Thank you for your help, my system is telling me my password is incorrect which is complete rubbish, but once I get things acting correctly I will input those commands.

Thanks again!

---

### Post by wildmanne39 on 2011-09-28
Hi, okay if the password becomes a serious issue you can reset it with the directions from this link.
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
Thank you

---

