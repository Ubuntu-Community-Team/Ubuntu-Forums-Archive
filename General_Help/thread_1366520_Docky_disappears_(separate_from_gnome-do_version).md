---
title: "Docky disappears (separate from gnome-do version)"
date: 2009-12-28
forum: General Help
---

### Post by lukaspress on 2009-12-28
Hi.  I am using the new version of docky, which is separate from gnome do.  unfortunately it displays the same problem I sometimes experienced while it was still part of gnome-do.  namely that it disappears for no apparent reason.

one login i have docky, next time i login its not there.  If i open the program through the menu or elsewhere it seems to do nothing, still no sign of docky.

whats going on? I really like docky but can't rely on it.  Anyone any ideas?   Ta

---

### Post by lukaspress on 2009-12-28
Trying to open the program by typing 'docky' into a terminal i got the message that the program was already running.  So I killed it using 

kill $(pgrep docky)

Then i was able to start it again, and it works.   So its a workaround i suppose, but still a pain in the arris.  Anyone know what's causing it to become invisible in the first place?

---

### Post by tom.swartz07 on 2009-12-28
> **lukaspress said:**
> Trying to open the program by typing 'docky' into a terminal i got the message that the program was already running.  So I killed it using 

kill $(pgrep docky)

Then i was able to start it again, and it works.   So its a workaround i suppose, but still a pain in the arris.  Anyone know what's causing it to become invisible in the first place?

I know this might be an obvious question, but it might be autohiding? Try and mouse over where the dock was, and see if it pops up.

I use docky too, and I know that sometimes after an update docky freezes and locks, forcing me to kill it and restart it. This may be the case too.

---

### Post by lukaspress on 2009-12-28
Haha no its not autohiding; i may be a newb but come on!!

Strangely I just left my pc for about an hour, and when i came back to it docky had gone again.   literally that - it was working, then one hour later it had disappeared.  Nothing happened in between at all.

---

### Post by lukaspress on 2009-12-28
Stranger still - i just got docky working again after killing then restarting it.  Then I opened image viewer briefly to view a single .png file.  When i closed image viewer docky has gone again!!

On looking into it a bit more it seems this is a known bug - it disappears whenever a window is closed.   Pretty big bug really!  Anyways it's reported so hopefully someone will get onto it soon.

---

### Post by jnew93 on 2009-12-28
Have you enabled a compositing manager? It's to my knowledge that in order for docky or similar programs to work (read: show up) there needs to be one turned on. If you are using compiz it should be fine, but if you are using metacity, you need to enable compositing, which can be done easily in gconf-editor.

But if it is a reported bug it may be docky's own fault.

---

### Post by argybee on 2010-05-03
Docky definitely disappears. I have just loaded fresh lucid and have had it disappear several (4?) times in a day. Checked processes list and it was not there. Had to re-start it from menus each time. At least that's not as bad as the problems with the AWN.

---

### Post by fabounet on 2010-05-03
you may want to try GLX-Dock; none of them is bug-free, but this one definitely rocks.
[http://www.glx-dock.org/ww_page.php?p=From%20the%20repository&lang=en]("http://www.glx-dock.org/ww_page.php?p=From%20the%20repository&lang=en")

---

