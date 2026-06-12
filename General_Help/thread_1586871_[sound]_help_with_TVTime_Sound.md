---
title: "[sound] help with TVTime Sound"
date: 2010-10-02
forum: General Help
---

### Post by hexabyte on 2010-10-02
Hello ppl. I am new to Ubuntu and also new to Ubuntu Forums. so I would like to say hello to everyone here!
Now the problem:
I have a TV Card from K-World. So i searched many applications for TV featuring MythTV , Zapping but they did not show any video/sound. I Found TVTime and it was okay , but it didn't show sound. so if anyone can help me, thanks.
P.S i've googled for many times and viewed many tutorials but no luck.
Thanks in Advance,
Georgij.
:guitar:

---

### Post by hexabyte on 2010-10-02
anyone? please! :confused:

---

### Post by hexabyte on 2010-10-03
No need ppl. I fixed it.
if anyone has the same problem try this
```
arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay - 
```after runing TVTIME!.
THANKS!
solution.
read this : [http://linuxtv.org/wiki/index.php/Saa7134-alsa](http://linuxtv.org/wiki/index.php/Saa7134-alsa)

---

