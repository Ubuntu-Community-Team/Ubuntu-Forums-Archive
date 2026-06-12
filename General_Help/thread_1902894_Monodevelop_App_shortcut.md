---
title: "Monodevelop App shortcut"
date: 2012-01-01
forum: General Help
---

### Post by tarun_pai on 2012-01-01
I'm on Ubuntu 11.10, and recently got monodevelop 2.8.5, 

As of now, I have to do

```
>make run 
```

on my terminal every time to run monodevelop, so to install it permanently and create a shortcut, I'm doing the following

```
>./configure --select --prefix=/opt/monodevelop
> sudo make && sudo make install

```

It's working perfectly, now to create a shortcut,

```
> sudo nano /usr/share/applications/Monodevelop.desktop

```
The contents of Monodevelop.desktop are as follows,

```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=MonoDevelop
GenericName=MonoDevelop IDE
Comment=MonoDevelop IDE
Exec=***path to executable*** - customize
Icon=***path to icon*** - customize
Terminal=false
Type=Application
StartupNotify=false
Categories=Development;IDE
```

**The PROBLEM :**

I don't know what the exact values of EXEC and ICON should be.


What should the values hold?

[The original question is here]("http://askubuntu.com/questions/91527/problem-installing-monodevelop-2-10-5-on-ubuntu-11-10")

---

