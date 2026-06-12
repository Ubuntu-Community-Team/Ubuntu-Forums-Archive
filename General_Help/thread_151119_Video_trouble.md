---
title: "Video trouble"
date: 2006-03-27
forum: General Help
---

### Post by Ubuntuud on 2006-03-27
Hi, I have some video in wmv and asf format some of them play fine, others don't. I think it must be something with the codecs, because it isn't just totem that scrambles the image, MPlayer can't play them either. I have attached a screenshot to show how it looks, and as you can see on the second image, even the startup-screen is scrambled...
And yes, I have done all the steps in the restricted formats wiki page.
Thanks in advance.

---

### Post by taurus on 2006-03-27
Did you remember to install w32codecs?

---

### Post by Ubuntuud on 2006-03-27
Yes, I did...

---

### Post by Ubuntuud on 2006-03-27
UPDATE: I figured the problem might be the fact that I have totem-xine... So I installed totem-gstreamer, now the start-up image isn't scrambled, but none of the movies display anything.

---

### Post by Perfect Storm on 2006-03-27
Try with a 

```
gst-register-0.8
```

---

### Post by Ubuntuud on 2006-03-27
I'm afraid it didn't work.

---

### Post by Perfect Storm on 2006-03-27
What does it say when you try running it in mplayer? My experience there are some trouble with wmv format.

---

### Post by Ubuntuud on 2006-03-27
MPlayer says the following (with asf and mpeg):
New_Face failed. Maybe the font path is wrong.
Please supply the text font file (~/.mplayer/subfont.ttf).

And then it plays just the sound.

I haven't got trouble with just the wmv format, the asf and mpeg do the same.

Also, I am running XGL (don't know if that matters).

---

### Post by qyot27 on 2006-03-27
Do you know what type of video the WMV and ASF files are holding?  There are a couple different formats that they can hold (aside from Windows Media formats, there's also Microsoft's 'ISO' MPEG-4 - i.e. what DivX was originally hacked from).  It may be a problem with that.  I don't know what the problems with MPEG (is it -1, -2, or -4?) would arise from.

---

### Post by Ubuntuud on 2006-03-27
I have downloaded a package with font in the name for mplayer, the movies can play now, but the problem now is compiz. I can't see a thing. Only when I <Alt><Tab> I can see it in the tiny window "preview"... Is there a way to fix this?

---

