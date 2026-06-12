---
title: "640x480 highest resolution, WM actions don't work"
date: 2010-02-20
forum: General Help
---

### Post by Dr.Dixie on 2010-02-20
Hullo, there...I've had these problems for weeks...but my Win7 RC is running out pretty soon, so I've got to get Ubuntu back up and operational if I want to continue using my computer (except I do have XP on another partition...still, there's tons on my Linux-only accessible partitions that I wish I didn't have to copy over...)

First, I think I should give you the details in chronological order (so to speak). When I boot up, GRUB naturally takes its usual resolution (720x400, I think)...I wouldn't expect this to be a problem either.
After selecting my Ubuntu installation and booting it, it shows a bit of text (pretty usual stuff, I'd think) and then goes to the Ubuntu loading screen. On this, it's set to 1600x1200. After it's loaded, however, one of two things have happened, I think.

First possibility: the screen goes blank, stays at 1600x1200, and won't change unless you make it go to screen 7 (CTRL+ALT+F7). When you go to screen 7, though, the screen goes to the login at 640x480. It stays this way throughout the X session (supposing it is an X session...I don't know much about this stuff, but I have reason to doubt it...details later). 

When I go into my NVidia settings thing (I've got a GeForce 8600GT with 256 MB of VRAM...if you want more details, I can get 'em), I find that, in reality, my screen can go to a number of non-3:4 resolutions, including our TV's 1360x768. I've used my computer multiple times on the TV, if that's relevant, and it is currently connected by a DVI-HDMI cable. Again, there are no higher resolutions that are 3:4...there is no 1280x960, no 1600x1200, no 2048x1536 (yeah, my CRT can do that!). Also, I think I should note, the output to the TV is flawless...I'd have to test it, alone, to see whether the X issues are resolved that way, but I doubt it.

I've tried at least three different drivers, including (I think) the beta one, a well-antiquated one, and the two that Ubuntu suggests. 

Now, it's probably important to note that the monitor and highest resolution (2048x1536) works FINE on Windows 7. It's been running great since the beginning. (I got the GeForce 8600 a few weeks ago, and have used it for games in Windows)

Also, it might be important to note that I'm using a DVI-VGA converter to connect my monitor...except, now that I think of it, it ought to fail in Windows just as badly.

Well...on to the X problems. I just brought up Ubuntu to do this, and, when I'm not in a text box (perhaps not at a few other times, too), the cursor is the waiting cursor...the ball with the Firefox-esque throbber. I cannot move the window, resize the window, or full-screen the window (F11, y'know?). Currently, in fact, I can't close this window except by its own built-in menu (meaning not by the X button or ALT+F4 I'd usually use). Also, I can't change windows...I'll update this post, I guess, if I remember anything else that's ticking me off about it.

Also, I started up my persistent 64-bit Ubuntu on USB a few times, and that came up with similar (but not identical) problems. Compiz actually starts up and starts working, and the maximum resolution is upped to 1024x768. This is still abysmal compared to my usual, and can't be tolerated by me for more than a few hours (except in games). The NVidia settings for this, likewise, though, have the highest resolution at 1360x768...which doesn't look very good on a 3:4 CRT, for those of you who no longer remember.

Well, I guess that's all...I can supply logs, Xorg.confs or messages or whatever you need...I might not get them up within the day, though.


!Dr.Dixie!

---

### Post by Dr.Dixie on 2010-03-01
*major bump*


!Dr.Dixie!

---

### Post by namluc on 2010-03-01
you've done a really good job of breaking your problems down in to lots of small paragraphs, try and be a bit more concise next time, might help you get a quicker reply!

i think you are missing a driver. have you checked 

system -> administration-> hardware drivers?

yes/no?

if there is nothing there, update your system, then do a google search, or a synaptic search, for nvidia drivers, look at my picture. install the right one, or trial and error until you get the right one, and you should be ok.

Reading your post again, i can see you've been looking for drivers.it must be a driver problem, there is no way that this is not fixable.

do you have the nvidia x server thing in my thumbnail, that controls ALL of my graphics

---

### Post by Dr.Dixie on 2010-03-01
Ok, sorry for not being concise. I'm rather prone to go toward the long-winded side of things.

First, yes, I've checked for drivers...I've tried both the ones that Ubuntu suggests, as well as a beta one that I downloaded from NVidia.

Also important: I just created a new live installation of Ubuntu on my USB flash drive, and it originally came up with 1024x768. Then I installed the NVidia driver, and it went down to 640x480 without WM controls. Couldn't close a window, move a window (even with ALT+LMB), etc. I couldn't even change windows, unless I closed the one on top!

And, yes, I do have the NVidia settings window.


!Dr.Dixie!

---

### Post by Dr.Dixie on 2010-03-11
*rebump*


!Dr.Dixie!

---

