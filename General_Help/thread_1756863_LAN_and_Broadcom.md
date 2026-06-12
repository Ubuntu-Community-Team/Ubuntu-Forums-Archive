---
title: "LAN and Broadcom"
date: 2011-05-12
forum: General Help
---

### Post by labtek on 2011-05-12
Hello to the group.

After loading Ubuntu 10.10 on an Acer Aspire 5100, I find that the onboard LAN does not work. My router "sees" the laptop but my laptop does not "see" the router. Ubuntu says that the firmware is not installed.

I read earlier posts about an issue with Broadcom and later editions of Ubuntu but I haven't seen a definitive fix. With the LAN not working, it is not possible to connect to the Internet and further compounds the problem.

My understanding is that the Acer Aspire 5100 uses a Broadcom LAN. How can I install the firmware that it is asking for?

Thanks for any thoughts.

---

### Post by lyrikdis on 2011-07-31
i am haveing the same exact issue with my acer aspire 5100. i am brand new to linux with virtually no knowledge of it. and installed ubuntu 11.04 any info on what to try would be awsome

edit. haveing same issue except my lan works just wireless same issue

---

### Post by wildmanne39 on 2011-07-31
Hi, run this command in a terminal 
```
cat /etc/modprobe.d/blacklist.conf
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by lyrikdis on 2011-08-01
# This file lists those modules which we don't want to be loaded by
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
william@william-Aspire-5100:~$

---

### Post by wildmanne39 on 2011-08-01
Hi, run these commands please
```
sudo lshw -C network 
```
```
lsmod
```
```
lspci -nn | grep -e 0280 -e 0200
```
```
iwconfig
```
```
rfkill list all
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by lyrikdis on 2011-08-01
```
  william@william-Aspire-5100:~$ sudo lshw -C network
[sudo] password for william: 
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:a4000000-a4003fff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:da:52:88
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.6 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:21 ioport:a000(size=256) memory:b0300000-b03000ff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:19:7e:84:f2:73
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-10-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
william@william-Aspire-5100:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
binfmt_misc            13213  1 
ppdev                  12849  0 
arc4                   12473  2 
snd_hda_codec_realtek   255882  1 
joydev                 17322  0 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
b43                   296610  0 
snd_seq_midi           13132  0 
radeon                900494  3 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
mac80211              257001  1 b43
ttm                    65184  1 radeon
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39671  0 
drm_kms_helper         40745  1 radeon
drm                   180037  5 radeon,ttm,drm_kms_helper
uvcvideo               66851  0 
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27230  0 
i2c_algo_bit           13184  1 radeon
videodev               75143  1 uvcvideo
psmouse                73312  0 
cfg80211              156212  2 b43,mac80211
pcmcia_rsrc            18292  1 yenta_socket
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
ati_agp                13202  0 
i2c_piix4              13095  0 
k8temp                 12872  0 
shpchp                 32345  0 
video                  18951  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
8139too                23208  0 
8139cp                 22497  0 
sdhci_pci              13623  0 
sdhci                  22720  1 sdhci_pci
ssb                    45942  1 b43
sata_sil               13278  2 
pata_atiixp            12968  0 
william@william-Aspire-5100:~$ lspci -nn | grep -e 0280 -e 0200
02:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
06:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
william@william-Aspire-5100:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
william@william-Aspire-5100:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
william@william-Aspire-5100:~$ 

```

---

### Post by wildmanne39 on 2011-08-01
Hi, run these commands please
```
dmesg | grep wlan0
```
```
dmesg | grep firmware
```
```
sudo iwlist scan
```
```
dmesg | grep 19.0
```
```
lsmod | grep b3
```
```
dmesg | grep b43
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by lyrikdis on 2011-08-01
```
william@william-Aspire-5100:~$ dmesg | grep wlan0
william@william-Aspire-5100:~$ dmesg | grep firmware
[   15.989050] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
william@william-Aspire-5100:~$ sudo iwlist scan
[sudo] password for william: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

william@william-Aspire-5100:~$ dmesg | grep 19.0
[    1.571980] cpuidle: using governor ladder
william@william-Aspire-5100:~$ lsmod | grep b3
william@william-Aspire-5100:~$ dmesg | grep b43
[    1.743820] b43-pci-bridge 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.743835] b43-pci-bridge 0000:02:00.0: setting latency timer to 64
[   15.420624] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   15.775879] Registered led device: b43-phy0::tx
[   15.775911] Registered led device: b43-phy0::rx
[   15.775947] Registered led device: b43-phy0::radio
[   15.989039] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   15.989045] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   15.989050] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
william@william-Aspire-5100:~$ 

