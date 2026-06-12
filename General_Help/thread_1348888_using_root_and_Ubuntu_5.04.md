---
title: "using root and Ubuntu 5.04"
date: 2009-12-07
forum: General Help
---

### Post by frankwakeman on 2009-12-07
As odd as it might sound to some, I've just put Ubuntu 5.04 on an old pc of mine which I've tried various distros on.  I pretty much bought the machine to use as a word processor, and the fact that this old version of Ubuntu plays dumb to my broadband dongle and is unbelievably smooth even with the onboard graphics instead of a card I bought is ideal for me.  The colour fringing problem with fonts seems to have begun as of 6.06, till 8.10, most noticeably with OpenOffice.org, so I'm not bothering with those.

But, I would like to add a couple of things if it's not going to be a hassle.

When I type alt F2 > gksu nautilus and try to dump some files in the file system, it doesn't accept my password like later versions have.  So when I tried to drop some Windows fonts in they were put in Home instead, which was no bother.  Can anyone who's been using Ubuntu this long clarify things for me?

I would also like to do the following:

1. Install some codecs offline, for mp3 and wma, and ideally for dvd playback.
2. Put the Ubuntu icon on the panel instead of the Gnome foot.
3. Add whatever files were used in 9.04 onwards that made the font rendering perfect, e.g. for lcd screens.

How are these three done?  As none of the other distros have achieved the good font rendering I'm hoping an Ubuntu follower will know where the magic files are.

Many thanks.

---

### Post by bodhi.zazen on 2009-12-07
Well, I do not think you can install anything unless you are willing to compile from source as I do not believe there are maintained repositories for 5.04.

I suggest a more up to date OS, puppy, DSL, SLAXX, Slackware even ...

---

### Post by synapsys on 2009-12-07
Use a recent version that is supported. Try Xubuntu for lower end hardware.

---

### Post by NoaHall on 2009-12-07
Don't use 5.04. That's silly.
Use DSL(Damn Small Linux) if it doesn't have much RAM, if it has enough, try out Mint.

---

### Post by frankwakeman on 2009-12-08
I have other computers for the snazzier stuff.  This old pc is just meant to be a word processor, with the possibility of playing some music while I write.

If I remember rightly, DSL and Puppy have some other more modest wordprocessing software.  I need my 'smart quotes' and .doc compatibility with good font rendering.  They're taking an age to get Abi Word finished.

I have put Windows 2000 on this machine now but I might try a Kubuntu 6 CD I've found while rummaging.

---

### Post by bodhi.zazen on 2009-12-08
Puppy has, IMO, better repositories then DSL and you can install OOO in puppy (Open office is available as  a dot pup)

[http://www.murga-linux.com/puppy/viewtopic.php?t=11802](http://www.murga-linux.com/puppy/viewtopic.php?t=11802)

---

### Post by slakkie on 2009-12-08
If you want lean and mean, try Debian, which is supported unlike your 5.04 install. Although I do applaud the effort to get it to work!

---

### Post by aysiu on 2009-12-08
> **synapsys said:**
> Use a recent version that is supported. Try Xubuntu for lower end hardware.

> **NoaHall said:**
> Don't use 5.04. That's silly.
Use DSL(Damn Small Linux) if it doesn't have much RAM, if it has enough, try out Mint. I agree with both of these statements.

Ubuntu 5.04 **no longer receives security updates**.

It is not a good choice. If you want to run on lower specs, you don't run an older version of Ubuntu. You run a lighter-weight window manager (IceWM, OpenBox, Fluxbox) instead of a heavier-weight desktop environment (KDE, Gnome, Xfce).

Here's a guide on how you can use the most recent version of Ubuntu to build a low-resource-using installation:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by sabre2th on 2009-12-08
Personally, I'm a firm believer in minimal installs.  There's a good thread in the forums (of course I can never find it when I need it) that gives a basic list of required packages to get you to a CLI.  After that, you just install whatever you want (ie. XFCE, Fluxbox, whatever) and you're off to the races.

I also know some people really like Crunchbang ([http://crunchbanglinux.org/](http://crunchbanglinux.org/)).  It's Ubuntu-based with Openbox as a WM.  I haven't tried it yet myself, but it is on my list to check out.  Might be worth a look.

Whatever you do, it's not really a great idea to run such an old, unsupported version.  The new ones can do everything that can do with very few exceptions.  They also can typically do it much, much easier.

---

