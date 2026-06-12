---
title: "How to record a webinar?"
date: 2012-08-22
forum: General Help
---

### Post by ELMIT on 2012-08-22
I need to record a webinar (for myself), which I attend. 

I tried many different ways, but nothing really got me to a satisfactory result.

I have installed Jack and qjackctl, that did not the trick yet either.

To record I use recordmydesktop. However, if at all, then the sound is very low, ... 
With Jack even the webinar stops and no sound at all, ...


Ant for Firefox does not record webinars. 

Any hint how to record?

---

### Post by llamabr on 2012-08-22
[https://addons.mozilla.org/en-US/firefox/addon/downthemall/](https://addons.mozilla.org/en-US/firefox/addon/downthemall/)

Additionally, you might check with your webinar administrator to see if they are archived.  This will be the best quality, probably.

Also, let me take this opportunity to complain about the instance of such absurdities and mundanities entering mainstream English.  Webinar?

---

### Post by ELMIT on 2012-08-22
I tried this, but it does not work.

It downloads a file playershell.swf and to play it I used all programs I could think of:

Movie player
Gnash swf viewer
Lightspark
VLC media player

and I tried to drag it into firefox, where it played original. 

> 
Also, let me take this opportunity to complain about the instance of such absurdities and mundanities entering mainstream English. Webinar? 

?????

---

### Post by ELMIT on 2012-08-22
I tried this:

ffmpeg -i playershell.swf out_file.avi
ffmpeg version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:52:09 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[swf @ 0x131b9a0] Compressed SWF format not supported
playershell.swf: Input/output error


so I tried this:

avconv -i playershell.swf out_file.avi
avconv version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:52:09 with gcc 4.6.3
[swf @ 0x63a9a0] Compressed SWF format not supported
playershell.swf: Input/output error



How to uncompress *.swf ???

---

