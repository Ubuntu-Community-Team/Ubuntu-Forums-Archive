---
title: "Sound choppy on Wow with wine under 9.10"
date: 2009-11-14
forum: General Help
---

### Post by ed-koala on 2009-11-14
Got a couple of small issues that I'd like to iron out.  Playing Wow under wine has choppy sound in 9.10.  Can anyone recommend settings to improve this that also allow other programs to play sound also?

I'll worry about getting vent to work later...trying the new Mangler, hope it works well so we can kick Ventrilo to the curb!

---

### Post by Sin@Sin-Sacrifice on 2009-11-14
Setting wine to only use oss in winecfg worked for me. I would get the choppy sound for about 30 sec then silence with alsa enabled. Now everything is spectacular.

---

### Post by ed-koala on 2009-11-14
yeah, it works, but I can't hear anything else (other programs) that way, can I?

9.10 also changed sound stuff around, now I can't find how to make my front mic work right with my new vent program ... sigh, I'm sure I'll find the answer eventually, as I did with Vent in 9.04

---

### Post by Sin@Sin-Sacrifice on 2009-11-14
Yeah... this is a problem for me when I want to listen to Rhythmbox while playing a game. I just don't... [http://ubuntuforums.org/showthread.php?t=254286](http://ubuntuforums.org/showthread.php?t=254286) may help you though.

---

### Post by Sin@Sin-Sacrifice on 2009-11-14
I found this [http://ubuntuforums.org/showthread.php?t=874824&page=2](http://ubuntuforums.org/showthread.php?t=874824&page=2) and [https://bugs.launchpad.net/ubuntu/+source/wine/+bug/371897](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/371897)

Hope there's something there for you.

---

### Post by ekilfoil on 2009-11-15
You should uninstall the default Ubuntu Wine packages and install from this PPA.  This will give WINE native PulseAudio support.

[https://launchpad.net/~neil-aldur/+archive/ppa](https://launchpad.net/~neil-aldur/+archive/ppa)

For a more detailed explanation of why, visit [http://www.mangler.org/forums/?vasthtmlaction=viewtopic&t=5.0](http://www.mangler.org/forums/?vasthtmlaction=viewtopic&t=5.0)

---

### Post by ed-koala on 2009-11-15
Will definately try it.  Not sure how to get the packages tho. I added the ppa, but I don't see any wine package to install.  Just a wine 1.2 already installed.

---

### Post by ekilfoil on 2009-11-17
> **ed-koala said:**
> Will definately try it.  Not sure how to get the packages tho. I added the ppa, but I don't see any wine package to install.  Just a wine 1.2 already installed.

When I add that PPA to software sources, I get this version which says "winepulse"

That's what you need to look for.

---

### Post by dalen__ on 2009-11-24
I've created a guide on how to install winepulse in Ubuntu 9.10, hope it can help you.

[http://dalenscomputerblog.blogspot.com/2009/11/how-to-install-winepulse-for-ubuntu.html]("http://dalenscomputerblog.blogspot.com/2009/11/how-to-install-winepulse-for-ubuntu.html")

---

### Post by Norwal on 2009-12-31
Awesome!  Thanks Dalen_

---

