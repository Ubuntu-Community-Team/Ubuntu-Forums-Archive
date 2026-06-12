---
title: "Frequent Bizarre Lockups/Freezes, but Still Running"
date: 2012-07-19
forum: General Help
---

### Post by DaPlipsta on 2012-07-19
Hello forum users,
I am running Ubuntu 12.04 on a custom AMD machine. My OS boots properly and works fine for a while, but then will freeze seemingly at random. The first couple of times it happened I thought it was just a normal lockup and just performed hard restarts, but then I noticed the computer was acting strangely while it was frozen. The mouse and keyboard both fail to work during these freezes, but yet the computer is clearly still working. I decided as an experiment to open up my system monitor and then wait for the lockup. Sure enough, after the mouse and keyboard froze, the system monitor continued to log processor function and network function as well, just at a reduced framerate. I decided to just let it do its thing for a while. The screen soon fell asleep, and occasionally it would awaken just to show my blank wallpaper, still not responding to mouse movement or keystrokes.

I don't know for sure yet, but this could be an issue related to high network volume. I had to use ndiswrapper to get my Netgear WNA3100 working, and it works fine (other than this freeze glitch which may or may not even be related). However, it could be a network volume issue because it froze a few times when I was attempting to install massive system updates at first (this is a new system) and its freezing now, perhaps due to my near full dropbox automatically downloading all of my files.

My computer is a custom build. It is running Ubuntu 12.04 x64.
Gigabyte mobo, AMD FX-4100 CPU, 8 gb matched RAM DDR3, a 64 gb SSD, and for graphics a NVIDIA GTS450. As I already mentioned my wireless card is a Netgear WNA3100 usb.

There are no hardware problems, its a relatively new system and my Win7 install works fine.

Any thoughts?

---

### Post by soslug on 2012-07-20
I also am running 12.04 64bit only on a Dell Inspiron 1521. I have experienced many lockups which are also truly bizarre, I can for instance play a video via youtube and the video will cease but the audio continues and the mouse movement is maintained, however all other keyboard and desktop functions are disabled. The problem is not only confined to audio and or video just using the internet I am using the chromium browser, further it matters not if the system itself is hot or cold. 

I am having to use an earlier version of wireless networking as the driver supplied does not support my device and as a result experience many daily re-curable data trip outs, where the signal will be lost and seeks to reacquire.

The lockup problem I seem the experience perhaps two or three times a day, I hope a solution to both the above problems can be found soon.

regards



> **DaPlipsta said:**
> Hello forum users,
I am running Ubuntu 12.04 on a custom AMD machine. My OS boots properly and works fine for a while, but then will freeze seemingly at random. The first couple of times it happened I thought it was just a normal lockup and just performed hard restarts, but then I noticed the computer was acting strangely while it was frozen. The mouse and keyboard both fail to work during these freezes, but yet the computer is clearly still working. I decided as an experiment to open up my system monitor and then wait for the lockup. Sure enough, after the mouse and keyboard froze, the system monitor continued to log processor function and network function as well, just at a reduced framerate. I decided to just let it do its thing for a while. The screen soon fell asleep, and occasionally it would awaken just to show my blank wallpaper, still not responding to mouse movement or keystrokes.

I don't know for sure yet, but this could be an issue related to high network volume. I had to use ndiswrapper to get my Netgear WNA3100 working, and it works fine (other than this freeze glitch which may or may not even be related). However, it could be a network volume issue because it froze a few times when I was attempting to install massive system updates at first (this is a new system) and its freezing now, perhaps due to my near full dropbox automatically downloading all of my files.

My computer is a custom build. It is running Ubuntu 12.04 x64.
Gigabyte mobo, AMD FX-4100 CPU, 8 gb matched RAM DDR3, a 64 gb SSD, and for graphics a NVIDIA GTS450. As I already mentioned my wireless card is a Netgear WNA3100 usb.

There are no hardware problems, its a relatively new system and my Win7 install works fine.

Any thoughts?

---

### Post by DaPlipsta on 2012-09-12
bump

---

### Post by batbrownbear on 2012-10-18
I am experiencing the same problems that you have described.  I started having them after purchasing the Netgear WNA3100 network adapter and using ndiswrapper to set up the driver.  My current solution is to purchase the same adapter that I had previously and presented no such problems.

---

### Post by Lisiano on 2012-10-19
I am running 12.10 but I also had lockups. Mine were caused by the nouveau driver, after switching to the proprietary nVidia driver, my system is running like butter. This might apply to 12.04.

I have a GT320 if it matters.

---

