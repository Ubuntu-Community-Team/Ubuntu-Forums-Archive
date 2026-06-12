---
title: "Apt-get update not working..."
date: 2009-10-05
forum: General Help
---

### Post by dopefish7590 on 2009-10-05
Hey all... I've had Ubuntu installed on one of my computers for quite a long time, and recently I can't seem to update any of my packages, or when I try to install a new one, it installs a previous version. (Like it installs GIMP 2.4 when I try to get the latest version). I try to apt-get update, but apt doesn't find any updates... I'm pretty sure it's because I'm still on Hardy Heron, and that it doesn't officially have updated repos any more, so if this is the case, how does one update where apt searches for repos? If this isn't what's wrong, then, does anyone have any suggestions on what the problem could be?

Thanks!

---

### Post by MelDJ on 2009-10-05
i dont know how to solve the problem. but maybe you could install the .deb packages for now

---

### Post by del_diablo on 2009-10-05
Oh, that problem. Under some settings under synaptics: Make sure it goes for "highest version" on package upgrade, i think its set to "native repos" when updating.

---

### Post by dopefish7590 on 2009-10-05
> **del_diablo said:**
> Oh, that problem. Under some settings under synaptics: Make sure it goes for "highest version" on package upgrade, i think its set to "native repos" when updating.

It's actually already set to that. :\
Any other thoughts?

---

### Post by 3rdalbum on 2009-10-05
Let's say you were a system administrator in charge of 50 computers running Hardy, and the users aren't computer whizzes.

One night, you run the usual Ubuntu updates. The next morning, you get thirty support calls from people complaining that their important program now has a different interface and that they can't find a particular function. In the afternoon, you get another twenty-five support calls complaining that there's now a bug in some software that wasn't there yesterday.

That's why software in the repositories does not get any updates except for uninvasive bugfixes. Any new software release that adds new features will not make it to an existing Ubuntu release.

Hardy is getting a bit long-in-the-tooth for new versions of software; you might be able to find a PPA with the new software you need, but probably not. You might be able to compile the source code for the new versions of software, but this might require you to compile new versions of lots of libraries.

Try compiling from source. If that's too difficult (i.e. requires libraries that are newer than what's available in the Hardy repositories) then you should upgrade to Intrepid, Jaunty or Karmic (when it comes out).

---

### Post by dopefish7590 on 2009-10-05
That's what I was hoping I wouldn't have to do since it would require me to either wipe my hdd or back it up... Ah well, guess it was worth a try. :\

---

