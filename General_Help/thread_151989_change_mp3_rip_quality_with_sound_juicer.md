---
title: "change mp3 rip quality with sound juicer"
date: 2006-03-28
forum: General Help
---

### Post by onesojourner on 2006-03-28
I am trying to rip some audio books and I want the bit rate to be about 32 maybe 64. I cant seem to find where i can change that with sound juicer.

---

### Post by aysiu on 2006-03-28
Thought about using Goobox?

---

### Post by onesojourner on 2006-03-29
seems like i have tried that one. I just always go back to sound juicer, its simple works well and its very easy to use (until i need to change the quality...)

---

### Post by Toddy on 2006-03-29
I don't have my Linux box in front of me, but where you created the MP3 profile of:

audio/x-raw-int, rate=44100,channels=2 ! lame name=enc

append bitrate=192 (or bitrate=64 in your case) to the end of it.  I think the default is 160 if bitrate isn't specified.

---

### Post by ahaslam on 2006-06-02
[QUOTE=Toddy]I don't have my Linux box in front of me, but where you created the MP3 profile of:

audio/x-raw-int, rate=44100,channels=2 ! lame name=enc

append bitrate=192 (or bitrate=64 in your case) to the end of it.  I think the default is 160 if bitrate isn't specified.[/QUOTE]
I used Grip before I saw this, it was very slow. Thanks for that, ripping at a decent quality is now easier & quicker with Sound Juicer.
Thanks again,
Tony.:)

---

