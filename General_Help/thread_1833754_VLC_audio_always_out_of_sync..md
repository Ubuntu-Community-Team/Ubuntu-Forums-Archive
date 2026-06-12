---
title: "VLC audio always out of sync."
date: 2011-08-26
forum: General Help
---

### Post by SyQo on 2011-08-26
When I was using Windows, VLC was absolutely amazing. Now that I'm on Ubuntu, it still is amazing, easily the best player out there in terms of functionality, but I'm having an issue that I haven't encountered elsewhere. Regardless of the type of file I am playing (AVI, MKV, MP4), the audio is always a little ahead of the video. Every time I start a new episode of a series, say, I have to go in and set the Audio delay to anywhere between .3 and .5 ms; it isn't that big a deal, but I have the itch to figure out what is wrong. Any assistance would be greatly appreciated.

---

### Post by elliotn on 2011-08-26
try ctrl+l or k just try the ctrl combination it shifts the audio. do that while the video is playing

---

### Post by SyQo on 2011-08-26
I've read about that and it definitely should work, but alas, it does not. Ctrl-K does nothing, where Ctrl-L switches to the Library. : /

---

### Post by sammiev on 2011-08-26
I select tools within VLC then select Track Sync. I use -0.400ms or what ever works for you. :)

---

### Post by scarboni on 2011-08-29
I have the same problem as in the original post.   Two points:

1) In the original post it is already stated that the person knows how to solve the problem on a case by case basis.  The problem here is why is it happening consistently?  VLC worked fine for me before Natty but ever since the OS upgrade the audio has consistently been 200ms faster than any video file played.  I never had to adjust it before and I am unable to find any setting in VLC where I can force it to start with the appropriate delay every time.

2) For those who aren't aware (because it seems like none of the repliers are) to increase the audio delay you press the letter j (on its own with no modifier keys like shift or alt) and to increase the audio delay you press k while the video is playing.

Now - is there anyone who can address the issue of the problem of the audio consistently being out of sync with the video by the same amount of time on any type of video played?  And I reiterate:  yes - we know how to fix it every single time but we'd rather not.

Thanks.

---

### Post by solitaire on 2011-09-10
I'm having the same problem in VLC. (1.1.11)
It's only happened in the past few weeks or so. i have to slow the audio by between -250 and -300 ms every time i play a video.

The video is in sync if I use totem player.

I've tried to purge VLC and reinstall in case it's a config thing, but it's made no difference.
Running Ubuntu 11.04 on a HP 550 Laptop (2Ghz & 2Gb ram)

Only change to my system is adding an extra 1Gb of ram...

---

### Post by rafaelcoelho on 2011-09-14
I'm having this problem too, I usually use -0.400

---

### Post by psrdotcom on 2011-09-14
Might be a bug of VLC .. We can post this in VLC forum

---

### Post by TenPlus1 on 2011-09-14
Make sure you are running the latest version of VLC by going here and following the steps to add the GetDeb repository:

[http://www.getdeb.net/updates/Ubuntu/11.04#how_to_install](http://www.getdeb.net/updates/Ubuntu/11.04#how_to_install)

---

### Post by 3rdalbum on 2011-09-14
Funnily enough, I noticed this yesterday and found the setting for the audio/video sync.

The tooltip for the audio sync feature says that the higher the number, the more delayed the audio will be. In fact, the reverse is true; if the audio is ahead of the video, you need to make the number negative instead of positive.

Now that I know a few other people have the same problem, I'll see if anything I do can fix it.

I'm running 11.10 BTW.

---

### Post by undoIT on 2011-09-14
Thanks.

Tools > Track Syncronization

with a setting between -0.400 s and -0.700 s works well for me.

Is there any way to keep this setting saved so that it is active every time VLC is opened?

---

### Post by sammiev on 2011-09-14
Likely best to send a bug report to VLC. Post it here and likely most people would confirm it and add to it. GL :)

---

### Post by clockworktri on 2011-10-03
ME TOO. I tried purging my files and re-installing and installing other versions, but to no avail. 

Has anyone reported this as a but to VLC yet? 

btw, running 10.04LTS

---

### Post by GBB1 on 2011-10-17
I have the same problem:
- Ubuntu 11.10 with Gnome 3
- VLC 1.1.11
- Audio correction of -300ms
- Haven't tried Totem yet, as I am not at home now

Could this be related to [Pulse Audio]("http://www.fedoraforum.org/forum/showthread.php?t=267353")? I found that it could be the case on [VLC-forums]("http://forum.videolan.org/viewtopic.php?f=13&t=91254").

