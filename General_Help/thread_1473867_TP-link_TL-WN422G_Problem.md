---
title: "TP-link TL-WN422G Problem"
date: 2010-05-05
forum: General Help
---

### Post by disPlay on 2010-05-05
Hi have posted this issue on this section [http://ubuntuforums.org/showthread.php?p=9243312#post9243312](http://ubuntuforums.org/showthread.php?p=9243312#post9243312) but nobody help me so I am trying to post the issue here.


I was trying to use the TP-link TL-WN422G in my ubuntu OS, the  problem is that when I insert it I don't have a response from the usb  wireless card. Any way to the usb card work on ubuntu?


Thanks,
disPlay

---

### Post by moviemaniac on 2010-05-05
can you post the output of lsusb?

---

### Post by disPlay on 2010-05-05
Sorry but I am new to ubuntu can you tell-me how I do that?


in conclusion the ubuntu don't recongnize the usb wireless card.

---

### Post by moviemaniac on 2010-05-05
//edit: fuggettaboutit, see below

---

### Post by moviemaniac on 2010-05-05
Okay, here's one thing to try:
Download this file to cour Desktop: [http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=blob;f=ar9271.fw;h=2398e5517b0ad7da7adad54763b91705a3d2acb7;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=blob;f=ar9271.fw;h=2398e5517b0ad7da7adad54763b91705a3d2acb7;hb=HEAD)

then open up a terminal and enter these commands one after the other (you will be asked for your password on the last step)

cd Desktop
sudo mv ar9271.fw /lib/firmware

reboot and see whether it works. Be sure to unplug your device and plug it in again after rebooting.

If it doesn't, follow these steps:

Download this file to your desktop: [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)
Then open a terminal and enter these commands one after the other (you will be asked for your password on the last step):
cd Desktop
tar xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless-2.6
./scripts/driver-select ath9k_htc
make && sudo make install

after that reboot.

---

### Post by disPlay on 2010-05-05
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0cf3:1006 Atheros Communications, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




Seems that ubuntu don't recognize the wireless card.

---

### Post by moviemaniac on 2010-05-05
> **disPlay said:**
> Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 002: ID 0cf3:1006 Atheros Communications, Inc. **
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Seems that ubuntu don't recognize the wireless card.

Yes it does, I marked it in bold. However you'll need updated drivers and (new) firmware to get it to work. Just follow my instructions above and you should be fine.

---

### Post by disPlay on 2010-05-05
I think that atheros is the one that is on my motherboard. not my wireless .

---

### Post by disPlay on 2010-05-05
I was wrong, It is my usb ... I unplug it from the computer and if I run lsusb again I will not see the atheros again. I will do what you said to me and see if it works.

---

### Post by moviemaniac on 2010-05-05
you can see what you have built in by using lspci - lsusb unly polls - as the name suggests - the usb ports ;)

---

### Post by disPlay on 2010-05-05
:p  the link that you provided to me the firmware have 0 bytes is this fine? it sounds strange I never saw a 0 byte firmware

---

### Post by moviemaniac on 2010-05-05
Very strange indeed - try this link: [http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=blob_plain;f=ar9271.fw;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=blob_plain;f=ar9271.fw;hb=HEAD)

---

### Post by disPlay on 2010-05-05
I tried the first but nothing. Trying the second one.

---

### Post by disPlay on 2010-05-05
The second one worked fine. Thanks for all the help. But one last question, why the ubuntu developers don't have a look at packs with drivers and firmwares like this and incorporate them in future versions?

---

### Post by moviemaniac on 2010-05-05
Well, support will most likely be there out of the box in a future version of Ubuntu (10.10) - some things come too late for inclusion in a certain release and this is one of these rare but unavoidable cases.

---

### Post by disPlay on 2010-05-05
Ok, and again thanks for the help moviemaniac.

Cya you later.

---

### Post by lukasz357 on 2010-05-11
Hello everybody. I am new here.
I have a similar problem like above.
I can't use my tl-wn422g v2 on my Ubuntu10.04 ( on 9.10 it didn't work too )
I tried doing your instruction, but when i type make, after moment there is an error like this:
/home/lukasz357/Pulpit/compat-wireless-2010-05-09/net/mac80211/scan.c: In function ‘ieee80211_scan_state_decision’:
/home/lukasz357/Pulpit/compat-wireless-2010-05-09/net/mac80211/scan.c:510: error: implicit declaration of function ‘pm_qos_request’
make[3]: *** [/home/lukasz357/Pulpit/compat-wireless-2010-05-09/net/mac80211/scan.o] B&#322;&#261;d 1
make[2]: *** [/home/lukasz357/Pulpit/compat-wireless-2010-05-09/net/mac80211] B&#322;&#261;d 2
make[1]: *** [_module_/home/lukasz357/Pulpit/compat-wireless-2010-05-09] B&#322;&#261;d 2
make[1]: Opuszczenie katalogu `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [modules] B&#322;&#261;d 2

I am polish.. Blad means  Error and Opuszczenie katalogu means Leaving directory

I would be really glad if anyone could help me.

---

### Post by moviemaniac on 2010-05-11
Try to use this compat-wireless package, there seems to be a problem with the latest one: [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-05-06.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-05-06.tar.bz2)

Oh, and just to be sure: you also have to adjust the file names in the commands to match the downloaded file.

---

### Post by lukasz357 on 2010-05-11
Thanks a lot man :)
It was that package fault.. Now it works perfectly..

---

### Post by moviemaniac on 2010-05-11
Glad to hear/read it works now :)

---

### Post by kivallee on 2010-05-12
Thanks a lot, I have finished to install it smoothly and it works very well. This is a perfect solution much better than the solution of ndiswrapper!!
:guitar:

> **moviemaniac said:**
> Try to use this compat-wireless package, there seems to be a problem with the latest one: [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-05-06.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-05-06.tar.bz2)

Oh, and just to be sure: you also have to adjust the file names in the commands to match the downloaded file.

---

### Post by kivallee on 2010-05-13
I got a new problem today after I install the drive of wn422G sucessfully by this solution. I undated the ubuntu packages from the upate center (I forgot the exact name.), and it haltd at the setp of grup update, so I choose the updating without grup update and finish all packages, then reboot.
After rebooting, I saw the wireless disappeared!!!
So do anyone know what happened? 
I will try to reinstall the driver by this solution tonight, should I?:confused:

---

### Post by moviemaniac on 2010-05-13
Yes, you will have to run above steps every time the kernel of your machine is updated.

---

### Post by tzarsmango on 2010-05-13
> **moviemaniac said:**
> Yes, you will have to run above steps every time the kernel of your machine is updated.

Hi and thanks for the solution. I'll try it right away...

Is there a way to put this wireless support into the kernel configuration after ubuntu installation? Because I doubt if we start ubuntu installation with the usb already installed, then somehow ubuntu detects the wireless and keeps a happy life with it...

---

### Post by moviemaniac on 2010-05-14
I don't know what it is exactly you want but I believe you want the module to automatically be updated when a new kernel is installed?

This is possible if you make a so-called DKMS module. You can find generic instructions on how to accomplish this here (beware - this is for experienced users only as you have to change quite a few things from the example shown):

[http://wiki.centos.org/HowTos/BuildingKernelModules#head-d313bd351f90d4f25a2143b7bbcff73f927731f0](http://wiki.centos.org/HowTos/BuildingKernelModules#head-d313bd351f90d4f25a2143b7bbcff73f927731f0)

---

### Post by Reinach on 2010-05-17
> **moviemaniac said:**
> 
If it doesn't, follow these steps:

Download this file to your desktop: [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)
Then open a terminal and enter these commands one after the other (you will be asked for your password on the last step):
cd Desktop
tar xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless-2.6
./scripts/driver-select ath9k_htc
make && sudo make install

after that reboot.

My friend, i apllied your above instructions on my system, and as it seems my Wireless USB Adapter TP-LINK WN722N is working at last!!! :):)

Here is the device+chipset from lsusb:

> Bus 001 Device 002: ID 0cf3:9271 Atheros Communications, Inc. 


[SIZE="4"]**But**[/SIZE]: the option "enable wireless connections" has been lost from the network icon on the panel, when right-clicking it. Also, left-click on the same network icon shows no wireless networks when i unplug the USB wireless adapter(it shows only the ethernet connection). This means that [SIZE="5"][COLOR="Red"]the built-in wireless device seems to be out of operation[/COLOR][/SIZE], though i have the wireless button on my laptop turned on. 

My built-in wireless device worked properly as of earlier, before i make the build of the TP-LINK drivers in your instructions. In my dual boot system the built-in  wireless card works perfectly in the Vista as i checked this a few minutes ago. (Here i must say that i turned the wireless button off at some point so to check if the USB adapter worked properly indeed, without the presence of the internal wireless card. But right after, i turned the button on again)

Besides, when i give the command 
```
ifconfig wlan0 up
```

so as to activate my internal wireless device (am i right??), i get the following:
```
wlan0: ERROR while getting interface flags: No such device
``` 
:confused::confused:

as if my internal wireless card is turned off. Have you any idea what can i do to reactivate this?

Thanks

---

### Post by moviemaniac on 2010-05-17
Hmmmm... could it be the internal card is being used as wlan1?

ifconfig wlan1 up

could you post what "lspci" gives you and also what "lsmod" gives you before (internal wlan working) and after (enabling and disabling the usb wifi device) recreating the problem?

---

### Post by Reinach on 2010-05-17
lspci before:
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040T PCI-E Fast Ethernet Controller (rev 12)
0a:01.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0a:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0a:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
```

lsmod before:
```
Module                  Size  Used by
aes_i586                8124  0 
aes_generic            27484  1 aes_i586
ipt_MASQUERADE          2204  0 
xt_state                1820  0 
ipt_REJECT              2812  0 
xt_tcpudp               2780  0 
nf_nat_h323             6204  0 
nf_conntrack_h323      48904  1 nf_nat_h323
nf_nat_pptp             2844  0 
nf_conntrack_pptp       5984  1 nf_nat_pptp
nf_conntrack_proto_gre     5344  1 nf_conntrack_pptp
nf_nat_proto_gre        2080  1 nf_nat_pptp
nf_nat_tftp             1340  0 
nf_conntrack_tftp       4048  1 nf_nat_tftp
nf_nat_sip              6300  0 
nf_conntrack_sip       17872  1 nf_nat_sip
nf_nat_irc              2012  0 
nf_conntrack_irc        4992  1 nf_nat_irc
nf_nat_ftp              2652  0 
nf_conntrack_ftp        6880  1 nf_nat_ftp
iptable_nat             5500  0 
nf_nat                 18096  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      13352  3 iptable_nat,nf_nat
nf_conntrack           67484  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1756  1 nf_conntrack_ipv4
arc4                    1660  0 
ecb                     2524  0 
ath9k_htc              40064  0 
ath9k_common            6972  1 ath9k_htc
ath9k_hw              285296  2 ath9k_htc,ath9k_common
ath                     8924  2 ath9k_htc,ath9k_hw
compat_firmware_class     8220  1 ath9k_htc
binfmt_misc             8356  1 
ppdev                   6688  0 
bridge                 47952  0 
stp                     2272  1 bridge
bnep                   12060  2 
slamr                 427368  0 
joydev                 10240  0 
mac80211              237356  2 ath9k_htc,ath9k_common
compat                  3900  1 mac80211
snd_hda_codec_atihdmi     3356  1 
snd_hda_codec_conexant    20060  1 
pcmcia_core            36528  1 compat
snd_hda_intel          26920  1 
snd_hda_codec          75708  3 snd_hda_codec_atihdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14336  2 uvcvideo,videodev
cfg80211              148968  4 ath9k_htc,ath9k_common,ath,mac80211
iptable_filter          3100  0 
ip_tables              11692  2 iptable_nat,iptable_filter
x_tables               16544  6 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_nat,ip_tables
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                56500  0 
serio_raw               5280  0 
sdhci_pci               7100  0 
sdhci                  17504  1 sdhci_pci
led_class               4096  2 ath9k_htc,sdhci
fglrx                1989532  28 
snd                    59204  14 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
btusb                  11856  2 
omnibook               53876  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
usbhid                 38208  0 
usb_storage            52768  0 
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
sky2                   46560  0 
video                  19380  0 
output                  2780  1 video
intel_agp              27676  0 
agpgart                34988  2 fglrx,intel_agp

```

After connection of Wireless USB Adapter TP-LINK-WN722N:

lspci after:
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040T PCI-E Fast Ethernet Controller (rev 12)
0a:01.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0a:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0a:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

```

lsmod after:
```
Module                  Size  Used by
aes_i586                8124  0 
aes_generic            27484  1 aes_i586
ipt_MASQUERADE          2204  1 
xt_state                1820  1 
ipt_REJECT              2812  2 
xt_tcpudp               2780  4 
nf_nat_h323             6204  0 
nf_conntrack_h323      48904  1 nf_nat_h323
nf_nat_pptp             2844  0 
nf_conntrack_pptp       5984  1 nf_nat_pptp
nf_conntrack_proto_gre     5344  1 nf_conntrack_pptp
nf_nat_proto_gre        2080  1 nf_nat_pptp
nf_nat_tftp             1340  0 
nf_conntrack_tftp       4048  1 nf_nat_tftp
nf_nat_sip              6300  0 
nf_conntrack_sip       17872  1 nf_nat_sip
nf_nat_irc              2012  0 
nf_conntrack_irc        4992  1 nf_nat_irc
nf_nat_ftp              2652  0 
nf_conntrack_ftp        6880  1 nf_nat_ftp
iptable_nat             5500  1 
nf_nat                 18096  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      13352  4 iptable_nat,nf_nat
nf_conntrack           67484  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1756  1 nf_conntrack_ipv4
arc4                    1660  2 
ecb                     2524  2 
ath9k_htc              40064  0 
ath9k_common            6972  1 ath9k_htc
ath9k_hw              285296  2 ath9k_htc,ath9k_common
ath                     8924  2 ath9k_htc,ath9k_hw
compat_firmware_class     8220  1 ath9k_htc
binfmt_misc             8356  1 
ppdev                   6688  0 
bridge                 47952  0 
stp                     2272  1 bridge
bnep                   12060  2 
slamr                 427368  0 
joydev                 10240  0 
mac80211              237356  2 ath9k_htc,ath9k_common
compat                  3900  1 mac80211
snd_hda_codec_atihdmi     3356  1 
snd_hda_codec_conexant    20060  1 
pcmcia_core            36528  1 compat
snd_hda_intel          26920  1 
snd_hda_codec          75708  3 snd_hda_codec_atihdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14336  2 uvcvideo,videodev
cfg80211              148968  4 ath9k_htc,ath9k_common,ath,mac80211
iptable_filter          3100  1 
ip_tables              11692  2 iptable_nat,iptable_filter
x_tables               16544  6 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_nat,ip_tables
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                56500  0 
serio_raw               5280  0 
sdhci_pci               7100  0 
sdhci                  17504  1 sdhci_pci
led_class               4096  2 ath9k_htc,sdhci
fglrx                1989532  28 
snd                    59204  14 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
btusb                  11856  2 
omnibook               53876  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
usbhid                 38208  0 
usb_storage            52768  0 
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
sky2                   46560  0 
video                  19380  0 
output                  2780  1 video
intel_agp              27676  0 
agpgart                34988  2 fglrx,intel_agp

