---
title: "De-interlacing"
date: 2006-02-22
forum: General Help
---

### Post by Jeffery Mewtamer on 2006-02-22
I got several DVDs worth of interlaced video that I've ripped to my harddrive. The horizontal lines from the interlacing are extremely noticable. I'm looking for good way to de-interlace the video without it having an adverse affect on video quality. I've tried DVD-rip Transcode with Smart De-interlacing, and the results were fairly blurring, and I tried AVI Demux with crystal clear results, but with the interlacing in tact. 

As far as the output format is concerned:
I'd like to be able to use Xvid/Vorbis .OGM with original framerate and resolution.

Thanks in Advance

---

### Post by rattking on 2006-02-22
hmm if transcode can't maybe mencoder can
The available deinterlacers are:
 -vf lavcdeint
 -vf kerndeint
 -vf filmdint
 -vf pp=lb
 -vf pp=li
 -vf pp=ci
 -vf pp=md
 -vf pp=fd
 
I don't know mencoder very well so you'll have to trial and error at it

man mplayer 
maybe more help

---

