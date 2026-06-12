---
title: "Rhythmbox Smart Playlists Broken?"
date: 2009-10-07
forum: General Help
---

### Post by hwttdz on 2009-10-07
Is anyone else having trouble creating smart playlists in rhythmbox?  I get a 
```
Rhythmbox:ERROR:rb-auto-playlist-source.c:745:rb_auto_playlist_source_do_query: assertion failed: (priv->cached_all_query) Aborted
```
error.

---

### Post by mac9416 on 2009-10-07
Yes, Rhythmbox shuts down on me when I try to create one. I haven't looked at the command-line output, though.

---

### Post by delianeal on 2009-10-07
I've also had Rhythm Box shut down on me while I was trying to make a smart playlist (I'm afraid of the command line so I didn't try it that way).  I got it to work once - no idea how or why - and then after that every time I enter all my parameters and hit "enter" or "create" or whatever the last button is, it shuts down. 

 I did post a question about it a while back but there was no answer so I figured it was some stupid mistake I was making since I'm such a complete noob.

---

### Post by hwttdz on 2009-10-07
Nope seems to be a bug.  I just wanted to do a sanity check before I reported it (or checked if it existed).  I'm going to see if I can take a look at the code and figure something out, but don't hold your breath.

---

### Post by sbsbessa on 2009-11-05
Just tried this on Rythmbox 0.12.5 and it worked.
I'm running a clean Ubuntu 9.10 64bit install.

---

### Post by hwttdz on 2009-11-05
Yup seems to be fixed.

---