```


I know that my internal wireless device always used the wlan0 and not the wlan1 interface.

---

### Post by moviemaniac on 2010-05-17
hmmm... that looks okay.

How about

**dmesg | grep wlan** and **cat /var/log/syslog/ | grep wlan**

---

### Post by Reinach on 2010-05-18
The **dmesg | grep wlan** command gave nothing, so i print the result of the **dmesg** command. There is nothing about wlan in this, so i guess it must be deactivated (??):

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-20-generic (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 (Ubuntu 2.6.31-20.58-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfed0000 (usable)
[    0.000000]  BIOS-e820: 00000000bfed0000 - 00000000bfee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfee3000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0xbfed0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0BFF00000 mask FFFF00000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bfed0000 (usable)
[    0.000000]  modified: 00000000bfed0000 - 00000000bfee3000 (ACPI NVS)
[    0.000000]  modified: 00000000bfee3000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 378a3000 - 37fefb67
[    0.000000] Allocated new RAMDISK: 008b2000 - 00ffeb67
[    0.000000] Move RAMDISK from 00000000378a3000 - 0000000037fefb66 to 008b2000 - 00ffeb66
[    0.000000] ACPI: RSDP 000f7700 00024 (v02 TOSQCI)
[    0.000000] ACPI: XSDT bfed2e38 00074 (v01 TOSQCI TOSQCI00 06040000  LTP 00000000)
[    0.000000] ACPI: FACP bfedfc92 000F4 (v03 T0SQCI TOSQCI00 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT bfed427e 0B9A0 (v02 TOSQCI N.Jersey 06040000 MSFT 03000001)
[    0.000000] ACPI: FACS bfee2fc0 00040
[    0.000000] ACPI: HPET bfedfd86 00038 (v01 TOSQCI TOSQCI00 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG bfedfdbe 0003C (v01 TOSQCI TOSQCI00 06040000 LOHR 0000005A)
[    0.000000] ACPI: APIC bfedfdfa 00068 (v01 PTLTD  	 APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT bfedfe62 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SLIC bfedfe8a 00176 (v01 TOSQCI TOSQCI00 06040000  LTP 00000000)
[    0.000000] ACPI: SSDT bfed3fd1 002AD (v01 SataRe SataAhci 00001000 INTL 20061109)
[    0.000000] ACPI: SSDT bfed3438 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20061109)
[    0.000000] ACPI: SSDT bfed3392 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20061109)
[    0.000000] ACPI: SSDT bfed2eac 004E6 (v01  PmRef    CpuPm 00003000 INTL 20061109)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2182MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008ad060]    TEXT DATA BSS ==> [0000100000 - 00008ad060]
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [00008ae000 - 00008b1194]              BRK ==> [00008ae000 - 00008b1194]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008b2000 - 0000ffeb67]      NEW RAMDISK ==> [00008b2000 - 0000ffeb67]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f77b0] f77b0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000bfed0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bfed0
[    0.000000] On node 0 totalpages: 786027
[    0.000000] free_area_init_node: node 0, pgdat c0788900, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4366 pages used for memmap
[    0.000000]   HighMem zone: 554436 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:20000000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c2810000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 779885
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=122d27ea-9505-496d-8a73-f2a175790246 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 15722560 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000bfed0)
[    0.000000] Memory: 3086908k/3144512k available (4578k kernel code, 56284k reserved, 2146k data, 540k init, 2235208k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0792000 - 0xc0819000   ( 540 kB)
[    0.000000]       .data : 0xc0578948 - 0xc0791408   (2146 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0578948   (4578 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1828.678 MHz processor.
[    0.001409] Console: colour VGA+ 80x25
[    0.001413] console [tty0] enabled
[    0.001589] hpet clockevent registered
[    0.001593] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.001600] Calibrating delay loop (skipped), value calculated using timer frequency.. 3657.35 BogoMIPS (lpj=7314712)
[    0.001619] Security Framework initialized
[    0.001641] AppArmor: AppArmor initialized
[    0.001648] Mount-cache hash table entries: 512
[    0.001785] Initializing cgroup subsys ns
[    0.001790] Initializing cgroup subsys cpuacct
[    0.001795] Initializing cgroup subsys memory
[    0.001802] Initializing cgroup subsys freezer
[    0.001804] Initializing cgroup subsys net_cls
[    0.001820] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.001822] CPU: L2 cache: 2048K
[    0.001825] CPU: Physical Processor ID: 0
[    0.001827] CPU: Processor Core ID: 0
[    0.001831] mce: CPU supports 6 MCE banks
[    0.001838] CPU0: Thermal monitoring handled by SMI
[    0.001842] using mwait in idle threads.
[    0.001849] Performance Counters: Core2 events, Intel PMU driver.
[    0.001859] ... version:                 2
[    0.001860] ... bit width:               40
[    0.001862] ... generic counters:        2
[    0.001864] ... value mask:              000000ffffffffff
[    0.001866] ... max period:              000000007fffffff
[    0.001868] ... fixed-purpose counters:  3
[    0.001870] ... counter mask:            0000000700000003
[    0.001874] Checking 'hlt' instruction... OK.
[    0.018746] ACPI: Core revision 20090521
[    0.036433] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.076241] CPU0: Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz stepping 0d
[    0.080001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3657.51 BogoMIPS (lpj=7315030)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] mce: CPU supports 6 MCE banks
[    0.004000] CPU1: Thermal monitoring handled by SMI
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.165550] CPU1: Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz stepping 0d
[    0.165565] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.168024] Brought up 2 CPUs
[    0.168027] Total of 2 processors activated (7314.87 BogoMIPS).
[    0.168081] CPU0 attaching sched-domain:
[    0.168084]  domain 0: span 0-1 level MC
[    0.168087]   groups: 0 1
[    0.168093] CPU1 attaching sched-domain:
[    0.168095]  domain 0: span 0-1 level MC
[    0.168098]   groups: 1 0
[    0.168176] Booting paravirtualized kernel on bare hardware
[    0.168221] regulator: core version 0.5
[    0.168221] Time:  9:56:09  Date: 05/18/10
[    0.168221] NET: Registered protocol family 16
[    0.168229] EISA bus registered
[    0.168239] ACPI: bus type pci registered
[    0.168312] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.168315] PCI: MCFG area at e0000000 reserved in E820
[    0.168317] PCI: Using MMCONFIG for extended config space
[    0.168320] PCI: Using configuration type 1 for base access
[    0.169437] bio: create slab <bio-0> at 0
[    0.173049] ACPI: EC: Look up EC in DSDT
[    0.178216] ACPI: BIOS _OSI(Linux) query ignored
[    0.180024] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.696005] ACPI: EC: missing confirmations, switch off interrupt mode.
[    0.976087] ACPI: Interpreter enabled
[    0.976094] ACPI: (supports S0 S3 S4 S5)
[    0.976116] ACPI: Using IOAPIC for interrupt routing
[    1.036961] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    1.036964] ACPI: EC: driver started in poll mode
[    1.037327] ACPI: No dock devices found.
[    1.038017] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    1.038023] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7013450), AE_NOT_FOUND
[    1.038058] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    1.038188] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    1.038192] pci 0000:00:01.0: PME# disabled
[    1.038293] pci 0000:00:1a.0: reg 20 io port: [0x1800-0x181f]
[    1.038367] pci 0000:00:1a.1: reg 20 io port: [0x1820-0x183f]
[    1.038449] pci 0000:00:1a.7: reg 10 32bit mmio: [0xf0604800-0xf0604bff]
[    1.038522] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    1.038528] pci 0000:00:1a.7: PME# disabled
[    1.038590] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf0600000-0xf0603fff]
[    1.038660] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.038665] pci 0000:00:1b.0: PME# disabled
[    1.038764] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.038769] pci 0000:00:1c.0: PME# disabled
[    1.038869] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    1.038875] pci 0000:00:1c.1: PME# disabled
[    1.038978] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    1.038984] pci 0000:00:1c.3: PME# disabled
[    1.039059] pci 0000:00:1d.0: reg 20 io port: [0x1840-0x185f]
[    1.039133] pci 0000:00:1d.1: reg 20 io port: [0x1860-0x187f]
[    1.039207] pci 0000:00:1d.2: reg 20 io port: [0x1880-0x189f]
[    1.039287] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf0604c00-0xf0604fff]
[    1.039360] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    1.039366] pci 0000:00:1d.7: PME# disabled
[    1.039555] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    1.039560] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
[    1.039565] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
[    1.039572] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0200 (mask 0013)
[    1.039577] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 4 PIO at 0068 (mask 0007)
[    1.039635] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    1.039644] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    1.039653] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    1.039662] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    1.039671] pci 0000:00:1f.1: reg 20 io port: [0x18a0-0x18af]
[    1.039756] pci 0000:00:1f.2: reg 10 io port: [0x18d8-0x18df]
[    1.039765] pci 0000:00:1f.2: reg 14 io port: [0x18cc-0x18cf]
[    1.039774] pci 0000:00:1f.2: reg 18 io port: [0x18d0-0x18d7]
[    1.039784] pci 0000:00:1f.2: reg 1c io port: [0x18c8-0x18cb]
[    1.039793] pci 0000:00:1f.2: reg 20 io port: [0x18e0-0x18ff]
[    1.039802] pci 0000:00:1f.2: reg 24 32bit mmio: [0xf0604000-0xf06047ff]
[    1.039850] pci 0000:00:1f.2: PME# supported from D3hot
[    1.039856] pci 0000:00:1f.2: PME# disabled
[    1.039893] pci 0000:00:1f.3: reg 10 32bit mmio: [0x000000-0x0000ff]
[    1.039922] pci 0000:00:1f.3: reg 20 io port: [0x1c00-0x1c1f]
[    1.040012] pci 0000:01:00.0: reg 10 64bit mmio: [0xd0000000-0xdfffffff]
[    1.040027] pci 0000:01:00.0: reg 18 64bit mmio: [0xf0200000-0xf020ffff]
[    1.040036] pci 0000:01:00.0: reg 20 io port: [0x2000-0x20ff]
[    1.040052] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    1.040085] pci 0000:01:00.0: supports D1 D2
[    1.040145] pci 0000:01:00.1: reg 10 64bit mmio: [0xf0210000-0xf0213fff]
[    1.040209] pci 0000:01:00.1: supports D1 D2
[    1.040291] pci 0000:00:01.0: bridge io port: [0x2000-0x2fff]
[    1.040295] pci 0000:00:01.0: bridge 32bit mmio: [0xf0200000-0xf02fffff]
[    1.040301] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    1.040451] pci 0000:02:00.0: reg 10 32bit mmio: [0xf0300000-0xf0300fff]
[    1.040702] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    1.040716] pci 0000:02:00.0: PME# disabled
[    1.040843] pci 0000:00:1c.0: bridge 32bit mmio: [0xf0300000-0xf03fffff]
[    1.040936] pci 0000:03:00.0: reg 10 64bit mmio: [0xf0400000-0xf0403fff]
[    1.040949] pci 0000:03:00.0: reg 18 io port: [0x3000-0x30ff]
[    1.041045] pci 0000:03:00.0: supports D1 D2
[    1.041048] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.041055] pci 0000:03:00.0: PME# disabled
[    1.041144] pci 0000:00:1c.1: bridge io port: [0x3000-0x3fff]
[    1.041150] pci 0000:00:1c.1: bridge 32bit mmio: [0xf0400000-0xf04fffff]
[    1.041282] pci 0000:0a:01.0: reg 10 32bit mmio: [0xf0501000-0xf0501fff]
[    1.041292] pci 0000:0a:01.0: reg 14 32bit mmio: [0xf0500000-0xf05007ff]
[    1.041351] pci 0000:0a:01.0: supports D1 D2
[    1.041353] pci 0000:0a:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.041359] pci 0000:0a:01.0: PME# disabled
[    1.041414] pci 0000:0a:01.2: reg 10 32bit mmio: [0xf0500800-0xf05008ff]
[    1.041492] pci 0000:0a:01.2: supports D1 D2
[    1.041494] pci 0000:0a:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    1.041501] pci 0000:0a:01.2: PME# disabled
[    1.041556] pci 0000:0a:01.3: reg 10 32bit mmio: [0xf0502000-0xf0502fff]
[    1.041633] pci 0000:0a:01.3: supports D1 D2
[    1.041636] pci 0000:0a:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    1.041642] pci 0000:0a:01.3: PME# disabled
[    1.041723] pci 0000:00:1e.0: transparent bridge
[    1.041732] pci 0000:00:1e.0: bridge 32bit mmio: [0xf0500000-0xf05fffff]
[    1.041772] pci_bus 0000:00: on NUMA node 0
[    1.041777] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.041988] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    1.042080] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    1.042165] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    1.042252] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    1.042370] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    1.042506] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    1.042513] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7013450), AE_NOT_FOUND
[    1.055028] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    1.055148] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    1.055265] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    1.055385] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    1.055501] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    1.055624] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    1.055739] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    1.055855] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    1.056060] SCSI subsystem initialized
[    1.056068] libata version 3.00 loaded.
[    1.056068] usbcore: registered new interface driver usbfs
[    1.056068] usbcore: registered new interface driver hub
[    1.056068] usbcore: registered new device driver usb
[    1.056101] ACPI: WMI: Mapper loaded
[    1.056103] PCI: Using ACPI for IRQ routing
[    1.068010] Bluetooth: Core ver 2.15
[    1.068015] NET: Registered protocol family 31
[    1.068016] Bluetooth: HCI device and connection manager initialized
[    1.068019] Bluetooth: HCI socket layer initialized
[    1.068022] NetLabel: Initializing
[    1.068023] NetLabel:  domain hash size = 128
[    1.068025] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.068038] NetLabel:  unlabeled traffic allowed by default
[    1.068074] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    1.068080] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    1.076011] Switched to high resolution mode on CPU 0
[    1.077592] Switched to high resolution mode on CPU 1
[    1.085010] pnp: PnP ACPI init
[    1.085020] ACPI: bus type pnp registered
[    1.140527] pnp: PnP ACPI: found 9 devices
[    1.140530] ACPI: ACPI bus type pnp unregistered
[    1.140534] PnPBIOS: Disabled by ACPI PNP
[    1.140545] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    1.140548] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    1.140552] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    1.140555] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    1.140558] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    1.140561] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    1.140565] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved
[    1.140568] system 00:01: iomem range 0xff80000-0xff8ffff could not be reserved
[    1.140577] system 00:03: iomem range 0xfed00000-0xfed003ff has been reserved
[    1.140585] system 00:05: ioport range 0x800-0x80f has been reserved
[    1.140588] system 00:05: ioport range 0x1000-0x107f has been reserved
[    1.140591] system 00:05: ioport range 0x1180-0x11bf has been reserved
[    1.140594] system 00:05: ioport range 0xfe00-0xfe00 has been reserved
[    1.175270] AppArmor: AppArmor Filesystem Enabled
[    1.175348] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    1.175352] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    1.175357] pci 0000:00:01.0:   MEM window: 0xf0200000-0xf02fffff
[    1.175361] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    1.175367] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    1.175369] pci 0000:00:1c.0:   IO window: disabled
[    1.175376] pci 0000:00:1c.0:   MEM window: 0xf0300000-0xf03fffff
[    1.175382] pci 0000:00:1c.0:   PREFETCH window: disabled
[    1.175388] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    1.175392] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
[    1.175399] pci 0000:00:1c.1:   MEM window: 0xf0400000-0xf04fffff
[    1.175404] pci 0000:00:1c.1:   PREFETCH window: disabled
[    1.175410] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:05
[    1.175412] pci 0000:00:1c.3:   IO window: disabled
[    1.175419] pci 0000:00:1c.3:   MEM window: disabled
[    1.175424] pci 0000:00:1c.3:   PREFETCH window: disabled
[    1.175430] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:0a
[    1.175432] pci 0000:00:1e.0:   IO window: disabled
[    1.175439] pci 0000:00:1e.0:   MEM window: 0xf0500000-0xf05fffff
[    1.175444] pci 0000:00:1e.0:   PREFETCH window: disabled
[    1.175457]   alloc irq_desc for 16 on node -1
[    1.175459]   alloc kstat_irqs on node -1
[    1.175464] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.175469] pci 0000:00:01.0: setting latency timer to 64
[    1.175478]   alloc irq_desc for 17 on node -1
[    1.175480]   alloc kstat_irqs on node -1
[    1.175484] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.175490] pci 0000:00:1c.0: setting latency timer to 64
[    1.175500] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.175506] pci 0000:00:1c.1: setting latency timer to 64
[    1.175515]   alloc irq_desc for 19 on node -1
[    1.175517]   alloc kstat_irqs on node -1
[    1.175521] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.175526] pci 0000:00:1c.3: setting latency timer to 64
[    1.175536] pci 0000:00:1e.0: setting latency timer to 64
[    1.175541] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    1.175544] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    1.175546] pci_bus 0000:01: resource 0 io:  [0x2000-0x2fff]
[    1.175549] pci_bus 0000:01: resource 1 mem: [0xf0200000-0xf02fffff]
[    1.175552] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    1.175556] pci_bus 0000:02: resource 1 mem: [0xf0300000-0xf03fffff]
[    1.175559] pci_bus 0000:03: resource 0 io:  [0x3000-0x3fff]
[    1.175561] pci_bus 0000:03: resource 1 mem: [0xf0400000-0xf04fffff]
[    1.175564] pci_bus 0000:0a: resource 1 mem: [0xf0500000-0xf05fffff]
[    1.175567] pci_bus 0000:0a: resource 3 io:  [0x00-0xffff]
[    1.175570] pci_bus 0000:0a: resource 4 mem: [0x000000-0xffffffff]
[    1.175609] NET: Registered protocol family 2
[    1.175710] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.176054] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.176594] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.176824] TCP: Hash tables configured (established 131072 bind 65536)
[    1.176827] TCP reno registered
[    1.176899] NET: Registered protocol family 1
[    1.176964] Trying to unpack rootfs image as initramfs...
[    1.381408] Freeing initrd memory: 7474k freed
[    1.385719] Simple Boot Flag at 0x36 set to 0x1
[    1.385918] cpufreq-nforce2: No nForce2 chipset.
[    1.385948] Scanning for low memory corruption every 60 seconds
[    1.386057] audit: initializing netlink socket (disabled)
[    1.386074] type=2000 audit(1274176569.385:1): initialized
[    1.395581] highmem bounce pool size: 64 pages
[    1.395587] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.397195] VFS: Disk quotas dquot_6.5.2
[    1.397262] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.397854] fuse init (API version 7.12)
[    1.397948] msgmni has been set to 1679
[    1.398173] alg: No test for stdrng (krng)
[    1.398184] io scheduler noop registered
[    1.398187] io scheduler anticipatory registered
[    1.398189] io scheduler deadline registered
[    1.398232] io scheduler cfq registered (default)
[    1.398389] pci 0000:01:00.0: Boot video device
[    1.398534]   alloc irq_desc for 24 on node -1
[    1.398536]   alloc kstat_irqs on node -1
[    1.398546] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    1.398554] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.398704]   alloc irq_desc for 25 on node -1
[    1.398706]   alloc kstat_irqs on node -1
[    1.398716] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X
[    1.398728] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.398897]   alloc irq_desc for 26 on node -1
[    1.398899]   alloc kstat_irqs on node -1
[    1.398909] pcieport-driver 0000:00:1c.1: irq 26 for MSI/MSI-X
[    1.398921] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.399089]   alloc irq_desc for 27 on node -1
[    1.399091]   alloc kstat_irqs on node -1
[    1.399101] pcieport-driver 0000:00:1c.3: irq 27 for MSI/MSI-X
[    1.399113] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.399231] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.399317] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    1.399323] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7013450), AE_NOT_FOUND
[    1.399420] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    1.399426] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7013450), AE_NOT_FOUND
[    1.399512] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    1.399518] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7013450), AE_NOT_FOUND
[    1.399601] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    1.399607] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7013450), AE_NOT_FOUND
[    1.399710] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    1.399716] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7013450), AE_NOT_FOUND
[    1.399800] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    1.399806] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7013450), AE_NOT_FOUND
[    1.399889] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    1.399896] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7013450), AE_NOT_FOUND
[    1.399979] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    1.399985] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7013450), AE_NOT_FOUND
[    1.400034] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.452095] ACPI: AC Adapter [ACAD] (on-line)
[    1.452176] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.452180] ACPI: Power Button [PWRF]
[    1.452239] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.452331] ACPI: Lid Switch [LID]
[    1.452378] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    1.452381] ACPI: Power Button [PWRB]
[    1.453108] ACPI: SSDT bfed3d13 001F6 (v01  PmRef  Cpu0Ist 00003000 INTL 20061109)
[    1.453752] ACPI: SSDT bfed3697 005F7 (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    1.456234] Monitor-Mwait will be used to enter C-1 state
[    1.456258] Monitor-Mwait will be used to enter C-2 state
[    1.456280] Monitor-Mwait will be used to enter C-3 state
[    1.456289] Marking TSC unstable due to TSC halts in idle
[    1.456310] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.456338] processor LNXCPU:00: registered as cooling_device0
[    1.456342] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.456724] ACPI: SSDT bfed3f09 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20061109)
[    1.457175] ACPI: SSDT bfed3c8e 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20061109)
[    1.458282] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.458304] processor LNXCPU:01: registered as cooling_device1
[    1.458308] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.684070] thermal LNXTHERM:01: registered as thermal_zone0
[    1.684080] ACPI: Thermal Zone [THRM] (38 C)
[    1.684143] isapnp: Scanning for PnP cards...
[    1.696082] ACPI: Battery Slot [BAT1] (battery absent)
[    2.038385] isapnp: No Plug & Play device found
[    2.039640] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    2.041052] brd: module loaded
[    2.041545] loop: module loaded
[    2.041615] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    2.041693] ahci 0000:00:1f.2: version 3.0
[    2.041707] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.041742]   alloc irq_desc for 28 on node -1
[    2.041745]   alloc kstat_irqs on node -1
[    2.041756] ahci 0000:00:1f.2: irq 28 for MSI/MSI-X
[    2.041826] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    2.041829] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[    2.041835] ahci 0000:00:1f.2: setting latency timer to 64
[    2.042070] scsi0 : ahci
[    2.042166] scsi1 : ahci
[    2.042230] scsi2 : ahci
[    2.042344] ata1: SATA max UDMA/133 abar m2048@0xf0604000 port 0xf0604100 irq 28
[    2.042348] ata2: SATA max UDMA/133 abar m2048@0xf0604000 port 0xf0604180 irq 28
[    2.042352] ata3: SATA max UDMA/133 abar m2048@0xf0604000 port 0xf0604200 irq 28
[    2.042406] ata_piix 0000:00:1f.1: version 2.13
[    2.042416] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.042453] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.042530] scsi3 : ata_piix
[    2.042592] scsi4 : ata_piix
[    2.043256] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x18a0 irq 14
[    2.043259] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18a8 irq 15
[    2.043463] ata5: port disabled. ignoring.
[    2.044252] Fixed MDIO Bus: probed
[    2.044288] PPP generic driver version 2.4.2
[    2.044381] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.044399]   alloc irq_desc for 18 on node -1
[    2.044401]   alloc kstat_irqs on node -1
[    2.044407] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.044419] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.044423] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.044454] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    2.048358] ehci_hcd 0000:00:1a.7: debug port 1
[    2.048366] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.048380] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf0604800
[    2.060020] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    2.060092] usb usb1: configuration #1 chosen from 1 choice
[    2.060124] hub 1-0:1.0: USB hub found
[    2.060132] hub 1-0:1.0: 4 ports detected
[    2.060191]   alloc irq_desc for 23 on node -1
[    2.060194]   alloc kstat_irqs on node -1
[    2.060198] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.060208] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.060212] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.060248] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    2.064166] ehci_hcd 0000:00:1d.7: debug port 1
[    2.064174] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.064187] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf0604c00
[    2.076020] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.076083] usb usb2: configuration #1 chosen from 1 choice
[    2.076113] hub 2-0:1.0: USB hub found
[    2.076120] hub 2-0:1.0: 6 ports detected
[    2.076187] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.076205] uhci_hcd: USB Universal Host Controller Interface driver
[    2.076229] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.076236] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.076240] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.076269] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    2.076307] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    2.076394] usb usb3: configuration #1 chosen from 1 choice
[    2.076421] hub 3-0:1.0: USB hub found
[    2.076429] hub 3-0:1.0: 2 ports detected
[    2.076476]   alloc irq_desc for 21 on node -1
[    2.076479]   alloc kstat_irqs on node -1
[    2.076483] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.076490] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.076494] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.076523] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    2.076561] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[    2.076643] usb usb4: configuration #1 chosen from 1 choice
[    2.076670] hub 4-0:1.0: USB hub found
[    2.076677] hub 4-0:1.0: 2 ports detected
[    2.076726] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.076733] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.076737] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.076766] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    2.076795] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001840
[    2.076877] usb usb5: configuration #1 chosen from 1 choice
[    2.076905] hub 5-0:1.0: USB hub found
[    2.076911] hub 5-0:1.0: 2 ports detected
[    2.076960] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.076969] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.076973] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.077018] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    2.077056] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001860
[    2.077137] usb usb6: configuration #1 chosen from 1 choice
[    2.077164] hub 6-0:1.0: USB hub found
[    2.077171] hub 6-0:1.0: 2 ports detected
[    2.077221] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.077228] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.077232] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.077269] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    2.077298] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001880
[    2.077381] usb usb7: configuration #1 chosen from 1 choice
[    2.077408] hub 7-0:1.0: USB hub found
[    2.077415] hub 7-0:1.0: 2 ports detected
[    2.077519] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.079911] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.090047] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.090053] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.090056] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.090059] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.090062] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.090124] mice: PS/2 mouse device common for all mice
[    2.090251] rtc_cmos 00:06: RTC can wake from S4
[    2.090283] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.090316] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    2.090419] device-mapper: uevent: version 1.0.3
[    2.090511] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    2.090605] device-mapper: multipath: version 1.1.0 loaded
[    2.090608] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.090734] EISA: Probing bus 0 at eisa.0
[    2.090740] Cannot allocate resource for EISA slot 1
[    2.090743] Cannot allocate resource for EISA slot 2
[    2.090745] Cannot allocate resource for EISA slot 3
[    2.090769] EISA: Detected 0 cards.
[    2.090950] cpuidle: using governor ladder
[    2.091082] cpuidle: using governor menu
[    2.091613] TCP cubic registered
[    2.091778] NET: Registered protocol family 10
[    2.092275] lo: Disabled Privacy Extensions
[    2.092648] NET: Registered protocol family 17
[    2.092666] Bluetooth: L2CAP ver 2.13
[    2.092668] Bluetooth: L2CAP socket layer initialized
[    2.092671] Bluetooth: SCO (Voice Link) ver 0.6
[    2.092672] Bluetooth: SCO socket layer initialized
[    2.092714] Bluetooth: RFCOMM TTY layer initialized
[    2.092717] Bluetooth: RFCOMM socket layer initialized
[    2.092719] Bluetooth: RFCOMM ver 1.11
[    2.093325] Using IPI No-Shortcut mode
[    2.093390] PM: Resume from disk failed.
[    2.093407] registered taskstats version 1
[    2.093537]   Magic number: 10:190:930
[    2.093627] rtc_cmos 00:06: setting system clock to 2010-05-18 09:56:11 UTC (1274176571)
[    2.093630] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.093632] EDD information not available.
[    2.120534] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.204450] ata4.00: ATAPI: HL-DT-ST DVDRAM GSA-T40N, JT03, max UDMA/33
[    2.220366] ata4.00: configured for UDMA/33
[    2.360123] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.360153] ata3: SATA link down (SStatus 0 SControl 300)
[    2.360180] ata2: SATA link down (SStatus 0 SControl 300)
[    2.361176] ACPI Warning: \_SB_.PCI0.SATA.PRT0._GTF: Return type mismatch - found Integer, expected Buffer 20090521 nspredef-940
[    2.361184] ata1.00: _GTF unexpected object type 0x1
[    2.361378] ata1.00: ATA-8: Hitachi HTS542525K9SA00, BBFOC33P, max UDMA/133
[    2.361385] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.362676] ata1.00: _GTF unexpected object type 0x1
[    2.362902] ata1.00: configured for UDMA/133
[    2.376305] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54252 BBFO PQ: 0 ANSI: 5
[    2.376432] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.376472] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.376520] sd 0:0:0:0: [sda] Write Protect is off
[    2.376523] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.376548] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.376679]  sda:
[    2.380381] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T40N  JT03 PQ: 0 ANSI: 5
[    2.388072] usb 2-2: new high speed USB device using ehci_hcd and address 2
[    2.391718] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.391724] Uniform CD-ROM driver Revision: 3.20
[    2.391868] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    2.391926] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    2.400676]  sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
[    2.454857] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.454887] Freeing unused kernel memory: 540k freed
[    2.455258] Write protecting the kernel text: 4580k
[    2.455320] Write protecting the kernel read-only data: 1840k
[    2.500016] Clocksource tsc unstable (delta = -251981592 ns)
[    2.522956] usb 2-2: configuration #1 chosen from 1 choice
[    2.523274] hub 2-2:1.0: USB hub found
[    2.523618] hub 2-2:1.0: 4 ports detected
[    2.582025] Linux agpgart interface v0.103
[    2.610146] sky2 driver version 1.23
[    2.610196] sky2 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.610212] sky2 0000:03:00.0: setting latency timer to 64
[    2.610244] sky2 0000:03:00.0: Yukon-2 FE+ chip revision 0
[    2.610354]   alloc irq_desc for 29 on node -1
[    2.610356]   alloc kstat_irqs on node -1
[    2.610375] sky2 0000:03:00.0: irq 29 for MSI/MSI-X
[    2.611326] sky2 eth0: addr 00:1e:68:83:04:a3
[    2.638126] usb 2-3: new high speed USB device using ehci_hcd and address 3
[    2.689513] ohci1394 0000:0a:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.745074] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[f0501000-f05017ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    2.781880] usb 2-3: configuration #1 chosen from 1 choice
[    2.856395] usb 2-2.1: new high speed USB device using ehci_hcd and address 4
[    2.889213] acpi device:04: registered as cooling_device2
[    2.889393] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/device:03/input/input5
[    2.889435] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    2.949515] usb 2-2.1: configuration #1 chosen from 1 choice
[    2.957356] Initializing USB Mass Storage driver...
[    2.957488] scsi5 : SCSI emulation for USB Mass Storage devices
[    2.957580] usbcore: registered new interface driver usb-storage
[    2.957583] USB Mass Storage support registered.
[    2.957663] usb-storage: device found at 4
[    2.957665] usb-storage: waiting for device to settle before scanning
[    3.020403] usb 2-2.3: new low speed USB device using ehci_hcd and address 5
[    3.131879] usb 2-2.3: configuration #1 chosen from 1 choice
[    3.138959] usbcore: registered new interface driver hiddev
[    3.146358] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2.3/2-2.3:1.0/input/input6
[    3.146442] generic-usb 0003:045E:00DD.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:1d.7-2.3/input0
[    3.158871] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2.3/2-2.3:1.1/input/input7
[    3.158948] generic-usb 0003:045E:00DD.0002: input,hidraw1: USB HID v1.11 Device [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:1d.7-2.3/input1
[    3.158965] usbcore: registered new interface driver usbhid
[    3.158968] usbhid: v2.6:USB HID core driver
[    3.209406] usb 2-2.4: new low speed USB device using ehci_hcd and address 6
[    3.319829] usb 2-2.4: configuration #1 chosen from 1 choice
[    3.323852] input: Microsoft Basic Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2.4/2-2.4:1.0/input/input8
[    3.323931] generic-usb 0003:045E:0084.0003: input,hidraw2: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:1d.7-2.4/input0
[    3.879694] PM: Starting manual resume from disk
[    3.879699] PM: Resume from partition 8:7
[    3.879701] PM: Checking hibernation image.
[    3.879864] PM: Resume from disk failed.
[    3.903347] EXT4-fs (sda5): barriers enabled
[    3.923763] kjournald2 starting: pid 418, dev sda5:8, commit interval 5 seconds
[    3.923910] EXT4-fs (sda5): delayed allocation enabled
[    3.923914] EXT4-fs: file extents enabled
[    3.925882] EXT4-fs: mballoc enabled
[    3.925897] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    4.024496] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001b240001084abd]
[    4.531901] type=1505 audit(1274176573.934:2): operation="profile_load" pid=443 name=/usr/share/gdm/guest-session/Xsession
[    4.534948] type=1505 audit(1274176573.938:3): operation="profile_load" pid=447 name=/sbin/dhclient3
[    4.535837] type=1505 audit(1274176573.938:4): operation="profile_load" pid=447 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.536284] type=1505 audit(1274176573.942:5): operation="profile_load" pid=447 name=/usr/lib/connman/scripts/dhclient-script
[    4.596835] type=1505 audit(1274176574.002:6): operation="profile_load" pid=451 name=/usr/bin/evince
[    4.609798] type=1505 audit(1274176574.015:7): operation="profile_load" pid=451 name=/usr/bin/evince-previewer
[    4.617961] type=1505 audit(1274176574.023:8): operation="profile_load" pid=451 name=/usr/bin/evince-thumbnailer
[    7.956501] usb-storage: device scan complete
[    7.957169] scsi 5:0:0:0: CD-ROM            TSSTcorp CDDVDW SE-S204N  TS01 PQ: 0 ANSI: 0
[    7.962796] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    7.962967] sr 5:0:0:0: Attached scsi CD-ROM sr1
[    7.963069] sr 5:0:0:0: Attached scsi generic sg2 type 5
[   19.184602] udev: starting version 147
[   19.215955] Adding 2192832k swap on /dev/sda7.  Priority:-1 extents:1 across:2192832k 
[   19.249146] lp: driver loaded but no devices found
[   19.253117] omnibook: Driver version 2.20090707-trunk.
[   19.253121] omnibook: Forced load with EC type 14.
[   19.253239] input: Omnibook ACPI scancode generator as /devices/virtual/input/input9
[   19.778534] EXT4-fs (sda5): internal journal on sda5:8
[   19.812078] usb 7-2: new full speed USB device using uhci_hcd and address 2
[   19.880288] omnibook: Enabled features: bluetooth dmi version.
[   19.978434] usb 7-2: configuration #1 chosen from 1 choice
[   19.985224] Bluetooth: Generic Bluetooth USB driver ver 0.5
[   19.985340] usbcore: registered new interface driver btusb
[   20.415972] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   20.415976] Disabling lock debugging due to kernel taint
[   20.484383] [fglrx] Maximum main memory to use for locked dma buffers: 2877 MBytes.
[   20.484772] [fglrx]   vendor: 1002 device: 95c4 count: 1
[   20.485468] [fglrx] ioport: bar 4, base 0x2000, size: 0x100
[   20.485497] pci 0000:01:00.0: power state changed by ACPI to D0
[   20.485508] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.485514] pci 0000:01:00.0: setting latency timer to 64
[   20.485757] [fglrx] Kernel PAT support is enabled
[   20.485782] [fglrx] module loaded - fglrx 8.66.10 [Sep  3 2009] with 1 minors
[   20.573944] ip_tables: (C) 2000-2006 Netfilter Core Team
[   20.577286] sdhci: Secure Digital Host Controller Interface driver
[   20.577289] sdhci: Copyright(c) Pierre Ossman
[   20.578669] sdhci-pci 0000:0a:01.2: SDHCI controller found [1217:7120] (rev 2)
[   20.578690] sdhci-pci 0000:0a:01.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.578712] mmc0: Unknown controller version (2). You may experience problems.
[   20.578753] Registered led device: mmc0::
[   20.578791] mmc0: SDHCI controller on PCI [0000:0a:01.2] using DMA
[   20.634815] Linux video capture interface: v2.00
[   20.638027] uvcvideo: Found UVC 1.00 device Chicony USB 2.0 Camera (04f2:b008)
[   20.641355] input: Chicony USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.0/input/input10
[   20.641417] usbcore: registered new interface driver uvcvideo
[   20.641420] USB Video Class driver (v0.1.0)
[   20.679284]   alloc irq_desc for 22 on node -1
[   20.679288]   alloc kstat_irqs on node -1
[   20.679295] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   20.679336] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   20.702827] cfg80211: Calling CRDA to update world regulatory domain
[   20.759381] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   20.759460] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   20.759522] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   20.760026] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   20.760062] HDA Intel 0000:01:00.1: setting latency timer to 64
[   20.771062] cfg80211: World regulatory domain updated:
[   20.771065]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   20.771069]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.771072]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.771075]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.771078]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.771080]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.007203] Generic kernel compatibility enabled based on linux-next next-20100113
[   21.170917] iwlcore: disagrees about version of symbol ieee80211_start_tx_ba_cb_irqsafe
[   21.170921] iwlcore: Unknown symbol ieee80211_start_tx_ba_cb_irqsafe
[   21.171240] iwlcore: disagrees about version of symbol ieee80211_alloc_hw
[   21.171242] iwlcore: Unknown symbol ieee80211_alloc_hw
[   21.171339] iwlcore: disagrees about version of symbol ieee80211_register_hw
[   21.171342] iwlcore: Unknown symbol ieee80211_register_hw
[   21.171588] iwlcore: disagrees about version of symbol __ieee80211_get_radio_led_name
[   21.171591] iwlcore: Unknown symbol __ieee80211_get_radio_led_name
[   21.171678] iwlcore: disagrees about version of symbol ieee80211_wake_queue
[   21.171680] iwlcore: Unknown symbol ieee80211_wake_queue
[   21.171763] iwlcore: disagrees about version of symbol ieee80211_get_tkip_key
[   21.171766] iwlcore: Unknown symbol ieee80211_get_tkip_key
[   21.171850] iwlcore: disagrees about version of symbol __ieee80211_get_tx_led_name
[   21.171853] iwlcore: Unknown symbol __ieee80211_get_tx_led_name
[   21.171973] iwlcore: disagrees about version of symbol ieee80211_find_sta
[   21.171975] iwlcore: Unknown symbol ieee80211_find_sta
[   21.172083] iwlcore: disagrees about version of symbol ieee80211_tx_status_irqsafe
[   21.172085] iwlcore: Unknown symbol ieee80211_tx_status_irqsafe
[   21.172260] iwlcore: disagrees about version of symbol __ieee80211_get_rx_led_name
[   21.172262] iwlcore: Unknown symbol __ieee80211_get_rx_led_name
[   21.172359] iwlcore: disagrees about version of symbol ieee80211_stop_tx_ba_cb_irqsafe
[   21.172362] iwlcore: Unknown symbol ieee80211_stop_tx_ba_cb_irqsafe
[   21.172613] iwlcore: disagrees about version of symbol ieee80211_stop_queue
[   21.172615] iwlcore: Unknown symbol ieee80211_stop_queue
[   21.172703] iwlcore: disagrees about version of symbol __ieee80211_get_assoc_led_name
[   21.172705] iwlcore: Unknown symbol __ieee80211_get_assoc_led_name
[   21.172795] iwlcore: disagrees about version of symbol ieee80211_scan_completed
[   21.172798] iwlcore: Unknown symbol ieee80211_scan_completed
[   21.173214] iwlcore: Unknown symbol ieee80211_beacon_get
[   21.173540] iwlcore: disagrees about version of symbol ieee80211_rx_irqsafe
[   21.173542] iwlcore: Unknown symbol ieee80211_rx_irqsafe
[   21.286109] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1e0b1, caps: 0xd04711/0xa00000
[   21.286122] synaptics: Toshiba Satellite A300 detected, limiting rate to 40pps.
[   21.321645] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input14
[   22.371941] EXT4-fs (sda6): barriers enabled
[   22.375569] kjournald2 starting: pid 890, dev sda6:8, commit interval 5 seconds
[   22.375917] EXT4-fs (sda6): internal journal on sda6:8
[   22.375924] EXT4-fs (sda6): delayed allocation enabled
[   22.375930] EXT4-fs: file extents enabled
[   22.377801] EXT4-fs: mballoc enabled
[   22.377817] EXT4-fs (sda6): mounted filesystem with ordered data mode
[   22.543424] __ratelimit: 15 callbacks suppressed
[   22.543427] type=1505 audit(1274165791.946:14): operation="profile_replace" pid=1045 name=/usr/share/gdm/guest-session/Xsession
[   22.570422] type=1505 audit(1274165791.974:15): operation="profile_replace" pid=1046 name=/sbin/dhclient3
[   22.571223] type=1505 audit(1274165791.974:16): operation="profile_replace" pid=1046 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   22.571657] type=1505 audit(1274165791.974:17): operation="profile_replace" pid=1046 name=/usr/lib/connman/scripts/dhclient-script
[   22.572150] sky2 eth0: enabling interface
[   22.572359] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.599734] type=1505 audit(1274165792.002:18): operation="profile_replace" pid=1052 name=/usr/bin/evince
[   22.614110] type=1505 audit(1274165792.018:19): operation="profile_replace" pid=1052 name=/usr/bin/evince-previewer
[   22.624848] type=1505 audit(1274165792.030:20): operation="profile_replace" pid=1052 name=/usr/bin/evince-thumbnailer
[   22.636088] type=1505 audit(1274165792.042:21): operation="profile_replace" pid=1069 name=/usr/bin/freshclam
[   22.640087] type=1505 audit(1274165792.046:22): operation="profile_replace" pid=1071 name=/usr/lib/cups/backend/cups-pdf
[   22.641037] type=1505 audit(1274165792.046:23): operation="profile_replace" pid=1071 name=/usr/sbin/cupsd
[   22.781417] slamr: SmartLink AMRMO modem.
[   23.696319]   alloc irq_desc for 30 on node -1
[   23.696323]   alloc kstat_irqs on node -1
[   23.696337] fglrx_pci 0000:01:00.0: irq 30 for MSI/MSI-X
[   23.697057] [fglrx] Firegl kernel thread PID: 1471
[   23.807834] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.807838] Bluetooth: BNEP filters: protocol multicast
[   23.822895] Bridge firewalling registered
[   23.895926] ppdev: user-space parallel port driver
[   24.140220] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   24.143299] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   24.374011] [fglrx] Gart USWC size:943 M.
[   24.374016] [fglrx] Gart cacheable size:373 M.
[   24.374022] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   24.374025] [fglrx] Reserved FB block: Unshared offset:7d07000, size:2f5000 
[   24.374028] [fglrx] Reserved FB block: Unshared offset:7ffc000, size:4000 
[   28.120760] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   34.848036] eth0: no IPv6 routers present
[  836.261057] CE: hpet increasing min_delta_ns to 15000 nsec
[ 1753.180097] usb 5-1: new full speed USB device using uhci_hcd and address 2
[ 1753.612241] usb 5-1: configuration #1 chosen from 1 choice
[ 1753.646392] usblp0: Disabling reads from problematic bidirectional printer
[ 1753.658212] usblp0: USB Unidirectional printer dev 2 if 0 alt 1 proto 2 vid 0x03F0 pid 0x0604
[ 1753.658239] usbcore: registered new interface driver usblp
[ 1754.852412] usb 5-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
```

