---
title: "Splitting an avi file"
date: 2009-11-19
forum: General Help
---

### Post by vaskark on 2009-11-19
Hi. I need to split a movie file (AVI) in half. Can someone recommend an app for this?
Thanks.

---

### Post by emigrant on 2009-11-19
is this for partability?
if so you can zip and split it.

---

### Post by vaskark on 2009-11-19
Partability? Not sure what you mean. I just want to split one avi file into two.

---

### Post by emigrant on 2009-11-19
sorry i meant portability.
ie. your avi is too big for the flashdrive and you want it to put into to flash drive etc...?
or you want it to be splitted and still view the video?

---

### Post by vaskark on 2009-11-19
Yes, I want 2 viewable video files.

---

### Post by election on 2009-11-19
u can use avidemux.
[http://fixounet.free.fr/avidemux/](http://fixounet.free.fr/avidemux/)

---

### Post by emigrant on 2009-11-19
this would help:
[http://manpages.ubuntu.com/manpages/karmic/man1/avisplit.1.html](http://manpages.ubuntu.com/manpages/karmic/man1/avisplit.1.html)

---

### Post by vaskark on 2009-11-19
Thanks ;)

---

### Post by vaskark on 2009-11-19
Dang.
*avisplit* didn't work right. it produced a file, but the video is compressed to about 1/4 of the expected size.

---

### Post by emigrant on 2009-11-19
what was the command you gave?

---

### Post by vaskark on 2009-11-19
avisplit -i file.avi -o one.avi -t 00:00:00-00:45:16 -m

---

### Post by BFG on 2009-11-19
> **election said:**
> u can use avidemux.
[http://fixounet.free.fr/avidemux/](http://fixounet.free.fr/avidemux/)

+1  Avidemux works very well for this.  I use it for topping / tailing vids before uploading to youtube.  It's in the repos.

---

### Post by vaskark on 2009-11-19
K, i'm trying *avidemux*, but it gives me the same problem as *avisplit* (the compressed image). I selected the start and end points, then File > Save > Save Video. Is this correct, or are there other steps I'm leaving out?

---

### Post by BFG on 2009-11-19
No step missing, that's what works for me.  Though I'm not an expert. Maybe there's something up with the source file.  I always find video formats to be such a problem.


Check the defaults for Video and Audio are "Copy". 

When making an edit for youtube, in the top menu I choose Auto > Ipod (mpeg4) and this resizes.

Also wouldn't hurt to make sure you have all the ffmpeg extras:
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by vaskark on 2009-11-19
Thanks for all the help, guys. I think I have it working now.
:p

---

