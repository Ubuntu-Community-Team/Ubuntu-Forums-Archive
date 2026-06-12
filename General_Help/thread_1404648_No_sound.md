---
title: "No sound"
date: 2010-02-11
forum: General Help
---

### Post by DanSchnell on 2010-02-11
I've had this problem since....8.04 I think and I still haven't been able to sort it.  It looks like my situation has improved a little bit in 9.10, but I still have no sound.  Any ideas why?

LSPCI
```
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:06.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:13.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:14.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:15.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:16.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:17.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:18.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
01:00.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
02:00.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
02:02.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
04:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 8800 GTS 512] (rev a2)
09:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
0a:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 AHCI Controller (rev 03)
0a:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 AHCI Controller (rev 03)
0c:00.0 PCI bridge: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG PCI to PCIe Bridge
0d:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG

```

LSMOD
```
Module                  Size  Used by
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
snd_hda_codec_ca0110     7932  1 
snd_usb_audio          85888  1 
snd_usb_lib            18012  1 snd_usb_audio
snd_hda_intel          25728  4 
snd_hda_codec          84384  2 snd_hda_codec_ca0110,snd_hda_intel
binfmt_misc             8356  1 
uvcvideo               59080  0 
snd_hwdep               7392  2 snd_usb_audio,snd_hda_codec
snd_pcm_oss            37472  0 
snd_mixer_oss          16220  1 snd_pcm_oss
snd_pcm                76480  5 snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2752  0 
snd_seq_oss            29216  0 
videodev               36736  1 uvcvideo
snd_seq_midi            6656  0 
v4l1_compat            14496  2 uvcvideo,videodev
snd_rawmidi            22336  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      7036  2 snd_seq_oss,snd_seq_midi
snd_seq                50896  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              21540  2 snd_pcm,snd_seq
snd_seq_device          7208  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   6688  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
snd                    61188  25 snd_hda_codec_ca0110,snd_usb_audio,snd_usb_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
iptable_filter          3100  0 
snd_page_alloc          9124  2 snd_hda_intel,snd_pcm
nvidia               9586440  38 
agpgart                34988  1 nvidia
shpchp                 32272  0 
i2c_nforce2             6784  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
usbhid                 38208  0 
usb_storage            52544  1 
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
forcedeth              54152  0 

```

I updated to ALSA 1.0.22.1 (Compiled Today by Me) and still nothing

Really want to make Ubuntu my main OS but won't do it without sound.

---

### Post by dillinger417 on 2010-02-11
Hi-

  After upgrading to 9.1 I also had no sound (though it worked for me before).  I also have a Creative sound card ( though Soundblaster Live! 7.1 in my case ). To get sound, I had to delete ~/.pulse and mute the IEC958 mixer via "amixer set IEC958 mute" on the command line-- or you could use alsamixer (alsamixer from command line) and highlight the mixer and hit 'm' for mute ( afai recall), or possibly other methods.  I was told Creative sound cards have had problems with the IEC958 mixer auto-un-muting with upgrades.  Hope that works for you.

d417.

---

### Post by DanSchnell on 2010-02-11
how do you delete ~./pulse   ?

---

### Post by samantha_ on 2010-02-11
try running this.
This will fry pulseaudio, and will hopefully force ubuntu to fall back on ALSA.
```

sudo apt-get --purge remove pulseaudio pulseaudio-*
sudo apt-get install linux-backports-modules-alsa-karmic-generic
```

---

### Post by lidex on 2010-02-11
Looks like the x-fi is supported in alsa since 1.0.21. Let's see what's going on in your setup. Download and run this script: 
[http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh]("http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh")
If you save the file locally please post it here. My browser displays this file so best to right-click on the link and select "save link as". Save to your home folder.
Run it with this command:
```
sudo bash utils_alsa-info.sh
```

---

### Post by lidex on 2010-02-12
Run this command in a terminal and reboot:
```
sudo modprobe snd-ctxfi 
```

Now this:
```
alsamixer
```

Make sure levels are up and channels are unmuted.

---

### Post by DanSchnell on 2010-02-12
> **lidex said:**
> Looks like the x-fi is supported in alsa since 1.0.21. Let's see what's going on in your setup. Download and run this script: 
[http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh]("http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh")
If you save the file locally please post it here. My browser displays this file so best to right-click on the link and select "save link as". Save to your home folder.
Run it with this command:
```
sudo bash utils_alsa-info.sh
```

