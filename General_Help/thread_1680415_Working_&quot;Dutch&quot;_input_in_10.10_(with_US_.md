---
title: "Working &quot;Dutch&quot; input in 10.10? (with US keyboard layout)"
date: 2011-02-02
forum: General Help
---

### Post by LBoksha on 2011-02-02
I've recently installed Maverick Meerkat, everything's working fine but I can't get the input working properly. Under Windows (and, if I remember correctly, Hardy Heron) I've always used the US keyboard layout (which is the layout of my keyboard, and the common layout in the Netherlands) and Dutch as input language.
This allows easy input of éóú etc. by hitting '+vowel but interprets the apostrophe as an actual apostrophe when it's followed by a letter that can't be accented; for example when typing "we're", you can just type W E ' R E.

The problem in Meerkat is that if I try that with my current keyboard layout (USA international with dead keys) I get "we&#341;e". In order to get the apostrophe right I now need to type W E ' space R. In addition, when I now try to add an apostrophe before a T, nothing happens and I get neither an apostrophe OR a T. Needless to say, this wreaks havoc with my typing.

I've tried looking for a solution and the closest I could find was 
[http://ubuntuforums.org/showthread.php?t=1451209](http://ubuntuforums.org/showthread.php?t=1451209)
which was set to "SOLVED" when someone pointed to a guide to make your own keyboard layouts:
[http://ubuntuforums.org/showthread.php?t=188761](http://ubuntuforums.org/showthread.php?t=188761)

I've read the guide, but from what I've seen, apparently by just editing keyboard layouts it's nigh impossible to make things work like I'm used to; in particular, to get '+T to result in 't, that combination would have to be separately added to the combine file and in fact, this would have to be done for every single combination of a diacritical and a letter above which that diacritical should not appear. (deleting old instances of &#324;&#341;&#7811;, etc. while taking care not to delete common diacritical combinations that do make sense like ñ)

Is there any simple way to get this to work like it did before in older versions of Ubuntu and does in Windows? How?

Thanks!

---

