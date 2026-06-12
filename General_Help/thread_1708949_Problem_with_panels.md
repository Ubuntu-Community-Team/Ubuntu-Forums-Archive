---
title: "Problem with panels"
date: 2011-03-17
forum: General Help
---

### Post by TimmyK. on 2011-03-17
Hi, can someone please help me? I accidentally created another panel, with autohide and oriented to the top. The only problem is, it did not sit nicely below the other one, it covers it up, and somehow, it is not on autohide, and the old one is. It's just a blank panel with nothing on it. I've tried right-clicking it and deleting panel, but the menu doesn't pop up when I do this. Can I somehow get rid of it from the terminal or the system monitor? Does anyone have any ideas?

---

### Post by ~Plue on 2011-03-17
you could reset the panels to default by running the following from a terminal or run dialogue
```
gconftool-2 --recursive-unset /apps/panel
or
rm -rf .gconf/apps/panel
```then re-login

---

### Post by TimmyK. on 2011-03-17
I tried it. Nothing happened. Am I doing this right? Just enter the commands and it should work?

---

### Post by ~Plue on 2011-03-17
> **TimmyK. said:**
>  Just enter the commands and it should work?
technically, yes. did you log-out  and log-in after running them? if not, do so. or run[I] killall gnome-panel
[/I]

---

### Post by TimmyK. on 2011-03-17
Thank you so much! Works fine now.

---

