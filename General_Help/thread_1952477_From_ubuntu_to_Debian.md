---
title: "From ubuntu to Debian"
date: 2012-04-04
forum: General Help
---

### Post by shad0w7 on 2012-04-04
Hello guys, I am removing ubuntu and installing debian. Ubuntu has become very heavy for my laptop. Will there be any main difference between the change? I mean for example commands like "sudo apt-get..." etc will still remain the same right? as they are part of linux?

---

### Post by squilookle on 2012-04-04
If things haven't changed too much since I used Debian, which was the last stable version, then the main difference was just that a lot of the automatic, hand holding type things like installing restricted drivers and codecs were not there. 

It uses the same packaging system, so you can still use apt-get (although that's a Debian thing rather than a Linux thing, other distributions like Fedora do work differently in that respect). 

Good luck.

---

### Post by shad0w7 on 2012-04-04
> **squilookle said:**
> If things haven't changed too much since I used Debian, which was the last stable version, then the main difference was just that a lot of the automatic, hand holding type things like installing restricted drivers and codecs were not there. 

It uses the same packaging system, so you can still use apt-get (although that's a Debian thing rather than a Linux thing, other distributions like Fedora do work differently in that respect). 

Good luck.

I have been doing some research and I found Lubuntu, to be a very light OS. Have you heard about it?

---

### Post by bobman321123 on 2012-04-04
I'm pretty sure Ubuntu is heavily based off Debian, so it wouldn't surprise me if your user experience is more or less the same. 
Sure the UI is different, Ubuntu has more features, but the basic system should be quite similar.

---

### Post by zombifier25 on 2012-04-04
> **shad0w7 said:**
> I have been doing some research and I found  Lubuntu, to be a very light OS. Have you heard about it?
I bet everyone here has heard about it :)
If you computer can't handle Ubuntu, then Lubuntu is the way for you.

---

### Post by bobman321123 on 2012-04-04
> **shad0w7 said:**
> I have been doing some research and I found Lubuntu, to be a very light OS. Have you heard about it?

I'm running Lubuntu on my desktop, and it's very light weight, but wicked fast. It has a memory footprint of something like 100mb.

---

### Post by squilookle on 2012-04-04
[Ubuntu is based on Debian]("http://www.ubuntu.com/project/about-ubuntu/ubuntu-and-debian")

Whether you want to go to Debian or Lubuntu depends on what you need. 

Lubuntu uses the Ubuntu base, meaning the respositories, commands, release schedule etc are the same, but the desktop is LXDE rather than Unity. 

If you want to stay within the Ubuntu family of distributions, want a low footprint and don't mind having less bells and whistles, then Lubuntu is your best bet. 

Debian will use a more fully featured desktop by default, but you will sacrifice the convenience of having things like automatic installation of wireless and graphics drivers, restricted codecs, etc. Not that these things are too difficult if you follow any instructions carefully. The experience otherwise shouldn't be too dissimilar. 

If you can, try both and see what you prefer, and what the footprint of each is like on your system.

---

### Post by lykwydchykyn on 2012-04-04
Lubuntu's good for slow computers.  Debian is too.

Biggest differences between Debian and Ubuntu that tend to trip people up:

 - Sudo isn't configured or installed by default on Debian.  Root is enabled instead.
 - No Jockey (drivers tool), no Unity, and other bits of "spit'n'polish" are not configured by default or missing entirely.  This is, of course, either good or bad depending on your needs.
 - The repositories are arranged differently.  Instead of Main, universe, restricted, and multiverse; they have main (kind of like Main and Universe combined), non-free (for non-FOSS software) and contrib (for FOSS that depends on non-free).  
- There are no PPA either; third party repos are scattered about the 'net.
- The install is the old, traditional "boot to an install wizard", rather than a LiveCD install like Ubuntu.

---

### Post by winh8r on 2012-04-04
As suggested already try Lubuntu and see how it goes for you .

If you are moving to Debian , I would suggest trying something like 

Crunchbang Linux, which is based on Debian, is very lightweight and fast 

and has a bit more of a user friendly environment than pure Debian.


[https://help.ubuntu.com/community/Lubuntu/GetLubuntu]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu")



[http://crunchbanglinux.org/]("http://crunchbanglinux.org/")


hope this helps you.

---

### Post by codemaniac on 2012-04-04
There are avalanche of lightweight linux distos out here to try upon .
[www.distrowatch.com](www.distrowatch.com)
[http://www.webdeveloperjuice.com/2011/08/12/7-outstanding-lightweight-linux-distributions/](http://www.webdeveloperjuice.com/2011/08/12/7-outstanding-lightweight-linux-distributions/)

---

### Post by QIII on 2012-04-04
apt is not a Linux-wide thing.  It belongs to a class of distros that use that construct.  Fedora, CentOS and that family use yum.  OpenSUSE uses zypper.  Just a point of clarification

But yes, Debian uses apt, as do many distros, like Ubuntu, that are originally derived from it.

Be prepared to use the terminal more, at least to begin with and get set up.  You can build things to where you have more GUI tools.

Just be aware that if you heap too much on Debian, you'll be back around to the same place -- heavy and slow.

---

### Post by malspa on 2012-04-04
> **shad0w7 said:**
> Will there be any main difference between the change? I mean for example commands like "sudo apt-get..." etc will still remain the same right? as they are part of linux?

lykwydchykyn nailed it, especially with regards to using su instead of sudo. Otherwise, commands are basically the same:

> **lykwydchykyn said:**
> Lubuntu's good for slow computers.  Debian is too.

Biggest differences between Debian and Ubuntu that tend to trip people up:

 - Sudo isn't configured or installed by default on Debian.  Root is enabled instead.
 - No Jockey (drivers tool), no Unity, and other bits of "spit'n'polish" are not configured by default or missing entirely.  This is, of course, either good or bad depending on your needs.
 - The repositories are arranged differently.  Instead of Main, universe, restricted, and multiverse; they have main (kind of like Main and Universe combined), non-free (for non-FOSS software) and contrib (for FOSS that depends on non-free).  
- There are no PPA either; third party repos are scattered about the 'net.
- The install is the old, traditional "boot to an install wizard", rather than a LiveCD install like Ubuntu.

There are lots of other options if you want a lighter system, some which have already been mentioned. Stay within the Ubuntu "family," or go straight Debian, or pick another distro (SalineOS comes to mind -- uses Xfce, based on Debian)? 

Debian does take a little more work to get installed and set up, but after that it's about as trouble-free as things get in the Linux world (specifically, Debian Stable).

---

