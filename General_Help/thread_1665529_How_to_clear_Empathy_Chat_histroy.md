---
title: "How to clear Empathy Chat histroy?"
date: 2011-01-12
forum: General Help
---

### Post by aisajib on 2011-01-12
Hi everyone! I'm an Ubuntu user and I always chat on Yahoo, MSN, Gtalk and Facebook accounts using Empathy (with the fact that there is no better alternative; pidgin is heavy for me). I have noticed long earlier that all the chat histories are saved. However, just today I discovered that I couldn't delete those histories. :o Hitting the clear option from the right click fly out menu doesn't permanently remove the history. I can see them again when I try to look for previous conversations.

I believe there is a way to permanently remove chat histories from Empathy. Anyone could help me out with this?

---

### Post by sum1nil on 2011-01-12
Are the logs being stored in a . directory in your home folder?

You may have to show hidden files on nautilus to see the . directories and then manually clear out any logs (careful though to check if they are settings and not conversations).

I'm not sure this is correct; just a thought. I'd try it myself first but don't use the program.

:)

---

### Post by aisajib on 2011-01-12
Thanks for your reply. I looked through the home folder but there is no directory such as .empathy or similar.

---

### Post by howefield on 2011-01-12
If I recall correctly, the path to the logs is

```
~/.local/share/Empathy/logs/
```

PS. and for info, The version in Maverick has an option not to save logs.

---

### Post by aisajib on 2011-01-12
He he you remember correct! ;)

The reason I'm not updating is it's not an LTS. However, i'm pretty disappointed with Unity being the primary desktop environment.

By the way, that worked perfect. Thank you so much. :)

---

### Post by howefield on 2011-01-12
> **aisajib said:**
> The reason I'm not updating is it's not an LTS.

A good reason :)

> However, i'm pretty disappointed with Unity being the primary desktop environment.

Again just for info, Unity isn't the default or primary environment in 10.10, it will be for 11.04 but even then it will be a very simple task to select the standard gnome environment from the session menu.

Don't want to deviate from your original question, just for info :)

> By the way, that worked perfect. Thank you so much. :)

Any time, my memory isn't so bad after all.

---

