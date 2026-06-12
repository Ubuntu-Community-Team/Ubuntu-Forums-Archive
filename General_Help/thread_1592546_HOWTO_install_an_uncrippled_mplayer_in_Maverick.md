---
title: "HOWTO: install an uncrippled mplayer in Maverick"
date: 2010-10-10
forum: General Help
---

### Post by fubarbundy on 2010-10-10
**Preamble:** So, like a lot of people I guess, I've been using the rvm PPA to get a working new/hotness mplayer in Ubuntu instead of their old/busted version. Well, with Maverick, there are no rvm packages, and Ubuntu's version is now new/still busted - for example, AC3 on the fly encoding (-af lavcac3enc) is missing (aside to Ubuntu packagers who will never read this: I assume this is because of patent bollocks not all of us live in software patent land - give us the damn option to install software for which patents don't apply in our country!). This fix took me a couple of days to figure out a nice-ish way of doing it, so I thought I'd share in case it helps. If it does, please say so :)

**The HOWTO**

(Make sure you get the correct packages for your system, e.g. i386, amd64)

[LIST]
[*]Create a folder called mplayer on your desktop.


[*]Download the following to it:

From Debian Lenny ([http://packages.debian.org/lenny/libartsc0](http://packages.debian.org/lenny/libartsc0)):

libartsc0

From [http://debian-multimedia.org/dists/unstable/main](http://debian-multimedia.org/dists/unstable/main):

libbs2b0
libfaac0
libx264-104
mplayer-nogui


[*]Fix dependencies:

Extract mplayer-nogui (right-click, Extract Here)
Delete the original mplayer-nogui package
In the extracted folder, open DEBIAN/control, and make the following changes:

Version: 2:1.0~rc3++svn20100804-0.1 **change to** Version: 2:1.0~rc3++svn20100804-0.1-ubuntuhack
libjpeg62 (>= 6b1) **change to** libjpeg62 (>= 6b-1)
liborc-0.4-0 (>= 1:0.4.6) **change to** liborc-0.4-0 (>= 0.4.6)


[*]Rebuild mplayer-nogui:

In a terminal:

```
cd ~/Desktop/mplayer
dpkg-deb --build mplayer-nogui_*
```


[*]Install:

```
sudo dpkg -i *deb
```
[/LIST]

**Notes:**

If you want to use mplayer instead of mplayer-nogui, you will also need mplayer-skins from debian-multimedia.org.

To help people searching for the error in question to find this thread: the error was: Couldn't find audio filter 'lavcac3enc'.

---

### Post by andrew.46 on 2010-10-10
Hi fubarbundy,

I believe my own compiled copy of the svn MPlayer has this filter available:

```

andrew@skamandros~$ mplayer -af help | grep lavcac3enc
  lavcac3enc     : runtime encode to ac3 using libavcodec

```

but I appear to be a little too obtuse to get it working :(. Can you explain its usage and syntax a little? Google has not been terribly useful with this one...

Andrew

---

### Post by DodgeV83 on 2010-10-24
Thanks so much for this!  Note, I also had to install the following to get it to install:

```
sudo apt-get install libdirac-decoder0 libggi2 libggiwmh0 libgii1 libggi-target-x libgii1-target-x
```

I can also confirm Andrew's compiled mplayer gave the following error, whereas yours works fine with decoding any 5.1 stream to AC3 on the fly (for my receiver):

```
Couldn't find audio filter 'lavcac3enc'
```

Would you happen to know what solved this?  If we can figure this out, we won't have to rely on the an official package, in-case a future release disables this.

Thanks again :)

Edit:  For those of you looking to use these packages to force mplayer to encode 5.1 to AC3 on the fly, I also had to add the following to my mplayer config file located here: /home/<username>/.mplayer/config

```
# Device, passthrough and on-the-fly-encoding
#=====================
# Default device is configured in the KDE4 system settings, so here I used just ao=alsa (not : ao=alsa:device=hw=0.1)
ao=alsa
#For both AC-3 and DTS passthroug, use -afm hwac3
afm=hwac3,
channels=6
af=scaletempo,lavcac3enc=1:640:3 

```

and set up smplayer to always use S/PDIF as follows:
Options/Preferences/General/Audio, untick enable the audio equalizer and tick AC3/DTS pass-through S/PDIF and select 6 (5.1) Surround channels by default.

Options/Preferences/Advanced/Options for MPlayer, enter the following in the Audio filters text box: lavcac3enc=1:640

Taken from this thread: [http://mepislovers.org/forums/showthread.php?t=23034](http://mepislovers.org/forums/showthread.php?t=23034)

---

### Post by kiplingw on 2010-10-24
I'm using an official package and when I run...

$ mplayer -af=scaletempo,lavcac3enc=1:640:3 -channels 6 -afm hwac3 some_file.mp3

I get:

[INDENT]Couldn't find audio filter 'lavcac3enc'
[libaf] Couldn't create or open audio filter 'lavcac3enc'
Error at audio filter chain pre-init![/INDENT]

The package needs to be rebuilt and I'm assuming something needs to modified in what ./configure is being passed via debian/rules. Somewhere buried in there is a switch to enable lavcac3enc.

Thoughts?

---

### Post by Jazz11 on 2010-12-12
hi,
i'm getting the following error:

dpkg-deb: failed to open package info file `mplayer-nogui_*/DEBIAN/control' for reading: No such file or directory

what am i missing ?

---

### Post by fubarbundy on 2010-12-30
An update: [https://launchpad.net/~motumedia/+archive/mplayer-daily](https://launchpad.net/~motumedia/+archive/mplayer-daily) has packages that aren't as broken as the stock ones - they at least seem to fix the AC3 encoding issue.

---

### Post by kiplingw on 2010-12-30
Thanks fubarbundy. The PPA's package appears to have been built with lavcac3enc enabled. After installing it, I went to test it.

```

$ mplayer -af scaletempo,lavcac3enc=1:640:3 -channels 6 -afm hwac3 tune.mp3 
MPlayer SVN-r32735-4.4.5 (C) 2000-2010 MPlayer Team

Playing tune.mp3.
Audio only file format detected.
==========================================================================
Trying to force audio codec driver family hwac3...
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 192.0 kbit/13.61% (ratio: 24000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   2.1 (02.1) of 317.0 (05:17.0)  0.5% 
[...]

```

My receiver appeared to just be receiving a regular vanilla stereo LPCM stream as usual and not the remixed AC3 stream I expected.

Ideas?

---

### Post by DodgeV83 on 2011-05-04
> **DodgeV83 said:**
> Thanks so much for this!  Note, I also had to install the following to get it to install:

```
sudo apt-get install libdirac-decoder0 libggi2 libggiwmh0 libgii1 libggi-target-x libgii1-target-x
```

I can also confirm Andrew's compiled mplayer gave the following error, whereas yours works fine with decoding any 5.1 stream to AC3 on the fly (for my receiver):

```
Couldn't find audio filter 'lavcac3enc'
```

Would you happen to know what solved this?  If we can figure this out, we won't have to rely on the an official package, in-case a future release disables this.

Thanks again :)

Edit:  For those of you looking to use these packages to force mplayer to encode 5.1 to AC3 on the fly, I also had to add the following to my mplayer config file located here: /home/<username>/.mplayer/config

```
# Device, passthrough and on-the-fly-encoding
#=====================
# Default device is configured in the KDE4 system settings, so here I used just ao=alsa (not : ao=alsa:device=hw=0.1)
ao=alsa
#For both AC-3 and DTS passthroug, use -afm hwac3
afm=hwac3,
channels=6
af=scaletempo,lavcac3enc=1:640:3 

```

and set up smplayer to always use S/PDIF as follows:
Options/Preferences/General/Audio, untick enable the audio equalizer and tick AC3/DTS pass-through S/PDIF and select 6 (5.1) Surround channels by default.

Options/Preferences/Advanced/Options for MPlayer, enter the following in the Audio filters text box: lavcac3enc=1:640

Taken from this thread: [http://mepislovers.org/forums/showthread.php?t=23034](http://mepislovers.org/forums/showthread.php?t=23034)

Was trying to get this working on my Natty installation, and actually had to UNcheck "AC3/DTS pass-through S/PDIF" to get it to work.  All other settings and instruction are identical...go figure.

At least it works :)

---

