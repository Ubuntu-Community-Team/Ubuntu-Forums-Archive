---
title: "Terminator font issue"
date: 2012-09-30
forum: General Help
---

### Post by lektap on 2012-09-30
Hi,

Can't seem to update the font in my terminal program terminator. The font spacing seems to be out. On my ubuntu computer at work this font can be applied without issue so it is something I am doing wrong with my PC here at home.

This is what it looks like with system fixed width font - [http://i.imgur.com/VFucZ.png]("http://i.imgur.com/VFucZ.png")

With arial selected as a font -
[http://i.imgur.com/RSJMo.png]("http://i.imgur.com/RSJMo.png")

Thanks

---

### Post by T.J. on 2012-09-30
The likely reason for space distortion in a terminal is because the font in question is probably designed for variable spacing.  By design, terminals use a font with a fixed spacing - such as monospace - in order to look nice.  The reasoning is that newer terminal windows, like those in Linux, use fixed space fonts by default for maximum compatibility with older terminal screens.

Using a variable spaced font will not do any harm, except that some of the letters will be squished a little bit.  As to why it works at work but not at home - is it the same font version or terminal setup?

---

### Post by lektap on 2012-09-30
You are right when I choose fixed space fonts it looks fine. It is strange that at work I could get variable spaced fonts to appear without jumbling them up.

I will just keep the font to fixed space fonts for the time being though.

Thanks for your help TJ.

---

### Post by T.J. on 2012-10-01
Just a last thought, perhaps your terminal at work has a setting that compensates for variable fonts? Only thing that might make sense if you are using the same font and terminal software.

---

