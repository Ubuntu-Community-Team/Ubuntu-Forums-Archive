---
title: "Strange ls behaviour in BASH Script"
date: 2010-01-21
forum: General Help
---

### Post by Mr_Lazy on 2010-01-21
Hi,

I hope someone can help, I have stared so long at this now.. maybe I am missing something obvious...

In some code that I have copied, I get this error when I run it by itself in a script.

The code:
```
ls wlanbase/all/status/!(*-mirror*)-packages | cut -f 4 -d /
```

The error:
```
./dev.sh: command substitution: line 113: syntax error near unexpected token `('
./dev.sh: command substitution: line 113: ` ls wlanbase/all/status/!(*-mirror*)-packages | cut -f 4 -d / )'

```

So, I thought I would try the ls command on the command line, like so:
```
ls wlanbase/all/status/!(*-mirror*)-packages | cut -f 4 -d /
```
and it works, I get my list of filenames without "mirror" in them:
```
status-kadaka-packages
status-kopli-packages
status-lasnamae-packages
status-mustamae_2-packages
status-mustamae-packages
status-paldiski-packages
status-parnu-packages

```

My question is, is why does this work on the command line and not in the script, what am I missing here?

Is there some kind of work-around?
Any help gratefully received....

Stephen

---

### Post by John Bean on 2010-01-21
It's probably being run by sh (not bash).

The syntax requires a POSIX shell like bash.

---

### Post by Mr_Lazy on 2010-01-21
Thanks for the reply John,

So I tried running the script with:
```
bash dev.sh
```

and I get the same error....

---

### Post by sisco311 on 2010-01-21
You have to enable the extglog shell option:
```
shopt -s extglob
ls !(pattern-list)

```

---

### Post by Mr_Lazy on 2010-01-21
Thanks Sisco, that works... I'll go and do some reading me thinks.

Stephen

---

