---
title: "Command-Not-Found"
date: 2010-05-26
forum: General Help
---

### Post by Wastedyouthfx0 on 2010-05-26
I have compiled a program and installed it in /usr/local/games.  I suppose, because it also exists in the repository, that I get and error when tying the command: The program 'angband' is currently not installed.  You can install it by typing:
apt-get install angband

I've tried removing the command-not-found package, but end up with an error now: /usr/bin/python: can't find '__main__.py' in '/usr/share/command-not-found'

By typing the full path, the game runs correctly.  How can I fix this?

---

### Post by tgalati4 on 2010-05-26
Open a terminal:

env

I have /usr/games but not /usr/local/games in my PATH statement.  Perhaps putting the statement:

PATH="/usr/local/games:$PATH"

at the end of your .profile might fix it.

---

### Post by jerome1232 on 2010-05-26
Or the more common approach is to make a symbolic link to the executable, place the symbolic link in a place that is in your path.

```
ln -s /usr/local/games/executablenamehere /usr/games/executablenamehere
```

---

### Post by Wastedyouthfx0 on 2010-05-26
> **jerome1232 said:**
> Or the more common approach is to make a symbolic link to the executable, place the symbolic link in a place that is in your path.

```
ln -s /usr/local/games/executablenamehere /usr/games/executablenamehere
```

Instead of making a symbolic link, I'm going to install it to /usr/games instead if thats where it belongs in ubuntu.  

My game is running nicely now, thanks for the help/

---

