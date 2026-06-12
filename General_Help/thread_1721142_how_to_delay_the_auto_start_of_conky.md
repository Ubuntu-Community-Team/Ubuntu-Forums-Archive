---
title: "how to delay the auto start of conky"
date: 2011-04-04
forum: General Help
---

### Post by rvchari on 2011-04-04
hey guys,
can i get help on how to make my conky autostart with say 30 seconds delay after the desktop has loaded ? sometimes conky is visible and at times it hides !!! i have to kill it and restart it. i felt if i can make it delay by say 30 seconds, it should work...
thanks in advance

---

### Post by DeMus on 2011-04-04
> **rvchari said:**
> hey guys,
can i get help on how to make my conky autostart with say 30 seconds delay after the desktop has loaded ? sometimes conky is visible and at times it hides !!! i have to kill it and restart it. i felt if i can make it delay by say 30 seconds, it should work...
thanks in advance

Write a small script with this in it:
#!/bin/bash
sleep 30
conky

Make this file executable and put in your startup programs list instead of conky.

---

### Post by rvchari on 2011-04-04
thanks !!! its functioning perfect, as desired !!!
i ll mark this thread as solved...

---

### Post by DeMus on 2011-04-04
> **rvchari said:**
> thanks !!! its functioning perfect, as desired !!!
i ll mark this thread as solved...

You're welcome.

---

