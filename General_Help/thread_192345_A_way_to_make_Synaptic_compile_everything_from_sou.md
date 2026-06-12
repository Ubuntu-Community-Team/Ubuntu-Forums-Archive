---
title: "A way to make Synaptic compile everything from source?"
date: 2006-06-08
forum: General Help
---

### Post by DDM on 2006-06-08
Alright, this is mostly for curiosity's sake, but I'm wondering if there is any way to force apt-get and synaptic to build every package from source. I realize that apt-get can do this pretty easily on individual packages, but adding this feature to synaptic would be pretty cool. Maybe a script could download and compile everything in dpkg, so the next day you'll be all set.

I'm asking this because I was considering loading a new distro onto one of my partitions and I realized that the only distros people are excited about are Gentoo and Ubuntu. And why do people use Gentoo? Most of them want those processor optimizations that account for a miniscule 2% speed increase or something. I'd like to see something similar for Ubuntu so you can tell Gentoo people "Hey, you can load nano 3 milliseconds quicker in Ubuntu too and you don't have to deal with the 'Science Project' aspect of Gentoo." And yes, I realize the repurcussions of compiling everything, especially the huge number of dependencies that would be needed, but it'd be interesting at least.

Just my 2 cents

---

### Post by xXx 0wn3d xXx on 2006-06-08
Well I highly doubt that your would notice any difference but try:
> sudo apt-get source program -b
Replace program with what you want to install. I don't know a way to force synaptic to use this method. Check out some options.

---

### Post by DDM on 2006-06-08
This theoretical program isn't really for myself, it's more of a way to get more people to use Ubuntu. If anyone has any tips on building a Bash script to get this going, I could ty to put something together. However, my programming skills are weak at best.

---

### Post by xXx 0wn3d xXx on 2006-06-08
[QUOTE=DDM]This theoretical program isn't really for myself, it's more of a way to get more people to use Ubuntu. If anyone has any tips on building a Bash script to get this going, I could ty to put something together. However, my programming skills are weak at best.[/QUOTE]
Well my programming skills are horrible so I couldn't help with much. Sorry :(

---

### Post by garyng on 2006-06-08
I don't think that is the philosophy of debian(and ubuntu), if anyone is interested in compiling everything locally, either gentoo or LFS are the right distro to choose. There is no way a distro can be all things to all people.

---

### Post by nix4me on 2006-06-08
Agreed.  Gentoo is awesome beacuse of the speed.  Ubuntu is awesome for different reasons.

I like them both, and I run them both on seperate machines.

nix4me

---

### Post by Shay Stephens on 2006-06-08
I use an OS for me and getting my work done.  I don't care about what other uber geeks think about it ;)

---

### Post by DDM on 2006-06-08
Yeah I guess I'm with you guys on this, I figured it might be effective "marketing" or whatever you wanna call it. Personally, Ubuntu is fast enough for me, and a 24 hour plus compile job isn't worth it. Then again, I also use Ubuntu on a slow 650mhz PIII, as well as my 2.4Ghz machine, and my laptop could use a little help.

---

### Post by 23meg on 2006-06-09
Check out apt-build.

---

### Post by daemoth on 2006-06-09
I actually know several people who run gentoo (I run it myself on my desktop), and none do it for speed reasons.  Most I know do it because it allows a fairly stripped down environment from which to build on and is easy for them to maintain.  In addition, the gentoo forums are fantastic.    Different strokes for different folks, that is the beauty of linux.

---

### Post by DougC on 2006-06-09
I've got a tripple boot system.
ms windows for games, ubuntu for most other things and gentoo just for messing around with.
I keep the gentoo partitions mounted under ubuntu so I can rebuild to my hearts  content.

Bit sad, but hey. :)

---

### Post by dresnu on 2006-06-09
For those interested on this topic check out this how-to: [http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html)

---

### Post by daemoth on 2006-06-09
[QUOTE=DougC]I've got a tripple boot system.
ms windows for games, ubuntu for most other things and gentoo just for messing around with.
I keep the gentoo partitions mounted under ubuntu so I can rebuild to my hearts  content.

Bit sad, but hey. :)[/QUOTE]

Well, I've never had a triple boot system, but I have been running a laptop with ubuntu and windows dual booted and a desktop with gentoo and windows dual booted.  Right now I'm just down to windows on the laptop and gentoo on the desktop.

---

