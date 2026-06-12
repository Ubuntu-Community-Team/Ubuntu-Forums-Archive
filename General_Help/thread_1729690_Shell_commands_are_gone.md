---
title: "Shell commands are gone"
date: 2011-04-15
forum: General Help
---

### Post by stino on 2011-04-15
I'm working in Xubuntos with tinyos to learn programming motes. I was following a tutorial where they said to set the PYTHONPATH environment variable.
I thought this had to be in the .bashrc file and I edited with nano the file like this:
export PATH=.:$PYTHONPATH
(there were already 2 paths that I included before like this:
export PATH=.:$PATH
export CLASSPATH=.:$CLASSPATH
which worked well)

But after editing the PYTHONPATH I got into troubles.
The shell doesn't recognize any commands anymore. When I type ls, it sais the command is not installed. So I can't do anything more in the shell.

-How can I resolve this problem and access the .bashrc file again in order to delete the PATHONPATH so the shell will know the commands again?

-Why did this happen?

---

### Post by idoitprone on 2011-04-15
[http://ubuntuforums.org/showthread.php?t=1608418](http://ubuntuforums.org/showthread.php?t=1608418)

this will solve you problem

you might have to use absolute paths

```
/usr/bin/cp -p /etc/skel/.bashrc ~/
```

restart computer then everything is restore to defaults


btw: i believe you override you $PATH with this


> export PATH=.:$PYTHONPATH

when you want to add and path nextime

PATH=$PATH:whateveryouwant

---

### Post by WorMzy on 2011-04-15
You're overwritten your PATH variable (don't worry, it's only temporary). Edit your .bashrc file again:
Press Ctrl+F2, then type
```
/usr/bin/gedit .bashrc
```

and change

```
export PATH=.:$PYTHONPATH
```

to

```
PATH=$PATH:$PYTHONPATH
```

Like idoitprone suggested. I'm assuming that $PYTHONPATH is actually set higher up in the file.

You will need to log out and back in for the changes to take effect.

EDIT: Just noticed you're using XFCE, not GNOME, so you probably don't have gedit. Amend the instructions to fit the text editor of your choice. I think Alt+F2 will still work, although it's been a while since I used XFCE, so I'm not sure.

---

### Post by stino on 2011-04-16
Alright, I followed the instructions from WorMzy and that solved the problem. I just used nano instead of gedit. I edited the file as described and restarted ubuntu.
The commands in the shell are back.

Thanks a lot!

---

