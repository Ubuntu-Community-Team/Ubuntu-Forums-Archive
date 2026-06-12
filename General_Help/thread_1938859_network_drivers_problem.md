---
title: "network drivers problem"
date: 2012-03-10
forum: General Help
---

### Post by mknutsen on 2012-03-10
i just got a new laptop and loaded it up with ubuntu but it seems the network card isnt supported by ubuntu
the laptop is the hp dm1-3214nr
network card, from what i can tell, is the ralink 539f
the hp website has the network drivers, but its an exe for win7

HELP PLEASE!!!!

---

### Post by wildmanne39 on 2012-03-10
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by mknutsen on 2012-03-10
```
max@max-HP-Pavilion-dm1-Notebook-PC:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux max-HP-Pavilion-dm1-Notebook-PC 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686 athlon i386 GNU/Linux
max@max-HP-Pavilion-dm1-Notebook-PC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

max@max-HP-Pavilion-dm1-Notebook-PC:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
max@max-HP-Pavilion-dm1-Notebook-PC:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  0 
binfmt_misc            13213  1 
rfcomm                 38125  8 
snd_seq_midi           13132  0 
sco                    17827  2 
bnep                   17785  2 
joydev                 17322  0 
l2cap                  48656  16 rfcomm,bnep
snd_hda_codec_idt      60537  1 
hp_wmi                 13418  0 
snd_rawmidi            25269  1 snd_seq_midi
zram                   18216  2 
sparse_keymap          13666  1 hp_wmi
snd_hda_codec_hdmi     27535  1 
snd_hda_intel          24140  2 
uvcvideo               66851  0 
snd_hda_codec          90901  3 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel
snd_seq_midi_event     14475  1 snd_seq_midi
snd_hwdep              13274  1 snd_hda_codec
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
psmouse                73312  0 
videodev               75143  1 uvcvideo
btusb                  18160  1 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
snd_timer              28659  2 snd_seq,snd_pcm
k10temp                12951  0 
serio_raw              12990  0 
snd                    55295  14 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_seq,snd_pcm,snd_seq_device,snd_timer
sp5100_tco             13456  0 
hp_accel               21632  0 
lis3lv02d              19285  1 hp_accel
i2c_piix4              13095  0 
input_polldev          13735  1 lis3lv02d
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
dm_raid45              88410  0 
xor                    21860  1 dm_raid45
btrfs                 527388  0 
zlib_deflate           26594  1 btrfs
libcrc32c              12543  1 btrfs
usbhid                 41704  0 
hid                    77084  1 usbhid
usb_storage            43946  0 
uas                    17676  0 
radeon                900494  4 
ttm                    65184  1 radeon
ahci                   21591  3 
drm_kms_helper         40745  1 radeon
libahci                25548  1 ahci
video                  18951  0 
drm                   180037  6 radeon,ttm,drm_kms_helper
r8169                  42534  0 
i2c_algo_bit           13184  1 radeon
ramzswap               13202  0 
xvmalloc               13453  1 ramzswap
max@max-HP-Pavilion-dm1-Notebook-PC:~$ 

```

---

### Post by mknutsen on 2012-03-10
the reply didnt go to you, sorry. see below. thanks!

---

### Post by wildmanne39 on 2012-03-10
Hi, I still need to see:
```
lspci -nnk | grep -iA2 net
```
and please include:
```
lsusb
```
Thanks

---

### Post by mknutsen on 2012-03-10
whoops, sorry
```
max@max-HP-Pavilion-dm1-Notebook-PC:~$ lspci -nnk | grep -A2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Hewlett-Packard Company Pavilion DM1Z-3000 [103c:1611]
	Kernel driver in use: r8169
max@max-HP-Pavilion-dm1-Notebook-PC:~$ lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 174f:1134 Syntek 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 003: ID 148f:2000 Ralink Technology, Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0461:4d81 Primax Electronics, Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
max@max-HP-Pavilion-dm1-Notebook-PC:~$ 

```

---

### Post by wildmanne39 on 2012-03-11
Hi, please try:
```
sudo rmmod -f hp_wmi
```
if this works we will need to make it permanent.

Is this a bluetooth device or do you have a wireless card also and is it built in?
Thanks

---

### Post by mknutsen on 2012-03-11
that did not fix anything, as far as i can tell.
this laptop has both bluetooth and a built in wireless card. my wifi network was automatically detected the one time i booted windows 7.

---

### Post by wildmanne39 on 2012-03-11
Hi, this should get your wireless working.
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms patch fakeroot unzip
wget http://media.cdn.ubuntu-de.org/forum/attachments/3208747/angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.zip
unzip angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.zip
cd angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/
sudo make
sudo make install
sudo modprobe -v rt5390sta
sudo depmod -a
sudo update-initramfs -u 
```
Then reboot.
Thanks

---

### Post by mknutsen on 2012-03-11
```
max@max-HP-Pavilion-dm1-Notebook-PC:~$ wget http://media.cdn.ubuntu-de.org/forum/attachments/3208747/angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.zip
--2012-03-11 12:56:09--  http://media.cdn.ubuntu-de.org/forum/attachments/3208747/angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.zip
Resolving media.cdn.ubuntu-de.org... 213.95.41.13
Connecting to media.cdn.ubuntu-de.org|213.95.41.13|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2012-03-11 12:56:09 ERROR 404: Not Found.

```

---

### Post by wildmanne39 on 2012-03-11
Hi, I am searching for that driver to see where else it can be downloaded from.
Thanks

---

### Post by mknutsen on 2012-03-11
ok!
thank you so much for your help

---

### Post by wildmanne39 on 2012-03-11
Hi, here is the directions with the new driver link just copy and paste the commands and it should work after a reboot.
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms patch fakeroot unzip
wget http://media.cdn.ubuntu-de.org/forum/attachments/35/07/3208747-angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.zip
unzip angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.zip
cd angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/
sudo make
sudo make install
sudo modprobe -v rt5390sta
sudo depmod -a
sudo update-initramfs -u 
```
Thanks

---

### Post by mknutsen on 2012-03-11
Thank you so much!!! you are a life saver!
i had heard great things about the ubuntu community

---

### Post by wildmanne39 on 2012-03-11
Hi, your welcome! I am glad I could help, please use thread tools at the top of the page to mark this thread solved.
Thanks

---

### Post by hwert on 2012-11-03
Thank you for reposting the correct download driver address. I spent the better part of three days trying to get my wireless driver rt5390sta working on my HO Pavilion g7 laptop with debian squeeze 6.0+, to no avail. Your post solved the problem.

Harry Wert
Nuclear Physicist

---

