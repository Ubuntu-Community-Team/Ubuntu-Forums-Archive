---
title: "VLC no Sound"
date: 2010-10-26
forum: General Help
---

### Post by fusky on 2010-10-26
I recently upgraded to 10.10 and tried playing a movie in vlc and got no sound ,tried playing a song in vlc and no sound as well. I tried in other music apps but i was able to get sound, is this a bug in vlc if anyone knows or am i doing something wrong? I tried changing the output to every option available but no sound still and tried restarting vlc after changing the output as well ,and made sure nothing was muted too.If anyone can help thanks.Also i seem to be having choppy sounds in youtube videos as well.Im not sure if its related problems or not but seems quite similar.

---

### Post by fusky on 2010-10-26
bump

---

### Post by MikeMiller on 2010-11-11
Same here.  Ever since I upgraded to 10.10, I have no sound in vlc no matter what I try.  I have sound in other applications, though.

Any ideas?

Thanks!

-Mike

---

### Post by deserthowler on 2010-11-12
My vlc works beautifully on CDs and Dvds in 10.10.  That is strange.  Are you sure it is not doing sound or is it that the speaker volume is set too low.  Volume on vlc is much lower than on rhythmbox on my machine.

Earl

---

### Post by MikeMiller on 2010-11-12
> **deserthowler said:**
> My vlc works beautifully on CDs and Dvds in 10.10.  That is strange.  Are you sure it is not doing sound or is it that the speaker volume is set too low.  Volume on vlc is much lower than on rhythmbox on my machine.

Earl

Volume is at 100%.

Simultaneously, I can play MP3 files using command line mpg321, and hear sound from youtube videos from the browser.

But then trying to play videos (.flv, .avi, .mp4, etc) using vlc or other video players (so it's not just vlc), I get NO sound.
It worked fine before upgrading to 10.10.

---

### Post by MikeMiller on 2010-11-18
Ok, so the problem turned out to be #$%@#$^@#$ PulseAudio.
I followed the procedure in another forum to remove ~/.pulse and other config files and it seemed to fix all the problems.

-Mike

---

