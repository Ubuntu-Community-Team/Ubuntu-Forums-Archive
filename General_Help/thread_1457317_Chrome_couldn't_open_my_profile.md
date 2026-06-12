---
title: "Chrome couldn't open my profile"
date: 2010-04-18
forum: General Help
---

### Post by Crazy K on 2010-04-18
I searched the forums about this issue and found something similar but it didn't work. Here's the problem, when I start up google chrome it gives me two warnings (the same one though) Check the attachment for what I mean. I have the bookmark bar up as you can see, and none of the icons to the bookmarks show up. 

So what can be the problem?

Btw, is this helps I'm using 5.0.342.9 beta of Chrome.

Disregard this thread, all I did was type this in, now it works. 

```
rm -rf ~/.config/google-chrome/Default
cp -R ~/.config/google-chrome/Backup ~/.config/google-chrome/Default
```

---

### Post by arroyocallejas on 2012-12-20
cp: cannot stat `/home/jcac/.config/google-chrome/Backup': No such file or directory

---

### Post by Matt12334 on 2012-12-20
This happens to me on occasion, and the only solution I could figure out is the one that most people are unwilling to try... Reboot your computer, and it should function normally. :)

---

