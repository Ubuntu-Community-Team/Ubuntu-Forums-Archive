---
title: "mplayer softsubs problems"
date: 2006-06-25
forum: General Help
---

### Post by hikitsu4 on 2006-06-25
How do you enable softsubs with mkv files with gmplayer?

I can choose subtitles with totem-gstreamer and xine-ui. 
But this file i wana play doesnt work any good at all with those two players so i most use gmplayer. 
It works perfectly with gmplayer but i cannot choose subtitles.

I have tried various options in gmplayer like:
Convert the given subtitle to mplayer subtitle format.
Convert the given subtitle to the time based Subviewer (SRT) format.

But those two doesnt work.

btw i got all the codecs needed it is just that gmplayer works much better with this h.264 file. totem-gstreamer just lags like hell and xine-ui just stops at the begining of the file.
I have also tried gxine but that just does what xine-ui does.
videolan 0.8.4 and 0.8.5 doesnt work at all.

I just wish there was some program like vobsub plugin to linux, that would help alot, does all the subtitle formats.

---

### Post by hikitsu4 on 2006-06-26
I fixed the problem, i got an answer from fendoraforums. 
The syntax is: mplayer -sid 0 myfile.mkv

---

