---
title: "Screen Recording?"
date: 2010-06-02
forum: General Help
---

### Post by Jake007g on 2010-06-02
I've been using Linux for a good six months now, and I'm loving it.

I've recently upgraded from Ubuntu 9.10 to Ubuntu 10.04. When I was using 9.10, I couldn't use ANY screen recording software (Trust me, I tried a lot), as it made my desktop 'lag' so much but I just thought it was a problem with my OS, because when I was running Windows Seven I could record my desktop perfectly in HD, whilst running a lot of other applications. 

My computer isn't exactly amazing spec, got a dual core 2.20ghz processor, and 256mb ATi Raedon graphic card. 

Since recently upgrading to 10.04, I still can't record my desktop due to 'lag'. 

Will this be a problem with my hardware? Is my computer just not powerful enough to record my desktop on Ubuntu? Or is another problem which I haven't even thought about?

Any help will greatly be appreciated.

-Jake

---

### Post by thebigob on 2010-06-02
I use gtk-recordmydesktop with a laptop that has much worse spec that yours and it works fine. Not sure if you have tried this already but if not:

```

sudo apt-get install gtk-recordmydesktop

```

---

### Post by Jake007g on 2010-06-02
Thanks, but I've already tried that program and it lags my desktop :\

---

### Post by Locke_99GS on 2010-06-02
Configure it (the screen-capture tool) to be more CPU friendly, and try renicing it.

I'm using an old 3.2GHz Celeron (single core) and I grab screen recordings with (gtk-)recordmydesktop without issue. 

BTW Youtube hates Theora 1.1 from Lucid.

---

### Post by Jake007g on 2010-06-02
Thanks for the reply, I've lowered all the 'Advanced Settings' and also disabled some of the features that sound like they use more CPU (Encoding on the fly etc) but it still lags :(

EDIT: I've also opened up .gtkrecordmydesktop (Home Folder) with gedit and lowered / disabled even more functions, still lags :/

---

### Post by dragos240 on 2010-06-02
Hi,

How did you install your system?

1) Boot from the CD, and partition drives.
2) Boot from the CD, and wipe everything.
3) Install within windows.

If it's the third one, that's your issue right there. I had an old laptop a while back. 1gb of ram, it lagged with everything, it just lagged like heck. Screen recording was very very slow. I later partitioned it, it went much faster. I don't know if WUBI has changed since then, but if you chose the third option I think you better look into partitioning.

---

### Post by Jake007g on 2010-06-02
> **dragos240 said:**
> Hi,

How did you install your system?

1) Boot from the CD, and partition drives.
2) Boot from the CD, and wipe everything.
3) Install within windows.

If it's the third one, that's your issue right there. I had an old laptop a while back. 1gb of ram, it lagged with everything, it just lagged like heck. Screen recording was very very slow. I later partitioned it, it went much faster. I don't know if WUBI has changed since then, but if you chose the third option I think you better look into partitioning.

Formatted my C:/ (280gb) and installed a fresh install, I then restored the files I backed up onto my 1tb Ext.HDD into my Ubuntu directories (Music, Video edits and general Documents, no programs or anything), not sure if that affects my speed though

---

### Post by ThesaurusRex on 2010-06-02
Have you tried Wink? It's relatively lightweight and very easy to use. I use it at work all the time.

---

### Post by Jake007g on 2010-06-02
> **ThesaurusRex said:**
> Have you tried Wink? It's relatively lightweight and very easy to use. I use it at work all the time.

No, I haven't tried Wink, I've just searched for it in the Ubuntu Software Centre and in the Synaptic Package Manager and couldn't find it :S

---

### Post by ThesaurusRex on 2010-06-02
> **Jake007g said:**
> No, I haven't tried Wink, I've just searched for it in the Ubuntu Software Centre and in the Synaptic Package Manager and couldn't find it :S

That's unfortunate. You can download the tarball from their website, if you'd like. I just tried it, and it's not necessarily simple, but isn't that why we're Linux users? Because we like the challenge?

Anyway, just a suggestion.

---

### Post by Jake007g on 2010-06-02
All right, thanks for the help, I'll give it a shot, I'll double post when I've finished :)

