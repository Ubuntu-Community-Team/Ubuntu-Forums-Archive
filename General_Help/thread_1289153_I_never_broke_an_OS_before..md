---
title: "I never broke an OS before."
date: 2009-10-12
forum: General Help
---

### Post by brandon_h on 2009-10-12
This is kind of exciting. I wasn't even trying but I did it. 

It started with a issue that I very much wanted corrected.

When I first installed ubuntu everything worked perfectly, at least as far as viewing videos went. I could watch hulu movies and tv shows, youtube videos, and pretty much any and every other video i stumbled across. 

It all worked perfectly, then for some reason or another, it quit working like it should. It was barely noticeable on smaller videos but, for example, full screen hulu, my video was horribly jerky while the audio was mostly perfect. 

The issue involved the entire screen. If I clicked pause or the button to leave full screen, sometimes 10 seconds would pass before the action would even take place. 

Following various threads I found on here, I tried to fix this issue. 

Next thing I knew, when i tried to boot, I couldn't get into the desktop. It'd get stuck at the black screen and ask me to log in. Eventually a box would pop up and, following options, let me revert to default. 

Now, every time I try to watch a video full screen firefox crashes.

I plan on reinstalling in the morning and trying again, this time with much less gusto. Hopefully everything will be perfect again with a fresh install and i can proceed more carefully.

That said, the question is.... Is there anything in Ubuntu that works like window's restore checkpoints?

I would like to keep playing around, learning, experimenting, etc, but it would be nice to have a way of undoing a mistake I make without having to reinstall the entire OS if I can't figure out what I did.

---

### Post by nothingspecial on 2009-10-12
> **brandon_h said:**
> 

I would like to keep playing around, learning, experimenting, etc, but it would be nice to have a way of undoing a mistake I make without having to reinstall the entire OS if I can't figure out what I did.

Install it twice, on seperate partitions. One for experimenting and one to use. Try stuff out on the experimental one and once you know it works, implement it on your main install.

---

### Post by MelDJ on 2009-10-12
windows recovery point utility just restores settings. it would be wise for you to backup your stuff in ubuntu before playing around. moreover most of the problems can be solved if you ask here. 
like what did the box say? did it say busybox? or did it tell you to login?

---

### Post by howefield on 2009-10-12
> **brandon_h said:**
> That said, the question is.... Is there anything in Ubuntu that works like window's restore checkpoints?

Just a couple of things to consider.. 

Not sure if there is anything comparable to windows restore feature but you could make an image of your partitions/disk with Clonezilla and use this to backup/restore.

Another option is to create a seperate /home partition with your reinstall which means future reinstalls are much easier as you are able to keep all your settings etc intact.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://clonezilla.org/clonezilla-live/](http://clonezilla.org/clonezilla-live/)

---

### Post by brandon_h on 2009-10-12
The part asking me to log in is, i think, the exact same thing you see if you press ctrl+alt+f1

I do not remember the title of the box that popped up, but it had several radio buttoned choices. It said something about using low graphics mode. I followed the options until I saw an option to restore default graphics mode. Using that the desktop loaded on next boot.

---

### Post by MelDJ on 2009-10-12
if you want to tinker around a system, maybe you should install it in virtualbox. then if it crashes, you dont have to go through a big deal of work. [http://www.virtualbox.org/](http://www.virtualbox.org/)

---

