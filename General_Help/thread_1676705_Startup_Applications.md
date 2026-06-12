---
title: "Startup Applications"
date: 2011-01-27
forum: General Help
---

### Post by mtrobey on 2011-01-27
Every time I log in, there's a bunch of applications that open on startup, such as Rhythmbox, a pdf document, and like 3-4 windows of nautilus.  I've checked "Startup Applications," and none of these are listed, and it's set to NOT remember running applications.  I've also checked /.config/autostart, also to no avail...anybody have any ideas for other places I could look?

---

### Post by mharrison on 2011-01-27
Click on System -> Preferences -> Startup Applications

There are two tabs.  Click on the 2nd tab and there should be a checkbox that says relaunch applications on startup or something like that.  Make sure it is not checked.

HTH

---

### Post by mtrobey on 2011-01-27
Yup, it's not checked.

---

### Post by mharrison on 2011-01-27
> **mtrobey said:**
> Yup, it's not checked.

Sorry, been a long day, just re-read your original post.


---
Edit:

When you click on Logout, is there a checkbox that says to remember applications?

---

### Post by mtrobey on 2011-01-27
No, it just says "Are you sure you want to close all programs and log out of the computer?"

---

### Post by mharrison on 2011-01-27
I'm at work so I can't test this first, but you can run

```
gnome-session-properties
```

and poke around and see if you can find the culprit there.

---

### Post by mtrobey on 2011-01-27
Yeah, I've checked there, but none of these applications are checked.

---

### Post by mharrison on 2011-01-27
I know you said you checked your /.config/autostart but have you checked your .bashrc file?

---

### Post by mtrobey on 2011-01-27
I don't see anything in .bashrc, though I'm not really familiar with it...

here it is:

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

# Add an "alert" alias for long running commands.  Use like so:
#   sleep 10; alert
alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'

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

---

### Post by mharrison on 2011-01-27
I'm at a loss then.

I'm not sure what to tell you short of possibly closing all of your programs, going to the Startup Applications app and clicking the button to Remember Currently Running Applications and seeing if that does anything to stop the apps from auto starting.

---

### Post by mtrobey on 2011-01-27
Well, that solved it!  Maybe I clicked that before, so this time it overwrote it?  Thanks for your help.

---

### Post by mharrison on 2011-01-27
> **mtrobey said:**
> Well, that solved it!  Maybe I clicked that before, so this time it overwrote it?  Thanks for your help.

Whew!  Glad I was able to be of eventual assistance, :P

---

