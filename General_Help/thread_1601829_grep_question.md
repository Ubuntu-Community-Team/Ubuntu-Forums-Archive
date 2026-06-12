---
title: "grep question"
date: 2010-10-20
forum: General Help
---

### Post by derblaue on 2010-10-20
I'm trying to get grep to display the process for transmission and for transmission only. Unfortunately, whenever I do: 
```
ps -e | grep transmission
```
I also get transmission-da (transmission-daemon):
```
 2796 ?        00:00:00 transmission-da
28279 ?        00:00:35 transmission

```
I have tried using ```
ps -e | grep -x transmission
``` This however seems to yield no result at all, it just returns to the commandline. 
So far I've circumvented the problem by using this
```
ps -e | grep transmission | awk '{print $4}' | grep -x transmission
``` but I get the feeling this is the long way around.

Is there an easier way and why won't grep -x work from the get-go? Any suggestions or ideas are welcome!

---

### Post by sisco311 on 2010-10-20
use pgrep:
```
pgrep -xfl transmission
```
see:
```
man pgrep
```

---

### Post by derblaue on 2010-10-21
Cheers!

---