_Possible solutions proposed by others would be:_
- Start VLC with: 'pasuspender vlc -A alsa'
- Remove Pulse Audio and revert to Alsa
- 'This all should be fixed in VLC 1.1.12 by now. Alternative, turning off tsched in pulse.conf can work around the problem.' Someone knows a PPA for Oneiric?

Any feedback on these guys?

---

### Post by SpEcIeS on 2011-10-17
Compiled the latest 1.1.12 and it seems to be fine.

---

### Post by gofurygo on 2011-10-17
Hello there...

I have experienced this problem on 11.04 as well. I loved VLC on windows but now Im using Totem for watching movies - only.

I do have another issue with VLC though. When playing music - MP3s - VLC is stuttering at the beginning of the song a few times until it plays fine. It also does it when skipping to the next song in the playlist... :( 

Any idea how to fix this guys?

---

### Post by GBB1 on 2011-10-17
> **SpEcIeS said:**
> Compiled the latest 1.1.12 and it seems to be fine.

I tried to compile VLC before, but that didn't go well. Isn't there a PPA somewhere for Ubuntu 11.10? Of how did you compile it? First you installed the normal VLC to have al dependencies and then you compiled?

Thanks for the feedback!

---

### Post by Atermoon on 2011-10-17
Just installed VLC 1.1.12 from this ppa and everything's back to normal.
```
https://launchpad.net/~n-muench/+archive/vlc
```
I can't comment on how stable it is yet but maybe give it a try?

---

### Post by GBB1 on 2011-10-17
> **Atermoon said:**
> Just installed VLC 1.1.12 from this ppa and everything's back to normal.
```
https://launchpad.net/~n-muench/+archive/vlc
```
I can't comment on how stable it is yet but maybe give it a try?

Yup! That's just what I was looking for, thx! I'll give it a spin when I get back home :)

---

### Post by mjuhasz on 2011-10-17
VLC with the bug fix is already in the queue waiting for approval after which it will land in the proposed updates (and eventually a normal update).

