---
title: "Aliases are deleted upon exiting the terminal"
date: 2011-03-09
forum: General Help
---

### Post by rottweiler1204 on 2011-03-09
I created 2 aliases to start with...
 
alias ls='ls --color'
alias rm='rm -i'
 
When I exit out of the terminal though, they aliases get wiped clean. How can I save this? 
 
I tried Googling this, and it mentioned two files, .bash_aliases and .bashrc, but it's going right over my head and confusing me.
 
Can someone please help me? All is appreciated.

---

### Post by debd on 2011-03-09
if you make aliases in the terminal, they will automatically be deleted after you close the session, i.e. the terminal window.
rather, open your home folder,
press ctrl+h
now search for the file  .bash_aliases
open it and create your aliases , save.

now whenever you open the terminal the aliases should work.

---

### Post by Habitual on 2011-03-09
create a new file in your /home directory called .aliases
(Notice the dot!)

Open .bashrc with 
```
vi + .bashrc
```

Press A (Shift +A) then Enter
should give you a new line and you'll be in insert mode.
Add
```
./home/xx/.aliases
alias reload='source ~/.bashrc'
```

Change xx to your username/LoginID (terminal > whoami)

Press ESC twice, then ZZ (has to be capitals)
type 'reload' and press enter.

Now you can edit ~/.aliases to your liking. Adding any aliases you like there.
After editing/saving, just type 'reload' in the terminal and you should be good to go.

HTH.

---

