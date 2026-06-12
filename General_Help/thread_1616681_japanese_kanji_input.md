---
title: "japanese kanji input"
date: 2010-11-08
forum: General Help
---

### Post by pikachugogo on 2010-11-08
i have set up japanese input on ubuntu, but when i type japanese using anthy, it only comes in hiragana, not katakana or kanji. it sais when i use the space key, it should change, but it does not. i do not understand what i did wrong.

---

### Post by temporos on 2011-01-07
I've been having this same issue.  The hiragana comes up fine, but pressing the space bar doesn't do anything.  It's supposed to present me with a list of katakana or kanji characters to use.

---

### Post by Motorhead Kaze on 2011-01-14
Totally! WTF? Bump!

---

### Post by temporos on 2011-01-15
&#12420;&#12387;&#12383;!  I've managed to fix the Kanji/Katakana issue in Lucid.  Basically, the m17n input method is buggy (at best), and isn't properly implemented in Lucid. The original Anthy (no suffix) works like it should, and like it did in Karmic.  Here are the steps to follow.

[LIST=1]
[*]Remove "anthy (m17n)" from your iBus list.
[*]Launch the Synaptic Package Manager.
[*]Search for "anthy".
[*]Click the checkbox next to "ibus-anthy".
[*]Select "Mark for installation..." in the context menu that appears.
[*]Click "Apply" at the top of the window.
[*]Click "OK" in the dialogue window that appears.
[*]Wait for the download and installation to complete.
[*]Close the Synaptic Package Manager.
[*]Restart your computer (you **must** restart, not logout/login).
[/LIST]

If it works, awesome!  Mark the thread solved.  If not, we'll have to figure it out.

---

### Post by Asday on 2012-01-24
> **temporos said:**
> &#12420;&#12387;&#12383;!  I've managed to fix the Kanji/Katakana issue in Lucid.  Basically, the m17n input method is buggy (at best), and isn't properly implemented in Lucid. The original Anthy (no suffix) works like it should, and like it did in Karmic.  Here are the steps to follow.

[LIST=1]
[*]Remove "anthy (m17n)" from your iBus list.
[*]Launch the Synaptic Package Manager.
[*]Search for "anthy".
[*]Click the checkbox next to "ibus-anthy".
[*]Select "Mark for installation..." in the context menu that appears.
[*]Click "Apply" at the top of the window.
[*]Click "OK" in the dialogue window that appears.
[*]Wait for the download and installation to complete.
[*]Close the Synaptic Package Manager.
[*]Restart your computer (you **must** restart, not logout/login).
[/LIST]

If it works, awesome!  Mark the thread solved.  If not, we'll have to figure it out.

You're a King.  My HDD is dead, and I'm running from a 10.04 livedisc, and your line "Restart your computer" made me _really_ sad.  I want to continue to use memrise, and the m17n is, for whatever reason, broke as all hell.

HOWEVER.  I got around it by going up to closing Synaptic, then I removed m17n from the IMEs in IBus, then quit IBus, and started it again, and Anthy was there.

It has a crown.  That crown I present to you.  Hence, you're a King.

EDIT:  I just realised it's 2012, not 2011.  Sorry for the necro.

At least I got here from google, so peeps also from there might get to see this.

---

