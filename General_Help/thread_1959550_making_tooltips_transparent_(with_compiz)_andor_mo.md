---
title: "making tooltips transparent (with compiz?) and/or modifying or eliminating them"
date: 2012-04-16
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2012-04-16
I've been chastised for practicing black magic in raising this thread [http://ubuntuforums.org/showthread.php?t=1411874](http://ubuntuforums.org/showthread.php?t=1411874) on tooltip extermination from the dead. Ncurses! I had to kill three chickens and use up half my unholy water to get that sucker to the front page and then the forum gods drove a stake through its heart.

These ancient writings saith that once upon a time in gnome 2 land there was a powerful magi named Compiz Config Settings Manager that was able to slay **[SIZE=2]ALL[/SIZE]** the tooltip monsters by making them transparent unto ghostly death. I reinstalled Compiz hoping to avail mineself of the magi's services, but, alas, that gentleprogram must have either changed his name or gone on to the Great Archive in the Cloud. Does anyone know if he left behind an apprentice or an heir that might accomplish the same magical feat and where I might find him or her if he or she does indeed still exist in this modern age?

I've been able to kill a few tooltips with mateconfig-editor, the son of gconfig-editor, and I think I may have knocked off one or two more with gconf-editor, but the Compiz approach is the only thing I've seen asserted to be more powerful. I can't seem to google up anything more recent than the thread alluded to.

Of course, if anyone knows of other methods of exterminating tooltips, either retail or en masse, I'd appreciate suggestions.

---

### Post by stinkeye on 2012-04-16
Still there in Oneiric.
Of course, you have to be running compiz as your window manager for this to work.

---

### Post by Dreamer Fithp Apprentice on 2012-04-18
Thanks, Stinkeye. At least now I know I'm not looking for an abandoned feature. My mistake was not in failing to use compiz after installing it but in failing to realize there was more to install than just compiz itself. I've now installed compizconfig-settings-manager and a couple of the plugins. Possibly it is in a plugin I haven't installed yet. Synaptic's plugin descriptions won't scroll for me since I reinstalled Compiz so I could have missed it in the description if it isn't in the first part. Or possibly I'm missing something because I have prepetual problems with windows that are drawn partially outside the monitor so to speak. Unlike the scrolling problem in Synaptic, this happens with both compiz and the mate clone of metacity and has been a problem ever since I installed Oneiric. Could be I'm missing some crucial button because it is in a part of a window I can't manage to drag into the monitor no matter how much I resize and drag. If anyone knows which plugin the effect I'm looking for is in I'll give this another try, but for now, absent any new info, I'm going to give up on tweaking this particular annoyance away and let it ride along with similar annoyances like my mouse pointer that shrinks to microscopic dimensions. For now, if I spend any more time trying to get Oneiric to work right,  I should probably concentrate on getting some window manager to understand where my monitor is and how big the screen is since that may be in the way of my attempts to fix other stuff like the tooltip annoyance. Maybe 12.04 will fix them anyway. If not, I think I'll just give Ubuntu up for a lost cause and move on to trying Slack and one of the BSDs.  I do appreciate your effort in thinking and posting an answer and I've tried to be a good forum cit and "pass it forward" when I saw the opportunity but I'm getting to the point I'm spending a lot more time working ON the Oneiric installation than WITH it and it just doesn't seem worth the effort.

---

### Post by stinkeye on 2012-04-18
Sounds like a broke install rather than a release problem.
The only thing you need to install for compiz is ccsm to change settings.
Try removing your compiz configs then log out/in
```
rm -rf .gconf/apps/compiz*
rm -rf .cache/compizconfig-1/
rm -rf .config/compiz-1/
rm -rf .compiz*
```

PS I've been using 12.04 for a couple of months now and find it quite stable.

---

