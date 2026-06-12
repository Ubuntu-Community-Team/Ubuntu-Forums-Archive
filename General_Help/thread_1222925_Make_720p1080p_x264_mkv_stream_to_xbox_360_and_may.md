---
title: "Make 720p/1080p x264 mkv stream to xbox 360 and maybe ps3"
date: 2009-07-25
forum: General Help
---

### Post by Voorhees1979 on 2009-07-25
This will work 100% on the xbox 360. Untested on the PS3

I use twonky to stream these to the 360

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

Now the file maybe over the 4gig limit for the xbox 360. Run mkvmerger and set it to splt either by file size (didnt work for me) or by a certain amount of time during the film (worked fine for me). If you try Avidemux to split the files it crashed when loading, 2nd time it didnt crash but saved the split file without any sound.

Hope this helps someone.

This is a pretty quick process even though a few commands need to be run.

If anyone has a faster and easier way to do this feel free to share it.

---

### Post by madsmeg on 2009-07-26
Nice how-to, but you should have "HOW-TO" in the title or people will just think you are having a problem streaming (as I did)

---

### Post by Steve Zenone on 2009-07-30
I've had success using k9copy to rip and encode video/audio to mp4 (video: x264, audio: aac).
[https://help.ubuntu.com/community/K9Copy](https://help.ubuntu.com/community/K9Copy)

I use Twonkymedia Server to stream content to the xbox 360. Currently, mp4 extensions aren't showing up on the xbox 360. However, if I change the mp4 extension to m4v, then it works. I believe this is an issue with Twonkymedia Server.
[http://www.twonkyvision.com/](http://www.twonkyvision.com/)

Though documentation claims mkv is supported by k9copy, I haven't personally tried converting mkv streams with k9copy. I'm posting this as a potential alternative to doing the conversion that might be easier for some.

[*UPDATE - 7/31/09*]
I installed the Handbrake deb package [GTK GUI (Ubuntu 8.10 x86 Binaries)] yesterday and have encoded several videos for playback on xbox 360. The encoding process was quicker with Handbrake than with k9copy, the mp4 videos work flawlessly on the xbox, and the quality looks and sounds really good. 
[http://handbrake.fr/?article=download](http://handbrake.fr/?article=download)

Handbrake conveniently has a preset for encoding for xbox 360 playback and now supports mkv files as a source too. I will try using the "Add to Queue" feature later today to convert a number of videos over the weekend.

---

### Post by sportsdude81 on 2009-08-06
so i have several .h264 mp4 videos that i encoded, but i encoded the audio to acc 5.1.  The only problem is I can't play them on my friends xbox 360 because it has to be stereo LC acc.  I have been looking for days on how to change the acc audio file.  The demuxing and muxing is not a problem just need to know how to convert the aac file.  Any ideas?

---

