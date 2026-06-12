---
title: "Creative Zen (MTP device) will not mount sync"
date: 2010-10-12
forum: General Help
---

### Post by pihbar on 2010-10-12
In 10.04 I was able to plug in my MP3 player and move songs to and fro in Banshee or rhythmbox. Now, I can mount it, but it freezes banshee when trying to access it from banshee (it does appear in the list).

Does anyone know which systems have changed since 10.04 to help me troubleshoot?

---

### Post by cottfcfan on 2010-10-12
Same problem here Banshee 1.6 worked fine in Lucid. 1.8 not so in Maverick. I have the same freeze you do.
Rhythmbox works fine with my Zen though.
One thing I have to do though is start Rhythmbox first, turn on my Zen and then plug in.

---

### Post by pihbar on 2010-10-22
Tell me if you get a solution eventually... Even though I lost my Zen in the meantime QQ

---

### Post by spyderpride on 2010-11-26
I have a procedure for managing my Zen in Banshee that works, but it is kind of strange.

First, make sure the MTP support extension is enabled (the Ipod support extension is also enabled, probably not important). Mass Media extension should be DISABLED.

Open up Nautilus and go to Edit-->Preferences, make sure the default action for a media player is to "Do Nothing".

With Banshee not running, plug in the Zen. Wait a few seconds for the icon to show up on the desktop. Right-click it and unmount.

Now run Banshee, go ahead and manage the player as you please.  Auto-sync or manual, it all should work pretty well.  Maybe not perfectly, but at least lets you put your music on it fairly easily without resorting to the use of Windows.

---

