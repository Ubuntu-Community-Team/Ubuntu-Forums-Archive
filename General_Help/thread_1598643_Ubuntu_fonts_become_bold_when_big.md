---
title: "Ubuntu fonts become bold when big"
date: 2010-10-16
forum: General Help
---

### Post by davidY on 2010-10-16
Hi,

Does anybody notice that in ubuntu fonts do not scale up smoothly?

Try it out - press [ctrl and +] to increase font size in firefox use [ctrl and 0] to reset size. At some font size all font will suddenly seem bold - no transition - it just becomes thick.

It seems like the hinting suddenly gets turned off. Or alternatively the font width goes from 1px -> 3px. Or alternatively subpixel rendering gets disabled.

This is an issue from a usability point of view, because my vision is not good, so I need larger default font size, but when the fonts go to a certain size it is all bold and hard to stare at. Even the new Ubuntu font suffers from this issue.

Edit:
Noticed that when hinting is on, the font becomes sharp because it uses only one pixel (ie lines up to the pixel grid). This means that it has to snap between one and two pixel sized text. Is there any way to use one pixel width text at higher font sizes?

Edit 2:
I use full hinting so i guess thats why

---

