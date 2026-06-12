---
title: "Airodump-ng don't find any wireless network"
date: 2011-07-25
forum: General Help
---

### Post by dvorel on 2011-07-25
I installed the patched driver from this site: [http://aircrack-ng.org/doku.php?id=r8187#power_settings](http://aircrack-ng.org/doku.php?id=r8187#power_settings)
Everything did without errors but when I type airodump-ng wlan0 it don't find any network.
:confused:

---

### Post by wildmanne39 on 2011-07-25
Hi, have you looked at this link?
[http://ubuntuforums.org/showthread.php?t=1598930&highlight=Airodump-ng](http://ubuntuforums.org/showthread.php?t=1598930&highlight=Airodump-ng)
I am headed to bed but if you need more help run these commands in a terminal
```
lsmod
```
```
sudo lshw -C network
```
```
lspci -nn | grep 0280
```
```
lsusb
```
```
iwconfig
```
```
rfkill list All
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by dvorel on 2011-07-25
It's working on WiFi SKY 1000mW but it don't work on kasens g5000 2000mW
:confused:

---

### Post by wildmanne39 on 2011-07-25
I am glad it is working some now anyway, if you post what I asked for in my previous post maybe we can help you.
Thank you

---

### Post by dvorel on 2011-07-26
#root@bt:~# lsmod
Module                  Size  Used by
arc4                    1046  2
ecb                     1565  2
rtl8187                52342  0
mac80211              207141  1 rtl8187
led_class               1787  1 rtl8187
cfg80211              120768  2 rtl8187,mac80211
rfkill                 12316  1 cfg80211
eeprom_93cx6             972  1 rtl8187
ipv6                  215277  10
video                  15550  0
output                  1296  1 video
sbs                     8489  0
sbshc                   2608  1 sbs
hed                     1147  0
mperf                    891  0
speedstep_lib           2528  0
cpufreq_stats           3073  0
cpufreq_powersave        634  0
cpufreq_performance      638  0
cpufreq_ondemand        6994  0
freq_table              2007  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     7564  0
iptable_filter           884  0
ip_tables               9231  1 iptable_filter
x_tables               10782  2 iptable_filter,ip_tables
lp                      7036  0
snd_intel8x0           22719  0
snd_ac97_codec         87936  1 snd_intel8x0
ac97_bus                 770  1 snd_ac97_codec
snd_pcm_oss            33635  0
snd_mixer_oss          12386  1 snd_pcm_oss
snd_pcm                57162  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1023  0
snd_seq_oss            23301  0
snd_seq_midi            3720  0
snd_rawmidi            14559  1 snd_seq_midi
rtc_cmos                7838  0
rtc_core               11455  1 rtc_cmos
snd_seq_midi_event      4312  2 snd_seq_oss,snd_seq_midi
rtc_lib                 1534  1 rtc_core
parport_pc             18091  1
parport                24431  2 lp,parport_pc
snd_seq                39714  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              14958  2 snd_pcm,snd_seq
option                 12554  0
snd_seq_device          4173  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
usb_wwan                6908  1 option
psmouse                32227  0
usbserial              26240  2 option,usb_wwan
snd                    38829  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               3352  0
sis_agp                 3609  1
soundcore               4271  1 snd
snd_page_alloc          5477  2 snd_intel8x0,snd_pcm
agpgart                22961  1 sis_agp
shpchp                 27915  0
evdev                   6681  8
joydev                  7824  0
mac_hid                 2425  0
aufs                  135501  1532
squashfs               19741  1
pata_acpi               2316  0
sis900                 16486  0
ata_generic             2319  0
sg                     20086  0
fuse                   52129  1
root@bt:~# sudo lshw -C network
  *-network
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 90
       serial: 00:13:d4:08:97:50
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.1.21 latency=64 link=yes maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       bus info: usb@1:7
       logical name: wlan0
       serial: 00:e0:0c:e1:9f:29
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=2.6.35.8 firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg
root@bt:~# lspci -nn | grep 0280
root@bt:~# lsusb
Bus 001 Device 005: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 flash drive
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 04fc:0538 Sunplus Technology Co., Ltd
Bus 002 Device 002: ID 046d:c316 Logitech, Inc. HID-Compliant Keyboard
root@bt:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

root@bt:~# rfkill list All
Bogus list argument 'All'.

---

### Post by wildmanne39 on 2011-07-26
Hi, will you run this command again please I made a typo. I am sorry about that.
```
rfkill list all
```
Thank you

---

### Post by blind2314 on 2011-07-26
For clarity's sake, maybe wrap the output you posted in CODE tags and add some formatting between each command (hit return a couple of times..the white space does wonders).

---

