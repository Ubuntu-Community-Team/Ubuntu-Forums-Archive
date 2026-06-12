---
title: "I need help!"
date: 2011-07-13
forum: General Help
---

### Post by louisgonick on 2011-07-13
Ok. I have been trying to get help on this forum for almost 2 weeks on how to get wifi to work on my laptop. I've posted many threads and all I get is redundant questions that don't get me anywhere. From what I know i need to get some madwifi drivers for my atheros card. Somebody gave me some commands to install them but now I get: you removed the configuration file /etc/modprobe.d/blacklist-ath_pci.conf . I tried to download it from the madwifi site and I get a folder full of files and I cant figure it out how to intall them . There is a file called install but it is some license agreement. How am i supposed to install this??? This is my first time with Linux in my life and it has mostly been a pain in the ***.

---

### Post by wildmanne39 on 2011-07-13
> **louisgonick said:**
> Ok. I have been trying to get help on this forum for almost 2 weeks on how to get wifi to work on my laptop. I've posted many threads and all I get is redundant questions that don't get me anywhere. From what I know i need to get some madwifi drivers for my atheros card. Somebody gave me some commands to install them but now I get: you removed the configuration file /etc/modprobe.d/blacklist-ath_pci.conf . I tried to download it from the madwifi site and I get a folder full of files and I cant figure it out how to intall them . There is a file called install but it is some license agreement. How am i supposed to install this??? This is my first time with Linux in my life and it has mostly been a pain in the ***.Hi, we need to start with these commands.
```
sudo lshw -C network
```
```
lspci -nn
```
```
iwconfig
```
```
lsmod
```
post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by louisgonick on 2011-07-13
> **wildmanne39 said:**
> Hi, we need to start with these commands.
```
sudo lshw -C network
```
```
lspci -nn
```
```
iwconfig
```
```
lsmod
```
post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

Sorry for the late response but here they are:

sudo lshw -C netwrok:
```
 resources: irq:43 ioport:3000(size=256) memory:90410000-90410fff memory:90400000-9040ffff memory:90420000-9043ffff
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wifi0
       version: 01
       serial: 00:24:2b:e5:00:33
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless

```

lspci -nm:
```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
00:1f.6 Signal processing controller [1180]: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem [8086:2932] (rev 03)
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)

```

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```
lsmod:
```
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27479  1 
snd_hda_codec_conexant    43782  1 
joydev                 17322  0 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
i915                  450944  4 
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
drm_kms_helper         40745  1 i915
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   180037  5 i915,drm_kms_helper
wlan_scan_sta          21945  1 
i2c_algo_bit           13184  1 i915
ath_rate_sample        17279  1 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
serio_raw              12990  0 
soundcore              12600  1 snd
video                  18951  1 i915
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
ath_pci               183044  0 
wlan                  224640  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               398701  3 ath_rate_sample,ath_pci
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
usb_storage            43946  0 
hid                    77084  1 usbhid
uas                    17676  0 
r8169                  42534  0 
ahci                   21591  2 
libahci                25548  1 ahci

```

---

### Post by wildmanne39 on 2011-07-13
Hi, I found a site that talks about the card, you can try this, I saw your post the other day but I did not find any real  good solution.

Also note that since you have tried other things first it might conflict getting the card working, in the past I had to get rid of everything I had installed previously before my card would work, but my card is not the same as yours.
1. You need to open synaptic,then click on settings, repositories, updates then check unsupported natty updates.

2.From a terminal window type:
```
sudo apt-get update
```
> sudo apt-get dist-upgrade
```
sudo apt-get dist-upgrade
```

3. ```
sudo apt-get install linux-backports-modules-wireless-natty-generic
```

4. This installs the backports package, which includes compat-wireless. When this is installed, reboot your computer. If wireless now works then congratulations. You’re one of the lucky ones!! If, as is likely the case, the wireless still doesn’t work, then open a terminal window and type:

5. ```
sudo rmmod ath5k
```
```
sudo rmmod ath
```
```
sudo modprobe ath5k
```

These instructions were used by a person to get his same card working, I hope it fixes your problem.

---

### Post by louisgonick on 2011-07-13
> **wildmanne39 said:**
> Hi, I found a site that talks about the card, you can try this, I saw your post the other day but I did not find any real  good solution.

Also note that since you have tried other things first it might conflict getting the card working, in the past I had to get rid of everything I had installed previously before my card would work, but my card is not the same as yours.
1. You need to open synaptic,then click on settings, repositories, updates then check unsupported natty updates.

2.From a terminal window type:
```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

