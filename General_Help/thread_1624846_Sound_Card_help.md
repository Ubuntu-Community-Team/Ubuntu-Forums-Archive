---
title: "Sound Card help"
date: 2010-11-18
forum: General Help
---

### Post by DWL52 on 2010-11-18
Hello All. I'm new to Ubuntu and need some help. I'm trying to configure the program gMFSK, which will allow me to work Amateur Radio digital modes. I have a SignaLink USB interface, which has its own internal soundcard, between the computer and the radio. From the desktop, I go into System-Preferences-Sound and click on the Hardware tab. It shows the SignaLink sound card as:

PCM2904 Audio Codec
1 output/1 input
Analog Stereo Duplex

When I check the "test Speakers" box and and run the test, the SignaLink keys the radio, so I know the computer, interface and radio are talking.The problem arises when I load the gMFSK program. I immediately get the message:

sound_open_for_read: opensnd: open: /dev/dsp: no such file or directory

When I go into gMFSK Settings-Preferences and look at sound card device, the options are /dev/dsp, /dev/dsp0, /dev/dps1 and /dev/dsp2. The requested sample rate default is 8000, the TX rate offset and RX rate offset are both 0, and Stereo Sound I/O is checked. I've tried all posssible combinations on this screen, clicking the "reset modem"  button after every change, but getting nothing on the watterfall. Any and all help would be greatly appreciated.

---

