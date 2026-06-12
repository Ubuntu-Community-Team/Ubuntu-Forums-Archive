---
title: "Evolution hangs"
date: 2011-05-09
forum: General Help
---

### Post by ziekfiguur on 2011-05-09
Hello everyone,

Ever since i upgraded to natty i have a problem. Whenever i ask 
evolution to fetch my rss feeds, it hangs and starts taking up 99% op 
my processor capacity. This wouldn't be so bad, if only evolution 
wouldn't crash every time i try to export my feed list (that part is a 
know problem).

So, does anyone have an idea what causes evolution to block, or how to 
fix it?

---

### Post by Ghost_Mazal on 2011-05-09
Don't know a fix fro your problem , just a suggestion.

Why not look into LifeRea as a RSS feed reader. It works very well.

---

### Post by ziekfiguur on 2011-05-09
Thanks for the tip, my problem with doing that was that i couldn't export my feed list from evolution, so i had to add every feed manually to a new reader (and i'm lazy :p)
But, i've come to the conclusion that that might still be the best option.

If anyone ever has the same problem, here's a python script to get the urls of your feeds from evolution:
[PHP]#!/usr/bin/env python

import re
import os.path

for l in open(
            os.path.expanduser(
                '~/.gconf/apps/evolution/evolution-rss/%gconf.xml')):
    m = re.search(r'(http.*?)&lt;', l)
    if m is not None:
        print m.group(1)
[/PHP]

---

