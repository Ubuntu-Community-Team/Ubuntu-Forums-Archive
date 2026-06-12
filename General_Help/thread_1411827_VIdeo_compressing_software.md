---
title: "VIdeo compressing software"
date: 2010-02-20
forum: General Help
---

### Post by colobix on 2010-02-20
Hey.I need a software I can use to compress some avi files I just converted from mkv format so they are pretty huge.
I used Avidemux or whatever it's called to convert them from mkv, but I couldn't find bitrate options there.
Ok so when I download a south park episode the file is about 180Mb big but after I converted the files from mkv they are like 4 - 600.
someone please help me here.

---

### Post by mkarr on 2010-02-20
Why would you convert them? I've been using .mkv files for months now and they work just fine for my media player, take up less space, and are better quality than the .avi files I used to depend on.

---

### Post by colobix on 2010-02-20
Because for some reason, the ps3 console doesn't support hd formats.
Just great huh? ;(

---

### Post by spiritofelric on 2010-03-15
maybe this might work?
[http://maketecheasier.com/how-to-compress-a-video-file-with-virtualdub/2009/05/31](http://maketecheasier.com/how-to-compress-a-video-file-with-virtualdub/2009/05/31)

---

### Post by 3rdalbum on 2010-03-15
> **mkarr said:**
> Why would you convert them? I've been using .mkv files for months now and they work just fine for my media player, take up less space, and are better quality than the .avi files I used to depend on.

*sigh* MKV and AVI are not compressors. They are container formats. If your MKVs are better quality and smaller than your AVIs, it's due to the codec and bitrate settings that are used. An H.264 video at 2mbps in an MKV will be identical to the same video stream in an AVI container.

There are heaps of transcoding frontends for Linux. Transmageddon, Arista, and WinFF are well-known. I tend to transcode using straight FFMPEG on the command-line - see 'man ffmpeg' for more details.

---

