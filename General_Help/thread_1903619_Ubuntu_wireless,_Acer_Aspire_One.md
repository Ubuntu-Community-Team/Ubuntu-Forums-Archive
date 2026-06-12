---
title: "Ubuntu wireless, Acer Aspire One"
date: 2012-01-02
forum: General Help
---

### Post by LinP on 2012-01-02
Sorry if this is in the wrong place i posted it where i thought was correct please move if needed. My problem is I have an acer aspire one netbook windows 7 starter dualbooted with the latest ubuntu I believe it's 11.10. I have no wifi i believe i need a fix for broadcom sta drivers but after reading a long time on the forum closest I could find was to go wired to fix it however i tried plugging in my ethernet only to have that not work as well. It just flashes as if loading then says wired network disconnected. Any idea how I can fix this would be greatly appreciated I have ubuntu on my desktop and have always liked linux but for every time I have tried to install on the netbook it is always the same problem with the wireless not working and I really want it to work as using windows 7 is a nightmare. Thankyou in advance for any replies It is worth mentioning i am no expert so any help should if possible be in a step by step beginner form please.

---

### Post by bluexrider on 2012-01-02
Try plugging in the LAN cable and rebooting.

---

### Post by fdrake on 2012-01-02
in the terminal can you post the output of 
```
ifconfig
```
while you are wire..

---

### Post by LinP on 2012-01-03
Output from ifconfig.


eth0 Link encap: Ethernet   HWaddr  70:5a:b6:cb:1f:e2 
        UP BROADCAST MULTICAST  MTU:1500  Metric:1
        RX packets:0 errors:0 dropped:0 overruns:0 frame:0
        TX packets:0 errors:0 drops:0 overruns:0  carrier:0
        collisions:0 txqueuelen:100
        RX bytes:0 (0.0 B)  TX bytes:0  (0.0 B)
        Interrupt:46

lo      Link encap:Local loopback
         inet   addr:127.0.0.1   Mask:255.0.0.0
         inet6  addr:  ::1/128  scope:Host
         UP LOOPBACK RUNNING  MTU:16436   Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RXbytes:0  (0.0  b)   TX bytes:0   (0.0  B)

Hope that helps

---

### Post by LinP on 2012-01-03
@bluexrider I tried that but did nothing I'm afraid just keeps loading and saying the same you have been disconnected message. Thanks for the reply though.

---

### Post by fdrake on 2012-01-03
> **LinP said:**
> Output from ifconfig.


eth0 Link encap: Ethernet   HWaddr  70:5a:b6:cb:1f:e2 
        UP BROADCAST MULTICAST  MTU:1500  Metric:1
        RX packets:0 errors:0 dropped:0 overruns:0 frame:0
        TX packets:0 errors:0 drops:0 overruns:0  carrier:0
        collisions:0 txqueuelen:100
        RX bytes:0 (0.0 B)  TX bytes:0  (0.0 B)
        Interrupt:46

lo      Link encap:Local loopback
         inet   addr:127.0.0.1   Mask:255.0.0.0
         inet6  addr:  ::1/128  scope:Host
         UP LOOPBACK RUNNING  MTU:16436   Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RXbytes:0  (0.0  b)   TX bytes:0   (0.0  B)

Hope that helps

can you please post the output of these commands (while you are wired to the router!)
```

lshw -c network
less /etc/network/interfaces
route -n
nm-tool

```
can you also try too boot in win7 and use thye wired connection with it, and while connected can you boot in ubuntu and see if that works.

---

### Post by bluexrider on 2012-01-03
> **LinP said:**
> @bluexrider I tried that but did nothing I'm afraid just keeps loading and saying the same you have been disconnected message. Thanks for the reply though.
lets at least try the 

```
lshw -c network
```and see where we are

---

### Post by LinP on 2012-01-03
lshw -c network
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:57100000-57103fff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 70:5a:b6:cb:1f:e2
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A latency=0 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:46 memory:55000000-5503ffff ioport:2000(size=128)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: c4:17:fe:b6:16:51
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-12-generic firmware=N/A multicast=yes wireless=IEEE 802.11bg




# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback



 route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface




NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             unavailable
  Default:           no
  HW Address:        C4:17:FE:B6:16:51

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             disconnected
  Default:           no
  HW Address:        70:5A:B6:CB:1F:E2

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on



This is the output from all commands you asked for thankyou for your time

---

### Post by TBABill on 2012-01-03
2 options for you. First is go to the "STA no internet access" section of [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) and follow those instructions.

Or, if you are willing to reinstall Ubuntu you can fire up the Live CD or DVD. No need to plug into a router. Instead, just go to Additional Drivers, select the STA driver, click activate and when it says you need to restart the computer, DO NOT RESTART! It's a live session and it will lose the settings...instead go back to a terminal and ```
sudo modprobe wl
``` Wait a few moments and then connect to your wireless network.

Once you have the active network connected, then reinstall Ubuntu. When it finishes you'll have a working wireless connection.

---

### Post by bluexrider on 2012-01-03
> **TBABill said:**
> 2 options for you. First is go to the "STA no internet access" section of [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) and follow those instructions.

Or, if you are willing to reinstall Ubuntu you can fire up the Live CD or DVD. No need to plug into a router. Instead, just go to Additional Drivers, select the STA driver, click activate and when it says you need to restart the computer, DO NOT RESTART! It's a live session and it will lose the settings...instead go back to a terminal and ```
sudo modprobe wl
``` Wait a few moments and then connect to your wireless network.

Once you have the active network connected, then reinstall Ubuntu. When it finishes you'll have a working wireless connection.
This would be a quick fix to a complex problem

---

### Post by LinP on 2012-01-03
The problem is it's a netbook so cannot boot from cd and also it won't connect to the internet wired either. I was hoping I could download a fix onto a usb plug that in and install the drivers straight from usb or whatever. It might be worth mentioning that i used wubi to install as I'm no expert would this be a factor perhaps in the problem?

---

### Post by fdrake on 2012-01-03
a couple of things to note:
your wireless card BCM4312 works only with module wl ([http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)), which should be already in your kernel. If you don't have the file then try to download the *.deb file from here [https://launchpad.net/ubuntu/oneiric/i386/bcmwl-kernel-source/5.100.82.38+bdcom-0ubuntu4](https://launchpad.net/ubuntu/oneiric/i386/bcmwl-kernel-source/5.100.82.38+bdcom-0ubuntu4)
so try this please :
```

less /etc/modprobe.d/blacklist.conf | grep "blacklist wl" -v > black.txt
sudo cp /etc/modprobe.d/blacklist.conf /etc/modprobe.d/blacklist.conf.bk 
sudo cp black.txt /etc/modprobe.d/blacklist.conf
echo "blacklist brcm*" | sudo tee -a /etc/modprobe.d/blacklist.conf
echo "blacklist b43*" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe wl
sudo reboot now