The command **cat /var/log/syslog | grep wlan** gave nothing too, so i printed the whole syslog file:

```
May 18 10:13:33 Acheron rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="916" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
May 18 10:14:09 Acheron anacron[1168]: Job `cron.daily' terminated
May 18 10:14:09 Acheron anacron[1168]: Normal exit (1 job run)
May 18 10:17:01 Acheron CRON[4939]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 18 10:25:21 Acheron kernel: [ 1753.180097] usb 5-1: new full speed USB device using uhci_hcd and address 2
May 18 10:25:22 Acheron kernel: [ 1753.612241] usb 5-1: configuration #1 chosen from 1 choice
May 18 10:25:22 Acheron udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0
May 18 10:25:22 Acheron udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb5/5-1
May 18 10:25:22 Acheron udev-configure-printer: Device vendor/product is 03F0:0604
May 18 10:25:22 Acheron kernel: [ 1753.646392] usblp0: Disabling reads from problematic bidirectional printer
May 18 10:25:22 Acheron kernel: [ 1753.658212] usblp0: USB Unidirectional printer dev 2 if 0 alt 1 proto 2 vid 0x03F0 pid 0x0604
May 18 10:25:22 Acheron kernel: [ 1753.658239] usbcore: registered new interface driver usblp
May 18 10:25:22 Acheron udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/usb/lp0
May 18 10:25:22 Acheron udev-configure-printer: failed to claim interface
May 18 10:25:22 Acheron udev-configure-printer: failed to claim interface
May 18 10:25:22 Acheron udev-configure-printer: invalid or missing IEEE 1284 Device ID
May 18 10:25:22 Acheron udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb5/5-1
May 18 10:25:22 Acheron udev-configure-printer: MFG:HEWLETT-PACKARD MDL:DESKJET 840C SERN:HU0292N111LW serial:HU0292N111LW
May 18 10:25:23 Acheron kernel: [ 1754.852412] usb 5-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
May 18 10:25:25 Acheron udev-configure-printer: SERN fields match
May 18 10:25:25 Acheron udev-configure-printer: URI match: usb://HP/DESKJET%20840C?serial=HU0292N111LW
May 18 10:25:25 Acheron udev-configure-printer: SERN fields match
May 18 10:25:25 Acheron udev-configure-printer: URI match: hp:/usb/DeskJet_840C?serial=HU0292N111LW
May 18 10:25:25 Acheron udev-configure-printer: Queue ipp://localhost:631/printers/DESKJET-840C has matching device URI
May 18 10:25:25 Acheron udev-configure-printer: Re-enabled printer ipp://localhost:631/printers/DESKJET-840C
May 18 10:25:25 Acheron udev-configure-printer: Queue ipp://localhost:631/printers/DeskJet_840C has matching device URI
May 18 10:25:25 Acheron udev-configure-printer: Re-enabled printer ipp://localhost:631/printers/DeskJet_840C
May 18 10:40:48 Acheron kernel: [ 2680.188108] CE: hpet increasing min_delta_ns to 22500 nsec
May 18 10:45:12 Acheron kernel: [ 2943.913129] CE: hpet increasing min_delta_ns to 33750 nsec
```

[SIZE="5"]moviemaniac[/SIZE], thanks a lot for your assistance.

---

### Post by moviemaniac on 2010-05-18
Well, you are using a rather outdated (-31) kernel which can cause (judging from dmesg) problems with the newer drivers. I strongly suggest using the -33 or just-released -34 branch of the Kernel ([http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)). As you're using the fglrx driver you will then either have to switch to the opensource-driver or use the latest official ATI driver from ati.amd.com

It also seems you're still on Karmic (judging from the kernel version) - I would strongly suggest upgrading to lucid for better hardware-support and better userspace-interaction with a -33 or -34 series kernel.

---

### Post by sujith_m82 on 2010-05-18
> **Reinach said:**
> 
[   20.771062] cfg80211: World regulatory domain updated:
[   20.771065]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   20.771069]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.771072]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.771075]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.771078]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.771080]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.007203] Generic kernel compatibility enabled based on linux-next next-20100113
[   21.170917] iwlcore: disagrees about version of symbol ieee80211_start_tx_ba_cb_irqsafe
[   21.170921] iwlcore: Unknown symbol ieee80211_start_tx_ba_cb_irqsafe
[   21.171240] iwlcore: disagrees about version of symbol ieee80211_alloc_hw
[   21.171242] iwlcore: Unknown symbol ieee80211_alloc_hw
[   21.171339] iwlcore: disagrees about version of symbol ieee80211_register_hw
[   21.171342] iwlcore: Unknown symbol ieee80211_register_hw
[   21.171588] iwlcore: disagrees about version of symbol __ieee80211_get_radio_led_name
[   21.171591] iwlcore: Unknown symbol __ieee80211_get_radio_led_name
[   21.171678] iwlcore: disagrees about version of symbol ieee80211_wake_queue
[   21.171680] iwlcore: Unknown symbol ieee80211_wake_queue
[   21.171763] iwlcore: disagrees about version of symbol ieee80211_get_tkip_key
[   21.171766] iwlcore: Unknown symbol ieee80211_get_tkip_key
[   21.171850] iwlcore: disagrees about version of symbol __ieee80211_get_tx_led_name
[   21.171853] iwlcore: Unknown symbol __ieee80211_get_tx_led_name
[   21.171973] iwlcore: disagrees about version of symbol ieee80211_find_sta
[   21.171975] iwlcore: Unknown symbol ieee80211_find_sta
[   21.172083] iwlcore: disagrees about version of symbol ieee80211_tx_status_irqsafe
[   21.172085] iwlcore: Unknown symbol ieee80211_tx_status_irqsafe
[   21.172260] iwlcore: disagrees about version of symbol __ieee80211_get_rx_led_name
[   21.172262] iwlcore: Unknown symbol __ieee80211_get_rx_led_name
[   21.172359] iwlcore: disagrees about version of symbol ieee80211_stop_tx_ba_cb_irqsafe
[   21.172362] iwlcore: Unknown symbol ieee80211_stop_tx_ba_cb_irqsafe
[   21.172613] iwlcore: disagrees about version of symbol ieee80211_stop_queue
[   21.172615] iwlcore: Unknown symbol ieee80211_stop_queue
[   21.172703] iwlcore: disagrees about version of symbol __ieee80211_get_assoc_led_name
[   21.172705] iwlcore: Unknown symbol __ieee80211_get_assoc_led_name
[   21.172795] iwlcore: disagrees about version of symbol ieee80211_scan_completed
[   21.172798] iwlcore: Unknown symbol ieee80211_scan_completed
[   21.173214] iwlcore: Unknown symbol ieee80211_beacon_get
[   21.173540] iwlcore: disagrees about version of symbol ieee80211_rx_irqsafe
[   21.173542] iwlcore: Unknown symbol ieee80211_rx_irqsafe


This is the problem.
You have selected ath9k_htc, but not iwlwifi when compiling compat-wireless, resulting in version mismatch.

Download the latest compat-wireless package from [http://wireless.kernel.org/en/users/Download]("http://wireless.kernel.org/en/users/Download") and just do 'make' followed by 'sudo make install'. That page also has detailed instructions. This will install all updated wireless drivers, which is a good thing anyway. :)

---

### Post by moviemaniac on 2010-05-18
> **sujith_m82 said:**
> This is the problem.
You have selected ath9k_htc, but not iwlwifi when compiling compat-wireless, resulting in version mismatch.

*facepalm* Overlooked the obvious - and here I was thinking it was a problem the drivers were having with the old(er) kernel... :)

---

### Post by Jackxn on 2010-05-18
Hi, i have the same Problem...
I too have Lucid and the TL-WN422G V2 wireless USB Stick.

I tried out both ways to install the driver/Firmware, but none of them works

Q: How do i see if the Device is installed correctly? Where does/should it show up?

I received no error messages during the installation process, but it still doesn't work

Lsusb shows the device as **Bus 001 Device 004: ID 0cf3:1006 Atheros Communications, Inc.**

---

### Post by moviemaniac on 2010-05-18
@Jackxn: Please post the output of dmesg

---

### Post by Reinach on 2010-05-18
> **sujith_m82 said:**
> This is the problem.
You have selected ath9k_htc, but not iwlwifi when compiling compat-wireless, resulting in version mismatch.

Download the latest compat-wireless package from [http://wireless.kernel.org/en/users/Download]("http://wireless.kernel.org/en/users/Download") and just do 'make' followed by 'sudo make install'. That page also has detailed instructions. This will install all updated wireless drivers, which is a good thing anyway. :)

So, instead of giving the command **./scripts/driver-select [COLOR="Red"]ath9k_htc[/COLOR]** what exactly should i have given?

Maybe **./scripts/driver-select [COLOR="#ff0000"]iwlwifi[/COLOR]**?? Is this the driver i need? And where do i know this from? From my above dmesg command?

---

### Post by Reinach on 2010-05-18
As i posted yesterday, my [COLOR="Black"]lsusb[/COLOR] command pertaining to the Wireless USB Adapter TP-LINK gives:

```
Bus 001 Device 002: ID 0cf3:[COLOR="Red"]9271[/COLOR] Atheros Communications, Inc.
```

So, my driver must be [COLOR="Red"]ar9271[/COLOR]. Am i right? So in the driver-select command i must type:

```
./scripts/driver-select [COLOR="#ff0000"]ar9271[/COLOR]
```

Is this correct? Can i proceed with this?

---

### Post by moviemaniac on 2010-05-18
sujith_m82 already explained it: Download the latest wireless-compat package from the site, extract it, open a terminal and cd into the extracted folder.
then type "make" followed by (when the computer's done) "sudo make install". After a reboot both your wifi cards should work.
There's NO NEED to select a specific driver as you're rebuilding ALL wireless drivers.

---

### Post by Reinach on 2010-05-18
As i just saw in the below link:

[http://wireless.kernel.org/en/users/Drivers/ath9k_htc]("http://wireless.kernel.org/en/users/Drivers/ath9k_htc")

the correct driver for the chipset ar9271 of my usb wireless card is indeed the ath9k_htc, i.e. the driver i have already installed...

So, what was the problem? Isn't this the correct driver?

---

### Post by Reinach on 2010-05-18
> There's NO NEED to select a specific driver as you're rebuilding ALL wireless drivers.

moviemaniac, thanks. But, this is exactly what i did in the first place i think. And it led to so many errors in the dmesg. Should i change something now?

---

### Post by moviemaniac on 2010-05-18
When you followed these instructions:

> Download this file to your desktop: [http://wireless.kernel.org/download/...ss-2.6.tar.bz2](http://wireless.kernel.org/download/...ss-2.6.tar.bz2)
Then open a terminal and enter these commands one after the other (you will be asked for your password on the last step):
cd Desktop
tar xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless-2.6
**./scripts/driver-select ath9k_htc**
make && sudo make install

the line in bold only build the driver for your USB card and NOT for the internal one. By repeating the instructions (delete the old folder first) but **leaving out the bold line** you'll also be building the driver needed for the internal intel card.

---

### Post by Reinach on 2010-05-18
OK, i think i got the gist of what you say. I deleted the old folder and uncompressed the tar file in my home folder. I moved into the new folder and gave the command [COLOR="Red"]make[/COLOR] first, but it returned errors:

```
./scripts/gen-compat-autoconf.sh config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/2.6.31-20-generic/build M=/home/trifonas/compat-wireless-2010-05-17 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  LD      /home/trifonas/compat-wireless-2010-05-17/compat/built-in.o
  CC [M]  /home/trifonas/compat-wireless-2010-05-17/compat/main.o
