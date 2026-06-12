---
title: "How to set terminal default path to pwd"
date: 2011-06-28
forum: General Help
---

### Post by legendbb on 2011-06-28
Open a new terminal either in tab or new windows,
The default work directory is $HOME
Does anyone know how to change it to `pwd`, so every time a new terminal starts form the same path as the mother terminal (the terminal user calls new from).

Thanks,:KS

---

### Post by nothingspecial on 2011-06-28
Well each time you start a new terminal you create a new shell, rather than a sub-shell of the one you started first.

Perhaps the best way would be to type

```
gnome-terminal . &
```

In the "mother terminal", leaving you the option of starting more terminals from her, new terminals or grandchild terminals from the child of the mother.

.....if you see what I mean.....

:-k

***Edit Actually, that's a load of nonsense. Good question. I'd like to know the answer too........ I mean it works, but it still acts like new shell.

---

### Post by lightstream on 2011-06-28
In terminal, you can just press Ctrl-Shift-T to create a new terminal, which will have the same working directory as the original.

Not sure how you could do the same by typing a command tho

---

### Post by collisionystm on 2011-06-28
[I][B]
NEVERMIND, WRONG ANSWER. HOWEVER THIS MAY STILL COME IN HANDY lol.[/B][/I] I didn't read your question all the way :p


> **legendbb said:**
> Open a new terminal either in tab or new windows,
The default work directory is $HOME
Does anyone know how to change it to `pwd`, so every time a new terminal  starts form the same path as the mother terminal (the terminal user  calls new from).

Thanks,:KS


Yes, you can change the directory that ssh will take you to by default. You do this by change the 'home' directory of the user.

Edit your /etc/passwd file
```

sudo nano /etc/passwd
```you should see something like this at the very bottom of the file.

> charles:mad::1000:1000:Charles,,,:/home/charles:/bin/bashChange this part
> 
/home/charlesto whatever path you would like it to point to.

Now next time you SSH it will take you there directly.

---

### Post by legendbb on 2011-06-28
Thank you guy, but I don't think those suggestion reach my purpose in uBuntu. 

I know Fedora does this, but haven't get change to dig out yet.

Who already knows the answer for uBuntu please add.

---

### Post by lightstream on 2011-06-28
> **legendbb said:**
> Open a new terminal either in tab or new windows

If you open Terminal and then choose 'Open Tab' or 'Open Terminal' from the File menu, it will open and have the currently active working directory.

Is that not good enough for you?

---

### Post by legendbb on 2011-06-28
> **lightstream said:**
> If you open Terminal and then choose 'Open Tab' or 'Open Terminal' from the File menu, it will open and have the currently active working directory.

Is that not good enough for you?
My gnome terminal doesn't work that way in uBuntu 10.10
Thanks anyways,

:KS

---

### Post by cowboy.bebop on 2011-06-28
I always thought you could it through: set PATH:<path-to-dir> for the envar.

---

### Post by Habitual on 2011-06-28
try this:
Alt+F2 then:
```
gnome-terminal --working-directory=/home/$(whoami)
```

after running with --working directory, new tabs should open in the same directory you are in when you open the new tab.

HTH.

---

### Post by legendbb on 2011-06-29
My deep deep sorry to all! :KS:KS:KS

I actually made change in .bashrc myself, since I have to cd to somewhere do something and come back. Since I did have a temp buf keeping pwd, I cd to $HOME.

I changed .bashrc and add:
TEMP=`pwd`
cd ...
  do jobs
cd ${TEMP}

---

