---
title: "unknown monitor in ubuntu 11.10 (i have lg monior)"
date: 2011-11-22
forum: General Help
---

### Post by y_garti on 2011-11-22
hi 

i installed Ubuntu 11.10 on a clean computer but i have some drivers problem
i don't know how to install the display driver and i cannot change the resultion (i dont care about 3d or gaming) all i want is a bigger resolution   which i know my display adapter and monitor can handle (i am using kvm )


i am sure that there is a file that i need to change or a command that i need to run (or to install a better generic display driver)  but i really don't know how to do this 

waiting for some help
THANK YOU :)

---

### Post by y_garti on 2011-11-22
i frogot to say that i am using lenovo thinkcentre with Intel HD graphics display adapter

:)

---

### Post by efflandt on 2011-11-22
What is the make/model of your monitor or its native resolution and what type of video cable is used to connect it?

DVI (or DVI to HDMI) seem to be the most intelligent about figuring out the best resolution with HDMI a close second (but maybe not all of monitor's modes).

VGA is often unaware of native resolution or best mode and may only come up with some default modes that are not optimum.  As a start see what **xrandr -q** shows about your current video modes.

I am not familiar with Intel HD video, but if xrandr displays modes without any errors see [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) especially the part about adding undetected resolutions at [https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions)

---

### Post by Hugh971 on 2011-11-22
There may be a driver available to you through restricted drivers. Have you tried that?

---

### Post by y_garti on 2011-11-23
first of all thank you both for your help

1. i use this command
```
xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
```

but when i ran xrandr i get this

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
  1600x900_60.00 (0xce)  118.2MHz
        h: width  1600 start 1696 end 1856 total 2112 skew    0 clock   56.0KHz
        v: height  900 start  903 end  908 total  934           clock   59.9Hz

my screen is connected throw VGA1
but when i ran 
```
xrandr --output VGA1 --mode 1600x900
```
it doesn't work
i even try this
```
xrandr --output DP1 --mode 1600x900
```
but it write xrandr: cannot find mode 1600x900
help for how to continue from here 

2. i have installed it but i still doesn't help or detect my display adapter or screen

BTW

my display is lg flatron w2243t  which support 1600x900 without any problem on VGA in windows

thank you very much

---

### Post by dandnsmith on 2011-11-23
I'm interested in this problem too - I have observed that when my LG M198WA is connected via DVI, the resolution is at the monitor recommended 1400x900, while connected via VGA it will only give 1024x768. I've also observed that Windows using VGA gives a lower resolution and also only occupies just over 3/4 of the screen width. This is a driver limitation, and I'm extremely reluctant to investigate alternative drivers since those for my hardware have been known to give real trouble.

Have you checked the modules loaded (lsmod)?
Have you investigated alternative drivers?

---

### Post by y_garti on 2011-11-23
1 the only think that i did is the one that is written in this thread
this is the output of lsmod

Module                  Size  Used by
des_generic            21191  0 
md4                    12523  0 
nls_utf8               12493  1 
cifs                  248817  2 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
tpm_tis                14002  0 
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73673  0 
wmi                    18744  0 
i915                  505108  3 
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
mei                    36466  0 
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
hid_logitech           17405  0 
ff_memless             12945  1 hid_logitech
usbhid                 41905  1 hid_logitech
hid                    77367  2 hid_logitech,usbhid
e1000e                139814  0 

if you think that installing a different driver will help I'll be glad to do that (all i need is a little instruction)

BTW on the windows i can use VGA and 1920x1080 but on the Ubuntu all i get is 1024x768 which i know that if i could change I'll will get a better resolutions (but i don't really know how to do that)


thanks

---

### Post by dandnsmith on 2011-11-23
Looks like you're using the i915 chipset driver - and I cannot see anything about alternatives/faults from my google searches.

---

### Post by y_garti on 2011-11-29
dose some one know how to help me or i am doomed to use 1024x768 ;)

---

### Post by h3nning94 on 2011-12-11
I have the same problem, only I'm on a laptop. Monitor unknown, 1024x768 resolution. Native res is 1366x768.

---

### Post by bgrau2000 on 2012-01-09
Well you are lucky, I just manage plain vga 640x480 panned on a LCD using DVI-D with native 1680x1050 !!! go figure... 

so far I tried almost all I know, and it will m=not budge...

I can't even have access to safe console mode!

this really sucks...

> **h3nning94 said:**
> I have the same problem, only I'm on a laptop. Monitor unknown, 1024x768 resolution. Native res is 1366x768.

---

### Post by Mhoz on 2012-02-03
Hi,

 I also have an LG monitor connected through a KVM switch that only displayed 1024x786.
If I connect direct to the monitor without the KVM it works fine, but  thanks to y_garti's post I got it working with the KVM
First create a Modeline:
```

cvt -v 1920 1080
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

```
and then using that info to xrandr
```

xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode VGA1 "1920x1080_60.00"
xrandr --output VGA1 --mode "1920x1080_60.00"

```

Finally back to the right resolution for the screen.

---

