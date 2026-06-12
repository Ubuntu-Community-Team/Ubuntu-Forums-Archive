---
title: "Why ~/.bashrc does not work after change?"
date: 2009-12-07
forum: General Help
---

### Post by iamgzy on 2009-12-07
Try to install Oracle 10g on 9.10, find something really weird.

I though ~/.bashrc should be the one to manipulate the shell. But whatever change I made to it, the Terminal just works as usual, even if I put some typo within.

[COLOR=Red]and something more interesting is, when I open Terminal, it is only start as $ without my username, and I cannot use up arrow and down arrow to get previous commands, werid....[/COLOR]

[COLOR=DarkOrchid]I used to install Tshell by root, is that the reason? Does Tshell by pass .bashrc?[/COLOR]

Any master here has an idea?

Thank you


here is my full version of ~/.bashrc
-----------------------
<code>

# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# don't overwrite GNU Midnight Commander's setting of `ignorespace'.
export HISTCONTROL=$HISTCONTROL${HISTCONTROL+,}ignoredups
# ... or force ignoredups and ignorespace
export HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)

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

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

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


export ORACLE_HOME=/home/oracle/oracle/product/10.2.0/db_1
export LD_LIBRARY_PATH=$ORACLE_HOME/lib
ln *s /usr/bin/basename /bin/basename
ln *s $ORACLE_HOME/lib/libclient10.a $ORACLE_HOME/lib/libagtsh.a
$ORACLE_HOME/bin/genagtsh $ORACLE_HOME/lib/libagtsh.so 1.0 
#export ORACLE_OWNER=oracle
#export ORACLE_SID=ora1
#export ORACLE_TERM=xterm
export PATH=$ORACLE_HOME/bin:$ORACLE_HOME/Apache/Apache/bin:$PATH

</code>

---

### Post by DasEi on 2009-12-07
Did you open a new terminal window after saving b~,bashrc ?

---

### Post by iamgzy on 2009-12-07
> **DasEi said:**
> Did you open a new terminal window after saving b~,bashrc ?

Thank you for the quick reply
Yes, I did. But seems it does not work

---

### Post by iamgzy on 2009-12-07
Hi, can anyone help?
thanks a million..

---

### Post by Sam on 2009-12-07
```
ln *s /usr/bin/basename /bin/basename
ln *s $ORACLE_HOME/lib/libclient10.a $ORACLE_HOME/lib/libagtsh.a
```
Maybe it's because you have "ln *s" instead of "ln -s".

---

### Post by lloyd_b on 2009-12-07
> **Sam said:**
> ```
ln *s /usr/bin/basename /bin/basename
ln *s $ORACLE_HOME/lib/libclient10.a $ORACLE_HOME/lib/libagtsh.a
```
Maybe it's because you have "ln *s" instead of "ln -s".

Still won't work (probably).  I have no clue where $ORACLE_HOME is, but /bin is a root owned directory - the 'ln' command will fail without a 'sudo'.

These two lines should not *be* in ~/.bashrc - they are "run once" commands that should be executed in a shell (with sudo), not something that needs to be run every time you open a terminal window.

Lloyd B.

---

### Post by lostinxlation on 2009-12-08
export ORACLE_HOME=/home/oracle/oracle/product/10.2.0/db_1
export LD_LIBRARY_PATH=$ORACLE_HOME/lib
ln *s /usr/bin/basename /bin/basename
ln *s $ORACLE_HOME/lib/libclient10.a $ORACLE_HOME/lib/libagtsh.a
$ORACLE_HOME/bin/genagtsh $ORACLE_HOME/lib/libagtsh.so 1.0 
#export ORACLE_OWNER=oracle
#export ORACLE_SID=ora1
#export ORACLE_TERM=xterm
export PATH=$ORACLE_HOME/bin:$ORACLE_HOME/Apache/Apache/bin:$PATH


Why don't you just make those two links manually and you don't have to put link commands in .bashrc.
 
I'd suspect genagtsh thing(I don't know what it is and I'm not familiar with Oracle stuffs).
Comment it out and start a new shell to see what will happen.

---

### Post by lloyd_b on 2009-12-08
> I though ~/.bashrc should be the one to manipulate the shell. But whatever change I made to it, the Terminal just works as usual, even if I put some typo within.

and something more interesting is, when I open Terminal, it is only start as $ without my username, and I cannot use up arrow and down arrow to get previous commands, werid....

I used to install Tshell by root, is that the reason? Does Tshell by pass .bashrc?

~/.bashrc is read ONLY by the bash shell.  If you are running another shell, then it won't be read (unless it's "sourced" from another file).

In a terminal window, type "ps", and post the output.  This will tell us which shell you are running.

Also, in the terminal window, type "bash" to force execution of the bash shell, and see if your settings are taking effect.

Lloyd B.

---

### Post by z_mikowski on 2009-12-09
This is way old, but I found this page after a google search, and thought I'd share what problem I was having and the solution.

In short, .bashrc in Jaunty is **not** automatically sourced by the bash shell.  You need a .profile to do that, e.g, the standard profile shipped with Jaunty:

```
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
  . "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
```

How I got there:

I created a 'custom' home user account that did not have all the default files (e.g. .profile, or .bashrc, etc.) and added them by hand later.  Obviously, I missed one.

If you run into the same problem, simply compare an existing account added through the normal tools, e.g. adduser, to the problem account.  Look for .bashrc, .bash_profile, .profile, etc.  The source mechanisms for shell startup can be pretty complex, and may change from release to release (IIRC).

Hope this helps someone!

---

