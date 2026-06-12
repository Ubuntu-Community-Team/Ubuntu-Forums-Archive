---
title: "Mplayer won't play commercial DVDs after upgrade to 10.10"
date: 2011-04-12
forum: General Help
---

### Post by -kg- on 2011-04-12
I recently upgraded to Maverick via the Update Manager, and just tried to play a commercial DVD.  MPlayer won't play it, though VLC will.  I had a heckuva time getting it to display with the correct aspect ratio and screen position, though.

I have all the requisites installed that I found through my research, but I couldn't find anything that seemed to relate exactly to my problem (under 10.10).  Has anyone had any experience with this and can suggest something?

Thanks!

---

### Post by -kg- on 2011-04-13
The requisite time has passed...Bump!

Any suggestions?  As soon as my BOINC work units are finished, I'm going to do a fresh install and put it all together again.  I'd like to fix it, though.  A learning experience, and all that.

---

### Post by sam123 on 2011-04-13
Try this:

export DVDCSS_METHOD=title;mplayer

---

### Post by SeijiSensei on 2011-04-13
Play it from the command line and see what errors mplayer throws:

```
mplayer dvd://1
```

will play the first track.  See [this guide]("http://www.mplayerhq.hu/DOCS/HTML/en/dvd.html") for details.

---

### Post by alphaamanitin on 2011-04-13
First check and make sure you have the most up to date libdvd4 in your synaptic package manager.  If you do have it reinstall it.  Also, not all DVDs will play, it is just a licensing issue you have to deal with.

AlphaA

---

### Post by -kg- on 2011-04-14
> **alphaamanitin said:**
> First check and make sure you have the most up to date libdvd4 in your synaptic package manager.  If you do have it reinstall it.  Also, not all DVDs will play, it is just a licensing issue you have to deal with.

AlphaA

I'll try the suggestions, but the particular DVD played in MPlayer before I upgraded, so I wouldn't think that's the issue.

Thanks!

---