/home/trifonas/compat-wireless-2010-05-17/compat/main.c:8:2: error: #error "You need a COMPAT_VERSION"
/home/trifonas/compat-wireless-2010-05-17/compat/main.c:11: error: &#8216;COMPAT_VERSION&#8217; undeclared here (not in a function)
make[3]: *** [/home/trifonas/compat-wireless-2010-05-17/compat/main.o] Error 1
make[2]: *** [/home/trifonas/compat-wireless-2010-05-17/compat] Error 2
make[1]: *** [_module_/home/trifonas/compat-wireless-2010-05-17] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
make: *** [modules] Error 2

```

So i didn't proceed further. What do i do next?

---

### Post by sippick on 2010-05-18
Guys, I can not make this darn thing work for me. 

I am a very new user to ubuntu 10.4 LTS and can not make my broadcom wireless adapter (built in) to work, and I gave up on it. 

Bought TL-WN422G wireless USB adapter since i was assured by TP-Link that this device will work under Ubuntu. Right...

Maybe I am doing something wrong - i do not know, since my experience with Linux is very minor. 

I can give remote access to someone if needed to help me make this work. 

any advice would also be very appreciated. 

Please let me know what you would need for me and I will get it and post it here if needed. 


One can send me a PM if that is more convenient.

Thanks,

sippick

---

### Post by moviemaniac on 2010-05-18
This means that there is a general problem with the latest package, try this one instead: [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-05-06.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-05-06.tar.bz2)

---

### Post by sippick on 2010-05-18
when i follow these instructions 

> Download this file to your desktop: [http://wireless.kernel.org/download/...ss-2.6.tar.bz2](http://wireless.kernel.org/download/...ss-2.6.tar.bz2)
Then open a terminal and enter these commands one after the other (you will be asked for your password on the last step):
cd Desktop
tar xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless-2.6
./scripts/driver-select ath9k_htc
make && sudo make install 

using the 05-06 package everything runs and installs smoothly with no error, but the device is not being detected.

the only network device i have detected is eth0 which is my cable connection obviously

any ideas?
please?

---

### Post by moviemaniac on 2010-05-18
You didn't copy the firmware file:

Download this file to cour Desktop: [http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=blob_plain;f=ar9271.fw;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=blob_plain;f=ar9271.fw;hb=HEAD)

then open up a terminal and enter these commands one after the other (you will be asked for your password on the last step)

cd Desktop
sudo mv ar9271.fw /lib/firmware

reboot and everything should work

---

### Post by Reinach on 2010-05-18
Wowww!!! moviemaniac, thank you a lot! The installation went smoothly and after the reboot, i pluged-in the USB wireless card TP-Link WN722N. Now, the network manager detects all three types of connections:

1. wired connection (eth)
2. wireless networks with the built-in wireless card Intel PRO Wireless 3945 ABG
3. wireless networks with the usb wireless card Atheros


You were correct, i built the driver only for the external card, so i needed to repeat the procedure for the internal as well. 

And thank you again, an important problem for my ubuntu networking now has been removed. 

One more question: when i upgrade to the Lucid Lynx 10.04 i will need to repeat this procedure eh? (i guess until the time when the driver is finaly incorporated into the kernel of 10.10 maybe...)

---

### Post by sippick on 2010-05-18
Thanks moviemaniac for your help.

i wish it did work though... 

i may have done too many things and messed some things up. 
I will make a clean installation of ubuntu 10.4 LTS again and see if i can make it work from scratch. 

Could someone please make a step by step guideline on what needs to be installed and which commands and when should be used? This would be very helpful for everyone using this device. 

I am going to reinstall ubuntu right away, so I will be back on this thread in about 30 minutes or so. 

Any help with the step by step guide would be much appreciated! 

cheers, 

sippick

---

### Post by moviemaniac on 2010-05-18
> **Reinach said:**
> One more question: when i upgrade to the Lucid Lynx 10.04 i will need to repeat this procedure eh? (i guess until the time when the driver is finaly incorporated into the kernel of 10.10 maybe...)

I just checked, the required firmware is not being shipped with 10.04 as it came too late for lucid - I guess it's gonna be included with 10.10.

---

### Post by moviemaniac on 2010-05-18
@sippick: I already posted the info in this thread, but here's an updated version:

Download this file to cour Desktop: [http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=blob_plain;f=ar9271.fw;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=blob_plain;f=ar9271.fw;hb=HEAD)

then open up a terminal and enter these commands one after the other (you will be asked for your password on the last step)

cd Desktop
sudo mv ar9271.fw /lib/firmware

Now download this file to your desktop: [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-05-06.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-05-06.tar.bz2)
Then open a terminal and enter these commands one after the other (you will be asked for your password on the last step):
cd Desktop
tar xjvf compat-wireless-2010-05-06.tar.bz2
cd compat-wireless-2010-05-06
make && sudo make install

after that reboot.

---

### Post by sippick on 2010-05-18
@moviemaniac

hope it does not sound too gay if I say "I love you man!!!"

I must have had something set up incorrectly while I was trying to get my internal broadcom to work yesterday night. 

reinstalled ubuntu and followed your instructions you left here and BAM! green light on my USB dongle! 

You rock!

Keep up the good work!

Cheers and Joy, 

sippick

---

### Post by moviemaniac on 2010-05-18
I'm glad to have been of help :)

---

### Post by Jackxn on 2010-05-19
@ Moviemaniac:

jackxn@jackxn-Kellerbar:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-22-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 (Ubuntu 2.6.32-22.33-generic 2.6.32.11+drm33.2)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001fff8000 - 0000000020000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x1fff0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 base 0E0000000 mask FF8000000 write-combining
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  modified: 000000001fff0000 - 000000001fff8000 (ACPI data)
[    0.000000]  modified: 000000001fff8000 - 0000000020000000 (ACPI NVS)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-000000001fff0000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 001fc00000 page 2M
[    0.000000]  001fc00000 - 001fff0000 page 4k
[    0.000000] kernel direct mapping tables up to 1fff0000 @ 10000-15000
[    0.000000] RAMDISK: 17899000 - 18033974
[    0.000000] ACPI: RSDP 000fa940 00014 (v00 AMI   )
[    0.000000] ACPI: RSDT 1fff0000 0002C (v01 AMIINT VIA_K7   00000010 MSFT 00000097)
[    0.000000] ACPI: FACP 1fff0030 00081 (v01 AMIINT VIA_K7   00000011 MSFT 00000097)
[    0.000000] ACPI: DSDT 1fff0120 032BF (v01    VIA   VIA_K7 00001000 MSFT 0100000D)
[    0.000000] ACPI: FACS 1fff8000 00040
[    0.000000] ACPI: APIC 1fff00c0 00054 (v01 AMIINT VIA_K7   00000009 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1fff0000
[    0.000000]   low ram: 0 - 1fff0000
[    0.000000]   node 0 low ram: 00000000 - 1fff0000
[    0.000000]   node 0 bootmap 00011000 - 00015000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001fff0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008d9e98]    TEXT DATA BSS ==> [0000100000 - 00008d9e98]
[    0.000000]   #4 [0017899000 - 0018033974]          RAMDISK ==> [0017899000 - 0018033974]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008da000 - 00008dd108]              BRK ==> [00008da000 - 00008dd108]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000015000]          BOOTMAP ==> [0000011000 - 0000015000]
[    0.000000] found SMP MP-table at [c00fb930] fb930
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001fff0
[    0.000000]   HighMem  0x0001fff0 -> 0x0001fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001fff0
[    0.000000] On node 0 totalpages: 130943
[    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c1001200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 992 pages used for memmap
[    0.000000]   Normal zone: 125968 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:dec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36024 r0 d21320 u4194304
[    0.000000] pcpu-alloc: s36024 r0 d21320 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129919
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=633eed08-4f72-4136-9861-e011a09f5e25 ro quiet splash
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2620800 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 500400k/524224k available (4673k kernel code, 22992k reserved, 2121k data, 656k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xe07f0000 - 0xff7fe000   ( 496 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
[    0.000000]       .data : 0xc0590653 - 0xc07a2e48   (2121 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590653   (4673 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1503.632 MHz processor.
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 3007.26 BogoMIPS (lpj=6014528)
[    0.004036] Security Framework initialized
[    0.004078] AppArmor: AppArmor initialized
[    0.004091] Mount-cache hash table entries: 512
[    0.004285] Initializing cgroup subsys ns
[    0.004292] Initializing cgroup subsys cpuacct
[    0.004298] Initializing cgroup subsys memory
[    0.004313] Initializing cgroup subsys devices
[    0.004317] Initializing cgroup subsys freezer
[    0.004321] Initializing cgroup subsys net_cls
[    0.004347] CPU: CLK_CTL MSR was 6003d22f. Reprogramming to 2003d22f
[    0.004353] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004358] CPU: L2 Cache: 256K (64 bytes/line)
[    0.004364] mce: CPU supports 4 MCE banks
[    0.004389] Performance Events: AMD PMU driver.
[    0.004407] ... version:                0
[    0.004410] ... bit width:              48
[    0.004413] ... generic registers:      4
[    0.004416] ... value mask:             0000ffffffffffff
[    0.004419] ... max period:             00007fffffffffff
[    0.004422] ... fixed-purpose events:   0
[    0.004425] ... event mask:             000000000000000f
[    0.004431] Checking 'hlt' instruction... OK.
[    0.020687] SMP alternatives: switching to UP code
[    0.028926] Freeing SMP alternatives: 19k freed
[    0.028966] ACPI: Core revision 20090903
[    0.036558] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.036570] ftrace: allocating 21771 entries in 43 pages
[    0.040165] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.041202] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.081555] CPU0: AMD Athlon(tm) XP 1800+ stepping 01
[    0.084001] Brought up 1 CPUs
[    0.084001] Total of 1 processors activated (3007.26 BogoMIPS).
[    0.084001] CPU0 attaching NULL sched-domain.
[    0.084001] devtmpfs: initialized
[    0.084001] regulator: core version 0.5
[    0.084001] Time: 18:48:47  Date: 05/19/10
[    0.084001] NET: Registered protocol family 16
[    0.084001] EISA bus registered
[    0.084001] ACPI: bus type pci registered
[    0.085866] PCI: PCI BIOS revision 2.10 entry at 0xfdaf1, last bus=1
[    0.085870] PCI: Using configuration type 1 for base access
[    0.087326] bio: create slab <bio-0> at 0
[    0.088055] ACPI: EC: Look up EC in DSDT
[    0.095017] ACPI: Interpreter enabled
[    0.095024] ACPI: (supports S0 S1 S4 S5)
[    0.095054] ACPI: Using IOAPIC for interrupt routing
[    0.099011] ACPI: Power Resource [URP1] (off)
[    0.099054] ACPI: Power Resource [URP2] (off)
[    0.099095] ACPI: Power Resource [FDDP] (off)
[    0.099135] ACPI: Power Resource [LPTP] (off)
[    0.099299] ACPI: No dock devices found.
[    0.099477] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.099545] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xe0000000-0xe7ffffff]
[    0.099637] pci 0000:00:01.0: supports D1
[    0.099700] pci 0000:00:10.0: reg 20 io port: [0xe400-0xe41f]
[    0.099725] pci 0000:00:10.0: supports D1 D2
[    0.099728] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.099734] pci 0000:00:10.0: PME# disabled
[    0.099782] pci 0000:00:10.1: reg 20 io port: [0xe800-0xe81f]
[    0.099807] pci 0000:00:10.1: supports D1 D2
[    0.099810] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.099815] pci 0000:00:10.1: PME# disabled
[    0.099862] pci 0000:00:10.2: reg 20 io port: [0xec00-0xec1f]
[    0.099887] pci 0000:00:10.2: supports D1 D2
[    0.099890] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.099895] pci 0000:00:10.2: PME# disabled
[    0.099928] pci 0000:00:10.3: reg 10 32bit mmio: [0xdfffff00-0xdfffffff]
[    0.099968] pci 0000:00:10.3: supports D1 D2
[    0.099971] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.099976] pci 0000:00:10.3: PME# disabled
[    0.100050] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.100060] pci 0000:00:11.0: quirk: region 0800-087f claimed by vt8235 PM
[    0.100066] pci 0000:00:11.0: quirk: region 0400-040f claimed by vt8235 SMB
[    0.100129] pci 0000:00:11.1: reg 20 io port: [0xfc00-0xfc0f]
[    0.100191] pci 0000:00:11.5: reg 10 io port: [0xe000-0xe0ff]
[    0.100234] pci 0000:00:11.5: supports D1 D2
[    0.100269] pci 0000:00:12.0: reg 10 io port: [0xdc00-0xdcff]
[    0.100277] pci 0000:00:12.0: reg 14 32bit mmio: [0xdffffe00-0xdffffeff]
[    0.100314] pci 0000:00:12.0: supports D1 D2
[    0.100318] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.100323] pci 0000:00:12.0: PME# disabled
[    0.100377] pci 0000:01:00.0: reg 10 32bit mmio: [0xde000000-0xdeffffff]
[    0.100384] pci 0000:01:00.0: reg 14 32bit mmio pref: [0xd0000000-0xd7ffffff]
[    0.100392] pci 0000:01:00.0: reg 18 32bit mmio pref: [0xddc80000-0xddcfffff]
[    0.100408] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xdfee0000-0xdfefffff]
[    0.100460] pci 0000:00:01.0: bridge 32bit mmio: [0xdde00000-0xdfefffff]
[    0.100466] pci 0000:00:01.0: bridge 32bit mmio pref: [0xcdc00000-0xddcfffff]
[    0.100475] pci_bus 0000:00: on NUMA node 0
[    0.100482] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.102797] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.102933] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.103066] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 *12 14 15)
[    0.103196] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.103362] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.103367] vgaarb: loaded
[    0.103574] SCSI subsystem initialized
[    0.103716] libata version 3.00 loaded.
[    0.103849] usbcore: registered new interface driver usbfs
[    0.103869] usbcore: registered new interface driver hub
[    0.103916] usbcore: registered new device driver usb
[    0.104135] ACPI: WMI: Mapper loaded
[    0.104138] PCI: Using ACPI for IRQ routing
[    0.104334] NetLabel: Initializing
[    0.104337] NetLabel:  domain hash size = 128
[    0.104340] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.104362] NetLabel:  unlabeled traffic allowed by default
[    0.104419] Switching to clocksource tsc
[    0.107804] AppArmor: AppArmor Filesystem Enabled
[    0.107841] pnp: PnP ACPI init
[    0.107874] ACPI: bus type pnp registered
[    0.109593] pnp: PnP ACPI: found 8 devices
[    0.109597] ACPI: ACPI bus type pnp unregistered
[    0.109603] PnPBIOS: Disabled by ACPI PNP
[    0.109624] system 00:01: ioport range 0x290-0x297 has been reserved
[    0.109629] system 00:01: ioport range 0x3f0-0x3f1 has been reserved
[    0.109634] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.109639] system 00:01: ioport range 0x400-0x40f has been reserved
[    0.109643] system 00:01: ioport range 0x800-0x87f has been reserved
[    0.109650] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.144458] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.144462] pci 0000:00:01.0:   IO window: disabled
[    0.144470] pci 0000:00:01.0:   MEM window: 0xdde00000-0xdfefffff
[    0.144476] pci 0000:00:01.0:   PREFETCH window: 0xcdc00000-0xddcfffff
[    0.144495] pci 0000:00:01.0: setting latency timer to 64
[    0.144503] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.144507] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.144512] pci_bus 0000:01: resource 1 mem: [0xdde00000-0xdfefffff]
[    0.144516] pci_bus 0000:01: resource 2 pref mem [0xcdc00000-0xddcfffff]
[    0.144576] NET: Registered protocol family 2
[    0.144713] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.145132] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.145355] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.145582] TCP: Hash tables configured (established 16384 bind 16384)
[    0.145586] TCP reno registered
[    0.145712] NET: Registered protocol family 1
[    0.145737] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.145834] pci 0000:01:00.0: Boot video device
[    0.146152] cpufreq-nforce2: No nForce2 chipset.
[    0.146204] Scanning for low memory corruption every 60 seconds
[    0.146371] audit: initializing netlink socket (disabled)
[    0.146389] type=2000 audit(1274294927.143:1): initialized
[    0.159432] Trying to unpack rootfs image as initramfs...
[    0.175736] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.178247] VFS: Disk quotas dquot_6.5.2
[    0.178347] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.183989] fuse init (API version 7.13)
[    0.184197] msgmni has been set to 978
[    0.184597] alg: No test for stdrng (krng)
[    0.184648] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.184653] io scheduler noop registered
[    0.184656] io scheduler anticipatory registered
[    0.184659] io scheduler deadline registered
[    0.184726] io scheduler cfq registered (default)
[    0.184878] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.184914] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.185058] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.185066] ACPI: Power Button [PWRB]
[    0.185154] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.185164] ACPI: Sleep Button [SLPB]
[    0.185236] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.185241] ACPI: Power Button [PWRF]
[    0.185484] processor LNXCPU:00: registered as cooling_device0
[    0.191803] isapnp: Scanning for PnP cards...
[    0.197711] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.203886] brd: module loaded
[    0.204674] loop: module loaded
[    0.204867] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.205122] pata_acpi 0000:00:11.1: can't derive routing for PCI INT A
[    0.205216] pata_acpi 0000:00:11.1: can't derive routing for PCI INT A
[    0.205688] Fixed MDIO Bus: probed
[    0.205742] PPP generic driver version 2.4.2
[    0.205805] tun: Universal TUN/TAP device driver, 1.6
[    0.205808] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.205936] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.205964]   alloc irq_desc for 21 on node -1
[    0.205968]   alloc kstat_irqs on node -1
[    0.205981] ehci_hcd 0000:00:10.3: PCI INT D -> GSI 21 (level, low) -> IRQ 21
[    0.206005] ehci_hcd 0000:00:10.3: EHCI Host Controller
[    0.206073] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 1
[    0.206161] ehci_hcd 0000:00:10.3: irq 21, io mem 0xdfffff00
[    0.249744] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00
[    0.249887] usb usb1: configuration #1 chosen from 1 choice
[    0.249933] hub 1-0:1.0: USB hub found
[    0.249950] hub 1-0:1.0: 6 ports detected
[    0.250035] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.250055] uhci_hcd: USB Universal Host Controller Interface driver
[    0.250125] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.250135] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.250190] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.250215] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000e400
[    0.250364] usb usb2: configuration #1 chosen from 1 choice
[    0.250404] hub 2-0:1.0: USB hub found
[    0.250417] hub 2-0:1.0: 2 ports detected
[    0.250484] uhci_hcd 0000:00:10.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.250492] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.250547] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.250570] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000e800
[    0.250712] usb usb3: configuration #1 chosen from 1 choice
[    0.250758] hub 3-0:1.0: USB hub found
[    0.250772] hub 3-0:1.0: 2 ports detected
[    0.250830] uhci_hcd 0000:00:10.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    0.250838] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.250899] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.250922] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000ec00
[    0.251072] usb usb4: configuration #1 chosen from 1 choice
[    0.251118] hub 4-0:1.0: USB hub found
[    0.251131] hub 4-0:1.0: 2 ports detected
[    0.251243] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.251247] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.251415] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.256116] mice: PS/2 mouse device common for all mice
[    0.256346] rtc_cmos 00:03: RTC can wake from S4
[    0.256426] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.256489] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    0.256633] device-mapper: uevent: version 1.0.3
[    0.256822] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.259612] device-mapper: multipath: version 1.1.0 loaded
[    0.259620] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.259930] EISA: Probing bus 0 at eisa.0
[    0.259973] EISA: Detected 0 cards.
[    0.261929] cpuidle: using governor ladder
[    0.261935] cpuidle: using governor menu
[    0.262644] TCP cubic registered
[    0.262896] NET: Registered protocol family 10
[    0.263587] lo: Disabled Privacy Extensions
[    0.264035] NET: Registered protocol family 17
[    0.264103] powernow-k8: Processor cpuid 681 not supported
[    0.264139] Using IPI No-Shortcut mode
[    0.264315] PM: Resume from disk failed.
[    0.264338] registered taskstats version 1
[    0.264590]   Magic number: 10:119:848
[    0.264724] rtc_cmos 00:03: setting system clock to 2010-05-19 18:48:48 UTC (1274294928)
[    0.264730] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.264733] EDD information not available.
[    0.278159] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.811054] Freeing initrd memory: 7786k freed
[    0.866819] isapnp: No Plug & Play device found
[    0.866874] Freeing unused kernel memory: 656k freed
[    0.868026] Write protecting the kernel text: 4676k
[    0.868073] Write protecting the kernel read-only data: 1840k
[    0.905258] udev: starting version 151
[    0.919893] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    1.169460] pata_via 0000:00:11.1: version 0.3.4
[    1.169479] pata_via 0000:00:11.1: can't derive routing for PCI INT A
[    1.178453] scsi0 : pata_via
[    1.190015] scsi1 : pata_via
[    1.192990] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    1.192996] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    1.197962] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    1.198026]   alloc irq_desc for 23 on node -1
[    1.198030]   alloc kstat_irqs on node -1
[    1.198042] via-rhine 0000:00:12.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.213942] eth0: VIA Rhine II at 0xdffffe00, 00:0c:76:f1:6d:5b, IRQ 23.
[    1.214656] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[    1.247133] usb 2-1: configuration #1 chosen from 1 choice
[    1.272689] usbcore: registered new interface driver hiddev
[    1.277609] input: A4Tech USB Full Speed as /devices/pci0000:00/0000:00:10.0/usb2/2-1/2-1:1.0/input/input5
[    1.277981] generic-usb 0003:09DA:8090.0001: input,hidraw0: USB HID v1.11 Mouse [A4Tech USB Full Speed] on usb-0000:00:10.0-1/input0
[    1.281998] input: A4Tech USB Full Speed as /devices/pci0000:00/0000:00:10.0/usb2/2-1/2-1:1.1/input/input6
[    1.282651] generic-usb 0003:09DA:8090.0002: input,hiddev96,hidraw1: USB HID v1.11 Keyboard [A4Tech USB Full Speed] on usb-0000:00:10.0-1/input1
[    1.282708] usbcore: registered new interface driver usbhid
[    1.282855] usbhid: v2.6:USB HID core driver
[    1.388327] ata1.01: HPA unlocked: 78163247 -> 78165360, native 78165360
[    1.388336] ata1.01: ATA-5: ST340016A, 3.75, max UDMA/100
[    1.388340] ata1.01: 78165360 sectors, multi 16: LBA 
[    1.404396] ata1.01: configured for UDMA/100
[    1.404595] scsi 0:0:1:0: Direct-Access     ATA      ST340016A        3.75 PQ: 0 ANSI: 5
[    1.404871] sd 0:0:1:0: Attached scsi generic sg0 type 0
[    1.405424] sd 0:0:1:0: [sda] 78165360 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.405512] sd 0:0:1:0: [sda] Write Protect is off
[    1.405517] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[    1.405562] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.405814]  sda: sda1 sda2 < sda5 >
[    1.446279] sd 0:0:1:0: [sda] Attached SCSI disk
[    1.568355] ata2.00: ATAPI: LITE-ON LTR-24102B, 5S04, max UDMA/33
[    1.584232] ata2.00: configured for UDMA/33
[    1.585169] scsi 1:0:0:0: CD-ROM            LITE-ON  LTR-24102B       5S04 PQ: 0 ANSI: 5
[    1.589176] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    1.589184] Uniform CD-ROM driver Revision: 3.20
[    1.589427] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.589539] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.938223] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    4.204037] floppy0: no floppy controllers found
[   14.533992] Adding 1489912k swap on /dev/sda5.  Priority:-1 extents:1 across:1489912k 
[   14.632222] udev: starting version 151
[   15.014461] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.215448] Linux agpgart interface v0.103
[   15.394422] type=1505 audit(1274287743.627:2):  operation="profile_load" pid=436 name="/sbin/dhclient3"
[   15.394844] type=1505 audit(1274287743.627:3):  operation="profile_load" pid=436 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   15.395098] type=1505 audit(1274287743.627:4):  operation="profile_load" pid=436 name="/usr/lib/connman/scripts/dhclient-script"
[   15.445389] irda_init()
[   15.445426] NET: Registered protocol family 23
[   15.510379] lp: driver loaded but no devices found
[   15.516527] vga16fb: initializing
[   15.516538] vga16fb: mapped to 0xc00a0000
[   15.516919] fb0: VGA16 VGA frame buffer device
[   15.548351] agpgart: Detected VIA KT400/KT400A/KT600 chipset
[   15.577575] agpgart-via 0000:00:00.0: AGP aperture is 128M @ 0xe0000000
[   15.851102] nvidia: module license 'NVIDIA' taints kernel.
[   15.851110] Disabling lock debugging due to kernel taint
[   16.624717] ACPI: resource vt596_smbus [0x400-0x407] conflicts with ACPI region SMOV [0x400-0x406]
[   16.624722] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   16.790637] Console: switching to colour frame buffer device 80x30
[   16.808880]   alloc irq_desc for 22 on node -1
[   16.808886]   alloc kstat_irqs on node -1
[   16.808899] VIA 82xx Audio 0000:00:11.5: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   16.809066] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   16.841953]   alloc irq_desc for 16 on node -1
[   16.841961]   alloc kstat_irqs on node -1
[   16.841974] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.841987] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   16.844697] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.17  Thu Apr 15 05:28:41 PDT 2010
[   17.081464] type=1505 audit(1274287745.315:5):  operation="profile_load" pid=586 name="/usr/share/gdm/guest-session/Xsession"
[   17.086510] type=1505 audit(1274287745.319:6):  operation="profile_replace" pid=587 name="/sbin/dhclient3"
[   17.086979] type=1505 audit(1274287745.319:7):  operation="profile_replace" pid=587 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   17.087242] type=1505 audit(1274287745.319:8):  operation="profile_replace" pid=587 name="/usr/lib/connman/scripts/dhclient-script"
[   17.105235] type=1505 audit(1274287745.339:9):  operation="profile_load" pid=588 name="/usr/bin/evince"
[   17.119774] type=1505 audit(1274287745.351:10):  operation="profile_load" pid=588 name="/usr/bin/evince-previewer"
[   17.128053] type=1505 audit(1274287745.363:11):  operation="profile_load" pid=588 name="/usr/bin/evince-thumbnailer"
[   17.554270] eth0: link down
[   17.554430] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.986221] ppdev: user-space parallel port driver
[   18.445072] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[   18.445094] agpgart-via 0000:00:00.0: bridge is in legacy mode, falling back to 2.x
[   18.445103] agpgart-via 0000:00:00.0: putting AGP V2 device into 4x mode
[   18.445154] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
[   18.569854] floppy0: no floppy controllers found
[  133.852036] usb 1-3: new high speed USB device using ehci_hcd and address 3
[  134.001911] usb 1-3: configuration #1 chosen from 1 choice
[  134.062392] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[  134.107173] usbcore: registered new interface driver ndiswrapper
[  165.176208] usb 1-3: USB disconnect, address 3
[  169.784031] usb 1-6: new high speed USB device using ehci_hcd and address 4
[  169.933156] usb 1-6: configuration #1 chosen from 1 choice
[  482.011882] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  482.011969] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  492.164042] eth0: no IPv6 routers present
jackxn@jackxn-Kellerbar:~$

---

### Post by moviemaniac on 2010-05-19
> [ 133.852036] usb 1-3: new high speed USB device using ehci_hcd and address 3
[ 134.001911] usb 1-3: configuration #1 chosen from 1 choice
[ 134.062392] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[ 134.107173] usbcore: registered new interface driver ndiswrapper
[ 165.176208] usb 1-3: USB disconnect, address 3
[ 169.784031] usb 1-6: new high speed USB device using ehci_hcd and address 4
[ 169.933156] usb 1-6: configuration #1 chosen from 1 choice

Did you try to get the stick running using ndiswrapper? If so, you will have to remove ndiswrapper support for this device.

---

### Post by Jackxn on 2010-05-19
No, didn't work with ndiswrapper either...i'lll remove it

---

### Post by Jackxn on 2010-05-19
repeated all steps, still no green light....already removed ndiswrapper...rebooting

---

### Post by Jackxn on 2010-05-19
Now run:

sudo make unload to unload both wireless and bluetooth modules
sudo make wlunload to unload wireless modules
sudo make btunload to unload bluetooth modules

And then load the wireless or bluetooth module you need. If unsure reboot.
Alternatively use sudo make load/wlload/btload to load modules

??? any action required?

---

### Post by moviemaniac on 2010-05-19
Nope, after a reboot it should work - but you might have to run "sudo make install" again in the folder where you built the new drivers.

---

### Post by Jackxn on 2010-05-19
Trying a clean re-install... at least the stick works with win7 :mad:

---

### Post by moviemaniac on 2010-05-19
Blame Atheror for their non-existing cooperation :(

---

### Post by Jackxn on 2010-05-19
there is an usb wlan stick from TP-Link that comes with a Linux driver, but that one was sold out...

---

### Post by moviemaniac on 2010-05-19
That one must've used a different, well supported chipset. The internal chipset - not the brand of stick - makes the difference.
When I bought my last wlan-stick I made sure it used a chipset (Ralink at the time) that was supported by both the manufacturer and the kernel. Great OOTB experience. However I have to say that most WLAN-USB-dongles available today should "just work" OOTB under linux if using a rather recent kernel - but there are always the unfortunate people with totally unsupported (due to a-hole manufacturers) or in-progress-support.

---

### Post by Jackxn on 2010-05-19
and you are sure that i use the correct firmware? would be a perfect facepalm experience if not^^

---

### Post by moviemaniac on 2010-05-19
there's no other firmware for this device - if you followed my advice to the letter the you should be fine. On that note: Could you check the filesize of the firmware? If it has 0kb then the download was corrupt - I just remembered this happened to someone else before in this thread :D

---

### Post by Jackxn on 2010-05-19
Funzt scho de Sau!

---

### Post by morph_89 on 2010-05-28
Hello, i have one of this wifi usb adapters. I install compat-wireless-2010-04-24 and moved the firmware to the correct place. I'm not sure if my problem is caused because i need a newer compat wireless installation or what. 

After i did sudo make load ubuntu completely frooze up. I couldn't even access the terminal by pressing cntrl alt f1. I rebooted. Inserted the card and it was working. I could even configure different VMWare virtal machines to access internet from different conections. Everything was running smoothly until i try using aircrack-ng.

When using it as monitor with airodump-ng it worked for about half an hour to lead to a completely system freeze again.
After I rebooted i tried using aireplay-ng to inject and it didn't even try, everything just froozed. 

Well i couldn't find what the problem is about. Maybe something went wrong during the installation, or the version of the compat* that i installed is outdated and does not support fully my wifi card or what.

Could anyone use this card to inject packages?

Please any help would be appreciated.

---

### Post by Elisa_carol on 2010-06-02
> **moviemaniac said:**
> @sippick: I already posted the info in this thread, but here's an updated version:

Download this file to cour Desktop: [http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=blob_plain;f=ar9271.fw;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=blob_plain;f=ar9271.fw;hb=HEAD)

then open up a terminal and enter these commands one after the other (you will be asked for your password on the last step)

cd Desktop
sudo mv ar9271.fw /lib/firmware

Now download this file to your desktop: [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-05-06.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-05-06.tar.bz2)
Then open a terminal and enter these commands one after the other (you will be asked for your password on the last step):
cd Desktop
tar xjvf compat-wireless-2010-05-06.tar.bz2
cd compat-wireless-2010-05-06
make && sudo make install

after that reboot.

I'm newbie to ubuntu. I got to install ubuntu 9.10 in my computer, cause the 10.04 I coun't make work.

So I read all the thread and, at last, i made the above steps.
It appeared to work fine, but I cannot connect to the rooter... it keeps asking the key for the conection. The key is right, works for windows and the linux in a notebook, so I don't know what to do.

lsusb:
Bus 002 Device 002: ID 0cf3:1006 Atheros Communications, Inc.

---

### Post by morph_89 on 2010-06-02
i don't know exactly how to solve your problem but i would bet money that it has to do with the encryption of the key. If you have access to the router and you want a temporal fix you could try changing between wpa and wpa2 encryptions or at last resort use wep. try connecting every time you change the configuration.

There is probably a way to fix your problem with the current encryption your router is using, a more experienced user may answer u how to do this... it is probably done by modifing /etc/network/interfaces 

good luck

---

### Post by samhall555 on 2010-06-10
[http://dinthsblog.blogspot.com/2010/04/i-was-fighting-to-run-tp-link-wn422g-v2.html](http://dinthsblog.blogspot.com/2010/04/i-was-fighting-to-run-tp-link-wn422g-v2.html)

worked for me

---

### Post by vagrale13 on 2010-07-01
[COLOR=#000000]If someone still have problems with[/COLOR]
```
 Bus 001 Device 006: ID 0cf3:1006 Atheros Communications, Inc.