Changes: 
 vlc (1.1.12-1) unstable; urgency=low
 .
   * New upstream release.
     - Multiple fixes and improved synchronization for PulseAudio support
       (Closes: #601826, LP: #805807).
     - Fix segmentation fault (LP: #803006).
     - Addd GenericName entries to desktop file (Closes: #640911).
     - Do not ignore the --quiet flag (Closes: #531975).
     - Fix vlc runs xdg-screensaver with signal child blocked (Closes: #640245).
     - Fix crashes when trying to play youtube URLs (Closes: #641507).
   * Drop xulrunner-1.9.1.patch (accepted upstream).
   * Refresh 200_osdmenu_paths.patch.
   * Fix typo in vlc.desktop: Name[nn] -> GenericName[nn].

---

### Post by SpEcIeS on 2011-10-17
> **GBB1 said:**
> I tried to compile VLC before, but that didn't go well. Isn't there a PPA somewhere for Ubuntu 11.10? Of how did you compile it? First you installed the normal VLC to have al dependencies and then you compiled?

Thanks for the feedback!

To build a x86_64 with a dual core processor, use the following:

```
sudo apt-get build-dep -y vlc

./configure --enable-static --build=x86_64-linux-gnu --config-cache --disable-maintainer-mode --disable-update-check --enable-fast-install --prefix=/usr --disable-atmo --disable-fluidsynth --disable-gnomevfs --disable-kate --disable-mtp --enable-x264 --disable-zvbi --enable-a52 --enable-aa --enable-bonjour --enable-caca --enable-dca --enable-dvb --enable-dvbpsi --enable-dvdnav --enable-faad --enable-flac --enable-freetype --enable-fribidi --enable-ggi --enable-gnutls --enable-libass --enable-libmpeg2 --enable-lirc --enable-live555 --enable-mad --enable-mkv --enable-mod --enable-mozilla --enable-mpc --enable-ncurses --enable-notify --enable-ogg --enable-pulse --enable-qt4 --enable-realrtsp --enable-sdl --enable-shout --enable-skins2 --enable-smb --enable-speex --enable-svg --enable-taglib --enable-telx --enable-theora --enable-twolame --enable-vcd --enable-vcdx --enable-vorbis --with-mozilla-pkg=libxul --enable-alsa --enable-dv --enable-pvr --enable-v4l --enable-v4l2  --enable-svgalib

make -j3

make install
```

Use the following CFLAGS for a AMD Athlon(tm) 64 X2 Dual Core Processor 4800+ CPU, or adjust to suit your CPU needs:

```
export CFLAGS="-march=k8 -O2 -msse3 -s -pipe"
```

The following I wrote, and used, in 10.10, which works well still. Remember to adjust the CFLAGS to suit your CPU needs and adjust your make command to the number of cores +1 (2 core CPU = make -j3):

**build-vlc**

```
#!/bin/bash

VR=$2
TBZ=vlc-$VR.tar.bz2
DWNPTH=http://download.videolan.org/pub/videolan/vlc/$VR
BLDPTH=$HOME/build
CFGPRM="--enable-static --build=x86_64-linux-gnu --config-cache --disable-maintainer-mode --disable-update-check --enable-fast-install --prefix=/usr --disable-atmo --disable-fluidsynth --disable-gnomevfs --disable-kate --disable-mtp --enable-x264 --disable-zvbi --enable-a52 --enable-aa --enable-bonjour --enable-caca --enable-dca --enable-dvb --enable-dvbpsi --enable-dvdnav --enable-faad --enable-flac --enable-freetype --enable-fribidi --enable-ggi --enable-gnutls --enable-libass --enable-libmpeg2 --enable-lirc --enable-live555 --enable-mad --enable-mkv --enable-mod --enable-mozilla --enable-mpc --enable-ncurses --enable-notify --enable-ogg --enable-pulse --enable-qt4 --enable-realrtsp --enable-sdl --enable-shout --enable-skins2 --enable-smb --enable-speex --enable-svg --enable-taglib --enable-telx --enable-theora --enable-twolame --enable-vcd --enable-vcdx --enable-vorbis --with-mozilla-pkg=libxul --enable-alsa --enable-dv --enable-pvr --enable-v4l --enable-v4l2  --enable-svgalib"

MTC="echo -en \E[300C\E[$[10]D"
OB="echo -n ["
CB="echo -e \E[0m]"

export CFLAGS="-march=k8 -O2 -msse3 -s -pipe"

sucmsg () {
	$MTC;$OB;echo -en "\E[1;32mSUCCESS";$CB
}

failmsg () {
	err=$1;$MTC;$OB;echo -en "\E[1;31mFAILED";$CB;echo -e "\E[1;31mError: \E[1;33m$err!\E[1;31m\E[0m";tput sgr0;exit 1
}

hlp () {
	echo -e "\E[1;33mUsage: `basename $0` [-b|--build|-i|--install|-u|--uninstall|-h|--help] [Version]";tput sgr0;exit 0
}

[ ! -d $BLDPTH/vlc ] && mkdir $BLDPTH/vlc
[ -d $BLDPTH/vlc ] && cd $BLDPTH/vlc || failmsg "Directory \"$BLDPTH/vlc\" not found"

if [ $# -eq 2 ]; then
	case "$1" in
		-b|--build)
			sudo echo -n;echo -ne "\E[0mBuilding \"\E[1;33mVLC $VR\"\E[0m -> "
			sudo apt-get build-dep -y vlc &> /dev/null
			[ $? -ne 0 ] && failmsg "apt-get could not get build dependencies"

			[ ! -f $TBZ ] && wget -q $DWNPTH/$TBZ
			[ -f $TBZ ] && tar jxf $TBZ || failmsg "tar produced an error"
			[ -d vlc-$VR ] && cd vlc-$VR || failmsg "\"vlc-$VR\" directory not found"

			./configure $CFGPRM &> /dev/null
			[ $? -ne 0 ] && failmsg "configuration failed"

			make clean &> /dev/null;make -j3 &> /dev/null
			[ $? -eq 0 ] && sucmsg || failmsg "build VLC $VR failed"
		;;
		-i|--install)
			sudo echo -n;echo -ne "\E[0mInstalling \"\E[1;33mVLC $VR\"\E[0m -> "
			[ -d vlc-$VR ] && cd vlc-$VR || failmsg "\"vlc-$VR\" directory not found"
			sudo make install &> /dev/null
			[ $? -eq 0 ] && sucmsg || failmsg "installing VLC $VR failed"
		;;
		-u|--uninstall)
			sudo echo -n;echo -ne "\E[0mUninstalling \"\E[1;33mVLC $VR\"\E[0m -> "
			[ -d vlc-$VR ] && cd vlc-$VR || failmsg "\"vlc-$VR\" directory not found"
			sudo make uninstall &> /dev/null
			[ $? -eq 0 ] && sucmsg || failmsg "uninstalling VLC $VR failed"
		;;
		*)
			hlp
		;;
	esac
else
	hlp	
fi

tput sgr0

```

This script is easily modified to compile other software packages. Enjoy ;)

---

### Post by GBB1 on 2011-10-18
Thanks for the script! I did try to install from the PPA and now everything is back to normal. Audio en video with the new VLC 1.1.12 is back in sync.

Btw, I love that simple new interface of Gnome 3 :)

---