### Post by -kg- on 2011-04-16
OK, I tried reinstalling libdvdread4 (that's what you meant, right?  There is no libdvd4 in the repos that I can find) and libdvdcss2, to boot.  It didn't help.

> **SeijiSensei said:**
> Play it from the command line and see what errors mplayer throws:

```
mplayer dvd://1
```

will play the first track.  See [this guide]("http://www.mplayerhq.hu/DOCS/HTML/en/dvd.html") for details.

The following is the results:

```
:~$ mplayer dvd://1
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
libdvdread: Using libdvdcss version 1.2.10 for DVD access
There are 24 titles on this DVD.
There are 1 angles in this DVD title.

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000160
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000240
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000002fb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x000003df
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0000049a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0007135b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00071427
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x00071516
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x000715d1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00072dfb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00072eb6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x000732db
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00073396
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x000736f1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x00095866
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x0034bb45
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x0034bc00
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x0034bccf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x0034bd8a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x0035f655
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x0035f710
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x003b2b9b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x003b2c56
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_0.VOB at 0x003b5511
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x003b55cc
libdvdread: Elapsed time 0
libdvdread: Found 12 VTS's
libdvdread: Elapsed time 0
number of audio channels on disk: 0.
number of subtitles on disk: 0
MPEG-PS file format detected.
MPEG: No audio stream found -> no sound.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  6000.0 kbps (750.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
Audio: no sound
Starting playback...
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 720x540 Planar YV12 
[mpeg2video @ 0x7f7a65a88020]ac-tex damaged at 23 7
[mpeg2video @ 0x7f7a65a88020]Warning MVs not available
[mpeg2video @ 0x7f7a65a88020]concealing 1035 DC, 1035 AC, 1035 MV errors
V:   0.7  16/ 16 66%  9%  0.0% 0 0 

Exiting... (End of file)
```

Like I said, Mplayer played this specific DVD fine before the upgrade, but not afterwards.  VLC plays it fine, but that's not the media player I want to use.  Besides that, Mplayer is the default player, so one would think that it would work at least as well as an add-on.

Oh yes, I also did a check for additional drivers...there were none available (nothing surprising to me there).  Any ideas?

---

### Post by andrew.46 on 2011-04-16
> **-kg- said:**
>  Any ideas?

Perhaps uninstall the repository version and try the latest, available from this PPA:

[https://launchpad.net/~motumedia/+archive/mplayer-daily](https://launchpad.net/~motumedia/+archive/mplayer-daily)

---

### Post by andymorton on 2011-04-16
I had the same problem a few weeks ago. I got round by using VLC instead of mplayer. 

andy

---

### Post by SeijiSensei on 2011-04-16
> **-kg- said:**
> The following is the results:

```
:~$ mplayer dvd://1
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
libdvdread: Using libdvdcss version 1.2.10 for DVD access
There are 24 titles on this DVD.
There are 1 angles in this DVD title.

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000160
libdvdread: Elapsed time 0

[etc.]

```

So far so good.  libdvdread is unlocking the CSS-encrypted chapters on the disk with libdvdcss.

```

number of audio channels on disk: 0.
number of subtitles on disk: 0
MPEG-PS file format detected.
MPEG: No audio stream found -> no sound.

```

This, on the other hand, is not so good.  Let's put this aside for a moment and look at the video.

```

VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  6000.0 kbps (750.0 kbyte/s)
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
[vdpau] Error when calling vdp_device_create_x11: 1

```

It tries a bunch of video drivers.  As you'll see below, it ends up using xv, which should be the best choice in many situations.

```

Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)

```

Good, we're using libavcodec to decode the video.

```

Audio: no sound
Starting playback...
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 720x540 Planar YV12 
[mpeg2video @ 0x7f7a65a88020]ac-tex damaged at 23 7
[mpeg2video @ 0x7f7a65a88020]Warning MVs not available
[mpeg2video @ 0x7f7a65a88020]concealing 1035 DC, 1035 AC, 1035 MV errors
V:   0.7  16/ 16 66%  9%  0.0% 0 0 

Exiting... (End of file)
```

I searched Google for "ac-tex damaged at" and found [this bug]("https://roundup.libav.org/issue2405").  It's marked as a "regression" which means it reappeared in a later build of the software.  You can try using a different mpeg2 decoder instead of libavcodec like that thread suggests.  Try this:

```
mplayer -vc mpeg12 -vo xv /path/to/file
```

and see if it plays correctly.  I still don't know what you should do about the audio.  If you were using ALSA before the upgrade, try switching to PulseAudio like this:

```
mplayer -vc mpeg12 -vo xv -ao pulse /path/to/file
```

I suggest you install smplayer so you can choose among different codecs and drivers from drop-down menus. In Options > Preferences > General you can easily select the options you want mplayer to use for video and audio.

You might also search Google for those other two error strings and see what comes up.

---

### Post by -kg- on 2011-04-16
I appreciate all the work you've done, and I'll keep this thread open.

At the moment, though, my BOINC Work Units are almost run out, and I think I'm going to go ahead and fresh (re-)install 10.10.  I have some other issues which popped up with the upgrade, and truth be told, I've never had a completely successful upgrade on this laptop.

Some of the former attempts have been unmitigated disasters, and at first I thought this was going to be my first success, but there are several niggling problems that popped up...enough that I'm just going to go ahead and completely re-install instead of trying to mess with them.

I'm thinking that, once 11.04 is released I'll go ahead and fresh install that, as well.  I may go ahead and install the Beta...I haven't made up my mind on that.  That's what I was really shooting for...trying out Unity.  Otherwise I would have stayed with the LTS version.

Hopefully, with the fresh install everything will "just work" once again.  Ubuntu has largely "just worked" with every release from Jaunty on.  Thanks again, and I'll check those links out.  I'm always up for learning something new.

---

### Post by -kg- on 2011-04-16
Just an FYI and FWIW...

I tried a permutation of the command you gave me.  The command I issued was:

```
:~$ mplayer -vc mpeg12 -vo xv -ao pulse dvd://1
```

The command had an output into terminal, mplayer launched momentarily, then closed.  I think I can see why, as determined from the terminal output:

```
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
libdvdread: Using libdvdcss version 1.2.10 for DVD access
There are 24 titles on this DVD.
There are 1 angles in this DVD title.

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000160
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000240
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000002fb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x000003df
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0000049a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0007135b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00071427
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x00071516
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x000715d1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00072dfb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00072eb6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x000732db
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00073396
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x000736f1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x00095866
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x0034bb45
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x0034bc00
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x0034bccf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x0034bd8a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x0035f655
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x0035f710
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x003b2b9b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x003b2c56
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_0.VOB at 0x003b5511
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x003b55cc
libdvdread: Elapsed time 0
libdvdread: Found 12 VTS's
libdvdread: Elapsed time 0
number of audio channels on disk: 0.
number of subtitles on disk: 0
MPEG-PS file format detected.
MPEG: No audio stream found -> no sound.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  6000.0 kbps (750.0 kbyte/s)
==========================================================================
Forced video codec: mpeg12
Opening video decoder: [libmpeg2] libmpeg2 MPEG 1/2 Video decoder
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Audio: no sound
Starting playback...
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 720x540 Planar YV12 
V:   0.7  16/ 16 27%  8%  0.0% 0 0 

Exiting... (End of file)
```

What this tells me is that it played the file...the first file...and then exited.  Still no sound...I can't imagine what would be causing that.  VLC plays the DVD fine and with sound.

---

### Post by SeijiSensei on 2011-04-16
Did you try dvd://2 and so forth? If the first file is really as short as your output suggests, maybe it just doesn't have any sound.  It could be the FBI warning or something like that.

Do other programs that use the audio system like Flash videos or music files still work the same way they did before the upgrade?

---

