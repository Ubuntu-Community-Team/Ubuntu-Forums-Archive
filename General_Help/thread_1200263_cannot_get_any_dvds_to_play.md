---
title: "cannot get any dvds to play"
date: 2009-06-29
forum: General Help
---

### Post by workshop1702 on 2009-06-29
hi i have tried playing dvds with vlc , totem and kaffiene none will work kaffiene says i need libdvdcss i have followed instructions on several sites i found on the net for installing them for ubuntu 8.04 but after doing this the dvds still wont play , help please.

---

### Post by t4thfavor on 2009-06-30
Did you reboot? Its not usually nessecary, but worth a try.

Also install all of the gstreamer packages for good measure. I know you can play dvs's I have done it.

Also if they wont play on vlc launch it from the command line and read the output, it may help.

---

### Post by linuxrockz on 2009-06-30
I would suggest that you give mplayer a try.
It is excellent and has never failed me.
To install it run

```
sudo apt-get install mplayer
```

Then you can play dvds directly from the commandline using

```
mplayer -vo xv -fs dvd:///
```

You can also play DVDs very easily from the mplayer GUI (gmplayer)

I agree with t4thfavor you can install all the gstreamer packages so that you can play DVDs with Totem.

---

### Post by masux594 on 2009-06-30
if u try to run the program like totem from a terminal by only typing the program name.. When an error occured, in the terminal where u launch the program appear more details of the error that occured.. Maybe only the permissions for using the dvd drive!

Sysc, A

---

### Post by kelvin spratt on 2009-06-30
1st you need to go here [http://www.medibuntu.org/](http://www.medibuntu.org/) this is the official site for all multimedia/free/non free stuff read the guide and all will be sorted very simple.

---

### Post by andrew.46 on 2009-06-30
Hi linuxrocks,

> **linuxrockz said:**
> ```
mplayer -vo xv -fs dvd:///
```

And of course if you hunt down a more modern version of MPlayer you can *also* access dvd menus from the commandline:

```
mplayer -mouse-movements -nocache dvdnav://
```

Andrew

---

### Post by workshop1702 on 2009-06-30
still no good have instaled the gstreamers and also mplayer still wont play .
when i try playing using mplayer from terminal this is what i get.
Couldn't open DVD device: /dev/dvd
No stream found to handle url dvd:///
ing

---

### Post by fooman on 2009-06-30
> **kelvin spratt said:**
> 1st you need to go here [http://www.medibuntu.org/](http://www.medibuntu.org/) this is the official site for all multimedia/free/non free stuff read the guide and all will be sorted very simple.

did you try what kelvin spratt suggested?  ....*add the medibuntu repos*,  then do:

```
sudo apt-get update && sudo apt-get upgrade
```

hope that helps.

---

### Post by workshop1702 on 2009-06-30
yes have installed the medibuntu stuff and done update and upgrade still no good.
kaffiene seems to be the best so far jerky sound but no picture and message saying i need to install the libdvdccs , but if i enter the suggested command into turminal it wont have it .anyone any more ideas please.Thanks again Andrew

---

### Post by colau on 2009-06-30
> **workshop1702 said:**
> yes have installed the medibuntu stuff and done update and upgrade still no good.
kaffiene seems to be the best so far jerky sound but no picture and message saying i need to install the libdvdccs , but if i enter the suggested command into turminal it wont have it .anyone any more ideas please.Thanks again Andrew
```

sudo apt-get install libdvdcss2

```

---

### Post by t4thfavor on 2009-06-30
Maybe a bad dvd drive? I don't know for sure, but it sounds like its having an issue reading/mounting the disk.

---

### Post by cph05a on 2009-06-30
Using totem with xine backend worked for me (I know for sure I didn't have a mounting issue, though).

---

### Post by t4thfavor on 2009-06-30
Glad to hear you got it solved, and the drive is not bad :)

---

### Post by workshop1702 on 2009-06-30
hi again i havent got it solved it still wont work , the dvd player works fine on another pc so its not that it also plays cds fine on this machine .
totem opens then shuts down , vlc does the same , kaffiene does the best it plays the sound sort of , the picture is missing and i get a message saying need to install libdvdcss , as far as i am aware i have already done this .
can someone tell me how to check i have actualy installed them please, or any other ideas on what the problem could be

---

### Post by t4thfavor on 2009-06-30
sudo apt-get install libdvdcss2 or libdvdcss depending on wich one it says you need. If you already have it, the command will tell you so.

---

### Post by workshop1702 on 2009-06-30
looks like i have the libdvdcss ok , still wont work.
just installed gxine this also wont work as when i go through the set up options , when checking for dvd rom it fails saying could not access dvdrom:/dev/dvd so this problem looks like some sort of dvdrom access problem can anyone help please as i dont have a clue

---

### Post by fooman on 2009-06-30
try this:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

scroll down to the instructions for 8.04....good luck.

---

### Post by workshop1702 on 2009-06-30
thanks for the suggestion , affraid i have already been there and done all of what it suggests still does not play dvds. still need help please.

---

### Post by workshop1702 on 2009-07-22
already done this ,tried it  again and terminal says i already have it .
still cannot get any dvds to play anyone any idea what the problem could be please.:confused:

---

### Post by dk06 on 2009-07-22
**Playing Restricted Formats**

  
Follow these steps to play and record most common multimedia formats, including MP3, DVD, Flash, Quicktime, WMA and WMV, including both standalone files and content embedded in web pages. 
 
**Ubuntu 9.04 (Jaunty Jackalope)**

 **[Click here to install the ubuntu-restricted-extras package]("apt:ubuntu-restricted-extras?section=universe?section=multiverse")** 
*The instructions below for 8.10, 8.04 and 7.10 should still also work.* 
 
**Ubuntu 9.04 ,8.10, 8.04 and 7.10**

  
**Synaptic**

 
[LIST]
[*]Go to **Applications** &#8594; **Add/Remove...** 
[*]Set Show: to **All available applications** 
[*]Search for **ubuntu-restricted-extras** and install it. Note that there is also **xubuntu-restricted-extras** (for Xubuntu) and **kubuntu-restricted-extras** (for Kubuntu.) 
[/LIST]
Or open the Terminal, and execute the following command: 

[LIST]
[*]sudo apt-get install ubuntu-restricted-extras
[/LIST]
 
**source: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)**


;)

