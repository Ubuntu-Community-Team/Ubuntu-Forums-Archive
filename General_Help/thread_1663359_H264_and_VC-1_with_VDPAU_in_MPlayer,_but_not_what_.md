---
title: "H264 and VC-1 with VDPAU in MPlayer, but not what everyone else asks"
date: 2011-01-09
forum: General Help
---

### Post by veggen on 2011-01-09
I can successfully play h264 and vc1 encoded HD videos with vdpau acceleration using Gnome MPlayer or SMplayer, but in order to accomplish this, I have to provide -vc ffh264vdpau/ffvc1vdpau as an extra argument for MPlayer. Now this totally sucks as I have to manually type this in for HD videos and remove for all others every single time... What's worse is that I have to know what the video is in advance so I first need to analyze it before playing.
So, I figured that if there's a way to tell MPlayer to aways use ffh264vdpau codec for h264 and ffvc1vdpau for vc1 videos, I'd be free to just click and watch. Is there any way to accomplish this?

Thanks for any ideas...

---

### Post by cchhrriiss121212 on 2011-01-09
Install smplayer, then put your options here: Preferences>Advanced>Options for Mplayer>Options.

---

### Post by veggen on 2011-01-09
I don't think you read my question right... I know I can do that, but then I have to type in the extra parameters every time I'm playing a h264 or vc1 video and remove them when playing other videos... It makes no sense that I am the one who has to first analyzie the video and then manually force the codes, so I figured I can tell MPlayer to always use e.g ffh264vdpau for playing h264 and be done with it once and for all.
If I leave the -vc ffh264vdpau option on all the time, non-h264 videos won't work...

---

### Post by no2498 on 2011-01-09
not sure if installing vlc would help or not
but it installs some codes with its install

---

### Post by veggen on 2011-01-09
Thanks everyone for responses.
I think I got it figured out. SMPlayer seems to be using vdpau codecs by default if vdpau is selected as the output renderer (which is smart indeed). Gnome MPlayer (which I use) seems to be less smart as I can't see any effect from just setting vdpau as the output renderer. One needs to add this:
```
-vc ffmpeg12vdpau,ffh264vdpau,ffwmv3vdpau,ffvc1vdpau,
```
as an extra MPlayer parameter to get the same effect (the trailing comma is important).
I found most of the info in [this](http://newyork.ubuntuforums.org/showthread.php?t=1037625&page=10) thread. The rest I uncovered by testing it myself.

---

### Post by Jose Catre-Vandis on 2011-01-09
You can set up an mplayer config file for specific file types.

For normal mplayer this goes in ~/.mplayer/config

for example to play all mkv files using vdpau you would put something like this in your config file:

```
[extension.mkv]
profile-desc="Profile for Matroska files"
profile=lang
vo=vdpau
vc=ffh264vdpau
```

in the default section you could put:

```
vo=vdpau,gl2,xv
```

then mplayer tries in that order to play the file

---

### Post by cchhrriiss121212 on 2011-01-09
So set smplayer as the default for mkv and mp4 files (which are typicaly used for h264), then set VLC to open all other video formats like AVI.

---

### Post by Jose Catre-Vandis on 2011-01-09
> **cchhrriiss121212 said:**
> So set smplayer as the default for mkv and mp4 files (which are typicaly used for h264), then set VLC to open all other video formats like AVI.

....but you can have a different profile in mplayer for avi files, so you can use mplayer as default for both. The one I use is as follows:

```
[extension.avi]
profile-desc="Profile for deinterlacing avi files"
vo=gl2
vfm=ffmpeg
vf=pp=lb/hb/vb/dr
```

---

### Post by veggen on 2011-01-10
@Jose Catre-Vandis
Great tips, thanks!

I have just noticed something wierd. When playing with ffh264vdpau, if I load an external subtitle (.srt in my case), memory usage jumps to 700MB and the video starts lagging severly. CPU usage is still very low.

Can someone please confirm?

---

### Post by veggen on 2011-01-10
Anyone?
Just a confirmation... You can play any h264 encoded file with any external subtitle loaded.

---

### Post by veggen on 2011-01-10
Since the problem I'm facing now is completely different than what I've started with, I started a new thread. If anyone is interested in helping me out, please post [here](http://ubuntuforums.org/showthread.php?p=10340116#post10340116).

---

