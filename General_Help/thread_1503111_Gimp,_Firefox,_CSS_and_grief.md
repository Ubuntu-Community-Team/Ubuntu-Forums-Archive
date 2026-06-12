---
title: "Gimp, Firefox, CSS and grief"
date: 2010-06-06
forum: General Help
---

### Post by BigJules on 2010-06-06
Ever have that situation where you doubt your own sanity? A cautionary tale of Linux, but with a happy ending.

Since going with Lucid (good move) noticed that colour graphics produced by the Gimp (2.6.8) were just that bit off, enough to niggle a lot. The default Lucid browser (F'fox 3.6) has a neat plug-in, Colorzilla, which gives a readout of the colour value at the + among other damn useful things. So a trial: got Gimp to produce a test square in #ff0000 (pure red). And Colorzilla read it as #fe000f. Is Gimp doing it wrong? Went to CSS and told it to do the same. Result - this time a pure #ff0000. Tried it every which way - CSS dialled colours new, or those on my old site or other sites, all read correctly, my Gimp stuff rubbish. Conclusive? 

OK - to cut a loooooong story short (cursing Gimp for a moron, removing/expunging/cauterizing, re-installing another ver, importing ICC profiles, using the color-picker etc etc etc) and remembering I'm no techie, I finally stumbled on the answer. 

I was looking at it from the wrong direction. Gimp is totally blameless - the villain in the piece was Firefox, which recently upgraded default color management to true. This overwrote the tagging (or whatever) in the Gimp graphic, controlled the expression of CSS values, fooled Colorzilla and so on. 

So the immediate and simple solution is go to about:config and set gfx.color_management.mode to 0. Gimp has a color management pref, for good measure I set it to 'none' as well. Huzzay! Everything agrees with everything else. Techier heads than mine can move on from this base and mess with profiles, color spaces and the like, I'll stick with sanity.

---

### Post by stderr on 2010-06-06
Thanks for posting this - interesting stuff!

---

