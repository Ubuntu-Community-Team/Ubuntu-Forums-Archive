---
title: "ps2eps - bounding box problems"
date: 2009-11-20
forum: General Help
---

### Post by engine on 2009-11-20
I'm using mup to create small (one or two lines of music per file) .ps files of music examples. The output sits neatly at the top of an A4 page.

Then I use ps2eps 1.64 to make .eps files so I can insert the examples in OpenOffice documents.

Problem: ps2eps often misses the bottom line in the last stave, or the bottom of the lowest note.

Question: is there a different way of making the .eps files I need?

Observation: ps2png, not that I want to downgrade to bitmapped graphics, reports

```
/usr/bin/ps2png: 18: pnmcrop: not found
/usr/bin/ps2png: 18: pnmmargin: not found
/usr/bin/ps2png: 18: pnmtopng: not found

```
and generates no output file. Related?

---

