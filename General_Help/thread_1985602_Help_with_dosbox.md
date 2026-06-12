---
title: "Help with dosbox"
date: 2012-05-23
forum: General Help
---

### Post by stalkingwolf on 2012-05-23
I am running gwbasic in dosbox.  CTRL+C and CTRL+Break dont work.
From what i have read i need to apply 2 patches to dosbox.  It seems they must be applied to the source code.  I have the source code and the patches
but have no idea how to proceed.

Can anyone help?

---

### Post by MG&amp;TL on 2012-05-23
You probably want to read this: [http://www.linuxtutorialblog.com/post/introduction-using-diff-and-patch-tutorial]("http://www.linuxtutorialblog.com/post/introduction-using-diff-and-patch-tutorial")

and possibly:

```
man patch
```

Essentially, use the *patch* command to apply the patch to your files.

---

### Post by stalkingwolf on 2012-05-24
thanks ill give both a read

---

### Post by stalkingwolf on 2012-05-25
while reading , preparing to try the patch i discovered that the patch wasnt needed just the proper key combination.  to end a running program in dosbox it has changed to ctrl+scrollbreak.

---

