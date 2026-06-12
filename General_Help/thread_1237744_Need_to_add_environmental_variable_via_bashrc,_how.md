---
title: "Need to add environmental variable via bashrc, how?"
date: 2009-08-11
forum: General Help
---

### Post by Kasperskii on 2009-08-11
Hey ubuntu guru's

I need to set java as an environmental variable, have tried to do
export JAVA_HOME="/usr/lib/jvm/java-6-sun-1.6.0.06;" >> .bashrc
and
export JAVA_HOME="/usr/lib/jvm/java-6-sun-1.6.0.06;" >> /etc/bashrc

But with the first, get no reaction, just a new line in Terminal and the second tells me permission denied

Many thanks to anyone that helps!

---

### Post by SoftwareExplorer on 2009-08-11
The first command sounds like it worked. Try running ```
cat ~/.bashrc
``` and seeing if the line you typed is at the end.

The second command didn't work because you didn't run it as the system administrator. To run a command as administrator add ```
sudo 
```(there's a space at the end of that) to the start of the command.

---

### Post by Kasperskii on 2009-08-11
> **SoftwareExplorer said:**
> The first command sounds like it worked. Try running ```
cat ~/.bashrc
``` and seeing if the line you typed is at the end.

The second command didn't work because you didn't run it as the system administrator. To run a command as administrator add ```
sudo 
```(there's a space at the end of that) to the start of the command.

cat ~/.bashrc gvies me a load of rubbish! lol
```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups
# ... and ignore same sucessive entries.
export HISTCONTROL=ignoreboth

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"

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
#force_colored_prompt=yes

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
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
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
if [ "$TERM" != "dumb" ] && [ -x /usr/bin/dircolors ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'

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

```

I also tried both of them with sudo in front:
```
admin@r26810:~$ sudo export JAVA_HOME="/usr/lib/jvm/java-6-sun-1.6.0.06;" >> .bashrc
[sudo] password for admin: 
sudo: export: command not found
admin@r26810:~$ sudo export JAVA_HOME="/usr/lib/jvm/java-6-sun-1.6.0.06;" >> /etc/bashrc
bash: /etc/bashrc: Permission denied

```

---

### Post by Johnny B on 2009-08-11
you dont need to use sudo on a file you own.
why not just open .bashrc with gedit and add the line to the end?

edit:  this might be what your looking for:
> echo 'JAVA_HOME="/usr/lib/jvm/java-6-sun-1.6.0.06;"' >> ~/.bashrc

---

### Post by DaithiF on 2009-08-11
Hi,
+1 for Johnny B's suggestion, as the first approach is kinda crazy ... if you really wanted to do it this way then you would need to use the echo command to append a line, so something like
echo "export JAVA_HOME=/path/to/your/jdk" >> .bashrc

but more importantly, I don't think you should be including the ';' in your JAVA_HOME.

cheers
D

---

### Post by Kasperskii on 2009-08-11
I second that!

Thanks  Johnny B, worked a charm!

Also I copy and pasted it from another tutorial about a mp3 codec, just changed it to java lol

I have no clue how to use shell commands lol

---