```see here [URL="https://bugs.launchpad.net/ubuntu/+source/linux/+bug/578267"]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/578267
[/URL] and just read the post **[COLOR=Blue]*#5*[/COLOR]** & **[COLOR=Blue]*#6*[/COLOR]**!
I made a *.deb* archive and works for kernel  **2.6.32-22-generic** & **2.6.32-23-generic** but  only **32bit**!

---

### Post by c0rrupt.own on 2010-07-03
Can I use this .deb for TL-WN722N ?

---

### Post by vagrale13 on 2010-07-04
> **c0rrupt.own said:**
> Can I use this .deb for TL-WN722N ?
I think yes, If **lsusb** output is
```
Bus 001 Device 006: ID 0cf3:1006 Atheros Communications, Inc
```then you can use it! Just select the right *.deb* for your kernel!

---

### Post by c0rrupt.own on 2010-07-04
Damn no 

Bus 001 Device 002: ID 0cf3:9271 Atheros Communications, Inc.

---

### Post by vagrale13 on 2010-07-04
> **c0rrupt.own said:**
> Damn no

Bus 001 Device 002: ID 0cf3:9271 Atheros Communications, Inc.
I think your chipset works with the same driver **ath9k_htc**
and must be works fine! :)
[http://linuxwireless.org/en/users/Drivers/ath9k_htc/devices](http://linuxwireless.org/en/users/Drivers/ath9k_htc/devices) :popcorn:

---

### Post by c0rrupt.own on 2010-07-05
That was first thing what I try then I try ndiswrapper and backports from repository. ](*,) [http://ubuntuforums.org/showthread.php?t=1522917](http://ubuntuforums.org/showthread.php?t=1522917)

---

### Post by nastelroy on 2010-07-17
> **moviemaniac said:**
> You didn't copy the firmware file:

Download this file to cour Desktop: [http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=blob_plain;f=ar9271.fw;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=blob_plain;f=ar9271.fw;hb=HEAD)

then open up a terminal and enter these commands one after the other (you will be asked for your password on the last step)

cd Desktop
sudo mv ar9271.fw /lib/firmware

reboot and everything should work

Hi moviemaniac...good job..its workk for me
I use compact-wireless-2010-07-08.
but I found some bug in this driver..I cannot connect to my AP with MAC filtering, tough i have change my 422g with authorized MAC address with "ifconfig".

I tried with another wireless (broadcom 4312) with b43 driver it has success connect to AP.
but no with 422g with ath9k_htc driver.

any idea please...


Dell Vostro 1320
Ubuntu 10.04 
kernel 2.6.32-21-generic

---

### Post by Falco-Peregrinus on 2010-09-13
Hi all this is my 2nd post on this forum


I read re-read and milled over the conversations in this link, to no avail not really sure which step is step 1 and how to go about it. I have never used a terminal before or installed ubuntu before today. I have 10.04 and I own a Toshiba L300  and would like to connect to my open wireless network with a TP-Link TL-WN422G usb wireless adapter 


I have also contacted tp link and will see what they have to say on the subject.

My sincere thanks in advance for your time and effort in helping me resolve this issue

---

### Post by Falco-Peregrinus on 2010-09-14
[SIZE=2][COLOR=navy][COLOR=navy][FONT=Verdana]This is what TP LINK had to say on the subject....
[/FONT][/COLOR][/COLOR][/SIZE]

[SIZE=2][COLOR=navy][COLOR=navy][FONT=Verdana][/FONT][/COLOR][/COLOR][/SIZE]
Is it worth looking at cause I'm afraid I bugger up something by mistake lol
[SIZE=2][COLOR=navy][COLOR=navy][FONT=Verdana][/FONT][/COLOR][/COLOR][/SIZE]
[SIZE=2][COLOR=navy][COLOR=navy][FONT=Verdana]
[/FONT][/COLOR][/COLOR][/SIZE]
[SIZE=2][COLOR=navy][COLOR=navy][FONT=Verdana]-----------------------------------------------------------------
[/FONT][/COLOR][/COLOR][/SIZE]
[SIZE=2][COLOR=navy][COLOR=navy][FONT=Verdana]Dear customer,[/FONT][/COLOR][/COLOR][/SIZE][COLOR=blue][COLOR=blue][/COLOR][/COLOR]
  [SIZE=2][COLOR=navy][COLOR=navy][FONT=Verdana]Thank you very much for your email requesting information about our product.[/FONT][/COLOR][/COLOR][/SIZE]
  [SIZE=2][COLOR=navy][COLOR=navy][FONT=Verdana] [/FONT][/COLOR][/COLOR][/SIZE]
  [SIZE=2][COLOR=navy][COLOR=navy][FONT=Verdana]As you known, there is no driver of ubuntu 10.04 (Linux) in the CD, so we don’t know what is your original driver and firmware,[/FONT][/COLOR][/COLOR][/SIZE]
  [SIZE=2][COLOR=navy][COLOR=navy][FONT=Verdana] [/FONT][/COLOR][/COLOR][/SIZE]
  [SIZE=2][COLOR=navy][COLOR=navy][FONT=Verdana]But I would like to provide you the chipset of the TL-WL422G[/FONT][/COLOR][/COLOR][/SIZE] [SIZE=2][COLOR=navy][COLOR=navy][FONT=Verdana][/FONT][/COLOR][/COLOR][/SIZE]
  [SIZE=2][COLOR=navy][COLOR=navy][FONT=Verdana] [/FONT][/COLOR][/COLOR][/SIZE]
  [SIZE=2][COLOR=navy][COLOR=navy][FONT=Verdana]TL-WL422G v1:[/FONT][/COLOR][/COLOR][/SIZE]**[B] **[/B]**[SIZE=2][COLOR=navy][COLOR=navy][FONT=Verdana][B]Atheros AR2524**[/FONT][/COLOR][/COLOR][/SIZE][/B][SIZE=2][COLOR=navy][COLOR=navy][FONT=Verdana], and V2: **[B]Atheros AR9271.**[/B] [/FONT][/COLOR][/COLOR][/SIZE]
  [SIZE=2][COLOR=navy][COLOR=navy][FONT=Verdana] [/FONT][/COLOR][/COLOR][/SIZE]
  [SIZE=2][COLOR=navy][COLOR=navy][FONT=Verdana]You may find the right driver from the chipset manufacturer's official site and you need to learn how to install or update from the Internet.[/FONT][/COLOR][/COLOR][/SIZE]
  [SIZE=2][COLOR=navy][COLOR=navy][FONT=Verdana] [/FONT][/COLOR][/COLOR][/SIZE]
  [SIZE=2][COLOR=navy][COLOR=navy][FONT=Verdana]For TL-WL422G V1, you can try this link:[/FONT][/COLOR][/COLOR][/SIZE] [SIZE=2][COLOR=navy][COLOR=navy][FONT=Verdana][http://wireless.kernel.org/en/users/Drivers/zd1211rw](http://wireless.kernel.org/en/users/Drivers/zd1211rw) [/FONT][/COLOR][/COLOR][/SIZE]
  [SIZE=2][COLOR=navy][COLOR=navy][FONT=Verdana] [/FONT][/COLOR][/COLOR][/SIZE]
  [SIZE=2][COLOR=navy][COLOR=navy][FONT=Verdana]And V2, try the link:[/FONT][/COLOR][/COLOR][/SIZE] [SIZE=2][COLOR=navy][COLOR=navy][FONT=Verdana][http://wireless.kernel.org/en/users/Drivers/ath9k_htc](http://wireless.kernel.org/en/users/Drivers/ath9k_htc) [/FONT][/COLOR][/COLOR][/SIZE]
  [SIZE=2][COLOR=navy][COLOR=navy][FONT=Verdana] [/FONT][/COLOR][/COLOR][/SIZE]
  [SIZE=2][COLOR=navy][COLOR=navy][FONT=Verdana]Hope you can understand that we have limited knowledge on this OS. And have a nice day~~[/FONT][/COLOR][/COLOR][/SIZE]
  [SIZE=2][COLOR=navy][COLOR=navy][FONT=Verdana] [/FONT][/COLOR][/COLOR][/SIZE]
  [SIZE=2][COLOR=navy][COLOR=navy][FONT=Verdana]Any further help please feel free to let me know.To get technical support quicker, please go to [/FONT][/COLOR][/COLOR][/SIZE][COLOR=blue][COLOR=blue][[SIZE=2][COLOR=navy][COLOR=navy][FONT=Verdana]http://www.tp-link.com/support/faq.asp[/FONT][/COLOR][/COLOR][/SIZE]]("http://www.tp-link.com/support/faq.asp")[/COLOR][/COLOR][SIZE=2][COLOR=navy][COLOR=navy][FONT=Verdana][/FONT][/COLOR][/COLOR][/SIZE]
  [SIZE=2][COLOR=navy][COLOR=navy][FONT=Verdana]Best Regards!
-----------------------------
Susan.ye
Technical Support Engineer
 TP-LINK TECHNOLOGIES CO., LTD.
 E-mail:  Susan.ye[/FONT][/COLOR][/COLOR][/SIZE][COLOR=blue][COLOR=blue][EMAIL="harvey.liu@tp-link.com"][SIZE=2][COLOR=navy][COLOR=navy][FONT=Verdana]@tp-link.com[/FONT][/COLOR][/COLOR][/SIZE][/EMAIL][/COLOR][/COLOR][SIZE=2][COLOR=navy][COLOR=navy][FONT=Verdana]
 Tel:  +1 866 225-8139
       +86 755-2650-4400
Website:  [/FONT][/COLOR][/COLOR][/SIZE][COLOR=blue][COLOR=blue][[SIZE=2][COLOR=navy][COLOR=navy][FONT=Verdana]www.tp-link.com/support/Support.asp[/FONT][/COLOR][/COLOR][/SIZE]]("http://www.tp-link.com/support/Support.asp")[/COLOR][/COLOR]

---

### Post by moviemaniac on 2010-09-19
Can you download the Ubuntu 10.10 beta from here: [http://cdimages.ubuntu.com/releases/10.10/beta/](http://cdimages.ubuntu.com/releases/10.10/beta/)

Then boot into the live CD and see whether the wifi-dongle works there (it should due to the updated drivers). In that case it would be the easiest solution for an inexperienced user to reinstall Ubuntu (use the 10.10 beta cd - it will be upgraded to the final release by means of daily updates). The reason I'm suggesting a reinstall is because I wouldn't recommend updating to 10.10beta using the updater as this tends to fail a lot before the release candidates are out.

@nastelroy: I would definitely suggest trying a newer compat-wireless version and see if the bug is fixed there. An easy way to check would also be to try the ubuntu 10.10 beta in live-mode. As you sound like a more experienced user I'd suggest trying a newer compat-wireless with the existing installation and switching to 10.10 once it's out.

---

### Post by opethonia on 2010-09-29
Hi, I'm new in linux environment, i just installed ubuntu 10.04 64 bits and after fallowing your instructions wn422g doesn't work, btw link to ar9271 is broken.

I also try using ndiswrapper but win2k_xp driver shows error, winxp64 drivers works but i get "hardware not present" then i  try **"sudo ndiswrapper -a 0cf3:1006 netathuw"**, **"sudo ndiswrapper -m"**, **"sudo ndiswrapper -ma"**, **"sudo ndiswrapper -mi" **but again... i get this:```
user@ubuntu:~$ sudo ndiswrapper -a 0cf3:1006 netathuw
driver 'netathuw' is not installed (properly)!

