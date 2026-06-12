---
title: "creating command line shortcuts"
date: 2012-09-06
forum: General Help
---

### Post by zapree on 2012-09-06
I just recently decided to jump back into ubuntu again after a 3 year haitus, and am having trouble remembering how to change my simple command line arguments.  The most basic one that I wanted to change was having ".." go up one directory, instead of having to type the full cd .. (lazy i know).  There is some file that I needed to get to to change which contains these modifiers, but I forget what it is.  Anyone got any ideas?

Thanks,

Eugene

---

### Post by Habitual on 2012-09-06
Terminal > 
```
nano ~/.bashrc
```and add this single line.
```
alias ..="cd .."
```then save it and exit nano.
```
source ~/.bashrc
```Open another terminal or tab and type 
```
.. <enter>
```These may help in the future:
[http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html) 
[http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html) 
[http://www.gnu.org/software/bash/manual/html_node/index.html](http://www.gnu.org/software/bash/manual/html_node/index.html)
[http://www.grymoire.com/Unix/Sh.html](http://www.grymoire.com/Unix/Sh.html)
[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/) 
[http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ)
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)

Eugene:
They are called "aliases"

Have a Great Day.

---

### Post by sisco311 on 2012-09-06
If you are using the default user shell, BASH, then you are looking for the ~/.bashrc file.

I prefere to keep my aliases in ~/.bash_aliases and functions in ~/.bash_functions. I *source* the files in ~/.bashrc:
```

...
[ -f ~/.bash_aliases ] && . ~/.bash_aliases
[ -f ~/.bash_functions ] && . ~/.bash_functions

```

If you want .. to go up one directory, you might want to enable the autocd option:
```
shopt -s autocd
```
If it's set,  a command name that is the name of a directory is executed as if it were the argument to  the  cd  command.

---

### Post by bodhi.zazen on 2012-09-06
put them in ~/.bashrc

```
alias ..='cd ..'
```

Tons of similar aliases are available via google.

See also [http://bodhizazen.net/Tutorials/envrc](http://bodhizazen.net/Tutorials/envrc)

I call .envrc from .bashrc (and .zshrc)

---

### Post by zapree on 2012-09-06
Thanks, that's exactly what I was talking about!

---

### Post by Cheesemill on 2012-09-06
A copy of my ~/.bash_aliases file for your enjoyment:
```
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias df='df -h -t ext4'
alias gipl='get_iplayer --nocopyright --output=/home/rob --tvmode=flashhd,flashvhigh,flashhigh,flashstd,flashnormal --get'
alias ipl='get_iplayer --nocopyright'
alias ls='ls -lh --color=auto'
alias paci='sudo pacman -S'
alias pacman='pacman-color'
alias pacr='sudo pacman -R'
alias pacs='pacman -Ss'
alias pacu='sudo pacman -Syyu'
alias sudo='sudo '
alias sv='sudo vim'
alias update-grub='sudo grub-mkconfig -o /boot/grub/grub.cfg'
alias vi='vim'
```
(You can ignore all of the pacman aliases, I'm on my Arch box at the moment).

---

### Post by JKyleOKC on 2012-09-06
One that I find extremely useful when I'm experimenting in a terminal and don't want to save all the wrong attempts in .bash-history is ```
alias zz=history -c;exit
```It clears the RAM copy of history so that nothing from that session is saved to the history file.

---

