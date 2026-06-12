---
title: "[Help] Missing nautilus-scripts folder."
date: 2012-06-19
forum: General Help
---

### Post by ubuntoneedhelp303 on 2012-06-19
Im missing my nautlius-scripts folder i need it to install newrez.
I just installed lubuntu and i wanted to use this progam. Please help :(



EDIT: Also its suppose to be in home/-[Accountname]-/gnome2/nautlius-scripts
but its not

---

### Post by ubuntoneedhelp303 on 2012-06-19
No answers... Comeon guys...

---

### Post by xp15 on 2012-06-19
Do you mean that when you tried to run sudo nautilus, you got a messege anout creating a folder?

it may happen at first but would fix itself at next time you try to run it (:

---

### Post by ubuntoneedhelp303 on 2012-06-19
> **xp15 said:**
> Do you mean that when you tried to run sudo nautilus, you got a messege anout creating a folder?

it may happen at first but would fix itself at next time you try to run it (:

I mean the folder is missing

---

### Post by ubuntoneedhelp303 on 2012-06-19
How about this question how do i install newrez.

---

### Post by nothingspecial on 2012-06-19
Changed prefix from lubuntu to ubuntu as the thread is about nautilus.

Also, please do not bump your thread more than once every 24 hours or so.

---

### Post by HiImTye on 2012-06-19
if this returns 'no such file or..':
```
ls $HOME/.gnome2/nautilus-scripts/
```then do this:
```
mkdir $HOME/.gnome2/nautilus-scripts
```now you have that folder

if it simply returns then the folder is already there, but empty, i.e.
```
tye@T:~$ ls $HOME/.gnome2/nautilus-scripts/
tye@T:~$
```

---

