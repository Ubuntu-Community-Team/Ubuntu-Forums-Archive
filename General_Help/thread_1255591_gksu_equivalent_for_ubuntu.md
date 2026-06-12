---
title: "gksu equivalent for ubuntu"
date: 2009-09-01
forum: General Help
---

### Post by pythonscript on 2009-09-01
Is there an equivalent of the gksudo /gksu command for icewm? I installed a command line only ubuntu interface, and then installed x and icewm on top of it, but I don't really want to pull in any gnome dependencies if I can help. Is there a graphical sudo for icewm? Thanks!

---

### Post by kerry_s on 2009-09-01
it is gksu/gksudo, if you installed gdm then you have it already.
it does not depend on much, if you don't have gdm use:
**sudo apt-get install --no-install-recommends gksu**

that will keep it small.

---

### Post by pythonscript on 2009-09-01
How can I show the results of your screenshot from the command line? Is this the same as the output from 

```
sudo aptitude show gksu
```or something else? I'd love to be able to show only the dependencies from the terminal. Thanks!

EDIT:  I don't have synaptic installed, hence the need for a terminal command.

---

### Post by kerry_s on 2009-09-01
```
apt-cache depends synaptic
```

sorry, i don't use aptitude, don't even have it installed.
you could look at the man pages, see what the commands are: **man aptitude**

i recommend you put your ~/.bashrc to work make you some alias's to save you typing.

mine:
```

alias !='sudo'
alias u='sudo apt-get update;sudo apt-get upgrade'
alias s='apt-cache search'
alias i='sudo apt-get install --no-install-recommends'
alias r='sudo apt-get purge'
alias ?='dpkg -l | grep'
alias c='sudo apt-get clean'
alias ch='clear;rm -f ~/.bash_history;history -c'
alias grep='grep --color'
alias less='most'
alias more='most'

```

---

### Post by pythonscript on 2009-09-05
Thanks for the tip. kerry_s, nice work on the aliases. I'd been forgetting about those, but that saves me a lot of typing. :)

---

