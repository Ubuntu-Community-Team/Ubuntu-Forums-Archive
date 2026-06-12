---
title: "Create file which will autorun a terminal command"
date: 2012-09-18
forum: General Help
---

### Post by redstring on 2012-09-18
As the title says, I'm trying to create a file which will auto-run a terminal command - particularly running a .sh file.  How might I go about creating some sort of shortcut on my desktop to save me the work of opening terminal, navigating to the folder, and running the file through terminal?


Thanks

---

### Post by black veils on 2012-09-27
you want a menu/launcher item to run a command, use **[this]("http://ubuntuforums.org/showthread.php?t=2007247&highlight=bodhi+easier")** method, but it will need some tweaking, you will also want to alter the command for xterm, so it doesnt stay open. i forget specifics, but this will get you going in the right direction!

---

### Post by HiImTye on 2012-09-27
you can do one of two methods, depending on your comfort level in the terminal
1:

[LIST=1]
[*]open 'Files'
[*]navigate to the folder that has your shell script
[*]right click on it and select 'Make Link'
[*]drag the link onto your desktop
[/LIST]
2:
```
ln -s /path/to/script $HOME/Desktop
```
obviously, replace '/path/to/script' with the actual path and filename of the script


now you just double click on the link on the desktop and viola!

---

