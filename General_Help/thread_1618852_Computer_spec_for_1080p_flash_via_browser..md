---
title: "Computer spec for 1080p flash via browser."
date: 2010-11-11
forum: General Help
---

### Post by oshirowanen on 2010-11-11
What is the minimum computer spec for playing 1080p flash files via a web browser smoothly at least 25fps?

We all know that flash is not very good on Linux.  On my old computer, I can play 720p flash files in the browser at arount 25fps on Windows, but on Ubuntu on the same computer via dual OS installation, it struggles to play 420p flash files in the browser.

So basically, i want to build a new computer and have Ubuntu as the only OS, but this computer needs to be able to play 1080p flash files via the browser (not by downloading and converting them), but straight from the browser smoothly.

Is this possible and what would the minimum computer spec need to be to achieve this?

---

### Post by oshirowanen on 2010-11-15
The lack of responses and my unsuccessful search attempts is giving me the impression that no amount of commercially available computer hardware power can give smooth playback of 1080p flash video via a web browser on Linux.

Someone please tell me I'm wrong.

---

### Post by cyrus_the_virus on 2010-11-15
> **oshirowanen said:**
> The lack of responses and my unsuccessful search attempts is giving me the impression that no amount of commercially available computer hardware power can give smooth playback of 1080p flash video via a web browser on Linux.

Someone please tell me I'm wrong.

After applying the following fix it became significantly better for me.
> 
- In CompizConfig Settings Manager (installable via Ubuntu Software Cemter), go to General Options > Display Settings. Set Refresh Rate to 60 and check “Sync to VBlank.”
- Enable “Sync to VBlank” under nvidia-settings. To do this, go to System > Administration > NVIDIA X Server Settings. Then, choose OpenGL Settings, and check the “Sync to VBlank” box.
 
This will only work if you have an nvidia graphic card with the official driver installed.

---

### Post by oshirowanen on 2010-11-17
I was looking for the minimum hardware requirements without software tweaking to get smooth 1080p flash playback via a browser such as Chromium.
 
So basically, I want to build a computer for 1080p browser playback, and I want it smooth out of the box.
 
What kind of hardware requirements should I be looking at.  Or, is flash so bad on Linux that no commercially available computer hardware is capable of achieving my objective?
 
My objective is to build a computer and only have ubuntu has the operating system, which is able to play back 1080p video smoothly via a web browser out of the box.
 
The most I look into this, the most impossible it seems...

---

### Post by cchhrriiss121212 on 2010-11-17
It does depend on what site you are viewing these videos from, Youtube for example has better performance than other websites. 
You can also simply load the video up and then watch it with an external player like VLC via your tmp folder. [This addon]("https://addons.mozilla.org/en-US/firefox/addon/161869/") for firefox will also be helpful.

In terms of hardware a gt210 by Nvidia and any mid range cpu would be fine. My system for example plays 1080p flash fine with this (which is by no means top of the line):
Athlon II 245 @2.9GHz
Nvidia 9600GT
this goes out to a 1920x1200 monitor.

But I have not tested this recently  and only with a few videos as my connection is far too slow for streaming 1080p. If you post a link to what sites you would like to watch I will report how it performs.

---

### Post by oshirowanen on 2010-11-17
If using Chromium, do you know the tmp folder where it will store the flash files?
 
I mainly want to play 1080p files from youtube.

---

### Post by blueridgedog on 2010-11-17
Most current nvidia cards and processors can easily handle 1080p playback.  The issue is typically internet bandwidth and that can be solved by playing the file off of the hard drive rather than as an internet stream.  There are a variety of tools to get content on the hard drive for later watching.  For example:

[http://www.ubuntugeek.com/howto-download-videos-from-youtube-in-ubuntu.html](http://www.ubuntugeek.com/howto-download-videos-from-youtube-in-ubuntu.html)

---

### Post by oshirowanen on 2010-11-17
Bandwidth speed does not seem to be an issue for me, it's more to do with trying to play the video streaming via a browser such as chromium at a decent framerate.

---

### Post by cchhrriiss121212 on 2010-11-17
For chromium, it should be: 
/home/user/.cache/chromium/Cache
(Files or folders with a "." prefix are hidden by default, so use ctrl+h to see them)

Keep in mind that other factors contribute beyond connection speed. You should install proprietary drivers and use the 64bit flash plugin to get better performance (assuming you use a 64bit install). Ubuntu will install open drivers out of the box, and the flash plugin in the ubuntu-restricted-extras package is always 32bit.

Edit: just tested some 1080p video using the latest chromium which plays nice and smooth on the hardware mentioned earlier at fullscreen. Running from within chromium uses ~70% cpu on both cores, opening the video externally with smplayer or VLC uses around 10%.

---

