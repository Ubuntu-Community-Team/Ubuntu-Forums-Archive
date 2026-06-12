---
title: "No linebreaks in txt file on ubuntu"
date: 2011-08-16
forum: General Help
---

### Post by kanishkdudeja on 2011-08-16
i wrote some text in a text file on windows..

and when i view it in gedit on ubuntu..everything was in a single line..

there were no line breaks..how can i restore the line breaks?

---

### Post by Wim Sturkenboom on 2011-08-16
*_fromdos_* to convert from Windows and *_todos_* to convert to Windows

You need to install the package (highlighted in red below)

```

wim@ubuntu-desktop01:~$ **fromdos**
The program 'fromdos' is currently not installed.  You can install it by typing:
sudo apt-get install **[COLOR="Red"]tofrodos[/COLOR]**
wim@ubuntu-desktop01:~$ **todos**
The program 'todos' is currently not installed.  You can install it by typing:
sudo apt-get install tofrodos
wim@ubuntu-desktop01:~$ 

```

---

