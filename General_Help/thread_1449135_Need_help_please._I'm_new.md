---
title: "Need help please. I'm new"
date: 2010-04-07
forum: General Help
---

### Post by Iviesaur on 2010-04-07
Ok my friend just got me started on lennox and i'm having two issues.

1st issue) I'm trying to compile the new Wesnoth but its asking for a cd rom drive when i type the sudo code. Me being on a netbook i don't have a cd drive. Is there anyway around that?

2nd issue) I have the Netbook remix lay out with the overlays but i'd like to to have the standard one my friends have. How would i go about that.

Any help would be most appreciated. Sorry if any of that sounds dumb. I hate being new at something X.x

---

### Post by Calash on 2010-04-07
Welcome to the forum :)

What instructions are you following to compile Wesnoth?  Also, and a more basic question, why are you compiling it instead of using the version in the Software Center?

If you have a reason that is fine, but many new people come to Linux thinking you have to compile to get anything installed, and this is far from the truth.

---

### Post by Iviesaur on 2010-04-07
Well i have to. If you go on to the Wesnoth home page. It tells you that you have to build it yourself. Or something along those lines

---

### Post by jrothwell97 on 2010-04-07
Welcome to Ubuntu L**i**nux! :P

[You don't need to compile a new version of Battle of Wesnoth](http://wiki.wesnoth.org/WesnothBinariesLinux#Ubuntu), you can install it automatically. You can use the Ubuntu Software Centre (Applications menu) to install it: just enter "Wesnoth" in the search box, and it'll appear in the list. You can install most software like this, and it's convenient because it's automatically kept up-to-date. Most of the time, ***you do not need to build software yourself*** - usually, you don't even have to download anything straight from the program's website.

I'm not sure it's possible to easily switch to the standard, non-netbook desktop if you're using Ubuntu 9.10 (Karmic Koala, or Karmic for short.) It used to be possible to do it automatically, but I believe that was unstable and it was temporarily withdrawn during the Karmic cycle.

You can do it manually - you can probably find instructions on the 'net by Googling, but IIRC it basically entails uninstalling a certain group of "packages" (the software components that make up the system) and then rearranging the panels. I'll see if I can find some more exhaustive instructions when I have the time.

Hope this helps!

---

### Post by Iviesaur on 2010-04-07
Actually Wesnoth doesn't update in the Ubuntu Software Center. My friend says i have to compile Wesnoth 1.8 from source since it was just released and there is no .deb available for the new version. My friend did this with no issue from a desktop. I am running a netbook with Ubuntu Netbook Remix

I am trying to run sudo apt-get build-dep wesnoth and I am getting the following error:
Do you want to continue [Y/n]? Y
Media change: please insert the disc labeled
 'Ubuntu-Netbook-Remix 9.10 _Karmic Koala_ - Release i386 (20091028.4)'
in the drive '/cdrom/' and press enter

My netbook does not have a CDrom drive. How do I proceed?

---

### Post by jrothwell97 on 2010-04-07
It does update, you just need to give them time to compile it and package it at their end.

On the other hand, if you *do* want to compile from source, what's happening here is that you appear to have your installation media selected as an apt repository. Try this: go to System/Administration/Software Sources, enter your password if prompted, and deselect the "installation CD" entry in the bottom of the Ubuntu Software tab. You should be asked to update your package data on closing: do this, and then try again.

---

### Post by mick222 on 2010-04-07
Here's a guide to compiling Wesnoth looks pretty straight forward but I would recommend using the package in the repositories until you are a little more familiar with Ubuntu. 
> [http://gwos.org/doku.php/guides:64bit:battle_for_wesnoth](http://gwos.org/doku.php/guides:64bit:battle_for_wesnoth)

---

