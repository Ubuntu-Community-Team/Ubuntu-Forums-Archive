---
title: "figuring out the terminal"
date: 2010-02-13
forum: General Help
---

### Post by smdawson on 2010-02-13
I am new to Linux and I am trying to familiarize myself with the command terminal. Is there a way I can download and install packages from the terminal? I have been using the software center, but I figured anything that will get me using the terminal and commands would be great.

---

### Post by flippo on 2010-02-13
there are two terminal based tools, aptitude and apt.  I'm only familiar with apt.

To install a package:
```
sudo apt-get install <packagename>
```

To search for a package
```
sudo apt-cache search <whatever your searching for>
```

To remove/purge a package:
```
sudo apt-get <remove or purge> <packagename>
```

Some terminal basics:
```
man <command>
```
gives you information about the command

Finally, 'sudo' elevates your permissions to super-user, you need it for some things (like installing packages)

Good luck

---

### Post by sisco311 on 2010-02-13
Start here: [uhelp]community/UsingTheTerminal[/uhelp].

You can use apt-get to install/remove packages, apt-cache to search for/display info about them. 
[uhelp]community/AptGet/Howto[/uhelp]

If you need a visual interface use aptitude. 

Read the man pages for more details:
```
man apt-get
man apt-cache
man aptitude
```

---

