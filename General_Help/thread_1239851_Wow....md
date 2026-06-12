---
title: "Wow..."
date: 2009-08-14
forum: General Help
---

### Post by trekon86 on 2009-08-14
I didn't think I'd have so much trouble trying to figure this out.
See I wanted to install Tor but no matter where I go I encounter trouble. First because I can't edit my sources.list file, it seems to be locked up tight. (I am an admin on this machine).

Second because I don't know how to compile software using the terminal. I don't even know where to begin. I know how to do sudo and I can copy and paste things that you folks recommend but I'm not about to screw with anything else...and I can't figure out how to run a shell-script in the terminal either.

Any help would be appreciated!

:(
PMZ

---

### Post by llamabr on 2009-08-14
Hello.  I don't know what tor is, but did you try:

```
sudo apt-get install tor
```

for your sources.list, you need to use sudo.  try:

```
sudo nano /etc/apt/sources.list
```

to add whatever repo you want.

Also, to get better help, you should have a more informative subject line.  Let us know what trouble you run into next.

---

### Post by mthalis on 2009-08-14
First Change your topic name always use **meaning full name** 

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by Chronon on 2009-08-14
You don't need to compile anything in order to install TOR.  Have you seen [this page](https://help.ubuntu.com/community/TOR)?

---

### Post by bboston7 on 2009-08-14
use sudo...

---

