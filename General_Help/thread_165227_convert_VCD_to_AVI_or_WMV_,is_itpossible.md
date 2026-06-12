---
title: "convert VCD to AVI or WMV ,is itpossible ?"
date: 2006-04-24
forum: General Help
---

### Post by medya on 2006-04-24
is it possible to conver my VCDs to AVI or WMV (no matter just a compressed version to reduce file size) in ubuntu ?

in windows I do it with mpeg4 direct

---

### Post by tribaal on 2006-04-24
It should be... Actually I have a similar lack of knowledge, I'd like to encode video in .wmv format (and yes, I got a very valid reason for that), and I can't seem to work that out on linux... :(

Anybody have a clue?

- trib'

---

### Post by pitkali on 2006-04-24
I'm always using mencoder console app from mplayer to do that. Consider the following for example:
```
mencoder vcd://2 -o file.avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=2000
```
Assuming the movie is the second title on VCD, this will create the file file.avi, which will be mpeg4 (divx) encoded movie with maximum average bitrate of 2000 Kb/s. The rest is in 'man mencoder' I found the final part of the manual (the examples ;) ) being most useful. 

You could also try using ffmpeg (also command-line tool) to do the same, but I never did, so don't know how. I don't know any GUI solutions either. Perhaps you could try some dvd ripping software and check if it supports VCDs as well?

---

### Post by adamkane on 2006-04-24
Most often you'll be using mencoder, mplayer, ffmpeg from the command line to convert video formats.

There are copious examples on google how to convert video from the command line or with bash scripts.

Sorry I don't have any example scripts, since I convert to VCD, not from VCD, but google really is a good resource for this.

vcdhelp.com is a great resource for windows users, and someone really should maintain a list of linux video conversion scripts.

---

### Post by jtpratt on 2006-04-25
I convert video like this all the time.  View my [Ubuntu Video Conversion Guide]("http://smorgasbord.net/convert_video_linux") to see how I do it.

---

### Post by cvmostert on 2006-10-15
> **pitkali said:**
> I'm always using mencoder console app from mplayer to do that. Consider the following for example:
```
mencoder vcd://2 -o file.avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=2000
```
Assuming the movie is the second title on VCD, this will create the file file.avi, which will be mpeg4 (divx) encoded movie with maximum average bitrate of 2000 Kb/s. The rest is in 'man mencoder' I found the final part of the manual (the examples ;) ) being most useful. 

You could also try using ffmpeg (also command-line tool) to do the same, but I never did, so don't know how. I don't know any GUI solutions either. Perhaps you could try some dvd ripping software and check if it supports VCDs as well?

Great guide.. i am bussy ripping now...

---

