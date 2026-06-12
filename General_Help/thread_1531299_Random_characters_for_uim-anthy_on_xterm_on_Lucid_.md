---
title: "Random characters for uim-anthy on xterm on Lucid Lynx"
date: 2010-07-14
forum: General Help
---

### Post by Izkata on 2010-07-14
So, I'm currently using 8.04 - this is the last thing I need to fix before switching to 10.04.

I use uim because it works nicely, even outside of Gnome, when setup correctly.  I tried the new IBus thing, couldn't get it to work satisfactorily.

Anyway, everything is working, except, while in xterm, the characters don't "resolve" into Japanese characters until "pasted" onto xterm.

For example, typing &#31169; (&#12431;&#12383;&#12375;/watashi) - before hitting space, it should look like this, and be able to press space to cycle through kanji options:
$ _&#12431;&#12383;&#12375;_

Instead, it looks something like this:
$ $o#$o$
<ENTER>
$ &#12431;&#12383;&#12375;

Note that so far this ONLY happens in xterm.  In gnome-terminal, and other applications that I've tried, it works correctly.

Best guess is that something isn't interpreting the unicode correctly, but I have no clue where to look.

---

### Post by Izkata on 2010-07-15
Fixed it!

Not sure why this changed since 8.04, but I found the solution here: [http://groups.google.com/group/uim-en/browse_thread/thread/5c6fe8d47df15273/64098bf72e9a24a0?pli=1](http://groups.google.com/group/uim-en/browse_thread/thread/5c6fe8d47df15273/64098bf72e9a24a0?pli=1)

Simply, one of the xterm settings was wrong.  All that had to be done was add this line to the configuration file:
> XTerm*ximFont: fixed

There's still an odd issue with this font, though, where if I've only typed the consonant (romaji mode), it should display the latin character.  As this font doesn't seem to support it, uim tries anyway by putting a small line in.  Whatever, good enough for me!

EDIT:  I also now know that what I'm talking about is called "preedit mode" ;)

---

### Post by itcotbtoemik on 2010-07-15
It's been "fixed" font in xterm since patch #242
(2009/2/15).  Perhaps 8.04 was released around the
same time.

---

### Post by Izkata on 2010-07-15
8.04, as the name means, is April 2008.

In 10.04, Lucid Lynx, the Xterm*ximFont is *not* set to "fixed", hence why I had to tell xterm to use it in the configuration file.

It is not required in 8.04, the older Ubuntu release.

---

