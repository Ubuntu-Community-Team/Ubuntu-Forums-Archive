---
title: "etags: no input files specified."
date: 2010-02-20
forum: General Help
---

### Post by tirengarfio on 2010-02-20
Hi,

i have install Emacs and im trying to able the possibility to go to the definition of a function or a variable:

You can find this text below [here]("http://deep.syminet.com/emacside.html"):

> 
Assuming CODEDIR to be the top-level source directory, first update your ~/.bashrc like so:

alias mktags='cd $CODEDIR && etags `find $CODEDIR -name "*.[h|c]"` && cd -'

Then run:

source ~/.bashrc
mktags


Now, inside ~./.bashrc i have this line:


```
alias mktags='cd /opt/lampp/htdocs/rs && etags `find /opt/lampp/htdocs/rs -name "*.[h|c]"` && cd -'
```

My problem: when i execute "mktags", it says:

> etags: no input files specified.
	Try `etags --help' for a complete list of options.


What's wrong?

Javi

---

### Post by gmargo on 2010-02-20
Remove the pipe symbol from the pattern.  Try: "*.[hc]".  Unless you actually have filenames that end in "|", which would probably be really inconvenient.:D  You might also find it easier to maintain if written as a function instead of an alias.

---

### Post by tirengarfio on 2010-02-20
> **gmargo said:**
> Remove the pipe symbol from the pattern.  Try: "*.[hc]".  Unless you actually have filenames that end in "|", which would probably be really inconvenient.:D

Thanks, but the error is the same..


> **gmargo said:**
> You might also find it easier to maintain if written as a function instead of an alias.

What do you meand with this?

Anyway, here you have my ~/.bashrc, maybe the place where i have to write that line matters...


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
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
    ;;
*)
    ;;
esac

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

alias mktags='cd /opt/lampp/htdocs/rs && etags `find /opt/lampp/htdocs/rs -name "*.[hc]"` && cd -'

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

---

### Post by gmargo on 2010-02-20
Here's how I would do it in a shell function:

```

mktags()
{
    local olddir="$PWD"
    local tagdir="/opt/lampp/htdocs/rs"

    cd "$tagdir"
    if [ "$?" != "0" ]; then
        echo "directory $tagdir not found"
        return;
    fi

    # Could have used "etags -R"
    find "$tagdir" -type f -name '*.[ch]' -print | etags -L -
    cd "$olddir"
}


```

---

