---
title: "Encoding for Youtube"
date: 2010-10-03
forum: General Help
---

### Post by ki4jgt on 2010-10-03
I have been working on a program for the last 5 months, but no one knows about it. I wanted to record it and show it off on Youtube, but every desktop program I try doesn't work. It's really starting to tick me off. I've tried combining Cheese and WebCamStudio video dimensions were disproportional causing everything to be blurry. I've tried recordmydesktop it doesn't encode it very well b/c everytime I upload it to youtube youtube gets the sound, but the video is just a bunch of colors on the screen. [http://www.youtube.com/watch?v=snYgRRVTRak](http://www.youtube.com/watch?v=snYgRRVTRak) I tried Istanbul. All it does is get tied up and then take a photo every 20-40 seconds. Anyone have any suggestions? Thanks.

---

### Post by zadehas on 2010-10-03
I always use recordMyDesktop (gtk version to be more exact) to make screen casts. If I remember correctly, it outputs the recording in ogv format, so I use mencoder to convert it to avi, I think that may help when uploading on Youtube. Here's the command to do that:

```
mencoder -idx out.ogv -ovc lavc -oac mp3lame -o output.avi
```

Where out.ogv is whatever file recordMyDesktop outputs to, and output.avi is the final avi version.

---

### Post by gandaran on 2010-10-03
seems gtk-recordmydesktop youtube videos is fixed in new version
[http://www.webupd8.org/2010/10/gtk-recordmydesktop-videos-now-work.html](http://www.webupd8.org/2010/10/gtk-recordmydesktop-videos-now-work.html)

---

### Post by ron999 on 2010-10-03
> **gandaran said:**
> seems gtk-recordmydesktop youtube videos is fixed in new version
[http://www.webupd8.org/2010/10/gtk-recordmydesktop-videos-now-work.html](http://www.webupd8.org/2010/10/gtk-recordmydesktop-videos-now-work.html)

It's still the same using Karmic Koala.:(
With recordmydesktop-0.3.8.1.

Maybe things are different with Meercat.

Best results for me are by using ffmpeg like in this tutorial:-[http://ubuntuforums.org/showthread.php?t=1392026]("http://ubuntuforums.org/showthread.php?t=1392026")
:)

(imho) recordmydesktop needs to have the option 'Save as raw' so that encoding could be done separately.
:mad:

---

