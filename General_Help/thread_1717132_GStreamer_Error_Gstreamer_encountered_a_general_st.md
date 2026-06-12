---
title: "GStreamer Error: Gstreamer encountered a general stream error (not all flacs)"
date: 2011-03-29
forum: General Help
---

### Post by astrobob.tk on 2011-03-29
Hello guys,

I was trying to convert a flac audio to mp3 using soundconverter & its failing with the error:

> GStreamer error: Gstreamer encountered a general stream error.:S

I should note that the flac is a rip of an actual Mono Vinyl disc. Am not exactly sure how that was done but I was interested in converting some those files to ogg & mp3. OGG conversion doesn't give any error.

Below is the result when launching soundconverter from the terminal & trying to convert the flac file(s) to mp3 (i just tried ogg to mp3 & the same error occurs):

```
$ soundconverter
SoundConverter 1.4.4
  using Gstreamer version: 0.10.28, Python binding version: 0.10.18
  using gio
  using 2 thread(s)
Queue done in 0s
Queue done in 0s
Queue done in 0s

```hope you could help me figure this out ;D

---

### Post by no2498 on 2011-03-29
look in your package manager for Gstreamer
you need the good, bad, ugly, and 10 for the linux/ubuntu you use

---

### Post by astrobob.tk on 2011-03-30
> **no2498 said:**
> look in your package manager for Gstreamer
you need the good, bad, ugly, and 10 for the linux/ubuntu you use

I already have each of the following installed:

gstreamer0.10-plugins-good
gstreamer0.10-plugins-good

gstreamer0.10-plugins-bad
gstreamer0.10-plugins-good-multiverse

gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse

missing anything ?

---

### Post by no2498 on 2011-03-30
do you have winff installed it comes up on my computer
it uses  Gstreamer

---

### Post by NFblaze on 2011-03-30
Try converting to WAV then convert from WAV to FLAC.

---

### Post by astrobob.tk on 2011-03-31
> **no2498 said:**
> do you have winff installed it comes up on my computer
it uses  Gstreamer

i just checked & no its not installed

---

### Post by astrobob.tk on 2011-03-31
> **NFblaze said:**
> Try converting to WAV then convert from WAV to FLAC.

i can convert to ogg or others & then to flac but thats not the purpose (loosing quality); besides the problem should not exist in the 1st place

---

### Post by trucken on 2012-02-27
Same issue, finally found the preference for resample must be checked for conversion to mp3 from flac. :)

---

### Post by etyrmi on 2012-03-09
Thanks!

---

### Post by astrobob.tk on 2012-03-10
just a mistake

resampling doesn't affect the problem (wma to ogg)

---

### Post by Antman on 2012-04-23
> **trucken said:**
> Same issue, finally found the preference for resample must be checked for conversion to mp3 from flac. :)

Old thread, but I just wanted to say thanks for this. It solved my issue too. :KS

---

