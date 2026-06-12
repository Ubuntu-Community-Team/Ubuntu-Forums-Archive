---
title: "Chrome Triggering Webcam"
date: 2012-07-19
forum: General Help
---

### Post by Big Dan on 2012-07-19
Hi Folks, 

  I have kind of an odd situation. Fresh install of Ubuntu with a Chrome download from google.com/chrome. My webcam's activity light keeps flickering when Chrome is running. Chrome is also very slow No extensions other than Lastpass and Xmarks. I've never seen Chrome do this before. Any ideas?

Thanks, 
Dan

---

### Post by akai_kenshi on 2012-07-20
Sounds like this issue _[here.]("http://productforums.google.com/d/topic/chrome/TU74PFU9NNQ/discussion")_

What kind of webcam are you using, out of curiosity? I've got a Microsoft LifeCam Studio that gets crashed by Gmail and Google Drive in Chrome. Ubuntu's included version of Chromium doesn't seem to cause any problems, if you don't mind using that.

---

### Post by Big Dan on 2012-07-20
> **akai_kenshi said:**
> Sounds like this issue _[here.]("http://productforums.google.com/d/topic/chrome/TU74PFU9NNQ/discussion")_

What kind of webcam are you using, out of curiosity? I've got a Microsoft LifeCam Studio that gets crashed by Gmail and Google Drive in Chrome. Ubuntu's included version of Chromium doesn't seem to cause any problems, if you don't mind using that.

Thanks. I have the same webcam, Lifecam Studio here. 

I'll check out Chromium here. By any chance do you know if you can use regular Chrome extension with it?

---

### Post by akai_kenshi on 2012-07-20
I haven't used Chromium that much so I can't say for sure, but I see no reason why they wouldn't. Chromium is the open-source version of Chrome so it's essentially the same browser. The only real differences are with some included codecs and plugins. Also, the version of Chrome that Google provides is a bit more up-to-date than the one of Chromium in the Ubuntu repos.

I do hope that Google fixes this bug, though.

---

### Post by Big Dan on 2012-07-20
> **akai_kenshi said:**
> I haven't used Chromium that much so I can't say for sure, but I see no reason why they wouldn't. Chromium is the open-source version of Chrome so it's essentially the same browser. The only real differences are with some included codecs and plugins. Also, the version of Chrome that Google provides is a bit more up-to-date than the one of Chromium in the Ubuntu repos.

I do hope that Google fixes this bug, though.

Thanks. I found out Chrome extension work fine in Chromium and am surfing along happily.:KS

---

### Post by shecky on 2012-07-30
Seems to be a bug in Chrome's PepperFlash plugin.
-Go to *about:plugins* in Chrome
-Click *+Details* to expand all items
-Under the Flash header, disable *"/opt/google/chrome/PepperFlash/libpepflashplayer.so"*
Leave the regular *libflashplayer.so* plugin enabled, or install it if you need to. Should stop the flickering.

---

### Post by Big Dan on 2012-07-30
> **shecky said:**
> Seems to be a bug in Chrome's PepperFlash plugin.
-Go to *about:plugins* in Chrome
-Click *+Details* to expand all items
-Under the Flash header, disable *"/opt/google/chrome/PepperFlash/libpepflashplayer.so"*
Leave the regular *libflashplayer.so* plugin enabled, or install it if you need to. Should stop the flickering.

This worked. Thank you! :)

---

### Post by mörgæs on 2012-07-30
Good, then please mark the thread 'solved' using 'thread tools'.

---

