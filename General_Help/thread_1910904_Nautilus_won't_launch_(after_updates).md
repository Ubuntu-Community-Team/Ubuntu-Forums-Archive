---
title: "Nautilus won't launch (after updates)"
date: 2012-01-18
forum: General Help
---

### Post by Scoobin on 2012-01-18
Help, I can no longer launch Nautilus. I click on the icon and it just flashes like it's trying to load but doesn't load.

If I try launching from the terminal I get this error:

```
nautilus: error while loading shared libraries:  libnautilus-extension.so.1: cannot open 
shared object file: No such file  or directory
```Anyone know anything about this?

I'm not sure which version of Nautilus it is as I can't query with the command. But I'm running 11.10 with latest updates, and I'm guessing the most recent updates killed it. 

...or it could have been the Unity 5 PPA I removed since it didn't work properly... 

So I guess I'm missing some files or some files or some update has messed things up.

---

### Post by nutr0cker on 2012-01-18
> **Scoobin said:**
> 
...or it could have been the Unity 5 PPA I removed since it didn't work properly... 

Yes, it seems to be the reason, I've got the same problem after downgrading Unity. But I also have no idea how to fix it.

---

### Post by Scoobin on 2012-01-18
I seem to have fixed it.

What worked for me was the this post:
[http://askubuntu.com/a/96445](http://askubuntu.com/a/96445)

But I found I had to follow it exactly and completely. The first time I tried it I started from after the purge since I had already done that. But you need to start from the top - even doing things again that you've already done. Don't skip anything. 

Hope that helps. :)

---

