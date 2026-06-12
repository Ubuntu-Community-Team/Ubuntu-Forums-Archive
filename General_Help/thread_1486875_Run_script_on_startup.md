---
title: "Run script on startup"
date: 2010-05-18
forum: General Help
---

### Post by imple on 2010-05-18
Hi,

I have a Python script that waits for user input. I want to run it every time I long in. So I added the command "python3 startup.py" to the list of startup programs. It runs, but it doesn't wait for user input.

How run it in a terminal and have it wait for user input?

Thanks!

---

### Post by BoneKracker on 2010-05-18
Since you mention a "list of startup programs", I assume you're in a graphical environment (e.g. Gnome).

If that's the case, what you are really wanting to start is a terminal emulator (what you probably know as a "terminal"), with your script running in it.

That would be something like:
```
gnome-terminal "python3 startup.py"
```

You could also start it automatically from your ~/.bash_profile like so (assuming that syntax for calling gnome-terminal is correct:

```
gnome-terminal "python3 startup.py" &
```

I probably got something wrong here because I don't use Gnome, in which case I invite corrections. :)

---

