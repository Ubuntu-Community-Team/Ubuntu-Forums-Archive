---
title: "Can't connect or see any wireless networks"
date: 2011-09-05
forum: General Help
---

### Post by DubyaStiles on 2011-09-05
I put 11.04 on my grandparents Compaq Presario C500 as the primary OS and when I try to open Network Connections under wireless no networks are being shown, I am wired right now

Thank you for your help!!

---

### Post by DubyaStiles on 2011-09-05
Bump

---

### Post by DubyaStiles on 2011-09-05
pmuB

---

### Post by ken_23434 on 2011-09-05
I have a Compaq laptop that has wireless issues too.  It's at home, so I cannot report the model #.  It's an older one, about 8 years old.  The problem I have w/ it is that I cannot get the "proprietary" driver to install.
 
It might be a similar problem w/ yours.
 
Under admin, click on "Additional Drivers" (I think that is the name, I am at work on an XP machine).  It will scan the system and inform you if there is a proprietary driver avail.
 
Ken

---

### Post by 3rdalbum on 2011-09-05
> **ken_23434 said:**
> I have a Compaq laptop that has wireless issues too.  It's at home, so I cannot report the model #.  It's an older one, about 8 years old.  The problem I have w/ it is that I cannot get the "proprietary" driver to install.
 
It might be a similar problem w/ yours.
 
Under admin, click on "Additional Drivers" (I think that is the name, I am at work on an XP machine).  It will scan the system and inform you if there is a proprietary driver avail.
 
Ken

The OP says they're using Ubuntu 11.04, so your instructions might not reflect what they have on screen.

If those instructions didn't make sense, then click on the "on/off switch" icon at the top-right corner of the screen, then go to System Settings at the bottom of that menu. Click on Additional Drivers.

Also, note that any detected wireless networks will appear under the Network Manager menu on the bar on the top of the screen, not in the Network Connections window. The window only shows networks that you've defined or have connected to previously.

---

### Post by DubyaStiles on 2011-09-05
> **ken_23434 said:**
> I have a Compaq laptop that has wireless issues too.  It's at home, so I cannot report the model #.  It's an older one, about 8 years old.  The problem I have w/ it is that I cannot get the "proprietary" driver to install.
 
It might be a similar problem w/ yours.
 
Under admin, click on "Additional Drivers" (I think that is the name, I am at work on an XP machine).  It will scan the system and inform you if there is a proprietary driver avail.
 
Ken
 
I did have a proprietary driver that was messing me up i guess but now that i have removed it on the network manager it says in grayed out text "wireless is disabled by hardware switch" and the "enable wireless," and "wireless networks" are also grayed out. Does this mean i need to look for drivers that are compatible with Ubuntu or what, I am pretty new to Ubuntu if you havent noticed. 

Also thank you 3rdalbum for showing me where to look for my network

---

### Post by lqlarry on 2011-09-05
I have a laptop that I use and would not install the wireless driver with 'Additional Drivers.'  The first thing I did was to open terminal - CTRL-ALT-T and made sure a hardware lister called lshw ins installed by using:
> sudo apt-get install lshw
It should already be installed in Ubuntu.  Then I run:
> sudo lshw -html > your-file-name.html
You can change your-file-name to whatever you want.  This saves your computer specs in your home folder as a html file.  Open it up and look for the section that has the information about your Wireless Interface.  Hopefully it will tell you what driver you need.  Google search it to see if what it takes to install this, or if you need another file to go with it and use synaptic or USC to install.  I did this with my HP and everything worked out.   

This spec sheet is a good thing to have on hand but remember to start with the easiest solution...make sure your wireless switch is turned on.   Enjoy

---

### Post by DubyaStiles on 2011-09-08
Haha ya my switch is turned on and I did what [lqlarry]("http://ubuntuforums.org/member.php?u=873428") told me to do and I had ~230 updates and now when i open network connections it says "Wireless Networks device not ready (firmware missing). Is it possible that Im boned and the drivers for my wireless card wont work with Ubuntu :(

