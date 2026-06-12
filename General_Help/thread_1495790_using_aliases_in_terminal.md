---
title: "using aliases in terminal"
date: 2010-05-28
forum: General Help
---

### Post by Leo_Alexander_Gesvantner on 2010-05-28
im new to ubuntu and having some difficulty with terminal commands... alias in particular.  im trying to set an alias that will allow me to access files that are buried in the filesystem.  sometimes it works and sometimes it doesnt and i cant seem to find the key factor that is causing this.  also, when i do manage to get it working its never there when i restart the terminal.  can anyone help me figure out what im doing wrong?

---

### Post by Miyavix3 on 2010-05-28
> **Leo_Alexander_Gesvantner said:**
> access files that are buried in the filesystem

When you say 'access' what do you mean you want to do?

For some files in your fs, you will need root permission to work with files. This also depends on what command you want to run.

Also make sure you set your alias right.

Type this in a file called .bash_aliases
(It's a hidden file, so ctrl+h to unhide it)
If it doesn't exist, you can create it.

Insert:
```

alias thisismyAlias="ls *"

```

You can replace **thisismyAlias** and **ls *** with your own commands. 


In the file .bashrc

There's a line
```

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

```

Make sure you un-comment it:
```

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```

---

### Post by PyrexKidd on 2010-05-28
What alias are you trying to use?
Where are you setting it up?

I used to just modify .bashrc

but after taking down my computer I decided to change to .bash_aliases.
Much safer.

---

### Post by DOSIX on 2010-05-28
the problem you have with using aliases is this:

let's say you are fixing someone else's ubuntu system (or another distro that uses bash). your aliases won't be on that system, since they are created on your local computer. you probably won't be able to remember how to use the commands because you aliased them. since bash's commands are the same on every single computer, it would be a better idea to actually learn how to use the commands. the point i'm trying to make is that it's important to learn the commands, because it might help in other situations. even if you alias them, learn the commands anyway.

---

### Post by Penguin Guy on 2010-05-28
You need to put the [FONT="Courier New"]alias myalias='command'[/FONT] in your [FONT="Courier New"].bashrc[/FONT] (or [FONT="Courier New"].bash_aliases[/FONT] if you've enabled it) to keep the alias after a reboot.
As for the code; you'll need to post it here if you want help with it.

---

### Post by Leo_Alexander_Gesvantner on 2010-05-28
i managed to get the alias saved permanently so thank you all for your help with that.  as for the alias itself, it is not accessing any files that require root powers nor is it a replacement for typing the individual commands (as far as i know anyway). all it is for is to access a file in fofix that was buried in directory after directory (however i moved the parent directory (fofix-3.121) directly into my home directory which cut down the length of the path by about half, however it still isnt working, so here is the alias code along with the message i see when i invoke it.         


> alias fof='/home/gesvantner/fofix-3.121/src/FoFiX.py'        


 > gesvantner@ubuntu:~$ fof
Traceback (most recent call last):
  File "/home/gesvantner/fofix-3.121/src/FoFiX.py", line 108, in <module>
    from GameEngine import GameEngine
  File "/home/gesvantner/fofix-3.121/src/GameEngine.py", line 379, in <module>
    allthemes = os.listdir(themepath)
OSError: [Errno 2] No such file or directory: '../data/themes'
gesvantner@ubuntu:~$ 



 after moving the parent directory it is no longer as annoying navigating to that specific file, however if any of you can help me figure this out i would really appreciate it.

---

### Post by DaithiF on 2010-05-28
try:
```
alias fof='cd /home/gesvantner/fofix-3.121/src && ./FoFiX.py' 			 		
```
it looks like the script is looking for its theme directory relative to the current working directory, rather than the location of the script file.  So you need the alias to cd to the directory first before running the script.

---

### Post by Leo_Alexander_Gesvantner on 2010-05-28
i fixed the alias and its working now.  i decided to break it into two parts, the first of which would move to the ~/fofix-3.121/src directory, and the second would invoke the FoFiX.py file from there.  it works every time now.  thank you all for the help youve given me.

here is the modified alias:
```
alias fof='cd /home/gesvantner/fofix-3.121/src && ./FoFiX.py'
```

---

### Post by Leo_Alexander_Gesvantner on 2010-05-28
> **DaithiF said:**
> try:
```
alias fof='cd /home/gesvantner/fofix-3.121/src && ./FoFiX.py'                      
```it looks like the script is looking for its theme directory relative to the current working directory, rather than the location of the script file.  So you need the alias to cd to the directory first before running the script.

yeah thank you... i managed to get it working right before i read your post but you are correct and that is what is was looking for.

---

