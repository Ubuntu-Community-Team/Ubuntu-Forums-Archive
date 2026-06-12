---
title: "Python file i/o trouble"
date: 2009-08-12
forum: General Help
---

### Post by Kopachris on 2009-08-12
So I've got this under **def** newGame():
```

    player_dir = ninja_dir + name + "/player"
    PLAYER_FILE = open(player_dir,"w")
    print "Player file opened."

```player_dir is ~/.ninja/chris/player.  I set it up to mkdir ~/.ninja/chris right before this.  ls confirms that ~/.ninja/chris exists.  When the code runs, though, I get the following error:
```

Traceback (most recent call last):
  File "./ninja.py", line 7, in <module>
    mainMenu()
  File "headers.py", line 58, in mainMenu
    newGame()
  File "headers.py", line 23, in newGame
    PLAYER_FILE = open(player_dir,"w")
IOError: [Errno 2] No such file or directory: '~/.ninja/chris/player'

```What am I doing wrong here? :confused: Isn't it supposed to make the file if it doesn't exist?  Even when running touch just before this and confirming it by running ls in a separate terminal, it gives the same error.  Python is version 2.6, btw.

---

### Post by DaithiF on 2009-08-12
Hi,
python doesn't recognise the unix convention that ~ refers to your home directory.
So either give it a full path (/home/you/.ninja/etc..), or use the HOME environment variable:
```
import os
myfile=open(os.path.join(os.environ['HOME'], '.ninja/etc'), 'w')

```

cheers
d

---

### Post by Kopachris on 2009-08-12
> **DaithiF said:**
> Hi,
python doesn't recognise the unix convention that ~ refers to your home directory.
So either give it a full path (/home/you/.ninja/etc..), or use the HOME environment variable:
```
import os
myfile=open(os.path.join(os.environ['HOME'], '.ninja/etc'), 'w')

```cheers
d
Oh, I see.  Thank you, that would explain it. :)

---

