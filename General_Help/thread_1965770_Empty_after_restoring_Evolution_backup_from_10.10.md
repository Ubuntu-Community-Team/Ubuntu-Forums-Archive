---
title: "Empty after restoring Evolution backup from 10.10"
date: 2012-04-26
forum: General Help
---

### Post by kabeza on 2012-04-26
Hi
I've installed a blank 11.10 Ubuntu install, and previously I did a Evolution backup by copying the following folders to a safe place

```

~/.evolution
~/.gconf/apps/evolution

```

Now, I downloaded Evolution, started it, put some dummy config, and closed it

```
sudo evolution --force-shutdown && sudo gconftool-2 --shutdown
```

Copied folders, overwrote existing ones, but when I restart Evolution I get nothing, no mails, no contacts, nothing...

Is there any way to restore this info?

Thanks,

---

### Post by kabeza on 2012-04-26
Found a solution

Evolution now stores data in 

```
~/.local/share/evolution
```

So I moved and renamed .evolution folder from backup, into .local/share/evolution and restarted Evolution

When Evolution started for first time, it showed a Window asking me to upgrade mail format. Clicked ok and all went fine. Now I'm fighting with proxy connection but this is another problem.

Please some mod mark as solved. Thanks

---

### Post by dcstar on 2012-04-27
> **kabeza said:**
> 
.........
Please some mod mark as solved. Thanks

There are no "mods" looking at **YOUR** threads, **you** mark it Solved.

---

