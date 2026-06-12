---
title: "Problems with Ubuntu 11.04 with hp envy 14 [graphics]"
date: 2011-10-08
forum: General Help
---

### Post by Goldenhouse on 2011-10-08
Hello.

I really need to get Ubuntu work properly on my computer. Here are some specifications:
[B]
 HP ENVY 14-2014eo[/B]
[B]Intel® Core&#8482; i7-2630QM (2 GHz)
AMD Radeon HD 6630M-grafik 4 gb DDR3
500 GB SATA
Intecrated 10/100/1000 Gigabit Ethernet LAN
14,5 inch HD LED HP Brightview
Synaptics PS/2 Port ClickPad Series 3.0 - Imaging Sensor[/B]

I think this is all the information you will need to be able to help me.

I have been searching around but I can't find the help I wanted so I thought it would be much easier for me (as a beginner) to write my own post here.

When I start up Ubuntu 11.04 I choose Ubuntu OS (have windows installed on another partition) I get a black screen. I have been able to login sometimes using ctrl + alt + f5 / f7 in the upstart. But I really need to fix the problems with the graphics so I always can login without problem. 

I also need help with fixing my ClickPad, the only thing that is working is left click. Things that is not working with the ClickPad:
- Two finger Scrolling
- Right Click
- Dubbel tap in left corner to turn it off
- It goes crazy if I have two fingers on the pad

And of course the right click option is the most important one to fix of these problems with the mousepad.

There might be another problems to but I really need to fix the graphics problem and clickpad before thinking of them.

Thank you for your help

---

### Post by Goldenhouse on 2011-10-10
Please, I really need help with fixing this...

---

### Post by bigas11 on 2011-10-10
Hello 

I have  a **HP Envy 14-2020ep** Beats Edition and it is the exact same problem. Some one help.


Regards

---

### Post by bigas11 on 2011-10-10
Goldenhouse after some research, i find a temporary solution it works for me.

The idea is use the internal intel graphic, instead the main graphic board ATI HD6630, it works to series HD6XXX too. In new version Ubuntu 11.10 , it should be solve those problems.
[B]
Meanwhile the solution,[/B]

Send radeon to ubuntu blacklist, by editing:
[B]
cd /etc/modprobe.d/
sudo gedit blacklist.conf[/B]

then put this line in the file and save it,
[B]
blacklist radeon[/B]

then,
[B]
cd /etc/
[/B][B]sudo gedit rc.local

[/B]then put this line in the file before "exit 0" and save it,

[B]modprobe radeon
echo OFF> /sys/kernel/debug/vgaswitcheroo/switch[/B]
Then reboot, and you won't have more startup ubuntu problems.

---

### Post by wildmanne39 on 2011-10-11
Hi, if you go with bigas11 solution when you run graphical applications like gedit always use gksudo or gksu so you do not end up with root taking ownership of the application.

To blacklist radeon if that is what you want to do and I am not saying that is the best course of action you can do it with this command:
```
sudo su
echo "blacklist radeon" >> /etc/modprobe.d/blacklist.conf
exit
```

Post here the results of these commands please and maybe someone can help you.
```
lspci | grep VGA
```
```
lsmod
```
click on new reply and click # and paste the information between the brackets.

Also you can use nomodeset to boot ubuntu most likely, then install your video card driver in additional drivers and see if that fixes your problem.

Here is a link for nomodeset.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thank you

---

### Post by Goldenhouse on 2011-10-12
Thank you all. I will try this tonight!

I will report back here and tell you how it works..

---

