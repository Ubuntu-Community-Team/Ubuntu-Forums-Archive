---
title: "help with vlc"
date: 2010-07-20
forum: General Help
---

### Post by Drenriza on 2010-07-20
I need to play a info movie on a monitor through VGA. When done, then re-start the movie and continue to run it, FOR EVER 

How do i do this?
If i install a ubuntu 10.04 server, or a very stripped down ubuntu version (i dont know one) then how do i setup VLC to do what i want it to?

All i can find is stuff about streaming over a network, and nothing on how to stream (local) over vga.

Thanks on advance.
Kind Regards

---

### Post by 3rdalbum on 2010-07-20
Use Ubuntu Desktop, set VLC playing on the monitor, right-click and choose Fullscreen, then right-click again and choose Repeat. Nothing to it, unless I am misunderstanding your 'streaming over VGA'.

---

### Post by Drenriza on 2010-07-20
the device that needs to stream the info-video is a 1200mhz single core, 2gb device. With limited resources. I have already tryed to run the video with lubuntu, and vlc. But it was to laggy and pixel errors. So i would like to install it on a extreamly stripped down ubuntu / linux distro.

And then run it from the command line interface. Over VGA.

I must say my #1 post was not very informing.
Sorry about that. Think i wrote something in #1 wanted to edit it and by mistake removed some information stuff about the device and what i wanted. :(

---

### Post by robsoles on 2010-07-20
Does this video play particularly well on ***any*** computer you can access?

(1) it should be possible to encode the video to play ~ok on the target machine if it plays particularly well on a more powerful PC.

(2) [http://ubuntuforums.org/showthread.php?t=1001970](http://ubuntuforums.org/showthread.php?t=1001970) may have what you are looking for.

---

### Post by Drenriza on 2010-07-20
Yes the video plays well on other (more powerfull) machines.
I think its because its bigger in size and thus take more resources. Resources that arnt available.

---

### Post by robsoles on 2010-07-20
> **robsoles said:**
> ...

(2) [http://ubuntuforums.org/showthread.php?t=1001970](http://ubuntuforums.org/showthread.php?t=1001970) may have what you are looking for.

Did you checkout the thread from that link? It has how to use mplayer from terminal - you will probably have to use apt-get to install the codecs required for your video format manually but otherwise it should cover your need.

---

### Post by Drenriza on 2010-08-04
i try what they did in that thread. But when doing so, it starts loading the file, and then the screen turns on saying
"no signal"

---

### Post by robsoles on 2010-08-04
The display is being driven 'out of range' by the software.

You need to get the full-screen playback configuration to use a mode and size that your monitor can handle.

I am at work and can't think of correct name of settings file but if you google

mplayer user settings file

and sift through the results you might get lucky with enough detail to manage by yourself - post back if not.

---

### Post by robsoles on 2010-08-05
I got home and reviewed as much as I can stand of this thread and thread I linked to twice.

Please try:
```
sudo mplayer -vo vga -ao sdl movie.avi
```

on your hardware.

---

### Post by Drenriza on 2010-08-06
playing 2mmovie.avi.
AVI file format detected.
[aviheader] video stream found, -vid 0
[aviheader] audio stream found , aid 1
video : [FLV1] 1280x720 25.000 fps 1514.5 kbps (184.9 kbyte/s)
error opening/initializing the selected video_out (-vo) device.
---------------------------------------------------------------
opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
---------------------------------------------------------------
No such audio driver 'sd1'
Could not open/initialize audio device -> no sound.
Audio: no sound
Video: no video

Exiting... (end of file)

---

### Post by Drenriza on 2010-08-09
Anyone?

---

### Post by robsoles on 2010-08-09
try

```
sudo mplayer -vo vesa movie.avi
```

also, try searching Google etc for things related to using mplayer from the command line and for ways to determine valid video modes on your equipment.

---

### Post by Drenriza on 2010-08-10
I'm not sure i understand whats going on with this mplayer

Output

```
Home directory /home/support not ours.
AO: [pulse] Init failed: Connection refused
Failed to initialize audio driver 'pulse'
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A: 216.2 (03:36.1) of 2807.7 (46:47.6) 5.5%

Exiting... (End of file)
```

What does this mean?

---

### Post by Drenriza on 2010-08-13
bump

---

