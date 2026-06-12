---
title: "terminal default location"
date: 2011-06-30
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-06-30
every time i open it it is at / instead of ~
and cd ~ gets old after a while
it did this before but it fixed it self how i fix it now

---

### Post by sam_delta on 2011-07-01
thats strange... i dunno if theres a better way of fixing it but you could always add the command "cd ~" into your .bashrc file


sam

---

### Post by sandman887 on 2011-07-01
try adding this line to your .bashrc file in your home (~) directory:
```
export PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"

```

save the file and exit out of the terminal or log out, then log back in. Open up a new terminal window and see where your starting directory is.

This is what my PS1 environment variable is set to:
```
\[\e]0;\u@\h: \w\a\]${debian_chroot:+($debian_chroot)}\u@\h:\w$

```

and all my terminals start out in my home directory.

---

### Post by sandman887 on 2011-07-01
Also, you can see what your PS1 environment variable is by typing: ```
echo $PS1
```

---

### Post by pqwoerituytrueiwoq on 2011-07-01
it seems to have fixed itself again ???

---

### Post by pqwoerituytrueiwoq on 2011-08-25
i figured out the cause i have a script on hot key to toggle compiz
```
cat /opt/toggle-Metacity-and-Compiz.sh 
#!/bin/sh
if [ 0`pidof metacity` -gt 0 ]; then
    compiz --replace &
else
    metacity --replace &
fi
exit
```
any idea why to changes my default terminal location to /

---

### Post by pqwoerituytrueiwoq on 2011-08-30
any ideas as to why that script changes the default location?

---

### Post by Enigmapond on 2011-08-30
I don't think that script did it. There's nothing in there that would do it....it's got to be something in your bashrc file....

---

### Post by pqwoerituytrueiwoq on 2011-08-31
it only changes to / after i run the script a second time and only if i use the hot key control to launch it (only tried hot key and terminal)
i just added a cd ~ at the top/bottom (bottom alone did not work) and now it does not do it :/
```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoredups:ignorespace

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

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
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
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

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi

# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi

```

---

