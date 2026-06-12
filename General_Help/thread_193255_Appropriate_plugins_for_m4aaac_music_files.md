---
title: "Appropriate plugins for m4a/aac music files"
date: 2006-06-09
forum: General Help
---

### Post by djb on 2006-06-09
I recently upgraded to Ubuntu 6.06 and had to install some of the GStreamer plugins to get m4a playback to work. I followed the instructions on the [RestrictedFormats]("http://wiki.ubuntu.com/RestrictedFormats") page, but still couldn't get my m4a files to play. I ended up installing the gstreamer0.10-plugins-bad package in addition to the gstreamer0.10-plugins-bad-multiverse package. The former is not listed on the Wiki page, however playback of m4a files only works for me when I have *both* installed.

I doubt that this is a typo in the Wiki - more likely it has something to do with my specific setup, but I wanted to post it here just in case anyone else is having the same problems.

---

### Post by Rebeca on 2006-06-11
Thank you for posting this. I had the same problem, but it was fine after I installed the plugins-bad package.

---

### Post by rsk on 2006-06-17
djb,
You just saved me from certain suicide. I've been trying ALL NIGHT to get this working (playing songs off my iPod) and have every other codec known to man installed, nothing was working.

I installed BAD and bam, everything is working now.

---

