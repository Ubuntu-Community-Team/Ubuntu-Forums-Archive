---
title: "Stumped by debuild manpage"
date: 2009-10-05
forum: General Help
---

### Post by markseger on 2009-10-05
When I look at the manpage it feels like it was written for a different command because it doesn't list the switches I've been told to use.  Even debuild -h doesn't show them.  The specific command I'm trying to use is "debuild -S -sa" and it runs just find but I can't tell what they mean.

Actually -S is casually mentioned in the text writeup as being used if you want a source package.  -sa is shown in an example but no description of what it does.  Further, in the very first example the command "debuild -i -us -uc -b" is given and most of those switches aren't described anywhere either.

What I really want to do is disable signing and I found another example also using -us and -uc and neither of those are described anywhere either so I don't know which (or if both) need to be specified.

Is there some other way to get a list of ALL switches?

-mark

---

### Post by geirha on 2009-10-05
```

EXAMPLES
       To build your own package, simply run debuild from  inside  the  source
       tree.  dpkg-buildpackage(1) options may be given on the command line.

```

So apparently, if debuild doesn't recognize an option, it passes it on to dpkg-buildpackage.

---

### Post by markseger on 2009-10-05
ahhhhhhh...  right in front on me, but I still managed to miss it.
thanks
-mark

---

