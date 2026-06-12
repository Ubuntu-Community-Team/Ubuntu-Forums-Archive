---
title: "Importing PNG in Pitivi"
date: 2010-06-25
forum: General Help
---

### Post by deancasino on 2010-06-25
Hey guys every time I import a PNG file into Pitivi, I get this error:

Problem:GStreamer encountered a general stream error.
Extra information:gstqueue.c(1212): gst_queue_loop (): /GstPipeline:pipeline0/GstBin:bin0/GnlComposition:gnlcomposition0/GnlSource:gnlsource: PictureFileSourceFactory1/GstBin:bin2/GstQueue:internal-queue:
streaming task paused, reason not-negotiated (-4)


and the playback doesn't work any more until I close and reopen Pitivi. Any suggestions?

---

### Post by deancasino on 2010-06-25
bump

---

### Post by deancasino on 2010-06-26
Anyone?

---

### Post by deancasino on 2010-07-02
bump

---

### Post by fragos on 2010-07-03
Pitivi doesn't operate on PNG images. I suggest you try Lives as it can operate on almost any format and can be installed with Synaptic.

---

### Post by kiddo on 2010-09-03
Bad answer. Pitivi supports PNG, JPEG, JPEG2000, PNM, SVG, etc. What you encountered was a bug. In those cases, report the bugs on the official bug tracker, not on the forum. Devs don't look at the forums.

---

### Post by fragos on 2010-09-03
> **kiddo said:**
> Bad answer. Pitivi supports PNG, JPEG, JPEG2000, PNM, SVG, etc. What you encountered was a bug. In those cases, report the bugs on the official bug tracker, not on the forum. Devs don't look at the forums.

Have you used Pitivi? When doing File-> Open-> All supported formats on a folder with PNG, GIF and JPG still images, no files are shown, verified with current release in Ubuntu 10.04. Didn't look like a bug to me, just non-support of still image formats.

---

