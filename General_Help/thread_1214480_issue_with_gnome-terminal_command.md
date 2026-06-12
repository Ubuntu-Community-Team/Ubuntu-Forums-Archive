---
title: "issue with gnome-terminal command"
date: 2009-07-16
forum: General Help
---

### Post by mjatte on 2009-07-16
what I really want to do is run a shell script with a command like this, and have the output appear in a new terminal window, so that I will be able to have it run and display right when I log in, such as like a welcome screen..

so when I open a terminal and run *gnome-terminal -x myscript*, a new terminal windows opens with a blinking cursor, and it looks like nothing happens, the script does not appear to run, and their is no output..what am I doing wrong??

edit: let me clarify. when I run *gnome-terminal -x vim tempFile, or something like that it works fine,  *but when I try gnome-terminal -x echo "ok", I want the new terminal to display "ok", but it doesn't show anything..

---

### Post by kaibob on 2009-07-16
> **mjatte said:**
> ...edit: let me clarify. when I run *gnome-terminal -x vim tempFile, or something like that it works fine,  *but when I try gnome-terminal -x echo "ok", I want the new terminal to display "ok", but it doesn't show anything..

The following command line will do what you want:

```
gnome-terminal -x bash -c "echo ok ; bash"
```

---

