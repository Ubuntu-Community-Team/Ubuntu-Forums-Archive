---
title: "Need help installing Starcraft on Wine OR Crossover"
date: 2010-05-02
forum: General Help
---

### Post by Flexia on 2010-05-02
I have been endlessly trying to install WoW as well as Starcraft onto Ubuntu with Wine, without success, then Cedega, no success once again, and now I'm onto Crossover. Every time I start the blizzard download it pulls up where I want to install the game like normal, but once I choose a location it tells me "Invalid path chosen!" no matter which file path. 

There is one other thread like my problem that I've come across:
[http://osdir.com/ml/wine-users/2010-03/msg00308.html](http://osdir.com/ml/wine-users/2010-03/msg00308.html)

I tried this and it did not work. In the registry the file does not import. Though, I tried this in Cross.

Yes, I have read over almost every how to install Starcraft article.

---

### Post by techunit on 2010-05-02
C: drive in WINE is represented by Z: if I am not mistaken....

---

### Post by Flexia on 2010-05-02
I didn't know that, but that is what I've been using for the file path

---

### Post by techunit on 2010-05-02
Alright maybe you need to set the path as C:/Starcraft/ or Z:/Starcraft/

---

### Post by morgue on 2010-08-17
Choosing Z still doesn't work. The message Invalid patch chosen still shows up after choosing a folder during setup.

---

### Post by tripmix on 2010-08-17
I had this problem in wine once, I never figured out what was wrong but I managed to work around it by running as root.
```
xhost +
sudo wine installer.exe
```
See if that works.

EDIT: oh, and you might need to set up wine for the root account, probably just run sudo winecfg or something.

---

