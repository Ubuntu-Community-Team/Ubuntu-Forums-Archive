---
title: "Prevent Hibernation While Script Running?"
date: 2010-07-12
forum: General Help
---

### Post by RangerX_308 on 2010-07-12
Running 10.04 32bit.

Is there a way to prevent hibernation from kicking in while a specific script is running?

---

### Post by gzarkadas on 2010-07-13
Hi, I haven't done this before, but a possible solution to your problem is to find the executable that hibernates the computer (this is that will get called by any user interface command) and inside your script change its permissions with the `chmod' command to become non-executable. Then at the end use chmod again to restore permissions.

In my system (9.10), it appears that this is `/usr/lib/pm-utils/bin/pm-action'. It is linked by `/usr/sbin/pm-hibernate' and `/usr/sbin/pm-suspend'.

So the script code would be something like that:
```

sudo chmod a-x /usr/lib/pm-utils/bin/pm-action
...
<your-commands>
...
sudo chmod a+x /usr/lib/pm-utils/bin/pm-action

```Hope this helps. If the concept works -which is the first question to answer- then we can polish the script out (such as writing a trap handler to always restore permissions if some of the commands in-between fails or the user presses Ctrl+C).

---

