---
title: "can't run update-manager : i get a red alert on desktop"
date: 2010-01-24
forum: General Help
---

### Post by karemlb on 2010-01-24
I can't run or install any application, there is a red alert on my desktop telling "an orrur occurred, please run Package manager rom the right-click menu or apt-get in a terminal to see what is wrong" 
and when i click on that red button, the package manager run and than a message tells me the following  : 


[SIZE=4][B][U]Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'gpg' is not known on line 55 in source list /etc/apt/sources.list, E:The list of sources could not be read.'[/U][/B][/SIZE]



[SIZE=3]**what should i do, especially i am new on ubuntu**[/SIZE]

---

### Post by ibuclaw on 2010-01-24
Press **Alt+F2** to load a Run Command box, and paste in the following:
```
gksu gedit /etc/apt/sources.list
```
And run.

Next, copy and paste the entire file contents into your next post.
Be sure to use [NOPARSE]```

```[/NOPARSE] tags.

Regards
Iain

---

### Post by michy99 on 2010-01-24
You have an error in your sources.list file. Post the contents of /etc/apt/sources.list and we will see what the problem is.

EDIT: I'm a slow typer.

---

