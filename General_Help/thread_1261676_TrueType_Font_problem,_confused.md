---
title: "TrueType Font problem, confused"
date: 2009-09-09
forum: General Help
---

### Post by ManCrab on 2009-09-09
I grabbed a font from a website, copied it to ./~fonts, rebooted and tried to use it in GIMP/Inkscape/OpenOffice, it did not work.

GIMP, Inkscape and OpenOffice show the font in their respective drop down lists but even though it appears I've selected the font,
the text continues to use the 'default' font.  Is there any way to get this to work, or am I out of luck?  

*[I]EDIT:* [/I]The answer was to install fontforge (it's in the repositories), edit the internal name of the font (included comas, hyphens, apostrophes and spaces originally) and re-save it. Works like a charm in Inkscape now.

Thanks for the help guys, hope this helps somebody else.

---

### Post by Achilles124 on 2009-09-09
Don't know but I tell you what I did. I copied the font into the .gimp/fonts folder. And that worked. So copy the fonts in the fonts folders of the programs.

---

### Post by ManCrab on 2009-09-09
> **Achilles124 said:**
> Don't know but I tell you what I did. I copied the font into the .gimp/fonts folder. And that worked. So copy the fonts in the fonts folders of the programs.

 Just tried that, no dice. Even issued [quote=]$ sudo fc-cache -fv[/quote] and nothing changed. I'm starting to lose hope. C'mon open source, don't let me down :(

---

### Post by Dennis N on 2009-09-09
I have put new font files into the /.fonts folder inside my home folder and that works for me, in particular with both Inkscape and Gimp. I don't think where you put them is the problem. Maybe something is wrong with that new font you added. Can you select other fonts and use them?

---

### Post by ManCrab on 2009-09-09
> **Dennis N said:**
> I have put new font files into the /.fonts folder inside my home folder and that works for me, in particular with both Inkscape and Gimp. I don't think where you put them is the problem. Maybe something is wrong with that new font you added. Can you select other fonts and use them?

 Just tried a few random fonts from the same site, seems like they work. What's got me confused, and more than a little frustrated is that the GNOME 'Font Viewer' displays the font I can't use just fine.  Ah well.

---

