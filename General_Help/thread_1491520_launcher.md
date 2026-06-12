---
title: "launcher"
date: 2010-05-23
forum: General Help
---

### Post by ibbill on 2010-05-23
3 problems

 1. cant right click on a program under applications and place it on the desktop or top panel. The program opens up instead.

2. right click on top panel there is no add to panel only see help or about panels.  Other icons that are already on the panel if I right click one of them to move I get help or about.

3. On boot up and closing 10.4 no sound

---

### Post by kaibob on 2010-05-23
There is a GConf setting that, if enabled, will cause that to happen. The key is:

/apps/panel/global/locked_down

I don't know about the sound issue.

---

### Post by ibbill on 2010-05-24
kaibob awesome whoosh thank you ever so much. Ran the following command in the terminal worked great thanks again.

gconftool-2 --type bool --set /apps/panel/global/locked_down false

Sound is no big deal.

Marking thread solved

---

