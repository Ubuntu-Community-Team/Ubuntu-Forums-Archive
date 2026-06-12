---
title: "burning dvds and cds"
date: 2006-03-05
forum: General Help
---

### Post by njzillest on 2006-03-05
i have downloaded a few .AVI files.. and now i want to burn it to a dvd.


i have a dvd burner, but what file formatt do i need it to be in so that i can burn it to the DVD, and watch it on another computer, and possiable my dvd player (attached to the T.V)


will burned avi files play on my tv, or do i have to put it in another format. 
if i do what software do i need? please tell me any type, either for linux or windows..


thanx

---

### Post by taurus on 2006-03-05
You have a few options to pick from if you want to convert an avi file to a dvd so you can play on your dvd player.  There are tovid, devede, avidemux, DVDAuthorWizard, and Video-DVDRip just to name a few...

---

### Post by jtpratt on 2006-03-14
Took me awhile to figure this out too.  You can read my Ubuntu guide to [converting video using ffmpeg here]("http://smorgasbord.net/convert_video_linux").

The quick answer is to use ffmpeg on the command line like this to convert your video files:
ffmpeg -i myfile.avi -target vcd /tmp/vcd.mpg

and then use K3B to burn them to a VCD or "Video CD" project that will play in about any modern DVD player.  I do it all the time.

Use your Synaptic Package Manager to make sure you have ffmpeg and K3B installed.

---

