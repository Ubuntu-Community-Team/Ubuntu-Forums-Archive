---
title: "Fspot Crashes on Printing (10.10)"
date: 2011-06-25
forum: General Help
---

### Post by BarryM on 2011-06-25
I have just upgraded to 10.10 and find that, if I attempt to print or print preview fspot crashes as soon as I click the print button in the printer dialog box. From previous posts it looks as if this problem was identified at the testing stage. has anyone got any suggestions for dealing with this? If not it seems that the only way I can get a decent print is by using Gimp. I have tried Shotwell and found that it does not print correctly, and in any case is markedly inferior to fspot, which begs the question why Canonical no longer support it! I hope I am not going to have to use the unmentionable operating system to print photos!

---

### Post by eric-yorba on 2011-06-28
> **BarryM said:**
> ...fspot crashes as soon as I click the print button in the printer dialog box.
> **BarryM said:**
> ...which begs the question why Canonical no longer support it!

I think you answered your own question. :P

What problems are you having printing from Shotwell?

---

### Post by BarryM on 2011-06-29
In a word, printing. Shotwell does not seem to have the flexibility that fspot had. If I try to print a 4:3 ratio photo (Olympus format, jpeg, high resolution) on 6"x4" paper, it prints the whole picture, whereas fspot had an option to slice off the outer long edges to make it fit. I tried trimming a picture to 3:2 ratio, and it then printed the whole trimmed picture, but at reduced size so that I have wide margins left, right and bottom but not top.

I have an HP C5180 printer with the usual HPLIP driver.

---

### Post by eric-yorba on 2011-06-30
Where do you see this option in F-Spot? Maybe I'm running a different version, but I'm not seeing that.

---

### Post by BarryM on 2011-06-30
In the Print dialog box, Image Settings (middle tab). You are presented with options:
Full Page (no margins) - Check box
Zoom/Fill/Scaled  - radio buttons
White Margins - Check box

Full Page only worked if you also selected printout mode Photo (on photo paper) in the Advanced tab dialog, otherwise you got white margins.
Selecting Zoom in the Zoom/Fill/Scaled gives full width with top and bottom cut off.

The paper selection in the Advanced tab may be specific to HP printers, but the Image Settings seem not to be printer specific.

I am using Fspot 0.8.0. I have to say that on first impressions, Fspot seems more versatile than Shotwell.

---

### Post by eric-yorba on 2011-06-30
There's definitely some features we're missing that F-Spot has.

Anyhow, I filed a ticket for this feature:
[http://trac.yorba.org/ticket/3789](http://trac.yorba.org/ticket/3789)

Feel free to comment and/or add yourself to the CC list if you like.

---

