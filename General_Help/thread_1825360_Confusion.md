---
title: "Confusion"
date: 2011-08-15
forum: General Help
---

### Post by Hexid on 2011-08-15
First of all,I'm totally a newbie,and I'm using ubuntu 11.04.
Can anyone tell me what is the difference between gnome and unity?
Is it impossible to use Kate in a nonKDE desktop environment?
TIA!!!

---

### Post by mcduck on 2011-08-15
Well, Gnome is a desktop environment (a combination of user interface, like menus and panels, different programs made to work closely together, configuration tools, background services and so on).

Unity is a shell running on top of Gnome, replacing some of the user interface elements with it's own.

And no, it's not impossible to use Kate on other DE's than KDE. You'll end using a bit more resources (since it needs to load some KDE libraries) but it works just fine and on any modern computer you aren't likely going to even notice the extra resource usage. In general all applications work in every desktop environment (while they might sometimes integrate better with a certain one).

---

### Post by Hexid on 2011-08-15
Thx . Then can I use KDE and GNOME at the same time?
Btw,is Konsole the same as the terminal in my gnome?

---

### Post by CatKiller on 2011-08-15
You can install them both and use applications from one in the other. When you log in you have a choice as to which you use.

Konsole is the KDE equivalent of gnome-terminal.

---

### Post by Nytram on 2011-08-15
At the login screen you can choose whether to log in to Gnome or KDE, but whichever you choose you are free to use applications designed for either interface. Yes, Konsole is the KDE equivalent of Gnome's terminal.

---

### Post by Hexid on 2011-08-15
Thanks all of you!!!
Really helpful.

---

### Post by Rhizoid on 2011-08-15
You don't need to install the whole of KDE just to use Kate.

Open a terminal and issue:

```
sudo apt-get install kate
```

It'll work just fine under gnome, but bear in mind what mcduck says about resources.

Cheese!

---

