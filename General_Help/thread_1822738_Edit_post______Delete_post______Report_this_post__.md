---
title: "* Edit post     * Delete post     * Report this post     * Reply with quote  Gr"
date: 2011-08-10
forum: General Help
---

### Post by smeagol271006 on 2011-08-10
Hi people,

I've been trying to run

```
growisofs -dvd-compat -Z  /dev/sr1 "$FOLDER_DVD_VIDEO"
```and
```
growisofs -dvd-compat -input-charset iso8859-1 -Z  /dev/sr1 "$FOLDER_DVD_VIDEO"
```either one of them gives me a dvd video with lowercase files instead of the uppercase files :confused:

input would be "$FOLDER_DVD_VIDEO"

```
VIDEO_TS -->>

VIDEO_TS.BUP  VTS_01_0.IFO  VTS_01_2.VOB  VTS_02_1.VOB  VTS_03_1.VOB
VIDEO_TS.IFO  VTS_01_0.VOB  VTS_02_0.BUP  VTS_03_0.BUP
VTS_01_0.BUP  VTS_01_1.VOB  VTS_02_0.IFO  VTS_03_0.IFO
```Output is the same but lowercase. Won't play in dvd players of course.

AUDIO_TS is not present in the input folder ("$FOLDER_DVD_VIDEO").
Still players work fine despite AUDIO_TS not present.

Possible cause?
AUDIO_TS not present and growisofs garbles the input to lowercase output?

```
cat /proc/filesystems
```do show     udf iso9660.

Would you be so kindly to explain me how to amend?
Thanks !

---

### Post by smeagol271006 on 2011-08-12
bump

---

### Post by smeagol271006 on 2011-08-14
bump

---

### Post by smeagol271006 on 2011-08-14
Solved had to use option -dvd-video of genisoimage

---

