---
title: "Ubuntu hard freezes on IBM X31, only solution is to shutdown. Please help!"
date: 2006-06-05
forum: General Help
---

### Post by touser on 2006-06-05
Hello everyone, i have ubuntu 6.06 running on my ibm X31 and i have been very pleased with it so far, everything just works. Except for one thing, it tends to completely lock up at random occasions for no apparant reason and i cant switch to another console or anything. The only solution is to hold the power button down and turn it off. If anyone has any ideas as to where i should look to see what the culprit is i would really appreciate any help! The last time it locked up was when i started firefox if that means anything...

---

### Post by Quirky on 2006-06-05
Same things happen here, but on completely different hardware (Fujitsu Amilo). Breezy worked perfectly, upgraded and I get freezes every 30mins-1hour.

There are a few bug reports in launchpad that suggest it may be the ati video driver. Do you have an ATI video card? I've turned off dri here to see if it helps, since that has been mentioned as a freeze causer.

[https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bugs](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bugs)

---

### Post by touser on 2006-06-05
Thanks for the reply quirky, yes my laptop does have an ati graphics card. So your saying commenting out the dri line in xorg.conf may help? Thanks!

---

### Post by Quirky on 2006-06-05
No! It's just frozen twice on me here with DRI removed :-( This is getting silly. I'm seriously tempted to reinstall Breezy, which had none of these problems.

---

### Post by touser on 2006-06-05
ouch, thats bad news. I just dissabled dri so i guess i'll see what happens. Luckily i still have windows on the laptop so if it keeps having problems i can always fall back to it for the time being..

---

### Post by Quirky on 2006-06-06
An update: I've removed ndiswrapper - now that the ralink rt2500 driver works with the SMP kernel - and I haven't had as much trouble. uptime is *gasp* 1:20. Almost as good as Windows ;-)

---

### Post by touser on 2006-06-06
glad to hear its running a little more stable, let me know if that fixes the problem ..

---

### Post by touser on 2006-06-08
Well, commenting out dri hasent solved anything, it just hard locked up several times last night while using VLC video player..

---

### Post by viciouslime on 2006-06-14
I have the same problem, anyone else got any ideas?

---

### Post by kevlarman on 2006-06-15
i have the same issue on a pentium 3 (video card is nvidia) with both dapper and breezy. my solution (which i am not very happy about) was to switch to the vesa driver:(. i have no idea how, but both nv and nvidia were causing the same problem

---

### Post by viz_e on 2006-06-23
There are a lot of people complaining about dapper freezes. They seems to be Xorg related...

I am still waiting for a fix...

---

### Post by viciouslime on 2006-06-24
I also get strange artifacts on buttons in dialogue boxes. I will upload a picture when i am back on the laptop.

EDIT: just found this bug [https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/34435]("https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/34435")

This is what i am experiencing, guess I will just have to wait for a fix now.

---

### Post by touser on 2006-07-01
Well, i'm still having the same problem, it will just randomly hard freeze and the only thing i can do is turn the computer off. It seems to happen mostly when using firefox and is totally random, it can sometimes go for hours or even days, or sometimes just minutes.. all i know is that i am forced to use windows at the moment because of it :(

---

### Post by begkev5 on 2006-07-10
Hi,

I had the same problem with my X31. I tried some of the suggestions with no luck. Finally, I was able to fix it by simply updating the BIOS and Embedded Controller Program.  :D 

So, make sure your fan IS turning ON. If it isn't you can download the updates from Lenovo or IBM.

---

### Post by Haylwood on 2006-07-28
I'm getting the same problem.  Different architecture, but I *am* using ATI video card.  I'm checking out the links posted by others now ... last time it froze was during an update so maybe there's a fix for it there?  :confused:

EDIT:

Oh and I also get the strange artifacts while scrolling some windows.  Also, the freezing seems to happen more when there are either a lot of windows being displayed or a 3D accelerated screensaver is running..... its got to be a a graphics driver issue.

---

### Post by AgenT on 2006-10-11
All of this seems fixed in Edgy. No more freezes, no more artifacts. There are bug reports on both of these issues in launchpad. Whether or not it will be backported to Dapper is unknown. It may already have been - no one has responded to this thread in a while.

---

### Post by Tyltyl on 2006-10-11
Since when I upgraded to Edgy I froze twice right after installing. Went back to Dapper, with all the freezes but at least they are less frequent.
The only thing I know is that I never had this problem with Breezy.

---

### Post by AgenT on 2006-10-11
> **Tyltyl said:**
> Since when I upgraded to Edgy I froze twice right after installing. Went back to Dapper, with all the freezes but at least they are less frequent.
The only thing I know is that I never had this problem with Breezy.

When did you upgrade to Edgy? The patch in Edgy was released only a few days ago: Oct 5th, 2006 [[see bug on launchpad]("https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-ati/+bug/16873")] - although officially it may have been added to the repos a day or two later due to a problem. 

Before this time Edgy froze just like Dapper. It was a driver memory problem. Basically, the driver told your computer that your video card had more memory than it really had - so when Xorg, GNOME, or another application tried using memory that did not physically exist, it crashed your whole memory access (which hard locked your computer). Your computer froze right away because it was probably configuring or doing intense graphic processing after install that triggered the memory bug.

---

### Post by viciouslime on 2006-10-11
Ahhhhh so that's what was doing it. I have noticed it no longer occurs in edgy but i didn't know a specific fix had been released.

Thanks for taking the time to explain. :)

---

### Post by drezha on 2006-10-11
Is this the same kind of problem I'm getting in this topic?

[http://ubuntuforums.org/showthread.php?t=275444](http://ubuntuforums.org/showthread.php?t=275444)

Maybe if I disabled the nVidia drivers?

---

### Post by AgenT on 2006-10-11
> **drezha said:**
> Is this the same kind of problem I'm getting in this topic?

[http://ubuntuforums.org/showthread.php?t=275444](http://ubuntuforums.org/showthread.php?t=275444)

Maybe if I disabled the nVidia drivers?
You are not suffering from the SAME bug, that's for sure. The bug mentioned above was only for certain ATI graphic adapters.

As this is a thread on ATI (in the x31 Thinkpad in particular), your question will NOT be answered in this topic. Please look for an answer shortly in the topic you created.

---

### Post by 25an on 2006-10-15
Hi! 
i had the same problem on Dapper but i found a solution to it when searching for fglrx problems.
What i did was to edit in /etc/X11/xorg.conf file
comment the Load "extmod" and see if it helps.

Section "Module"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
#       Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

---

