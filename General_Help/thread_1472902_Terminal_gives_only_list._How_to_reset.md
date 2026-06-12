---
title: "Terminal gives only list. How to reset"
date: 2010-05-04
forum: General Help
---

### Post by panachippara on 2010-05-04
I am new to Linux. All of a sudden my terminal output changed from the traditional looks to giving only lists(one item per line) as output to "ls" command. Because of this, when there is a large number of files in a directory, I have to scroll up and down to see all files. A link to the screen shot is given below.

[IMG]http://s859.photobucket.com/albums/ab156/panachippara/?action=view&current=screenshot.jpg%22%20target=%22_blank%22%3E%3Cimg%20src=%22http://i859.photobucket.com/albums/ab156/panachippara/screenshot.jpg[/IMG]
">[[IMG]http://i859.photobucket.com/albums/ab156/panachippara/screenshot.jpg[/IMG]]("http://s859.photobucket.com/albums/ab156/panachippara/?action=view&current=screenshot.jpg")


I tried  "reset" and did not make any difference. Please help

---

### Post by DomesDKG on 2010-05-04
try "ls -x"
also, look though "man ls" to see if there's anything else that might work better.

---

### Post by sisco311 on 2010-05-04
what's the output of:
```
alias ls
```and```
grep alias ~/.bashrc /etc/bash.bashrc ~/.profile /etc/profile
```
?

---

### Post by panachippara on 2010-05-04
> **sisco311 said:**
> what's the output of:
```
alias ls
```and```
grep alias ~/.bashrc /etc/bash.bashrc ~/.profile /etc/profile
```?


alias ls gives

alias ls='ls --color=auto'

grep alias ~/.bashrc /etc/bash.bashrc ~/.profile /etc/profile

gives 


/home/joy/.bashrc:# enable color support of ls and also add handy aliases
/home/joy/.bashrc:    alias ls='ls --color=auto'
/home/joy/.bashrc:    #alias dir='dir --color=auto'
/home/joy/.bashrc:    #alias vdir='vdir --color=auto'
/home/joy/.bashrc:    alias grep='grep --color=auto'
/home/joy/.bashrc:    alias fgrep='fgrep --color=auto'
/home/joy/.bashrc:    alias egrep='egrep --color=auto'
/home/joy/.bashrc:# some more ls aliases
/home/joy/.bashrc:#alias ll='ls -l'
/home/joy/.bashrc:#alias la='ls -A'
/home/joy/.bashrc:#alias l='ls -CF'
/home/joy/.bashrc:# ~/.bash_aliases, instead of adding them here directly.
/home/joy/.bashrc:if [ -f ~/.bash_aliases ]; then
/home/joy/.bashrc:    . ~/.bash_aliases

I did not change anything knowingly. Rather I do not have that much knowledge.

---

### Post by panachippara on 2010-05-04
> **DomesDKG said:**
> try "ls -x"
also, look though "man ls" to see if there's anything else that might work better.

I did that and there was no difference. Will try man pages. But if someone has any suggestions that will be great

---

### Post by StuartN on 2010-05-04
> **panachippara said:**
> All of a sudden my terminal output changed from the traditional looks to giving only lists(one item per line) as output to "ls" command.

The output of ls is determined by the width of the widest item, so the columns are as wide as the longest file name. Most likely you have a very long file name in the directory you are listing.

---

### Post by panachippara on 2010-05-04
> **StuartN said:**
> The output of ls is determined by the width of the widest item, so the columns are as wide as the longest file name. Most likely you have a very long file name in the directory you are listing.

wow!! That is correct. You are a true Ubuntu guru. Many thanks

---

