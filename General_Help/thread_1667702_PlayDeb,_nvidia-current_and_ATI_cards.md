---
title: "PlayDeb, nvidia-current and ATI cards"
date: 2011-01-15
forum: General Help
---

### Post by 3602 on 2011-01-15
I wanted to get a couple of games not in the repos, so I installed the GetDeb package and added a couple of Software Sources.
Now, when I click on the "Install this Now" on the PlayDeb website, Synaptic opens and starts to download package *nvidia-current.* I immediately halted the download because, well, I am using an *ATI card*.
So basically, what's up?

---

### Post by ajgreeny on 2011-01-15
Perhaps it is not for a graphics card; maybe some other nvidia chip in your computer.

It could also be set as one of the dependencies of the game, just to ensure that where people are not using the most recent/current driver but have nvidia cards, they are updated, as the game needs that driver installed.

---

### Post by 3602 on 2011-01-15
Well I just downloaded this thing (along with a couple of nice 3D games). Games run mighty fine and Gnome/X hasn't crashed... yet. Here's the description in Synaptics:
> The binary driver provide optimized hardware acceleration of OpenGL
applications via a direct-rendering X Server. AGP, PCIe, SLI, TV-out
and flat panel displays are also supported.So I guess it's not a graphics card driver, but it provides support for accelerations of all types, huh.
Interesting. I'll reboot and run the games. if all is well then I'll mark this thing SOLVED.

EDIT: Well all is well. man Ubuntu sure boots fast.

---

### Post by ajgreeny on 2011-01-16
In most cases, even if you downloaded several different drivers for graphics cards, including ones for a card you don't have, it would do nothing other than use a bit of disk space.

You might even find that ```
sudo apt-get autoclean
``` would remove it along with other superfluous packages, but unless you are short of disk space, I would leave well alone.

If it ain't broke, don't fix it!
If you do fix it, be prepared, just in case it does break!

---

### Post by 3602 on 2011-01-16
Yeah I got some 448GB left. I'll do some housekeeping when I'm down to, day, 14GB. Thanks.

---

