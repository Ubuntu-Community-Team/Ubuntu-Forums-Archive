---
title: "Terminal command reload shell (Alt+F2 R)"
date: 2011-11-25
forum: General Help
---

### Post by scratch178 on 2011-11-25
is there a Terminal command for Alt+F2 R (reload shell)?

I'm using the system-monitor shell extension and the network speed doesn't always work,
when i restart the shell everything works fine.

So i like to make a gesture in easystroke to easy reload the shell fast and easy.

---

### Post by whatthefunk on 2011-11-25
```
source ~/.bashrc
```

Is this what youre looking for?

---

### Post by scratch178 on 2011-11-26
no not really

i want to reload the shell with a terminal command


source ~/.bashrc
bash: /home/dominik/.bashrc: No such file or directory

---

### Post by jocko on 2011-11-26
> **scratch178 said:**
> no not really

i want to reload the shell with a terminal command


source ~/.bashrc
bash: /home/dominik/.bashrc: No such file or directory
Exactly what do you mean by "reload the shell", and what is Alt+F2+R supposed to do? It swiches to tty2 (Alt+F2) but adding the R does not seem to do anything...
source ~/.bashrc will execute the commands in .bashrc (which if it exists contains your user-specific settings, so it essentially reloads the settings for the shell, but afaik it does not reload the shell itself...)

---

### Post by scratch178 on 2011-11-29
```
ALT + F2 doesn't work by default in GNOME Shell under
Ubuntu 11.10 Oneiric Ocelot. To fix it, open "System Settings"
and under Keyboard > Shortcuts > System, click "Disabled" next
to "Show the run command prompt" and press ALT + F2 - this
should set ALT + F2 for running the command prompt.
```

```
Typing 'r' in the Alt+F2 prompt will restart GNOME Shell.
This is useful when you are make changes to the GNOME Shell
code while working within the GNOME Shell.
```

Its not ALT+F2+R but ALT+F2 enter r

it reloads the shell, and im looking for a command that i can
run in terminal, so i can run it with my startup Applications,
because shell-Extension-system-monitor only works after
reloading the shell.

Hope you know now what i meant.

---

### Post by thaelim on 2011-11-29
The command you are after is ```
gnome-shell --replace
```

---

### Post by scratch178 on 2011-11-29
thx 

thats what i was looking for

---

