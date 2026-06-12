---
title: "Evergreen co-editor - howto uninstall?"
date: 2009-09-03
forum: General Help
---

### Post by gf_gollum on 2009-09-03
In my search for a code editor on Ubuntu I tried the evergreen product. It was a .deb file installer - but didn't seem to register itself anywhere for uninstall. Needless to say - I want to uninstall it - and I can't see how. Add/remove and the package manager don't know what I'm talking about - nor does apt-get remove evergreen

How do I neatly remove this?
Thx
Graham

---

### Post by gldearman on 2009-09-03
I've never used Evergreen, but a general tip:

I'm guessing that this is a program you installed from source?

Have you tried navigating to the directory containing the Evergreen makefile and typing:

```
make uninstall
```

(You may or may not be required to prefix that with sudo, depending on how you installed it.)

---

### Post by gf_gollum on 2009-09-05
nope - i didn't build it from source - it was a binary distribution. Ok - I'll delete the program folder just to free up the space and tidy the menus by hand. I can't break anything that way  can I?
Graham

---

### Post by gf_gollum on 2009-09-06
I figured it out.. the original package name wasn't the same as the program name. once I removed the package org.jessies.evergreen - rather than just evergreen - it worked just fine. Another thing learnt!
Graham

---

