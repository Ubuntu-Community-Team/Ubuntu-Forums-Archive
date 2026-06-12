---
title: "fresh 12.04 install. Wireless can view and connect to a network, but no internet"
date: 2012-06-24
forum: General Help
---

### Post by demonic_bunny on 2012-06-24
Hey all. Just threw 12.04 on my laptop, a Dell Latitude e6400, and I'm having a bit of an issue. The laptop connects fine over wifi on my wireless network when booted into Windows 7, and it can connect over Ethernet, but when connecting over wifi in Ubuntu, it detects the network and successfully connects, but will not load any web pages, and all we-dependent apps can't connect either. I tried following the Wireless Troubleshooting Guide but no luck. There seems to be a lot of people with similar questions around the, but looking through them I didn't find anything that seemed to work. I'm sad to say that I'm pretty cluesless when it comes to networking issues, so I don't really know where to go from here.

Any ideas?

---

### Post by neu5eeCh on 2012-06-24
> **demonic_bunny said:**
> Hey all. Just threw 12.04 on my laptop, a Dell Latitude e6400, and I'm having a bit of an issue. The laptop connects fine over wifi on my wireless network when booted into Windows 7, and it can connect over Ethernet, but when connecting over wifi in Ubuntu, it detects the network and successfully connects, but will not load any web pages, and all we-dependent apps can't connect either. I tried following the Wireless Troubleshooting Guide but no luck. There seems to be a lot of people with similar questions around the, but looking through them I didn't find anything that seemed to work. I'm sad to say that I'm pretty cluesless when it comes to networking issues, so I don't really know where to go from here.

Any ideas?

Two questions: 

1.) You're using Ubuntu, and not Kubuntu, right? I always used to have this problem with Kubuntu.

2.) If you're using Ubuntu, did you tell Ubuntu to remember/store your Wifi connection while you were in the Live/Install environment? There's a bug associated with this. I couldn't be bothered waiting for Ubuntu devs to solve the problem (let alone respond). Easier to just re-install and uncheck the store wifi option.

---

### Post by demonic_bunny on 2012-06-24
> **VTPoet said:**
> Two questions: 

1.) You're using Ubuntu, and not Kubuntu, right? I always used to have this problem with Kubuntu.

2.) If you're using Ubuntu, did you tell Ubuntu to remember/store your Wifi connection while you were in the Live/Install environment? There's a bug associated with this. I couldn't be bothered waiting for Ubuntu devs to solve the problem (let alone respond). Easier to just re-install and uncheck the store wifi option.

1) Yes I'm using Ubuntu xP

2) I don't believe so, unless its enabled by default? I had initially installed as a partition and the wifi failed, so I thought I'd just reinstall the entire OS and wipe the drive clean, but the inital setup was done using Ethernet, not wifi, cuz even when running off the live CD it would connect, but not actually *work...*

---

### Post by neu5eeCh on 2012-06-24
OK. Then this already sounds above my pay grade. If you know what wireless hardware you're using, then I would google that (along with Ubuntu). If you're not sure, then type lspci in a terminal window and see what comes up. Also, edit that information into your original post for others more knowledgeable.

---

### Post by blackflame2996 on 2012-06-24
does your network connect through any special AP's or a proxy?

---

### Post by demonic_bunny on 2012-06-24
> **blackflame2996 said:**
> does your network connect through any special AP's or a proxy?

Nope, just a simple WPA key...

---

### Post by wanderingwaste on 2012-06-24
Demonic, I have the 15" version of your laptop, and from experience, it's a drivers thing with the Broadcom card that is installed. Do me a favor, and punch lspci into the terminal, and post the results here.

There are some work arounds for this. My solution: I'm lazy, so I bought a $15 external tp-link card off Amazon, and shut the internal wifi card off in bios.

---

### Post by demonic_bunny on 2012-06-24
> **wanderingwaste said:**
> Demonic, I have the 15" version of your laptop, and from experience, it's a drivers thing with the Broadcom card that is installed. Do me a favor, and punch lspci into the terminal, and post the results here.

There are some work arounds for this. My solution: I'm lazy, so I bought a $15 external tp-link card off Amazon, and shut the internal wifi card off in bios.

