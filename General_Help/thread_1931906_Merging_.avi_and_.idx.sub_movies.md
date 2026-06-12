---
title: "Merging .avi and .idx/.sub movies"
date: 2012-02-26
forum: General Help
---

### Post by thedemon13666 on 2012-02-26
Hi

I am having trouble merging .avi movies with their respective subtitles (in .idx and .sub format) so they are hard coded into the movie so I can play them on my media player (its a LG home system).

I have tried this method (you have to scroll down a little bit):

[http://automate-everything.com/lang/en/page/3/](http://automate-everything.com/lang/en/page/3/)



but when I attempt to play the output file my media player says it is unsupported, BUT the original movie file (without subtitles) is supported.

I should add that when running the memcoder code as suggested above it does not actually run and gives this error message:

Audio LAVC, couldn't find encoder for codec libfaac.

So I followed a suggestion to change to "-oac faac" instead of "oac lavc", which also didint run due to faac not being installed. So then I followed another suggestion to reinstall mencoder using the mediabuntu repository, it then did run using "-oac faac"

This however does not help getting the video to run on my media player....

Thanks

---

### Post by Khayyam on 2012-02-26
In the example the poster is converting to .mkv (Matroska) and then to .mp4, your player either doesn't support mp4, or expects the suffix to be .avi. [Mastoska]("http://matroska.org/") is not a codec but a container, its a means of 'wrapping' video, subtitles, etc, into a bundled format. With matroska your not really re-encoding the video, so when mencoder does the encoding (with the subtitles) it can output whatever format your player supports, and whichever mencoder has support for. I imagine your player will support xvid so try encoding  with "-ovc xvid".

So, basically, convert to whatever video codec your player supports, mencoder if built with support for them, can output most formats. You might also try changing the suffix to ".avi" .. I'm not sure about your player but I've had one DVD player (that supports playing video via USB) balk at .xvid but would play them if the suffix was .avi.

HTH ... khay

---

### Post by thedemon13666 on 2012-02-26
Thanks for the reply.

I also forgot to say that I had already tried changing format=mp4 to format=avi and changing the suffix to .avi

I tried changing -ovc lavc to -ovc xvid and I got this error:


Movie-Aspect is 2.35:1 - prescaling to correct movie aspect.
videocodec: XviD (640x272 fourcc=44495658 [XVID])
xvid: par=0/0 (vga11), displayed=640x272, sampled=640x272
xvid: you must specify one or a valid combination of 'bitrate', 'pass', 'fixed_quant' settings
FATAL: Cannot initialize video driver.

---

### Post by Khayyam on 2012-02-26
Your welome ...

The error is because you are not passing it the 'bitrate', 'pass', 'fixed_quant' settings, so it doesn't now 'how' to encode the file.

I suggest reading the [XviD section](http://en.gentoo-wiki.com/wiki/HOWTO_Mencoder_Introduction_Guide#XviD) of the [Gentoo Mencoder HOWTO](http://en.gentoo-wiki.com/wiki/HOWTO_Mencoder_Introduction_Guide). It's pretty streighforward, and you should be able to figure out what bitrate, etc, you want.

HTH ... khay

---

