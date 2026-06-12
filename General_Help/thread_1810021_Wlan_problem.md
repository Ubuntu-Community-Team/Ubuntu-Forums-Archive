---
title: "Wlan problem"
date: 2011-07-22
forum: General Help
---

### Post by akina_ian on 2011-07-22
This is my very first time to use linux . 

I Installed Ubuntu 11.04 By LiveCD . Everything is Fine except  the wifi .  it cannot connect .So i think i will just install the driver of Wlan . Can I  install windows Driver in linux . SAmple Wlan driver or Bluetooth driver.

---

### Post by jamesisin on 2011-07-22
No.  Windows drivers will not work with the Linux kernel.  If you provide more information about your connection problems we might be able to give you better advice.

Also, it's important to note that you may need to add additional wireless adapter drivers while still connected via wire.  Ubuntu will need to download those drivers somehow and cannot connect via wireless without having done so.

---

### Post by Roter1337 on 2011-07-22
If you have the windows drivers, wouldn't you be able to integrate them in using ndiswrapper? Just a thought.

---

### Post by gandaran on 2011-07-22
> **akina_ian said:**
> This is my very first time to use linux . 

I Installed Ubuntu 11.04 By LiveCD . Everything is Fine except  the wifi .  it cannot connect .So i think i will just install the driver of Wlan . Can I  install windows Driver in linux . SAmple Wlan driver or Bluetooth driver.
yes you can use windows XP drivers, (windows 7 and vista don't work) but I don't recommend it as in 99% of wireless devices there is a native linux driver for it.
first you need to find the wireless device chipset, type in terminal and post the output
```
lspci
```
then we will find the driver.

---

### Post by jamesisin on 2011-07-22
gandaran - I didn't realize XP drivers would work.

---

### Post by akina_ian on 2011-07-22
> **jamesisin said:**
> No.  Windows drivers will not work with the Linux kernel.  If you provide more information about your connection problems we might be able to give you better advice.

Also, it's important to note that you may need to add additional wireless adapter drivers while still connected via wire.  Ubuntu will need to download those drivers somehow and cannot connect via wireless without having done so.

Thank you . i will connect the Via Wire , because it prompt to download the driver . I use ACER Apire 4310

---

### Post by akina_ian on 2011-07-22
> **gandaran said:**
> yes you can use windows XP drivers, (windows 7 and vista don't work) but I don't recommend it as in 99% of wireless devices there is a native linux driver for it.
first you need to find the wireless device chipset, type in terminal and post the output
```
lspci
```
then we will find the driver.

ok i will try it .

---

### Post by wildmanne39 on 2011-07-22
Hi, we need more information please type these commands in a terminal
```
lspci -nn
```
```
iwconfig
```
```
rfkill list All
```
```
lsmod
```
post the outcome  here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by akina_ian on 2011-07-23
> **wildmanne39 said:**
> Hi, we need more information please type these commands in a terminal
```
lspci -nn
``````
iwconfig
``````
rfkill list All
``````
lsmod
```post the outcome  here by clicking on new reply and click # and paste the information between the brackets.
Thank you

thank you sir . this is a great forum. so many supports "":):)

---

### Post by akina_ian on 2011-12-18
> **wildmanne39 said:**
> Hi, we need more information please type these commands in a terminal
```
lspci -nn
``````
iwconfig
``````
rfkill list All
``````
lsmod
```post the outcome  here by clicking on new reply and click # and paste the information between the brackets.
Thank you


Here's the result sir

