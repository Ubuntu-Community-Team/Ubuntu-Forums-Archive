---
title: "External storage for Ubuntu"
date: 2009-08-19
forum: General Help
---

### Post by Megamanic on 2009-08-19
I´m currently thinking about getting some external storage. Windows compatibility is not a consideration.

I like the sound of a NAS device but none of the boxes I´ve looked at claim Linux compatibility - although I believe (correct me if I´m wrong) that they actually run Linux.

Would a NAS be plug (into my router) & play?

If I got a NAS with a built in printer server would that feature ¨just work¨ for me?  Not that it´s a big deal but it would be nice.

I know that if I got a USB drive I could reasonably easily reformat it in EXT3/4but would be presumably slower as a NAS would run at network (100Mb) speed.

Does anybody have experience, war stories & better still recommendations of what I should buy & why?

Thanks in anticipation

Mike

---

### Post by Mighty_Joe on 2009-08-19
> **Megamanic said:**
> 
Would a NAS be plug (into my router) & play?


It *should* be.  If it makes the drives available via CIFS (Samba), NFS, heck, even SSH, you're good to go because Linux supports mounting drives via those protocols.  
Personally, I needed a little more functionality (web server, torrent client, NAS, SSH), so I got a [cheap, low power VIA mobo]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813153045") and a big hard drive, installed Ubuntu server and viola, an "[appliance]("http://blogs.zdnet.com/Ou/?p=275")" that does whatever I want for much less $ than a shrink-wrapped NAS.

---

### Post by Megamanic on 2009-08-19
> **Mighty_Joe said:**
> It *should* be.  If it makes the drives available via CIFS (Samba), NFS, heck, even SSH, you're good to go because Linux supports mounting drives via those protocols.  
Personally, I needed a little more functionality (web server, torrent client, NAS, SSH), so I got a [cheap, low power VIA mobo]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813153045") and a big hard drive, installed Ubuntu server and viola, an "[appliance]("http://blogs.zdnet.com/Ou/?p=275")" that does whatever I want for much less $ than a shrink-wrapped NAS.

Good suggestion - I like the sound of that

---

### Post by Mighty_Joe on 2009-08-19
> **Megamanic said:**
> Good suggestion - I like the sound of that

It's a fun ongoing project.  Since it's Ubuntu, everything in the repository is available (as opposed to something like [FreeNAS]("http://www.freenas.org/"), which is fast and tiny, but has a very specific purpose).   
One caveat: if you do choose that particular board, [I've heard]("http://ubuntuforums.org/showthread.php?t=1166037") problems with the video driver under Linux.  I run my system headless (no Xwindows) so it doesn't affect me.
There are new Atom-based boards around the same price. They will be as stingy with the electricity but probably have far more computing power than the ancient VIA C3.  I don't know if their video is better supported, but if you anticipate running Xwindows (running X programs remotely is always fun), it may be worth a look.

---

### Post by Megamanic on 2009-08-20
> **Mighty_Joe said:**
> It's a fun ongoing project.  Since it's Ubuntu, everything in the repository is available (as opposed to something like [FreeNAS]("http://www.freenas.org/"), which is fast and tiny, but has a very specific purpose).   
One caveat: if you do choose that particular board, [I've heard]("http://ubuntuforums.org/showthread.php?t=1166037") problems with the video driver under Linux.  I run my system headless (no Xwindows) so it doesn't affect me.
There are new Atom-based boards around the same price. They will be as stingy with the electricity but probably have far more computing power than the ancient VIA C3.  I don't know if their video is better supported, but if you anticipate running Xwindows (running X programs remotely is always fun), it may be worth a look.

Thanks, the whole project is very appealing to the nerd in me.  It also means I can do stuff like turn it into a PVR when the wife allows.  On the same track I have to make sure it's near silent in operation (I imagine I should be able to get a case that runs off a block style external power supply) and doesn't "look too ugly" according to She Who Must Be Obeyed's rather unpredictable aesthetic.  Wish me luck...

---

### Post by Mighty_Joe on 2009-08-21
> **Megamanic said:**
> . . .She Who Must Be Obeyed.. .

Hoo yea.  Got one of those myself.  She was overjoyed when I replaced my desktop "server" that sounded like a vacuum cleaner with the aforementioned appliance.  Two pointers:
I followed [this guy's lead]("http://smallandquiet.blogspot.com/2006/08/linux-on-wall.html") and replaced the CPU heatsink with a northbridge cooler (it's too small for a "real" cpu cooler).  Of course, there are fanless mobo/cpu combos available, but they tend to be underpowered or expensive.
I used a "real" power supply because I'm cheap and didn't want to invest more money or time (I did replace the fan in it with a quieter one). I plan to replace the PSU with a slow, quiet case fan and a [pico PSU]("http://www.mini-box.com/s.nl/it.A/id.417/.f?sc=8&category=13") (more efficient at low wattage than a "real" PSU).  My appliance does generate some heat and better safe than sorry.
[SilentPCReview]("http://www.silentpcreview.com/") has tons of info on making pc's quiet.  There's plenty of folks building MythTV boxes there.

---

