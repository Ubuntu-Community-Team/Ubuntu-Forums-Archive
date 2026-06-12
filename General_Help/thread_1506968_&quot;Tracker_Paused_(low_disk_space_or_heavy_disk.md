---
title: "&quot;Tracker: Paused (low disk space or heavy disk use)&quot; Since Last Updates"
date: 2010-06-11
forum: General Help
---

### Post by OzzyFrank on 2010-06-11
Great. Since the last bunch of updates a couple of days ago, I basically can't search for anything in Ubuntu, not unless I use an app like **Catfish**. But what I want is to be able to seach in **Nautilus**, as I basically do searches for photos and clip art, so the presented thumbnails are a big help and time saver.

But now nothing comes up when I search, or at best just a few hits when I know there should be many more. The tooltip for the Tracker shows:

**[COLOR="Red"]Tracker: Paused (low disk space or heavy disk use)[/COLOR]**

But I actually have a few Gb to spare, and I have never gotten this message even when the drive was getting rather full. I can **[COLOR="Purple"]Re-index[/COLOR]** via the menu, and at the top is says **[COLOR="Purple"]Pause All Indexing[/COLOR]**, but nothing is actually happening. I just did a reboot, hoping something hadn't loaded previously, but now it's even worse (got 40 hits on a word previously [where there should have been 85], but now zero).

Any ideas? Also, if you know of a good search tool that displays results as thumbnails (and you can do things with those, like open or delete files), please let me know. Cheers.

---

### Post by OzzyFrank on 2010-06-22
No one else had this happen? As it is pretty much constant for me. I don't know how many Gb it needs to do its indexing, but I get this message when I have a few free, and disk use is basically zero.

It then goes to index every now and then, then pauses with the same message (or sometimes "Shutting down" instead of "Paused" in the message). Obviously any previous indexing is out the window as it can't find anything, and neither can other file managers like Dolphin.

I'd really be interested in a useful restart command for the tracker, or something that can get me searching from with Nautilus. Its Preferences haven't helped, so someone might know of a config file hack or something. I even just rebooted and it is still paused, even though I have 5Gb free and the PC is idle (besides me typing).

Any help on this would be appreciated.

---

### Post by OzzyFrank on 2010-06-22
OK, looks like I figured it out (fingers crossed!), so will detail what I did here, and mark it as solved.

First, open the **Tracker config file for editing** (do that in a terminal, as Alt+F2 opens an empty file unless you replace the tilde (~) with the actual path to your home folder):

**[COLOR="DarkRed"]gedit ~/.config/tracker/tracker.cfg[/COLOR]**

Find the following section:

[B]# Pause indexer when disk space is <= this value
# (0->100, value is in % of $HOME file system, -1=disable pausing)
LowDiskSpaceLimit=1[/B]

... and do as suggested, and make the value a _minus_ (ie: **LowDiskSpaceLimit=[COLOR="Red"]-1[/COLOR]**). Then save and close the file, and close the tracker with the following command:

**[COLOR="DarkRed"]sudo killall trackerd[/COLOR]**

To restart it, I found the command **[COLOR="DarkRed"]trackerd[/COLOR]** by itself just resulted in:

**trackerd: command not found**

... so run the following command (via Alt+F2, unless you don't mind keeping a terminal open while Tracker indexes):

**[COLOR="DarkRed"]/usr/lib/tracker/trackerd[/COLOR]**

That's it... it all seems to be running now, and will continue to do so from now on, even if I am getting perilously low on disk space (which never used to be a problem, and now it should never be again!).

You will also see there are other options to hack that aren't in the preferences GUIs, and cures for others woes I've seen people complain of, like the missing system tray icon, etc.

---

### Post by OzzyFrank on 2010-06-22
PS: I still wouldn't mind knowing why, when this was happening, there seemed to be no data from previous indexing (just before I figured this out, I was getting **_zero_** hits on **_any_** word I searched for, in Nautilus, Dolphin, and Tracker's own search tool).

And yeah, wouldn't mind seeing if I can find a way to specify certain folders to be indexed first, as it is still useless for searching my home folder half an hour into indexing, hehe. At least it _is_ indexing now, and I'll be back to searching in another hour or so.

---

### Post by OzzyFrank on 2010-06-22
Yup... never mark a thread as solved until you're actually sure it is. After the indexing finished, **[COLOR="Red"]I still can't search in anything that uses Tracker[/COLOR]**, and I even killed Nautilus just in case, and even after a reboot: **nothing**. It just tells me the tracker is idle, and here and there I see it do some crawling, but this is now worse than it ever was (so have unmarked this as solved).

I thought I may as well try re-indexing, and it asked for approval, but then saw the tooltip say Tracker was shutting down. It did restart fine manually and begin indexing, but it keeps doing weird stuff like showing that same pause message (which the icon indicates is the case) but when I move the mouse back over it, it shows it is indexing. However, then the icon disappears, and sure enough trackerd isn't running; I've restarted it manually about 6 times now, and pretty much any time I go to do a search, it's gone again.

Anyway, so there you have it. I just can't search, unless I use something like Catfish, but I prefer seeing thumbnails as the results (and the Nautilus context menu has more options to do with those files you find).

---