---

### Post by fdrake on 2011-09-08
> **DubyaStiles said:**
> Haha ya my switch is turned on and I did what [lqlarry]("http://ubuntuforums.org/member.php?u=873428") told me to do and I had ~230 updates and now when i open network connections it says "Wireless Networks device not ready (firmware missing). Is it possible that Im boned and the drivers for my wireless card wont work with Ubuntu :(

can you post the results for
```

sudo lshw -c Network
dmesg | grep irmware

```

---

### Post by 3rdalbum on 2011-09-09
> **DubyaStiles said:**
> Haha ya my switch is turned on and I did what [lqlarry]("http://ubuntuforums.org/member.php?u=873428") told me to do and I had ~230 updates and now when i open network connections it says "Wireless Networks device not ready (firmware missing). Is it possible that Im boned and the drivers for my wireless card wont work with Ubuntu :(

You have a driver, but no firmware for the card. You might be able to find the firmware file online - do a search for the code number of the chipset (the commands posted by the above poster will help us find it) and the word "firmware". The firmware can be put into a folder on Linux and the card will work.

I'm curious though. You said that you were getting messed up by a propriatary driver. Which driver was this? It wasn't something to do with Broadcom, was it? (which would have probably been the firmware for the card).

---

### Post by DubyaStiles on 2011-09-10
> **fdrake said:**
> can you post the results for
```

sudo lshw -c Network
dmesg | grep irmware

```

  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:20400000-20403fff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:c4:71:41
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.111 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:16 ioport:2000(size=256) memory:d0100000-d01000ff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:37:82:f3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-11-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

---

### Post by DubyaStiles on 2011-09-10
> **3rdalbum said:**
> I'm curious though. You said that you were getting messed up by a propriatary driver. Which driver was this? It wasn't something to do with Broadcom, was it? (which would have probably been the firmware for the card).

Ya when i ran an Additional Drivers scan, it was what the the first guy told me to do , it found a proprietary drive and he suggested that that could be a problem and the scan gave me an option to remove it so i did was i wrong in doing this?

---

### Post by fdrake on 2011-09-10
can you also post the results for
```

lsmod
iwconfig
sudo iwlist scan
rfkill list all
less /etc/modprobe.d/blacklist.conf

```

your system shows 2 wireless drivers with two broadcom drivers. I think this may be due to a drive/firmware conflict. lest get the rest of the results and will try a way to solve it.

---

### Post by DubyaStiles on 2011-09-11
lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_conexant    43782  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
i915                  451033  3 
drm_kms_helper         40745  1 i915
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17322  0 
drm                   184164  4 i915,drm_kms_helper
snd                    55295  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
psmouse                73312  0 
arc4                   12473  2 
i2c_algo_bit           13184  1 i915
serio_raw              12990  0 
hp_wmi                 13418  0 
b43                   296610  0 
sparse_keymap          13666  1 hp_wmi
video                  18951  1 i915
mac80211              257001  1 b43
cfg80211              156212  2 b43,mac80211
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
libahci                25548  1 ahci
8139too                23208  0 
8139cp                 22497  0 
ssb                    45942  1 b43
maynard@maynard-Presario-C500-RZ350UA-ABA:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
maynard@maynard-Presario-C500-RZ350UA-ABA:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

maynard@maynard-Presario-C500-RZ350UA-ABA:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
maynard@maynard-Presario-C500-RZ350UA-ABA:~$ less /etc/modprobe.d/blacklist.conf

---

### Post by fdrake on 2011-09-11
try this :
```

sudo modprobe -r b43
sudo modprobe -r b43-pci-bridge
sudo apt-get install b43-fwcutter
sudo modprobe b43

```
reboot and try if it works.
if the problem persists please post again the results of the commands in post #13, #9

---

