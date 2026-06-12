---
title: "rsync makes system unusably slow"
date: 2010-04-21
forum: General Help
---

### Post by ExquisiteDeadGuy on 2010-04-21
Is there a way to make rsync play nice with the rest of the system? When I run it, it does so much disk access that the rest of the system slows to a crawl to the point that all applications "grey out" and the mouse cursor doesn't even move smoothly.

I've tried running it with nice -n 19, but it makes no difference as I think it's the constant disk access that's slowing everything down and not the CPU time.

Is there a way to make rsync run at a slower pace so that even though the backup may take longer, I can still use the system while it's going on?

Thanks!

---

### Post by gmargo on 2010-04-21
Try the --bwlimit option.

---

### Post by bwitherell on 2010-04-21
Are you rsyncing changes only or everything?

---

### Post by ExquisiteDeadGuy on 2010-04-22
> **gmargo said:**
> Try the --bwlimit option.

Thanks for the tip. Reading the manpage, it looks like that's only applicable when running in daemon mode, this is happening on a client machine not running in daemon mode.


> **bwitherell said:**
> Are you rsyncing changes only or everything?

Either way makes the machine slow way down, syncing everything is much worse of course. It's not an old machine either.

---

### Post by DeMus on 2010-04-22
> **ExquisiteDeadGuy said:**
> Is there a way to make rsync play nice with the rest of the system? When I run it, it does so much disk access that the rest of the system slows to a crawl to the point that all applications "grey out" and the mouse cursor doesn't even move smoothly.

I've tried running it with nice -n 19, but it makes no difference as I think it's the constant disk access that's slowing everything down and not the CPU time.

Is there a way to make rsync run at a slower pace so that even though the backup may take longer, I can still use the system while it's going on?

Thanks!

Not that this will help you, but I still wanted to let you know it does not only happen with rsync. I have the same problem when using Archive manager to unrar a whole series of rar files. Because of the disc access the pc is almost standing still for all other programs. When I look at System monitor I see it is definitely not the CPU which is doing a max of 20%.
Is there a way to share more between programs or is one always taking what it needs to run maximal leaving the others doing nothing?

---

### Post by gmargo on 2010-04-22
> **ExquisiteDeadGuy said:**
> Reading the manpage, it looks like that's only applicable when running in daemon mode, this is happening on a client machine not running in daemon mode.


Not true; it it applicable to the client as well - the man page mentions it in two distinct places.  I always use it to avoid saturating my wimpy DSL line.  Whether it will help with disk-to-disk transfers I don't know.

---

### Post by ExquisiteDeadGuy on 2010-04-22
> **gmargo said:**
> Not true; it it applicable to the client as well - the man page mentions it in two distinct places.  I always use it to avoid saturating my wimpy DSL line.  Whether it will help with disk-to-disk transfers I don't know.

Great, thanks! I must've overlooked that. I'll give it a try.

---