### Post by Goldenhouse on 2011-10-13
**lspci | grep VGA**
> 00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: ATI Technologies Inc NI Whistler [AMD Radeon HD 6600M Series]
**lsmod**
> Module                  Size  Used by
cryptd                 20510  0 
aes_x86_64             17208  0 
aes_generic            38279  1 aes_x86_64
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     28167  1 
snd_hda_codec_idt      71137  1 
rfcomm                 47694  8 
sco                    18187  2 
bnep                   18308  2 
binfmt_misc            17565  1 
l2cap                  53570  16 rfcomm,bnep
arc4                   12529  2 
snd_hda_intel          33176  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
i915                  515121  3 
iwlagn                333716  0 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
iwlcore               167502  1 iwlagn
btusb                  18600  2 
mac80211              294370  2 iwlagn,iwlcore
hp_wmi                 13706  0 
joydev                 17606  0 
radeon                982152  0 
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
sparse_keymap          13898  1 hp_wmi
bluetooth              72320  9 rfcomm,sco,bnep,l2cap,btusb
ttm                    76664  1 radeon
uvcvideo               72195  0 
videodev               82052  1 uvcvideo
usb_storage            53538  0 
psmouse                73535  0 
cfg80211              178528  3 iwlagn,iwlcore,mac80211
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l2_compat_ioctl32    17078  1 videodev
drm_kms_helper         42136  2 i915,radeon
uas                    17996  0 
drm                   227534  6 i915,radeon,ttm,drm_kms_helper
serio_raw              13166  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13400  2 radeon,i915
video                  19438  1 i915
hp_accel               21880  0 
lis3lv02d              19893  1 hp_accel
input_polldev          14007  1 lis3lv02d
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  2 
xhci_hcd               77643  0 
libahci                26642  1 ahci
atl1c                  41171  0 
I didn't blacklist driver yet because of the ubuntu works but I have sometimes to restart like 5-6 times before getting in, and I use some commands when it's starting up.

I tried additional drivers but that only makes it worse..

One problem that is critical is that my battery life is really short. Don't really know why but I think the fans is working to hard all the time.

---

### Post by wildmanne39 on 2011-10-13
Hi, the battery issue is a bug.

You could just use the intel graphics but I have seen some people have two cards working but I am not sure it is with your cards.

Tomorrow 11.10 comes out you might wait for it then install it and see if that fixes some of your issues, it is up to you how you want to proceed.
Thank you

---

### Post by dstien on 2011-10-14
I might suggest you spend a bit of time working through the blog posts at [http://linuxenvy.blogspot.com/](http://linuxenvy.blogspot.com/).  It helped me get my 11.04 envy 14 (480m, 5650) running almost perfectly.  There are some instructions there on how to blacklist the discrete card and then activate it later in the boot process (avoiding the black screen) and other important instructions to get things working right.

I'm really curious to find out who has tried 11.10 on an envy 14.  I tried it last night with a live USB and it seemed to work really quite well.  Since it wasn't installed, I couldn't try out switcheroo and all that so battery life was around 1-2 hours.  Even suspended and resumed quickly.

---

### Post by Goldenhouse on 2011-10-24
After updating (reinstalled) ubuntu, the graphics are working correctly and no problem with startup anymore. But now my big problem is the fan, it is going on full speed all the time. I check my temperatures and they are low, around 50-60 C, so no problem with temperature. And I think because of the fans my battery will run out fast, in 1,5 hours or less.

If anyone know how to fix this I would really appreciate it (: 

Thank you

> **wildmanne39 said:**
> Hi, the battery issue is a bug.

You could just use the intel graphics but I have seen some people have two cards working but I am not sure it is with your cards.

Tomorrow 11.10 comes out you might wait for it then install it and see if that fixes some of your issues, it is up to you how you want to proceed.
Thank you

---

### Post by dstien on 2011-10-24
> **Goldenhouse said:**
> After updating (reinstalled) ubuntu, the graphics are working correctly and no problem with startup anymore. But now my big problem is the fan, it is going on full speed all the time. I check my temperatures and they are low, around 50-60 C, so no problem with temperature. And I think because of the fans my battery will run out fast, in 1,5 hours or less.

If anyone know how to fix this I would really appreciate it (: 

Thank you

Are you sure you are using the integrated graphics card and not the discrete graphics card?  And that the discrete card is turned off?  Are you using switcheroo to change the cards?  If you haven't done anything to change the cards, the discrete GPU is the default, and it may on and creating enough heat to require the fans to be one.  I'd think it would run cooler than 50-60 on the iGPU.  What do you use to measure the temp?  I could measure mine and find out if your temps are normal.

---

### Post by Henkdroid on 2011-10-24
For the mouse, 2 finger tap is the same as a right click and you can enable  2 finger scrolling in the mouse options, had the same problems with the clickpad on a hp probook.

---

