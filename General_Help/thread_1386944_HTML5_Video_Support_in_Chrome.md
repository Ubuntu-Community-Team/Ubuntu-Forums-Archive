---
title: "HTML5 Video Support in Chrome"
date: 2010-01-21
forum: General Help
---

### Post by Thelasko on 2010-01-21
I've been playing around with [Google's new HTML5 version of You Tube]("http://www.youtube.com/html5") with the daily build of Chromium.  Unfortunately, I keep getting a message that says, "Your browser does not recognize any of the video formats available."  I've noticed a package called, "chromium-codecs-ffmpeg-nonfree" in the PPA, but that didn't fix anything.  Has anyone been able to get this to work?

---

### Post by Zorael on 2010-01-21
No luck here. The [Chromium issue entry](http://code.google.com/p/chromium/issues/detail?id=13416) regarding this suggests that we need to separately install ffmpeg, which I have - but to no success. I tried making symlinks to the libraries mentioned, into /usr/lib/chromium-browser, but that didn't help.

I haven't tried recompiling it myself yet (I'm using the ppa as well.) And FWIW, I'm on a 32-bit installation.

---

### Post by themgt on 2010-01-21
You need to install libavcodec-extra-52. It's working for me now.

---

### Post by themgt on 2010-01-21
Oops, no it's not. Bugger. It slipped in a flash one to confuse me.

---

### Post by nortexoid on 2010-01-21
Still no luck huh? Is it just a matter of installing the relevant codec pack?

---

### Post by nortexoid on 2010-01-21
After doing some searching, it appears that the reason linux Chromium won't support the format is due to licensing issues with h.264. Same with open source firefox.

---

### Post by abrahamsmith on 2010-01-21
> **nortexoid said:**
> After doing some searching, it appears that the reason linux Chromium won't support the format is due to licensing issues with h.264. Same with open source firefox.


Do you have a link to this reference?

If true, it seems like an odd decision, since the browser itself doesn't really have to do anything, it just has to pass the content onto a system backend (ffmpeg, gstreamer, whatever) that handles whatever media it can.

---

### Post by nortexoid on 2010-01-21
> **abrahamsmith said:**
> Do you have a link to this reference?

If true, it seems like an odd decision, since the browser itself doesn't really have to do anything, it just has to pass the content onto a system backend (ffmpeg, gstreamer, whatever) that handles whatever media it can.

Here's a thread: [http://www.google.co.uk/support/forum/p/youtube/thread?tid=0eb07f33a7614546&hl=en](http://www.google.co.uk/support/forum/p/youtube/thread?tid=0eb07f33a7614546&hl=en)

And there's a bunch others if you do a search for something like "youtube html5 "does not currently"".

---

### Post by Thelasko on 2010-01-21
> **nortexoid said:**
> After doing some searching, it appears that the reason linux Chromium won't support the format is due to licensing issues with h.264. Same with open source firefox.

There are two versions of ffmpeg available for Chromium.  The default is free software only, but you can install the nonfree version as well.

I already have the nonfree version installed, and it hasn't helped.

---

### Post by abrahamsmith on 2010-01-21
Right. I have -nonfree installed, (and all of the medibuntu codecs, etc) and it still doesn't work.  It's not clear to me what's actually happening here.

---

### Post by Thelasko on 2010-01-21
> **abrahamsmith said:**
> Right. I have -nonfree installed, (and all of the medibuntu codecs, etc) and it still doesn't work.  It's not clear to me what's actually happening here.

I'm guessing it's just a bug.

---

