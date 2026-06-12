---
title: "Avermedia UltraTV 1500 MCE"
date: 2010-02-24
forum: General Help
---

### Post by aphtk on 2010-02-24
I have searched the forums and taken their fatal advice. But for the life of me I cannot get this card working properly.
I have a 
Avermedia UltraTV 1500 MCE...works perfectly under MS Windoze. But on Ubuntu 9.10 (latest updates), I can get video on mplayer but no sound. I know the included firmware is loaded and seems like its working ...any advice is appreciated.

**anang@linux-svr:~$** lspc
...
...roller (rev 02)
**03:07.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)**

From** synaptic** i have the following installed
X.Org X server -- IVTV display driver
libvideo-ivtv-perl
ivtv-utils
v4l2ucp

All dependencies are correctly installed
**anang@linux-svr:~$** mplayer /dev/video0

this yields an mplayer window with static and sound of static


I have the composite input
**anang@linux-svr:~$**v4l2-ctl -i 2
**Video input set to 2 (Composite 1)**
**anang@linux-svr:~$** mplayer /dev/video0

the above yields a perfect tv picture but no sound

**anang@linux-svr:~$** v4l2-ctl --get-audio-input
**Audio input : 1 (Line In 1)**
**anang@linux-svr:~$** v4l2-ctl --get-audio-output
**VIDIOC_G_AUDOUT: failed: Invalid argument**
**anang@linux-svr:~$ **v4l2-ctl --list-audio-outputs[B]
ioctl: VIDIOC_ENUMAUDOUT[/B]



**anang@linux-svr:/proc/asound$ **v4l2-ctl --list-audio-inputs
[B]ioctl: VIDIOC_ENUMAUDIO
    Input   : 0
    Name    : Tuner 1

    Input   : 1
    Name    : Line In 1
[/B]

Setting the audio-input to 0 creates a lot of white noise... there is no way to tell it to set the audio to composite ?

Can anyone tell me what I am doing wrong ?

Thanks a ton in advance !

---

### Post by aphtk on 2010-02-25
is this not the right place to post ?
bump!!

---

