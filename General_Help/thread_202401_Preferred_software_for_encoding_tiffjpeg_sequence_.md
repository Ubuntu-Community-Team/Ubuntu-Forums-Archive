---
title: "Preferred software for encoding tiff/jpeg sequence to mpeg format?"
date: 2006-06-23
forum: General Help
---

### Post by Roobert on 2006-06-23
The subject says it all, I have a series of tiffs which represents a 3D animation I did in some proprietary software. I want to encode an mpeg from these tiffs - what is the recommended software for this? The software in question should also cope with encoding jpegs as well.

Thanks,

~ Eric.

---

### Post by xmastree on 2006-09-07
I'm looking for something similar too. I found this post when searching for it...
I have a sequence of JPG images which I would like to string together as a video. Animate (part of imagemagick) will show them on the screen, but I want to generate a video file.

[This](http://www.phrozensmoke.com/projects/ganim8/index.php) looked promising, but I couldn't get it running...

---

### Post by monktbd on 2006-09-07
for animation of jpeg i would use the mplayer/mencoder combination on the command line.
it allows a big variety of codec for output.

edit:
e.g. encode all jpg images in that folder witht the mpeg4 codec:
> 
 mencoder "mf://*.jpg" -mf fps=25 -o output.avi -ovc lavc -lavcopts vcodec=mpeg4

the tiffs can be easily converted with convert.

the syntax of mencoder is not really that straightforward but looking into the help docs gives some basic examples of the usage for jepgs in a folder.

---

### Post by xmastree on 2006-09-07
Wahey! \\:D/ 

That's exactly what I was looking for. Thanks.

That command produces a workable avi file, but my windows using friends couldn't view it. Eventually I used ffmpeg to re-encode it as mpg and that worked, although the file was bigger for a smaller image. :( 

I need to investigate that mencoder thing to find the best option.

---

### Post by monktbd on 2006-09-07
[http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html#CODEC%20SPECIFIC%20ENCODING%20OPTIONS%20(MENCODER%20ONLY)](http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html#CODEC%20SPECIFIC%20ENCODING%20OPTIONS%20(MENCODER%20ONLY))

scroll down to the lavc options especially the vcodec one.
maybe wmv2 might be the best option for exchange with windows.

---

