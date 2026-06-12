---
title: "devilspie help please"
date: 2010-10-03
forum: General Help
---

### Post by cadcam on 2010-10-03
So, i'm running devilspie (via gdevilspie) on my lucid comp.  when i start devils pie, either via the start button, or the command "devilspie", it works great.  I've added devils pie to my list of startup applications.  i want it to maximize a window (program) on startup.  it doesn't.  when i check to see if devilspie is running, it is.  if i restart devils pie, it maximizes....

thoughts?

help?

thanks,
A

---

### Post by cadcam on 2010-10-17
please help?  i don't understand why devils pie works as a command after startup, but fails to maximize the program at startup.  it works for all other programs.?/  


thanks,
A

---

### Post by dodo3773 on 2010-10-17
> **cadcam said:**
> please help?  i don't understand why devils pie works as a command after startup, but fails to maximize the program at startup.  it works for all other programs.?/  


thanks,
A

I messed with this program all morning. The way I got it to work for me was with

```
devilspie -a
```That way if the applications load first then devilspie will still apply your settings afterwards. I also wrote this script for myself

```

#!/bin/bash

evolution & deluge & firefox & sleep 15 && devilspie -a &  sleep 20 && pkill -f "devilspie -a"

exit

```In this script the applications load first, then the script sleeps, then devilspie loads, then it sleeps again and finally kills devilspie. I only use it initially at startup. Also, I do not run it as a startup application either. Oh, and for me I found that it was better to load all of your rules in a single .ds file in the .devilspie folder instead of multiple files all with one rule each. I hope that helps.

---

### Post by cadcam on 2010-11-04
thanks a lot, i'll give that a shot when i get back to the office.

---

### Post by cadcam on 2010-11-24
That works great.  thanks, A.

---

