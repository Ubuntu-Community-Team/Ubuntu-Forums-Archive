---
title: "Unusually long rendering times"
date: 2011-09-23
forum: General Help
---

### Post by linuxuser12345 on 2011-09-23
Hi, I am trying to make a video for a school project in PiTiVi .14.0, and every time I go to render the project, rendering times take unusually long. So long, that I have never successfully rendered the video I am trying to assemble. The rendering seems to go fine until it gets to a certain point, then just stalls. My computer even got to a point of freezing, too! I have tried rendering in multiple formats.

I don't think memory or the processor are a problem, as I have an AMD Athlon II X3 processor with 4GB DDR3.



Can someone help me out here? Thanks.

---

### Post by MG&amp;TL on 2011-09-23
1. Does it give an error?
2. Run pitivi from terminal like this:

```
pitivi
```

And render as usual. See if there's any error messages.

---

### Post by linuxuser12345 on 2011-09-23
Okay, now I fixed up the video so it appears to render it quite fast, but once it gets down to the last second, it just stalls there. Any ideas?

---

### Post by linuxuser12345 on 2011-09-23
It is taking a very long time to render from Pitivi opened through the terminal, but at least I see progress. Lets hope it doesn't freeze at the last second.

---

### Post by linuxuser12345 on 2011-09-23
```
jeb@Kitchen-PC:~$ pitivi
/usr/lib/pitivi/python/pitivi/application.py:266: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  self.mainloop.run()
ERROR [ 5743] [0x7f032e33b720] "<Pipeline at 0x271e090>"        pipeline          Sep 23 16:02:12      _handleErrorMessage: error from /GstPipeline:pipeline1/GstBin:bin1/GnlComposition:gnlcomposition3/GnlSource:gnlsource: FileSourceFactory276/GstBin:bin284/pitivi+elements+singledecodebin+SingleDecodeBin:pitivi+elements+singledecodebin+singledecodebin67/GstQueue:queue40 (__main__.GstQueue): GStreamer encountered a general stream error. (gstqueue.c(1290): gst_queue_loop (): /GstPipeline:pipeline1/GstBin:bin1/GnlComposition:gnlcomposition3/GnlSource:gnlsource: FileSourceFactory276/GstBin:bin284/pitivi+elements+singledecodebin+SingleDecodeBin:pitivi+elements+singledecodebin+singledecodebin67/GstQueue:queue40:
streaming task paused, reason error (-5)) (/usr/lib/pitivi/python/pitivi/pipeline.py:852)
ERROR [ 5743] [0x7f032e33b720] "<Pipeline at 0x271e090>"        pipeline          Sep 23 16:02:12      _handleErrorMessage: error from /GstPipeline:pipeline1/GstBin:bin1/GnlComposition:gnlcomposition2/GnlSource:gnlsource: VideoTestSourceFactory356/GstBin:bin370/GstVideoTestSrc:videotestsrc218 (__main__.GstVideoTestSrc): GStreamer encountered a general stream error. (gstbasesrc.c(2582): gst_base_src_loop (): /GstPipeline:pipeline1/GstBin:bin1/GnlComposition:gnlcomposition2/GnlSource:gnlsource: VideoTestSourceFactory356/GstBin:bin370/GstVideoTestSrc:videotestsrc218:
streaming task paused, reason not-linked (-1)) (/usr/lib/pitivi/python/pitivi/pipeline.py:852)



```

---

### Post by linuxuser12345 on 2011-09-23
Yeah, it froze in the middle this time! :O

---

### Post by linuxuser12345 on 2011-09-23
Now it was working well again, but froze at the last second! Pitivi is really pissing me off! I am going to probably switch to KDEnlive

