---
title: "Firefox refuses to load"
date: 2006-03-28
forum: General Help
---

### Post by o_O on 2006-03-28
So I just made a fresh install of 32-bit Ubuntu 5.10 ('cause I was fed up of 64-bit and the problems I had)... It all went without problems, till I installed flash and java for Firefox. I tested both plugins after installing and they seemed to work, but I rebooted and since then Firefox just won't load... 

I have tried uninstalling and installing both firefox and the plugins, and even uninstalling both and then reainstalling only firefox, to no avail. Any ideas?

---

### Post by taurus on 2006-03-28
Can you run firefox from a terminal to see what the error is?  Without it, it's kind of hard to figure out what's wrong with it...
```

firefox

```

---

### Post by towsonu2003 on 2006-03-28
[QUOTE=taurus]Can you run firefox from a terminal to see what the error is?  Without it, it's kind of hard to figure out what's wrong with it...
```

firefox

```[/QUOTE]
also with ```
firefox --safe-mode
``` so we can be sure any extension and stuff isn't causing this.

---

### Post by o_O on 2006-03-28
The error was:

"Error:

INTERNAL ERROR on Browser End: No manager for initializing factory?

System error?:: Conseguido"


But it works now... Installing FF 1.5.0.1 and getting rid of FF 1.0.7 kept all plugins just fine, and everything runs smooth... Thanks anyway. *crosses fingers, hoping that Thunderbird will be less of a trouble*.

---

