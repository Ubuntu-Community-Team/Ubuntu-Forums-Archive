---
title: "Why Video is very blocky when I changed ATI drivers?"
date: 2006-03-17
forum: General Help
---

### Post by matts0344 on 2006-03-17
Ever since I changed my ATI drivers (can't remember exactly what I did because it was a while ago). I changed it to get hardware acceleration because I had none and things were very slow in the desktop.

I changed the drivers from the default to the fgrlx (something like that :D )

After I did this all my video files in VLC, Mplayer or anything are terribly blocky, pretty unwatchable so I have to boot to windows to watch anything.

Anyone heard of this or have any suggestions on how I might fix this?

Thanks for any help you can give. 

I may be able to take some screenshots later if need be.

---

### Post by bluevoodoo1 on 2006-03-17
Why not change it back to what it was before? It was working correctly before right? 

What graphics card are you using?

---

### Post by matts0344 on 2006-03-17
The reason I don't want to change it back is that things run too slow on the old drivers (even just browsing webpages) because there is apparently no hardware acceleration.

When I did the gear test thing, they ran very slow. 

If I wanted to change it back do I just run the X11 config?

I'm using a Radeon 9600 by the way.

---

### Post by bluevoodoo1 on 2006-03-17
[QUOTE=matts0344]The reason I don't want to change it back is that things run too slow on the old drivers (even just browsing webpages) because there is apparently no hardware acceleration.[/QUOTE]

Ohhh, ok. Now I got you. Yeah, try running "sudo dpkg-reconfigure xserver-xorg" and try using the "ati" or "radeon" drivers. See if that helps. Make a backup of your xorg.conf first. And if there is trouble, use the "vesa" driver to get you back on track. 

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

This is the ATI page you might have been referring to... if you have trouble, might want to look through that thread, or post there, the author of the thread is very knowledgeable.
[http://ubuntuforums.org/showthread.php?t=75378](http://ubuntuforums.org/showthread.php?t=75378)

By the way, what does the output of "glxgears -printfps" give you?

---

### Post by matts0344 on 2006-03-17
glxgears -printfps gives me

14934 frames in 5.0 seconds = 2986.768 FPS


I switched back to the old driver and now I get:

1778 frames in 5.3 seconds = 337.293 FPS

BUT now my videos look fine.

Is this normal? I haven't tried to play any games with this ATI drivers but does this mean that with the 3D drivers I'm using now I can't have hardware accelerated 3D?

Thanks for the help by the way.

---

### Post by bluevoodoo1 on 2006-03-17
Hmmm, that's a huge change for the worse! Definitely not normal. There could be an option in your xorg.conf to change to fix it? I don't know. Might want to post over at the thread I mentioned. You'll probably get more attention there. Plus, I was an ATI guy, now I'm a nvidia guy :) (my ATI hardware was never good enough for 3D anyway), so I'm out of ideas.

---

### Post by Strike&gt;&gt; on 2006-03-17
hello

i have the same card as you do. Kubuntu or anything graphical ran very slowly, so i installed the ati driver. however i installed it differently ,and it worked great for me. good quality movies, and games, and lots more.

Here are the instructions:
[http://ubuntuforums.org/showthread.php?t=134348](http://ubuntuforums.org/showthread.php?t=134348)

Ocxic did a great job of explaining it.

I had the same video issues, choppy and bad qulity but thanks to this forum i now watch videos in ubuntu.:-D 
[http://ubuntuforums.org/showthread.php?t=111181](http://ubuntuforums.org/showthread.php?t=111181)

hope this helps.

---

### Post by matts0344 on 2006-03-17
Well, I tried to to follow those instructions but when I get to 

sudo module-assistant build,install fglrx-kernel

I get an error about Linux header files.

I'm having such bad luck with these video drivers, I can't suspend to RAM and I don't have hardware acceleration. (Firefox easily uses 100% CPU when browsing some web pages).

I'm surprised more people don't have these problems, there must be something I can do.

Thanks for the help again guys.

---

### Post by matts0344 on 2006-03-18
OK! Problem is solved! \\:D/ 

Added this to my xorg.conf

Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"

As suggested in that thread and now my videos look normal AND I have hardware acceleration, now only if I could get suspend to RAM to work...but I'm satisfied with 1 problem solved for tonight :-D 

Thanks guys!

---

### Post by Strike&gt;&gt; on 2006-03-18
Oh man, the same things happened to me. 

I think i got the same error as you. I think i fixed it by simply installing the linux headers from Synaptic, just do a search for the linux or kernel headers. If they are missing, careful to get the ones for your machine. 
i am gonna install ubuntu breezy again, and see if i can get it working once more.

help that works.

---

