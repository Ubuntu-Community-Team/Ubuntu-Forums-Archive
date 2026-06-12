---
title: "Not able to covert MP4 to MP3 using ffmpeg in Oneiric"
date: 2011-11-14
forum: General Help
---

### Post by anur.bhargav on 2011-11-14
I'm trying to covert a video that's in MP4 format to MP3 in Ubuntu 11.10, when I do so, I get this error >  Encoder (codec id 86017) not found for output stream #0.0 .
The same command worked perfectly fine in 11.04. Have I done something wrong ? Are any packages missing ?

---

### Post by ajgreeny on 2011-11-14
The standard ffmpeg in ubuntu does not encode to mp3, if I remember correctly.

I suggest you enable the partner repos if they are not already enabled, and also enable medibuntu repos as they contain versions of various libav packages that you may need, eg libavcodec-extra-52 (that's for 10.04, not sure about 11.10) for encoding to mp3.

---

### Post by anur.bhargav on 2011-11-14
Solved it :D... I installed >  Ubuntu Restricted Extras .. And that solved my problem. Worked like a charm :D

---

### Post by FakeOutdoorsman on 2011-11-14
> **ajgreeny said:**
> you may need, eg libavcodec-extra-52 (that's for 10.04, not sure about 11.10) for encoding to mp3.

This is correct. It is **libavcodec-extra-53** for 11.10. More info:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by anur.bhargav on 2011-11-15
> **FakeOutdoorsman said:**
> This is correct. It is **libavcodec-extra-53** for 11.10. More info:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

Thanks for the heads up :D

---

