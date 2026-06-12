---
title: "easy sound fix for karmic 9.10 ubuntu"
date: 2010-01-31
forum: General Help
---

### Post by kronictokr on 2010-01-31
ubuntu karmic 9.10 sound fix solved

redone for more recent pakages, as well, removed a couple useless ones
doesnt involve removing pulse. gets sound through hdmi earphones and laptop speakers
still testing, but all works

sudo aptitude install libdns53 libdns53 ureadahead alsa-oss alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base asoundconf-gtk cabextract flashplugin-installer freepats gnome-alsamixer gsfonts-x11 gstreamer0.10-ffmpeg libesd-alsa0 gnome-alsamixer gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs java-common lib32asound2 lib32bz2-1.0 lib32ncurses5 lib32stdc++6 lib32v4l-0 lib32z1 liba52-0.7.4 libao2 libass3 libaudclient2 libaudcore1 libaudid3tag2 libaudio2 libaudutil1 libavcodec52 libavformat52 libavutil49 libbinio1ldbl libbio2jack0 libbio2jack0-dev libcdaudio1 libcddb2 libcelt0 libdc1394-22 libdca0 libdirac0c2a libdvbpsi5 libdvdnav4 libdvdread4 libebml0 libenca0 libfaac0 libfaad0 libffado1 libfftw3-3 libfluidsynth1 libfreebob0 libftgl2 libgconfmm-2.6-1c2 libglademm-2.4-1c2a libglew1.5 libgsm1 libid3tag0 libiptcdata0 libiso9660-5 libjack-dev libjack0 libjack0 liblash2 liblua5.1-0 libmad0 libmatroska0 libmcs1 libmimic0 libmjpegtools-1.9 libmms0 libmodplug0c2 libmowgli1 libmp3lame0 libmp4v2-0 libmpcdec3 libmpeg2-4 libofa0 libpostproc51 libprojectm-data libprojectm2 libquicktime1 libreadline5 libresid-builder0c2a libsad2 libschroedinger-1.0-0 libsdl1.2debian-all libsidplay1 libsidplay2 libsoundtouch1c2 libswscale0 libtwolame0 libvcdinfo0 libvlc2 libvlccore2 libwildmidi0 libx264-67 libxml++2.6-2 libxvidcore4 nspluginwrapper odbcinst1debian1 sun-java6-bin sun-java6-jre sun-java6-plugin ttf-dejavu ttf-dejavu-extra ttf-liberation ttf-mscorefonts-installer ubuntu-restricted-extras unixodbc unrar vlc-data vlc-nox vlc-plugin-pulse linux-backports-modules-2.6.31-20-generic linux-backports-modules-alsa-2.6.31-20-generic linux-backports-modules-alsa-karmic-generic linux-backports-modules-headers-karmic-generic linux-backports-modules-karmic linux-backports-modules-karmic-generic linux-headers-lbm-2.6.31-20-generic vlc

sudo reboot

enjoy!!

leave a message if you have any problems. but this shouldnt harm anything at all

getting great sound :D

---

### Post by karmic-koala on 2010-01-31
Has anybody given this a go yet?

---

### Post by kronictokr on 2010-02-05
i just did a fresh install, updated the pakages in the list again, and tried it again, rebooted, and was greated with sound when i signed in. you have to play with some of the controls, in pulse volume control, and gnome mixer, but everything works, and great sound

---

### Post by marjancek on 2010-02-15
> **kronictokr said:**
> ubuntu karmic 9.10 sound fix solved...

So you install everything from unrar to true type fonts in order to fix the sound ???

Do you know which update actually fixes it?

M.-

---

### Post by MADwe on 2010-02-15
It's the linux-backports-modules-karmic-generic package, just install it with Synaptic.
After installing it, sound after plugging in/out my headphones works perfectly with my Acer 5739g (Realtek ALC888).

---

