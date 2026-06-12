---
title: "security updates question"
date: 2006-01-21
forum: General Help
---

### Post by monkblah on 2006-01-21
When I do

sudo apt-get update

...does this get security updates for my computer? Or must I do something else?

---

### Post by 23meg on 2006-01-21
It just updates your apt cache to reflect the latest changes in the repositories that are in your sources.list file. To get security updates, make sure you have your sources.list includes the appropriate security update repository and when updates are available, mark them in the update manager / Synaptic and apply.

---

### Post by aysiu on 2006-01-21
[QUOTE=23meg]It just updates your apt cache to reflect the latest changes in the repositories that are in your sources.list file.[/quote] In other words, it just checks to see if there *are* any updates/ upgrades.  > To get security updates, make sure you have your sources.list includes the appropriate security update repository and when updates are available, mark them in the update manager / Synaptic and apply. If you prefer to do it from the command-line: ```
sudo apt-get dist-upgrade
```

---

### Post by monkblah on 2006-01-21
Thanks for the replies.

Is there a way to ask apt-get (or another program) to print a list of all the packages with updates available so I know what will get updated before I run a dist-upgrade?

Is it possible to get such a list of only packages with SECURITY updates available?

Thank you!

---

### Post by aysiu on 2006-01-21
[QUOTE=monkblah]
Is it possible to get such a list of only packages with SECURITY updates available?[/QUOTE] As far as I know, they're *all* security updates, unless you have backports in your repositories sources.list.

---

