---
title: "Make XP default for GRUB"
date: 2011-03-22
forum: General Help
---

### Post by wolf99 on 2011-03-22
ubuntu 10.04

Hi There

Just did my first side by side install with XP already on board, so far theres only been one or two minor hiccups.

One detail to tidy up is the default ordering on the GRUB loader, currently it Ubuntu first and the default to load if uninterrupted, while XP is at the bottom of the list.

How can I make XP first on the list and default to boot?

I have looked at a couple "explanations" on this, but they are not very clear to a n00b like myself so a 'for dummies' version would be much appreciated :)

Thank you

---

### Post by pqwoerituytrueiwoq on 2011-03-22
startup manager will make it easy

---

### Post by wilee-nilee on 2011-03-22
Startup manager will allow you to choose the default boot.
sudo apt-get install startupmanager 
in the terminal.

---

### Post by marin123 on 2011-03-22
[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

this is another handy app...

---

