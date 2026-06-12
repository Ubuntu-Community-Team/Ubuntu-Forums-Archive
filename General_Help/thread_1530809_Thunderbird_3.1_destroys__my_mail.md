---
title: "Thunderbird 3.1 destroys  my mail"
date: 2010-07-14
forum: General Help
---

### Post by afrodeity on 2010-07-14
My system just upgraded from a ppa which installed Thunderbird 3.1.

I now only have mail from 2009.

Can't see what is going on. Have tried looking .mozilla-thunderbird folder but nothing.

Took a look in the supposed back of my home folder and back in time has been merrily forgetting to back up any of the hidden .folders. Blimey, is there anything I can do? 

I have an important legal email which I seriously need in there, besides personal correspondence.

UPDATE: I think I might have figured out what is going on. But its a bit more complicated than I like my daily crossword puzzle to be:

I now have a four mail folders.


.mozilla-thunderbird
.thunderbird
.thunderbird.upstream
.thunderbird-2.0-replaced

One of these, probably .thunderbird-upstream, is the current one used by a maverick lucid backport which decided to use .thunderbird-2.0 folder as its source (at least this is what I think happened. Which means either .mozilla-thunderbird or .thunderbird has the missing mail


Any advice on how to resolve the conflict, this is not funny, first thing in the morning.

---

### Post by afrodeity on 2010-07-15
This time I had to move contents of .thunderbird-2.0-replaced into .thunderbird. Wish there was a tool which did this deja vu operation or better yet, a tool for examining thunderbird mail archives etc. I will now delete the other folders.

---

