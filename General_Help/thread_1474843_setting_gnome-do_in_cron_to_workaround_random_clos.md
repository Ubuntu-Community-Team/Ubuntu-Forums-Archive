---
title: "setting gnome-do in cron to workaround random closings"
date: 2010-05-06
forum: General Help
---

### Post by joselitux on 2010-05-06
Hi all

Gnome-do closes randomly in my Lucid Lynx, so I tought to set cron to check every five minutes if is open and if not, command gnome-do and get the launcher up again.

This is my script (named wakeUpGnomeDo):

```
#!/bin/bash
ps -ef | pgrep gnome-do || export DISPLAY=:0 && gnome-do
```

And this is my crontab:

```
*/5 * * * * /home/joselitux/wakeUpGnomeDo
```


The problem is that gnome-do is launched, I can see in*** ps aux***, but no applet icon is shown and can't interact with gnome-do. the <super+Space> is not working.

Is a completely useless gnome-do process running.

any help will be appreciated.

thanks

---

