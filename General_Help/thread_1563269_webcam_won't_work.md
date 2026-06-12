---
title: "webcam won't work"
date: 2010-08-28
forum: General Help
---

### Post by a sandwhich on 2010-08-28
Hello, I have a logitech quickcam orbitsphere af webcam. I already have skype installed, every time I try to use it skype crashes or something. How can I get it to work?

---

### Post by Baldrick_NZ on 2010-08-28
> **a sandwhich said:**
> Hello, I have a logitech quickcam orbitsphere af webcam. I already have skype installed, every time I try to use it skype crashes or something. How can I get it to work?

Might be a good idea to see whether you webcam works under another program like 'cheese' before going any further. This would then prove if your system sees the webcam. Alternatively, you could post the result of running lspci in terminal.

---

### Post by a sandwhich on 2010-08-29
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:06.0 Network controller: Atheros Communications Inc. AR922X Wireless Network Adapter (rev 01)
01:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
02:00.0 VGA compatible controller: nVidia Corporation GT215 [GeForce GT 240] (rev a2)
02:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)

---

### Post by anubhavrocks on 2010-08-29
> **a sandwhich said:**
> Hello, I have a logitech quickcam orbitsphere af webcam. I already have skype installed, every time I try to use it skype crashes or something. How can I get it to work?

Can you use the following command from terminal to run skype:
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

---

### Post by a sandwhich on 2010-08-29
it returned an error but skype did run.

---

### Post by anubhavrocks on 2010-08-29
I guess you are missing the library.

Use this command to install:
sudo apt-get install libv4l-0

Once this is complete try out the command in the prev post.

---

### Post by a sandwhich on 2010-08-29
kevin@kevin-desktop:~$ sudo apt-get install libv4l-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libv4l-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kevin@kevin-desktop:~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

Once the error came up the skype window popped up infront of the terminal. The error message is the same as the one before. cheese does not recognize my webcam

---

### Post by anubhavrocks on 2010-08-29
Are you using a 64bit Ubuntu?

---

### Post by a sandwhich on 2010-08-29
64 bit ubuntu studio. I also have vista installed on another drive. The webcam works fine in vista. When i try to accept a call in skype the indicator light on the cam goes active for 2 seconds then stops and skype crashes

---

### Post by anubhavrocks on 2010-08-29
Okay you need to install the 32 bit libv4l
sudo apt-get install lib32v4l-0 

And use this command:
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

---

### Post by a sandwhich on 2010-08-29
it said the 32 bit was already installed. Webcam still didn't work. Skype didn't crash though.

---

### Post by anubhavrocks on 2010-08-29
Does your webcam work with cheese?
Also post the outputs of 
lsub
lsmod

---

### Post by a sandwhich on 2010-08-29
no it says device not found

---

### Post by anubhavrocks on 2010-08-29
Seems like the webcam is not supported, anyways can you post outputs of 
lsub
lsmod

---