```

Please help me i don't really want to back to windows 7  :/

Thanks and sorry for my english.

---

### Post by moviemaniac on 2010-10-03
I've never used ndiswrapper before so I can't comment on that issue.

Your problem ist most likely that you didn't install the firmware file (you said the download is broken).

Download the attached firmware file to your desktop. The open a terminal and proceed as follows:

cd Desktop
tar -xvf ar9271.fw.tar.bz2
sudo mv ar9271.fw /lib/firmware

reboot and see whether it works. Be sure to unplug your device and plug it in again after rebooting.

---

### Post by Costas000 on 2010-12-07
> **moviemaniac said:**
> Okay, here's one thing to try:
Download this file to cour Desktop: [http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=blob;f=ar9271.fw;h=2398e5517b0ad7da7adad54763b91705a3d2acb7;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=blob;f=ar9271.fw;h=2398e5517b0ad7da7adad54763b91705a3d2acb7;hb=HEAD)

then open up a terminal and enter these commands one after the other (you will be asked for your password on the last step)

cd Desktop
sudo mv ar9271.fw /lib/firmware

reboot and see whether it works. Be sure to unplug your device and plug it in again after rebooting.

If it doesn't, follow these steps:

Download this file to your desktop: [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)
Then open a terminal and enter these commands one after the other (you will be asked for your password on the last step):
cd Desktop
tar xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless-2.6
./scripts/driver-select ath9k_htc
make && sudo make install

after that reboot.

i have done all these and still can`t make it work. Not even the light on the the usb wireless card won't turn on, is there anything else to do?

