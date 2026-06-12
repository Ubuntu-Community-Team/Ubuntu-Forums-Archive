---
title: "show time of multiple time zones"
date: 2010-11-04
forum: General Help
---

### Post by aspedisca on 2010-11-04
Hi all,
Is there a program that you know to show time in multiple time zones. 
I would like it to be cli based.
Thank you

---

### Post by sisco311 on 2010-11-04
You can use the date command and the [TZ environment variable]("https://help.ubuntu.com/community/EnvironmentVariables"), i.e.:
```
TZ="Europe/Bucharest" date
```

---

### Post by aspedisca on 2010-11-04
I would like to display multiple time zones not for any instance. 
Like a multiple clocks with second but in terminal window.

Local ...
UTC ...
.
.
.

something like this.
Thank you

---

### Post by sisco311 on 2010-11-04
You mean something like:
```
watch --interval=1 --no-title "echo -n \"local: \"; date +\"%R:%S\"; echo -n \"Budapest: \"; TZ=\"Europe/Budapest\" date +\"%R:%S\""
```

Of course, you can write a script and run it with watch.

tz-script:
```
#!/bin/bash

echo -n "Local:   "
date +"%H:%M:%S"

echo -n "Hungary: "
TZ="Europe/Budapest" date +"%H:%M:%S"

echo -n "Romania: "
TZ="Europe/Bucharest" date +"%H:%M:%S"

echo -n "UTC:     "
TZ="UTC" date +"%H:%M:%S"

```

```
watch --interval=1 --no-title path/to/tz-script
```

---

