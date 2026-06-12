---
title: "Problems with chinese language"
date: 2011-04-26
forum: General Help
---

### Post by Rob8900 on 2011-04-26
I'm using xubuntu 10.10 and wine 1.0.

When i choose chineese in my program everything is translated right. But when i restart my pc some items are not translated anymore in my program. English, Russian, German, ... translations works fine.

Upgrading of wine or xubuntu are no option.

Any idee someone?

---

### Post by idoitprone on 2011-04-26
Did you ever try symlink your system fonts to your wine fonts?

---

### Post by Rob8900 on 2011-04-27
What do you mean with symlink?

---

### Post by Rob8900 on 2011-04-27
> **idoitprone said:**
> Did you ever try symlink your system fonts to your wine fonts?

What do you mean with symlink?

---

### Post by idoitprone on 2011-04-27
Read this link and you will understand
[http://en.wikipedia.org/wiki/Symbolic_link](http://en.wikipedia.org/wiki/Symbolic_link)

Basically what I want you to do is symlink your system font to your wine fonts folder. This way wine will access your fonts.
I do not have Ubuntu at this moment, so i want you to run some commands.

locate the wine font folder
```
sudo find / -name fonts
```

what type of chinese fonts do you use ttf?
You can either do two things go through synaptic and find the files through the install files list or 
```
sudo find / -name *.tff

```
hope it picks up those chinese fonts

when you find all the files

```
sudo ln -s /path/to/chinese/fonts.ttf /path/to/wine/fonts/
```

---