---

### Post by edgethehog on 2011-01-03
I've got Ubuntu 10.10, Windows 7 and TL-WN422g. 
It works from scratch under Ubuntu. Still it really lacks consistency. Speed is going up and down every second, it is ok for web surfing and absolutely intolerable in case you want to download something. 
Under Win7 max speed is around 1.2 mb/sec, Ubuntu - 600-800 kb/sec best. Under Win7 adapter runs smoothly, Ubuntu provides some kind of a slalom ride - speed can go up and down though it rarely disconnects. And yeah, sometimes I have to unplug adapter and plug it again.

Comparing to Windows 7 I have to admit there is no sense using Ubuntu with such wi-fi connection. But I really like the OS.

I hope to find help here.

P.S. I have tried ndiswrapper and solution from this topic. First one killed connection at all, second didn't bring any changes.

---

### Post by akunp2 on 2011-01-12
> **moviemaniac said:**
> Okay, here's one thing to try:
Download this file to cour Desktop: [http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=blob;f=ar9271.fw;h=2398e5517b0ad7da7adad54763b91705a3d2acb7;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=blob;f=ar9271.fw;h=2398e5517b0ad7da7adad54763b91705a3d2acb7;hb=HEAD)

then open up a terminal and enter these commands one after the other (you will be asked for your password on the last step)

