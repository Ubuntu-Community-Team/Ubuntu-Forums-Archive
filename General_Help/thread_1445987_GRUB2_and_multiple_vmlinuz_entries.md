---
title: "GRUB2 and multiple vmlinuz entries"
date: 2010-04-03
forum: General Help
---

### Post by pc.huff on 2010-04-03
Okay, I'm a noob but enjoying dual booting.

However, every time I run update manager I get a new vmlinuz entry and now I have multiple boot options in my grub boot menu.  Now when I have like 5 ubuntu entries to move past to select Windows.  and the latest Ubuntu is always at the bottom so I have to annoyingly scroll down to select the latest there.

I don't really understand what the vmlinuzXXX entries in the boot folder are for so I don't want to delete them.  I've thought about editing the loop in the 10_linux file in the grub.d folder but it looks like its calling a function or macro or something:

```
linux='version_find_latest $list'
```But like I said, I'm a noob to all this (a .Net developer on Windows professionally) and don't understand where this is.  It looks like this function call has the logic I need to fix.  Because its not finding the latest, its just finding all.

How to I get back to one Ubunutu boot option like when I first installed?

Thanks!

---

### Post by efflandt on 2010-04-03
Not sure what you changed, but usually the most recent (newest) Linux version ends up at the top of the grub2 menu list.

To remove old kernels open Synaptic and type **linux** into Quick Search.  For **linux-generic** and **linux-headers** for the versions you want to remove, "Mark for complete removal".  But make certain which versions you are removing.

You should keep the current version unless that is giving you trouble.  And people usually keep a previous version just in case something crops up with the current version.

---

### Post by pc.huff on 2010-04-06
Awesome, thanks for your reply.  I'll give this a shot this weekend.  I'm crazy busy with work so haven't had time to think about this again.  I'll keep everyone posted on how it works.  Thanks again!

---

### Post by pc.huff on 2010-05-05
That worked like a charm.  Thanks.  Man, I was making that complicated, didn't realize how easy that was.  Gotta keep learning.

Thanks!

---

### Post by dino99 on 2010-05-05
Ubuntu is Magic  :p

---

