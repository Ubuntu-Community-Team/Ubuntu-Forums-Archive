---
title: "sux xdotool working using ssh session but not when added to script"
date: 2011-09-25
forum: General Help
---

### Post by swiep on 2011-09-25
When running the following via _SSH _I get the wanted result (fullscreen):
*sux - user1 /usr/bin/xdotool click 1*

When I add the following as _cronjob _I don't get the wanted result:
*01 * * * * sux - user1 /usr/bin/xdotool click 1*

I am unable to locate the log file for xdotool and can not find a parameter for verbose.

Any suggestions to what might be my mistake or how I can get some logging so that I can have a clue on how to get this working?

Thanks in advance.

---

