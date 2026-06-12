---
title: "Keffaine stops reacting"
date: 2006-02-14
forum: General Help
---

### Post by WujekSamoZlo on 2006-02-14
When I watch a film, and play a little with arrows and searching the moment I want to watch, Keffeine just locks - the film (audio too) goes on, but it doesn't react to myu input. What I can do is to switch to the next visrtual desktop, run the Konsole and kill it.
I use the Xine engine. What's wrong?

---

### Post by Rog131 on 2006-02-15
Launch kaffeine in konsole -> get error message(s) (if any).

---

### Post by WujekSamoZlo on 2006-02-15
Such msg keeps repeating:

[mpeg4 @ 0xb61ace50]vop not coded

---

### Post by Rog131 on 2006-02-15
D'oh !

It seems that xine has problem with over 2 GB files (->vop not coded error).
Is this problem here ?

Videos over 2GB - Xine & MPlayer Problems:
[http://www.gossamer-threads.com/lists/mythtv/users/91616?page=last](http://www.gossamer-threads.com/lists/mythtv/users/91616?page=last)

Xine - Green Screen during Playback:
"I"m still having this problem, but I think I narrowed down the types
of files that are failing.  The problem appears to only occur with avi
files over 2GB whether they"re encoded with DivX or Xvid."
[http://sourceforge.net/mailarchive/forum.php?forum_id=3438&max_rows=25&style=nested&viewmonth=200410](http://sourceforge.net/mailarchive/forum.php?forum_id=3438&max_rows=25&style=nested&viewmonth=200410)

Fast solution: Try VLC - player.
[http://www.videolan.org/vlc/](http://www.videolan.org/vlc/) 
It is also in the repositories.

Slower (better) solution:
From Xine - Green Screen during Playback -
"You are right, this is a codec problem. The file is handled by xine"s copy of
ffmpeg. If you want to try something, you could install the latest ffmpeg"...

:confused:

---

### Post by WujekSamoZlo on 2006-02-15
But the file I played was only 350 mb large.

---

### Post by Rog131 on 2006-02-16
Kaffeine bugs:[http://sourceforge.net/tracker/?group_id=86937&atid=581406](http://sourceforge.net/tracker/?group_id=86937&atid=581406)

Kaffeine GUI freezes after seeking. ID=1389188. Open Date 2005-12-23.

<snip>
Summary:
Kaffeine GUI freezes after seeking
When I have a long film (120 min for example) and I
seek a lot (20 minutes for example) the GUI dies
forever....movie keeps playing but the GUI is frozen.

Resolution: None

</snip>

Same bug ?
:(

---

