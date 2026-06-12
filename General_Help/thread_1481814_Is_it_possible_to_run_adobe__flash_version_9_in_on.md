---
title: "Is it possible to run adobe  flash version 9 in one browser and 10 in another?"
date: 2010-05-12
forum: General Help
---

### Post by waynefoutz on 2010-05-12
I'm running Hardy. 

I'm noticing some sites I go to work flawlessly in version 9, but flicker with version 10.Other sitese work great with version 10, and some sites need version 10, like Fancast and Hulu.  Is it possible to have separate browsers, for example Firefox running version 9, and Chromium running 10?

---

### Post by upbeat.linux on 2010-05-13
A shot in the dark but are you running 64bit Ubuntu?  If you are installing from repository you are most likely getting the x32 which has known issues with x64.  There's an installer script to install the correct version here:

[http://helpforlinux.blogspot.com/2010/05/install-flash-player-10-on-ubuntu-1004.html](http://helpforlinux.blogspot.com/2010/05/install-flash-player-10-on-ubuntu-1004.html)

You also might have good luck compiling from source.  Flash 10 pre-releases are available on the Adobe labs page:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

If all else fails you could try Gnash, but you're mileage may vary:

[http://www.gnashdev.org/](http://www.gnashdev.org/)

Further reading:

[https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins)

Sorry for all the info, but figured its worth troubleshooting a bit.

---

### Post by waynefoutz on 2010-05-13
I found a solution to this. I'm running 32 bit hardy. Youtube and other sites were giving me flickering problems with Flash 10, but look great with 9, and other sites required 10. I found a Firefox add on that forces Firefox into using 9. 

Low Quality Flash

[https://addons.mozilla.org/en-US/firefox/addon/80205/]("https://addons.mozilla.org/en-US/firefox/addon/80205/")

This cured my flickering problem.

---

### Post by ehabh on 2010-05-19
I have flickering too whenever I scroll a webpage only the flash flickers, I am on 10.04 on 64 bits.

---

### Post by ehabh on 2010-05-19
This plugin does not run flash 9 I tried it, it only makes flash run in low quality and it did not fix my flickering.

> **waynefoutz said:**
> I found a solution to this. I'm running 32 bit hardy. Youtube and other sites were giving me flickering problems with Flash 10, but look great with 9, and other sites required 10. I found a Firefox add on that forces Firefox into using 9. 

Low Quality Flash

[https://addons.mozilla.org/en-US/firefox/addon/80205/]("https://addons.mozilla.org/en-US/firefox/addon/80205/")

This cured my flickering problem.

---

### Post by ehabh on 2010-05-19
Thanks this installer fixed my flash problems :)

> **upbeat.linux said:**
> A shot in the dark but are you running 64bit Ubuntu?  If you are installing from repository you are most likely getting the x32 which has known issues with x64.  There's an installer script to install the correct version here:

[http://helpforlinux.blogspot.com/2010/05/install-flash-player-10-on-ubuntu-1004.html](http://helpforlinux.blogspot.com/2010/05/install-flash-player-10-on-ubuntu-1004.html)

You also might have good luck compiling from source.  Flash 10 pre-releases are available on the Adobe labs page:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

If all else fails you could try Gnash, but you're mileage may vary:

[http://www.gnashdev.org/](http://www.gnashdev.org/)

Further reading:

[https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins)

Sorry for all the info, but figured its worth troubleshooting a bit.

---