cd Desktop
sudo mv ar9271.fw /lib/firmware

reboot and see whether it works. Be sure to unplug your device and plug it in again after rebooting.

If it doesn't, follow these steps:

Download this file to your desktop: [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)
Then open a terminal and enter these commands one after the other (you will be asked for your password on the last step):
cd Desktop
tar xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless-2.6
./scripts/driver-select ath9k_htc
make && sudo make install

after that reboot.


i have follow your instruction but the wireless still undetected can you help me ?

---

### Post by Ubunfoo on 2011-07-10
Hey there:

I appear to be having the same problem disPlay was having.  I bought a TP-Link TL-WN422G v2 usb adapter, and am having trouble getting Kubuntu 11.04 to utilize it.  I have a built-in wireless card in my Lenovo G560 that it seems to be utilizing by default - even when the TP-Link is plugged in.  

lspci specifies this built in card as:
```
05:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controler (rev 01) 
```when I plug in the TP-Link adapter, it recognizes it, as you pointed out moviemaniac.  
lsusb returns its entry:
```
Bus 002 Device 005: ID 0cf3:1006 Atheros Communications, Inc. TP-Link TL-WN422G v2 802.11g [Atheros AR9271]
```However, I tried both of your fixes you listed, and so far neither of them seem to be working.  My signal strength is just as it was before - sub-mediocre.  

An interesting bit of information though - I use backtrack5 on occasion as well, and it seems to be able to utilize its power just fine.  I know this because I can packet inject with it - which I couldn't do with my built-in card.  This is actually what fooled me into believing that this card was going to be perfect.  Before I tested it in kubuntu and windows 7 that is.  No driver support for windows 7 it seems...(TP-Link....honestly....)

Thanks, 
Ubunfoo

---

### Post by buckbugs on 2012-01-05
im having the same problem with USB wireless TP-Link TL-WN422G

My OS is backtrack5 R1 (kernel : 2.6.39.4)

This is my solution to share:

Download this file to your desktop: [http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.39/compat-wireless-2.6.39-1.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.39/compat-wireless-2.6.39-1.tar.bz2)

#tar xjvf compat-wireless-2.6.39-1.tar.bz2
#cd compat-wireless-2.6.39-1
#./configure
#sudo make && sudo make install

 after that reboot.

hmmmm the problem is SOLVED :)

---

