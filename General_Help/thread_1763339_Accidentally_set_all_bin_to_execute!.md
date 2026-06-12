---
title: "Accidentally set all bin to execute!"
date: 2011-05-20
forum: General Help
---

### Post by dmdzado on 2011-05-20
I was in the wrong directory when I did a chmod +x *.bin, so now all of my commands in the terminal come back with the error "Cannot execute binary file." From ls, to cd .. I get this error. I seem to be able to do things with sudo, but does anyone know how to fix all of my permissions so that basic terminal commands come back??

Thanks

David

---

### Post by WorMzy on 2011-05-20
Which directory were you in when you ran that command? Did you run the command with sudo?

"cd" is a shell command, so that shouldn't be giving you a "Cannot execute binary file" error.

---

### Post by matt_symes on 2011-05-20
Hi

> **dmdzado said:**
> I was in the wrong directory when I did a chmod +x *.bin, so now all of my commands in the terminal come back with the error "Cannot execute binary file." From ls, to cd .. I get this error. I seem to be able to do things with sudo, but does anyone know how to fix all of my permissions so that basic terminal commands come back??

Thanks

David

What directory were you in ? Did you chmod recursively ? Do you have a live CD/USB handy ?

BTW: Why did you use a wildcard ?

Kind regards

---

### Post by dmdzado on 2011-05-20
sorry, not the cd command. 
 
I'm pretty sure I was in the home folder.
 
I used the wildcard cause I thought I was in a folder with a ton of bin files for a dev board SDK I was trying to execute and install. I was following some documentation.

---

### Post by WorMzy on 2011-05-20
post the output of ```
ls -la ~ | grep "\.bin"
```

---

### Post by matt_symes on 2011-05-20
Hi

> **dmdzado said:**
> sorry, not the cd command. 
 
I'm pretty sure I was in the home folder.
 
I used the wildcard cause I thought I was in a folder with a ton of bin files for a dev board SDK I was trying to execute and install. I was following some documentation.

Can you post a link to the documentation you were following ? Either that or post it here. Changing .bin files in your home directory should not stop you using ls etc. I think the issue may be due to something else.

EDIT: So there are not too many cooks, i will bow out and WorMzy can handle this one.

Kind regards

---

### Post by dmdzado on 2011-05-20
@matt
 
I'll have to dig it up.  I assumed that's what I did, judging from the binary file executing error. 
 
Actually, when the terminal first starts, I get these errors:
 
bash: /home/d/bin/uname: cannot execute binary file
bash: [: =: unary operator expected
bash: /home/d/bin/sed: cannot execute binary file
bash: /home/d/bin/ls: cannot execute binary file

---

### Post by matt_symes on 2011-05-20
Hi

> **dmdzado said:**
> @matt
 
I'll have to dig it up.  I assumed that's what I did, judging from the binary file executing error. 
 
Actually, when the terminal first starts, I get these errors:
 
bash: /home/d/bin/uname: cannot execute binary file
bash: [: =: unary operator expected
bash: /home/d/bin/sed: cannot execute binary file
bash: /home/d/bin/ls: cannot execute binary file

Post the output of

```
cat /home/d/.bashrc
```

and

```
echo $PATH
```

Kind regards

---

### Post by dmdzado on 2011-05-20
so I found out that I probably did chmod +x *.bin in usr/bin....
**note I had to use sudo so this would even work
 
[EMAIL="d@ubuntu:/bin$"]d@ubuntu:/bin$[/EMAIL] sudo cat /home/d//.bashrc
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
# If this is an xterm set the title to [EMAIL="user@host:dir"]user@host:dir[/EMAIL]
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

[EMAIL="d@ubuntu:/bin$"]d@ubuntu:/bin$[/EMAIL] echo $PATH
 
/home/d/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

---

### Post by dmdzado on 2011-05-20
so anything in that usr/bin file I can't call without sudo, or i get the "cannot execute binary file"

---

### Post by matt_symes on 2011-05-20
Hi

Your .bashrc file looks fine.

If you open a terminal and type

```
/bin/ls
```

does it print the directory contents of your current directory ?

Kind regards

---

### Post by dmdzado on 2011-05-20
it doesn't. I am just going to reinstall the whole thing. Thanks for your help. I'll have to be more careful when messing with permissions!

---

### Post by WorMzy on 2011-05-20
Yeah, something here really doesn't add up. Firstly, there are no .bin files in /bin or /usr/bin. Secondly, everything in those directories should have the executable bit set in the first place, so "chmod +x"ing them shouldn't make a blind bit of difference.

I suspect that there's something (or, indeed, several somethings) in your ~/bin folder that are trying to get executed in place of the "real" commands.

These errors in particular add weight to that theory:
> bash: /home/d/bin/uname: cannot execute binary file
 bash: [: =: unary operator expected
 bash: /home/d/bin/sed: cannot execute binary file
 bash: /home/d/bin/ls: cannot execute binary file

I'm not sure if that would explain why calling the "broken" commands with sudo works or not (I've never had any use for a ~/bin, I don't know if it gets used in sudo's $PATH or not).

If this is, as I suspect, the cause of the problem, either remove or rename ~/bin, or edit ~/.profile so that the following lines:

```
if [ -d "$HOME/bin" ] ; then
    PATH="[COLOR="#ff0000"]$HOME/bin[/COLOR]:[COLOR="Green"]$PATH[/COLOR]"
fi
```

look like this:

```
if [ -d "$HOME/bin" ] ; then
    PATH="[COLOR="Green"]$PATH[/COLOR]:[COLOR="#ff0000"]$HOME/bin[/COLOR]"
fi
```

I honestly don't know why the default is that executables in ~/bin get precedence over system executables. :/

EDIT: looks like I took a little too long writing that up, hopefully you see this before you reinstall.

---

### Post by matt_symes on 2011-05-20
Hi

@Wormzy 

I agree something strange is going on. 

The only thing i could think it might be are aliases changing the executables to point elsewhere, but i think that is ruled out.

Maybe a reinstall is the quickest method to fix this.

Kind regards

---

