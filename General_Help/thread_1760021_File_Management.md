---
title: "File Management?"
date: 2011-05-16
forum: General Help
---

### Post by UncleMonty on 2011-05-16
I want to have movie files only on my main PC. Is there any simple way of collecting together all document files and similar?

---

### Post by TeoBigusGeekus on 2011-05-16
Could you please explain a bit more about what you want to do?

---

### Post by mikewhatever on 2011-05-16
You could use the 'find' command, but I wouldn't call it simple. To get you started, the following will look for and move all .txt file in your home directory to Documents:

```
find ~ -name '*.txt' -execdir mv '{}' ~/Documents \;
```

...or all .pdf files:
```
find ~ -name '*.pdf' -execdir mv '{}' ~/Documents \;
```

---

### Post by UncleMonty on 2011-05-16
> **TeoBigusGeekus said:**
> Could you please explain a bit more about what you want to do?

Sorry my post wasn't that clear. Basically I have countless word documents scattered all over the harddrive and I basically want to round them all up into a single folder. I would like to do the same with photos and the like.

---

