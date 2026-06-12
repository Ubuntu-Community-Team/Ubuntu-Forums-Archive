---
title: "Gnome panel help"
date: 2010-06-16
forum: General Help
---

### Post by yo2boy on 2010-06-16
Hey! Here's my problem:

I installed AWN, and I configured everything to how I wanted it to be. Now, after a while, I wanted to remove gnome-panel. So a user on a irc channel suggested that I execute the following command:

```
sudo mv /usr/bin/gnome-panel /usr/bin/gnome-panel2 && killall gnome-panel
```

Now, I want to undo this really bad.. if not reinstall gnome-panel. How would I do that?

I am on Ubuntu 10.04

---

### Post by wojox on 2010-06-16
Just reverse it:

```
sudo mv /usr/bin/gnome-panel2 /usr/bin/gnome-panel
```

And to reset the panels like a fresh install run these two commands

```

gconftool --recursive-unset /apps/panel
pkill gnome-panel

```

---

### Post by yo2boy on 2010-06-16
@wojox:

```
mv: cannot stat `/usr/bin/gnome-panel2': No such file or directory
```

---

### Post by wojox on 2010-06-16
You sudo?

Open up /usr/bin and see if you can find anything similar to gnome-panel.

---

### Post by yo2boy on 2010-06-16
Ok! I clicked the gnome-panel and it came back! I wonder why it didn't work with Terminal. But anyway, thanks for helping!!

---

### Post by Anxious Nut on 2010-07-23
Ok ok ok! This piece of info is missing from the internet SO please anybody reads this, REMEMBER IT later when you're asked!

I ran through this today, my little bro went through the same Yo2boy did and i found it, the way to remove all gnome-panels, here's the solution!

Launch gconf editor (Alt+F2 and enter gconf-editor) then goto Desktop --> gnome --> session! then double click on "required_components_list" and remove panel! We're not done yet! click on the sub directory off session which is required_components and set "panel"'s value to "", empty!

Wasnt that hard now was it ;)

**update:** this is also provided in Ubuntu Tweak, under session control! now, it's like i didnt do anything special:(

Chaw guys ;)

---

