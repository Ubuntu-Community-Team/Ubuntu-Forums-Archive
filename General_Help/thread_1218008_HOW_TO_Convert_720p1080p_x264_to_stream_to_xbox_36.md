---
title: "HOW TO: Convert 720p/1080p x264 to stream to xbox 360"
date: 2009-07-20
forum: General Help
---

### Post by Voorhees1979 on 2009-07-20
I use Twonky to stream to the 360

No quality in video is lost, just downsampling of audio.

First job you need to install some files some are in the repos some are not:

mkvtoolnix, a52dec, neroAacEnc, gpac (MP4Box)

Step 1: mkvextract tracks input-movie.mkv 1:output.h264
Step 2: mkvextract tracks input-movie.mkv 2:output.ac3
Step 3: a52dec -o wavdolby output.ac3 > output.wav
Step 4: neroAacEnc -br 160000 -if output.wav -of output.m4a
Step 5: MP4Box -add output.h264 -fps 23.976 -par 1=119:100 -add output.m4a output-movie.mp4

If fps is different you can check running mediainfo.

I dont fully understand step 5: -par section. This is stuff I have picked up over various foums, put it together and it works very well.

Now the file will be over the 4gig limit for the xbox 360. Run mkvmerger and set it to splt either by file size (didnt work for me) or by a certain amount of time during the film (worked fine for me). If you try Avidemux to split the files it crashed when loading, 2nd time it didnt crash but saved the split file without any sound.

Hope this helps someone.

This is a pretty quick process even though a few commands need to be run.

If anyone has a faster and easier way to do this feel free to share it.

---

