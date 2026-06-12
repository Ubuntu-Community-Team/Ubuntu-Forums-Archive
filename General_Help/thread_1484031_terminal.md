---
title: "terminal"
date: 2010-05-15
forum: General Help
---

### Post by Kofgarter on 2010-05-15
How, in terminal, get back menu bar. The problem is that, yesterday I was tricking with options of this utility, and sat transparency, and disable top menu bar (I don't remember actual name of this option). Now I have only window of terminal, and nothing more. I need return top bar, with menus, options of terminal, and etc.
How do it? Please help.

---

### Post by dv3500ea on 2010-05-15
run
```
gconftool-2 --set -t bool /apps/gnome-terminal/profiles/Default/default_show_menubar true

```
Replacing 'Default' if you use a different profile with the name of that profile.

---

### Post by WorMzy on 2010-05-15
Open a terminal -> right click inside it -> Show Menubar

Is that what you mean?

---

### Post by Kofgarter on 2010-05-16
thanks guys! now works fine! :)

---

### Post by Penguin Guy on 2010-05-16
> **Kofgarter said:**
> thanks guys! now works fine! :)
It helps other people find what they are looking for if you mark you threads as solved once you have found your answer. You can do this by clicking [COLOR="Green"]Thread Tools -> Mark as Solved[/COLOR]. Thanks.

---

