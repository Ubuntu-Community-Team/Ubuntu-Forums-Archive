---
title: "Is there a /dev/ file associated with virtual drives/mounted ISOs?"
date: 2009-08-19
forum: General Help
---

### Post by Doval on 2009-08-19
I'm trying to get ePSXe to load a mounted ISO (I'm aware that ePSXe can run the ISO as-is without mounting, but this one particular game seems to give trouble unless it's running as a virtual drive first.) Problem is, ePSXe asks for the /dev/ file of the CD Drive, not the mount point. Is there a /dev/ file associated with mounted ISOs/virtual drives that I could put into ePSXe to get it to read the ISO I'm mounting?

I realize the question is partially game-related but I didn't get any answer at all in the Game subsection, and the issue I'm trying to resolve is somewhat technical, so I thought it would be OK to try here instead.

---

### Post by Doval on 2009-08-19
Thread's already down to the 6th page without an answer, so gonna bump.

---

### Post by phinullfermata on 2009-08-19
After some digging, I found this command:
```
losetup /dev/loop0 example.img

```

Although I haven't tried this, what this does is provide a /dev file for an image you give, which seems to be what you're looking for.  For more info I'd see the man page.

Hope this helps!

---