### Post by abrahamsmith on 2010-01-22
here it is:
[http://code.google.com/p/chromium/issues/detail?id=21318](http://code.google.com/p/chromium/issues/detail?id=21318)

---

### Post by Anubis on 2010-01-22
Works just fine for my system.

Google Chrome 4.0.249.43

[http://imagebin.ca/view/2COe7dSw.html]("http://imagebin.ca/view/2COe7dSw.html"):guitar:

---

### Post by manoynmonic on 2010-01-22
> **abrahamsmith said:**
> Right. I have -nonfree installed, (and all of the medibuntu codecs, etc) and it still doesn't work.  It's not clear to me what's actually happening here.


Same here.  HTML5 wont work on Chromium-browser.  Works fine on Google Chrome though.:confused:

---

### Post by Thelasko on 2010-01-22
Last night's update (Chromium 4.0.304.0) seems to have solved the issue for me.  I now have HTML5 video.  A few bugs to note:

[LIST=1]
[*]The time code and navigation bar aren't correct.

[*]No full screen support. (this may be a "feature")

[*]I notice that when I move my mouse across the video it skips slightly.  This may be an issue with my video card.
[/LIST]

---

### Post by nortexoid on 2010-01-23
> **Thelasko said:**
> There are two versions of ffmpeg available for Chromium.  The default is free software only, but you can install the nonfree version as well.

I already have the nonfree version installed, and it hasn't helped.

How'd you install the non-free codec? It keeps giving me dependency issues.

---

### Post by Thelasko on 2010-01-23
> **nortexoid said:**
> How'd you install the non-free codec? It keeps giving me dependency issues.

I just went into synaptic and installed it.  The only dependency issue it had was that it had to uninstall the free codec.

I'm using Hardy Heron, so it might be version specific.

---

### Post by nortexoid on 2010-01-23
> **Thelasko said:**
> I just went into synaptic and installed it.  The only dependency issue it had was that it had to uninstall the free codec.

I'm using Hardy Heron, so it might be version specific.

Ah, KPackageKit was making it impossible so I just did an install via konsole/terminal.

The video quality is worse than "480p" flash, but on my system it uses about 15% less cpu utilization. You also lose fullscreen capability and the option to choose various other video settings. All in all, not very enticing unless you're having some serious issues with flash.

---

### Post by Thelasko on 2010-01-23
> **nortexoid said:**
> Ah, KPackageKit was making it impossible so I just did an install via konsole/terminal.

The video quality is worse than "480p" flash, but on my system it uses about 15% less cpu utilization. You also lose fullscreen capability and the option to choose various other video settings. All in all, not very enticing unless you're having some serious issues with flash.

I'm hoping those issues get resolved.  Try the Vimeo HTML5 player.  It seems a bit more advanced.

---

### Post by PC_load_letter on 2010-01-23
> **themgt said:**
> You need to install libavcodec-extra-52. It's working for me now.

I installed this library, and it automatically uninstalled the free version. Now, with Chromium, I can view some videos on youtube but others simply do not play as I keep getting a busy animated HTML5 icon. So, does this mean not all videos are available in this format, or do I have a problem?

---

### Post by Exilant on 2010-07-30
Has this been solved for you?

With current chromium-daily, i can view no html5 or webm videos, chromium-browser and chromium-codecs-ffmpeg-nonfree are installed.

It should work in non-ubuntu-chromium, I was told, but i get the aforementioned "Your browser does not currently recognize any of the video formats" message instead of a video

---

### Post by nortexoid on 2010-07-30
> **Exilant said:**
> Has this been solved for you?

With current chromium-daily, i can view no html5 or webm videos, chromium-browser and chromium-codecs-ffmpeg-nonfree are installed.

It should work in non-ubuntu-chromium, I was told, but i get the aforementioned "Your browser does not currently recognize any of the video formats" message instead of a video

I'm using the chromium-dev ppa (newer than stable, older than daily) and html5 works just fine (e.g. in Youtube) using the nonfree codecs. I would suggest uninstalling the daily build and going with the dev channel. (There's good reason for doing this in general that I need not cite here.)

---

### Post by Exilant on 2010-07-30
Thank you very much, nortexoid.

I wasn't aware of the dev-ppa's existence.  With the chromium there at least my 32-bit-laptop works with html5 and webm, i'll test the 64-bit machine tomorrow.

---

### Post by Tich666 on 2010-08-02
Using the "dev" ppa instead of the "daily" one fixed it for me on 64bit too. Thanks for the tip!

Link to the "dev" ppa:
[https://launchpad.net/~chromium-daily/+archive/dev/](https://launchpad.net/~chromium-daily/+archive/dev/)

---

### Post by lukeiamyourfather on 2010-08-02
> **manoynmonic said:**
> Same here.  HTML5 wont work on Chromium-browser.  Works fine on Google Chrome though.:confused:

Chromium != Chrome

From my understand of it, if you want H.264 support then use Chrome which is the Google product based on the open source project Chromium.

---

### Post by xiphosurus on 2010-12-07
html5 video is still not working for me in chromium dev build. Currently my Chromium is 9.0.597.0 (67679) Ubuntu 10.10, 64 bit. I have chromium-codecs-ffmpeg-nonfree installed. WebM in youtube doesn't work, telling me "your browser does not currently recognize any of the video formats available". The same video will work in Chrome 9.0.597.0 dev. The html5 video test in [http://html5demos.com/video](http://html5demos.com/video) also doesn't work for Chromium but works for Chrome. Is it working for you guys?

---

