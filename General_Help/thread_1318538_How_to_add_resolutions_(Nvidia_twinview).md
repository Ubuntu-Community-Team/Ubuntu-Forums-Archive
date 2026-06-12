---
title: "How to add resolutions (Nvidia twinview)?"
date: 2009-11-07
forum: General Help
---

### Post by spoon_ on 2009-11-07
I'm running Nvidia twinview with two monitors, and whenever I launch a 3D game like etuxracer, the only resolutions I can pick is 3520x1200 (though sometimes 800x600 is also offered). How do I get some more choices? I tried adding "modes" to the display subsection of xorg.conf but nothing has changed...

Thanks.

---

### Post by spoon_ on 2009-11-07
bump?

---

### Post by Bluekkis on 2009-11-08
You need to add twinview metamodes to xorg.conf. Syntax is detailed in nvidia driver release note appendixes, but here is my line for reference.

```
Option "metamodes" "DFP-0: 1920x1200 +0+0, DFP-1: 1600x1200 +1920+0; DFP-0: 1920x1200; DFP-0: 1600x1200; DFP-0: 1680x1050; DFP-0: 1280x960; DFP-0: 1280x800; DFP-0: 1024x768; DFP-0: 800x600; DFP-0: 640x480"
```

---

### Post by spoon_ on 2009-11-08
That works, thanks!

---

