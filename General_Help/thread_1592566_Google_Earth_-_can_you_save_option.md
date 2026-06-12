---
title: "Google Earth - can you save option?"
date: 2010-10-10
forum: General Help
---

### Post by Sepiraph on 2010-10-10
I am running Google Earth on Ubuntu 10.04.  It works fine except if I tried to save specific option, then I get the error upon closing the application:

"Google Earth: Could Not Write File Error "
For more information, click the link below
[http://earth.google.com/support/bin/answer.py?answer=31651&hl=en](http://earth.google.com/support/bin/answer.py?answer=31651&hl=en)

Which unfortunately doesn't have any info.

I am guessing that it has something to do with permission right?  I am launching the program as a default (non-root) user even though I see the googlearth.bin is owned by root.  I tried:

1) Change ownership (chown -R username filename) of the bin file, however same error
2) Try to launch GE using gksudo / sudo which unfortunately opens GE in a rather flicky setting (probably because I built GE using make install)

I also posted this on the GE help forum [http://www.google.com/support/forum/p/earth/thread?tid=4c73b36980d6538a&hl=en](http://www.google.com/support/forum/p/earth/thread?tid=4c73b36980d6538a&hl=en)

---