---

### Post by workshop1702 on 2009-07-23
already done all of this still wont work , i really am at a total loss as to why they wont play anyone any more ideas please

---

### Post by Rarensu on 2009-08-08
Your sudo fetch for the libdvdcss2 saved my life!

I have MPlayer, VCL, and Movie Player. None of them had worked. I ran your code and now Movie Player and VCL both work perfectly. For some reason MPlayer is still broken but I'm too happy to care.

Many thanks!

---

### Post by ubu-lemon on 2009-08-25
I have got the same problem (never had any trouble reading DVD'swith Feisty, it started with Ibex last year)
libdvdccs2 is installed, restricted extras too, medibuntu too
I get with VLC and Movieplayer : 'could not read from resource'
Xine says : 'The source seems encrypted and can't be read. Are you trying to play an encrypted DVD without libdvdcss'
Burning a CD or a DVD does work.
(the DVD's I here tested are old movies (3Musketeers and Final Fantasy) and have no trouble playing on any other DVD-player or computer; the DVD player is said to be able to read bleuraydisks but I wouldn't know, I'd just want it to play a simple movie on a simple DVD, the DVD logo is present on the player as well)


I tried the solution with mplayer (here posted in this thread) and with one dvd nothing happens and I get:

mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd:///.
There are 7 titles on this DVD.
There are 11 chapters in this DVD title.
There are 1 angles in this DVD title.
audio stream: 0 format: ac3 (5.1) language: en aid: 128.
audio stream: 1 format: ac3 (5.1) language: fr aid: 129.
number of audio channels on disk: 2.
subtitle ( sid ): 0 language: en
subtitle ( sid ): 2 language: fr
subtitle ( sid ): 4 language: nl
subtitle ( sid ): 6 language: fr
number of subtitles on disk: 4
MPEG-PS file format detected.

Too many audio packets in the buffer: (4096 in 8257536 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
MPEG: FATAL: EOF while searching for sequence header.
Video: Cannot read properties.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
a52: CRC check failed!  
a52: error at resampling
A:   0.6 (00.6) of 6075.4 ( 1:41:15.4) ??,?% 

[B]
and another DVD does play somehow without sound and slow and/or double images and the terminal tells me this:[/B]

Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd:///.
There are 50 titles on this DVD.
There are 2 chapters in this DVD title.
There are 1 angles in this DVD title.
audio stream: 0 format: ac3 (stereo) language: ja aid: 128.
number of audio channels on disk: 1.
subtitle ( sid ): 0 language: en
subtitle ( sid ): 1 language: fr
subtitle ( sid ): 2 language: de
subtitle ( sid ): 3 language: it
subtitle ( sid ): 4 language: es
subtitle ( sid ): 5 language: nl
number of subtitles on disk: 6
MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 2)  25.000 fps  9800.0 kbps (1225.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
a52: CRC check failed!  
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 768x576 Planar YV12  [fs]
a52: CRC check failed!  1.534 ct:  0.000   1/  1 ??% ??% ??,?% 0 0 
a52: CRC check failed!  
a52: CRC check failed!  (etc...)

---

### Post by ubu-lemon on 2009-09-09
anyone there to help me out ? 
i tried to play the same DVD's with the Vista which was still on this computer and it worked, so it's not a hardware problem either.

Please help me play it on Ubuntu (me and Vista not friends ;) )

---

### Post by ubu-lemon on 2009-09-14
no suggestions?

---

### Post by ubu-lemon on 2009-12-22
problem solved with update (9.10 karmic koala)

---

