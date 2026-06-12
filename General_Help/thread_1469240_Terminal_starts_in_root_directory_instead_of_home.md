---
title: "Terminal starts in root directory instead of home"
date: 2010-05-02
forum: General Help
---

### Post by Gforce20 on 2010-05-02
After upgrading to Lucid, gnome-terminal and xterm both start in the root directory (/); I'd like for them to start in my home directory instead. I had added "cd /home/myname" to the end of .bashrc, and this worked well as a temporary fix, but was never necessary in Karmic. Furthermore, modifying .bashrc in this way renders Nautilus' "Open in Terminal" menu item useless, as it still opens the home directory instead of the folder Nautilus was viewing. Any ideas?

---

### Post by Ryan Dwyer on 2010-05-02
What do you get when you echo $HOME?

---

### Post by WorMzy on 2010-05-02
My terminals start in my home directory. Here's a copy of my .bashrc for comparison:

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
```

---

### Post by Ryan Dwyer on 2010-05-02
Your .bashrc is fine. Now what do you get when you echo $HOME? You probably just need to correct your home directory path in /etc/passwd.

---

### Post by nathan726 on 2010-05-04
Are you starting your Terminal using a keyboard shortcut by any chance?

Then you'll want to change the shortcut command to:

```
gnome-terminal --working-directory=/home/username
```

---

### Post by bmarius on 2010-05-04
> **nathan726 said:**
> Are you starting your Terminal using a keyboard shortcut by any chance?

Then you'll want to change the shortcut command to:

```
gnome-terminal --working-directory=/home/username
```

Thanks a lot, that solved it for me. Why on earth is this necessary? What's different from launching from a keyboard shortcut versus launching from Alt+F2 or Gnome-DO?

---

### Post by Gforce20 on 2010-05-04
`echo $HOME` returns my home directory.

> **nathan726 said:**
> Are you starting your Terminal using a keyboard shortcut by any chance?

Then you'll want to change the shortcut command to:

```
gnome-terminal --working-directory=/home/username
```

This will do fine for me; thanks for the help. :)

---

### Post by shadestalker on 2010-05-05
It looks like the solution for xterm, rxvt et al is a wrapper script.  I'm unable to come up with a syntax for the keyboard shortcut that allows multiple commands seperated by ;

Presumably we're inheriting the cwd from whatever handles keyboard shortcuts here, which I think is gnome.  pwdx output for compiz and the running gnome pieces on my Lucid install show that gnome-settings-daemon and all the panel applets (but not the panel) seem to be run from / .  Is it useful or desirable to run user-specific programs this way?

---

### Post by nathan726 on 2010-05-06
> **shadestalker said:**
> I'm unable to come up with a syntax for the keyboard shortcut that allows multiple commands seperated by ;

Are you looking for something like this:
```
gnome-terminal --execute bash -c "echo \"hello $USER\"; echo \"you are using \"`uname`; bash"
```

Or:
```
sh -c 'cd $HOME;xterm'
```

---

### Post by dowcet on 2010-05-15
> **Gforce20 said:**
> `echo $HOME` returns my home directory.

This will do fine for me; thanks for the help. :)

Ditto, thanks to Nathan726!

---

### Post by linfidel on 2010-08-20
Hi all,

I had a similar problem, and have a different take on the solution...

First of all, my keyboard shortcut worked, because I set it in the "Keyboard Shortcuts" menu under the standard "Run a Terminal" shortcut, which has no command that can be changed.

However, I have always had an alternate, custom shortcut for using a different profile (using shift with the normal shortcut), and this one began starting in the root directory.  This was entered at the end of the "Keyboard Shortcuts" menu, by pressing the "Add" button to add a custom shortcut.  I was able to fix it by using the command from Gforce20; I added it to my custom command by appending it, along with the double hyphens, so it now says: 
```
gnome-terminal --window-with-profile=MyProfileName --working-directory=/home/MyProfileDirectory
```Perhaps this will help someone with a similar problem.

---

