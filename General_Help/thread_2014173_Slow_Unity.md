---
title: "Slow Unity"
date: 2012-07-01
forum: General Help
---

### Post by usmanasim on 2012-07-01
Hey folks,

I recently installed ubuntu 12.04 LTS one year old pentium laptop "Samsung RV508". The unity desktop interface is kinda slow (i have 4gb of ram)

What can I do to make it faster especially the Dash Home. It's very slow. I don't want to overclock my cpu or anything as I have to use this laptop on the go... just a few tweaks in the setting to make it more responsive.

Thank You.

---

### Post by sanderj on 2012-07-01
Maybe this helps:

open a terminal, and then type:

```

uptime
top -bn1 | head -25

```


Post the output here.

Or, the GUI method:

In the Dash, type "system monitor" and click it. Then under Processes and Resources find out if there is a process eating your resources ...

---

