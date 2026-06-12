---
title: "After grub update &quot;loadfront&quot; not found"
date: 2010-11-28
forum: General Help
---

### Post by phflupp on 2010-11-28
I foolishly let Ubuntu update grub yesterday on my Wubi installation and now cannot boot:

First I get the error:

Error: unknown command - loadfront
Error: File not found

...then the system reboots almost immediately so there is no chance to get to the grub prompt.


I assume my choices are 1) restore from backup (I have one) or 2) boot from a LiveCD and edit grub (I don't know what changes to make).

But I would rather be able to update grub in the future along with other Ubuntu updates, so I'm really hoping someone knows what the error is in this last update and whether it will be fixed.

Thanks in advance,
-P.
ps: Dear Ubuntu/grub coders - please test your work before sending out updates, thx.

---

### Post by restorator on 2010-11-28
Try reading [this]("http://ubuntuforums.org/showthread.php?t=1195275") see if that helps you out.

---

### Post by Rubi1200 on 2010-11-28
There are problems with GRUB updates and Wubi installs at the moment on both 10.04 and 10.10 versions.

See here for a description of the problem and possible solutions:
[http://ubuntuforums.org/showpost.php?p=10159040&postcount=5](http://ubuntuforums.org/showpost.php?p=10159040&postcount=5)

Forum member bcbc currently recommends locking the GRUB and lupin versions in Synaptic to prevent this happening.

---

### Post by phflupp on 2010-11-30
Great... this does it.

Shameful lack of coordination between Wubi folks and Grub folks, though. Let me know when THAT one can be marked SOLVED. ;-)

---

