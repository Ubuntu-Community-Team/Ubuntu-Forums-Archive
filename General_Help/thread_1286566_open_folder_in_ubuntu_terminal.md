---
title: "open folder in ubuntu terminal"
date: 2009-10-09
forum: General Help
---

### Post by mmohaveri on 2009-10-09
Dear all
who know how can I open a folder in Ubuntu terminal ?
:confused:

---

### Post by nothingspecial on 2009-10-09
What sort of folder do you want to open and what do you want to do with it?

---

### Post by lisati on 2009-10-09
One way to "open" a folder is with the "cd" ("Change Directory") command.

---

### Post by akakingess on 2009-10-09
just a little more detail, let's say I wanted to open the Documents folder that is in my home folder, remember that ~ is equal to "home"```
cd ~/Documents
``` and once there you could type in ```
ls
```
and that will list the items within that directory. Just a quick run through, hope it helps.

---

### Post by pmlxuser on 2009-10-09
if you mean opening a folder using commandline then
```

nautilus /path/nameoffolder

```
does the trick

else when you cd into a folder you have actually opened it to view its contents

```

ls -l

```

---

### Post by bollix47 on 2009-10-09
In case you're referring to the ability to open a folder in a terminal when browsing using nautilus:

```
sudo apt-get install nautilus-open-terminal
```

or use Synaptic and search for nautilus-open-terminal.

Once installed the option to open in terminal will be in the right-click menu.

---

### Post by CatKiller on 2009-10-09
And the other one that no one's mentioned; if you've entered some location in the Terminal, and you want to open a file browser window at that location, you can use ```
nautilus $(pwd)
```Isn't it fun when we all have to go on this elaborate guessing game...?

---

### Post by donsy on 2009-10-28
> **bollix47 said:**
> In case you're referring to the ability to open a folder in a terminal when browsing using nautilus:

```
sudo apt-get install nautilus-open-terminal
```or use Synaptic and search for nautilus-open-terminal.

Once installed the option to open in terminal will be in the right-click menu.

I found this very handy. However in Main Menu I launch the terminal maximized with the following command:
```
gnome-terminal --geometry 1024x768
```Is there a way to launch the terminal in a similar manner from nautilus?

---

