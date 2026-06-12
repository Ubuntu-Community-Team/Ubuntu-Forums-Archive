---
title: "menCODER Audio Record (Xbox 360)"
date: 2010-06-04
forum: General Help
---

### Post by Jake007g on 2010-06-04
So I've gotten pretty nice quality video capturing my Xbox 360 through easyCAP, but I've spent the last 4 days (About 10 hours) trying to get the audio to record. Also, I cannot seem to get it to record in my specified dimensions or FPS. Here is my current menCODER .sh script:

> mencoder tv:// -tv device=/dev/video0:input=1:norm=PAL-60:adevice=/dev/audio1:audiorate=48000:amode=1:forceaudio -vf pp=md:fps=60:mpeg4:width=1920: height=1080 -o Recording -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=8000:aspect=16/9 -oac mp3lame -lameopts cbr:br=128

I am using Ubuntu (Studio) 10.04, and I'm from Europe so PAL is my TV standard. 

Most importantly, what I would like to know is, how to find which 'device' (/dev/audio etc) my easyCAP's audio is linked to, or if that isn't the problem with my script, how I can get the audio to record.

Also if possible, all though I'm not that bothered about this part, how I could get menCODER to actually record my footage in 1920x1080 @ 60fps (It currently records in 720x480 @ 29.97 FPS for some reason).

Many thanks in advance, from your friendly Ubuntu noob 

-Jake :)

---

### Post by Jake007g on 2010-06-04
Bump, need help ASAP please :-)

---

### Post by Jake007g on 2010-06-06
Does no one know how to sort this out? :(

---

### Post by Jake007g on 2010-06-06
Please if ANYBODY knows anything that might help me work it out, please reply!

I really want to get the sound working so I can start making videos for my YouTube channel again!

---

### Post by Jake007g on 2010-06-07
I'm so desperate for help with this!

---

