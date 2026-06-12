---
title: "&quot;Open With&quot; locating another program"
date: 2010-04-13
forum: General Help
---

### Post by TheConsaw on 2010-04-13
so ive just installed Flush torrent downloader,
and when i go to download torrent i'm greeted with the usual, "open with" or "save as", and obviously Transmission is the default bt downloader,
id like to open with "other" and locate to flush, how do i know where to look, where do installed programs go to, so i may locate it

thanks

---

### Post by jaco223 on 2010-04-13
> **TheConsaw said:**
> so ive just installed Flush torrent downloader,
and when i go to download torrent i'm greeted with the usual, "open with" or "save as", and obviously Transmission is the default bt downloader,
id like to open with "other" and locate to flush, how do i know where to look, where do installed programs go to, so i may locate it

thanks


Open a terminal and type:

```
whereis flush
```

This should help you locate the directories associated with flush.

Hope this helps.

Jaco

---

### Post by agnes on 2010-04-13
In Terminal, type
> which flush

it will give the location of the executable.
Installed programs go to /usr/local/bin; sometimes /usr/bin

Note, sometimes the program name is not the command-line name of the executable, e.g. for program 'abc' the command-line name for the GUI program could be 'gtk-abc'; you can type 
> sudo find / -iname "*abc*" to find the 'abc' related executable file.

---

### Post by TheConsaw on 2010-04-13
thanks guys, great to learn a new trick
and how easy !!

---

