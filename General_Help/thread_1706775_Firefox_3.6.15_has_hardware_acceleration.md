---
title: "Firefox 3.6.15 has hardware acceleration?"
date: 2011-03-14
forum: General Help
---

### Post by weirddan455 on 2011-03-14
Hardware acceleration is supposed to be a new feature in Firefox 4 but for some reason it seems that it's actually enabled in the Ubuntu 10.10 version of 3.6.15 (possibly other versions too) but not in the Windows version.

[http://hacks.mozilla.org/2010/09/hardware-acceleration/](http://hacks.mozilla.org/2010/09/hardware-acceleration/)

This is a test to see if you have it.  The difference in FPS with and without is substantial.  Here are my results.  I also tested Chrome 10 which does have and is documented to have hardware acceleration if you change these settings.

[http://lifehacker.com/#!5781261/turn-on-hardware-acceleration-in-google-chrome-10%252B](http://lifehacker.com/#!5781261/turn-on-hardware-acceleration-in-google-chrome-10%252B)

My results:

Windows 7 64 bit:
Chrome 10 (hardware acceleration disabled): 12 FPS
Chrome 10 (hardware acceleration enabled): 60+ FPS
Firefox 3.6.15: 6 FPS

Ubuntu 10.10 64 bit:
Chrome 10 (hardware acceleration disabled): 17 FPS
Chrome 10 (hardware acceleration enabled): 60+ FPS
Firefox 3.6.15: 60+ FPS

My specs:

Intel Core 2 Duo 6420 OC'd @ 2.67ghz
2 GB RAM
Nvidia GeForce 8800 GTX

If someone could click that link and run the test on Firefox (takes less than a minute) to confirm my suspicions I'd appreciate it.

---

### Post by lithopsian on 2011-03-14
Firefox 3.6.15 doesn't have hardware acceleration.  Nothing to "enable", it just isn't there.

---

### Post by weirddan455 on 2011-03-14
See that's what I thought.  It shouldn't have hardware acceleration but it also shouldn't be getting 60+ FPS if it doesn't.  Click that link for me in your Ubuntu box and prove me wrong.

---

### Post by lithopsian on 2011-03-14
First, I don't have 64 bit.  Second, I don't have 3.6.15.  I do have 3.6.8 (3.6 releases are security and bug fix, no functional changes, certainly nothing as big as hardware acceleration) and it scrapes above 1fps occasionally.  Third, my graphics card is blacklisted and won't accelerate that page even in 4.0 :p

I suspect a big in the javascript that is telling you 60fps but lying.  Or you are actually running a different version of Firefox.  Or your machine is astonishingly fast :)

---

### Post by lithopsian on 2011-03-14
You could also try about:support which tells you what sort of acceleration you have enabled.  Obviously in 3.6 versions it says nothing because there is no hardware acceleration.

You could also try forcing the Grafx Bot extension in and seeing what it says.

---

### Post by weirddan455 on 2011-03-14
Well I can actually see the animation go way faster so I know the number is right.  I've done this multiple times now.  Chrome is kind of acting as my baseline as it can be run hardware accelerated and not.  In Windows, the results are what you would expect.  Firefox performes worse than Chrome with hardware acceleration turned off.  In linux, Firefox performes as good as chrome with hardware acceleration turned on which doesn't make any sense unless ubuntu added some extra code or took Firefox 4 and branded it as Firefox 3.6.15.

---

### Post by weirddan455 on 2011-03-14
about:support says I have version 3.6.15, lists these extension:

Ubuntu Firefox Modifications	0.9rc2	true	[email]ubufox@ubuntu.com[/email]
QuakeLive.com Game Launcher	1.0.401	true	[email]quakeliveplugin@idsoftware.com[/email]

and these modified preferences:

browser.history_expire_days.mirror	180
browser.places.importBookmarksHTML	false
browser.places.smartBookmarksVersion	2
browser.startup.homepage_override.mstone	rv:1.9.2.15
extensions.lastAppVersion	3.6.15
network.cookie.prefsMigrated	true
privacy.sanitize.migrateFx3Prefs	true

I'm about to download Grafx Bot

---

### Post by lithopsian on 2011-03-14
The Ubuntu package in Maverick doesn't look like 4.0 although I didn't install it.

Try [FishIE]("http://ie.microsoft.com/testdrive/performance/fishIETank/default.html") which is a slightly tougher benchmark for hardware acceleration.

---

### Post by weirddan455 on 2011-03-14
Firefox 3.6.15 at a window size of 1920 x 974:
Below 50 was 60FPS constant
got from 40 - 60 FPS at 50 fish
around 58FPS at 100 fish
30 FPS at 250 fish
21 FPS at 500 fish
6 FPS at 1000 fish

Chrome 10 (hardware acceleration disabled) at window size 1911 x 974:
57FPS at 1 fish
48FPS at 10 fish
37 FPS at 20 fish
20 FPS at 50 fish
30 FPS at 100 fish (weird)
16 FPS at 250 fish
6 FPS at 500 fish
3 FPS at 1000 fish

Chrome 10 (hardware acceleration enabled) at window size 1911 x 974:
59FPS at 1000 fish and a constant 60FPS at everything else

Interesting... not sure what to take away from that

---

### Post by pqwoerituytrueiwoq on 2011-03-14
I believe the Linux branch of Firefox has had hardware acceleration for some time now via opengl
Fish IE test:
48 to 60 fps on ff4 (minefield)
usually upper 50s on 3.6.15

GeForce 8200M G rev 2a

lucid 64bit

---

### Post by weirddan455 on 2011-03-14
How do I force Grafx Bot to install?

---

### Post by lithopsian on 2011-03-14
> Interesting... not sure what to take away from that
Simple.  You don't have hardware acceleration but you do have a very good CPU.  And Firefox 3.6.15 is performing that test in software faster than Chrome 10.  Download Firefox 4.0 and see the difference.  I'm pretty sure your card is well supported for hardware acceleration, at least if you have the latest drivers.

> I believe the Linux branch of Firefox has had hardware acceleration for some time now via openglWebGL has been available for some time, and not just on Linux.  However, these benchmarks are not WebGL.  Linux hardware acceleration even in Firefox 4.0 is still somewhat limited compared to DirectX acceleration in the windows builds.

---

