---
title: "find space convertion"
date: 2011-03-09
forum: General Help
---

### Post by cbob on 2011-03-09
Hello,
I'm trying to copy all my photos from a windows drive to my Linux partition. So i created this small one-liner:
```
$ cp -f `find -not -iname "thumbs.db" -type f -printf "%p\n"` /home/b/Pictures/

```But the output from find has no space esc-character, i.e. [FONT=Courier New]/path/sub folder[/FONT] should be [FONT=Courier New]/path/sub\ folder[/FONT].
Anybody have a quick fix for this?

/cbob

---

### Post by cbob on 2011-03-09
I changed my mind to
```
find -iname "thumbs.db" -type f -exec rm -f {} \; ; rsync -pr --existing . /home/b/Pictures
```but would still like to know if there is a way to print esc-space in [FONT=Courier New]find[/FONT].

/cbob

---

### Post by tordeu on 2011-03-09
You could simply put the ouput of find into quotes. This would not escape the spaces, but it would solve the problem.

```
$ cp -f **[COLOR=Red]"[/COLOR]**`find -not -iname "thumbs.db" -type f -printf "%p\n"`**[COLOR=Red]"[/COLOR]** /home/b/Pictures/

```

---

### Post by cbob on 2011-03-09
That solves that:D Thanks!

/cbob

---

