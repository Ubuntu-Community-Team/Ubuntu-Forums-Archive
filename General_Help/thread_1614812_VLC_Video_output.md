---
title: "VLC Video output"
date: 2010-11-06
forum: General Help
---

### Post by DeMus on 2010-11-06
Hi,
I mostly use VLC as movieplayer and I just tried to play a blu-ray movie using it, but it is as if I am looking at a slide show. I see picture by picture passing, instead of a fluent movie.
As you can see in my specs at the bottom of this post, my computer should be well prepared to play a movie like that.
When I look at the system monitor I see VLC is using one of the CPU cores at 100%. I have tried to select another output in VLC but it only gets worse when I choose anything else than Default. I was hoping I could use the nVidia vdpau system, but I can not select it in VLC.
Is there a way to do so and let the GPU do all the work instead of the CPU? If so, who can tell me how to do this?
I use LinuxMint 9 Isadora, based on Ubuntu 10.04 LTS, in a 64-bits version, I have kernel 2.6.32-21, nVidia driver 195.36.24. VLC version is 1.1.2 The Luggage.
If you need more info please ask and I try to give it.

---

### Post by P4man on 2010-11-06
install libvdpau1 and I think VLC also needs vdpau-va-driver but Im not entirely sure.
vdpau support in vlc is a bit hit and miss though, may I suggest trying smplayer? Or xbmc. Either support vdpau pretty well, especially xbmc.

---

### Post by DeMus on 2010-11-06
> **P4man said:**
> install libvdpau1 and I think VLC also needs vdpau-va-driver but Im not entirely sure.
vdpau support in vlc is a bit hit and miss though, may I suggest trying smplayer? Or xbmc. Either support vdpau pretty well, especially xbmc.

Thanks P4man. I have installed libvdpau-1 but can not find the vdpau-va-driver.
I just tried XBMC which does play the movie correctly, although when I start it the screen is completely green with stripes. After a while the movie is visible and stays visible. In XBMC I chose vdpau as output so that seems to work.
I must say that I do not like XBMC that much, the interface is so different than other programs, and is so slow. When I want to click a button with my mouse it seems I have to move it several meters before the cursor finally reaches the button.
I will also try smplayer to see if that plays the movie also, including the Dutch subtitles.
Thanks again for your answer.

---

### Post by P4man on 2010-11-06
XBMC is really intended for a TV to be used with a remote. Thats where its absolutely brilliant. I agree as player on the desktop its a bit overkill and the interface not very intuitive with a mouse (use keyboard and it works great though), but since vdpau support is top notch I suggested it so you can see where the problem is.