3. ```
sudo apt-get install linux-backports-modules-wireless-natty-generic
```

4. This installs the backports package, which includes compat-wireless. When this is installed, reboot your computer. If wireless now works then congratulations. You’re one of the lucky ones!! If, as is likely the case, the wireless still doesn’t work, then open a terminal window and type:

5. ```
sudo rmmod ath5k
```
```
sudo rmmod ath
```
```
sudo modprobe ath5k
```

These instructions were used by a person to get his same card working, I hope it fixes your problem.

when I try to run :sudo rmmod ath5k it tells me this:```
ERROR: Module ath5k does not exist in /proc/modules

```

---

### Post by wildmanne39 on 2011-07-13
Hi, thats ok it just means it is already removed or was never there. That is what the command is for it removes it. Go a head and run 
**sudo modprobe ath5k** you may have to reboot afterwards but hopefully you will be able to enter your password and connect to the net.

---

### Post by louisgonick on 2011-07-13
> **wildmanne39 said:**
> Hi, thats ok it just means it is already removed or was never there. That is what the command is for it removes it. Go a head and run 
**sudo modprobe ath5k** you may have to reboot afterwards but hopefully you will be able to enter your password and connect to the net.

at first the light of the wireless button went from red to blue, which meant that it turned on but after I rebooted the light is red and I cant connect through wireless :(

---

### Post by wildmanne39 on 2011-07-13
> **louisgonick said:**
> at first the light of the wireless button went from red to blue, which meant that it turned on but after I rebooted the light is red and I cant connect through wireless :(Hi, that is progress, at least the light came on. Try this
```
rfkill unblock wifi
```
```
sudo ifconfig wlan0 down
```
```
sudo ifconfig wlan0 up
```
if this does not work type this in a terminal
```
lsmod
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by louisgonick on 2011-07-13
> **wildmanne39 said:**
> Hi, that is progress, at least the light came on. Try this
```
rfkill unblock wifi
```
```
sudo ifconfig wlan0 down
```
```
sudo ifconfig wlan0 up
```
if this does not work type this in a terminal
```
lsmod
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

now the wireless light is blue but I still have no connectivity.

heres what i got from lsmod:
```
Module                  Size  Used by
arc4                   12473  2 
ath5k                 144412  0 
ath                    19141  1 ath5k
mac80211              257001  1 ath5k
cfg80211              156212  3 ath5k,ath,mac80211
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27535  1 
joydev                 17322  0 
snd_hda_codec_conexant    43782  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
psmouse                73312  0 
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i915                  450934  4 
drm_kms_helper         40745  1 i915
drm                   180037  5 i915,drm_kms_helper
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  0 
uas                    17676  0 
ahci                   21591  2 
libahci                25548  1 ahci
r8169                  42534  0
```

---

### Post by louisgonick on 2011-07-13
I tried rebooting again to see if that fixed the problem and now my wireless light is red again

---

### Post by wildmanne39 on 2011-07-13
> **louisgonick said:**
> I tried rebooting again to see if that fixed the problem and now my wireless light is red again
Hi, try this again
```
sudo rmmod ath
```
Also make sure there is only one athoes  driver being used in synaptic and see if any ndiswrapper drivers are installed while you have synaptic open if so right click on them and choose remove completely. 

In the right top corner of the screen click on the network icon and make sure wireless is enabled. You will probably have to enter a password to connect to your network.

If still does not work post the result of this with the network card blue light on.

---

### Post by louisgonick on 2011-07-13
> **wildmanne39 said:**
> Hi, try this again
```
sudo rmmod ath
```
Also make sure there is only one athoes  driver being used in synaptic and see if any ndiswrapper drivers are installed while you have synaptic open if so right click on them and choose remove completely. 

In the right top corner of the screen click on the network icon and make sure wireless is enabled. You will probably have to enter a password to connect to your network.

If still does not work post the result of this with the network card blue light on.

I tried the command: sudo rmmod ath and it tells me: ```
ERROR: Module ath is in use by ath5k

```

I'm sorry but I dont know how to check for that in synaptic. Can you tell me how to do it? I searched for ndiswrapper and some files appear and it tells me that they have to do with the kernel, should I delete them all? When I click on the network thing on the top bar I do get the option to enable wireless but above it tells me that wireless is disabled.

---

### Post by wildmanne39 on 2011-07-13
Hi, did you click on enable wireless it should have a check mark beside it when it is enabled. If so then we will go from there.

After you check the enabled run this command and post the results.
```
iwconfig
```
Is today the first time the light started coming on?

---

### Post by louisgonick on 2011-07-13
> **wildmanne39 said:**
> Hi, did you click on enable wireless it should have a check mark beside it when it is enabled. If so then we will go from there.

After you check the enabled run this command and post the results.
```
iwconfig
```
Is today the first time the light started coming on?
today is the first time that the wireless button goes from red to blue in ubuntu.

yes I did enable wireless, there is a check right next to it.
heres the result: ```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

---

### Post by wildmanne39 on 2011-07-13
Hi, asked an expert to take a look hopefully he will because at this point it is just a minor thing, I suspect another driver is causing problems.

---

### Post by louisgonick on 2011-07-13
> **wildmanne39 said:**
> Hi, asked an expert to take a look hopefully he will because at this point it is just a minor thing, I suspect another driver is causing problems.

Any help is appreciated

---

### Post by wildmanne39 on 2011-07-14
> **louisgonick said:**
> Any help is appreciated, do you have any clue of what driver might it be?
Hi, you know you might just need to go in and setup your wireless card manually. 

Click on the internet icon then edit connections. I see you do not have a 
ssid listed here is what my looks like and your ssid will be the name of your network. I am including screenshots.

---

### Post by louisgonick on 2011-07-14
> **wildmanne39 said:**
> Hi, you know you might just need to go in and setup your wireless card manually. 

Click on the internet icon then edit connections. I see you do not have a 
ssid listed here is what my looks like and your ssid will be the name of your network. I am including screenshots.

I already set up my network but my wireless card is now off and it doesn't turn on through the button

---

### Post by wildmanne39 on 2011-07-14
> **louisgonick said:**
> I already set up my network but my wireless card is now off and it doesn't turn on through the buttonHi, run those first three commands again that are in post#8 and see if it will turn back on. 

If it does see if you can connect, you should have to enter a password.
If you can not connect make sure firefox is not in offline mode, then post the results of these commands again while your light is on.
```
sudo lshw -C network
```
```
iwconfig
```

---

### Post by louisgonick on 2011-07-14
> **wildmanne39 said:**
> Hi, run those first three commands again that are in post#8 and see if it will turn back on. 

If it does see if you can connect, you should have to enter a password.
If you can not connect make sure firefox is not in offline mode, then post the results of these commands again while your light is on.
```
sudo lshw -C network
```
```
iwconfig
```

I tried the commands and I get this: ```
wlan0: ERROR while getting interface flags: No such device
```

---

### Post by wildmanne39 on 2011-07-14
> **louisgonick said:**
> I tried the commands and I get this: ```
wlan0: ERROR while getting interface flags: No such device
```Hi, here is were I want you to look and see if you have ndiswrapper installed.

---

### Post by louisgonick on 2011-07-14
> **wildmanne39 said:**
> Hi, here is were I want you to look and see if you have ndiswrapper installed.

I get the exact same thing that you get but when I right click the only option that is available is mark for installation

---

### Post by wildmanne39 on 2011-07-14
> **louisgonick said:**
> I get the exact same thing that you get but when I right click the only option that is available is mark for installation
Ok, that means it is not installed thats good. Disconnect your wired internet then try to connect with the wireless. You can not connected wired and wireless at the same time. Is there a button that turns on your wireless? also some laptops have a function key that turns it on and off. like fn11. After you disconnect your wire connection restart your computer.

---

### Post by louisgonick on 2011-07-14
> **wildmanne39 said:**
> Ok, that means it is not installed thats good. Disconnect your wired internet then try to connect with the wireless. You can not connected wired and wireless at the same time. Is there a button that turns on your wireless? also some laptops have a function key that turns it on and off. like fn11. After you disconnect your wire connection restart your computer.

yes there is a button that turns it on, which at the same time is an indicator on weather the card is on or off. There is no other way to turn it on.

---

### Post by louisgonick on 2011-07-14
I tried disconnecting the internet cable from my pc and rebooting and the wireless is still off.

---

### Post by wildmanne39 on 2011-07-14
> **louisgonick said:**
> I tried rebooting again to see if that fixed the problem and now my wireless light is red again
Hi, try this
```
sudo rmmod -f ath5k
```
```
sudo rfkill unblock all
```
```
sudo modprobe ath5k
```

---

### Post by louisgonick on 2011-07-14
> **wildmanne39 said:**
> Hi, try this
```
sudo rmmod -f ath5k
```
```
sudo rfkill unblock all
```
```
sudo modprobe ath5k
```

Now my wifi card is on but I still can't connect to wifi

---

### Post by wildmanne39 on 2011-07-14
Hi, progress now post the out come of these commands no that the light is on.
```
sudo lshw -C network
```
```
iwconfig
```
```
lsmod
```
```
gksudo gedit /etc/resolv.conf
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets. Also I found a bug report about that card turning off and having to be manually turned on by the commands I gave you so it will probably turn off again, but we can try to fix that after it connects.

Does it see the wireless connection while it is on? Check and make sure your connection is like mine in my screenshots.

---

### Post by louisgonick on 2011-07-14
> **wildmanne39 said:**
> Hi, progress now post the out come of these commands no that the light is on.
```
sudo lshw -C network
```
```
iwconfig
```
```
lsmod
```
```
gksudo gedit /etc/resolv.conf
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets. Also I found a bug report about that card turning off and having to be manually turned on by the commands I gave you so it will probably turn off again, but we can try to fix that after it connects.

Does it see the wireless connection while it is on? Check and make sure your connection is like mine in my screenshots.

YES!!! finally wifi is working. But i had to turn it on using commands.

---

### Post by louisgonick on 2011-07-14
I also noticed that the light blinks from blue to red. This is not normal.

---

### Post by wildmanne39 on 2011-07-14
Hi, that is what I figured here is the bug report on it. I am glad it is working.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/478036](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/478036)

---

### Post by louisgonick on 2011-07-14
> **wildmanne39 said:**
> Hi, that is what I figured here is the bug report on it. I am glad it is working.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/478036](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/478036)

But the light blinks red and blue. This should not be happening. It either stays red or blue. But atleast wifi works.

---

### Post by wildmanne39 on 2011-07-14
Hi, it might help if you still run those last commands I gave you, we might be able to see what is going on.

---

### Post by louisgonick on 2011-07-14
Heres the results:
sudo lshw -C network
```
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:77:19:6d
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:3000(size=256) memory:90410000-90410fff memory:90400000-9040ffff memory:90420000-9043ffff
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:24:2b:e5:00:33
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-10-generic firmware=N/A ip=192.168.1.4 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:92600000-9260ffff
```
iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"             RED DE CASA"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:E0:4D:9C:28:F8   
          Bit Rate=24 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=26/70  Signal level=-84 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:284   Missed beacon:0
```

lsmod:
```
Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  2 
aes_generic            38023  1 aes_i586
ath5k                 144412  0 
arc4                   12473  2 
ath                    19141  1 ath5k
mac80211              257001  1 ath5k
cfg80211              156212  3 ath5k,ath,mac80211
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_conexant    43782  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
joydev                 17322  0 
binfmt_misc            13213  1 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
i915                  450934  4 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         40745  1 i915
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hp_wmi                 13418  0 
psmouse                73312  0 
drm                   180037  5 i915,drm_kms_helper
i2c_algo_bit           13184  1 i915
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
sparse_keymap          13666  1 hp_wmi
serio_raw              12990  0 
usb_storage            43946  0 
uas                    17676  0 
r8169                  42534  0 
ahci                   21591  2 
libahci                25548  1 ahci

```

gksudo gedit /etc/resolv.conf:
# Generated by NetworkManager
nameserver 200.107.10.52
nameserver 200.107.60.58

---

### Post by wildmanne39 on 2011-07-14
Hi, I looked at everything and I do not see  anything that would make your light flash it may have to do with the bug. What I would do is mark this thread solved then if you have more issues start a thread in networking where some of the experts are. I may start working over there some myself but I am still no where near an expert.

---

### Post by louisgonick on 2011-07-14
> **wildmanne39 said:**
> Hi, I looked at everything and I do not see  anything that would make your light flash it may have to do with the bug. What I would do is mark this thread solved then if you have more issues start a thread in networking where some of the experts are. I may start working over there some myself but I am still no where near an expert.

Ok, I really appreciated your help :)

---

### Post by wildmanne39 on 2011-07-14
Hi, you are very welcome! glad I could help.

---

