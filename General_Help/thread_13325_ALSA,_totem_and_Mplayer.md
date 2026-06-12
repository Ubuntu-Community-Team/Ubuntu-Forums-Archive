---
title: "ALSA, totem and Mplayer"
date: 2005-01-30
forum: General Help
---

### Post by Yukino on 2005-01-30
I have a problem with the sound. I'm using alsa plugin, but I don't know how configure totem. I see the images but I don't heard anything. 

I have the same problem with Mplayer. I try 
$ gmplayer -ao alsa

 but I get this error

"Could not open/initialize audio device -> no sound"

and 

$ gmplayer -ao help
Available audio output drivers:
        mpegpes DVB audio output
        oss     OSS/ioctl audio output
        null    Null audio output
        pcm     RAW PCM/WAVE file writer audio output
        plugin  Plugin audio output

I don't understand why alsa don't appear. Xmms works fine with alsa plugin.

Anybody could help me?

---

### Post by ctt1wbw on 2005-01-30
Check to see if you have alsa-oss installed.  If not, download it via synaptic and then reboot.  Once rebooted, recompile and make/make install the MPlayer program, then reboot again.  See if that works.  Plus, there's a giant thread in the faq/how-to section about this.  :)

---

### Post by ow50 on 2005-01-30
When/if recompiling mplayer use:
"./configure --enable-gui --enable-alsa"

And the giant thread mentioned would be [this one](http://www.ubuntuforums.org/showthread.php?t=94).

---

### Post by Yukino on 2005-01-31
In fact, when I compiled Mplayer, I read that thread and I did it step by step.
I had downloading alsa-oss before compile Mplayer. I have just recompiled Mplayer using 
./configure --enable-gui --enable-alsa, and I continue with the same problem.

gmplayer -ao help
Available audio output drivers:
        mpegpes DVB audio output
        oss     OSS/ioctl audio output
        null    Null audio output
        pcm     RAW PCM/WAVE file writer audio output
        plugin  Plugin audio output

And "Could not open/initialize audio device -> no sound"

:(

---

### Post by ctt1wbw on 2005-01-31
Go back through synaptic and make sure you have the alsa packages.  Sounds to me like you're missing a few.

---

### Post by Yukino on 2005-01-31
First of all, thanks for your help  :D 

I think I have all necesary packages... If I didn't, can I play mp3 with xmms (with alsa) without problems?

I'm very new to linux and I'm starting to worry..  :sad:

---

### Post by ups on 2005-01-31
u might want to try this: run the file using mplayer:
```
mplayer filename.ext
```
if you get both audio and video, then it's probably a problem with the config files (mplayer uses a seperate config file when running as gmplayer) . i had a similar problem, and solved it by deleting the ~/.mplayer/gui.conf file, and then running gmplayer. it will reset all the settings to the defaults, and the gui.conf file will be recreated.

---

### Post by Yukino on 2005-01-31
mplayer doesn't work...

$ mplayer -ao alsa file.avi
[..]
Checking audio filter chain for 44100Hz/2ch/16bit -> 44100Hz/2ch/16bit...
AF_pre: af format: 2 bps, 2 ch, 44100 hz, little endian signed int
AF_pre: 44100Hz 2ch Signed 16-bit (Little-Endian)
Could not open/initialize audio device -> no sound.
Audio: no sound
Starting playback...
[...]

---

### Post by ups on 2005-01-31
[QUOTE=Yukino]mplayer doesn't work...

$ mplayer -ao alsa file.avi
[..]
Checking audio filter chain for 44100Hz/2ch/16bit -> 44100Hz/2ch/16bit...
AF_pre: af format: 2 bps, 2 ch, 44100 hz, little endian signed int
AF_pre: 44100Hz 2ch Signed 16-bit (Little-Endian)
Could not open/initialize audio device -> no sound.
Audio: no sound
Starting playback...
[...][/QUOTE]
oh no, without specifying the driver... just use **mplayer file.avi**

---

### Post by Yukino on 2005-01-31
Yes, I tried before without specifying the driver. This is what I got..

```

$ mplayer file.avi

           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try -hardframedrop.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.
```

and no sound at all...

```
$ mplayer -ao sdl file.avi

Checking audio filter chain for 44100Hz/2ch/16bit -> 44100Hz/2ch/16bit...
AF_pre: af format: 2 bps, 2 ch, 44100 hz, little endian signed int
AF_pre: 44100Hz 2ch Signed 16-bit (Little-Endian)
Could not open/initialize audio device -> no sound.
Audio: no sound
Starting playback...
```

Thanks for your help

---

### Post by llamakc on 2005-02-05
I compiled MPlayer from one of the threads here in the forums and I too had the no sound problem. Turns out stupid-@ss me still had RealPlayer in my processes. Killing that did the trick. So, is anything blocking access to /dev/dsp?

---