```

---

### Post by lyrikdis on 2011-08-01
tryed oing what code told me to do whent to page tryed downloading that cutter tool but idk i think i just really need to do a clean install and start trouble shooting again  this is what it said   ```
 william@william-Aspire-5100:~$ sudo apt-get install b43-fwcutter
[sudo] password for william: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.38-8 dkms linux-headers-2.6.38-8-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up firmware-b43-lpphy-installer (4.174.64.19-5) ...
Not supported card here (PCI id 14e4:4311)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-lpphy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
william@william-Aspire-5100:~$ 
```

---

### Post by wildmanne39 on 2011-08-01
Hi, I am working on that exact same error message in another thread right now.
Try this I am going to give you a zip file and here is how to install it.

Down load the file then drag and drop the file to your desktop. Right-click it and select Extract Here. Open a terminal and do:
```
cd Desktop
sudo mv b43/ /lib/firmware
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
You will need to unplug your wired connection then restart your computer.
Now does your wireless work?
Thank you

---

### Post by lyrikdis on 2011-08-01
ya not working ```
  william@william-Aspire-5100:~$ cd Desktop
william@william-Aspire-5100:~/Desktop$ sudo mv b43/ /lib/firmware
[sudo] password for william: 
#Sorry, try again.
[sudo] password for william: 
mv: cannot move `b43/' to `/lib/firmware/b43': Directory not empty
william@william-Aspire-5100:~/Desktop$ 






  
```

---

### Post by wildmanne39 on 2011-08-01
Hi, try it this way.
```
sudo mv b43 /lib/firmware
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
let me know if it works.
Thank you

---

### Post by lyrikdis on 2011-08-01
i now have wireless which is awsome but i hope i didnt mess anything up while trying

---

### Post by wildmanne39 on 2011-08-01
Hi, you should be ok, I am glad you got it working,would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by lyrikdis on 2011-08-01
ok. and thank you for your help. if support for other things happen like this i will be very happy away from windows thanks again prob solved. btw i cant mark this solved prob because i didnt start the thread

---

### Post by wildmanne39 on 2011-08-01
Hi, your welcome! anytime you need help just start a thread there is always someone willing to help.

---

### Post by hindered on 2012-02-17
Hi, I got the same issue on my Acer Aspire 5100 and it's solved. Thank you, I'll try to learn this stuff so I can know some secret unknowable shadowy stuff like this wild39 guy

---

### Post by IvanRadev on 2012-03-22
oxo@oxo-Aspire-5100:~$ sudo mv b43 /lib/firmware
[sudo] password for oxo: 
mv: impossible  stat for «b43»: Not found this file or catalogue
oxo@oxo-Aspire-5100:~$

---