[http://pastebin.ubuntu.com/374459/](http://pastebin.ubuntu.com/374459/)

There's my ALSA info

Edit:

Did sudo modprobe and got

```
WARNING: All config files need .conf: /etc/modprobe.d/sound, it will be ignored in a future release.

``` 

Normal?

And still nothing btw

---

### Post by lidex on 2010-02-12
So you removed pulseaudio? You're showing no sound servers. This is a problem:
```
!!Loaded ALSA modules
!!-------------------

snd_hda_intel
snd_usb_audio


!!Sound Servers on this system
!!----------------------------

No sound servers found.


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfebfc000 irq 16
 1 [VX5000         ]: USB-Audio - Microsoft LifeCam VX-5000
                      Microsoft Microsoft LifeCam VX-5000 at usb-0000:00:0b.1-4, high speed


```
Your soundcard module is not loaded, snd_hda_intel is however and alsa is picking it up. If you have onboard sound, please disable it in your bios. I take that back , it is getting loaded  - but not as an alsa module. I was looking for wrong module.

---

### Post by lidex on 2010-02-12
[http://en.wikipedia.org/wiki/X-fi#X-Fi_Xtreme_Audio]("http://en.wikipedia.org/wiki/X-fi#X-Fi_Xtreme_Audio")

> X-Fi Xtreme Audio

The entry-level model of the X-Fi series, the Sound Blaster X-Fi Xtreme Audio, does not actually have the EMU20K1 chip but is a re-branded Audigy SE, using the same family of chips (CA0106-WBTLF), and even the same drivers.[9] Thus, not only is all of the X-Fi–related processing performed in software, but it also lacks basic hardware acceleration just like the SB Live! 24-bit, the Audigy SE and other budget Soundblaster models. The X-Fi Xtreme Audio does not use the same drivers as the rest of the X-Fi family, some games do not recognize it as being "X-Fi capable hardware", and the device's hardware profile resembles that of older Live! and Audigy cards.

Furthermore, users have reported that it slows down some applications and games, and that rear sound in games (all) is muffled and of profoundly low quality.[18][19][20] Thus, even if the card is marketed as part of the X-Fi line, it does not belong to it technically, just like the Audigy SE doesn't technically belong to the Sound Blaster Audigy series. The card is not marketed as supporting the "X-Fi Gaming Mode" (but is still marketed as "X-Fi"), and there are no official implicit or explicit statements regarding its having hardware acceleration or not.

Those using computers for home recording should be aware that both the Extreme Audio PCI and PCI Express sound cards have known latency issues using the microphone/line in jack. Creative's support section states: "Sound Blaster X-Fi Xtreme Audio Series users may experience issues with latency when trying to record via the microphone. This behaviour is due to the microphone software monitoring feature routing the audio signal to the host and back to the card resulting in some latency." The other Creative X-Fi soundcards do not have this warning.

---

### Post by Tim_nz on 2010-02-12
run this in termnial ALWAYS fixes sound

sudo aptitude install libdns53 libdns53 ureadahead alsa-oss alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base asoundconf-gtk cabextract flashplugin-installer freepats gnome-alsamixer gsfonts-x11 gstreamer0.10-ffmpeg libesd-alsa0 gnome-alsamixer gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs java-common lib32asound2 lib32bz2-1.0 lib32ncurses5 lib32stdc++6 lib32v4l-0 lib32z1 liba52-0.7.4 libao2 libass3 libaudclient2 libaudcore1 libaudid3tag2 libaudio2 libaudutil1 libavcodec52 libavformat52 libavutil49 libbinio1ldbl libbio2jack0 libbio2jack0-dev libcdaudio1 libcddb2 libcelt0 libdc1394-22 libdca0 libdirac0c2a libdvbpsi5 libdvdnav4 libdvdread4 libebml0 libenca0 libfaac0 libfaad0 libffado1 libfftw3-3 libfluidsynth1 libfreebob0 libftgl2 libgconfmm-2.6-1c2 libglademm-2.4-1c2a libglew1.5 libgsm1 libid3tag0 libiptcdata0 libiso9660-5 libjack-dev libjack0 libjack0 liblash2 liblua5.1-0 libmad0 libmatroska0 libmcs1 libmimic0 libmjpegtools-1.9 libmms0 libmodplug0c2 libmowgli1 libmp3lame0 libmp4v2-0 libmpcdec3 libmpeg2-4 libofa0 libpostproc51 libprojectm-data libprojectm2 libquicktime1 libreadline5 libresid-builder0c2a libsad2 libschroedinger-1.0-0 libsdl1.2debian-all libsidplay1 libsidplay2 libsoundtouch1c2 libswscale0 libtwolame0 libvcdinfo0 libvlc2 libvlccore2 libwildmidi0 libx264-67 libxml++2.6-2 libxvidcore4 nspluginwrapper odbcinst1debian1 sun-java6-bin sun-java6-jre sun-java6-plugin ttf-dejavu ttf-dejavu-extra ttf-liberation ttf-mscorefonts-installer ubuntu-restricted-extras unixodbc unrar vlc-data vlc-nox vlc-plugin-pulse linux-backports-modules-2.6.31-17-generic linux-backports-modules-alsa-2.6.31-17-generic linux-backports-modules-alsa-karmic-generic linux-backports-modules-headers-karmic-generic linux-backports-modules-karmic linux-backports-modules-karmic-generic linux-backports-modules-wireless-karmic-generic linux-headers-lbm-2.6.31-17-generic vlc

---

### Post by DanSchnell on 2010-02-12
> **lidex said:**
> So you removed pulseaudio? You're showing no sound servers. This is a problem:
```
!!Loaded ALSA modules
!!-------------------

snd_hda_intel
snd_usb_audio


!!Sound Servers on this system
!!----------------------------

No sound servers found.


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfebfc000 irq 16
 1 [VX5000         ]: USB-Audio - Microsoft LifeCam VX-5000
                      Microsoft Microsoft LifeCam VX-5000 at usb-0000:00:0b.1-4, high speed


```
Your soundcard module is not loaded, snd_hda_intel is however and alsa is picking it up. If you have onboard sound, please disable it in your bios. I take that back , it is getting loaded  - but not as an alsa module. I was looking for wrong module.

So I need to put back pulseaudio?

Also, I have no onboard sound, just the card.  Mobo was packaged with the card instead of having onboard (In retrospect, I won't ever do this again.  I have had ALOT of problems with this mobo)

---

### Post by DanSchnell on 2010-02-12
> **Tim_nz said:**
> run this in termnial ALWAYS fixes sound

```
sudo aptitude install libdns53 libdns53 ureadahead alsa-oss alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base asoundconf-gtk cabextract flashplugin-installer freepats gnome-alsamixer gsfonts-x11 gstreamer0.10-ffmpeg libesd-alsa0 gnome-alsamixer gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs java-common lib32asound2 lib32bz2-1.0 lib32ncurses5 lib32stdc++6 lib32v4l-0 lib32z1 liba52-0.7.4 libao2 libass3 libaudclient2 libaudcore1 libaudid3tag2 libaudio2 libaudutil1 libavcodec52 libavformat52 libavutil49 libbinio1ldbl libbio2jack0 libbio2jack0-dev libcdaudio1 libcddb2 libcelt0 libdc1394-22 libdca0 libdirac0c2a libdvbpsi5 libdvdnav4 libdvdread4 libebml0 libenca0 libfaac0 libfaad0 libffado1 libfftw3-3 libfluidsynth1 libfreebob0 libftgl2 libgconfmm-2.6-1c2 libglademm-2.4-1c2a libglew1.5 libgsm1 libid3tag0 libiptcdata0 libiso9660-5 libjack-dev libjack0 libjack0 liblash2 liblua5.1-0 libmad0 libmatroska0 libmcs1 libmimic0 libmjpegtools-1.9 libmms0 libmodplug0c2 libmowgli1 libmp3lame0 libmp4v2-0 libmpcdec3 libmpeg2-4 libofa0 libpostproc51 libprojectm-data libprojectm2 libquicktime1 libreadline5 libresid-builder0c2a libsad2 libschroedinger-1.0-0 libsdl1.2debian-all libsidplay1 libsidplay2 libsoundtouch1c2 libswscale0 libtwolame0 libvcdinfo0 libvlc2 libvlccore2 libwildmidi0 libx264-67 libxml++2.6-2 libxvidcore4 nspluginwrapper odbcinst1debian1 sun-java6-bin sun-java6-jre sun-java6-plugin ttf-dejavu ttf-dejavu-extra ttf-liberation ttf-mscorefonts-installer ubuntu-restricted-extras unixodbc unrar vlc-data vlc-nox vlc-plugin-pulse linux-backports-modules-2.6.31-17-generic linux-backports-modules-alsa-2.6.31-17-generic linux-backports-modules-alsa-karmic-generic linux-backports-modules-headers-karmic-generic linux-backports-modules-karmic linux-backports-modules-karmic-generic linux-backports-modules-wireless-karmic-generic linux-headers-lbm-2.6.31-17-generic vlc
```


```
Couldn't find any package whose name or description matched "ia32-libs"
Couldn't find any package whose name or description matched "lib32asound2"
Couldn't find any package whose name or description matched "lib32bz2-1.0"
Couldn't find any package whose name or description matched "lib32ncurses5"
Couldn't find any package whose name or description matched "lib32stdc++6"
Couldn't find any package whose name or description matched "lib32v4l-0"
Couldn't find any package whose name or description matched "lib32z1"
Couldn't find any package whose name or description matched "ia32-libs"
Couldn't find any package whose name or description matched "lib32asound2"
Couldn't find any package whose name or description matched "lib32bz2-1.0"
Couldn't find any package whose name or description matched "lib32ncurses5"
Couldn't find any package whose name or description matched "lib32stdc++6"
Couldn't find any package whose name or description matched "lib32v4l-0"
Couldn't find any package whose name or description matched "lib32z1"
The following packages are BROKEN:
  adobe-flashplugin sreadahead ureadahead 

```

Thanks for updating my kernel... But still no sound..

---

### Post by DanSchnell on 2010-02-12
Bump...Sorry, but I really would like to resolve this asap.

---

### Post by lidex on 2010-02-12
```
run this in termnial ALWAYS fixes sound
```

In what universe?:rolleyes:

---

### Post by lidex on 2010-02-12
In a terminal:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Add this line at the bottom and save:
```
options snd_hda_codec_ca0110 index=0
```
Reboot

---

### Post by DanSchnell on 2010-02-13
Nothing yet unfortunately...

---

### Post by lidex on 2010-02-13
I believe all we need to do is get alsa to default to the x-fi and get the proper module loaded (the module is loading, just not where we need it). Can you run the script again to see if anything has changed? Just save it locally this time.

---

### Post by DanSchnell on 2010-02-14
[http://www.alsa-project.org/db/?f=2f4998172e20566b5fc98cca6ea20edd62fb69e2](http://www.alsa-project.org/db/?f=2f4998172e20566b5fc98cca6ea20edd62fb69e2)

I can't get my driver to be to same version as the library and utils.... :-\

edit: and this:

```
# Loaded ALSA modules
# -------------------
#  
# snd_hda_intel
#  
#  
```

---

### Post by lidex on 2010-02-14
Your module is not being loaded at all now. My understanding is that alsa should be recognizing your soundcard and installing the proper driver automagically.

First comment out those last two lines in alsa-base.conf (Place a # at the beginning of each line)
Go here:
[http://ubuntuforums.org/showthread.php?t=1046137]("http://ubuntuforums.org/showthread.php?t=1046137")
Download the update script "AlsaUpgrade-1.0.22.1-2.tar" near the bottom of post #1.

Instructions:
> Short Alsa-Upgrade script install instructions:

1. download the script and save it somewhere
2. cd <your-download-dir>
3. tar xvf AlsaUpgrade-1.0.22.1-2.tar
4. sudo ./AlsaUpgrade-1.0.22.1-2.sh -d
5. sudo ./AlsaUpgrade-1.0.22.1-2.sh -c
6. sudo ./AlsaUpgrade-1.0.22.1-2.sh -i
7. sudo shutdown -r 0

---

### Post by DanSchnell on 2010-02-15
[http://www.alsa-project.org/db/?f=9ea56fd24ed8d383fbe99b7dc798af4f95d5346f](http://www.alsa-project.org/db/?f=9ea56fd24ed8d383fbe99b7dc798af4f95d5346f)

It's still at 1.0.21 :( and it didn't load the module.

---

### Post by lidex on 2010-02-15
OK. More on that later, for now try this.
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

Add this line at the bottom:
```
blacklist snd_hda_intel

```

Save and reboot.

---

### Post by dillinger417 on 2010-03-09
> **DanSchnell said:**
> how do you delete ~./pulse   ?

~ is a symbol for your home folder i.e. /home/YOUR_USER_NAME

There was a typo there, sorry, I meant "~/.pulse".  Perhaps that was the source of confusion.  Anyway, it is the folder that has profile pulseaudio settings for YOUR_USER_NAME.  As in my case, sometimes it can be helpful to delete (or rename) this folder after an upgrade, this allows pulse to create a new ~/.pulse folder with all of the default settings in case there are settings, possibly outdated from the previous version, that are causing problems.

That doesn't seem to be the problem here though.

Like the example shown in [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) , it looks like Ubuntu is trying to use the snd_hda_intel module with the CA0110 codec ( CA0110 btw doesn't match a chipset listed in the ALSA matrix [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)). Looking at the alsa documentation for the intel module, the fact that your card is called "Generic" gives cause for concern ( and that you have no sound ) along with HDA messages about no response in your posts.

"The model name "genric" is treated as a special case.  When this model is given, the driver uses the generic codec parser without
 "codec-patch".  It's sometimes good for testing and debugging."

It seems like during install of Ubuntu, the Alsa version in place did not support your card, and all this snd_hda_intel + ca0110 codec business was its best attempt to support your card.

Anyway, blacklisting snd_hda_intel and trying to force use of the codec module does not seem like a viable option imho.  

If you have ALSA working at a version that supports the snd-ctxfi then I would highly recommend trying to load and use that.  You could try using the method that lidex was explaining, but substituting snd-ctxfi for snd_hda_codec_ca0110 during this section

In a terminal:

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

Add this line at the bottom and save:

```
options snd-ctxfi index=0
```

---

### Post by endor43 on 2010-03-21
any progress? i am having the same issue.

---

