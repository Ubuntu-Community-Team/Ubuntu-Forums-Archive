---
title: "No Wireless Networks"
date: 2011-07-29
forum: General Help
---

### Post by Snigglechop on 2011-07-29
Hi guys, I'm REALLY super new here... I need help with a BIG problem (for me that is...) So I click the little icon (I think it's called Network Management?) to selct my home wireless network and it's doesn't show ANY wireless networks what so ever! Can someone PLEASE be kind enough to help a Ubuntu newbie like me?

---

### Post by TeoBigusGeekus on 2011-07-30
Have you checked in additional drivers about whether there is a proprietary driver for your wireless card?

---

### Post by Snigglechop on 2011-07-30
> **TeoBigusGeekus said:**
> Have you checked in additional drivers about whether there is a proprietary driver for your wireless card?
 
When I click "Additional Drivers" it shows absolutley NOTHING. But I can find out my Wireless Card type if that would help.:)

---

### Post by dim_hyder on 2011-07-30
Is the wireless network setup with SSID (the name of the wireless network) to broadcast or hidden?

---

### Post by Snigglechop on 2011-07-30
> **dim_hyder said:**
> Is the wireless network setup with SSID (the name of the wireless network) to broadcast or hidden?
 I'm not sure... It just says "Wireless Networks" in dark letters so I can't click on it. So I don't know if they are hidden or not because I cannot access the wirless networks...:confused:

---

### Post by flipper T on 2011-07-30
have you turned your wireless on ?

might seem like a silly question, but is often the answer

eg on my laptop i have to press fn & f11 to enable the wireless

:)

---

### Post by Snigglechop on 2011-07-30
> **flipper T said:**
> have you turned your wireless on ?
 
might seem like a silly question, but is often the answer
 
eg on my laptop i have to press fn & f11 to enable the wireless
 
:)
 fn? That's a key?

---

### Post by lisati on 2011-07-30
> **Snigglechop said:**
> fn? That's a key?

Yup. On my laptop, it's between the left-ctrl and "Windows" keys.

---

### Post by Snigglechop on 2011-07-30
> **lisati said:**
> Yup. On my laptop, it's between the left-ctrl and "Windows" keys.
 Oh... Then I don't have it. I just have a basic Dell keyboard.

---

### Post by IWantFroyo on 2011-07-30
Copy and paste this into the "Terminal" app (ctrl-alt-t to get to it more easily), and post the output here.
```
lspci | grep -i net
```

---

### Post by Snigglechop on 2011-08-03
> **flipper T said:**
> have you turned your wireless on ?
 
might seem like a silly question, but is often the answer
 
eg on my laptop i have to press fn & f11 to enable the wireless
 
:)
 Is there a terminal command to turn the wireless on?

---

### Post by flipper T on 2011-08-03
rfkill list all

this will tell you if wireless is enabled

output should look like this:


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

### Post by Snigglechop on 2011-08-03
> **flipper T said:**
> rfkill list all
 
this will tell you if wireless is enabled
 
output should look like this:
 
 
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
 OK so I know my wireless in enabled... Now I just need to find a way to get Ubuntu to show my networks.

---

