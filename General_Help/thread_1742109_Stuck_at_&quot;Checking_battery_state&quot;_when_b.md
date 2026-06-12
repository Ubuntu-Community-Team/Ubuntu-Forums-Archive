---
title: "Stuck at &quot;Checking battery state&quot; when booting"
date: 2011-04-28
forum: General Help
---

### Post by t36 on 2011-04-28
Is there a way to permanently fix this bug?

Thanks

---

### Post by flyingsolow on 2011-04-28
In the same situation and not too sure how to resolve this.

---

### Post by x C0MMAND0 x on 2011-04-28
I have been having this issue recently too (running 10.10 64bit).  No resolution.  Seems to happen every few boot cycles.

---

### Post by t36 on 2011-04-29
Apparently the answer for my problem is to reinstall the graphics driver. Thanks for the replies.

---

### Post by vks_foe on 2011-05-02
its a prb with graphics driver.

press ctrl+alt+f1 to get a terminal
login as root

try following commands :
"/etc/init.d/gdm restart"

or 
"/etc/init.d/kdm restart"

follow what pops up...
this worked for me.

---

