---
title: "Termina Help - Alias: command not found"
date: 2012-01-02
forum: General Help
---

### Post by TimEnid on 2012-01-02
Every time i open my terminal, the first two lines say ""alias: command not found". how do i get rid of this?

---

### Post by Lars Noodén on 2012-01-02
There's probably an error in your [font=Courier New].bashrc[/font] file.  What's the full error message?

---

### Post by TimEnid on 2012-01-05
this is what i get when i open my termina

&#8220;alias: command not found
&#8220;alias: command not found
tim@tim:~$

---

### Post by WorMzy on 2012-01-05
I assume you're using the bash shell? Post the contents of your .bashrc file here.

---

### Post by TimEnid on 2012-01-05
&#8220;alias: command not found
&#8220;alias: command not found
tim@tim:~$ . ~/.bashrc
&#8220;alias: command not found
&#8220;alias: command not found
tim@tim:~$

---

### Post by WorMzy on 2012-01-05
No no, post the *contents* of the file.

Open it in gedit, or use cat to print the contents to stdout, then copy and paste it into a new reply, in CODE tags preferably.

---

### Post by TimEnid on 2012-01-05
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
&#8220;alias android-connect=&#8221;mtpfs -o allow_other /media/GalaxyNexus&#8221;&#8221;
&#8220;alias android-disconnect=&#8221;fusermount -u /media/GalaxyNexus&#8221;&#8221;
```

---

### Post by matt_symes on 2012-01-05
Hi
> 
“alias android-connect=”mtpfs -o allow_other /media/GalaxyNexus”” 
“alias android-disconnect=”fusermount -u /media/GalaxyNexus””

It does not like the above two commands. Change them to

[FONT=monospace][/FONT]```
alias 'android-connect=mtpfs -o allow_other /media/GalaxyNexus'
alias 'android-disconnect=fusermount -u /media/GalaxyNexus'
```

Kind regards

---

### Post by TimEnid on 2012-01-05
> **matt_symes said:**
> Hi


It does not like the above two commands. Change them to

[FONT=monospace][/FONT]```
alias 'android-connect=mtpfs -o allow_other /media/GalaxyNexus'
alias 'android-disconnect=fusermount -u /media/GalaxyNexus'
```

Kind regards

remove the quotes and paste as you type it?

---

### Post by matt_symes on 2012-01-05
Hi

Remove the double quotes and add the single quotes. I have written it out of you above.

Kind regards

---

### Post by WorMzy on 2012-01-05
Yes. I'm not sure who or what told you to use 66's and 99's in those statements, but I'd definitely remove the first and last marks from both of those lines, and then replace the two remaining marks with standard ambiguous quote marks (") or apostrophes (').

```
alias android-connect="mtpfs -o allow_other /media/GalaxyNexus"
alias android-disconnect="fusermount -u /media/GalaxyNexus"
```

Matt's suggestion should work fine too.

---

### Post by TimEnid on 2012-01-05
> **matt_symes said:**
> Hi

Remove the double quotes and add the single quotes. I have written it out of you above.

Kind regards

thanks for the help guys. this helped a lot.

---

