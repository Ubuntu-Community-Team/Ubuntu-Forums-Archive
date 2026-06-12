---
title: "gnumeric cut and paste issue"
date: 2011-07-10
forum: General Help
---

### Post by maclenin on 2011-07-10
Hello!

I have just opened a spreadsheet (created in intrepid / edited plenty in lucid) in natty, with **gnumeric 1.10.13** (using gnumeric for the fist time in my fresh natty install) - and am unable to **paste** data / text within the spreadsheet, after **cutting** data / text from another part of the same spreadsheet - **via mouse or keyboard shortcuts** (i.e. ctrl+x or ctrl+c and ctrl+v). Moreover, "Undo" is greyed-out after cutting, so I can't return the "cut" data / text to its original position. Also, the "cut" item vanishes as it's cut, rather than being surrounded by the dotted line - which (in my experience) is the "normal" behavior.

Copying (and pasting) using the mouse or keyboard seems (preliminarily) to work as it should - though I've started seeing some behavior similar to "cut" with the "copy" function, as well.

Any ideas?

---

### Post by Toz on 2011-07-10
Looks like they are known bugs:

[https://bugzilla.gnome.org/show_bug.cgi?id=640913]("https://bugzilla.gnome.org/show_bug.cgi?id=640913")

and

[https://bugzilla.xfce.org/show_bug.cgi?id=6521]("https://bugzilla.xfce.org/show_bug.cgi?id=6521")

However, a suggestion in one of those threads to uncheck the "Prefer CLIPBOARD over PRIMARY selection" in the "Copy and Paste" section of the preferences seems to fix the issue for me.

---

### Post by maclenin on 2011-07-10
Thanks, **Toz**!

No joy with an unchecked "Prefer CLIPBOARD over PRIMARY selection" - what I may end up doing ('cause I need the functionality - before bugs are resolved in current versions) is installing **gnumeric 1.10.16** - to see whether this fixes the cut and past issue....

However, cut and paste is exhibiting "extra-gnunmeric" quirks - like pasting data / text from other applications / browsers / file managers - when the thing I've cut is a value with**IN** gnumeric - which (along with my read through your bug links) makes me worry a new gnumeric may not be the answer....

Hmmm....

Thanks, again, for the references and suggestion.

---

### Post by maclenin on 2011-07-11
I am loathe to (finish) install(ing) **gnumeric 1.10.16** - as it seems to crack the lid on a pandora's box of dependency breakages and entanglements....

I'll keep searching and will report back if I make any headway.

---