### Post by a sandwhich on 2010-08-29
kevin@kevin-desktop:~$ lsusb
Bus 002 Device 007: ID 0a5c:2148 Broadcom Corp. 
Bus 002 Device 006: ID 0a5c:4503 Broadcom Corp. 
Bus 002 Device 005: ID 0a5c:4502 Broadcom Corp. 
Bus 002 Device 004: ID 04b9:0300 Rainbow Technologies, Inc. SafeNet USB SuperPro/UltraPro
Bus 002 Device 003: ID 046d:c526 Logitech, Inc. MX Revolution Cordless Mouse
Bus 002 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
Bus 001 Device 005: ID 15a9:0004  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
kevin@kevin-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc             7960  1 
rfcomm                 40393  4 
sco                     9617  2 
ppdev                   6375  0 
bridge                 53184  0 
stp                     2171  1 bridge
bnep                   11884  2 
l2cap                  34806  16 rfcomm,bnep
snd_hda_codec_realtek   279040  1 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
arc4                    1473  2 
snd_hda_intel          25677  2 
snd_pcm_oss            41394  0 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_mixer_oss          16299  1 snd_pcm_oss
snd_hwdep               6924  1 snd_hda_codec
snd_pcm                87882  3 snd_hda_intel,snd_pcm_oss,snd_hda_codec
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
ath9k                 328989  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              238448  1 ath9k
ath                     9723  1 ath9k
snd                    71106  17 snd_hda_codec_realtek,snd_hda_intel,snd_pcm_oss,snd_hda_codec,snd_mixer_oss,snd_hwdep,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8052  1 snd
cfg80211              148546  3 ath9k,mac80211,ath
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
btusb                  12969  2 
bluetooth              58685  9 rfcomm,sco,bnep,l2cap,btusb
joydev                 11072  0 
usbhid                 41084  0 
led_class               3764  1 ath9k
hid                    83440  1 usbhid
edac_core              45423  0 
edac_mce_amd            9278  0 
nouveau               515227  2 
ttm                    60847  1 nouveau
drm_kms_helper         30742  1 nouveau
i2c_nforce2             6099  0 
drm                   199268  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit            6024  1 nouveau
ndiswrapper           244768  0 
lp                      9336  0 
parport                37160  2 ppdev,lp
usb_storage            49833  0 
ohci1394               30260  0 
forcedeth              55592  0 
pata_amd               11962  0 
ieee1394               94771  1 ohci1394
sata_nv                23778  3 
kevin@kevin-desktop:~$ 


The camera is on the uvc supported devices list so im assuming it will work.

---

### Post by anubhavrocks on 2010-08-29
Very strange lsusb should be listing your webcam.Somehow i do not see that.

This is a USB webcam right?

---

### Post by a sandwhich on 2010-08-29
Correct. The logitech orbitsphere af

---

### Post by anubhavrocks on 2010-08-29
Can you unplug and plug it in again.Then try lsusb.

lsusb should atleast list the device.

---

### Post by a sandwhich on 2010-08-29
Nope. Nothing different. The usb port is functioning. I checked

---

### Post by anubhavrocks on 2010-08-29
Can you post the output of
dmesg|tail -n10

---

### Post by a sandwhich on 2010-08-29
[13108.579193] composite sync not supported
[13109.148706] composite sync not supported
[13127.274264] operapluginwrap[6995]: segfault at 0 ip (null) sp 00007fff769bbb88 error 14 in operapluginwrapper-native[400000+31000]
[13127.316333] operapluginwrap[7011]: segfault at 0 ip (null) sp 00007fff1e322eb8 error 14 in operapluginwrapper-native[400000+31000]
[13127.358878] operapluginwrap[7028]: segfault at 0 ip (null) sp 00007fff11535698 error 14 in operapluginwrapper-native[400000+31000]
[13127.399909] operapluginwrap[7044]: segfault at 0 ip (null) sp 00007fff140b3418 error 14 in operapluginwrapper-native[400000+31000]
[13127.477655] operapluginwrap[7076]: segfault at 0 ip (null) sp 00007fff21591218 error 14 in operapluginwrapper-native[400000+31000]
[13127.519940] operapluginwrap[7092]: segfault at 0 ip (null) sp 00007fffc0e26168 error 14 in operapluginwrapper-native[400000+31000]
[13127.562119] operapluginwrap[7108]: segfault at 0 ip (null) sp 00007fffe44365e8 error 14 in operapluginwrapper-native[400000+31000]
[13127.603347] operapluginwrap[7124]: segfault at 0 ip (null) sp 00007fff13fe0fb8 error 14 in operapluginwrapper-native[400000+31000]

---

### Post by anubhavrocks on 2010-08-29
Can you try this command:
modprobe uvcvideo

---

### Post by a sandwhich on 2010-08-29
kevin@kevin-desktop:~$ modprobe uvcvideo
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: Error inserting v4l1_compat (/lib/modules/2.6.32-24-generic/kernel/drivers/media/video/v4l1-compat.ko): Operation not permitted
WARNING: Error inserting videodev (/lib/modules/2.6.32-24-generic/kernel/drivers/media/video/videodev.ko): Operation not permitted
FATAL: Error inserting uvcvideo (/lib/modules/2.6.32-24-generic/kernel/drivers/media/video/uvc/uvcvideo.ko): Operation not permitted
kevin@kevin-desktop:~$

