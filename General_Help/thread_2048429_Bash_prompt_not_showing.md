---
title: "Bash prompt not showing"
date: 2012-08-26
forum: General Help
---

### Post by wobert on 2012-08-26
Hello

I have prompted the terminal from dashome and directly with ctrl+alt+t having the same result, the prompt is not appearing.  If I log into my computer with a guest, the terminal does show the prompt.  I do not know how to troubleshoot this one, it will be long and impractical to replace *bash files one by one until I find the corrupted one.  Will really appreciate help on this one.

By the way, I have the latest ubuntu release.

Thanks

---

### Post by papibe on 2012-08-26
Hi wobert.

Could you post the result of these commands?
```
diff /etc/skel/.bashrc ~/.bashrc

diff /etc/skel/.profile ~/.profile
```
Regards.

---

### Post by wobert on 2012-08-26
Hello papibe

Just did it on the Guest session and did not had any results. It just resulted with the prompt on a new line.

---

### Post by papibe on 2012-08-26
Thanks.

Could you running it on the account that has the problem?

Regards.

---

### Post by wobert on 2012-08-26
There is no way I can put any text into the bash window,
it is the black screen without the prompt, tried to paste the command you told me and hit enter, but nothing happens.

Any other options?

Thanks

---

### Post by wobert on 2012-08-28
Any other clue to fix this issue?

Thanks

---

### Post by drmrgd on 2012-08-28
Can you enter another TTY window and try from there.  You can access by pressing 'Ctrl + Alt + F1'.  To return back to your graphical session, press 'Ctrl + Alt + F7'.  

Maybe there is a problem with your terminal and not with your .bashrc file?

---

### Post by wobert on 2012-08-29
Thanks for your help!

the ouptut is :
diff:missing operand after ´/etc/skel/.bashrc~/.bashrc´

same case with the second commmand.

---

### Post by drmrgd on 2012-08-29
You need to put a space between the "/etc/skel/.bashrc" and "~/.bashrc".  Just copy and paste the commands that papibe listed in his post to make sure you don't put any typos in there.

---

### Post by wobert on 2012-08-29
Thanks for helping.

The output is for both commands:

No such file or directory

---

### Post by jwbrase on 2012-08-30
> **wobert said:**
> Thanks for helping.

The output is for both commands:

No such file or directory

This doesn't surprise me. /etc/skel/.bashrc doesn't exist on my system.

Could you open up ~/.bashrc in a text editor and post its contents?

Also, in your terminal, go to "Edit -> Profiles" and make sure that "Profile used when launching a new terminal" is set to "Default" (unless you've been creating your own profiles, "Default" should be the only profile that exists, so you should be fine here). If it's set to something other than "Default", that is probably your problem.

Then go to "Edit -> Profile Preferences" and then to the "Title and Command" tab.

If the "run custom command instead of my shell" box is ticked, untick it. Once again, if it is ticked, this is probably your problem.

---

### Post by wobert on 2012-08-31
The configuration from the terminal is fine, nothing to change.

I did notice, and did not recall, that I have a terminal to display it on the desktop, named "miterminal", this one is working well!


Can you please help me on how to print the contents of the folder you are requesting me?

Thanks

---

### Post by jwbrase on 2012-09-01
> **wobert said:**
> Can you please help me on how to print the contents of the folder you are requesting me?

It's not a folder, it's a file.

Open up your home folder in Nautilus, go to "Edit > Preferences" and make sure "Show hidden and backup files" is ticked. You should then be able to find the file ".bashrc" in your home folder.

Open it, highlight everything in the file, hit "Ctrl-C". Make a new post in this thread, and type: ```
[noparse][code]
```[/noparse][/code] 

Put the cursor between the code tags, and hit Ctrl-V.

Your post should then look like this:
```
[noparse][code]Whatever is in .bashrc
```[/noparse][/CODE]

Hit "Submit reply" and you're done. Preferences and make sure

---

### Post by wobert on 2012-12-01
Hello

Thanks for your help, and sorry for the delayed response.

Please see attached photo, the folder from basch did not appear even thought I ask to show everything on the preferences menu.

---

### Post by Vaphell on 2012-12-01
.bashrc is a file and you are looking at directories, scroll down.

---

### Post by wobert on 2012-12-01
Code:

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

