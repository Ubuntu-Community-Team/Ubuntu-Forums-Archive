---
title: "Sorted unicode blocks in character map?"
date: 2010-06-26
forum: General Help
---

### Post by DarkerStar on 2010-06-26
When I switched from Karmic to Lucid, one thing that changed is the Character Map application. In Karmic, when I selected View->By Unicode Block, what I would get on the left is a list of Unicode blocks in logical order. At the top would be "All", then "Basic Latin", then "Latin-1 Supplement" and so on. Basically, after "All", each Unicode block would be listed in order by the range in the block. This was handy because it meant that the blocks with the lowest code points were at the top.

Now, in Lucid, the Unicode blocks are listed by alphabetical order, after "All". So it goes "All", "Aegean Numbers" (!), then "Alphabetic Presentation Forms" (ligatures and so on), then "Ancient Greek Musical Notation" (!!), and so on. "Basic Latin" shows up in the B's, of course, and "Latin-1 Supplement" is way down.

i couldn't find any info that clearly told me whether this change was intentional or not. There is [a bug filed that sounds suspiciously relevant](https://bugs.launchpad.net/ubuntu/+source/gucharmap/+bug/479330), but i would hardly call ordering Unicode blocks by... **Unicode**... "*jumbled in no discernible order or relation*", so i'm not sure.

Does anyone know if there is a way to get back the old behaviour? The documentation isn't particularly helpful.

---

