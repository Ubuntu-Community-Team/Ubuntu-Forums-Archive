---
title: "Using gtkpod to sync podcast"
date: 2009-09-01
forum: General Help
---

### Post by bledsoe on 2009-09-01
Hi,

I've been using gtkpod with Rhythmbox for a while, and find them to be a fairly straightforward way to manage my iPod music and podcasts.  The one problem I've had is that I can't figure out how to make gtkpod automatically sync my iPod when I add new episodes of podcasts.

I am currently subscribed to three podcasts (using Rhythmbox), and when a new episode is posted, Rhythmbox automatically downloads it.  But when I start gtkpod and plug in my iPod, the only way I've been able to get the new podcast episodes onto my iPod is to select the "Podcasts" playlist under my iPod heading in the "Playlists" sidebar, then click the "Add Folder" button and select/add the new episodes manually.

Admittedly, this is not the worst thing in the world, and this manual method has been working fine for me for several months, but it really seems like it would be fairly simple to have my iPod update automatically with the new podcast episodes when I plug it in, yet I haven't been able to figure out how to do it.

Any suggestions greatly appreciated.

---

### Post by jdforsythe on 2009-09-14
Bumping because I'm trying to do the same exact thing.

I have nailed down the problem, the solution is eluding me, though.

The problem is that Rhythmbox is downloading the podcasts to separate directories and gtkpod won't look recursively through folders for files.

For example, you have Rhythmbox set up to download podcasts to /data/music/podcasts

It will download separate podcasts to
/data/music/podcasts/podcast_a
/data/music/podcasts/podcast_b
/data/music/podcasts/podcast_c
etc.

In gtkpod, if you go to the repository options, choose your ipod, choose the playlist tab, and choose podcasts, you can have it automatically sync with a directory. You probably, as I do, have selected /data/music/podcasts hoping that it will pick up the subdirectories for each podcast. However, gtkpod does not go into folders. It will only find files that reside in /data/music/podcasts, the exact directory you picked.

Possible solutions would be to find a way to have Rhythmbox not create subdirectories for each podcast, or alternatively to have gtkpod look recursively through directories. The only other way I can think of off the top of my head would be to have a script run with cron that every so often would create symbolic links to all files under a certain directory, effectively putting links to all podcasts in a single directory. Maybe then gtkpod would see them. I hope there's a simpler solution.

---

### Post by yaztromo on 2010-03-29
Same problem here. Here's hoping the gtkpod developer adds support for recursive syncing of folders sometime soon.

---

### Post by Lacoste on 2010-05-21
+1 ;  if anyone comes across this thread and knows of a better solution, please update it.

Thx

Lacoste

---

### Post by ForgivenByJC on 2010-06-23
Not certain if this will work, but there are two gconf-editor entries which may help with how the podcasts are stored.
[LIST=1]
[*]/apps/rhythmbox/library_layout_path
[*]/apps/rhythmbox/library_layout_filename
[/LIST]
I do not have time to research them right now (Rhythmbox's website has good documentation, if I recall) but these might lead to answers about how Rhythmbox stores its podcasts.

There is one potential issue possibly, since the podcast functionality is actually a plugin for Rhythmbox, this podcast plugin may not adhere to the gconf-editor entries above.  There is neither any path related entries for the podcast plugin within gconf-editor.

Please, give an update if any of this information gets you closer to your intended goal!

---