```
tommyoliver@tommyoliver-Latitude-E6400:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: NVIDIA Corporation G98M [Quadro NVS 160M] (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
03:01.2 SD Host controller: Ricoh Co Ltd R5C843 MMC Host Controller (rev 11)
0c:00.0 Network controller: Intel Corporation Ultimate N WiFi Link 5300
tommyoliver@tommyoliver-Latitude-E6400:~$ 

```


Doesn't seem like its a Broadcom Wifi Adapter...however, I'm pretty sure the adapter reported in this model was the 5100, but this says its a 5300...hmm...

---

### Post by wildmanne39 on 2012-06-24
Hi, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
nm-tool
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by demonic_bunny on 2012-06-24
> **wildmanne39 said:**
> Hi, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
nm-tool
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

```
tommyoliver@tommyoliver-Latitude-E6400:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux tommyoliver-Latitude-E6400 3.2.0-25-generic #40-Ubuntu SMP Wed May 23 20:30:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
tommyoliver@tommyoliver-Latitude-E6400:~$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM Gigabit Network Connection [8086:10f5] (rev 03)
	Subsystem: Dell Device [1028:0233]
	Kernel driver in use: e1000e
--
0c:00.0 Network controller [0280]: Intel Corporation Ultimate N WiFi Link 5300 [8086:4235]
	Subsystem: Intel Corporation Device [8086:1121]
	Kernel driver in use: iwlwifi
tommyoliver@tommyoliver-Latitude-E6400:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"ballan"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 30:46:9A:80:87:36   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:99   Missed beacon:0

eth0      no wireless extensions.

tommyoliver@tommyoliver-Latitude-E6400:~$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
tommyoliver@tommyoliver-Latitude-E6400:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [ballan] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           no
  HW Address:        00:21:6A:42:DE:CA

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *ballan:         Infra, 30:46:9A:80:87:36, Freq 2462 MHz, Rate 54 Mb/s, Strength 80 WPA
    imPort2.4G:      Infra, C4:3D:C7:9B:95:20, Freq 2417 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    MVV51:           Infra, 00:26:B8:1D:D1:A7, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WEP
    2NQ72:           Infra, 00:1F:90:ED:FD:95, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WEP

  IPv4 Settings:
    Address:         192.168.1.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        5C:26:0A:2C:26:92

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.10
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


tommyoliver@tommyoliver-Latitude-E6400:~$ lsmod
Module                  Size  Used by
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
vesafb                 13844  1 
nvidia              12319264  48 
snd_hda_codec_idt      70795  1 
joydev                 17693  0 
arc4                   12529  2 
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
iwlwifi               332672  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
uvcvideo               72627  0 
mac80211              506816  1 iwlwifi
psmouse                87692  0 
videodev               98259  1 uvcvideo
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
cfg80211              205544  2 iwlwifi,mac80211
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
v4l2_compat_ioctl32    17128  1 videodev
snd                    78855  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  19596  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
dell_laptop            18119  0 
mac_hid                13253  0 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
serio_raw              13211  0 
wmi                    19256  1 dell_wmi
lp                     17799  0 
dcdbas                 14490  1 dell_laptop
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
e1000e                156693  0 
tommyoliver@tommyoliver-Latitude-E6400:~$ 

```

---

### Post by wildmanne39 on 2012-06-24
Hi, please do:
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
Then:
```
gksudo gedit /etc/pm/power.d/wireless
```

(this will create or edit a configuration file that will override the default powermanagement behavior) and enter the following: 
```
#!/bin/sh

/sbin/iwconfig wlan0 power off
```

above exit0, then save gedit and close.

Also go into your router settings and change wpa to just wpa2 encryption.
Reboot
Thanks

---

### Post by demonic_bunny on 2012-06-24
> **wildmanne39 said:**
> Hi, please do:
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
Then:
```
gksudo gedit /etc/pm/power.d/wireless
```

(this will create or edit a configuration file that will override the default powermanagement behavior) and enter the following: 
```
#!/bin/sh

/sbin/iwconfig wlan0 power off
```

above exit0, then save gedit and close.

Also go into your router settings and change wpa to just wpa2 encryption.
Reboot
Thanks

Dude I could hug you, worked like a charm. xD

Srsly...dunno how you were able to figure that out just like that...Im pretty jelly of your ka-nowledge.

---

### Post by wildmanne39 on 2012-06-24
Hi, glad it worked, please use thread tools at the top of the page to mark the thread solved.
Thanks

---

