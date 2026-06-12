---
title: "can't get pid of gwibber"
date: 2010-05-10
forum: General Help
---

### Post by Neovos on 2010-05-10
I'm writing some simple scripts to detect if programs are running and if so close them, if not, run them. That part is cool but I can't for some reason get gwibber working with "pidof." I know that it is running but "pidof gwibber" doesn't return anything. Is this because it's python? is there another method of detecting if it's running or not?

---

### Post by Zorael on 2010-05-10
Hmm.
```
ps x -o pid -o cmd | grep *gwibber* | grep -v grep | awk '{ print $1 }'
```
Very dirty solution, there ought to be something neater.

(edit: made it at least a bit neater)

---

### Post by Neovos on 2010-05-10
> **Zorael said:**
> 
```
ps x -o pid -o cmd | grep *gwibber* | grep -v grep | awk '{ print $1 }'
```

haha wow. You went the long way twice around to get that, but it works, thanks! Any clue as to why pidof doesn't work though? It boggles the mind.

I modified it to also ignore gwibber-service as I still wanted it to run in the background, I just didn't want the main window running:

```
ps x -o pid -o cmd | grep gwibber | grep -v grep | grep -v gwibber-service | awk '{ print $1 }'

```

---

