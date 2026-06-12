---
title: "Clearing MPlayer's recent movies list"
date: 2009-09-27
forum: General Help
---

### Post by malfist on 2009-09-27
I'm not the only person who uses this computer, and I would like to set MPlayer not to remember the recently played movies. How can i do this?

---

### Post by SoftwareExplorer on 2009-09-27
You could alway set up separate users and then set the permissions for vlc user specific folders to be readable only by the user they belong to.
[COLOR="White"]I'm tempted to say, 'so you've been watching...' Never mind.[/COLOR]

---

### Post by malfist on 2009-09-27
Well, the recently viewed video's on mplayer are not cross-user, more than one person uses this account. If I could find where it stores the data, I could probably write a cron to erase it every now and again, that'd be enough for me.

---

### Post by StuartN on 2009-09-27
It must be all those embarrassing Lisbon II Referendum campaign information films...

Try ~/.mplayer/gui.history and ~/.mplayer/gui.url

(OMG see what those horrible Eurocrats are REALLY going to do [http://www.indymedia.ie/article/94231](http://www.indymedia.ie/article/94231))

---

### Post by bear24rw on 2009-09-27
you can go to Place > Recent Documents > Clear  which will clear recent videos from totem i'd imagine it might also work for mplayer

---

### Post by malfist on 2009-09-27
gui.history is empty and so is gui.url. Also there is not a "place" menu item.

---

### Post by StuartN on 2009-09-27
> **malfist said:**
> gui.history is empty and so is gui.url. Also there is not a "place" menu item.

My ~/mplayer/gui.history contains the recent file list, which is updated when mplayer exits. If I clear this file, then mplayer's file dialogue clears. If I edit it then the items appear in mplayer's file dialogue.

---

### Post by malfist on 2009-09-28
Not for me, mine are completely empty. I'm talking about the movie player that comes default with a gnome installation, build on top of totem.

---

### Post by fluffman86 on 2009-09-28
Just FYI, Totem is not MPlayer.  Two completely separate projects.

And to clear your totem movie player recent files, go to Places (at the top panel, next to Applications), then Recent Documents, and click "Clear Recent Documents" at the bottom.  That should work.

---

### Post by malfist on 2009-09-28
Perfect, thank you! Sorry about the confusion.

---

### Post by aala on 2010-09-28
> **bear24rw said:**
> you can go to Place > Recent Documents > Clear  which will clear recent videos from totem i'd imagine it might also work for mplayer
This works good for Gnome-Mplayer!

---

