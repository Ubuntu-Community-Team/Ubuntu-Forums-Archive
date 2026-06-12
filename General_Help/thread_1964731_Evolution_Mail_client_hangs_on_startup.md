---
title: "Evolution Mail client hangs on startup"
date: 2012-04-24
forum: General Help
---

### Post by detl_ on 2012-04-24
Hi,
after my system partition ran out of disk space, my Evolution client hangs during startup. I was able to free disk space after the space went short, but still my Evolution client is not able to start up anymore.
The app starts, but then the loaded screen turns grey - means it is not responding. I cannot find a hint within my log files.
I then removed Evolution from my System using the Software-Center and reinstalled it. Also with no success.
No evolution process like the alarm notification is running when I do
ps -ef | grep evo

I guess it has got something to do with local caches.
How can I solve that issue ?
I am running Ubuntu 11.04

thanks,
detlef

---

### Post by dcstar on 2012-04-24
> **detl_ said:**
> Hi,
after my system partition ran out of disk space, my Evolution client hangs during startup. I was able to free disk space after the space went short, but still my Evolution client is not able to start up anymore.
The app starts, but then the loaded screen turns grey - means it is not responding. I cannot find a hint within my log files.
I then removed Evolution from my System using the Software-Center and reinstalled it. Also with no success.
No evolution process like the alarm notification is running when I do
ps -ef | grep evo

I guess it has got something to do with local caches.
How can I solve that issue ?
I am running Ubuntu 11.04

thanks,
detlef

Begin with this in a terminal:

```
evolution --offline
```

If still no success then rename the .evolution folder and it will create a fresh configuration. You can then manually copy data from the saved folder to the new one.

---

