---
title: "(all varients) fixing scratching/poping noise on ubuntu 9.10"
date: 2010-02-07
forum: General Help
---

### Post by linuxgeek77 on 2010-02-07
[B][U]IMPORTANT- KUBUNTU USERS USE kate INSTEAD OF gedit
           XUBUNTU USERS USE mousepad INSTEAD OF gedit
[/U][/B]
hello guys i posted a post about this a while ago that did not work for some people so today i am going to post both ways where u can actually MAKE your sound work with ubuntu if you have an HDA audio card. the first solution is this: open the terminal and type-  (this is for the crackling/poping noise only. not muted sound cards, and you may skip this step if it is not crackling/poping) : 


```
sudo gedit /etc/modprobe.d/alsa-base.conf
```then type your password


and then the last two lines where you see power-save option, just delete it. and save it.

**FOR ATI/HDA/HDMI DRIVERS this MAY work for you as well: : ( you can try adding backports for your driver with this command - it may work for you)** open terminal and type:

```
**sudo apt-get install linux-backports-modules-alsa-karmic-generic**
```REBOOT- this will work if your experiencing wither no sound or your audio jacks are not working.
I hope i helped someone out there with my post :smile: please comment back and let me know if it works for you. 
this was tested on HP dv6636nr laptop with HDA NVIDIA card.
                                                                                                   
**[COLOR=black]SECOND STEP - UPDATING ALSA:- [/COLOR]**

IF THAT DOESNT HELP WHILE PLAYING GAMES/ WATCHING VIDEOS THEN TRY THIS:

here i will show you how to update your alsa drivers for your sound card to teh latest one that support alot more HDA audio cards. follow the steps and report back to me. 

To do this, we must begin by determining our version of alsa as follows :

```
cat /proc/asound/version
``` Advanced Linux Sound Architecture Driver Version 1.0.20.
 

To avoid problems during the upgrade of Alsa-utils, we need to stop it with the following command :
 

 ```
sudo /etc/init.d/alsa-utils stop
```  [LEFT]
We must then install the necessary tools to compile along with the kernel headers :[/LEFT]
 

```
sudo apt-get -y install build-essential ncurses-dev gettext xmlto libasound2-dev
``` ```
sudo apt-get -y install linux-headers-`uname -r` libncursesw5-dev
```Then, we go in our personal folder and download alsa-driver, alsa-lib and alsa-utils :
 

```
cd ~
``````
rm -rf ~/alsa* ~/.pulse*
```[HTML]wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.23.tar.bz2[/HTML][HTML]wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.23.tar.bz2[/HTML][HTML]wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.23.tar.bz2[/HTML]After that, we create a new folder for the compilation and installation of the 3 files. Then, we move the 3 tar files that we just downloaded in this folder :
 

```
sudo rm -rf /usr/src/alsa
``````
sudo mkdir -p /usr/src/alsa
``````
cd /usr/src/alsa
``````
sudo cp ~/alsa* .
```Unpack the 3 tar files :
 

```
sudo tar xjf alsa-driver*
``````
sudo tar xjf alsa-lib*
``````
sudo tar xjf alsa-utils*
```We compile and install alsa-driver :
 

```
cd alsa-driver*
``````
sudo ./configure
``````
sudo make
``````
sudo make install
```We compile and install alsa-lib :
 

```
cd ../alsa-lib*
``````
sudo ./configure
``````
sudo make
``````
sudo make install
```We compile and install alsa-utils :
 

```
cd ../alsa-utils*
``````
sudo ./configure
``````
sudo make
``````
sudo make install
```_If like me, you got this error during the last &#8220;sudo ./configure&#8221; :_
 ```
checking form.h presence... yes
checking for form.h... yes
checking for new_panel in -lpanelw... no
configure: error: panelw library not found 
```You will need to add those symbolics links (**only if you got the error**) and restart the installation from the last &#8220;sudo ./configure&#8221; :


```
sudo ln -s libpanelw.so.5 /usr/lib/libpanelw.so
``````
sudo ln -s libformw.so.5 /usr/lib/libformw.so
``````
sudo ln -s libmenuw.so.5 /usr/lib/libmenuw.so
``````
sudo ln -s libncursesw.so.5 /lib/libncursesw.so
```Then, we remove the 3 tar files in our personal folder that are not anymore necessary :
 