---

### Post by inameiname on 2010-06-02
Wink sounds pretty cool. I may check it out myself, as recordtomydesktop lags more than I'd like for me.

It seems 'wink' was taken out of the official repos after Jaunty. However, you can get download the deb file for it directly with any one of the links on this site:

[http://packages.ubuntu.com/jaunty/i386/wink/download](http://packages.ubuntu.com/jaunty/i386/wink/download)

Unfortunately, some of the dependencies for it seem to not be available when you hit install, so I guess we're left with having to install the tar file.

---

### Post by Jake007g on 2010-06-02
Sorry if I'm annoying you guys now, but as I've come to install wink, I've gotten this error:

> 
Error: Dependency is not satisfiable: libstdc++5(>=1:3.3.4-1)


EDIT: I'll give the tarball a shot.

---

### Post by sedawk on 2010-06-02
If you are using the open source driver for the radeon graphics
card try to use the one from ATI instead (if there is
one already available for 10.4).

What you can also try to do is to reduce the screen resolution
and see if that helps. 

In general you can monitor cpu usage with command line tool top.
But I wouldn't start it on the desktop you are capturing - too
many updates might additionally slow down capturing.
If you have two computers you can try to ssh into
your computer and run top from the second computer, so the
data is not shown on the screen you try to capture.

---

### Post by Jake007g on 2010-06-02
Wink doesn't work, anybody got another solution? :(

---

### Post by Bonster on 2010-06-02
u can use ffmpeg to do ur screencasting, thats what i use

---

### Post by inameiname on 2010-06-03
Do you know a good terminal command to use ffmpeg for that?

---

### Post by Bonster on 2010-06-03
> **inameiname said:**
> Do you know a good terminal command to use ffmpeg for that?


This is what im using

> ffmpeg -f alsa -ac 2 -i hw:0,0 -f x11grab -r 30 -s 1680x1050+0+0 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 -y output.mkv

then press q to stop

---

### Post by inameiname on 2010-06-03
Why thanks. :) It works just fine. I only had to change the resolution.

I also found this handy little script to convert mkv to avi which works just fine:

[http://www.larsen-b.com/Article/261.html](http://www.larsen-b.com/Article/261.html)

Update:

I make this into a script real quick, adding to have it run in terminal and that way I can put it in my nautilus-scripts. Figured I'd share:

#!/bin/sh

tty -s; if [ $? -ne 0 ]; then gnome-terminal -e "$0"; exit; fi
ffmpeg -f alsa -ac 2 -i hw:0,0 -f x11grab -r 30 -s 1680x1050+0+0 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 -y output.mkv

Just remember to change the resolution (1680x1050) if desired.

I also added the mkv2avi script in there as well, so it's very easy to convert if need be.

---

### Post by hugmenot on 2010-06-03
This is a nice script that wraps ffmpeg screen recording:
[http://github.com/lolilolicon/ffcast](http://github.com/lolilolicon/ffcast)

The included xrectsel provides a little utility to make a rectangular selection.

---

### Post by FakeOutdoorsman on 2010-06-03
I'm surprised that nobody has mentioned:

[HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?t=1392026)

It's a well written and informative guide showing how to use FFmpeg to record your screen.

---

### Post by Jake007g on 2010-06-03
Even using FFmpeg to record my desktop lags it up completely, which is strange, because when I use FFmpeg to deinterlace four videos at once, my computer doesn't lag at all. I think one guy who replied here (Can't remember your name sorry) hit the nail on the head by suggesting that it is probably my GFX Card drivers. I shall investigate into installing some official ATi drivers instead of the open source ones, and see if that solves my problem. 

PS, thank you very much to the people who have replied and tried helping me, it's the main reason why I love Linux, everybody is willing to help everybody else <3

---

### Post by cadcam on 2010-09-28
dude, just grab the c++5 dist from 

[http://packages.ubuntu.com/jaunty/i386/libstdc++5/download](http://packages.ubuntu.com/jaunty/i386/libstdc++5/download)

and install it on your system.  i had the same error, and fixed it this way.  lucid comes with c++6 , but it doesn't mean you can't install the 5 dist from the site.

hope it helps,
A.

---

