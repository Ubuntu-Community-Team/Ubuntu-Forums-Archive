---
title: "Installing sound card drivers - 'make' error"
date: 2009-09-15
forum: General Help
---

### Post by Millenia on 2009-09-15
I've been trying to install my sound card drivers, and so far I've had no luck. I can't manage to understand the instructions. Here they are:
> STEPS TO BUILD DRIVER
================================================================================

  1. Backup the Config.in and Makefile in the sound driver directory
     (/usr/src/linux/driver/sound).
     The Configure.help provide help when you config driver in step
     4, please backup the original one (/usr/src/linux/Document) and
     copy this file.
     The cmpci is document for the driver in detail, please copy it
     to /usr/src/linux/Document/sound so you can refer it. Backup if
     there is already one.

  2. Extract the tar file by 'tar xvzf cmpci-xx.tar.gz' in the above
     directory.

  3. Change directory to /usr/src/linux

  4. Config cm8338 driver by 'make menuconfig', 'make config' or
     'make xconfig' command.

  5. Please select Sound Card (CONFIG_SOUND=m) support and CMPCI
     driver (CONFIG_SOUND_CMPCI=m) as modules. Resident mode not tested.
     For driver option, please refer 'DRIVER PARAMETER'

  6. Compile the kernel if necessary.

  7. Compile the modules by 'make modules'.

  8. Install the modules by 'make modules_install'Even at step 1 I've had problems. I don't have a /usr/src/linux/driver/sound directory. So instead I've put my 'cmpci' directory with all my the driver files into a directory I made myself which is at /usr/src/cmpci. The instructions don't seem to make sense. While I'm in my 'cmpci' directory, I try running the commands it gives me, such as make config, make menuconfig and make xconfig, but all of those give me the same error:
> Makefile:159: /Rules.make: No such file or directory
make: *** No rule to make target `/Rules.make'. Stop.
I have tried make -f Makefile config with no further luck. Even 'make clean' gives me the same error. 

Can anyone help me with these instructions and my wierd make problems?

Thanks.

---

### Post by Millenia on 2009-09-16
Bump? (If that's allowed)

---

### Post by oldos2er on 2009-09-16
What sound card do you have?

---

### Post by Millenia on 2009-09-16
'CMI-8768' it says on the box. I'm not sure if that's the name of the actual card. It says that on the chip too though.

---

### Post by Millenia on 2009-09-16
[http://www.cmedia.com.tw/pci_cmI8768.html](http://www.cmedia.com.tw/pci_cmI8768.html)

That's a link to the 'official site' of the chip. The card was bought because of the supposed compatability with Linux. On the box it actually says 'CMI-8738', while on the card itself it says '8768'. The CD contains the drivers (for more than one piece of hardware) for both cards. I've been trying to install the 8738 drivers, but I presume it would work anyway? When I had a look in the 8768 directory, I noticed no Linux installation options. Simply a setup.exe. 

I have another soundcard which is coincidently the 8738 card. I've tried that and I still had issues with installing the drivers.

I presume the problem isn't the card or the drivers; but the make command on my computer?

---

### Post by oldos2er on 2009-09-16
I don't see anything on their site about Linux. 

 Can you run the command **alsamixer **in a terminal, and are you able to move the sliders?

---

### Post by Millenia on 2009-09-16
I just ran that command and got this error:

```

alsamixer: function snd_ctl_open failed for default: No such file or directory

