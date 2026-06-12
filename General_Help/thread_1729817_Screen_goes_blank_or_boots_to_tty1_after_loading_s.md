---
title: "Screen goes blank or boots to tty1 after loading screen"
date: 2011-04-15
forum: General Help
---

### Post by nannirk on 2011-04-15
Hey.
So, like any other Linux newb, I came to Ubuntu because my Windows crashed one time too many.
And I chose Ubuntu because "it just works".
But these past few days that hasn't been true.

I'm posting this from a netbook with Ubuntu, and am having no problems whatsoever, but normally I use an Acer Aspire 5920G laptop. I'll include the specs as written on the sticker:
* Intel Core 2 Duo processor T5250 (1.5GHz etc)
* Up to 1024 MB Nvidia Geforce 8600M GS Turbocache
* 2 GB DDR2

Let me know if you need more details, and I'll add them later.

Now, what happened was I clicked "hibernate" while leaving Firefox open. (I've done this hundreds of times, no problem)
And when I went to turn it back on the next day there were weird graphical glitches in the loading screen, and it booted to the "tty1" prompt screen.
I did a lot of googling and found quite a few posts about it, but the solutions either didn't work, or I didn't understand them.
After trying several different suggestions from this forum and others,  I managed to delete the graphics drivers. That enabled me to boot in low graphics mode, and naturally, I tried a whole bunch of things to make it work properly again.
That only made it worse. Now it went straight from the loading screen to just blanking out and turning the display off. 
So, I tried new things. Over and over. The weird thing is even when I disconnected my harddrive and ran from a Live USB, the problem persisted. Could there be an issue with the graphics card itself?
Anyway, after reconnecting the harddrive I tried to boot again. And it suddenly worked. Even HDMI to my bigger screen worked.

But today, I tried to reinstall the current driver. The one Ubuntu suggests under System-->Administration-->Aditional Drivers.
Later, the Update Manager appeared, so I started updating, and it froze in the middle of the process.
Now it boots to a black screen all the time. Even when I try recovery mode.
And I don't know how to get back into tty1. Ctrl+Alt+F1 doesn't work.

Please help a newbie. I like the idea of open operating systems, and this is the first issue I've had with Ubuntu since switching around new year.

Also, feel free to hijack this thread if you're having similar issues.

---

### Post by nannirk on 2011-04-15
Ok, now I have access to the tty1 prompt.

I did this:
1) Hold down Shift while booting to get to grub.
2) Type 'e'. Then add "nomodeset" after "quiet splash".
3) Ctrl+x to boot.

Now to see if I can go back to a decent experiennce of Ubuntu.
Might have to live without video drivers.. Hope this doesn't last forever.

One suggestion was to enter this while in the command line.
```
sudo nvidia-xconfig --add-argb-glx-visuals --no-logo --force-generate
```
Hasn't helped so  far.
I really don't know what to do here..

---

