---
title: "Q: getting rid of compiz processes after uninstalling?"
date: 2010-04-26
forum: General Help
---

### Post by soona86 on 2010-04-26
Hi,
I installed the compiz config. app, then changed some values. and after that I uninstalled it..

Now I see two or three processes running in System Monitor

I want to get rid of all that. how can I do that? :)

Thanks in advance

---

### Post by ubunterooster on 2010-04-26
Click them in System monitor and select "end process" unless they are Important. If unsure, paste the names of them here

---

### Post by ajgreeny on 2010-04-26
Simply using metacity --replace in the Alt+F2 dialog should stop compiz running, or, of course, System ->Preferences ->Appearance and set "None" in Effects tab.  Also remove any "Startup Applications" entry for compiz that you might have added.

---

### Post by soona86 on 2010-04-29
> **ubunterooster said:**
> Click them in System monitor and select "end process" unless they are Important. If unsure, paste the names of them here

the list of processes are :

1-compiz (100 KiB)
2-compiz-decorato (80 KiB)
3-compiz.real (21.5 MiB)

when I kill them they go away (note : I didn't try "ending" them)..but the next start up the come back..so, what can I do? :)

[CENTER]_______________________________________________________________[/CENTER]

> **ajgreeny said:**
> Simply using metacity --replace in the Alt+F2 dialog should stop compiz running, or, of course, System ->Preferences ->Appearance and set "None" in Effects tab.  Also remove any "Startup Applications" entry for compiz that you might have added.

1-sorry, but what's metacity?
2-won't setting the effects to "none"; disable everything?..I mean I don't wanna disable it..this feature doesn't belong to "compiz", does it?
3-where can I find the "Startup Applications"?

thanks for your help so far :)

---

### Post by nothingspecial on 2010-04-29
```
sudo apt-get remove compiz-core
```

That will remove compiz all together.

Simply removing the settings manager doesn`t remove compiz itself.

---

### Post by ubunterooster on 2010-04-29
> **soona86 said:**
> when I kill them they go away (note : I didn't try "ending" them)..but the next start up the come back..so, what can I do? :) edit the startup applications> 1-sorry, but what's metacity?
2-won't setting the effects to "none"; disable everything?..I mean I don't wanna disable it..this feature doesn't belong to "compiz", does it?
3-where can I find the "Startup Applications"?
1. metacity=default desktop effects manager. run ```
metacity --replace
``` in the box that comes up when you press alt+F2.
2. That does refer to compiz.
3.System>preferences>Startup Applications.

---

### Post by 3rdalbum on 2010-04-29
Compiz is a window manager that provides the desktop effects.

CompizConfig Settings Manager is a program that lets you change the settings of Compiz.

You can't have the effects without Compiz, and removing CompizConfig Settings Manager will neither put the settings back the way they were, nor will remove the effects altogether.

---

### Post by soona86 on 2010-04-30
Thanks guys for your efforts..problem solved

Btw, I uninstalled Ubuntu..and now I'm trying Xubuntu..

Thanks again

---

