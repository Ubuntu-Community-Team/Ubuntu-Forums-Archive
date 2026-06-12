---
title: "prompt string too long.."
date: 2012-08-20
forum: General Help
---

### Post by scottr99 on 2012-08-20
Hi all, whenever I open up a terminal I see this as my command prompt:

scott@scott-HP-Pavilion-dm4-Notebook-PC:~$

which is WAY too long.  How can I change this?

Thanks, noob.

---

### Post by spjackson on 2012-08-21
You need to edit the file .bashrc in your home directory using a text editor. If the file does not exist then create it.

At the end, add a line:
```

PS1='$ '

```This will change your prompt to just a dollar sign followed by a space. (This all assumes that your shell is Bash, which is the default on Ubuntu.)

---

### Post by Vaphell on 2012-08-21
in standard configuration your .bashrc should already have that string defined so edit the line to suit your needs.
simple '$ ' is not too usable imo, you don't see the current location etc. If you want to show username use \u, path \w, eg PS1='\u:\w\$ '

---

### Post by vasa1 on 2012-08-21
I have a prompt very similar to what the OP reports.

For some reason, my .bashrc seems quite complicated. I haven't done anything to it myself. If it's different from the vanilla Ubuntu, it maybe because I installed Xfce 4.10. (This changed the appearance of my GRUB screen as well.)

So it's not clear which line containing PS1 has to be edited.

```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines or lines starting with space in the history.
# See bash(1) for more options
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# If set, the pattern "**" used in a pathname expansion context will
# match all files and zero or more directories and subdirectories.
#shopt -s globstar

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
```

---

### Post by vasa1 on 2012-08-21
I'd like to have a prompt that shows
\@     the current time in 12-hour am/pm format
and then
\w     the current working directory

So I imagine it would be like
PS1="[\@] \w $ "
but, if it's correct, I don't know where to put it in my .bashrc :(

Edit: I stuck this at the very end and it works
```
PS1="[\@] \w $ "
```
There are three spaces in that code.

Now, I see:
```
[04:54 PM] ~ $
[04:54 PM] ~ $ cd Desktop
[04:54 PM] ~/Desktop $

```

---

### Post by scottr99 on 2012-08-21
Sweet! It worked, thanks all! :)

---

### Post by codemaniac on 2012-08-21
I always like my prompt to show some important info and have enough space to accomodate my long command-line .Here is how it looks like .

```
echo $PS1
\[\033[35m\]$(/bin/date)\n\[\033[32m\]\w\n\[\033[1;31m\]\u@\h: \[\033[1;34m\]$(/usr/bin/tty | /bin/sed -e 's:/dev/::'): \[\033[1;36m\]$(/bin/ls -1 | /usr/bin/wc -l | /bin/sed 's: ::g') files \[\033[1;33m\]$(/bin/ls -lah | /bin/grep -m 1 total | /bin/sed 's/total //')b\[\033[0m\] -> \[\033[0m\]
```

---

### Post by scottr99 on 2012-08-21
Actually one other thing is terminal opens up to the Documents directory.  I'd prefer it opened up to my home directory.  Is this in the .bashrc as well?  I didn't see it in there.

---

### Post by spjackson on 2012-08-21
> **scottr99 said:**
> Actually one other thing is terminal opens up to the Documents directory.  I'd prefer it opened up to my home directory.  Is this in the .bashrc as well?  I didn't see it in there.
If you still need help, then the thread isn't really solved.

This doesn't happen to me on Ubuntu 12.04 (Unity), Ubuntu 10.04, Lubuntu 12.04, Xubuntu 12.04. It seems odd to me.

The only thing similar is that if you start a new terminal from the terminal menu, its current directory will be the same as the starting terminal.

What happens if you start a terminal in this manner? i.e. start a terminal, cd /tmp then start a new one from your first terminal's menu?

I can't see anything in your .bashrc that does
```

cd ~/Documents

```so it doesn't look like .bashrc is doing this. I wouldn't expect it to either. .bashrc sources other files, and there could be a cd in one of these, but again that seems unlikely.

You could "correct" it putting
```

cd ~

``` in .bashrc, but that solution seems wrong to me - it works but doesn't address the root cause. It would break the behaviour described above of starting a new terminal from within an old one.

Assuming you are using gnome-terminal, it has a --working-directory=DIRNAME option, so I suspect that this is being set by the launcher, but I rarely use Unity, so I don't know much about where that might be set. (Most [maybe all] other terminal programs have the same option.)

---

### Post by vasa1 on 2012-08-21
> **spjackson said:**
> If you still need help, then the thread isn't really solved.
Actually, OP should be encouraged to **open a new thread** since the issue now has nothing to do with prompt length.
> **spjackson said:**
> 
... I can't see anything in your .bashrc ...
OP has not revealed the .bashrc contents, AFAICT.

---

### Post by scottr99 on 2012-08-22
Thanks I'll start a new thread, cause I checked multiple terminals and I get the same effect.

---

### Post by Zvlwab on 2012-08-22
By default it shows:
```
username@hostname:workingdirectory$
```

I think you should just change your hostname.
You can edit it by editing /etc/hostname and then reboot.

---

### Post by MG&amp;TL on 2012-08-22
> **Zvlwab said:**
> By default it shows:
```
username@hostname:workingdirectory$
```I think you should just change your hostname.
You can edit it by editing /etc/hostname and then reboot.

You'll want to change that value in /etc/hosts as well. 

Probably easier to run:

```
gksu gnome-control-center
```

then click on 'Details'  and change the name there.

---