```

i am still figuring out about your wired connection..

---

### Post by LinP on 2012-01-03
Should I enter that line by line or all at once? Thankyou all for your time and patience.

---

### Post by fdrake on 2012-01-03
> **LinP said:**
> Should I enter that line by line or all at once? Thankyou all for your time and patience.you can try 1 by 1. also may I suggest you to download that *deb file I pointed you,(check again my post I edited it), just in case the last command ("sudo modprobe wl
") gives an error, install the deb and retry the last command again.

---

### Post by LinP on 2012-01-03
Edit- I downloaded the deb file and double clicked it. I am now on a screen that tells me to install this through my normal software channels. What are my normal software channels because if it is synaptic package manager i can't get that without internet as it is not installed by default anymore. also the option to install this deb file is greyed out i cannot click it.

---

### Post by TBABill on 2012-01-04
If you are able to get a connection anywhere in order to be able to download the files, you may also have success with the BCM4312 LP-PHY by doing: ```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
``` I think you were missing firmware and the b43 will support your device only with the correct firmware for it.

---

### Post by TBABill on 2012-01-04
Can you right click the file and select open with gdebi?

---

### Post by LinP on 2012-01-04
> **TBABill said:**
> Can you right click the file and select open with gdebi?

No that option is not there when I right click.

---

### Post by LinP on 2012-01-05
So does anyone reading have any other ideas how to install this deb file?

---

### Post by MARP1961 on 2012-01-05
Go to Software Centre, search for and install **gdebi**. Reboot, right click the deb file and select 'Install With Gdebi'.

---

### Post by rjf1 on 2012-01-05
If you can't do a a live cd, put the iso on a usb stick instead, and then do the procedure that TBABill mentioned.

---

### Post by LinP on 2012-01-05
This too is greyed out so I cannot install. Is it possible to force an install of the .deb file by using a terminal command?  Would it be easier or possible to put another os on like for example mint or something. I have no problem trying another os that may work out of the box  apart from joli os which I have tried before and didn't  like that much. I just really hate using windows.

---

### Post by MARP1961 on 2012-01-06
I think the latest Linux Mint will behave as the latest Ubuntu. If possible, I would try to start from scratch with a fresh install of the latest Ubuntu. The Broadcom wifi is the problem. They are a complete 'pain in the rear' with Ubuntu. Some people have given up on them and opened up their computers and replaced them with a compatible Intel version which just costs a few pounds (if you don't mind getting out the screwdriver).

In Lucid Lynx 10.04, my son's Dell Inspiron 6400 would flash up a message from Additional Drivers giving a choice of STA or B43. STA refused to install but we always got it working with B43. Later versions of Ubuntu seemed not to offer the B43 driver; only STA. In the end I did fresh installs, ignored the Additional Drivers application and searched for the B43 firmware installer in Synaptic. After installing B43 and rebooting we've not failed to get wireless working.

Strangely, I do remember trying Fedora which seemed to work 'out of the box' as you say. I think Ubuntu ought to try to fix the 'STA/B43problem' with these Broadcom cards.

---

### Post by LinP on 2012-01-07
Thanks for the reply but I wouldn't know where to start with swapping out the cards. I guess I will just uninstall and hope the next upgrade they fix it. Won't hold my breath though as I have been waiting ever since unr was released:(

---

### Post by wildmanne39 on 2012-01-07
Hi, this card should not be hard to get working normally please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
cat /etc/modprobe.d/blacklist.conf
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by LinP on 2012-01-08
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux

01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e01b]
    Kernel driver in use: b43-pci-bridge
--
03:00.0 Ethernet controller [0200]: Atheros Communications AR8132 Fast Ethernet [1969:1062] (rev c0)
    Subsystem: Acer Incorporated [ALI] Device [1025:022f]
    Kernel driver in use: atl1c


lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no



Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
usb_storage            44173  1 
uas                    17699  0 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
binfmt_misc            17292  1 
joydev                 17393  0 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
acer_wmi               23302  0 
snd_hwdep              13276  1 snd_hda_codec
sparse_keymap          13658  1 acer_wmi
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
i915                  505108  3 
arc4                   12473  2 
uvcvideo               67271  0 
b43                   318816  0 
videodev               85626  1 uvcvideo
snd_timer              28932  2 snd_pcm,snd_seq
psmouse                73673  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              12990  0 
mac80211              272785  1 b43
drm_kms_helper         32889  1 i915
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   192226  4 i915,drm_kms_helper
cfg80211              172392  2 b43,mac80211
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
wmi                    18744  1 acer_wmi
video                  18908  1 i915
ahci                   21634  1 
libahci                25727  1 ahci
atl1c                  36638  0 
ssb                    50682  1 b43



This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist brcm*
blacklist b43*


```

---

### Post by LinP on 2012-01-08
Above is the output from the commands you gave me. Hope this helps do you think it is still straightforward and easy to get this card working ? I do hope so thank you for your time either way.

---

### Post by MARP1961 on 2012-01-08
Have a read of this to see if it helps:

