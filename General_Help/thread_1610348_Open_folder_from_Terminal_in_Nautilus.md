---
title: "Open folder from Terminal in Nautilus"
date: 2010-10-31
forum: General Help
---

### Post by Fracta on 2010-10-31
This probably seems like a strange request. Every other thread I could find was about "Open in Terminal" on right click in nautilus. That was the first thing I installed.
Now I want the opposite too. I want to be able to open the current folder (or any folder) in nautilus from the terminal command line.

---

### Post by nothingspecial on 2010-10-31
Current folder

```
nautilus .
```
***Edit Notice the dot, that stands for the current directory***

Any folder
```

nautilus /path/to/folder
```

---

### Post by Fracta on 2010-11-01
Awesome, thanks!

---

### Post by HiImTye on 2010-11-01
you could also make an alias so you just have to remember a simple command like:
```
alias opnaut='nautilus .'
```would open nautilus in your current directory if you typed opnaut

to add a permanent (for your current user) alias, open up gedit and open ~/.bashrc
once there, add a new line after the other aliases and viola! you can also put them in their own file if you create a new file called .bash_aliases in your home folder.

---

