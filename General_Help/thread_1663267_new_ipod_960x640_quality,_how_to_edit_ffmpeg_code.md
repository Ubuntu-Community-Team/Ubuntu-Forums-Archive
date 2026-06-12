---
title: "new ipod 960x640 quality, how to edit ffmpeg code?"
date: 2011-01-09
forum: General Help
---

### Post by Mesqueeb on 2011-01-09
What would give me good quality: 960x640 for ipod 4
but keep the file low size?

I found 2 codes online:

ffmpeg -i Name.avi -acodec libfaac -ac 2 -ab 128k -vcodec libx264 -vpre hq -vpre ipod640 -crf 26 -s 640x480 -threads 0 Name.mp4

ffmpeg -i source_video.avi input -acodec aac -ab 128kb -vcodec mpeg4 -b 1200kb -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 320x180 -title X final_video.mp4

I guess I need to edit the resolutions there? anything else? (btw I know nothing of commands, but i can copy paste! xD)
Or! can anyone propose something better?

(and how to convert mkv -> avi/mp4?)

greets!

-Mesqueeb

---

### Post by Mesqueeb on 2011-01-09
SOLVED!
[http://handbrake.fr/]("http://handbrake.fr/")

(/^^)/

---

