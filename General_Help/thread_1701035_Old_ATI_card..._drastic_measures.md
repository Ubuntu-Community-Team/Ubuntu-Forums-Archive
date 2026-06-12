---
title: "Old ATI card... drastic measures?"
date: 2011-03-05
forum: General Help
---

### Post by bcoffield on 2011-03-05
I hope someone can guide me on this one.

I've been using Ubuntu since 7.10 and have been updating regularly with each release until the last one (10.10) because I felt it didn't run well enough on my machine.  I've been wondering for a long time why my graphics performance has sucked, compiz has quit working etc.  I periodically would get fed up and mess with my drivers to no avail and it wasn't until recently that I stumbled upon the fact that my old ATI card stopped being supported after 8.10

SO... I feel a little ridiculous having put up w all of this for so long without knowing the reason behind it, but whatever.

Anyway, today I made a little partition and installed 8.10 on my machine and WOW is it running so much smoother.  I have compiz cranked up and its still great.  Amazing what some hardware acceleration will do for ya, eh?

ACTUAL QUESTION:  This sucks.  The repos are all unsupported etc...   What can I do to get this optimum graphical/general performance experience (directly tied to this 8.10 kernel version and ATI drivers) AND as much of the current repos and goodies from the latest and greatest releases.  I'm not aftraid of the command line but have no idea where to start or if this is a foolish quest...

Any guidance on my situation would be appreciated.  Thanks.

---

### Post by dcstar on 2011-03-06
> **bcoffield said:**
> I hope someone can guide me on this one.

I've been using Ubuntu since 7.10 and have been updating regularly with each release until the last one (10.10) because I felt it didn't run well enough on my machine.  I've been wondering for a long time why my graphics performance has sucked, compiz has quit working etc.  I periodically would get fed up and mess with my drivers to no avail and it wasn't until recently that I stumbled upon the fact that my old ATI card stopped being supported after 8.10

SO... I feel a little ridiculous having put up w all of this for so long without knowing the reason behind it, but whatever.

Anyway, today I made a little partition and installed 8.10 on my machine and WOW is it running so much smoother.  I have compiz cranked up and its still great.  Amazing what some hardware acceleration will do for ya, eh?

ACTUAL QUESTION:  This sucks.  The repos are all unsupported etc...   What can I do to get this optimum graphical/general performance experience (directly tied to this 8.10 kernel version and ATI drivers) AND as much of the current repos and goodies from the latest and greatest releases.  I'm not aftraid of the command line but have no idea where to start or if this is a foolish quest...

Any guidance on my situation would be appreciated.  Thanks.

You can't. All subsequent releases have dependencies that cannot be met by earlier releases.

Spend a few dollars on a supported graphics card.

---

### Post by bcoffield on 2011-03-06
I guess that I should have predicted someone would give me that answer...however that is not an option.  The system in question is a laptop and while I've upgraded the HD and ram over time the gpu isn't an option.


I don't really use all that many programs...  So, should I just update them and move forward?  Would not having ubuntu updates mainly just be a security issue?  Are there any other distros, or derivative distros (like Mint) that accommodate the older ATI cards while being a newer release?

---

### Post by bcoffield on 2011-03-06
Is it not an option to just add newer update sources to 8.10?

---

### Post by cascade9 on 2011-03-06
> **bcoffield said:**
> Is it not an option to just add newer update sources to 8.10?

No. 

You could try gallium3D with the open source ATI/AMD drivers, it should be better than just the opensource drivers.

---

### Post by bcoffield on 2011-03-06
Interesting... thanks.

Questions:  on wikipedia it says : As of 21 September 2010 (2010 -09-21)[update], There are two Gallium3D drivers for ATI hardware known as r300g and r600g for R100-R500 and R600-Evergreen GPUs respectively. Initial support for the Evergreen GPUs was added to the r600g driver on 2010-09-10.


My video card is listed as (using lspci command)
VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600


Does mine fall under those that gallium supports?  (like, is mine an "evergreen" gpu?")

---

### Post by cascade9 on 2011-03-06
Its not an 'evergreen' GPU, if it was you would have ATI/AMD drivers (evergreen = HD5XXX = currently supported by ATI/AMD closed source drivers). 

x600 = RV370, so it should use the r300g gallium version.  

The only ATI/AMD cards that aren't supported by gallium are the very old 'rage' chips. As to how good gallium is on your card, you would need to try them to find out.

---

### Post by bcoffield on 2011-03-07
Well I followed the instructions on this link:
[http://brainacle.com/how-to-easily-enable-r600g-gallium3d-in-ubuntu-and-ubuntu-derivatives-for-radeon.html](http://brainacle.com/how-to-easily-enable-r600g-gallium3d-in-ubuntu-and-ubuntu-derivatives-for-radeon.html)


And it was only after doing it that I re-read your post and saw that I should use the r300g driver... so maybe that discrepancy explains what I'm now seeing

using glxgears in 8.10 I get like 8000 frames 
in 10.04 before doing the gallium I was getting around 700
now I'm getting 300...

Can you please help me/point me to a page w directions to enabling the proper gallium driver?  Thank you!

---

### Post by bcoffield on 2011-03-10
Gallium3d did drastically improve my performance, though not up to actual 8.10 levels, though that wasn't expected.

followed the ubuntu specific instructions here

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

marking thread solved.  Thanks for the assistance!

---

### Post by lithopsian on 2011-03-10
Beyond a few hundred frames per second, glxgears tells you very little.  Try a comparison in an actual game.  Most probably there will be little difference.  Also check out things like large videos, desktop transparency effects, or Flash in your browser.  Some may be good, some not so good as they all use slightly different graphics capabilities.

---