### Post by wildmanne39 on 2011-08-03
Hi, you need to run these commands so we can help you.
```
sudo lshw -C network
```
```
lspci -nn | grep 0280
```
```
lsmod
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

### Post by Snigglechop on 2011-08-03
> **wildmanne39 said:**
> Hi, you need to run these commands so we can help you.
```
sudo lshw -C network
```
```
lspci -nn | grep 0280
```
```
lsmod
```
```
iwconfig
```
```
rfkill list all
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you
 Uh, Hi I eneterd your codes into terminal and got 2 pages worth of codes (I printed them). Now one problem. I cannot copy and paste the codes... I do Ctrl + C on the codes while highlited, switch to Windows (that's how I am writing this reply) try, Ctrl + V and nothing shows up!??? I'm not sure what I should do...

---

### Post by wildmanne39 on 2011-08-03
Hi, you will need to put them on a usb stick then when you boot windows you  can copy and paste them here.

---

### Post by IWantFroyo on 2011-08-03
Ctrl+Shift+C to copy from command line. Put the code in gedit and onto a USB.

---

### Post by Snigglechop on 2011-08-03
> **wildmanne39 said:**
> Hi, you need to run these commands so we can help you.
```
sudo lshw -C network
```
```
lspci -nn | grep 0280
```
```
lsmod
```
```
iwconfig
```
```
rfkill list all
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you
 
Here you go: 
[SIZE=3][FONT=Batang] [/FONT][/SIZE]```
 
*-network               
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@0000:01:0a.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:18 memory:fd9fe000-fd9fffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1d:60:d6:28:8f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

```
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
```
 
Hardware Lister (lshw) - B.02.15
usage: lshw [-format] [-options ...]
       lshw -version
 
            -version        print program version (B.02.15)
 
format can be
            -html           output hardware tree as HTML
            -xml            output hardware tree as XML
            -short          output hardware paths
            -businfo        output bus information
 
options can be
            -class CLASS    only show a certain class of hardware
            -C CLASS        same as '-class CLASS'
            -c CLASS        same as '-class CLASS'
            -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
            -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
            -quiet          don't display status
            -sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
            -numeric        output numeric IDs (for PCI, USB, etc.)

```
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
```
 
Module                  Size  Used by
parport_pc             32111  0
ppdev                  12849  0
dm_crypt               22463  0
lp                     13349  0
parport                36746  3 parport_pc,ppdev,lp
binfmt_misc            13213  1
snd_hda_codec_realtek   255820  1
snd_hda_intel          24140  2
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
arc4                   12473  2
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
b43                   296610  0
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              257001  1 b43
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              156212  2 b43,mac80211
psmouse                73312  0
soundcore              12600  1 snd
k8temp                 12872  0
serio_raw              12990  0
i2c_nforce2            12906  0
dcdbas                 14054  0
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
squashfs               35973  1
aufs                  159344  4221
nls_utf8               12493  1
isofs                  39571  1
nls_iso8859_1          12617  1
nls_cp437              12751  1
vfat                   17335  1
fat                    55505  1 vfat
jfs                   174783  0
xfs                   735018  0
exportfs               12870  1 xfs
reiserfs              234405  0
dm_raid45              88410  0
xor                    21860  1 dm_raid45
btrfs                 527341  0
zlib_deflate           26594  1 btrfs
libcrc32c              12543  1 btrfs
usbhid                 41704  0
hid                    77084  1 usbhid
usb_storage            43946  1
uas                    17676  0
nouveau               621970  2
ttm                    65184  1 nouveau
drm_kms_helper         40745  1 nouveau
drm                   180037  4 nouveau,ttm,drm_kms_helper
pata_amd               13762  0
ssb                    45942  1 b43
sata_nv                23176  1
i2c_algo_bit           13184  1 nouveau
video                  18951  1 nouveau
forcedeth              58190  0

```[FONT=Batang][SIZE=3] [/SIZE][/FONT]
```
 
lo        no wireless extensions.
 
eth0      no wireless extensions.
 
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```[FONT=Batang][SIZE=3]          [/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
```
 
0: phy0: Wireless LAN
            Soft blocked: no
            Hard blocked: no

```
Hope this helps!

---

### Post by flipper T on 2011-08-03
read this

it seems relevant

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by wildmanne39 on 2011-08-03
Hi, what version of ubuntu are you using?

Where did you install the broadcom drivers from?

Please run these commands and post the out put here.
```
nm-tool
```
```
lspci -nn | grep -e 0280 -e 0200
```
```
ls /lib/firmware/b43
```
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
dmesg | grep b43
```
```
lsmod | grep b43
```
```
nm-tool
```
The reason I gave you so many commands at one time is so you will have to switch between windows and ubuntu less.

Just copy and paste the commands that way you make sure they are correct.
Thank you

---

### Post by 3rdalbum on 2011-08-03
Just about the suggestion of using the Additional Drivers program: You need an internet connection in order for drivers to be found and downloaded. You can just plug your computer into your modem via the Ethernet port to get an internet connection, and this will allow you to look for a driver in Additional Drivers.

---