```

Edit:

> **oldos2er said:**
> I don't see anything on their site about Linux. 


That's because I linked to the 8768 chip which I have. I am tying to install the Linux drivers for the 8738 chip which does support Linux. I was hoping that those drivers would still apply to the chip I have. After all, I have a spare card with the 8738 chip in it, and got the same error with everything I've tried to do.

---

### Post by Millenia on 2009-09-17
[http://alsa.opensrc.org/index.php/Quick_Install](http://alsa.opensrc.org/index.php/Quick_Install)

I visited that site. I checked with **sudo apt-get installed alsa** that I have alsa installed. I'm sure I had it installed anyway. I don't understand most of the instructions, but I skipped to the 'Loading the ALSA Modules'.
[B]modprobe snd-ens1371
modprobe snd-pcm-oss
modprobe snd-mixer-oss
modprobe snd-seq-oss[/B]

I ran all of them, and all of them worked apart from the top one, which I got this error message:
```
FATAL: Module snd_ens1371 not found.
```The command **alsamixer** still doesn't work.

I ran** lsmod** and got this if it is of any use:
```
Module                  Size  Used by
snd_pcm_oss            45984  0 
snd_pcm                83716  1 snd_pcm_oss
snd_page_alloc         17032  1 snd_pcm
snd_mixer_oss          22912  1 snd_pcm_oss
snd_seq_oss            36224  0 
snd_seq_midi_event     15232  1 snd_seq_oss
snd_seq                57584  4 snd_seq_oss,snd_seq_midi_event
snd_timer              29192  2 snd_pcm,snd_seq
snd_seq_device         15372  2 snd_seq_oss,snd_seq
snd                    67236  7 snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
binfmt_misc            16776  1 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
video                  25360  0 
output                 11008  1 video
input_polldev          11912  0 
lp                     17156  0 
ppdev                  15620  0 
pcspkr                 10496  0 
k8temp                 12416  0 
nvidia               7097928  34 
i2c_viapro             15892  0 
shpchp                 40212  0 
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
amd64_agp              18184  1 
agpgart                42696  2 nvidia,amd64_agp
usbhid                 42336  0 
skge                   48272  0 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
floppy                 64324  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```

---

### Post by P4man on 2009-09-17
What version of ubuntu are you using?
Could you try a livecd? Googling on your card seems to suggest it should work out of the box, so Im wondering if you didn't break alsa trying to make it work.

---

### Post by Millenia on 2009-09-17
Ubuntu 9.04 Jaunty Jackalope. I have a few spare liveCD's lying around the house. What would you want me to do exactly?

---

### Post by theozzlives on 2009-09-17
Do you have an onboard sound card? If so, you may have to disable it in your BIOS.

---

### Post by P4man on 2009-09-17
> **Millenia said:**
> Ubuntu 9.04 Jaunty Jackalope. I have a few spare liveCD's lying around the house. What would you want me to do exactly?

Just boot from one and see if you have sound (and if alsamixer does work, and if ```
aplay -l
``` lists your card.)

---

### Post by Millenia on 2009-09-17
> **theozzlives said:**
> Do you have an onboard sound card? If so, you may have to disable it in your BIOS.

I'm not sure I do, but I presume so. I looked in the BIOS and I can't see any options for a sound card. Although I could play music (very badly) through my computer before I decided to buy one.

> **P4man said:**
> Just boot from one and see if you have sound (and if alsamixer does work, and if ```
aplay -l
``` lists your card.)

I tried that command and got this:
```
aplay: device_list:217: no soundcards found...

```

I'm going to go try it on a LiveCD of Ubuntu and see what happens then.

---

### Post by Millenia on 2009-09-17
When I first put the card in, I had problems. As soon as I would log on, the computer would freeze. Black screen and stationary mouse (forcing me to restart). When I took out the card, it would work fine. I tried changing the slot which the sound card was on my motherboard and it worked. No problems no freezing. Although the sound card wouldn't work.

When I boot into the LiveCD I get the same problem. After I select 'Try Ubuntu', and waited for it to load, it freezes.

---

### Post by Millenia on 2009-09-17
> **theozzlives said:**
> Do you have an onboard sound card? If so, you may have to disable it in your BIOS.

I just checked in my BIOS, and under 'Onboard devices' I found something called **Onboard AS '97 Audio**. It's currently enabled; so I presume that's the on-board soundcard?

---

### Post by danwood76 on 2009-09-17
Yes thats the onboard sound.

You can build alsa from source with a script:
[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

Takes all the fun out of compiling yourself though :) but does make life easier.
Try that first so you are running the very latest version of alsa, with any luck your soundcard will just start working with the latest alsa.

---

### Post by Millenia on 2009-09-17
Before upgrading ALSA do you want me to disable the on-board sound?

---

### Post by danwood76 on 2009-09-17
Pulseaudio allows for multiple sound cards and you select the one you want to use so its fine for it to be enabled.
Compile and install alsa and then post back if you get sound.

---

### Post by Millenia on 2009-09-18
It's good news that my sound is working. I can listen to all my music. Although the bad news is that I can't get any sound on flash to work. I've tried **sudo apt-get install flashplugin-nonfree-extrasound**, but still no luck. I regularly use Youtube, and it's a shame I can't get any sound!

Anyone got any ideas for getting my sound to work on flash/Firefox?

---

### Post by Millenia on 2009-09-19
It's started working now. Thanks for all the help.

---

