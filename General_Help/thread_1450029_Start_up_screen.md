---
title: "Start up screen?"
date: 2010-04-08
forum: General Help
---

### Post by gjtoth on 2010-04-08
I'm having a memory relapse.  Can someone tell me what the name of the screen is that shows when I'm first booting Ubuntu?  The one that shows instead of going into verbose, line-by-line dialog?  And, while you're at it, can anyone tell me how to enable it.  I've disabled it somehow.

Thanks.

Oh, yeah.  I'm using 9.04 on a laptop.

---

### Post by dcstar on 2010-04-09
> **gjtoth said:**
> I'm having a memory relapse.  Can someone tell me what the name of the screen is that shows when I'm first booting Ubuntu?  The one that shows instead of going into verbose, line-by-line dialog?  And, while you're at it, can anyone tell me how to enable it.  I've disabled it somehow.

Thanks.

Oh, yeah.  I'm using 9.04 on a laptop.

You are probably referring to the Splash screen, and usually there is a line in each Grub entry about it.

This may also help:

```
sudo update-initramfs -k all -u
```

---

