---
title: "conflict between audacity and hydrogen"
date: 2011-08-08
forum: General Help
---

### Post by john.errington on 2011-08-08
I'm running Ubuntu 11.04 on an HP compaq nc6220 with 1G RAM.  It has  "Integrated 16-bit Sound Blaster Pro compatible audio"
I'm using the Hydrogen drum machine to generate a beat thru speakers, then trying to record my accompaniment with Audacity, using the internal microphone. (all current versions)
However Audacity stops recording when Hydrogen generates a beat.
Otherwise the system works - for example I can record using Audacity on another PC - but I want a portable system.
Does anyone have any ideas or suggestions?

---

### Post by CatKiller on 2011-08-08
Import your Hydrogen song into Rosegarden and use that or set up JACK.

---

### Post by john.errington on 2011-08-09
Thanks CatKiller - I'm an UBUNTU newbie having used Windows since it was just slits for arrows. Since reading your reply (thanks) I've read up about JACK and it talks about needing a different kernel, and all kinds of setup.
[http://ubuntuforums.org/showthread.php?t=788600](http://ubuntuforums.org/showthread.php?t=788600)

However I'm using ubuntu 11.04 as downloaded from [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)  - exactly "as is" except for getting rid of the unity interface.

Can I just get JACK with ubuntu software manager and run it?

If I need a new kernel which one and how do I get it?  The cpu is a single core pentium M and all 32 bit.

---

### Post by CatKiller on 2011-08-09
> **john.errington said:**
> Can I just get JACK with ubuntu software manager and run it?

Pretty much. QJackctl is the easiest way to start the JACK server.

There was a time when the realtime kernel project got much better results than mainline. It didn't last long; the improvements got merged into the generic kernel & the project pretty much disbanded. You don't need to worry about it.

Last time I looked, the Ubuntu Studio website had some useful information about Audio and Ubuntu.

---

### Post by john.errington on 2011-08-14
Nope, I'm now using JACK and while Hydrogen generates beats and Audacity records, when I come to play back (with Hydrogen stopped) there is a problem with the recorded track (about 3 min) and it wont play - even when saved as an MP3 - for more than a fraction of a second!

---

### Post by CatKiller on 2011-08-14
You need to set Audacity's output to either JACK or auto-detect.

---

### Post by john.errington on 2011-08-15
I went through all the Audacity settings - no JACK option.  Lost my rag and uninstalled Audacity thinking I'd try an earlier version.  Finally reinstalled it and a JACK option appeared!  Perhaps Jack needs to be installed first.  Anyway now I can play a drum tune and record at the same time.  Many thanks for your patience and help CatKiller.

:)

May I ask - for newbies is there a simple explanation of how the sound hardware relates with ALSA, JACK and other apps like hydrogen and audacity?

---

### Post by CatKiller on 2011-08-15
A simple answer? No.

 [http://ubuntuforums.org/showpost.php?p=11041035&postcount=9](http://ubuntuforums.org/showpost.php?p=11041035&postcount=9)

---