### Post by IvanRadev on 2012-03-22
oxo@oxo-Aspire-5100:~$ cd Desktop
bash: cd: Desktop: &#1053;&#1077;&#1090; &#1090;&#1072;&#1082;&#1086;&#1075;&#1086; &#1092;&#1072;&#1081;&#1083;&#1072; &#1080;&#1083;&#1080; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072;
oxo@oxo-Aspire-5100:~$ 


 I don`t no whay.....my ubunto on russian ?!

---

### Post by wildmanne39 on 2012-03-22
Hi, did you follow the directions exactly in post 10?
thanks

---

### Post by IvanRadev on 2012-03-25
> **wildmanne39 said:**
> Hi, did you follow the directions exactly in post 10?
thanks

yes...I`m follow you`r instruction.....save b43.zip on my desktop....and extract it on desktop.....after that terminal
cd Desktop ......but everything it is same :(  thanks.....respect

---

### Post by IvanRadev on 2012-03-25
and I`m did you`r comand 
oxo@oxo-Aspire-5100:~$ sudo mv b43/ /lib/firmware
[sudo] password for oxo: 
mv: &#1085;&#1077;&#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086; &#1074;&#1099;&#1087;&#1086;&#1083;&#1085;&#1080;&#1090;&#1100; stat &#1076;&#1083;&#1103; «b43/»: &#1053;&#1077;&#1090; &#1090;&#1072;&#1082;&#1086;&#1075;&#1086; &#1092;&#1072;&#1081;&#1083;&#1072; &#1080;&#1083;&#1080; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072;
oxo@oxo-Aspire-5100:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
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
oxo@oxo-Aspire-5100:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:1c:15:9f
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.108 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:21 ioport:a000(size=256) memory:c0202000-c02020ff
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:22 memory:c0200000-c0201fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:16:cf:5a:b5:55
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-16-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
oxo@oxo-Aspire-5100:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
acer_wmi               23302  0 
sparse_keymap          13658  1 acer_wmi
snd_hda_codec_realtek   254163  1 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
snd_hda_intel          24262  4 
snd_hda_codec          91859  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
radeon                929507  2 
pcmcia                 39822  0 
snd_rawmidi            25241  1 snd_seq_midi
arc4                   12473  2 
snd_seq_midi_event     14475  1 snd_seq_midi
b43                   318816  0 
mac80211              393421  1 b43
ttm                    65224  1 radeon
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         32889  1 radeon
drm                   192194  4 radeon,ttm,drm_kms_helper
psmouse                73673  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
serio_raw              12990  0 
k8temp                 12905  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
cfg80211              172427  2 b43,mac80211
snd                    55902  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13199  1 radeon
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_piix4              13093  0 
shpchp                 32356  0 
binfmt_misc            17292  1 
wmi                    18744  1 acer_wmi
ati_agp                13242  0 
video                  18908  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
8139too                23283  0 
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
8139cp                 22636  0 
ssb                    50682  1 b43
pata_atiixp            12967  3 
oxo@oxo-Aspire-5100:~$ lspci -nn | grep -e 0280 -e 0200
06:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
oxo@oxo-Aspire-5100:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
oxo@oxo-Aspire-5100:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
oxo@oxo-Aspire-5100:~$ dmesg | grep wlan0
oxo@oxo-Aspire-5100:~$ dmesg | grep firmware
[   20.450781] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
oxo@oxo-Aspire-5100:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

oxo@oxo-Aspire-5100:~$ dmesg | grep 19.0
[    0.000000] reg 1, base: 1920MB, range: 128MB, type UC
[    0.000000] total RAM covered: 1920M
[    0.000000] reg 1, base: 1920MB, range: 128MB, type UC
[   19.007038] type=1400 audit(1332721866.370:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=701 comm="apparmor_parser"
[   19.015944] type=1400 audit(1332721866.378:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=701 comm="apparmor_parser"
[   19.031025] 
[   19.031034] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge window: [mem 0xc0200000-0xc02fffff]
[   19.031039] pcmcia_socket pcmcia_socket0: cs: memory probe 0xc0200000-0xc02fffff: excluding 0xc0200000-0xc020ffff
[   19.031059] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge window: [mem 0x80000000-0x83ffffff pref]
[   19.031062] pcmcia_socket pcmcia_socket0: cs: memory probe 0x80000000-0x83ffffff: excluding 0x80000000-0x83ffffff
[   19.819707] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
oxo@oxo-Aspire-5100:~$ lsmod | grep b3
oxo@oxo-Aspire-5100:~$ dmesg | grep b43
[    1.382587] b43-pci-bridge 0000:06:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   18.844180] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   18.979041] Registered led device: b43-phy0::tx
[   18.979091] Registered led device: b43-phy0::rx
[   18.979139] Registered led device: b43-phy0::radio
[   20.450771] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   20.450777] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   20.450781] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
oxo@oxo-Aspire-5100:~$ cd Desktop
bash: cd: Desktop: &#1053;&#1077;&#1090; &#1090;&#1072;&#1082;&#1086;&#1075;&#1086; &#1092;&#1072;&#1081;&#1083;&#1072; &#1080;&#1083;&#1080; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072;
oxo@oxo-Aspire-5100:~$ 

I did every you`r instruction #5...#6....#7   :))))

from that site [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware)  

oxo@oxo-Aspire-5100:~$ sudo apt-get install firmware-b43-installer
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1089;&#1087;&#1080;&#1089;&#1082;&#1086;&#1074; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
&#1055;&#1086;&#1089;&#1090;&#1088;&#1086;&#1077;&#1085;&#1080;&#1077; &#1076;&#1077;&#1088;&#1077;&#1074;&#1072; &#1079;&#1072;&#1074;&#1080;&#1089;&#1080;&#1084;&#1086;&#1089;&#1090;&#1077;&#1081; * * **


I`m completed IHUUUUUU     thanks   and respect ....&#1057;&#1087;&#1072;&#1089;&#1080;&#1073;&#1086; :)

---

### Post by wildmanne39 on 2012-03-25
Hi, try this instead run the commands one line at a time and watch for errors.
```
[http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz]("http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz")
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
sudo modprobe b43
```
Thanks

---

