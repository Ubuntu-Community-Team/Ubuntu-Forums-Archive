---
title: "Getting Wifi Card to work"
date: 2012-02-23
forum: General Help
---

### Post by louisgonick on 2012-02-23
This issue has been going on ever since I installed ubuntu on my machine. My wifi card simply wont be recognized by the OS. I have managed to turn it on using these commands: 
```
sudo rmmod -f ath5k
sudo rfkill unblock all
sudo modprobe ath5k

```

This gets my card working, but it is annoying to to this every time I turn my computer on. 

My card is an Intel Atheros chip.

---

### Post by wildmanne39 on 2012-02-23
Hi, this should make it work at boot, I thought we did this a long time ago.

```
gksudo gedit /etc/rc.local
```
Add your three lines above exit 0 
```
rmmod -f ath5k
rfkill unblock all
modprobe ath5k
```
Proofread carefully, save and close gedit. Reboot and tell us if it's working as expected.
Thanks

---

### Post by louisgonick on 2012-02-23
> **wildmanne39 said:**
> Hi, this should make it work at boot, I thought we did this a long time ago.

```
gksudo gedit /etc/rc.local
```
Add your three lines above exit 0 
```
rmmod -f ath5k
rfkill unblock all
modprobe ath5k
```
Proofread carefully, save and close gedit. Reboot and tell us if it's working as expected.
Thanks

Before saving, I will post the gedit text here:

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

rmmod -f ath5k
rfkill unblock all
modprobe ath5k 
exit 0

does everything look fine?

---

### Post by wildmanne39 on 2012-02-23
Hi, yes it does.
Thanks

---

### Post by louisgonick on 2012-02-23
> **wildmanne39 said:**
> Hi, yes it does.
Thanks

already rebooted and I had to turn the chipset manually again. It seems that it didn't work

---

### Post by wildmanne39 on 2012-02-23
Hi, post that contents of that file here please so we can make sure it got saved, because I have never seen that fail to work and that is the only way that I know of to make it work.
Thanks

---

### Post by louisgonick on 2012-02-23
> **wildmanne39 said:**
> Hi, post that contents of that file here please so we can make sure it got saved, because I have never seen that fail to work and that is the only way that I know of to make it work.
Thanks
This is what I get when I type "gksudo gedit /etc/rc.local":
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

rmmod -f ath5k
rfkill unblock all
modprobe ath5k 
exit 0
```

---

### Post by wildmanne39 on 2012-02-23
Hi, that should do it, that is exactly what is done when you type it manually after you boot.

Is your wired connection unplugged when you boot up or is there any other internet devices connected like an usb adapter? 

Also please reboot then before you run the commands please post:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
nm-tool
sudo iwlist scan
```
Thanks

---

### Post by louisgonick on 2012-02-23
> **wildmanne39 said:**
> Hi, that should do it, that is exactly what is done when you type it manually after you boot.

Is your wired connection unplugged when you boot up or is there any other internet devices connected like an usb adapter? 

Also please reboot then before you run the commands please post:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
nm-tool
sudo iwlist scan
```
Thanks

Here are the results:
cat /etc/lsb-release; uname -a
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux louis-Compaq-Presario-CQ60-Notebook-PC 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:50:54 UTC 2012 i686 i686 i386 GNU/Linux
```

lspci -nnk | grep -iA2 net:
```
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:360b]
	Kernel driver in use: r8169
--
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
	Subsystem: Hewlett-Packard Company AR5BXB63 (Foxconn) 802.11bg Mini PCIe NIC [103c:137a]
	Kernel modules: ath5k


```

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

```

rfkill list all:
```
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
lsmod:
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
joydev                 17393  0 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_conexant    52418  1 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_hda_intel          24262  2 
snd_hda_codec          91859  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73673  0 
serio_raw              12990  0 
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i915                  509519  3 
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
wmi                    18744  1 hp_wmi
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
ums_realtek            13096  0 
usb_storage            44173  1 ums_realtek
hid                    77367  1 usbhid
uas                    17699  0 
ahci                   21634  2 
libahci                25727  1 ahci
r8169                  43104  0 


```

nm-tool:
```
NetworkManager Tool

State: disconnected


** (process:2207): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation
- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:1F:16:77:19:6D

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off
```

sudo iwlist scan:
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

---

### Post by wildmanne39 on 2012-02-23
Hi, ok I am going to ask a friend to take a look that is very experienced with networking issues.
Thanks

---

### Post by chili555 on 2012-02-23
Please try this:> sudo gedit /etc/rc.localChange it to:```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

[COLOR="Red"]modprobe -r[/COLOR] ath5k
rfkill unblock all
modprobe ath5k 

exit 0
```Proofread carefully, save and close gedit. Now do:```
sudo su
echo "blacklist hp-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and let us have your (good) report.

---

### Post by louisgonick on 2012-02-23
> **chili555 said:**
> Please try this:Change it to:```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

[COLOR="Red"]modprobe -r[/COLOR] ath5k
rfkill unblock all
modprobe ath5k 

exit 0
```Proofread carefully, save and close gedit. Now do:```
sudo su
echo "blacklist hp-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and let us have your (good) report.

So far it works... I will test it tomorrow with other networks. 

Thanks in advance

---

### Post by wildmanne39 on 2012-02-24
Hi, I am glad it  looks like it is working.

Thank you chili555.

---

### Post by chili555 on 2012-02-24
My pleasure, Wild Man! hp-wmi is always a little suspect.> 0: [COLOR="Red"]hp-wifi[/COLOR]: Wireless LAN
	Soft blocked: no
	[COLOR="Red"]Hard blocked: yes[/COLOR]

---

