---
title: "Where can I get a list of all the commands for terminal"
date: 2006-02-09
forum: General Help
---

### Post by geniusvicks on 2006-02-09
Where can I get a list of all the commands for terminal?

---

### Post by n5jyk on 2006-02-09
[QUOTE=geniusvicks]Where can I get a list of all the commands for terminal?[/QUOTE]
Could you be a little more specific? Do you mean "term" or the shell terminal that one might launch from the Gnome menu "Applications -- Accessories -- Terminal" perhaps? If the latter is the case you want information about bash... and there is a LOT of information about it. You might want to start at [http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html) also I would like to mention that there is a lot of great information about programming at [http://www.w3schools.com](http://www.w3schools.com)

-b

---

### Post by nanotube on 2006-02-09
if you really want a giant "list" of all the commands available to you, just open the terminal, and hit the tab key twice. it will ask you if you really want to display all 2000+ possibilities, and just say "yes", and you will see them all. :)
though i cant imagine why you might want such a giant list.

---

### Post by Zeroangel on 2006-02-09
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

This is another list, similar to the ones posted above. 

If you want additional information on a specific command **while in the terminal**, Just type in the name of the command in question like so
```
commandname --help | more
```
where commandname is the name of your command (such as cp, rm, mount, ls, etc..). And you can get additional information on that command, such as what it does and the switches you can use to modify it (ie: **rm -r** will remove files in subdirectories as well)

the | more modifier simply allows you to read huge amounts of text screen by screen instead of relying on you having a reading ability of 10 bajillion words per second.

---

### Post by n5jyk on 2006-02-09
[QUOTE=Zeroangel][http://www.ss64.com/bash/](http://www.ss64.com/bash/)

This is another list, similar to the ones posted above. 

If you want additional information on a specific command **while in the terminal**, Just type in the name of the command in question like so
```
commandname --help | more
```
where commandname is the name of your command (such as cp, rm, mount, ls, etc..). And you can get additional information on that command, such as what it does and the switches you can use to modify it (ie: **rm -r** will remove files in subdirectories as well)

the | more modifier simply allows you to read huge amounts of text screen by screen instead of relying on you having a reading ability of 10 bajillion words per second.[/QUOTE]
....and the man pages, I forgot to mention them. At the command line type man commandname where commandname is the command you need more info on. Of course you can type man man to see how man works. Man doesn't always have the most up to date information, however. 

-b

---

### Post by Kiwinote on 2006-02-09
[https://wiki.ubuntu.com/BasicCommands]("https://wiki.ubuntu.com/BasicCommands")
[http://www.linuxcommand.org/learning_the_shell.php]("http://www.linuxcommand.org/learning_the_shell.php")
[http://www.ubuntuforums.org/showthread.php?t=73885&]("http://www.ubuntuforums.org/showthread.php?t=73885&")

Hope this helps

Kiwinote

---

