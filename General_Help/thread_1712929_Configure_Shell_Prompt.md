---
title: "Configure Shell Prompt"
date: 2011-03-23
forum: General Help
---

### Post by borgward on 2011-03-23
I need a complete list of the characters that the shell treats specially in the prompt string. (Escape Codes Used In Shell Prompts)

Also please list the string of escape codes used for the default shell prompt. (GNOME Terminal 2.29.6)

---

### Post by sisco311 on 2011-03-23
> **borgward said:**
> I need a complete list of the characters that the shell treats specially in the prompt string. (Escape Codes Used In Shell Prompts)


It depends what shell are you using. The default user shell in Ubuntu is bash, so check out:
```
man bash | less +/"^PROMPTING"
```

> **borgward said:**
> 
Also please list the string of escape codes used for the default shell prompt. (GNOME Terminal 2.29.6)

In bash, the value of PS1 is expanded and used as the primary prompt string:
```
echo $PS1
```

---

### Post by borgward on 2011-03-23
In bash, the value of PS1 is expanded and used as the primary prompt string:
```
echo $PS1
```[/QUOTE]

I messed up the shell prompt, so that will tell me what it currently is.

I need to know what the default shell prompt should be.

---

### Post by sisco311 on 2011-03-23
> **borgward said:**
> 
I messed up the shell prompt, so that will tell me what it currently is.

I need to know what the default shell prompt should be.

The value of PS1 should be in your ~/.bashrc file. If you changed the value of PS1 in ~/.bashrc, check out the default .bashrc file: /etc/skel/.bashrc

---

### Post by Telengard C64 on 2011-03-23
What sisco311 said, plus 
[http://www.gnu.org/software/bash/manual/html_node/Printing-a-Prompt.html#Printing-a-Prompt](http://www.gnu.org/software/bash/manual/html_node/Printing-a-Prompt.html#Printing-a-Prompt)

I also found this helpful
[http://lindesk.com/2009/03/customizing-the-terminal-the-prompt/](http://lindesk.com/2009/03/customizing-the-terminal-the-prompt/)

---

### Post by borgward on 2011-03-27
I did:

PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"

and then:

export PS1

I now have my prompt as xyz@1234:~$,(as it should be) however when I first open GNOME Terminal 2.29.6, or the terminal at F2 after I log in to F2 I get:

No command 'Fri' found, did you mean:
 Command 'ri' from package 'ri' (universe)
 Command 'gri' from package 'gri' (universe)
Fri: command not found
xyz@1234:~$

I was getting the above before I contacted the forum.

How do I remove:

No command 'Fri' found, did you mean:
 Command 'ri' from package 'ri' (universe)
 Command 'gri' from package 'gri' (universe)
Fri: command not found

I only get that when I first open a terminal, not every time the prompt appears.

---

### Post by sisco311 on 2011-03-27
As a quick fix you could restore the default .bashrc file:
```
cp /etc/skel/.bashrc ~/.bashrc
```

If you want to do future investigations to find out why this happened, then first backup the file then post its content:
```
cp ~/.bashrc ~/.bashrc.bkp
cp /etc/skel/.bashrc ~/.bashrc
```
post the output of:
```
cat ~/.bashrc.bkp
```

---

### Post by borgward on 2011-03-28
xyz@1234:~$ cat ~/.bashrc.bkp
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

-------

What is the skel directory?

---

