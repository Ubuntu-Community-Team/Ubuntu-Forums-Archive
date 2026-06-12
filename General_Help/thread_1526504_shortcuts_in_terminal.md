---
title: "shortcuts in terminal"
date: 2010-07-08
forum: General Help
---

### Post by l3ecl on 2010-07-08
when type ~ in the terminal, it sends me to the directory /home/user. is there a way for me to make my own shortcut, lets say 
typing # gets me to /home/user/Desktop/someFolder1/?

since terminal loads in the / directory by default, i keep having to type: " cd~/Desktop/someFolders..." constantly in order to access my files. also, are there alternative ways to do this all while in the terminal (not talking about desktop shortcuts)?

---

### Post by xifer on 2010-07-08
> **l3ecl said:**
> 

since terminal loads in the / directory by default,

Huh? no it doesn't.  not unless something is specifically changing the directory after you login or / is set as the users home directory.  look for files like .bash_profile .bashrc .profile in your user home directory which might be doing this.  See if there are any cd commands in there.

You can easily create scripts and store them in /usr/bin or your home directory to change to specific locations.

e.g. create a file called cds and put this in it

```

#bash
cd $HOME/Documents/somedir

```

execute it whenever you want.

Or add some alias commands into your .bashrc config file

lines like this

alias cdf = 'cd ~/Documents/somedir'

---

### Post by nothingspecial on 2010-07-08
You want to know some bash shortcuts?

Here you go :D


```
Key    Action
Ctrl-a Move cursor to the beginning of the line.
Ctrl-e Move cursor to the end of the line.
Ctrl-f Move cursor forward one character; same as the right arrow key.
Ctrl-b Move cursor backward one character; same as the left arrow key.
Alt-f  Move cursor forward one word.
Alt-b  Move cursor backward one word.
Ctrl-l Clear the screen and move the cursor to the top left corner. The
       clear command does the same thing.






Key    Action
Ctrl-d Delete the character at the cursor location
Ctrl-t Transpose (exchange) the character at the cursor location with the
       one preceding it.
Alt-t  Transpose the word at the cursor location with the one preceding it.
Alt-l  Convert the characters from the cursor location to the end of the
       word to lowercase.
Alt-u  Convert the characters from the cursor location to the end of the
       word to uppercase.



Key       Action
Ctrl-k    Kill text from the cursor location to the end of line.
Ctrl-u    Kill text from the cursor location to the beginning of the line.
Alt-d     Kill text from the cursor location to the end of the current word.
Alt-      Kill text from the cursor location to the beginning of the current
           Backspace word. If the cursor is at the beginning of a word, kill the previous
           word.
Ctrl-y    Yank text from the kill-ring and insert it at the cursor location.
```

---

### Post by l3ecl on 2010-07-08
> **xifer said:**
> 
Or add some alias commands into your .bashrc config file

lines like this

alias cdf = 'cd ~/Documents/somedir'


thats what i was looking for! 

for future reference to anyone interested
 the command should be alias='cd ~......', notice the lack of spacing between the equal signs to make it work properly and the command source ~/.bashrc might be of some use to you.

---

