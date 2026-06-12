---
title: "terminal question.."
date: 2012-05-14
forum: General Help
---

### Post by scottr99 on 2012-05-14
Hello, when I open a terminal it asks for a password, and when I submit my pw, it sits there for about 4-5 seconds and comes back with the following:

sshd is not running, starting the service...
Adding known_hosts entries for host scottr99fo-HP-Pavilion-dm4-Notebook-PC

The terminal does work, so I'm content with that.  But, I'd love to be able to part with a) having to enter my password, and b) the 4-5 second wait.  Also is the 'sshd' line an indication of something is wrong in the set-up?

I am running the latest version of Ubuntu, 12.

---

### Post by Enigmapond on 2012-05-14
Did you alter the .bashrc file in any way?

---

### Post by roelforg on 2012-05-14
Okay, what!?
It shouldn't ask for a pass when you hit CTRL-ALT-T
What were you trying to do?
Maybe that asked for a pass.

---

### Post by codemaniac on 2012-05-14
Can you please post the contents of your ~/.bashrc .It might be interesting !!

---

### Post by sudodus on 2012-05-14
It seems to log in via ssh. How to you open the terminal, which command or menu entry? Are you working locally (or are you trying to access another computer)?

---

### Post by scottr99 on 2012-05-14
Ctrl-Alt-T is how it happens, but it also happens if I use the shortcut terminal icon.  No I did not alter the .bashrc file.


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

# source variables for CAELinux packages
. /opt/.bashrc-CAE

```

---

### Post by matt_symes on 2012-05-14
Hi

Can you post the output of this file.
[LEFT]

```
cat /opt/.bashrc-CAE
```It is being sourced from your .bashrc file and is most lighly causing the problem.


Do you even need to source that file in .bashrc ? If not the just remove that line (cat /opt/.bashrc-CAE) from .bashrc using gedit.
 

Kind regards[/LEFT]

---

### Post by scottr99 on 2012-05-14
Hi Matt, yes that fixed it thank you!

> **matt_symes said:**
> Hi

Can you post the output of this file.
[LEFT]

```
cat /opt/.bashrc-CAE
```It is being sourced from your .bashrc file and is most lighly causing the problem.


Do you even need to source that file in .bashrc ? If not the just remove that line (cat /opt/.bashrc-CAE) from .bashrc using gedit.
 

Kind regards[/LEFT]


---

