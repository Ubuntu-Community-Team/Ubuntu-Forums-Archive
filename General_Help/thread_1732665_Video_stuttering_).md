---
title: "Video stuttering :)"
date: 2011-04-18
forum: General Help
---

### Post by infohub on 2011-04-18
Hi, I ve been using Ubuntu 10.10 for a while. I have installed it inside windows, because it is much easier. It runs smoothly,but I have problems with video playback. The video stutters slightly when viewed with VLC (normal screen), the stuttering becomes worse in fullscreen. Meanwhile flash videos also have the same problem. Please help me out. 

Some specs

Compaq CQ45 Laptop
Core 2 Duo 2.0Ghz
3gb DDR 2 Ram
256mb NVIDIA Geforce
250gb Hard disk


Does the install inside windows have anything to do with perfromance, including this stuttering issue? Please help me, I love ubuntu!

---

### Post by flipper T on 2011-04-18
have you tried a different player ?

vlc is good but can be a resource hog.

try Mplayer, it should be preinstalled

---

### Post by PCaddicted on 2011-04-18
Personally,I've read in the PCutilities magazine that,if you install Ubuntu as application inside Windows,system performance will be slightly reduced.However,that was about Karmic Koala(Ubuntu 9.10) and I am not sure if it applies to Maverick Meerkat(Ubuntu 10.10),too,but it probably does.

---

### Post by infohub on 2011-04-18
> **flipper T said:**
> have you tried a different player ?

vlc is good but can be a resource hog.

try Mplayer, it should be preinstalled

Well, even flash videos have the same issue, so should there be some fix in the System software section? Like drivers??

---

### Post by flipper T on 2011-04-18
flash videos played through vlc ?

please be clearer

---

### Post by infohub on 2011-04-18
> **flipper T said:**
> flash videos played through vlc ?

please be clearer

Well, I meant the flash videos watched online, e.g Youtube. Which are obviously :) played by Adobe Flash Plugin.

---

### Post by mörgæs on 2011-04-19
This is not 'obviously'. There are several alternative Flash players and plug-ins.

---

### Post by flipper T on 2011-04-19
ok, one last time, have you tried a different media player ?

---

### Post by infohub on 2011-04-19
> **flipper T said:**
> ok, one last time, have you tried a different media player ?

Nope I havent, coz i dunno of any. do u use vlc? is the video smooth (in both normal and fullscreen)?

Else which is the best media player, i mean a good allrounder for both audio and video???

---

### Post by infohub on 2011-04-19
> **mörgæs said:**
> This is not 'obviously'. There are several alternative Flash players and plug-ins.

Whats ur feedback for Adobe flash, is it smooth on urs? If not which is the best flash plugin? 

"Obvious"- comment withdrawn :)

---

### Post by flipper T on 2011-04-19
have you installed ubuntu "inside windows" using wubi ?

this will affect performance.

why not just watch your videos in windows ?

why not try dual booting ?

why not try all those media players available in ubuntu software centre?


as for streaming flash, what browser do you use? if firefox, google the flashaid extension.

ps "nope i havent cuz i dunno of any" is a bit lame.

people are here to help, not babysit.

---

### Post by Sillywombat on 2011-04-19
DPI plays a part too. If your watching high def (e.g. 1080 dpi), and your PC isnt that hot, you may want to try Xine player. It handles like an old school PC DVD player but manages to handle high rez files rather well.
For youtube and whatnot, try adding this ti firefox, should get rid of any uneeded codecs: [http://www.webgapps.org/addons/flash-aid]("http://www.webgapps.org/addons/flash-aid")

---

### Post by SeijiSensei on 2011-04-19
```
sudo apt-get install smplayer
```

is a good place to start.

---

### Post by infohub on 2011-04-19
> **flipper T said:**
> have you installed ubuntu "inside windows" using wubi ?

this will affect performance.

why not just watch your videos in windows ?

why not try dual booting ?

why not try all those media players available in ubuntu software centre?


as for streaming flash, what browser do you use? if firefox, google the flashaid extension.

ps "nope i havent cuz i dunno of any" is a bit lame.

people are here to help, not babysit.


Well, I tried with dual boot (in a separate partition), but the problem persisted, i think ubuntu was a bit slower too in dual boot.

ps "why not just watch your videos in windows?" sounds illogical ... people start using ubuntu coz they are fed up of Windows performance. And ppl use windows only for higher end purposes like converting videos, or compiling programs.

Playing audio/video is one of the "basic" features of an OS, else it would just be useless.

I'll have to try other media players anyways.

---

### Post by mörgæs on 2011-04-19
> **infohub said:**
> Whats ur feedback for Adobe flash, is it smooth on urs? If not which is the best flash plugin? 

"Obvious"- comment withdrawn :)

Just try a broad selection of them, and try both Firefox and Chromium. 

Running **top** while watching Flash will tell about CPU load. Press q for quitting top.

I mostly use VLC, but don't take this as the only option. Experimenting is the way to go.

---