Anyway, look again for vdpau-va-driver, it should be in synaptic and you do need it for VLC.  More info here:
[http://ubuntuforums.org/showthread.php?t=1037625](http://ubuntuforums.org/showthread.php?t=1037625)

---

### Post by DeMus on 2010-11-06
I tried playing the movie with smplayer but it tells me I don't have the latest mplayer. Well, I added several ppa's for mplayer, nvidia, vdpau and I must have the latest version. Still I get no sound and no subtitles.
In the audio menu there is no choice for any audio stream, for subtitles it is the same. Only video works.
Yes, I know XBMC is for use on TV's. But I only use it on the computer and using the mouse is a pain in the ....
I'll try to learn how to control it by keyboard because it does play the movies other players don't, so I will have to use it.
Thanks again for your answer.

---

### Post by P4man on 2010-11-06
smplayer is a gui over mplayer. I seem to remember in older versions it sometimes had issues identifying the version of mplayer installed, and that does cause problems with subs and audio (I think the popup even says that, doesnt it?)

Can you report the version of mplayer you have?

```
mplayer -v
```

IN smplayer also check options > pref > general > mplayer executable.
Does it just say "mplayer" or something else (like an absolute path) ?

Is smplayer working correctly with non bluray rips?

---

### Post by DeMus on 2010-11-06
> **P4man said:**
> smplayer is a gui over mplayer. I seem to remember in older versions it sometimes had issues identifying the version of mplayer installed, and that does cause problems with subs and audio (I think the popup even says that, doesnt it?)

Can you report the version of mplayer you have?

```
mplayer -v
```

IN smplayer also check options > pref > general > mplayer executable.
Does it just say "mplayer" or something else (like an absolute path) ?

Is smplayer working correctly with non bluray rips?

mplayer -v gives me:
```
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
CPU vendor name: GenuineIntel  max cpuid level: 10
CPU: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz (Family: 6, Model: 15, Stepping: 11)
extended cpuid-level: 8
extended cache-info: 268468288
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNowExt: 0 SSE: 1 SSE2: 1 SSSE3: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/username/.mplayer/codecs.conf'
Reading /home/jan/.mplayer/codecs.conf: Can't open '/home/username/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
```

In smplayer the reference to mplayer is: mplayer (without a path)

I just started another movie and although less menus are greyed-out, I still don't hear sound and I still don't get subtitles. I am able to choose something now, it just doesn't work.
I hope you have more ideas because I can use all the help I can get.

---

### Post by P4man on 2010-11-06
Thats definitely not the latest version of mplayer. Mine is from 2010 and is version 1.0rc4-4.4.5

Perhaps try adding this PPA for mplayer:
[https://launchpad.net/~rvm/+archive/smplayer](https://launchpad.net/~rvm/+archive/smplayer)

Its not bleeding edge but I think that one ought to work with smplayer. If you want bleeding edge, including support for multiple threads, try this one (havent tested myself);
[https://launchpad.net/~ripps818/+archive/coreavc](https://launchpad.net/~ripps818/+archive/coreavc)

---

### Post by DeMus on 2010-11-06
Something has changed: I do have subtitles now but still no sound.

```
mplayer -v
MPlayer UNKNOWN-4.4.3 (C) 2000-2010 MPlayer Team
CPU vendor name: GenuineIntel  max cpuid level: 10
CPU: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz (Family: 6, Model: 15, Stepping: 11)
extended cpuid-level: 8
extended cache-info: 268468288
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNowExt: 0 SSE: 1 SSE2: 1 SSSE3: 1
Compiled with runtime CPU detection.
[B]get_path('codecs.conf') -> '/home/jan/.mplayer/codecs.conf'
Reading /home/username/.mplayer/codecs.conf: Can't open '/home/username/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.[/B]
Usage:   mplayer [options] [url|path/]filename
```

I get reports about not being able to find codec.conf in 2 folders. Are they necessary and if so what do I need to install to get either one of them?

---

### Post by P4man on 2010-11-06
Looks different but I dont like the UKNOWN and its still 4.4.3 :confused:
Maybe you can install the mplayer package from maverick? 

As for the rest of the output, I have the same, so that seems normal. I think you can make config file to use external codecs, but you dont have to, it will use its own.

---

### Post by P4man on 2010-11-06
BTW, check preferences > options > general > audio in smplayer
Perhaps mplayer is okay now, but you just havent configured the audio right.

---

### Post by DeMus on 2010-11-06
> **P4man said:**
> BTW, check preferences > options > general > audio in smplayer
Perhaps mplayer is okay now, but you just havent configured the audio right.

You were right again, my audio settings were not set properly. Now I have video, audio and subtitles. Thank you so very much P4man. You really helped me.

---

### Post by DeMus on 2010-11-06
It seems I wrote too early. I do have a part of the sound, music, background sounds, but no voices. I see people speak but I don't hear them. I do hear for example applause. 
Tried many different settings in the audio preferences of smplayer but nothing seems to work.
What to do now?

---

### Post by P4man on 2010-11-06
Sounds like its using 5.1 audio with a center channel and you dont have a 5.1 setup?  If you dont have it, change that setting in smplayer. If you do have one, double check your pulsaudio configuration.

---

### Post by DeMus on 2010-11-06
> **P4man said:**
> Sounds like its using 5.1 audio with a center channel and you dont have a 5.1 setup?  If you dont have it, change that setting in smplayer. If you do have one, double check your pulsaudio configuration.

I really don't know what to do. I set audio-preferences to Stereo, to 4.0, to 5.1 and nothings chances. I set the audio-preferences in smplayer to different settings and nothing changes.
Where do I have to do what?

```
lspci |grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
```

---

### Post by P4man on 2010-11-06
Your speakersetup is stereo? Check your (pulse) sound preferences, go to hardware, select your audiocard and set the profile to analog stereo duplex (assuming you are using analogue audio).

If that doesnt help, see if the BR rip doesnt have a stereo track (audio > track).

Worst case scenario you could remux the file to  2 channel audio but that shouldnt be necessary.

---

### Post by DeMus on 2010-11-06
It really drives me crazy. I hear the opening tune of Columbia movies, I hear all kind of noises in the movies, I just don't hear the voices. As i wrote before I chose Stereo 2.0, Surround 4.0, 4.1, 5.0, 5.1 and nothing works.
Who can tell me what to do here, I have in total 6 loudspeakers connected to 3 outputs of my audio card it it won't work.

Please help.

---

### Post by mc4man on 2010-11-06
> Who can tell me what to do here, I have in total 6 loudspeakers connected to 3 outputs of my audio card it it won't work.

It may be time for a new thread - there are several people here that know sound issues well but the thread title won't garner much attention.

If your sound pref's are set to 5.1 (from the sound icon - hardware), then possibly check in smplayer as to the audio output driver, -  I'd only use alsa or pulse.

If the audio stream is ac3 here is a decent test file to see if it's your settings or that particlar source material

```
wget http://www.lynnepublishing.com/surround/www_lynnemusic_com_surround_test.ac3
```

=============================================================

For future use - as far as an mplayer ppa this is one to consider - updates every 3 days or so though one doesn't have to update
[https://launchpad.net/~motumedia/+archive/mplayer-daily](https://launchpad.net/~motumedia/+archive/mplayer-daily)

As far as vlc and nvidia - it needs libva (libva1), though vlc needs to be built w/ vaapi support, plus vaapi support in your ffmpeg libs
Standard in 10.10, no idea about your vlc (from a ppa.?
(vdpau in mplayer works better here than vaapi in vlc (maverick, though same previously in 9.10 & 10.04

---

### Post by DeMus on 2010-11-06
Thank you mc4man. I downloaded the test file and it sounds good. The sound comes from the correct speakers.

At the moment I have set the sound preferences to:
Analog Surround 5.1 Output + Analog Stereo Input

In smplayer I chose 6 Channels, (5.1 Surround)
I think this should be good. Not all movies play sound like I would expect. Still I get sometimes background noises but no voices, or nothing at all.

What else should I do?

---

### Post by mc4man on 2010-11-06
If some 5.1 streams are ok and others not so, I guess I'd look at the troublesome media files,  - try to identify the audio stream(s).
ffmpeg -i /path/to/video should provide some info. [mediainfo ]("https://launchpad.net/~shiki/+archive/mediainfo")could also be useful

for mediainfo (gui),either open and drop your file into the 'easy' view or r. click on file open with ...

**Then** switch to html view for more info, text view to copy from if need be.

If you see a eac3 maybe the more up to date mplayer from the link above
(I hope you're keeping track of your ppa usage - disabling ones not in use ect.

And you did ck. that smplayer isn't using oss as the audio driver?

Edit; I'm off to buy a new keyboard - lost l and trying to figure ways to misspell so spell checker can fix is becoming a real pita

---

