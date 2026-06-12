---
title: "zsh - how can I clear the history"
date: 2010-05-29
forum: General Help
---

### Post by theLured on 2010-05-29
Sometimes I don't want commands to be added to my history. In bash it was
```
unset HISTFILE
```
You would run it after a few commands and it would clear them all.

I can't find out how to do it with ZSH. Any ideas?

---

### Post by alexandroid on 2011-03-07
Better late than never, since I stepped on this thread too when searching for same question.

Looks like there is no standard command for that. The only way is deleting your history file.

```
echo $HISTFILE
rm $HISTFILE
```

---

