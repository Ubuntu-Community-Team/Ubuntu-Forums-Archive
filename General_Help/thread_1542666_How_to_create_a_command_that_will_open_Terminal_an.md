---
title: "How to create a command that will open Terminal and keep it open?"
date: 2010-07-30
forum: General Help
---

### Post by macrocheesium on 2010-07-30
Hey, I have a problem that I can't seem to figure out. I can easily create a .sh file that will execute a command in Terminal, but as soon as it executes the terminal disappears. How do I get it to stay? My idea is to have the keyboard shortcut "ctrl+alt+del" open a .sh file with the contents "ps ax". Then it would be just like having a task manager; the terminal would open with "ps ax" already executed, and all I would have to do is kill the process number.

---

### Post by GlazedDonut on 2010-07-30
You could execute the script from an already open terminal.

---

### Post by macrocheesium on 2010-07-30
I can always open a terminal manually, but I'm looking to make it quicker.

---

### Post by patchwork on 2010-07-30
Disregard

---

### Post by prodigy_ on 2010-07-30
```
gnome-terminal -x bash -c "/path-to-your-script/your-script.name; bash"
```
And don't forget to make your script executable.

Or, if you really want just **ps**:
```
gnome-terminal -x bash -c "ps -eF; bash"
```
And you won't even need a script.

---

### Post by macrocheesium on 2010-07-31
> **prodigy_ said:**
> ```
gnome-terminal -x bash -c "/path-to-your-script/your-script.name; bash"
```
And don't forget to make your script executable.

Thanks, that did it.

---

