---
title: "Backtick key - have to press twice"
date: 2009-11-20
forum: General Help
---

### Post by Richard1979 on 2009-11-20
Hi all,

I have a problem with the backtick key which is the ` character.
This is the key to the left of 1 and above TAB (UK keyboard layout).
Using shift with this key gives ¬

My problem is that I have to press it twice to type a backtick character.
Any ideas? I can't see any options for this in Keyboard prefs.

UPDATE: Have fixed it now by clicking "Reset to Default" in the Keyboard prefs.

---

### Post by cbuckley on 2011-02-27
The above solution didn't work for my keyboard, so I had to modify my key map to stop generating the [dead key]("http://en.wikipedia.org/wiki/Dead_key"):

```

xmodmap -e 'keycode 49 = grave asciitilde'

```

You should also use [FONT=monospace]xev[/FONT] to get the correct keycode for your keyboard.

---

### Post by tredegar on 2011-02-27
I'm just being picky here, but the "`" symbol quotation seems mostly to be used by shells to represent "the result of the command within back-tick symbols".

The back-tick character was generally recognised as too easily confused with the "'" character, so using `command` is now deprecated and $(command) now replaces it. Backticks will still work in most shells, but who knows for how much longer?

This is good, as $(command) is easier to read, easier to type and causes less confusion.

---

### Post by ttwt on 2012-06-17
xmodmap -e 'keycode 49 = grave asciitilde'

also worked fine for me on Lubuntu 12.04 LTS.  British keyboard, ` key left of the 1 and above the tab.

Regarding tredegar - TMTOS (There's more than one shell ):P to Perl's TMTOWTDI) - Perl uses it too in the same manner.

My pet hate is M4 which expects a quoted string to be `a quoted string' :lolflag:

Agree $(command) is nice though.

Regards,



D

---

### Post by howefield on 2012-06-17
Thread closed.

---

