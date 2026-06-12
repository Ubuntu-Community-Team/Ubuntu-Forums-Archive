---
title: "i7-860, 8GB, ATI 4850 and it is crawling. (10.10)"
date: 2011-01-07
forum: General Help
---

### Post by tertius on 2011-01-07
When I use firefox and I hover over a link it takes 2+ seconds + for the cursor to change to a hand from a text selection tool.

When I scroll with my mouse wheel, it (at first) takes 2+ seconds before the page starts moving.

As I am typing this, occasionally I see no text being added to a line and then a whole line or a few words all of a sudden (as I don't stop typing).

What do I have to do to get a smooth experience?

I'm am not a newbie so any advice of any level will be helpful.

---

### Post by cogier on 2011-01-07
You need to establish what it is that is slowing you down. I would start with running Terminal **[Ctrl] + [Alt] + T** and entering "**top**"

If you need a GUI version go to **System>Administration>System Monitor** and click on the **Processes** tab.

This will show what is using all your resources.

---

### Post by tertius on 2011-01-07
The only thing taking 100% (of one "CPU") every 10 seconds is firefox.

As I have it here firefox is using 1.8GB of memory (jumps between 1.5 and 2GB) currently.  I have to again say that I have 8GB with the current usage at 3.5GB.

I do have some add-ons installed and quite a few tabs/windows open (that I leave open).

- Amazon wishlist.
- Cloudmagic.
- Firebug.
- Google Shortcuts.
- LastPass.
- Read it later.
- SearchStatus
- Ubuntu firefox addons.
- XMarks.

Do I just need to operate with less windows and tabs?  It doesn't do that much to speed it up and clearly it's only using half a CPU core when I get these spikes (and it changes which is used).

---

