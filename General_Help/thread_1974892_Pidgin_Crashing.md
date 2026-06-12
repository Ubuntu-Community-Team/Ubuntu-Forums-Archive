---
title: "Pidgin Crashing"
date: 2012-05-06
forum: General Help
---

### Post by yahoowizard on 2012-05-06
So, I upgraded twice two days ago from 11.04 to 12.04, and now, Pidgin is frequently crashing. Every 20 minutes or so, the chat window would just stop, freeze, gray out, and then allow me to force quit out of it. I tried removing then reinstalling it, but the same problem happens, and not sure where to go with this since Empathy isn't too good for me overall. 

Maybe if there was a way for me to completely uninstall it, which I know how to do with Windows, but unfamiliar with Ubuntu. Would it be the same, where I would
1. Remove Pidgin
2. Delete all the files it has
3. Install again?

But then again, not sure if that's going to help entirely yet, so x.x

---

### Post by Erik1984 on 2012-05-06
To remove a program together with configuration files in your home directory use purge. The following commands can be used in the terminal.

```
sudo apt-get purge pidgin
```install again with:
```
sudo apt-get install pidgin
```

---

### Post by yahoowizard on 2012-05-06
Thanks a lot, but yeah, that didn't do anything much. Or at least, didn't go through a hard uninstall, only took care of a few of the things on there. And after reinstalling, it still crashes so not much progress.

---

### Post by yahoowizard on 2012-05-08
Bump?

---

