---
title: "encouragement and advice please"
date: 2006-02-09
forum: General Help
---

### Post by LJW on 2006-02-09
been using windows for a looooong time, even work in desktop support so i thought i'd take the leap into linux, straight away a brick wall.

Installation goes smoothly, no errors and installing the whole package.

asks for a root passwd i give it on

asks for a username and passwd i give it one

setup finishes and i log in as username as it won't let me login as root.

i want to install some drivers so i go to system>administration>synaptic pckge manager, it asks for passwd so first i try root passwd, wrong passwd, so i try username passwd and it just dissapears, nothing, i try launching it again and it shows the clock then dissapears.  

at this point i'm thinking "it wants me logged in as root so i goto system>login screen setup to check the box for root login but once again....nothing!

I'm sure i am missing something incredibly basic and admit i haven't got my head around the linux tech tree yet so any help would be greatly appreciated.

---

### Post by az on 2006-02-09
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)


You were never asked for the root password in the ubuntu default installation.  You were asked for a full username, a username and a password.

You can always boot into recovery mode and change the password for your user by running 
passwd (user)

---

### Post by LJW on 2006-02-09
i used the expert installation because it's a dual boot, it asked for shadow passwds to which i said yes then asked for a root pass which i gave then a full name, username and pass which i gave.

has using the expert install been the cause of my woes?

---

### Post by LJW on 2006-02-09
running a default install now, probably  little cheeky of me to assume i could handle an expert install  just because i know my way around fisher-price XP :)

---

### Post by Ocxic on 2006-02-09
doing an expert install breaks sudo, it a problem everyone has. and expert install really changes almost nothing, and a normal install will do, so don't worry you didn't to anything wrong with your expert install, it's just a bug.

---

### Post by LJW on 2006-02-09
that went smoothly...a bug in a Linux distro? THEY SAID IT WAS INFALLIBLE *sob*

seriously tho, cheers for the heads up as i would have been there all year trying to get expert working, it's just the kind of chimp i am :D

---

### Post by az on 2006-02-09
[QUOTE=LJW]i used the expert installation because it's a dual boot, it ...[/QUOTE]

By default, you will dual boot using a regular install, closing your eyes and hitting enter a few times.  

Expert mode does less, not more!



[QUOTE=LJW]
has using the expert install been the cause of my woes?[/QUOTE]

Expert mode should be renamed "debug" mode or "****-around" mode.


*Ahem!*   Excuse me.

---

### Post by LJW on 2006-02-09
default install completed and blow me if everything isn't working! will install the nvidia drivers when i get home tonight and have a play with cedega....i can't be without my beloved world of warcraft for too long and it's a pain booting to windows everytime.  one last quick question, i have a pair of 21" monitors that i like to run in dualview, is this going to be a major job?

---