> 
[LEFT]  iwconfig
   
  lo        no wireless extensions.
   
  eth0      no wireless extensions.
   
   
  lspci -nn
   
  00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
  00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
  00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
  00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
  00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
  00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
  00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
  00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
  00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
  00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
  00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
  00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
  00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
  00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
  00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
  00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
  00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
  02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
  03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
  0a:06.0 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02)
  0a:06.2 SD Host controller [0805]: O2 Micro, Inc. Integrated MMC/SD Controller [1217:7120] (rev 02)
  0a:06.3 Mass storage controller [0180]: O2 Micro, Inc. Integrated MS/xD Controller [1217:7130] (rev
   
   
   
  rfkill list all
   
  0: acer-wireless: Wireless LAN
                  Soft blocked: no
                  Hard blocked: no
  1: acer-bluetooth: Bluetooth
                  Soft blocked: yes
                  Hard blocked: no
  2: acer-threeg: Wireless WAN
                  Soft blocked: yes
                  Hard blocked: no
   
[/LEFT]


---

### Post by kaar3l on 2011-12-18
Open up hardware drivers. Then you can select b43 driver. You have to be connected to internet some way - with cable maybe. Then the driver is installed and after restart you should have a connection.

---

### Post by akina_ian on 2011-12-18
> **kaar3l said:**
> Open up hardware drivers. Then you can select b43 driver. You have to be connected to internet some way - with cable maybe. Then the driver is installed and after restart you should have a connection.

I've tried already connecting cable . But i cannot browse which means i don't have connection , but i'm connected via wire.

---

### Post by wildmanne39 on 2011-12-18
Hi, please post the results of:
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by akina_ian on 2011-12-18
> **wildmanne39 said:**
> Hi, please post the results of:
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

Here you go sir

> lsmod
Module                  Size  Used by
parport_pc             32111  0
ppdev                  12849  0
snd_hda_codec_realtek   255820  1
snd_hda_intel          24140  2
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0
i915                  450944  3
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
wl                   2642531  0
binfmt_misc            13213  1
acer_wmi               23123  0
sparse_keymap          13666  1 acer_wmi
drm_kms_helper         40745  1 i915
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   180037  4 i915,drm_kms_helper
uvcvideo               66851  0
psmouse                73312  0
videodev               75143  1 uvcvideo
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 17322  0
serio_raw              12990  0
i2c_algo_bit           13184  1 i915
soundcore              12600  1 snd
lib80211               14570  1 wl
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  1 i915
lp                     13349  0
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0
hid                    77084  1 usbhid
firewire_ohci          31504  0
sdhci_pci              13623  0
firewire_core          56138  1 firewire_ohci
sdhci                  22720  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
tg3                   131476  0

---

### Post by wildmanne39 on 2011-12-18
Hi, you have three things we need to take care of.

Please run these commands:
```
sudo su
echo "blacklist acer_wmi" >> /etc/modprobe.d/blacklist.conf
exit
```
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
```
sudo apt-get install b43-fwcutter firmware-b43-installer

```
Then unplug your wired connection and reboot.
Thanks

---

### Post by akina_ian on 2011-12-18
> **wildmanne39 said:**
> Hi, you have three things we need to take care of.

Please run these commands:
```
sudo su
echo "blacklist wl" >> /etc/modprobe.d/blacklist.conf
exit
```
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
```
sudo apt-get install b43-fwcutter firmware-b43-installer

```
Then unplug your wired connection and reboot.
Thanks


"blacklist wl" with the quote sir

---

### Post by wildmanne39 on 2011-12-18
Yes.

---

### Post by akina_ian on 2011-12-18
> **wildmanne39 said:**
> Yes.

this what is show

ian@ian-Aspire-4310:~$ sudo su
root@ian-Aspire-4310:/home/ian# echo "blacklist wl" >> /etc/modprobe.d/blacklist.conf
root@ian-Aspire-4310:/home/ian# exit
exit
ian@ian-Aspire-4310:~$ sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bcmwl-kernel-source
E: Unable to locate package broadcom-sta-common
E: Unable to locate package broadcom-sta-source

---

### Post by wildmanne39 on 2011-12-18
Hi, are you connected to the internet with a hard wire?
Thanks

---

### Post by akina_ian on 2011-12-18
> **wildmanne39 said:**
> Hi, are you connected to the internet with a hard wire?
Thanks

yes sir I'm connected via hard wire . its show connectd.

---

### Post by akina_ian on 2011-12-18
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package broadcom-sta-common is not installed, so not removed
Package broadcom-sta-source is not installed, so not removed
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 258 not upgraded.
After this operation, 3,367 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 129581 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules (1)
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
ian@ian-Aspire-4310:~$ sudo apt-get install b43-fvcutter firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package b43-fvcutter

---

### Post by wildmanne39 on 2011-12-18
Hi, run the commands again and just copy and paste them into the terminal so there are no typos.
Thanks

---

### Post by akina_ian on 2011-12-18
> **wildmanne39 said:**
> Hi, run the commands again and just copy and paste them into the terminal so there are no typos.
Thanks

hi sir i'm already connected via hard wire . when it prompted to install the driver i installed it but it cannot installed here's the error

[IMG]http://i.lulzimg.com/9e2f6bbf19.png[/IMG]

---

### Post by wildmanne39 on 2011-12-18
Hi, we are not tring to install the driver in additional drivers that one is harder to get to work. Please post the results of:
```
iwconfig
```
```
rfkill list all
``` 
```
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thanks

---

### Post by akina_ian on 2011-12-18
```

ian@ian-Aspire-4310:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ian@ian-Aspire-4310:~$ rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: acer-threeg: Wireless WAN
    Soft blocked: yes
    Hard blocked: no
ian@ian-Aspire-4310:~$ ^C
ian@ian-Aspire-4310:~$ lsmod
Module                  Size  Used by
wl                   2642531  0 
lib80211               14570  1 wl
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  2 
binfmt_misc            13213  1 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
i915                  450944  3 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
drm_kms_helper         40745  1 i915
acer_wmi               23123  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
sparse_keymap          13666  1 acer_wmi
snd_timer              28659  2 snd_pcm,snd_seq
uvcvideo               66851  0 
drm                   180037  4 i915,drm_kms_helper
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17322  0 
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
videodev               75143  1 uvcvideo
i2c_algo_bit           13184  1 i915
serio_raw              12990  0 
soundcore              12600  1 snd
video                  18951  1 i915
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
firewire_ohci          31504  0 
sdhci_pci              13623  0 
firewire_core          56138  1 firewire_ohci
sdhci                  22720  1 sdhci_pci
tg3                   131476  0 
crc_itu_t              12627  1 firewire_core



```

---

### Post by wildmanne39 on 2011-12-18
Hi, please run all the commands in post 15 again by copying and pasting exactly as they are.

The wl driver is still loading and it should not be, and the b3 driver should have installed but it was typed incorrectly.
Thanks

---

### Post by akina_ian on 2011-12-18
```
ian@ian-Aspire-4310:~$ sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package broadcom-sta-common is not installed, so not removed
Package broadcom-sta-source is not installed, so not removed
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 257 not upgraded.
After this operation, 3,367 kB disk space will be freed.
Do you want to continue [Y/n]?
```

sir what should i press Y/N.

---

### Post by wildmanne39 on 2011-12-18
Hi, yes.

---

### Post by akina_ian on 2011-12-18
wow , its already okie sir I'm already connected . Thank you very much  to you . I love you. haha. :):):):)

---

### Post by wildmanne39 on 2011-12-18
Hi, that is great, your welcome!!! would you please go to the top of the page and mark this thread solved by clicking on thread tools. 
Thank you

---