---

### Post by anubhavrocks on 2010-08-29
You need super user privileges to insert module:
 
sudo modprobe uvcvideo

After doing this post the output of:
dmesg|tail -n20

---

### Post by a sandwhich on 2010-08-29
kevin@kevin-desktop:~$ sudo modprobe uvcvideo
[sudo] password for kevin: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
kevin@kevin-desktop:~$ dmesg|tail -n20
[13063.737680] composite sync not supported
[13065.027040] composite sync not supported
[13066.298279] composite sync not supported
[13066.869643] composite sync not supported
[13105.270673] composite sync not supported
[13105.988267] composite sync not supported
[13107.287301] composite sync not supported
[13108.579193] composite sync not supported
[13109.148706] composite sync not supported
[13127.274264] operapluginwrap[6995]: segfault at 0 ip (null) sp 00007fff769bbb88 error 14 in operapluginwrapper-native[400000+31000]
[13127.316333] operapluginwrap[7011]: segfault at 0 ip (null) sp 00007fff1e322eb8 error 14 in operapluginwrapper-native[400000+31000]
[13127.358878] operapluginwrap[7028]: segfault at 0 ip (null) sp 00007fff11535698 error 14 in operapluginwrapper-native[400000+31000]
[13127.399909] operapluginwrap[7044]: segfault at 0 ip (null) sp 00007fff140b3418 error 14 in operapluginwrapper-native[400000+31000]
[13127.477655] operapluginwrap[7076]: segfault at 0 ip (null) sp 00007fff21591218 error 14 in operapluginwrapper-native[400000+31000]
[13127.519940] operapluginwrap[7092]: segfault at 0 ip (null) sp 00007fffc0e26168 error 14 in operapluginwrapper-native[400000+31000]
[13127.562119] operapluginwrap[7108]: segfault at 0 ip (null) sp 00007fffe44365e8 error 14 in operapluginwrapper-native[400000+31000]
[13127.603347] operapluginwrap[7124]: segfault at 0 ip (null) sp 00007fff13fe0fb8 error 14 in operapluginwrapper-native[400000+31000]
[15218.235627] Linux video capture interface: v2.00
[15218.249610] usbcore: registered new interface driver uvcvideo
[15218.249675] USB Video Class driver (v0.1.0)
kevin@kevin-desktop:~$

---

### Post by anubhavrocks on 2010-08-29
Somehow the Operating system is not detecting the webcam at all.Are you sure it works?The cable etc. is all right.

---

### Post by anubhavrocks on 2010-08-29
Try a different USB port.See if that helps.

---

### Post by a sandwhich on 2010-08-29
let me reboot into vista to double check.

---

### Post by a sandwhich on 2010-08-29
Wow I hate vista. Takes 15 min to boot, misconfigures montiors, and returns 36 errors. Webcam works. Booted into ubuntu. cam works now. Strange.

---

### Post by a sandwhich on 2010-08-29
I can use cheese and guvcvideo but whenever skype tries to it crashes.

---

### Post by no2498 on 2010-08-29
read the cheese help faq's if it stops working

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype


did you try that yet ?

---

### Post by a sandwhich on 2010-08-29
Just did. I cannot see my own video but the person on the other end can see the video. It doesn't crash. Does this mean i have to launch skype taht way all the time?

---

### Post by a sandwhich on 2010-08-29
skype does not transmit any audio but it does transmit video.

---

### Post by anubhavrocks on 2010-08-29
See if you find this helpful:
[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

---

### Post by a sandwhich on 2010-08-29
links broken

---

### Post by no2498 on 2010-08-30
re try his link it worked for me

an yes till you can make the file
an for the audio i cant help you with it


an glad you got it somewhat working

---