[http://www.computerandyou.net/2011/05/how-to-solve-no-wireless-networks-in-ubuntu-11-04/](http://www.computerandyou.net/2011/05/how-to-solve-no-wireless-networks-in-ubuntu-11-04/)

If you can face doing a fresh install of the latest Ubuntu first, I would do it. You do need at least a wired ethernet connection working.

---

### Post by wildmanne39 on 2012-01-08
Hi, let's start with removing the driver from the blacklist please.
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
Remove:
```
blacklist b43*
```
save, exit gedit.

Then let's turn power management off:
```
gksudo gedit /etc/pm/power.d/wireless
```
add these lines:
```

#!/bin/sh

/sbin/iwconfig wlan0 power off

```
Save, exit gedit and reboot.  If it does not come on post the output of:
```
iwconfig
rfkill list all
sudo iwlist scan
nm-tool
lsmod | grep b43
```
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e  wlan -e etork | tail -n55
```
Thanks

---

### Post by LinP on 2012-01-08
I will be trying this now and will let you know the outcome. Does anyone  know why this is and has been a problem for such a long time? joli os works fine but i much prefer ubuntu. Is there a way of asking ubuntu developers to fix the drivers ?

---

### Post by miasmablk on 2012-01-08
the problem is most likely related to the STA driver... try removing it and installing both

```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
```

I have the same card and have had similar problems with that driver.

---

### Post by miasmablk on 2012-01-08
you can try moving the .deb package into your home directory from your downloads folder and run the following to "force" install the .deb package
```
sudo dpkg -i --force-all bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu4_i386.deb
```

---

### Post by LinP on 2012-01-09
How do I remove the sta driver?

---

### Post by wildmanne39 on 2012-01-09
Hi LinP, you do not have the sta driver installed, we can help you more when you do what was suggested in post 29.

I suspect you have the wrong firmware but I will not know until I see the information from that post and the first set of commands in that post may fix your problem.
Thanks

---

### Post by LinP on 2012-01-10
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no


lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down



b43                   318816  0 
mac80211              272785  1 b43
cfg80211              172392  2 b43,mac80211
ssb                    50682  1 b43



Jan  5 11:26:49 ubuntu kernel: [ 2339.216682] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
Jan  5 11:26:49 ubuntu NetworkManager[777]: <warn> (wlan0): firmware may be missing.
Jan  5 11:26:49 ubuntu NetworkManager[777]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jan  5 11:32:49 ubuntu NetworkManager[777]: <info> (wlan0): now unmanaged
Jan  5 11:32:49 ubuntu NetworkManager[777]: <info> (wlan0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
Jan  7 23:30:04 ubuntu kernel: [ 2704.408281] b43-pci-bridge 0000:01:00.0: PCI INT A disabled
Jan  7 23:30:04 ubuntu kernel: [ 2705.872610] b43-pci-bridge 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan  7 23:30:06 ubuntu NetworkManager[777]: <info> (wlan0): now managed
Jan  7 23:30:06 ubuntu NetworkManager[777]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan  7 23:30:06 ubuntu NetworkManager[777]: <info> (wlan0): bringing up device.
Jan  7 23:30:06 ubuntu NetworkManager[777]: <warn> (wlan0): firmware may be missing.
Jan  7 23:30:06 ubuntu kernel: [ 2710.846316] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
Jan  7 23:30:06 ubuntu NetworkManager[777]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jan  7 23:30:06 ubuntu kernel: [ 2710.846329] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
Jan  7 23:30:06 ubuntu kernel: [ 2710.846339] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
Jan  8 16:58:03 ubuntu kernel: [    2.021320] b43-pci-bridge 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan  8 16:58:03 ubuntu kernel: [    2.021351] b43-pci-bridge 0000:01:00.0: setting latency timer to 64
Jan  8 16:58:03 ubuntu kernel: [   22.293639] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
Jan  8 16:58:03 ubuntu kernel: [   22.431385] Registered led device: b43-phy0::tx
Jan  8 16:58:03 ubuntu kernel: [   22.431574] Registered led device: b43-phy0::rx
Jan  8 16:58:03 ubuntu kernel: [   22.431761] Registered led device: b43-phy0::radio
Jan  8 16:58:05 ubuntu NetworkManager[785]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/ssb0:0/net/wlan0, iface: wlan0)
Jan  8 16:58:05 ubuntu NetworkManager[785]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan  8 16:58:05 ubuntu NetworkManager[785]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan  8 16:58:05 ubuntu NetworkManager[785]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Jan  8 16:58:05 ubuntu NetworkManager[785]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Jan  8 16:58:05 ubuntu NetworkManager[785]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Jan  8 16:58:05 ubuntu NetworkManager[785]: <info> (wlan0): now managed
Jan  8 16:58:05 ubuntu NetworkManager[785]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan  8 16:58:05 ubuntu NetworkManager[785]: <info> (wlan0): bringing up device.
Jan  8 16:58:05 ubuntu kernel: [   29.601500] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
Jan  8 16:58:05 ubuntu kernel: [   29.601513] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
Jan  8 16:58:05 ubuntu kernel: [   29.601523] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
Jan  8 16:58:05 ubuntu NetworkManager[785]: <warn> (wlan0): firmware may be missing.
Jan  8 16:58:05 ubuntu NetworkManager[785]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jan  8 17:07:18 ubuntu kernel: [    2.024576] b43-pci-bridge 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan  8 17:07:18 ubuntu kernel: [    2.024608] b43-pci-bridge 0000:01:00.0: setting latency timer to 64
Jan  8 17:07:18 ubuntu kernel: [   22.164467] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
Jan  8 17:07:18 ubuntu kernel: [   22.451596] Registered led device: b43-phy0::tx
Jan  8 17:07:18 ubuntu kernel: [   22.451777] Registered led device: b43-phy0::rx
Jan  8 17:07:18 ubuntu kernel: [   22.451996] Registered led device: b43-phy0::radio
Jan  8 17:07:19 ubuntu NetworkManager[767]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/ssb0:0/net/wlan0, iface: wlan0)
Jan  8 17:07:19 ubuntu NetworkManager[767]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan  8 17:07:19 ubuntu NetworkManager[767]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan  8 17:07:20 ubuntu NetworkManager[767]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Jan  8 17:07:20 ubuntu NetworkManager[767]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Jan  8 17:07:20 ubuntu NetworkManager[767]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Jan  8 17:07:20 ubuntu NetworkManager[767]: <info> (wlan0): now managed
Jan  8 17:07:20 ubuntu NetworkManager[767]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan  8 17:07:20 ubuntu NetworkManager[767]: <info> (wlan0): bringing up device.
Jan  8 17:07:20 ubuntu kernel: [   29.191713] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
Jan  8 17:07:20 ubuntu kernel: [   29.191726] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
Jan  8 17:07:20 ubuntu kernel: [   29.191736] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
Jan  8 17:07:20 ubuntu NetworkManager[767]: <warn> (wlan0): firmware may be missing.
Jan  8 17:07:20 ubuntu NetworkManager[767]: <info> (wlan0): deactivating device (reason 'managed') [2]


```

---

### Post by wildmanne39 on 2012-01-10
Hi, you do have a firmware issue and possibly one or two more but let's start with the firmware problem.

Copy and paste all commands for accuracy.

Download the b43 zip file then drag and drop the file to your desktop. 
Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
your wireless should start working, I also recommend doing this please:
```
gksudo gedit /etc/pm/power.d/wireless
```
(this will create or edit a configuration file that will override the default powermanagement behavior) and enter the following: 
```
#!/bin/sh

/sbin/iwconfig wlan0 power off
```
save, exit gedit and reboot.

I will not be on much today because it is my birthday.
Thanks

---

### Post by LinP on 2012-01-11
sudo cp Desktop/b43/*  /lib/firmware/b43 after this code I got "cannot stat no such file or directory  and with rmod i got command not found.

---

### Post by Quarkrad on 2012-01-11
Apologies to break into this thread.  I noticed you used Wubi to install Ubuntu.  I have one of these notebooks and dislike/hate Windoze.  I created a new partition and have the dualboot option - everything on the notebook, including wifi, worked 'out of the box'.  I am using Ubuntu 10.10 but I see no reason it would not be the same on 11.10.  Perhaps you need to consider creating a new partition and re-installing.  In 30mins you will have a fully functioning Ubuntu system on your notebook - as I did. (I had terrible Skype issues on a number of Desktops with 10.10 but when I installed 10.10 on the Acer notebook it too worked 'out of the box').

---

### Post by adityamagadi on 2012-01-11
while installing your ubuntu 11.10 are you connected to the internet? if yes while installing have you checked the box which mentions "download and install third-party software"? if u havent done these try doing it n be plugged to AC source while installing..i had the same issue wit my acer these steps fixed the issue. let me know if it worked .

---

### Post by LinP on 2012-01-11
> **Quarkrad said:**
> Apologies to break into this thread.  I noticed you used Wubi to install Ubuntu.  I have one of these notebooks and dislike/hate Windoze.  I created a new partition and have the dualboot option - everything on the notebook, including wifi, worked 'out of the box'.  I am using Ubuntu 10.10 but I see no reason it would not be the same on 11.10.  Perhaps you need to consider creating a new partition and re-installing.  In 30mins you will have a fully functioning Ubuntu system on your notebook - as I did. (I had terrible Skype issues on a number of Desktops with 10.10 but when I installed 10.10 on the Acer notebook it too worked 'out of the box').

Problem is it's a netbook and wubi is the best I can do as I don't trust myself to try installing it without wubi unless I had a step by step walkthrough with answers incase anything went wrong I am just not that knowledgeable i feel to try an install without something like wubi

---

### Post by wildmanne39 on 2012-01-12
Hi LinP, did you download the b43zip file and place it on your desktop and extract it there?

Copy and paste all commands for accuracy one line at a time, because you have typo's.

Please let me know how it goes this time.
Thanks

---

### Post by LinP on 2012-01-13
Thanks for the reply and patience. Unfortunately I get the same  response that I previously got and I did it 4 separate times but always the same outcome. For the second command the output I get is can't stat etc and for the rmod command I get command not found. I cannot understand what is going wrong as like I said I did it exactly as you said copied and pasted for accuracy etc 4 different times but still no luck.

---

### Post by wildmanne39 on 2012-01-13
Hi, after you pasted the command with sudo did you enter your user password? if so you may be having problems with sudo and we need it to install the firmware, to find out please run this command and post the results here.
```
sudo apt-get update
```
and the remove module command should look like this:
```
sudo rmmod -f
```
Thanks

---

### Post by LinP on 2012-01-13
Yes I entered my password for sudo after that command. I just entered the sudo -get update and got the output "failed to fetch http://security.ubuntu.com/ubuntu/dists/oneiric-security/inrelease."

---

### Post by lintoon on 2012-01-13
I had a problem with an sta driver.  Apparently mine wasn't supplied in the 3.x kernel, when it had been supplied in earlier version.

My fix (for a different wifi adapter) was to find the device id by running lsusb and to add that id to a driver supplied in the kernel.   

My solution is here:  [http://ubuntuforums.org/showthread.php?t=1902715](http://ubuntuforums.org/showthread.php?t=1902715)

This is probably not your answer but I thought I would just mention because you never know, and it may just spark an idea for someone.

---

### Post by wildmanne39 on 2012-01-13
Hi, did you download the b43zip file in post 36 that I attached for you? please refer to the screenshot.

If not you can use another computer to download it and put it on a flash drive then copy it to your ubuntu desktop.
Thanks

---

### Post by LinP on 2012-01-13
Yes i had already downloaded that and selected extract here on the desktop.

---

### Post by wildmanne39 on 2012-01-13
Hi, go back to post 36 and try again.

The second command had two spaces in it and it is only suppose to have one so I have corrected it, if you get any errors go ahead and run the other commands anyway and if it does not come on  after about 30 seconds reboot. 

I am sorry I did not see the extra space just looking at it, it was almost impossible to tell that it was there.
Thanks

---

### Post by LinP on 2012-01-14
I went ahead and did that but still no wireless. Id like to thank you for your help and extreme patience I think it will take the developers coming up with a fix for this problem which I hope they do soon. I guess until then I give up as there is probably nothing more that can be tried.

---

### Post by wildmanne39 on 2012-01-14
Hi, I have seen many people get there wireless issues resolved this way, did your light come on? if so we can troubleshot it, were there errors this time when you ran the codes?
Thanks

---

### Post by LinP on 2012-01-15
Yes apart from the first one all others  returned an error.

---

### Post by wildmanne39 on 2012-01-15
Hi, I do not know why those commands to install the driver keeps failing but we can try it this way.

Open software center type bcm into the search window anything that has a green check mark by it uninstall then reboot.

Then:
```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
```
Reboot
Thanks

---

