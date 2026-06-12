---
title: "simplify upgrades"
date: 2012-03-22
forum: General Help
---

### Post by jpaulb on 2012-03-22
The new 12.04 is coming soon. I usually do a new install, which is real time consuming reinstalling the various packages I use.

Is there anyway to simplify this? Is there a list of what is already installed on the box that could be transfered to a new installation?

---

### Post by snowpine on 2012-03-22
Have you seen these instructions?

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

It will be just one mouse click to upgrade to 12.04 next month, it really couldn't be any easier in my opinion. :)

---

### Post by jpaulb on 2012-03-22
> **snowpine said:**
> Have you seen these instructions?

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

It will be just one mouse click to upgrade to 12.04 next month, it really couldn't be any easier in my opinion. :)

I find that sometimes the one click upgrade have caused problems, old libs don´t get removed properly.

---

### Post by snowpine on 2012-03-22
That is probably true; some releases have had smooth upgrades, others have had problems. If you hang out on the forums for a couple of weeks after the release, you'll read all about it I'm sure, then you can make your decision based on that. :)

To answer your specific question, are you looking for something like this? [http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

The only catch is that sometimes the package names change across releases.... for example everything with gnome2 changed to gnome3, etc.

---

### Post by jpaulb on 2012-03-22
I´ll have to give that a try.
Many thanks

---

### Post by Paqman on 2012-03-22
There's a couple of options. You can use a tool like [apt-clone]("apt:apt-clone"), which is supposed to make restoring absolutely everything pretty easy. It comes highly recommended, but I've not used it myself.

The old-school method is to [get APT to spit out a list of packages]("http://ubuntuforums.org/showthread.php?t=261366"), then feed them back into it.

---

