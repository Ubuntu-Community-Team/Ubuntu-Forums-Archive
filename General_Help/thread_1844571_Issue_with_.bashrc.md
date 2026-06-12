---
title: "Issue with .bashrc"
date: 2011-09-15
forum: General Help
---

### Post by xeNULL on 2011-09-15
Here is the .bashrc

```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# don't overwrite GNU Midnight Commander's setting of `ignorespace'.
HISTCONTROL=$HISTCONTROL${HISTCONTROL+:}ignoredups
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
#[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
    # We have color support; assume it's compliant with Ecma-48
    # (ISO/IEC-6429). (Lack of such support is extremely rare, and such
    # a case would tend to support setf rather than setaf.)
    color_prompt=yes
    else
    color_prompt=
    fi
fi

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}&#9484;&#9472;&#9472;[\t] [\W]
&#9492;&#9472;&#9472;&#9632; '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    #alias grep='grep --color=auto'
    #alias fgrep='fgrep --color=auto'
    #alias egrep='egrep --color=auto'

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

fi

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

## Dir shortcuts
alias back='cd ..'
alias home='cd ~/'
alias documents='cd ~/Documents'
alias downloads='cd ~/Downloads'
alias images='cd ~/Images'
alias music='cd ~/Music'
alias videos='cd ~/Videos'
alias external='cd /media/XEHD'
alias awm='cd 'cd ~/.config/awesome'

## Easier Apt 
alias install='sudo apt-get install'
alias remove='sudo apt-get remove'
alias update='sudo apt-get update'
alias upgrade='sudo apt-get update && sudo apt-get upgrade'
alias dupgrade='sudo apt-get update && sudo apt-get dist-upgrade'
alias orphand='sudo deborphan | xargs sudo apt-get -y remove --purge'
alias cleanup='sudo apt-get autoclean && sudo apt-get autoremove && sudo apt-get clean && sudo apt-get remove && orphand'
alias search='sudo apt-cache search'

## Other shortcuts
alias mocp='mocp -T blackwhite'  

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi
## STARTUP SCRIPT
#!/bin/bash
```

And that is giving this output everytime I start a terminal

```
bash: alias: `/home/xenull/.config/awesome

## Easier Apt 
alias install': invalid alias name
bash: alias: apt-get: not found
bash: alias: `install
alias remove': invalid alias name
bash: alias: apt-get: not found
bash: alias: `remove
alias update': invalid alias name
bash: alias: apt-get: not found
bash: alias: `update
alias upgrade': invalid alias name
bash: alias: apt-get: not found
bash: alias: update: not found

```

---

### Post by sisco311 on 2011-09-15
Welcome to the forums!


You have a typo in declaration of the awm alias:
```
alias external='cd /media/XEHD'
alias awm=[color=red]'cd [/color]'cd ~/.config/awesome'

## Easier Apt 
alias install='sudo apt-get install'

```

It should be:
```
alias awm='cd ~/.config/awesome'
```

---

### Post by xeNULL on 2011-09-15
Lol it is usually always something small like that *kicks self* thanks =]

EDIT: it has fixed that output and now it is showing

```
bash: alias: need: not found
bash: alias: to: not found
bash: alias: enable: not found
&#9484;&#9472;&#9472;[15:32:30] [~]
&#9492;&#9472;&#9472;&#9632; 

```

---

### Post by sisco311 on 2011-09-15
After fixing that typo the .bashrc posted works fine for me. Did you edit it in the meantime?

---

### Post by xeNULL on 2011-09-15
I fixed that typo and haven't changed anything but that is showing. I think I will just add clear to my bashrc startup script

---

