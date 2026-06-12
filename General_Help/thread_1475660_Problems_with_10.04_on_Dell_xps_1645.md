---
title: "Problems with 10.04 on Dell xps 1645"
date: 2010-05-07
forum: General Help
---

### Post by BlueDandelion on 2010-05-07
Hi Guys,

I have a new Dell xps 1645 and several issues when running Kubuntu 10.04!

1. Wireless only when I first boot Windows then turn on wireless reboot and reboot to Kubuntu. Know wireless works fine I have good signal strength. As soon as I turn wireless off via the soft button I get get it back on! I activated the broadcom STA wireless drivers in System -> Hardware Drivers!

2. I can't get Compositing to work! I always get the note that Compositing has been suspended by another program. Opengl works fine, I can run glxgears. I also tried some games they run with up to 60 fps. Here I also activated the ATI/AMD proprietary FGLRX graphics drivers in System -> Hardware Drivers 

How can I get these things to work?

I hope someone can help!

Greetiings

---

### Post by Isidith on 2010-05-07
Hi,

Run lsmod and check if 'wl' is here.
If it's not you should add it to /etc/modules like this for example :

```

echo wl | sudo tee -a /etc/modules


```The correct module should now be loaded at startup.

I.

---

### Post by BlueDandelion on 2010-05-07
thanks for the replay!

wl is there

here the lsmod output:

```

Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_atihdmi     2367  1 
snd_hda_codec_idt      51914  1 
snd_hda_intel          22005  3 
snd_hda_codec          74201  3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70886  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lib80211_crypt_tkip     7596  0 
joydev                  8708  0 
fbcon                  35102  71 
snd                    54148  18 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tileblit                2031  1 fbcon
fglrx                2093229  31 
wl                   1959630  0 
soundcore               6620  1 snd
font                    7557  1 fbcon
dell_wmi                1793  0                                                                                                                                                                                                                    
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm                                                                                                                                                                                              
bitblit                 4707  1 fbcon                                                                                                                                                                                                              
sdhci_pci               5502  0                                                                                                                                                                                                                    
sdhci                  15654  1 sdhci_pci                                                                                                                                                                                                          
led_class               2864  1 sdhci                                                                                                                                                                                                              
uvcvideo               57022  0                                                                                                                                                                                                                    
videodev               34361  1 uvcvideo                                                                                                                                                                                                           
psmouse                63245  0                                                                                                                                                                                                                    
v4l1_compat            13251  2 uvcvideo,videodev                                                                                                                                                                                                  
serio_raw               3978  0                                                                                                                                                                                                                    
agpgart                31788  1 fglrx                                                                                                                                                                                                              
video                  17375  0                                                                                                                                                                                                                    
softcursor              1189  1 bitblit                                                                                                                                                                                                            
dell_laptop             6856  0                                                                                                                                                                                                                    
lib80211                5046  2 lib80211_crypt_tkip,wl                                                                                                                                                                                             
vga16fb                11385  1                                                                                                                                                                                                                    
vgastate                8961  1 vga16fb                                                                                                                                                                                                            
output                  1871  1 video                                                                                                                                                                                                              
dcdbas                  5490  1 dell_laptop                                                                                                                                                                                                        
lp                      7028  0                                                                                                                                                                                                                    
parport                32635  2 ppdev,lp                                                                                                                                                                                                           
usbhid                 36174  0                                                                                                                                                                                                                    
hid                    67032  1 usbhid                                                                                                                                                                                                             
ohci1394               27238  0                                                                                                                                                                                                                    
ahci                   32040  3                                                                                                                                                                                                                    
tg3                   109580  0                                                                                                                                                                                                                    
ieee1394               81213  1 ohci1394  

```

---

### Post by LordSavage on 2010-05-10
I have the same problem with ubuntu 10.04. Is there a solution?

---

### Post by om26er on 2010-05-12
you could try installing the latest kernel that might be helpful [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/)

---

