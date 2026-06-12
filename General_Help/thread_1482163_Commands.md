---
title: "Commands"
date: 2010-05-13
forum: General Help
---

### Post by crazyamerican on 2010-05-13
I am attempting to assign a command that will open the disk utility to the hotkey (ctrl + alt + u). I am using CompizFusion's Commands thingy. Is there an existing hotkey for this? If not, what is the command that should be put in the box?

___________________________________________

[color=red]<###############################[/color][color=black]]@:":%%%]=[%%%:":@[[/color][color=red]###############################>[/color]

---

### Post by sisco311 on 2010-05-13
```
palimpsest
```

---

### Post by crazyamerican on 2010-05-13
Can someone post commands for useful programs. I really like hotkeys. I'll start the list:

gnome-terminal: terminal
gedit: gedit
nano: simple text editor
rhythmbox: rhythmbox music player

_________________________________________

[color=red]<###############################[/color][color=black]]@:":%%%]=[%%%:":@[[/color][color=red]###############################>[/color]

---

### Post by sisco311 on 2010-05-13
To get a list of commands for the applications listed in the menus run:
```
awk -F= ' $1=="Name" || $1=="Comment" {print} /^Exec/{print "Command="$2"\n"}' /usr/share/applications/*.desktop | less
```

use the arrow keys to scroll up and down, q to quit.

------------------------------------------------------------------------

To set up a signature go to User CP -> Edit Signature

---

### Post by alienprdkt on 2010-05-13
> **sisco311 said:**
> To get a list of commands for the applications listed in the menus run:
```
awk -F= ' $1=="Name" || $1=="Comment" {print} /^Exec/{print "Command="$2"\n"}' /usr/share/applications/*.desktop | less
```use the arrow keys to scroll up and down, q to quit.

------------------------------------------------------------------------

To set up a signature go to User CP -> Edit Signature

Nice one, will have to remember that.

---

### Post by GameDog(A) on 2010-05-13
> **sisco311 said:**
> To get a list of commands for the applications listed in the menus run:
```
awk -F= ' $1=="Name" || $1=="Comment" {print} /^Exec/{print "Command="$2"\n"}' /usr/share/applications/*.desktop | less
```

use the arrow keys to scroll up and down, q to quit.

------------------------------------------------------------------------

To set up a signature go to User CP -> Edit Signature

Nice TY!

---