```
jeb@Kitchen-PC:~$ pitivi
/usr/lib/pitivi/python/pitivi/application.py:266: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  self.mainloop.run()
ERROR [ 6190] [0x7f3f1d610720] "<Pipeline at 0x2514090>"        pipeline          Sep 23 16:06:33      _handleErrorMessage: error from /GstPipeline:pipeline1/GstBin:bin1/GnlComposition:gnlcomposition3/GnlSource:gnlsource: FileSourceFactory276/GstBin:bin284/pitivi+elements+singledecodebin+SingleDecodeBin:pitivi+elements+singledecodebin+singledecodebin67/GstQueue:queue36 (__main__.GstQueue): GStreamer encountered a general stream error. (gstqueue.c(1290): gst_queue_loop (): /GstPipeline:pipeline1/GstBin:bin1/GnlComposition:gnlcomposition3/GnlSource:gnlsource: FileSourceFactory276/GstBin:bin284/pitivi+elements+singledecodebin+SingleDecodeBin:pitivi+elements+singledecodebin+singledecodebin67/GstQueue:queue36:
streaming task paused, reason error (-5)) (/usr/lib/pitivi/python/pitivi/pipeline.py:852)
ERROR [ 6190] [0x7f3f1d610720] "<Pipeline at 0x2514090>"        pipeline          Sep 23 16:06:40      _handleErrorMessage: error from /GstPipeline:pipeline1/GstBin:bin1/GnlComposition:gnlcomposition3/GnlSource:gnlsource: FileSourceFactory276/GstBin:bin284/pitivi+elements+singledecodebin+SingleDecodeBin:pitivi+elements+singledecodebin+singledecodebin67/GstQueue:queue36 (__main__.GstQueue): GStreamer encountered a general stream error. (gstqueue.c(1290): gst_queue_loop (): /GstPipeline:pipeline1/GstBin:bin1/GnlComposition:gnlcomposition3/GnlSource:gnlsource: FileSourceFactory276/GstBin:bin284/pitivi+elements+singledecodebin+SingleDecodeBin:pitivi+elements+singledecodebin+singledecodebin67/GstQueue:queue36:
streaming task paused, reason error (-5)) (/usr/lib/pitivi/python/pitivi/pipeline.py:852)
ERROR [ 6190] [0x7f3f1d610720] "<Pipeline at 0x2514090>"        pipeline          Sep 23 16:06:46      _handleErrorMessage: error from /GstPipeline:pipeline1/GstBin:bin1/GnlComposition:gnlcomposition3/GnlSource:gnlsource: FileSourceFactory276/GstBin:bin284/pitivi+elements+singledecodebin+SingleDecodeBin:pitivi+elements+singledecodebin+singledecodebin67/GstQueue:queue36 (__main__.GstQueue): GStreamer encountered a general stream error. (gstqueue.c(1290): gst_queue_loop (): /GstPipeline:pipeline1/GstBin:bin1/GnlComposition:gnlcomposition3/GnlSource:gnlsource: FileSourceFactory276/GstBin:bin284/pitivi+elements+singledecodebin+SingleDecodeBin:pitivi+elements+singledecodebin+singledecodebin67/GstQueue:queue36:
streaming task paused, reason error (-5)) (/usr/lib/pitivi/python/pitivi/pipeline.py:852)

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

** (pitivi:6190): CRITICAL **: gst_audio_buffer_clip: assertion `segment->format == GST_FORMAT_TIME || segment->format == GST_FORMAT_DEFAULT' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

** (pitivi:6190): CRITICAL **: gst_audio_buffer_clip: assertion `segment->format == GST_FORMAT_TIME || segment->format == GST_FORMAT_DEFAULT' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed

(pitivi:6190): GStreamer-CRITICAL **: gst_segment_set_seek: assertion `start <= stop' failed
ERROR [ 6190] [0x7f3f1d610720] "<Pipeline at 0x2514090>"        pipeline          Sep 23 16:17:31      _handleErrorMessage: error from /GstPipeline:pipeline1/GstBin:bin1/GnlComposition:gnlcomposition3/GnlSource:gnlsource: FileSourceFactory276/GstBin:bin284/pitivi+elements+singledecodebin+SingleDecodeBin:pitivi+elements+singledecodebin+singledecodebin67/GstQueue:queue36 (__main__.GstQueue): GStreamer encountered a general stream error. (gstqueue.c(1290): gst_queue_loop (): /GstPipeline:pipeline1/GstBin:bin1/GnlComposition:gnlcomposition3/GnlSource:gnlsource: FileSourceFactory276/GstBin:bin284/pitivi+elements+singledecodebin+SingleDecodeBin:pitivi+elements+singledecodebin+singledecodebin67/GstQueue:queue36:
streaming task paused, reason error (-5)) (/usr/lib/pitivi/python/pitivi/pipeline.py:852)
jeb@Kitchen-PC:~$ pitivi
/usr/lib/pitivi/python/pitivi/application.py:266: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  self.mainloop.run()
ERROR [ 6840] [0x7f61a05c4720] "<Pipeline at 0x316c090>"        pipeline          Sep 23 16:20:47      _handleErrorMessage: error from /GstPipeline:pipeline1/GstBin:bin1/GnlComposition:gnlcomposition3/GnlSource:gnlsource: FileSourceFactory276/GstBin:bin284/pitivi+elements+singledecodebin+SingleDecodeBin:pitivi+elements+singledecodebin+singledecodebin67/GstQueue:queue36 (__main__.GstQueue): GStreamer encountered a general stream error. (gstqueue.c(1290): gst_queue_loop (): /GstPipeline:pipeline1/GstBin:bin1/GnlComposition:gnlcomposition3/GnlSource:gnlsource: FileSourceFactory276/GstBin:bin284/pitivi+elements+singledecodebin+SingleDecodeBin:pitivi+elements+singledecodebin+singledecodebin67/GstQueue:queue36:
streaming task paused, reason error (-5)) (/usr/lib/pitivi/python/pitivi/pipeline.py:852)


```

---

### Post by MG&amp;TL on 2011-09-23
Yeah, there's loads of alternatives. Best thing about Ubuntu-if you don't like something, or it doesn't work for you, typically here's a choice of three or four. Or several thousand, if you're talking something controversial like text editors, or DEs.

---

