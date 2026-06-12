---
title: "Transluscent window"
date: 2010-02-16
forum: General Help
---

### Post by Nikias on 2010-02-16
I'm running Ubuntu 9.10 and I've just installed [DROD Archetect's Edition version 1.6.7]("http://forum.caravelgames.com/viewsitepage.php?id=90294"). The install went perfectly fine and the game technically runs correctly as well, in that it opens and plays as it should, however the game renders translucent to the point that it is unplayable. If memory serves I've had this issue in previous versions of Ubuntu as well but never bothered to ask about it. I've attached a screenshot to show what I mean. I don't have this issue with any other program, just DROD.

I'm not sure if it's relevant but when I run DROD from terminal I get

Warning: Couldn't get memory information, assuming it's ok.

But, as I said before, aside from the graphical issue the game runs fine.

Any help would be greatly appreciated, thanks.

---

### Post by pbpersson on 2010-02-16
I have never heard of this game, but according to a [page I found]("http://forum.caravelgames.com/viewtopic.php?TopicID=30496"), many people on different Linux distros are having this problem

---

### Post by Nikias on 2010-02-17
> **pbpersson said:**
> I have never heard of this game, but according to a [page I found]("http://forum.caravelgames.com/viewtopic.php?TopicID=30496"), many people on different Linux distros are having this problem

That is a separate game, DROD RPG, with a newer engine. Also the issue described there is different. That is an in-game glitch causing individual tiles failing to have their transparent regions be rendered as transparent. My issue with DROD Architect's Edition is that the entire game window renders as translucent.

---

### Post by juan.villa on 2010-02-17
Do you have desktop composting on? Have you tried disabling it?

---

### Post by mcduck on 2010-02-17
Install CompizConfig Settings Manager if you haven't got it already, enable the Window Rules-plugin and add your program to the "No ARGB Visuals"-section.

If you need more details about matching windows to Compiz plugins this should help: [http://wiki.compiz.org/WindowMatching]("http://wiki.compiz.org/WindowMatching")

---

### Post by Nikias on 2010-02-17
> **mcduck said:**
> Install CompizConfig Settings Manager if you haven't got it already, enable the Window Rules-plugin and add your program to the "No ARGB Visuals"-section.

If you need more details about matching windows to Compiz plugins this should help: [http://wiki.compiz.org/WindowMatching]("http://wiki.compiz.org/WindowMatching")

That did it. Thanks for your help. I can't imagine what caused this to happen in the first place but I'm glad it's finally fixed.

---

### Post by mcduck on 2010-02-18
> **Nikias said:**
> That did it. Thanks for your help. I can't imagine what caused this to happen in the first place but I'm glad it's finally fixed.

Some programs simply can't handle working in an environment that supports ARGB colors. This happens most often with games and other apps that don't use any of the normal toolkits (GTK, Qt etc.) to draw their graphics.

---

