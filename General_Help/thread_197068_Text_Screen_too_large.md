---
title: "Text Screen too large"
date: 2006-06-15
forum: General Help
---

### Post by SteveF on 2006-06-15
Since upgrading to Dapper, I have had a problem with screen realestate whne switching to a text console (CTRL-ALT-F1).  I think it is related to the graphical login because when I boot into recovery mode, I don't have the issue.

The problem is parts of the text are offscreen.  It's as if the screen is too small for the size the terminal thinks my screen is.

Is there any place I can make a change to fix this?

Thanks,

Steve

---

### Post by Ramses de Norre on 2006-06-15
What resolution are you running? The terminal resolution is set by adding a vga=xxx option to your menu.lst, with xxx the code for the resolution you want. I'm not sure this will fix your problem though..

---

### Post by SteveF on 2006-06-15
[QUOTE=Ramses de Norre]What resolution are you running? The terminal resolution is set by adding a vga=xxx option to your menu.lst, with xxx the code for the resolution you want. I'm not sure this will fix your problem though..[/QUOTE]

Do you mean adding it to my grub menu?  Right now there is not setting like that so I guess I'm running at default.  Also, wouldn't resolution affect the size of the text, not whether or not the text is off-screen?

Thanks,

Steve

---

