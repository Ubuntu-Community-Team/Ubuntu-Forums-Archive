---
title: "Help - Networking"
date: 2010-08-02
forum: General Help
---

### Post by Quarkrad on 2010-08-02
I did clean install of 10.04 the week it came out and all has been fine except randomly after 10 minutes or so my wireless connection drops out.  I have installed WICD but it has made no difference.  The way I have restored the connection is to restart the machine.  I thought about killing and restarting 'networking' via the terminal to save the switch off/on.   I found this command via google:  **sudo  etc/init.d/networking restart**  but when I try this terminal tells me Command not found.  I have also tried sudo etc/init.d/networking stop  but again, command not found.   My USB wireless card is a Sweetx model and has worked like a rock since I first use Ubuntu with 8.04.  Any advice much appreciated (newbie user!).

---

### Post by deathadder on 2010-08-02
> **Quarkrad said:**
> **sudo  etc/init.d/networking restart**  
If that's a straight copy and paste then the command is wrong, you're missing the leading slash. You command should be:
```
sudo /etc/init.d/networking restart
```
Can you provide some more information about the wireless card, the module (driver) used (if you're not sure post the output of the lsmod command).

---

### Post by Quarkrad on 2010-08-02
Thank you for your help.  The command with the extra slash worked - the output of my lsmod is:

Module                  Size  Used by
aes_i586                7268  2 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
arc4                    1153  2 
snd_hda_codec_realtek   203310  1 
snd_hda_intel          21941  0 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
rt73usb                22434  0 
crc_itu_t               1371  1 rt73usb
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
ppdev                   5259  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  12 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rt2500usb              18141  0 
rt2x00usb               9703  2 rt73usb,rt2500usb
rt2x00lib              27509  3 rt73usb,rt2500usb,rt2x00usb
led_class               2864  1 rt2x00lib
mac80211              205146  2 rt2x00usb,rt2x00lib
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
cfg80211              126517  2 rt2x00lib,mac80211
joydev                  8708  0 
parport_pc             25962  1 
psmouse                63245  0 
serio_raw               3978  0 
i2c_viapro              5573  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
nvidia               9961216  48 
via_agp                 5310  1 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
shpchp                 28820  0 
agpgart                31724  2 nvidia,via_agp
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usb_storage            39425  0 
usbhid                 36110  0 
hid                    67032  1 usbhid
ohci1394               26950  0 
floppy                 53016  0 
pata_via                7272  0 
sata_via                6945  2 
via_rhine              19154  0 
mii                     4381  1 via_rhine
ieee1394               81181  1 ohci1394

---

### Post by Quarkrad on 2010-08-02
My winxp side shows the card as RT73 USB Wireless Network Card with the appropriate win driver.  I notice I have a number of instances listed:


rt73usb                22434  0 
crc_itu_t               1371  1 rt73usb
rt2x00usb               9703  2 rt73usb,rt2500usb
rt2x00lib              27509  3 rt73usb,rt2500usb,rt2x00usb

---

### Post by Quarkrad on 2010-08-02
This may be relevant - I think this is incorrect.  When I installed WICD I still had the original Network Applet 0.8 sowing in the top panel.  It appears to me I have both WICD and gnome(?) network manager working.  Infact I have just quit WICD and am mailing this through the original network manager applet.

---

### Post by Quarkrad on 2010-08-08
Bump - I'm still getting random disconnects.  Can anybody help?

---

