---
title: "/usr/games' is not inculded in the PATH environment variable"
date: 2010-12-06
forum: General Help
---

### Post by M1C4HTRON13 on 2010-12-06
I get this every time I try to run a game
eg pacman

Command 'pacman' is available in '/usr/games/pacman'
The command could not be located because '/usr/games' is not included in the PATH environment variable.
pacman: command not found

---

### Post by TeoBigusGeekus on 2010-12-06
Add the path to your ~/.profile file or simply run
```
/usr/games/pacman
```
from terminal.

---

### Post by M1C4HTRON13 on 2010-12-06
> **TeoBigusGeekus said:**
> Add the path to your ~/.profile file or simply run
```
/usr/games/pacman
```
from terminal.
~/.profile file?

---

### Post by efflandt on 2010-12-06
Did you tamper with your ~/.profile or ~/.bashrc (or related defaults in /etc/)?  /usr/games is usually in your PATH by default (and /home/username/bin is automatically added if you create ~/bin for your own scripts or programs):

**echo $PATH**
/home/efflandt/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

---

### Post by M1C4HTRON13 on 2010-12-06
Er opp's
I might have tampered with /ect/environment when I was trying to enabel clutterflow in nautilus

---

