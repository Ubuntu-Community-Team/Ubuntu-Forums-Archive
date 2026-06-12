---
title: "Patch failure on bcm43xx drivers.../cry"
date: 2011-07-08
forum: General Help
---

### Post by Spetsnazos on 2011-07-08
I just can't seem to overcome this issue....

I downloaded the LatinSud patch from
[http://www.latinsud.com/bcm/bcm43xx-injection-linux-2.6.20.patch](http://www.latinsud.com/bcm/bcm43xx-injection-linux-2.6.20.patch)

I set up a repository to download bcm43xx-fwcutter
I downloaded wl_apsta-3.130.20.0.o

I couldn't find for the life of me find linux-source-2.6.20 but I did have the repository for 2.6.38 so I did this.
#sudo apt-get install linux-source-2.6.38 build-essential gawk

I then did the following
#cd /usr/src/
#tar jxvf linux-source-2.6.38.tar.bz2

At this point I got a whole ton of response that said

"Cannot open: No such file or directory"
"Cannot mkdir: Permission denied"

Pretty much got spammed with that for like a couple hundred files/folders.

I knew something was wrong but I kept going(lol).

#cd linux-source-2.6.38
#sudo cp ~/bcm43xx-injection-linux-2.6.22.patch bcm43xx-injection-linux-2.6.22.patch
#sudo cp ../linux-headers-2.6.38-8-generic/.config .config
#sudo patch -p1 -i bcm43xx-injection-linux-2.6.22.patch

This is where the fail happened

Hunk#1 FAILED at 104.
Hunk#1 FAILED at 3365.
Hunk#1 FAILED at 3636.
Hunk#1 FAILED at 3645.
Hunk#1 FAILED at 3892.
5 out of 5 hunks FAILED -- saving rejects to file drivers/net/wireless/bcm43xx/bcm43xx_main.c.rej

Hunk #1 FAILED at 352

1 out of 1 hunks FAILED --saving rejects...


LOL Any tips guys?  Maybe I should try the Broadcom b34 drivers instead with b34 fwcutter?  I'm not quite sure how to clean up all the folders now where I spammed all this patch stuff incase I wanted to try it again?

<3 you forever if you can help

---

### Post by Spetsnazos on 2011-07-08
shameless bump been trying more stuff and nothing works

---

### Post by ruffEdgz on 2011-07-08
Well it seems that the extraction of the tar file failed which would mean everything below wouldn't work. Who owns the file 'linux-source-2.6.38.tar.bz2'? It just sounds like you need more permissions to create directories and anything else needed to extract that tarball.
```

ll /usr/src/linux-source-2.6.38.tar.bz2

```

But before you use the downloaded one, did you see if the repo could help you in this part?
```

sudo apt-cache search linux-source

```
When I did a search on my 11.04 laptop, I noticed it had the version you downloaded and could help with making this task a bit easier.

Cheers!

---

### Post by Spetsnazos on 2011-07-08
> **ruffEdgz said:**
> Well it seems that the extraction of the tar file failed which would mean everything below wouldn't work. Who owns the file 'linux-source-2.6.38.tar.bz2'? It just sounds like you need more permissions to create directories and anything else needed to extract that tarball.
```

ll /usr/src/linux-source-2.6.38.tar.bz2

```

But before you use the downloaded one, did you see if the repo could help you in this part?
```

sudo apt-cache search linux-source

```
When I did a search on my 11.04 laptop, I noticed it had the version you downloaded and could help with making this task a bit easier.

Cheers!

When I typed
#sudo apt-cache search linux-source

I got

linux-source-2.6.38 - Linux kernel source for version 2.6.38 with Ubuntu Patches
linux-source-2.6.15 - Linux kernel source for version 2.6.15 with Ubuntu Patches

---

### Post by Spetsnazos on 2011-07-08
when i typed in 

#ll /usr/src/linux-source-2.6.38.tar.bz2

THe archive manager opened and I opened up that specific tar file.  Inside I found all the necessary files.

I thought that with Linux I have full permission if I do sudo?

---

### Post by Spetsnazos on 2011-07-08
Anyone know why it would tell me permission denied?  Am I not able to write to the src directory?

---

### Post by Spetsnazos on 2011-07-08
The most bizarre thing just happened...
I just typed
#sudo tar jxvf linux-source-2.6.38.tar.bz2

and it worked...lol.

Time to try to patch again!

---

### Post by Spetsnazos on 2011-07-08
$ sudo patch -p1 -i bcm43xx-injection-linux-2.6.20.patch
patching file drivers/net/wireless/bcm43xx/bcm43xx_main.c
Hunk #1 FAILED at 104.
Hunk #2 FAILED at 3365.
Hunk #3 FAILED at 3636.
Hunk #4 FAILED at 3645.
Hunk #5 FAILED at 3892.
5 out of 5 hunks FAILED -- saving rejects to file drivers/net/wireless/bcm43xx/bcm43xx_main.c.rej
patching file drivers/net/wireless/bcm43xx/bcm43xx_xmit.c
Hunk #1 FAILED at 352.
1 out of 1 hunk FAILED -- saving rejects to file drivers/net/wireless/bcm43xx/bcm43xx_xmit.c.rej

Got that...

Not even sure where to go from here?  Tempted to just uninstall ubuntu and reinstall all over and try from scratch??

---

### Post by Spetsnazos on 2011-07-08
shameless bump

---

### Post by westie457 on 2011-07-08
Hi being curious about why you are patching drivers and have no idea how to do this.

Are you having problems setting up your wireless?
Also what Broadcom chip do you have?

---

### Post by wildmanne39 on 2011-07-08
> **Spetsnazos said:**
> shameless bump
Hi, I do not think you need to patch, you are just making things harder then they have to be, put these coomands in a terminal 
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
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by Spetsnazos on 2011-07-08
> **westie457 said:**
> Hi being curious about why you are patching drivers and have no idea how to do this.

Are you having problems setting up your wireless?
Also what Broadcom chip do you have?

my chipset for Broadcom is BCM4313.  I am doing all this so I can go into monitored mode on my card.  My wireless works just fine but its in managed mode.

---

### Post by wildmanne39 on 2011-07-08
> **Spetsnazos said:**
> my chipset for Broadcom is BCM4313.  I am doing all this so I can go into monitored mode on my card.  My wireless works just fine but its in managed mode.
Hi, ok sorry I thought it was not working.

---

### Post by Spetsnazos on 2011-07-08
> **wildmanne39 said:**
> Hi, I do not think you need to patch, you are just making things harder then they have to be, put these coomands in a terminal 
```
sudo lshw -C network
``````
lspci -nn
``````
iwconfig
``````
lsmod
```and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

incase tis might help someone else figure my issue out

$sudo lshw -C network
```

  *-network               
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 48:5d:60:2a:90:46
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcm80211 driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fbffc000-fbffffff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 20:cf:30:6f:3c:fc
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:f7fc0000-f7ffffff ioport:ec00(size=128)

```

$lspci -nn
```

00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA AHCI Controller [8086:27c1] (rev 02)
01:00.0 Ethernet controller [0200]: Atheros Communications AR8132 Fast Ethernet [1969:1062] (rev c0)
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

```

$iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

```

$lsmod

```
Module                  Size  Used by
joydev                 17606  0 
parport_pc             36959  0 
ppdev                  17113  0 
arc4                   12529  2 
binfmt_misc            17565  1 
snd_hda_codec_realtek   336693  1 
snd_hda_intel          33211  2 
snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
eeepc_wmi              19323  0 
sparse_keymap          13898  1 eeepc_wmi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
brcm80211             748941  0 
i915                  514985  3 
snd_timer              29602  2 snd_pcm,snd_seq
mac80211              294370  1 brcm80211
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               72195  0 
snd                    67382  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
psmouse                73535  0 
drm_kms_helper         42136  1 i915
cfg80211              178528  2 brcm80211,mac80211
serio_raw              13166  0 
drm                   227495  4 i915,drm_kms_helper
i2c_algo_bit           13400  1 i915
video                  19438  1 i915
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
ahci                   25951  2 
libahci                26642  1 ahci
atl1c                  41171  0 
```

---

### Post by Spetsnazos on 2011-07-08
This whole thing just got personal :) I will defeat you Linux!! <3

---

### Post by westie457 on 2011-07-08
May be this will be of some use to you [http://ubuntuforums.org/showthread.php?t=539385](http://ubuntuforums.org/showthread.php?t=539385)

---

### Post by Spetsnazos on 2011-07-11
shameless bump just reinstalled Ubuntu 11.04 because I couldn't even connect to the internet anymore after trying all sorts of stuff 

:)

---