### Post by kronictokr on 2010-02-16
for some thats all it takes, for others they need a couple more pakages. or one removed. also some have issues with the new headers loading or something, and this seems to resolve that as well.

it does fix the sound, and anything else installed is usually a good idea for overall functionality, even for the basics. if you already have it installed it wont reinstall it anyway.

the idea is helping someone with a problem before they may know they have it ;)
its completely harmless, and it may help a couple noobs out. thats why it is as it is

---

### Post by ublunted on 2010-02-23
High. Im playing with Ubuntu 9.10 on my HP DV6 2164ca laptop. I too had no sound, but it works now after whatever you wrote up and playing with the mixer. I don't know how you kids figure this stuff out, but it's pretty freekin cool. I'm new at linux and just installed this last night, so I figure I will be working some kinks out. I'm online, so dats good. So, the sound works, except that plugging in headphones doesn't mute the laptop speakers, but the headphones work:D

---

### Post by kronictokr on 2010-02-23
i did find a fix for the headphones, im looking for it now. untill i post you can always use the mixer to mute your speakers when you want to use headphones. for now

---

### Post by ublunted on 2010-02-24
If I mute the speakers, it mutes the phones too:confused: unless i'm missing something.

---

### Post by tominto on 2010-02-24
I've been having problems with sound ever since I've installed karmic.  I get sound for maybe ten minutes or so after a reboot, and then nothing.  I tried the above solution and got these error messages 

"Couldn't find any package whose name or description matched "ia32-libs"
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
"

Is this normal?  
Anyone have any idea what my actual problem might be?  As I said I get sound for a short while after I reboot, and then nothing.  I have a tv tuner installed in my computer, and the sound on that is fine.:confused:

---

### Post by vnyprasad on 2010-02-25
Thanks for that! I did that and my sound works perfectly!
BUT... My wireless stopped working! I have a HP tx2 laptop...any ideas on how to make it work again? thanks!

---

### Post by kronictokr on 2010-02-25
> **ublunted said:**
> If I mute the speakers, it mutes the phones too:confused: unless i'm missing something.
if  you into sound application, and gnome mixer, you can choose level output of all devices

tominto: are you running 64 bit? shouldnt matter , what did you do exactly?

---

### Post by kronictokr on 2010-02-26
> **vnyprasad said:**
> Thanks for that! I did that and my sound works perfectly!
BUT... My wireless stopped working! I have a HP tx2 laptop...any ideas on how to make it work again? thanks!
reinstall your network manager, through synaptics or with your terminal

if youre using a base network manager, open a terminal and type

sudo aptitude remove network-manager

then 

sudo aptitude install network-manager

---

### Post by subru77 on 2010-02-26
Just works ... I did dig deep. Just paste and hit enter ..

Thanks a bunch

---

### Post by hman469 on 2010-02-27
Still no sound, can the tuner card cause problems? I do have  64 bit.

---

### Post by matthus on 2010-03-12
I had this problem for ages, turns out it was due to this [https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/) the dvdcss library there was messin up my sound, that or was as I didn't unplug my headphones socket before booting up then pluggin em in

---

### Post by kronictokr on 2010-03-14
as far as muting : go into APPLICATIONS>>SOUND &VIDEO>>GNOME MIXER
ther you should be able to mute individual components of your sound system

those errrors would tell me that you most likely have a 32 bit system, or possibly used a 32 bit install cd/dvd.   this solution is for ubuntu karmic 9.10 64 bit, sorry

---

### Post by Jimbopix on 2010-03-18
Another win in the column for this thread. I think it was the gnome-alsamixer that solved it for me. Once that was installed I was able to select the Audigy Analog/Digital Output Jack from the list of check boxes and away went my sound.

Thanks so much for this post. The silence was making me go crazy, lol.

---

### Post by kronictokr on 2010-06-23
glad i could help!

copy paste, hit enter, gotta love it , hehe

---

### Post by subru77 on 2010-07-08
Is there a Lucid 10.04 version for this one ?

---

