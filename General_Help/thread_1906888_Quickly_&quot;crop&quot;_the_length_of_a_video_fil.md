---
title: "Quickly &quot;crop&quot; the length of a video file"
date: 2012-01-10
forum: General Help
---

### Post by IQAndreas on 2012-01-10
Let's say you have an existing video file (perhaps 30 minutes long) but you want to cut out a small snippet out of it (usually between 30 seconds and two minutes) such as a quote from a long lecture.

Is there any tool that allows you to just "crop" a section out of an existing video file?

[LIST]
[*]I want the video/audio encoding of the output video to exactly match the encoding of the input video (of course I could go through the output settings one by one and make sure they all match up, but this seems unnecessary.
[*]I don't want to wait 5 minutes for the entire video to render, as most of the video should already be rendered up to the last keyframe, right?
[/LIST]

This need arises for me rather frequently, so I was wondering if there was an existing application for this? (as right now, I'm doing this manually in Pitivi which is a relatively slow and arduous process)

---

### Post by TeoBigusGeekus on 2012-01-10
Try with ffmpeg.
If you want to save a part of the original video starting from, say, the 25th minute and lasting 5 minutes, you'd give:
```
ffmpeg -i original_video.ext -vcodec copy -acodec copy -ss 00:25:00 -t 00:05:00 output_video.ext
```

---

### Post by Laobi on 2012-01-10
Or, if you want a GUI tool, you can install Avidemux.  Mark beginning and end of a clip, select *Copy* for Video and Audio, select a container format and save.  It will not recompress your file so it will be quick and will not affect the quallity of the output.

---

### Post by holycow131415 on 2012-01-10
Openshot is a nice program. It reminds me of windows live movie maker, but has more options.

---

### Post by IQAndreas on 2012-01-17
> **Laobi said:**
> Or, if you want a GUI tool, you can install Avidemux.
Avidemux was perfect for the job! Thank you.

I wasn't sure which container format to use, but the default one worked out just fine.

---

