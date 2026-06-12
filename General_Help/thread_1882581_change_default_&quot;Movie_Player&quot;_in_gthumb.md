---
title: "change default &quot;Movie Player&quot; in gthumb?"
date: 2011-11-17
forum: General Help
---

### Post by buntuyu on 2011-11-17
this should be trivial but it seems frustratingly impossible.

When you right-click on a video thumbnail image in gthumb, "Open With..." gives you "Available applications", where you see "Movie Player".  There seems to be space for more items, but "Movie Player" is the only one, and it's "totem %U".  How do I replace totem with, say, vlc as the default movie player in gthumb?

In the section below that, there is a list of custom commands you recently used.  But that still doesn't make anything else the default.  

I simply want to doubleclick on a thumbnail and have a player of MY choice to play back the video.

(Right now i have to do right-click, "Open With...", then doubleclick on the recently used vlc command, in the bottom box.)


thanks

---

### Post by buntuyu on 2011-11-20
bump

---

### Post by buntuyu on 2011-11-28
bump. Anyone?  

(so, I was right -- this looks DECEPTIVELY trivial, but is really impossible?)

---

### Post by claracc on 2011-11-28
What ubuntu are you using?

In lucid lynx (ubuntu 10.04) you right click on the video file, select properties, open with, if vlc doesn't appear in the list, you click on add, use a personalized command, and then write /bin/vlc

---

### Post by PGScooter on 2011-11-28
yes, you are right; it is a pain :(
Hopefully they change this in 12.04.

See here for a solution:
[http://ubuntuforums.org/showthread.php?t=1863021&highlight=open+with](http://ubuntuforums.org/showthread.php?t=1863021&highlight=open+with)

---

### Post by buntuyu on 2011-11-29
> **PGScooter said:**
> yes, you are right; it is a pain :(
Hopefully they change this in 12.04.

See here for a solution:
[http://ubuntuforums.org/showthread.php?t=1863021&highlight=open+with](http://ubuntuforums.org/showthread.php?t=1863021&highlight=open+with)

I am on Maverick (10.10).  I want to ditto cookacounty in his frustration over Ubuntu 11.* -- although I haven't tried it, what I am reading about it makes me want to stick with Maverick.  And regression is the most hurtful thing (once you have a working feature, why remove it? Why take a step back?)

Back to my current issue:  to claracc: You probably meant just "right-click, open with".   I don't have an Add button in that dialogue. Only remove (?!)

However, I just found a work-around!

In the gthumb application menus I went to "Edit" -> "Preferences" -> "Hot Keys" (tab), and added "vlc %f" (Previously, I had misread the legend -- "%f" stands for the file name WITH FULL PATH, and I had the "%p/%f" redundancy -- that's why it wouldn't work before!)

:-) :-(

So, the above works even on laptops -- with the "Fn + [numeric equivalent]"

They should fix the "Open With" settings and controls, still... (It's, like, almost there -- it stores the command-line history in a list below, but doesn't give you a way to make a certain command PRIMARY (default))

Thanks to the responders!

---

