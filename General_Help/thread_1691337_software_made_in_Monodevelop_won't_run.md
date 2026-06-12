---
title: "software made in Monodevelop won't run"
date: 2011-02-19
forum: General Help
---

### Post by Slench on 2011-02-19
I made a little applicaton in MonoDevelop, it works fine and does what it's supposed to when I run it inside of MonoDevelop itself.
but
when I try running the output exe file from either the debug or release folders it just won't do anything...
is is because my system assorts exe's with wine or is it something else?
I can't really figure it out...

and now we're at it is there a way for me to change the output format in MonoDevelop??? I pretty much just got it...

PS I'm still pretty much a noob at linux, only having the system for a week and not using it for more than a couple of hours a day..

so it'd be nice to get some tips from you hardcore linux users out there...:D

---

### Post by WorMzy on 2011-02-19
Try running it from a terminal.

```
mono /path/to/program.exe
```

---

### Post by Slench on 2011-02-20
> **WorMzy said:**
> Try running it from a terminal.

```
mono /path/to/program.exe
```

see that's what my program was made for, to not use the terminal to open bin files xD


edit: when I try it says:
```
user@computername:~$ mono home/user/Projects/program/program/bin/Release/program.exe 
Cannot open assembly 'home/user/Projects/program/program/bin/Release/program.exe': No such file or directory.
```

which is odd since I'm looking straight at it...

edit 2:
however if I cd the path first it works

---

