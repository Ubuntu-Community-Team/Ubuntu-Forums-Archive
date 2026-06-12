---
title: "Users and Groups"
date: 2010-01-11
forum: General Help
---

### Post by warfacegod on 2010-01-11
Ubuntu 9.10 will not display usernames in Users and Groups. Yes, I clicked the keys icon to make changes. Hence, if username is not diplayed, I cannot modify user account permissions. I've searched the forum rather extensively and can only find one mention of this.

hakimoerton's thread:

[http://ubuntuforums.org/showthread.php?t=1371417]("http://ubuntuforums.org/showthread.php?t=1371417")

I'm already there trying to help him with his hard drive and now believe it has to do with the same problem I'm having on my other computer.

P.S. Please disregard hakimoerton's crankiness, he's really an alright guy!

---

### Post by Leppie on 2010-01-11
well, as i stated there too, you can always revert to the cli... :P

---

### Post by warfacegod on 2010-01-11
Forgot about that CLI thing.

---

### Post by Leppie on 2010-01-11
try completely removing the system tools:
```
sudo apt-get purge gnome-system-tools
sudo apt-get install gnome-system-tools
```

---

### Post by warfacegod on 2010-01-11
> **Leppie said:**
> try completely removing the system tools:
```
sudo apt-get purge gnome-system-tools
sudo apt-get install gnome-system-tools
```

That didn't work. Although, it did make root appear so that was better than it was before.

This did though.

Go to Applications> System Tools> Configuration Editor> apps> gnome-system-tools> users and check show all.

Thanks Leppie.

---

### Post by Leppie on 2010-01-11
> **warfacegod said:**
> That didn't work. Although, it did make root appear so that was better than it was before.

This did though.

Go to Applications> System Tools> Configuration Editor> apps> gnome-system-tools> users and check show all.

Thanks Leppie.

haha, didn't know you could even hide the users simply like that. good to know, thanks ;)

---

### Post by warfacegod on 2010-01-11
Certainly.

---

