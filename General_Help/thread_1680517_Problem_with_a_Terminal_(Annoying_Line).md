---
title: "Problem with a Terminal (Annoying Line)"
date: 2011-02-02
forum: General Help
---

### Post by TROQX on 2011-02-02
In every time when I opening the Terminal, there is annoying line displayed directly before terminal start :mad: >> see picture.
[B]How can I remove this line and fix the problem if it's exist ?
[/B]
```
bash: [: /etc/gedit: binary operator expected

```

---

### Post by sdennie on 2011-02-02
Does it only happen when you first open the terminal or after every command?  The problem is likely with your .bashrc file either way.  Posting the output of this might help:

```

grep gedit ~/.bashrc

```

If not, you may need to post your entire .bashrc file.

---

### Post by TROQX on 2011-02-03
> **sdennie said:**
> Does it only happen when you first open the terminal or after every command?  The problem is likely with your .bashrc file either way.  Posting the output of this might help:

```

grep gedit ~/.bashrc

```

If not, you may need to post your entire .bashrc file.

Yes, it's only happen when I first open the terminal not after every command.

When I executed the above command:

```
bash: [: /etc/gedit: binary operator expected
troqx@troqx:~$ grep gedit ~/.bashrc
if [ -z "$debian_chroot" ] && [ -r /etc/gedit ~/.bashrcdebian_chroot ]; then
troqx@troqx:~$ 
```

I open the bashrc file and found the complete code:

```
# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/[COLOR="DarkRed"]gedit[/COLOR] ~/.bashrcdebian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

```

---

### Post by cipherboy_loc on 2011-02-03
Do you mean /usr/bin/gedit?

My lines are:
> if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)


Cipherboy

---

### Post by AlphaLexman on 2011-02-03
> **TROQX said:**
> ```
if [ -z "$debian_chroot" ] && [ -r /etc/gedit ~/.bashrcdebian_chroot ]; then
```

'if [ -z "$debian_chroot" ]' means the variable is **zero** length, '**&&**', means both conditions must be true, '[ **-r** /etc/gedit ]' means the file exists and is readable, ; then 'debian_chroot=$(cat /etc/debian_chroot)' means we are replacing the empty variable with the output of 'cat /etc/debian_chroot'

This is a simple variable substitution and should not produce any errors. However there really shouldn't be a file by default at '/etc/gedit', so the **if** statement should fail because **both** arguments are not true (by default), is there an **else** statement following the conditional? 

Best to post your entire ~/.bashrc in [code ] tags please.

---

### Post by TROQX on 2011-02-03
This is my entire bashrc file:

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
if [ -z "$debian_chroot" ] && [ -r /etc/gedit ~/.bashrcdebian_chroot ]; then
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

#AndroidDev PATH 
export PATH=$PATH:/home/troqx/android-sdk-linux_86/tools
export PATH=$PATH:/home/troqx/android-sdk-linux_86/platform-tools

#Komodo
export PATH="/home/troqx/Komodo-IDE-6/bin:$PATH"

```

---

### Post by b0b138 on 2011-02-03
> **TROQX said:**
> This is my entire bashrc file:

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
if [ -z "$debian_chroot" ] && [ -r /etc/[COLOR="DarkOrange"]**_gedit ~/.bashrc_**[/COLOR]debian_chroot ]; then
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

#AndroidDev PATH 
export PATH=$PATH:/home/troqx/android-sdk-linux_86/tools
export PATH=$PATH:/home/troqx/android-sdk-linux_86/platform-tools

#Komodo
export PATH="/home/troqx/Komodo-IDE-6/bin:$PATH"

```

+1   Thats what mine looks like, minus the last two entries that look custom

This is also just a generic file that can be found at /etc/skel/

no wait..... mines a bit different

```
# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi
```

---

### Post by cipherboy_loc on 2011-02-03
Take the lines:

```

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/gedit ~/.bashrcdebian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

```

and replace it with:

```

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

```


What it looks like is that some how you pasted **gedit ~/.bashrc** into your .bashrc file.



Cipherboy

---

### Post by sisco311 on 2011-02-03
EDIT: I'm kinda slow today...

> **AlphaLexman said:**
> [ **-r** /etc/gedit ]' means the file exists and is readable,
[...] 
This is a simple variable substitution and should not produce any errors. 

Yep, but **[ -r /etc/gedit ~/.bashrcdebian_chroot ]** throws an error because -r is an unary operator, it expects only one argument...


@OP:

Don't know how, but you managed to paste **gedit ~/.bashrc** in your ~.bashrc file.  Most likely a mouse middle click accident... 

So, in your ~/.bashrc file replace:
```
# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/**gedit ~/.bashrc**debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi
```

with

```
# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi
```


BTW: the ~/.bashrc file is sourced, so you don't have to use export to set the PATH variable:

```
#AndroidDev PATH 
PATH=$PATH:/home/troqx/android-sdk-linux_86/tools
PATH=$PATH:/home/troqx/android-sdk-linux_86/platform-tools

#Komodo
PATH="/home/troqx/Komodo-IDE-6/bin:$PATH"

```

should do the trick as well. Just sayin'... :)

---

### Post by TROQX on 2011-02-04
[COLOR=Red]**PROBLEM SOLVED :p**[/COLOR]

Thank you guys for your helping, I really appreciate that.

=====================================

> **sisco311 said:**
> EDIT:
BTW: the ~/.bashrc file is sourced, so you don't have to use export to set the PATH 

I don't understand what did you mean !! can you explain more please.

---

### Post by cipherboy_loc on 2011-02-04
What he means is that you can take the lines:

```

#AndroidDev PATH 
export PATH=$PATH:/home/troqx/android-sdk-linux_86/tools
export PATH=$PATH:/home/troqx/android-sdk-linux_86/platform-tools

#Komodo
export PATH="/home/troqx/Komodo-IDE-6/bin:$PATH"

```


and change it to:

```

#AndroidDev PATH 
PATH=$PATH:/home/troqx/android-sdk-linux_86/tools
PATH=$PATH:/home/troqx/android-sdk-linux_86/platform-tools

#Komodo
PATH="/home/troqx/Komodo-IDE-6/bin:$PATH"

```


Cipherboy

---

### Post by AlphaLexman on 2011-02-04
Variables in a shell or a function are **local** by default, you must 'export' them to make them **global**, which means they are still available after the script or function finishes execution.

---

