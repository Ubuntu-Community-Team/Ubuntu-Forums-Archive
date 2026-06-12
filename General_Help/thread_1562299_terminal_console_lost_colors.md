---
title: "terminal console lost colors"
date: 2010-08-27
forum: General Help
---

### Post by cybo on 2010-08-27
i'm using LucidLynx. for some reason my console lost all colors. and i can't restore them. does anybody know what happened?

---

### Post by AlphaLexman on 2010-08-27
Do you mean the directory colors when you type 'ls' or your prompt? or what? Can you give more detail?

---

### Post by WorMzy on 2010-08-27
Have you modified any of your bash config files?

A quick solution would be to add these into your ~/.bash_aliases file:

```
alias ls='ls --color=auto'
alias grep='grep --color=auto'
alias fgrep='fgrep --color=auto'
alias egrep='egrep --color=auto'
alias grep='grep --color=auto'
alias fgrep='fgrep --color=auto'
alias egrep='egrep --color=auto'
```

---

### Post by cybo on 2010-08-27
> **AlphaLexman said:**
> Do you mean the directory colors when you type 'ls' or your prompt? or what? Can you give more detail?

correct. when i type 'ls' i don't see any colors.

---

### Post by AlphaLexman on 2010-08-27
Wormzy's advise to set 'ls' as an alias is good, however the default setup should have that enabled already. So try it directly from the command line ->
```
ls --color=auto
```

---

### Post by cybo on 2010-08-27
> **WorMzy said:**
> Have you modified any of your bash config files?

A quick solution would be to add these into your ~/.bash_aliases file:

```
alias ls='ls --color=auto'
alias grep='grep --color=auto'
alias fgrep='fgrep --color=auto'
alias egrep='egrep --color=auto'
alias grep='grep --color=auto'
alias fgrep='fgrep --color=auto'
alias egrep='egrep --color=auto'
```

this file is missing from my home directory. it seems like it got deleted somehow. do you know if this file should have anything else?

---

### Post by WorMzy on 2010-08-27
Actually, it seems that Lucid doesn't have that file by default. But it should use it if it's there.

Instead, you can put aliases in ~/.bashrc

If you don't have that file either, then here's mine:

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
    [COLOR="Red"]alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'[/COLOR]
fi

# some more ls aliases
[COLOR="Red"]alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'[/COLOR]

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

I've made the aliases a different colour, just in case you have the file and want to compare.

---

### Post by AlphaLexman on 2010-08-27
I don't recall it exists by default. You'll have to make a new file. Just copy and paste Wormzy's text into a new file in gedit and save it as .bash_aliases 

Then make sure your .bashrc will 'call' the .bash_aliases file. You should have something like this ->
```
    if [ -f ~/.bash_aliases ]; then
        . ~/.bash_aliases
    fi

```If not, copy and paste that to your .bashrc file.

The .bash_aliases file does not need any special items in it (like a sha-bang), just alias ls='ls --color=auto'

Make sure to quote everything after the equal (=) sign and don't put any spaces around the equal sign.

---

### Post by cybo on 2010-08-30
thanks for help everyone. it turns out i accedentally deleted parts of my home folder. i simply reinstalled ubuntu. i know this is a lame solution but i needed some of those files and i didn't have anything important stored (not yet at least)

---

### Post by Emiliano Carvalho on 2013-01-23
I found the same problem when performing installations and some of them created the file .bash_profile, if the rvm that manages the settings of Ruby on Rails, repeating the same configuration in .bashrc

Check your settings in .bash_profile too.

---

### Post by overdrank on 2013-01-23
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

