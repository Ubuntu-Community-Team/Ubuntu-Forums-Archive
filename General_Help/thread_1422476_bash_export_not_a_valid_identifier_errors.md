---
title: "bash: export: not a valid identifier errors"
date: 2010-03-05
forum: General Help
---

### Post by cbeast on 2010-03-05
Hello all, 
I am a complete newbie to Ubuntu and have started diving in to try my hand at some Android programming.  In the course of setting up the Android SDK, I needed to update the PATH to know where the Android tools folder is.  I think I got that covered, but now every time I start the Terminal I get the following errors:
bash: export: `=': not a valid identifier
bash: export: `/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/beastie/android-sdk-linux_86/tools': not a valid identifier

Anyone have any ideas on what I did wrong or need to do to clean that up?
Thank you!

**_My /etc/environment file contents_**
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:"

**_My ~/.bashrc contents_**
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# don't overwrite GNU Midnight Commander's setting of `ignorespace'.
export HISTCONTROL=$HISTCONTROL${HISTCONTROL+,}ignoredups
# ... or force ignoredups and ignorespace
export HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)

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

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    #alias grep='grep --color=auto'
    #alias fgrep='fgrep --color=auto'
    #alias egrep='egrep --color=auto'
fi

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

# Path to the Android SDK
export PATH=${PATH}:/home/beastie/android-sdk-linux_86/tools

---

### Post by DaithiF on 2010-03-05
Hi, its not clear from the file you posted, but that error is what you would get if you had a space before and after the '='.   No spaces!

---

### Post by justniik on 2010-08-25
> **DaithiF said:**
> Hi, its not clear from the file you posted, but that error is what you would get if you had a space before and after the '='.   No spaces!


hay i also have a problem .......when i install cakephp...
and configur .bashrc file......aftere then my terminal showing error.......

bash: export: `/var/www/cakephp/console:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games': not a valid identifier
root@nikesh-laptop:~# gedit .bashrc
bash: gedit: No such file or directory

any command dos'n work in terminal
plz help what can i do??

---

### Post by DaithiF on 2010-08-25
try:```

/usr/bin/gedit .bashrc

```
look for the line that has:
```
export $PATH=.......

```
and remove the '$' so that it becomes:
```
export PATH=.......

```

---

### Post by justniik on 2010-08-25
hay lot of thanxxx.......my problem solved...

---

