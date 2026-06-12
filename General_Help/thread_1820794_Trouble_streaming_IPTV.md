---
title: "Trouble streaming IPTV"
date: 2011-08-08
forum: General Help
---

### Post by cyberjar09 on 2011-08-08
I have an iptv on a multicast address streaming to my computer elsewhere via RJ45 (ethernet) cable. The stream seems stable but after a while, the display starts framing and I have to close the application and restart it. 

I initially thought the problem was isolated at the iptv because when I tamper with the antenna, the display goes bad and then recovers when I place it back. This goes on until I tamper with it enough times (5-6 on average) and then the video feed totally freezes and does not recover.

I have tested over UDP in VLC media player as well as over HTTP in chrome browser (totem plugin). 

Next I booted into the Windows 7 partition of the same computer, fired up VLC and (God forbid), its running without a hitch! I even tampered with the antenna as I did on Ubuntu but windows seems to be able to handle the recovery much better than Ubuntu. 

The computer I am testing on is running 10.04 LTS. Any known issue in regard to this matter? Should I try some other Linux distro that has an alternate implementation? I feel it is eventually boiling down to some problem with Gstreamer but I am only speculating. please help....

Thanks.

---

### Post by cyberjar09 on 2011-08-10
Update: I installed medibuntu, ffmpeg, vlc plugins and some other codecs and libraries. 

Now VLC is able to seamlessly recover from the distortion of the signal but totem still behaves the same(freezing after some time). This would lead me to believe that the problem does not lie in the operating system but the plugins and how they handle the breakage of the stream. 

I also tried gecko plugins for Chrome browser but they dont seem to work either.

Problem: 
I need the stream in my Chrome browser. Totem plugin is the only one I have got working in Chrome. Gecko and VLC plugin do not work. I need to now either get VLC to playback the stream in the browser or find a fix for the totem plugin. 

Does VLC use Gstreamer library or does it have its own engine? I assume it does not work with gstreamer and the problem can be isolated to gstreamer. 

Also, I test totem by launching ```
totem --debug udp://xxx.x.x.x:xxxx
``` but the information provided is not at all a clear indicator of the state of the player. VLC when launched with ```
vlc -vvv udp://xxx.x.x.x:xxxx
``` is very informative and I can follow the breakage if there is any.

Help me please.

---

### Post by cyberjar09 on 2011-08-10
Should I move this thread to the "Multimedia and Video" sub-forum? How do I do that?

---

### Post by cyberjar09 on 2011-08-10
*bump*

---

