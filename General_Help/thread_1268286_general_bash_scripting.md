---
title: "general bash scripting"
date: 2009-09-16
forum: General Help
---

### Post by kevbrad on 2009-09-16
hi all,

i am creating a bash script to automate a process but have run into a problem. the main script calls another script and i want that to run in the background without echoing out anything to the current screen. i am calling external script like so...

`./backgroundjob.sh &`

but the backgroundjob.sh script is outputting the main screen.

what's the work around for this?

---

### Post by DaithiF on 2009-09-16
```
./backgroundjob.sh > /dev/null 2>&1 &

```

which means redirect stdout and stderr output to /dev/null (ie. discard it)

---

### Post by Bachstelze on 2009-09-16
> **DaithiF said:**
> ```
./backgroundjob.sh > /dev/null 2>&1 &

```

which means redirect stdout and stderr output to /dev/null (ie. discard it)

```
./backgroundjob.sh &> /dev/null &

```

Shorter. ;)

---

