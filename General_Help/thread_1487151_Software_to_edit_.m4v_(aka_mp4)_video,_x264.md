---
title: "Software to edit .m4v (aka mp4) video, x264"
date: 2010-05-18
forum: General Help
---

### Post by jerome1232 on 2010-05-18
Those handbrake guys are big apple fans I think.


Anyways is there any software, or a way to get avidemux to edit m4v Videos, encoded with x264 Video and AAC Audio?

---

### Post by gordintoronto on 2010-05-18
Between Video Converter and Cinelerra, I have not seen a video I couldn't edit. Some people dislike any program which has a multiple-window interface, which is the biggest criticism of Cinelerra -- but it's an excellent program.

---

### Post by mb_webguy on 2010-05-18
Avidemux can work with the mp4 container and aac audio just fine, but it tends to crash a lot when working with h.264 video.  Also, even if it doesn't crash, it uses a "safe" mode that causes you to lose frame accuracy.

If you don't need to do anything fancy, Ubuntu's new default video editor, PiTiVi, can edit mp4 videos with h.264 video and aac audio just fine (assuming you have the appropriate codecs installed on your machine, of course).  PiTiVi's a bit like Windows Movie Maker, though -- great for quick edits and splicing clips together, but not anything more advanced than that.

I haven't played around with Cinelerra much, but if you need to do some advanced editing, it's definitely a good place to start.

---

### Post by jerome1232 on 2010-05-19
Thanks for the recommendations, I actually tried Pitivi and couldn't figure out how to edit the file, I just tried it again and realized I just may be partially retarded.

I really only need to do some basic cutting. So I think Pitivi will fulfill my needs.

---

### Post by dino99 on 2010-05-19
i'm not used with this kind of problem but if directly editing is too hard or impossible, maybe you can try to translate these formats

---

### Post by jerome1232 on 2010-05-19
I meant that I figured out why it wasn't working for me earlier (I didn't realize you have to drag your clips down to the timeline)

Doh!

---

### Post by FakeOutdoorsman on 2010-05-19
If you want to perform a simple trim, then FFmpeg is well suited for this.  The following example will just copy the audio and video streams, so there is no re-encoding.
```
ffmpeg -ss 00:01:12.00 -i input.foo -acodec copy -vcodec copy -t 14 output.foo
```
[list][*]**-ss:** time offset from beginning.  The example will ignore the fist 1 minute and 12 seconds of the input.  The example uses a *hours:minutes:seconds.thousandths of seconds* format.  You can also use seconds as shown in *-t*.
[*]**-t:** duration. The example will create a 14 second output.[/list]
The placement of *-ss* is important.  Putting it before *-i* tells FFmpeg to "seek then decode", but may not be exactly frame-accurate, while placing *-ss* after *-i* will make FFmpeg decode until it reaches *foo* time and then start doing whatever you told it to do.  Putting it before *-i* is usually faster, and if one placement doesn't work, then try the other.

---

### Post by Dafydd on 2012-08-17
>>>ffmpeg -ss 00:01:12.00 -i input.foo -acodec copy -vcodec copy -t 14 output.foo>>>
Thanks. This worked for me. Just one question. How do I get ffmpeg to copy TWO audio tracks (if there are two)?
It just seems to have ignored the second audio track.

---

### Post by wildmanne39 on 2012-08-17
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

