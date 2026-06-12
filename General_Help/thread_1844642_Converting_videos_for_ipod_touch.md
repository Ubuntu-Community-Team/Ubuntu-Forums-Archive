---
title: "Converting videos for ipod touch"
date: 2011-09-15
forum: General Help
---

### Post by chromatica86 on 2011-09-15
Hi all. I have an ipod touch 3rd gen. I'm trying to use handbrake to convert videos for it, but no matter what I try, when it comes time to sync I get an error saying the file type is not supported.
I'm using the iphone/ipod touch preset. What am I doing wrong?
Btw, syncing is being done with banshee and files that were previously converted with anyvideoconverter in windows are working fine.

---

### Post by dniMretsaM on 2011-09-15
Try FFmpeg:
```
ffmpeg -i source_video.avi input -acodec aac -ab 128kb -vcodec mpeg4 -b 1200kb -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 320x180 -title X final_video.mp4
```[QUOTE=Cats Who Code]
Explanations :

[LIST]
[*]Source : source_video.avi
[*]Audio codec : aac
[*]Audio bitrate : 128kb/s
[*]Video codec : mpeg4
[*]Video bitrate : 1200kb/s
[*]Video size : 320px par 180px
[*]Generated video : final_video.mp4
[/LIST]
[/QUOTE]Taken from: [http://www.catswhocode.com/blog/19-ffmpeg-commands-for-all-needs](http://www.catswhocode.com/blog/19-ffmpeg-commands-for-all-needs)

Also, can you confirm that syncing your iPhone works? Like can you sync music? If not, it may not be a problem with the videos but with the system (which can almost certainly be fixed, so don't get scared).

---

### Post by BHEJU on 2011-09-15
Agree with dniMretsaM.
I used that in past.
However, if you want GUI, try handbreak. It't just graphical interface on top of ffmpeg.

Cheers,

---

### Post by chromatica86 on 2011-09-15
I'm already trying handbrake with the iphone/touch preset.
Yes syncing to the device is working.

---

### Post by dniMretsaM on 2011-09-15
> **BHEJU said:**
> Agree with dniMretsaM.
I used that in past.
However, if you want GUI, try handbreak. It't just graphical interface on top of ffmpeg.

Cheers,

Wow I did not know this. Not that I've ever used it... Anyway, try the command I gave you and see if that works.

---

### Post by chromatica86 on 2011-09-15
The problem seemed to be that it kept creating a .m4v instead of .mp4
I just tried arista with the psp profile and it synced the file. The video plays kind of choppy on the ipod though, so I'll have to figure that out now.
Thanks for the suggestions though.

---

### Post by kerry_s on 2011-09-15
Winff is a good GUI converter too. It has presets you can select, I mostly use it for xbox now though, so i can stream straight to tv from the xbox.

---

### Post by dniMretsaM on 2011-09-15
> **chromatica86 said:**
> The problem seemed to be that it kept creating a .m4v instead of .mp4
I just tried arista with the psp profile and it synced the file. The video plays kind of choppy on the ipod though, so I'll have to figure that out now.
Thanks for the suggestions though.

That's odd because .m4v files play on the iPod. Have you tried syncing with GtkPod? And did it still do that when you ran the code I gave you?

---

### Post by JohnAStebbins on 2011-09-15
> **BHEJU said:**
> Agree with dniMretsaM.
I used that in past.
However, if you want GUI, try handbreak. It't just graphical interface on top of ffmpeg.

Cheers,

Umm, not exactly.  HandBrake selectively uses Libav for some decoding and encoding tasks.  But goes directly to other libraries for other things.  E.g. ac3, and dts audio are decoded by liba52 and libdca.  mpeg2 video is decoded by mpeg2dec.  h.264 video encoding is done directly by libx264.  theora encoding is done directly by libtheora.  HandBrake also has it's own demuxers for mpeg transport and program streams and links directly to libdvdread/libdvdnav for DVD reading and libbluray for BD reading.  Muxing is done by libmkv and mp4v2.

---

### Post by JD8182 on 2011-09-15
Not sure if this would help or not, but the firefox plugin (downloadhelper) has a built in conversion program for Ipod videos. Just a thought.

---

