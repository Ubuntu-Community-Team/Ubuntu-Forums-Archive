---
title: "dependencies and computer janitor"
date: 2011-02-03
forum: General Help
---

### Post by musendrophilus on 2011-02-03
Good day! I went to run Computer Janitor, it mentioned a few lib files for deletion but it also said it was going to remove Opera which I downloaded two days ago.
I'm not going to remove Opera but I want to be absolutely certain these libraries are truly orphaned so I don't break another program. What command would I run?

---

### Post by TeoBigusGeekus on 2011-02-03
Have you tried
```
sudo apt-get autoremove
```
?

---

### Post by Rubi1200 on 2011-02-03
I suggest you avoid Computer Janitor; as you have seen it is likely to remove things that it shouldn't!!!

Use commands like these to keep things clean:

```
sudo apt-get autoclean

sudo apt-get clean
```

Linux does not accumulate junk the way, for example, Windows does and the potential loss by using Computer Janitor will not be offset by gaining a few hundred MB of extra space (at most).

---

### Post by mike555 on 2011-02-03
I  uninstall Computer Janitor first thing .........

---

### Post by Rubi1200 on 2011-02-03
> **mike555 said:**
> I  uninstall Computer Janitor first thing .........
:-)

It's the second thing I uninstall, right after remote desktop!

---

