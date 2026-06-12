---
title: "can I stop seeing an update listed that I don't want?"
date: 2006-04-20
forum: General Help
---

### Post by Alev on 2006-04-20
I noticed that the ubuntu software update wants me to install firefox 1.0.8-0ubuntu5.10.  The thing is that I already have firefox 1.5.  Is there something I can do so that this update stops showing up?

---

### Post by lolocaust on 2006-04-20
if you're using firefox 1.5.x in breezy, then you probably didnt install on top of 1.0. My advice is to install that particular update, because many programs rely on firefox 1.0.x for the rendering engine and that means any programs that do rely on it are vunerable to the security flaws.

replacing 1.0 with 1.5 would have broken your system, so im sure 1.0 is still there, and separate from 1.5.

---

### Post by PapaWiskas on 2006-04-20
Open up Synaptic Manager, and find the FireFox updates listed.

Highlight them, then all you have to do is go up to your menu area at the top and choose "Package", then chose Lock Version then apply.

And you are done, updates wont show up for that package again.

---

### Post by PapaWiskas on 2006-04-20
[QUOTE=lolocaust]replacing 1.0 with 1.5 would have broken your system, so im sure 1.0 is still there, and separate from 1.5.[/QUOTE]

My system didnt break...so I am not sure what this means or if it is true.  But I have had no problems.

---

### Post by Alev on 2006-04-21
Ok, I went ahead with it and installed it.  But it's good to know how to block the updates for a program.  Often times I only want to update when there is a new version, not a fix for a bug that I never encounter.
Thank you.

---

