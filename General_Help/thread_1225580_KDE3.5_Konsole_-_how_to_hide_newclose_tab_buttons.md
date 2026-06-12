---
title: "KDE3.5 Konsole - how to hide new/close tab buttons?"
date: 2009-07-28
forum: General Help
---

### Post by Swords on 2009-07-28
Title says it all. I found a hidden option to do this in konqueror using google, but no such luck for konsole. I'd really like to keep my tab bars consistent and also unclutter my limited tab space.

---

### Post by Swords on 2009-07-29
Since it seems there isn't any option for it, I decided to go ahead and dive into dcop and do it myself. This requires konsole to be running with --script for the qt bridge.
```
#!/bin/sh
session=`dcop konsole* | head -1`
IFS=$'\n'
for i in `dcop $session qt objects | grep QToolButton`; do
	dcop $session "$i" hide
done
```
Just change 'hide' to 'show' to bring them back. Now I just need a way to make this run every time I start konsole. I'll probably just make a new session that runs it and add it to my profile.

---

