---
title: "A better PS1 prompt"
date: 2010-05-13
forum: General Help
---

### Post by linux-hack on 2010-05-13
Ok this is not much but I rely like'it a lot so why not share'it with others. This is my PS1 prompt variable that gives you a rely nice bash prompt to wor with .. You can add or remove stuff as you wish.

```
PS1="\n\[\e[30;1m\]\[\016\]l\[\017\](\[\e[34;1m\]\u@\h\[\e[30;1m\])-(\[\e[34;1m\]\j\[\e[30;1m\])-(\[\e[34;1m\]\@ \d\[\e[30;1m\])->\[\e[30;1m\]\n\[\016\]m\[\017\]-(\[\e[32;1m\]\w\[\e[30;1m\])-(\[\e[32;1m\]\$(/bin/ls -1 | /usr/bin/wc -l | /bin/sed 's: ::g') files, \$(/bin/ls -lah | /bin/grep -m 1 total | /bin/sed 's/total //')b\[\e[30;1m\])--> \$ \[\e[0m\]"
```

---

### Post by K.Mandla on 2010-05-20
Moved to General Help.

---

