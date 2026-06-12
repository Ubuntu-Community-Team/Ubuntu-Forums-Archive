---
title: "Terminal closes auomatically"
date: 2011-02-20
forum: General Help
---

### Post by mynameissagarbhatt on 2011-02-20
when i start the terminal, it just closes within a second!......any idea why?

---

### Post by mynameissagarbhatt on 2011-02-22
ne one knows was happening?........without terminal m virtually crippled!

---

### Post by Habitual on 2011-02-22
Create another user on the system.
Logout and login as the new user.
run the same terminal, does terminal still close automatically?

Please let us know...

---

### Post by Syed75 on 2011-02-22
How about a reboot?

---

### Post by jhun_jhaye on 2011-02-22
If  your using ncomputing u had to register vspace software.

---

### Post by mynameissagarbhatt on 2011-02-23
> **Habitual said:**
> Create another user on the system.
Logout and login as the new user.
run the same terminal, does terminal still close automatically?

Please let us know...

No it does not!
it is working perfectly when i created a new user.
what exactly happened?

---

### Post by cgroza on 2011-02-23
> **mynameissagarbhatt said:**
> No it does not!
it is working perfectly when i created a new user.
what exactly happened?

Maybe the config file of gnome-termial got corrupted somehow?

---

### Post by Habitual on 2011-02-23
If your .bashrc is not anything special, then you can copy the "new" user's .bashrc to your own with
```
gksu nautilus
```

Make sure 2 tabs are open at the same time.
Navigate to the new user's home directory and press Ctrl+H
find .bashrc highlight it, right mouse click and select copy.
Goto the broken user's tab and right mouse click and paste.

Logout|in 
run terminal.

Let us know...

Note, **If your .bashrc is something special, COPY IT FIRST** (in terminal)
```
cp .bashrc bashrc.org
```

---

### Post by mynameissagarbhatt on 2011-02-23
> **Habitual said:**
> If your .bashrc is not anything special, then you can copy the "new" user's .bashrc to your own with
```
gksu nautilus
```Make sure 2 tabs are open at the same time.
Navigate to the new user's home directory and press Ctrl+H
find .bashrc highlight it, right mouse click and select copy.
Goto the broken user's tab and right mouse click and paste.

Logout|in 
run terminal.

Let us know...

Note, **If your .bashrc is something special, COPY IT FIRST** (in terminal)
```
cp .bashrc bashrc.org
```

it didn't help:(..

---

### Post by TeoBigusGeekus on 2011-02-23
Try to launch terminal.
When it fails, go to tty1 (ctrl+alt+f1).
See if you get any error messages - post them.
(Go back to X from tty1 with ctrl+alt+f7)

---

### Post by mynameissagarbhatt on 2011-02-24
> **TeoBigusGeekus said:**
> Try to launch terminal.
When it fails, go to tty1 (ctrl+alt+f1).
See if you get any error messages - post them.
(Go back to X from tty1 with ctrl+alt+f7)

nope......no error msg:(......just a blank screen........

---

### Post by migs73 on 2011-02-24
Install a different type of terminal (Konsole etc) this will probably bring in other KDE based apps as well but will be better than nothing.

You could then use this to run the gnome terminal and see what error messages come up when you run it.

BTW to run gnome terminal from CLI use 'gnome-terminal'

---

### Post by cgroza on 2011-02-24
No need to install Konsole and all the dependencies that come with it. Hit Alt+F2 and type:

```
xterm
```

and hit Enter. If this brings a white terminal window, then it is a gnome-terminal issue.

---

### Post by AlphaLexman on 2011-02-24
@O.P.
I don't believe your problem is the gnome-terminal, but your shell config files. Try switching shells, see what other shells you have installed:
```
chsh -l
```
invoke one of them (i.e. Alt-F2: /bin/zsh) and see if the terminal crashes the same way.

---

### Post by mynameissagarbhatt on 2011-02-25
> **cgroza said:**
> No need to install Konsole and all the dependencies that come with it. Hit Alt+F2 and type:

```
xterm
```and hit Enter. If this brings a white terminal window, then it is a gnome-terminal issue.


u're right......it brought up a white terminal which also closed,,,,,

---

