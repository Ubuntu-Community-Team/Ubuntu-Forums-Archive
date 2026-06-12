---
title: "Ubuntu Distros for 600mhz + 256mb ram desktop"
date: 2010-04-08
forum: General Help
---

### Post by joni8.10 on 2010-04-08
What would be the best ubuntu version to run well and fast on an old P3 600mhz + 256mb ram?

Currently I am running ubuntu 9.04 and it's very slow. Any suggestions?

---

### Post by uRock on 2010-04-08
Lubuntu uses the LXDE desktop environment and is very lightweigh.

Cheers,
Ronnie

---

### Post by -humanaut- on 2010-04-08
Linux Mint 8 Fluxbox edition might be the best way to go if you want to stay in the *buntu family

---

### Post by nothingspecial on 2010-04-08
There is also crunchbang and masonux.

Or ubuntu minimal and build up.

---

### Post by cascade9 on 2010-04-08
> **nothingspecial said:**
> There is also crunchbang and masonux.

Or ubuntu minimal and build up.

+1 to 'minimal and build up'. I'd use lxde or Xfce as the desktop (fluxbox should work OK as well)

---

### Post by ubunterooster on 2010-04-08
Lubuntu or U-lite

---

### Post by joni8.10 on 2010-04-08
Thanks everybody for the suggestions!

I was kinda hoping to stay with ubuntu, and maybe downgrade to version 5, 6, or 7.04. 

Does anyone know if ubuntu 7.04 would run well with what I have, which is 600mhz + 256mb ram?

---

### Post by nothingspecial on 2010-04-08
> **joni8.10 said:**
> Thanks everybody for the suggestions!

I was kinda hoping to stay with ubuntu, and maybe downgrade to version 5, 6, or 7.04. 

Does anyone know if ubuntu 7.04 would run well with what I have, which is 600mhz + 256mb ram?

Using an older version of Ubuntu will not help you.

Believe it or not, they actually try to improve performance with each release and, more importantly, you will not get security updates or bug fixes.

Don`t go down that road.

---

### Post by snowpine on 2010-04-08
Software can't magically turn slow hardware into fast hardware. :) That being said, I am partial to CrunchBang. Another good option is AntiX (though not based on Ubuntu, it is based on MEPIS, which is very similar). The fastest options have the least in common with Ubuntu: Puppy, SliTaz, TinyCore, etc.

I agree with NothingSpecial that you should not use older, unsupported Ubuntu releases.

---

### Post by nothingspecial on 2010-04-08
> **snowpine said:**
> : Puppy, .

+1 Puppy is wonderful .........


.......if your hardware is supported "out of the box" ..........


........ if your hardware is not, it`s a bit tricky if you don`t know what you are doing.

Wouldn`t hurt to give it a spin though.

---

### Post by joni8.10 on 2010-04-08
> **nothingspecial said:**
> Using an older version of Ubuntu will not help you.

Believe it or not, they actually try to improve performance with each release and, more importantly, you will not get security updates or bug fixes.

Don`t go down that road.

Well OK, but I have another HD that has ubuntu 6.10 on it and it seems to run very well on this computer when I've switched to it. I don't understand why 9.04 is using up so much memory and is so slow, especially if as you say it should be an improved performance from 6.10.

I was thinking of installing 7.04 because the system requirements state that it only needs 192mb ram memory to run well.

I dunno what to do.:roll:

I'd at least like to stay with Ubuntu because I've learned how to get tvtime working with it!:)

---

### Post by nothingspecial on 2010-04-08
The main point I was making was about security.

Linux endeavours to be rock solid. Developers find flaws in the code and sometimes crackers find ways around security implementations. Linux developers respond. Ubuntu includes those responses in it`s updates.

Older versions of Ubuntu cease to be updated. Therefore any security hole that has been exposed will not get fixed if you run an old (unsupported) version of Ubuntu.

Go with an upto date lightweight version.

---

### Post by -humanaut- on 2010-04-08
oh yeah, another distro that would probably work good on that hardware is Slitaz.

---

### Post by agnes on 2010-04-08
Since the Window Manager can slow down or speed up your system a lot many lightweight distro's  use JWM / ICEWM / LXDE / XFCE / OpenBox by default; but another lightweight choice (that seems to be rarely used) is the Enlightenment WM. But it looks better and more user-friendly then all of them... imho.

Two .deb using, Enlightenment-by-default distros, that are aimed at being lightweight:
- OpenGEU, 9.10 Ubuntu-based.  You could also download an older OpenGEU version if you'd want to, the one based on Ubuntu 8.04 (LTS) would then be the best, if you'd want to keep receiving Ubuntu (security) updates until March 2011.
- Elive, it is Debian-based. However you have to pay US $ 15 for a hard-drive install.

Other supposed-to-be-lightweight distros:
- wattOS (9.10 Ubuntu-based  with Openbox/LXDE)
- Wolvix (uses Xfce, based on slackware)
- Zenwalk (^ same)

Then there are the minimal ones, like Puppy, Damn Small Linux, etc. (they are already mentioned) - which will run the best on your hardware. 

A bit more 'heavy' but friendly Puppy is LightHouse Pup (Puppy + codecs, Gslapt package manager, more default programs, and choice of WM's).

If you use wireless the kernel version may be important to you (most Puppy's e.g. use 2.6 now, which is pretty old) but since you also run 6.10 happily  I guess that not the case.

---

### Post by joni8.10 on 2010-04-08
Thanks again everyone! I didn't realise there were so many choices it's kind of overwhelming!:shock:

One question for agnes: is OpenGEU 9.10 basically the same as Karmic Koala (ubuntu 9.10)?? 

If I want something more lightweight that will also work with tvtime :popcorn: (I know this might seem trivial but I can't live without it now!) would all of those suggestions above be OK?

---

### Post by agnes on 2010-04-08
Since openGEU (the latest) is based on Ubuntu 9.10 it will have the Ubuntu 9.10 repositories enabled by default, - all .debs for 9.10 should work fine anyway. By default they also provide some typical GNOME stuff like Synaptic, Brasero, Transmisson.

The developers say it's not the same as Ubuntu 9.10 with a different WM, the WM is better integrated; and they have less programs installed by default... for the rest I honestly don't know. For proof that is is faster, you could always try the LIVE CD. (It was faster for me but that's no proof)

But since OpenGEU is Debian/Ubuntu-based it also uses aptitude, so it may be the case that if you download quite a few (GNOME) apps, aptitude makes you download a lot of "recommended" and "suggested" dependencies and the system will hog or slow down as well - but you could use the --without-recommends, --without-suggests flags with "aptitude" to avoid downloading a lot of unneeded stuff.

Personally for your hardware I think for fast performance a really tiny-base distro would be the best - so actually nothing based on Ubuntu or Debian...


I don't know anything about TV cards and those programs and such, sorry.
On the Puppy forums there is a tvtime .pet package but it is always the question if they work for everyone, again, you could try it with the live cd ;)

---

### Post by joni8.10 on 2010-04-22
In case anyone is interested, I had a photo for my desktop background which I removed and replaced with a solid colour, and now my system memory has greatly improved! I may stick with ubuntu afterall!

Just one more question though. Can I use this lightweight lxde desktop environment with the system I currently have (ie ubuntu jaunty) just by installing it from synaptic, and will it work?

---