```
rm -f ~/alsa-driver*
``````
rm -f ~/alsa-lib*
``````
rm -f ~/alsa-utils*
```Then, just restart your computer and your alsa version should be 1.0.22.1!
 You can verify that you have now indeed have this version of alsa :
 

```
cat /proc/asound/version
```Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Dec 29 2009 for kernel 2.6.31-16-generic (SMP).
 

Just to be sure everything is well configured, execute this command :
 

```
sudo alsaconf
```and reboot again!

**THIRD STEP POSTED BELOW AS A REPLY **

CREDITS: [http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/)
[IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]                            [[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=8370514")                                                                       [IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG]             [[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=8370514")

---

### Post by linuxgeek77 on 2010-03-02
Okay here is the last solution i can think of that may work for you if all failed:

open teh terminal and type this:

```
aplay -l 
```and look for your sound card driver there/codec then:

```
sudo gedit /etc/modprobe.d/alsa-base

```will get you into the sound setup file

after the last line of code enter the following:

```
options snd-hda-intel model="your sound card model"
```save it


(replace teh "your card model" with your actual card sound card driver/codec -remove qoutes- if you have more than one add both of them)

Reboot


**-FORTH STEP ( IT MAY BE PULSE AUDIO CAUSING THE PROBLEM)**

WE will Remove Pulseaudio and use regular asla-mixer instead. 

```
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
``````
sudo apt-get autoremove
``````
sudo apt-get install esound esound-clients esound-common libesd-alsa0 gnome-alsamixer
```restart your computer!

Notes:
-run gstreamer-properties in terminal to set defaults to alsa (the old system/preferences/sound in jaunty)[INDENT]This means:
    
     ```
gstreamer-properties 
```[/INDENT]-remove gstreamer0.10-pulseaudio to get sound in totem.[INDENT]The above commands should have taken care of that, but it never hurts to be sure when talking about the hydra that is PulseAudio.
[/INDENT]-gnome-alsamixer is for changing the volume, not an applet but better that nothing[INDENT]This means you are left without a panel applet to control volume across the board, thanks to the thoughtful efforts of Canonical to shove PulseAudio down our throats. So you need to have something to control audio with:
   
     ```
sudo apt-get install gnome-alsamixer
```And something to keep gnome-alsamixer within easy reach, provided by AllTray:
    
     ```
sudo apt-get install alltray
```credits goes to: [nullrend]("http://ubuntu-ky.ubuntuforums.org/member.php?u=702166")[/INDENT]

---

### Post by leorolla on 2010-03-07
Latest Karmic kernell already comes with ALSA 1.0.22
So no need for re-compiling everything and doing all that ugly job.

For "your sound card model", you know where we can find a list?

---

### Post by linuxgeek77 on 2010-03-07
> **leorolla said:**
> Latest Karmic kernell already comes with ALSA 1.0.22
So no need for re-compiling everything and doing all that ugly job.

For "your sound card model", you know where we can find a list?

yes but on linux mint for some reason it is not updated


aplay -l should so it or you can try this:

```
lspci -v | less
```

see if you card is supported here: [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)

---

### Post by leorolla on 2010-03-08
> **linuxgeek77 said:**
> aplay -l should so it or you can try this:

```
lspci -v | less
```see if you card is supported here: [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)

I mean a comprehensive list with all possible values.


Edit:
FOUND IT!
[http://git.alsa-project.org/?p=alsa-kernel.git;a=blob;f=Documentation/sound/alsa/HD-Audio-Models.txt;hb=HEAD](http://git.alsa-project.org/?p=alsa-kernel.git;a=blob;f=Documentation/sound/alsa/HD-Audio-Models.txt;hb=HEAD)

---

### Post by leorolla on 2010-03-08
> **linuxgeek77 said:**
> yes but on linux mint for some reason it is not updated[]("http://www.alsa-project.org/main/index.php/Matrix:Main")

Even with linux-backports-modules-alsa-karmic-generic ?

From Karmic repositories, and without recompiling alsa or rebuilding kernel, I got:

```
$ uname -r
2.6.31-20-generic
$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Feb  8 2010 for kernel 2.6.31-20-generic (SMP).
$ apt-cache policy linux-backports-modules-alsa-2.6.31-20-generic
linux-backports-modules-alsa-2.6.31-20-generic:
  Installed: 2.6.31-20.22
  Candidate: 2.6.31-20.22
  Version table:
 *** 2.6.31-20.22 0
        901 http://archive.ubuntu.com karmic-updates/main Packages
        100 /var/lib/dpkg/status
$ 

```

---

### Post by yorgmeister on 2010-03-13
This fix broke mplayer, I now get:

mplayer has finished unexpectedly. exit code 1

Log file:

 p, li { white-space: pre-wrap; }  mplayer -noquiet -nofs -nomouseinput -afm hwac3 -sub-fuzziness 1 -identify -slave -vo xv -ao alsa:device=hw=0.1 -nokeepaspect -framedrop -autosync 100 -nodr -double -input nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 62914575 -monitorpixelaspect 1 -subcp ISO-8859-1 -subpos 100 -volume 50 -nocache -osdlevel 0 -vf-add screenshot -slices -channels 6 -softvol -softvol-max 120 /home/yorgie/Downloads/Sherlok.Holms.2009.x264.BDRip.1080p-kinozal.tv-HD/Sherlok.Holms.2009.x264.BDRip.1080p-kinozal.tv-HD.mkv
  MPlayer SVN-r30886-4.3.4 (C) 2000-2010 MPlayer Team
 Terminal type `unknown' is not defined.
  Playing /home/yorgie/Downloads/Sherlok.Holms.2009.x264.BDRip.1080p-kinozal.tv-HD/Sherlok.Holms.2009.x264.BDRip.1080p-kinozal.tv-HD.mkv.
 ID_VIDEO_ID=0
 [mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
 ID_AUDIO_ID=0
 ID_AID_0_NAME=MVO
 ID_AID_0_LANG=rus
 [mkv] Track ID 2: audio (A_AC3) "MVO", -aid 0, -alang rus
 ID_AUDIO_ID=1
 ID_AID_1_NAME=DUB (Line)
 ID_AID_1_LANG=rus
 [mkv] Track ID 3: audio (A_MPEG/L3) "DUB (Line)", -aid 1, -alang rus
 ID_AUDIO_ID=2
 ID_AID_2_LANG=und
 [mkv] Track ID 4: audio (A_DTS), -aid 2, -alang und
 [mkv] Will play video track 1.
 Matroska file format detected.
 VIDEO:  [avc1]  1920x1080  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
 ID_FILE_SUB_ID=0
 ID_FILE_SUB_FILENAME=/home/yorgie/Downloads/Sherlok.Holms.2009.x264.BDRip.1080p-kinozal.tv-HD/Sherlok.Holms.2009.x264.BDRip.1080p-kinozal.tv-HD.srt
 SUB: Added subtitle file (1): /home/yorgie/Downloads/Sherlok.Holms.2009.x264.BDRip.1080p-kinozal.tv-HD/Sherlok.Holms.2009.x264.BDRip.1080p-kinozal.tv-HD.srt
 ID_FILENAME=/home/yorgie/Downloads/Sherlok.Holms.2009.x264.BDRip.1080p-kinozal.tv-HD/Sherlok.Holms.2009.x264.BDRip.1080p-kinozal.tv-HD.mkv
 ID_DEMUXER=mkv
 ID_VIDEO_FORMAT=avc1
 ID_VIDEO_BITRATE=0
 ID_VIDEO_WIDTH=1920
 ID_VIDEO_HEIGHT=1080
 ID_VIDEO_FPS=23.976
 ID_VIDEO_ASPECT=1.7778
 ID_AUDIO_FORMAT=8192
 ID_AUDIO_BITRATE=0
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=6
 ID_LENGTH=7704.71
 ID_SEEKABLE=1
 ID_CHAPTERS=0
 Opening video filter: [screenshot]
 ==========================================================================
 Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
 Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
 ==========================================================================
 ID_VIDEO_CODEC=ffh264
 ==========================================================================
 Trying to force audio codec driver family hwac3...
 Opening audio decoder: [hwac3] AC3/DTS pass-through S/PDIF
 hwac3: switched to AC3, 384000 bps, 48000 Hz
 AUDIO: 48000 Hz, 2 ch, ac3be, 384.0 kbit/25.00% (ratio: 48000->192000)
 ID_AUDIO_BITRATE=384000
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=2
 Selected audio codec: [hwac3] afm: hwac3 (AC3 through S/PDIF)
 ==========================================================================
 [AO_ALSA] alsa-lib: conf.c:3843:(parse_args) Unknown parameter AES0
 [AO_ALSA] alsa-lib: conf.c:3969:(snd_config_expand) Parse arguments error: No such file or directory
 [AO_ALSA] alsa-lib: pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM hw:0,1,AES0=6
 [AO_ALSA] Format ac3be is not supported by hardware, trying default.
 AO: [alsa] 48000Hz 2ch ac3le (2 bytes per sample)
 ID_AUDIO_CODEC=hwac3
 [Mixer] No hardware mixing, inserting volume filter.
 [format] Sample format big-endian AC3 not yet supported 
 Starting playback...
   MPlayer interrupted by signal 11 in module: decode_audio
 ID_SIGNAL=11
 - MPlayer crashed by bad usage of CPU/FPU/RAM.
   Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
   disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
 - MPlayer crashed. This shouldn't happen.
   It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
   gcc version. If you think it's MPlayer's fault, please read
   DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
   won't help unless you provide this information when reporting a possible bug.

---

### Post by linuxgeek77 on 2010-03-17
> **yorgmeister said:**
> This fix broke mplayer, I now get:

mplayer has finished unexpectedly. exit code 1

Log file:

 p, li { white-space: pre-wrap; }  mplayer -noquiet -nofs -nomouseinput -afm hwac3 -sub-fuzziness 1 -identify -slave -vo xv -ao alsa:device=hw=0.1 -nokeepaspect -framedrop -autosync 100 -nodr -double -input nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 62914575 -monitorpixelaspect 1 -subcp ISO-8859-1 -subpos 100 -volume 50 -nocache -osdlevel 0 -vf-add screenshot -slices -channels 6 -softvol -softvol-max 120 /home/yorgie/Downloads/Sherlok.Holms.2009.x264.BDRip.1080p-kinozal.tv-HD/Sherlok.Holms.2009.x264.BDRip.1080p-kinozal.tv-HD.mkv
  MPlayer SVN-r30886-4.3.4 (C) 2000-2010 MPlayer Team
 Terminal type `unknown' is not defined.
  Playing /home/yorgie/Downloads/Sherlok.Holms.2009.x264.BDRip.1080p-kinozal.tv-HD/Sherlok.Holms.2009.x264.BDRip.1080p-kinozal.tv-HD.mkv.
 ID_VIDEO_ID=0
 [mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
 ID_AUDIO_ID=0
 ID_AID_0_NAME=MVO
 ID_AID_0_LANG=rus
 [mkv] Track ID 2: audio (A_AC3) "MVO", -aid 0, -alang rus
 ID_AUDIO_ID=1
 ID_AID_1_NAME=DUB (Line)
 ID_AID_1_LANG=rus
 [mkv] Track ID 3: audio (A_MPEG/L3) "DUB (Line)", -aid 1, -alang rus
 ID_AUDIO_ID=2
 ID_AID_2_LANG=und
 [mkv] Track ID 4: audio (A_DTS), -aid 2, -alang und
 [mkv] Will play video track 1.
 Matroska file format detected.
 VIDEO:  [avc1]  1920x1080  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
 ID_FILE_SUB_ID=0
 ID_FILE_SUB_FILENAME=/home/yorgie/Downloads/Sherlok.Holms.2009.x264.BDRip.1080p-kinozal.tv-HD/Sherlok.Holms.2009.x264.BDRip.1080p-kinozal.tv-HD.srt
 SUB: Added subtitle file (1): /home/yorgie/Downloads/Sherlok.Holms.2009.x264.BDRip.1080p-kinozal.tv-HD/Sherlok.Holms.2009.x264.BDRip.1080p-kinozal.tv-HD.srt
 ID_FILENAME=/home/yorgie/Downloads/Sherlok.Holms.2009.x264.BDRip.1080p-kinozal.tv-HD/Sherlok.Holms.2009.x264.BDRip.1080p-kinozal.tv-HD.mkv
 ID_DEMUXER=mkv
 ID_VIDEO_FORMAT=avc1
 ID_VIDEO_BITRATE=0
 ID_VIDEO_WIDTH=1920
 ID_VIDEO_HEIGHT=1080
 ID_VIDEO_FPS=23.976
 ID_VIDEO_ASPECT=1.7778
 ID_AUDIO_FORMAT=8192
 ID_AUDIO_BITRATE=0
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=6
 ID_LENGTH=7704.71
 ID_SEEKABLE=1
 ID_CHAPTERS=0
 Opening video filter: [screenshot]
 ==========================================================================
 Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
 Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
 ==========================================================================
 ID_VIDEO_CODEC=ffh264
 ==========================================================================
 Trying to force audio codec driver family hwac3...
 Opening audio decoder: [hwac3] AC3/DTS pass-through S/PDIF
 hwac3: switched to AC3, 384000 bps, 48000 Hz
 AUDIO: 48000 Hz, 2 ch, ac3be, 384.0 kbit/25.00% (ratio: 48000->192000)
 ID_AUDIO_BITRATE=384000
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=2
 Selected audio codec: [hwac3] afm: hwac3 (AC3 through S/PDIF)
 ==========================================================================
 [AO_ALSA] alsa-lib: conf.c:3843:(parse_args) Unknown parameter AES0
 [AO_ALSA] alsa-lib: conf.c:3969:(snd_config_expand) Parse arguments error: No such file or directory
 [AO_ALSA] alsa-lib: pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM hw:0,1,AES0=6
 [AO_ALSA] Format ac3be is not supported by hardware, trying default.
 AO: [alsa] 48000Hz 2ch ac3le (2 bytes per sample)
 ID_AUDIO_CODEC=hwac3
 [Mixer] No hardware mixing, inserting volume filter.
 [format] Sample format big-endian AC3 not yet supported 
 Starting playback...
   MPlayer interrupted by signal 11 in module: decode_audio
 ID_SIGNAL=11
 - MPlayer crashed by bad usage of CPU/FPU/RAM.
   Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
   disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
 - MPlayer crashed. This shouldn't happen.
   It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
   gcc version. If you think it's MPlayer's fault, please read
   DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
   won't help unless you provide this information when reporting a possible bug.


WHich fix did you use? there was 4 different spteps for 4 different things. ANd for Mplayer. just reinstall. Mplayer has nothing to do with this fix here.  we simply update your alsa - and remove pulse audio ( in teh last section). I did not mention Mplayer in any of the steps :S. this is weird. but from ur post ur Mplayer is not fuctioning due to errors whithin Mplayer not your sound card or pulse audio

---

### Post by linuxgeek77 on 2010-03-18
> **leorolla said:**
> Even with linux-backports-modules-alsa-karmic-generic ?

From Karmic repositories, and without recompiling alsa or rebuilding kernel, I got:

```
$ uname -r
2.6.31-20-generic
$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Feb  8 2010 for kernel 2.6.31-20-generic (SMP).
$ apt-cache policy linux-backports-modules-alsa-2.6.31-20-generic
linux-backports-modules-alsa-2.6.31-20-generic:
  Installed: 2.6.31-20.22
  Candidate: 2.6.31-20.22
  Version table:
 *** 2.6.31-20.22 0
        901 http://archive.ubuntu.com karmic-updates/main Packages
        100 /var/lib/dpkg/status
$ 

```

Oh if they added them recently to teh backports i didnt have an access to that when karmic / mint 9 came out

---

### Post by yorgmeister on 2010-03-20
Posted by linuxgeek77

WHich fix did you use? there was 4 different spteps for 4 different things. ANd for Mplayer. just reinstall. Mplayer has nothing to do with this fix here. we simply update your alsa - and remove pulse audio ( in teh last section). I did not mention Mplayer in any of the steps :S. this is weird. but from ur post ur Mplayer is not fuctioning due to errors whithin Mplayer not your sound card or pulse audio

I tried you first fix, it did not work, so I tried your second fix. the sound worked great for one mkv file. then after a restart the system seemed to reset itself and I ended up with the same popping and broken up audio, through my hdmi cable. Before I tried you fixes mplayer worked great except my audio through hdmi was all broken up. after your fixes mplayer exits unexpectantly with exit code 1, but all my other players work. I have tried to re-install, same result. please help!

thanks, yorgie

 		                   		  		  		  		  		  	   	 		[IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG]   		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=8982590") 		 		  	 	 	 	 		  		 		 		 			[[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=8982590")usted

---

