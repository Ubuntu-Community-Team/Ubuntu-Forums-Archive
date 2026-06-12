---
title: "cron forcing gnome-do to start"
date: 2010-05-11
forum: General Help
---

### Post by joselitux on 2010-05-11
Hi all

In my Lucid system, gnome-do closes unexpectedly, so when it comes to need it, it's not started. I've set a script to check if it's open and if not, then force it to start. This is my script:


```
#!/bin/bash
ps -ef | pgrep gnome-do || export DISPLAY:0 && gnome-do
```

and this script is called by cron job running every 5 minutes.
it seems to work but gnome-do is not accesible. I can see the process running with system monitor, but there is no panel icon and no possiblity to interact with the default <super+space> keys.

Seems to be working but lack of some config or more commands that is ar away from my linux knowledge.

any help would be appreciated

---

