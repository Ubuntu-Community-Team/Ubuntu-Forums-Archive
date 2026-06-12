---
title: "top or bottom taskbar (panel) deleted or hidden .. how to show it (reset to default)"
date: 2010-07-23
forum: General Help
---

### Post by Jacky92 on 2010-07-23
[SIZE=3]Hello ... UBUNTU users ... 

I'm New Here and this is my first thread ..
and I'm new UBUNTU user .. so .. be easy with me ...

this thread is about how to show the top panel or the bottom panel after accidentally deleting  or after re-starting computer or upgrading .. or any thing could delete or hide or remove one of the two panels ...

YOU just have to follow these steps then it's will work ...

1- Go to Terminal ,,, ( if the top panel deleted or not showing hit { Ctrl+Alt+t } )

2- in the Terminal you have to write :

```
gconftool --recursive-unset /apps/panel
```[/SIZE][SIZE=3]
after that...

```
pkill gnome-panel
```[/SIZE][SIZE=3]

now .. it should work 1000% ... [-o<
[/SIZE]```
[SIZE=3]
Note : remember that all the settings or preferences or adds you make for the panels will reset to DEFAULT[/SIZE]
```[SIZE=3]
Bye.:D



Greetings:popcorn:

Jacky

[/SIZE]

---

### Post by ubunterooster on 2010-07-23
Presses *like* button ;)


> **Jacky92 said:**
> [SIZE=2]Go to Terminal ,,, ( if the top panel deleted or not showing hit { Alt+F2 } then type >> gnome-terminal << then hit RUN .. )[/SIZE]I prefer ctrl+Alt+t

---

