---
title: "Nautilus shows text files as Adobe Bridge Workspace Files"
date: 2009-11-12
forum: General Help
---

### Post by blur xc on 2009-11-12
Hey- a while back I tried installing Photoshop and Lightroom in Wine and ever since nautilus lists all text files as Adobe Bridge Workspace Files...  This is a bit annoying.  Is there some way to fix it?  I've already removed Wine and all wine programs in the .wine directory.  

Any help would be appreciated...

Thanks,
BM


ps...  here's a screenshot of what I'm talking about...

---

### Post by coldReactive on 2009-11-12
install wine again, then sudo apt-get purge wine rather than sudo apt-get remove.

purge deletes all the configurations, even those that aren't in the .wine directory.

See if that helps.

---

### Post by blur xc on 2009-11-13
Thanks- But I should have mentioned that I did purge wine w/ apt-get purge when I removed it.  My bad...

BM

---

### Post by Dave M G on 2010-08-28
A bit late perhaps, but since this thread comes up first in Google when looking for answers to this problem, I thought I'd post the solution.

There are some files in the ~/.local/share/mime/packages directory that begin with "x-wine". You can search within those for mentions of "Adobe Bridge Workspace File". Remove those entries, and then run:

```
update-mime-database ~/.local/share/mime
```

You may or may not have to restart Nautilus for the effect to take place.

You can see a complete thread on the topic, with the solution, here:

[http://lists.tlug.jp/ML/1008/msg00169.html]("http://lists.tlug.jp/ML/1008/msg00169.html")

Hope that helps others get rid of this minor annoyance!

---

