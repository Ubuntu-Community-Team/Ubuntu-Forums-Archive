---
title: "Cannot open transcoded video"
date: 2012-06-09
forum: General Help
---

### Post by 0011235813 on 2012-06-09
Hi,
I tried to transcode an .mp4 video with kdenlive. I selected 1080p 30fps for the output format, but when it finished transcoding and I tried to open the .mov file with both vlc and dragon, neither of them will play it!
It also seems to have generated a .stat file. Has that got something to do with this?

---

### Post by zero2xiii on 2012-06-09
Hay,

The first thing that pops to mind is codecs.

Make sure you have the correct encoding AND decoding codecs for the format you wish to use.

Also check if a log file was generated (Might be the *.stat file?) and read through it for hints. You can also attach a copy here for us to inspect if you cant make heads or tails :)

Cherz

---

### Post by 0011235813 on 2012-06-09
> **zero2xiii said:**
> Hay,

The first thing that pops to mind is codecs.

Make sure you have the correct encoding AND decoding codecs for the format you wish to use.

Also check if a log file was generated (Might be the *.stat file?) and read through it for hints. You can also attach a copy here for us to inspect if you cant make heads or tails :)

Cherz

Yeah, there WAS a .stat file generated! 
I was trying to convert from .mp4 (h.264 video codec, aac audio) to .mov (can't tell the codecs used). 
I have uploaded the stat file if it helps (you will have to extract it).

---

### Post by zero2xiii on 2012-06-10
Hmmm,

Not anything in the stat file, seems like you are trying to imbed a xvid file in a mov shell.

Have you maybe tried other formats? Why do you specificaly need it to be .mov (usualy realtime codecs)?? Most players will play xvid/divx .mp4 files, or try renaming it to avi.

Cherz

---

### Post by 0011235813 on 2012-06-10
> **zero2xiii said:**
> Hmmm,

Not anything in the stat file, seems like you are trying to imbed a xvid file in a mov shell.

Have you maybe tried other formats? Why do you specificaly need it to be .mov (usualy realtime codecs)?? Most players will play xvid/divx .mp4 files, or try renaming it to avi.

Cherz

I probably should try other formats, I was merely trying out the transcoding capabilities of the software. I could use Avidemux I suppose... But yes, it does seem strange as to why the program can't convert between these two particular formats.

---

### Post by zero2xiii on 2012-06-10
> **0011235813 said:**
> I probably should try other formats, I was merely trying out the transcoding capabilities of the software. I could use Avidemux I suppose... But yes, it does seem strange as to why the program can't convert between these two particular formats.

I can almost bet it is not the program's incapability as I have used it before on FHD files and saved to numerous formats including mov and some raw formats. Never had issues.

Thats why I assume its a codec issue. But try other formats aswell. Also try other software with the same formats, also try FFMPEG directly from cli. See if any difference is noted. IF it is a codec issue, all software will give similar results from similar source and destination codecs.

Cherz

---

