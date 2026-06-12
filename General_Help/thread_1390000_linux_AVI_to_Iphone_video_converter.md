---
title: "linux AVI to Iphone video converter?"
date: 2010-01-25
forum: General Help
---

### Post by Arminius on 2010-01-25
is there a linux avi to iphone video converter?
specifically .avi to .mp4?
cause my iphone would only sync to itunes I was trying out windows based ones.
but they all claim to be free then only convert the first 5 mins then demand money.

so is there a linux one that will do the whole thing then I simply transfer the .mp4 file over to my virtual windows?

---

### Post by m0o on 2010-01-25
Use [Handbrake]("http://handbrake.fr/").

---

### Post by Arminius on 2010-01-25
neither of the codecs for mp4 worked
both H.264 and MPEG-4 displayed the "this file" was not copied to the iphone cause it cannot be played on the iphone

---

### Post by spcwingo on 2010-01-25
Have you tried pytube?

[http://www.marcosrodriguez.me/pytube/]("http://www.marcosrodriguez.me/pytube/")

---

### Post by Arminius on 2010-01-26
tried pytube just now
it's converter finished in under a second and reported it was done.
and yet no converted file is sitting on the desktop

---

### Post by nothingspecial on 2010-01-26
If you do [[COLOR="Magenta"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=786095") you will be able to convert to mp4.

It looks really complicated, but it is just a matter of copy and paste.

When you are done, install winff and you will be able to use it to convert to mp4.

---

### Post by head2head on 2010-01-26
Were you using the Iphone specific preset when converting the videos using Handbrake? If not, that would explain why the phone can't play it.

---

### Post by 3rdalbum on 2010-01-26
> **nothingspecial said:**
> If you do [[COLOR="Magenta"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=786095") you will be able to convert to mp4.

It looks really complicated, but it is just a matter of copy and paste.

When you are done, install winff and you will be able to use it to convert to mp4.

I don't think the "compile ffmpeg and x264" is necessary anymore for this task. The Medibuntu repository in 9.10 contains a suitable ffmpeg and "libav" for encoding videos in h.264 and aac. Just add the Medibuntu.org repository and then install the packages whose names begin with the words "libav" and end in "extra" or "unstripped".

---

### Post by nothingspecial on 2010-01-26
> **3rdalbum said:**
> I don't think the "compile ffmpeg and x264" is necessary anymore for this task. The Medibuntu repository in 9.10 contains a suitable ffmpeg and "libav" for encoding videos in h.264 and aac. Just add the Medibuntu.org repository and then install the packages whose names begin with the words "libav" and end in "extra" or "unstripped".

Aahh, haddn`t spotted that. Cheers.

@OP theres a link on the page that my link points to, telling you HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg.

Do that instead. Alot less time watching gobbldygook flash by.

---

### Post by Arminius on 2010-01-26
> Were you using the Iphone specific preset when converting the videos using Handbrake? If not, that would explain why the phone can't play it.

no I didn't use the ipod 5g support option
the subtext said it was for older ipods.

---

### Post by head2head on 2010-01-26
There should be an ***iphone*** specific option - at least there is on mine. Not on home pc at the moment but will get a screenshot and version no. in next couple of hours.

EDIT - not my screenshot, but my presets look like this;

[IMG]http://www.rationalplanet.com/wp-content/uploads/2009/06/screenshot-012.png[/IMG]

---

### Post by FakeOutdoorsman on 2010-01-26
Perhaps FFmpeg itself will work for you.  Either compile FFmpeg ([instructions](http://ubuntuforums.org/showthread.php?t=786095)) or install **libavcodec-extra-52** from Medibuntu ([instructions](http://ubuntuforums.org/showthread.php?t=1117283)) as mentioned by other forum members in this thread, and then:
```
ffmpeg -i input.avi -acodec libfaac -vcodec libx264 -vpre hq -vpre ipod640 -f ipod -crf 26 -threads 0 output.mp4
```
This is untested.  I don't own an iPhone.

---

### Post by vinnywright on 2010-01-26
if you'v added the medibuntu repo you can install and use ffmpg and the GUI winff to do this.

withought neading to know the CLI gobelde gook.     LOL

VINNY

---

### Post by Arminius on 2010-01-27
using the ipod 5g support option didn't help make handshake make anything iphone compatible.

---

### Post by Arminius on 2010-01-27
damn, didn't see the updates when I came on
didn't have the presets panel showing on handbrake, I'll try it now, thanks

---

### Post by head2head on 2010-01-27
Any joy?

---

### Post by brundles on 2010-02-18
Well I don't know about Arminius, but I've just put 0.93 on to my laptop (still running 8.10 so no PPAs for 0.94 yet) and it works a treat :).

Count mine as another vote for Handbrake!

---

