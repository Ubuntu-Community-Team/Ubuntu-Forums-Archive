---
title: "VLC crashes when playing a video"
date: 2009-08-05
forum: General Help
---

### Post by mybrownianmotion on 2009-08-05
Hi all, My laptop started having a problem with vlc crashing when I start a video, it seems to be an X11 error, but I have no idea what could be causing it. I have had this problem before, and the only way I was able to fix it is by backing up my home directory, and all my installed packages, and reinstalling ubuntu, and reinstalling everything. VLC worked for playing videos after that, but now it started crashing again, I am assuming it was from something that update manager changed.

this is the vlc output in terminal as it crashes
```
VLC media player 1.0.1-rc Goldeneye
[0x961f140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 140.3 failed with error code 8:
 BadMatch (invalid parameter attributes)
[????????] x11 video output notice: buggy X11 server claims shared memory
[????????] x11 video output notice: support though it does not work (OpenSSH?)
[????????] x11 video output error: X11 request 140.3 failed with error code 8:
 BadMatch (invalid parameter attributes)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (MIT-SHM)
  Minor opcode of failed request:  3 (X_ShmPutImage)
  Serial number of failed request:  61
  Current serial number in output stream:  62
```

this is the terminal output using the verbose option with vlc
```
mybrownianmotion@LinuxBoxLaptop:~$ vlc -v
VLC media player 1.0.1-rc Goldeneye
[0x9a40328] main demux warning: no access_demux module matching "file" could be loaded
[0x998f140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x9d5e2e8] avcodec decoder warning: Physical channel configuration not set : guessing
QPainter::begin: Paint device returned engine == 0, type: 1
[0xa05f108] freetype spu text warning: unbreakable string
[0xa085968] scaletempo audio filter warning: bad input or output format
[0xa085968] main audio filter warning: no audio filter module matching "scaletempo" could be loaded
[0xa0e7080] main audio output warning: PTS is out of range (-8298), dropping buffer
[0xa0e7080] main audio output warning: PTS is out of range (-34186), dropping buffer
[0xa0e7080] main audio output warning: output date isn't PTS date, requesting resampling (49955)
[0xa0e7080] main audio output warning: buffer is 49791 late, triggering upsampling
[????????] x11 video output error: X11 request 132.19 failed with error code 8:
 BadMatch (invalid parameter attributes)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  102
  Current serial number in output stream:  103
[0xa0e7080] main audio output warning: output date isn't PTS date, requesting resampling (47049)

```

obviously, reinstalling everything is not something that I would want to do, as it takes so long, Does anyone have any ideas how to fix this? Thanks

---

### Post by mybrownianmotion on 2009-08-09
bump

---

### Post by noname580 on 2009-08-16
open vlc via application menu.  go to tools>preferences and uncheck embed video in interface.  should solve your problem.

---

### Post by mybrownianmotion on 2009-08-17
Thanks, that worked. The video plays separate from the controls now, which isnt a big deal, I am just glad the videos play again. thanks again

---

### Post by WindPower on 2009-09-19
Same error here. A fix I found to get the embedded video is to switch to the OpenGL video output mule in the preferences. However, playback becomes choppy when playing high-def content with it, and the video isn't centered in the window, it's aligned on the left instead.
I looked forward to VLC 1.0 to finally get embedded video! :( Sounds like we have to wait even longer.

---

