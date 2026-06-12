---
title: "Skype video problem with Logitech Quickcam"
date: 2010-04-26
forum: General Help
---

### Post by noob555 on 2010-04-26
Hi Everyone,

I have a Logitech Quickcam for Notebooks, ID 046d:08dd.
I'm running Karmic 32-bit, on an IBM X41 Thinkpad.

Until recently, the video on Skype worked if I opened Skype by using the following workaround, which is now well-known.

Code:

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

But a couple weeks ago it stopped working. I don't know why. Now I can't figure out any way to get my outgoing video to work in Skype. The SkypeWebcams-Wiki does not indicate a workaround.

I appreciate any help that you can offer.

---

### Post by noob555 on 2010-04-27
Bump?  Anyone?  Please?

---

### Post by LurkyLou on 2010-04-27
hmm. Do you have "qc-usb-source" enabled?  These are logitech webcam drivers, you can find via Synaptic Package Manager.

---

### Post by noob555 on 2010-04-27
Thank you for your response.

I just downloaded qc-usb-source from Synaptic, but the video didn't change at all. Thoughts?  

One thing occurred to me, should I be downloading the source code?  Don't I need the binary or something like that?

---

### Post by LurkyLou on 2010-04-27
I don't think you should have to download the source/binary, enabling from Synaptic should do it.  Does the cam work in other programs, like 'cheese'?
Have you rebooted lately?

---

### Post by noob555 on 2010-04-28
The camera works fine in Cheese.  And it was working in Skype via the workaround mentioned above for quite some time.  But for some reason it just stopped working a couple weeks ago.  And I just don't know why.

If I try to use the workaround now, I get the following error:

```
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
```

I imagine it's because something was updated, but I don't have a clue how to figure out what changed.  That's way above my skill level.

---

### Post by LurkyLou on 2010-04-28
Do you have 'skysentials' enabled in Synaptic?

---

### Post by noob555 on 2010-04-28
No, but I don't think Skysentials has anything to do with video.  According to the website, it's about SMS, Registering your Mobile phone, and, transferring calls.

---

### Post by josta7 on 2010-05-07
Mine just stopped working yesterday... it seemed to get flaky around the time that your cam stopped working but it crashed yesterday and now it won't start at all... my hack that I found on here was a little different, had a little bit more on it:
 sh -c 'export XLIB_SKIP_ARGB_VISUALS=1 && LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype'
But that's what got my Logitech cam working.... it was fine until yesterday it crashed mid-call and ... nothing now. :/ It stutters starting up, I see the icon and the program, but it closes every time, giving this message in the terminal:

bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
skype: pcm_null.c:130: snd_pcm_null_start: Assertion `null->state == SND_PCM_STATE_PREPARED' failed.
Aborted
:frown:
Glad to know I'm not the only one!

---

### Post by ashwyn on 2010-05-12
Same issue, I get this when I start it from the terminal now.

user@user-laptop:~$ LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

This only started after upgrading to 10.04, and installing the latest version of skype.

---

