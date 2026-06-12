---
title: "Ubuntu ate my hard drive! Is it possible to save corrupted hd?"
date: 2006-04-08
forum: General Help
---

### Post by excelsior on 2006-04-08
Ubuntu crashed this Friday, and now the Hard Drive is so messed up I can't even format it, much less run my OS.
 1) Do big crashes happen very often to you guys? Or am I doing something wrong maintainence-wise?

2)Is there any way I can salvage the Hard Drive? It's not partitioned or anything, just one HD dedicated to ubuntu.

---

### Post by trent dillman on 2006-04-09
Can you mount with a live cd?

---

### Post by jpkotta on 2006-04-09
> Ubuntu crashed this Friday, and now the Hard Drive is so messed up I can't even format it, much less run my OS.
 1) Do big crashes happen very often to you guys? Or am I doing something wrong maintainence-wise?


No.  I've never had Ubuntu crash after about about a month of first installing it on my desktop.  I reboot every 1-2 months.  I can easily crash my laptop because I use buggy, closed ATI drivers.  

I have no idea what you did or didn't do, maybe it's your fault, maybe it's something beyond your control.

> 
2)Is there any way I can salvage the Hard Drive? It's not partitioned or anything, just one HD dedicated to ubuntu.

Boot from the Live CD.  If it can't find the HD, the HD probably failed.  There are ways of recovering a dead HD, but they tend to be very expensive.  Always backup your data, because HDs fail.

You can mount the HD from the Live CD with something like```
mount /dev/hda1 /mnt
```

---

### Post by excelsior on 2006-04-09
<quote>I can easily crash my laptop because I use buggy, closed ATI drivers.
</quote>
Hmm... i use a laptop.
What are ATI drivers?

And would it help or hinder stability if I kept it on all the time?

Oh, and I did try the live CD. Couldn't even start the liveCD, it was that bad.
Thanks anyway

---

