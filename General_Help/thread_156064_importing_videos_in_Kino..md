---
title: "importing videos in Kino."
date: 2006-04-06
forum: General Help
---

### Post by Specialsauce on 2006-04-06
I have no clue how to do it... it doesnt really matter what format theclip is, i cant import it. Im confused. can someone explain this process to me?

Every time it asks me "This is not a DV file, do you want to import it?" and i say yeah, it gives a loading screen wich promptly disappears, and the video has not been loaded into kino.

---

### Post by TomG on 2006-04-15
Have same problem. Seems not working like "other" softs and need to capture to get stuff into... :confused:

---

### Post by fsman on 2006-04-15
try using ffmpeg on the comand line or avidemux (gui) to convert to a dv file.
you can get avidemux through automatix.

try this

ffmpeg -i '/D/cap/1.avi' -vcodec dvvideo -acodec copy -f dv /D/cap/2.dv -hq

---

### Post by TomG on 2006-04-15
Thanks. So it requires DV files only for input.

---

### Post by brokenthorn on 2006-10-19
[http://ubuntuforums.org/showthread.php?t=249673](http://ubuntuforums.org/showthread.php?t=249673) : My Fix (i.e. works for me)
I think I found a fix, might not work for everybody.

---

### Post by az on 2006-10-19
> **Specialsauce said:**
> I have no clue how to do it... it doesnt really matter what format theclip is, i cant import it. Im confused. can someone explain this process to me?

Every time it asks me "This is not a DV file, do you want to import it?" and i say yeah, it gives a loading screen wich promptly disappears, and the video has not been loaded into kino.

It's not your fault - it's an upstream bug.

---

