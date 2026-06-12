---
title: "location of PATH variable on netbook 10.10 maverick?"
date: 2010-11-13
forum: General Help
---

### Post by gregconquest on 2010-11-13
I'm trying to install Go (programming language):
[golang.org/doc/install.html]("http://golang.org/doc/install.html")
The installation was OK, but I can't find where the PATH variable is set for 10.10 netbook remix.

Can anyone help, please? 
```
~$ echo $PATH
```
gives:
```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

Thank you.
Greg

---

### Post by lmarmisa on 2010-11-13
I do not understand you. Maybe you need to add a new directory to the $PATH variable.

If so, follow these instructions.

Open a terminal and type:

```

gedit ~/.bashrc

```Add these two lines to the end of the file

```

PATH=$PATH:/path_for_Go_here
export PATH

```Finally type these two commands

```

. ~/.bashrc
echo $PATH

```and check if the new directory was added to the $PATH variable.

---

### Post by gregconquest on 2010-11-13
~/.bashrc
is an empty file for me. That is what I'm looking for.

Thank you,
Greg

---

### Post by lmarmisa on 2010-11-13
Is it empty?.

Are you sure?.

Do you not use the bash shell?.

Please, type these commands:

```

cd
ls -l .bas*

```This is the otput in my system:

```

luis@UB1010ENG:~$ ls -l .bas*
-rw------- 1 luis luis 3676 2010-11-13 16:12 .bash_history
-rw-r--r-- 1 luis luis  220 2010-10-10 13:40 .bash_logout
-rw-r--r-- 1 luis luis 3353 2010-10-10 13:40 .bashrc
luis@UB1010ENG:~$

```

---

### Post by gregconquest on 2010-11-13
I get:
> -rw------- 1 gregconquest gregconquest 1351 2010-11-13 21:51 .bash_history
-rw-r--r-- 1 gregconquest gregconquest  220 2010-04-24 16:33 .bash_logout
-rw-r--r-- 1 gregconquest gregconquest 3103 2010-04-24 16:33 .bashrc

And no, I don't think I use bash manually. I used gedit and Terminal. I don't know how this differs from bash.

It seems as though bashrc, or profile, or whatever it is, can be stored in several different places:
[ubuntu-ky.ubuntuforums.org/showpost.php?p=7420768&postcount=3]("http://ubuntu-ky.ubuntuforums.org/showpost.php?p=7420768&postcount=3")
But when I open these in gedit, they are all blank. This is true even if I invoke gedit with gksu:
```
gksu gedit ~/.bashrc
```
etc.

---

### Post by lmarmisa on 2010-11-13
Your file .bashrc is not empty. Its size is 3103 bytes. 

This is the file to edit if you wish to add a new dir to the path.

---

### Post by chaanakya_chiraag on 2010-11-13
can you type in
```
cd
cat .bashrc
```
and post the output here?

---

### Post by efflandt on 2010-11-13
Note that hidden files like .bashrc in your home directory have a leading dot.  If you want to see them in nautilus you have to hit Ctrl+H.

---

### Post by gregconquest on 2010-11-13
So, shouldn't
```
gksu gedit ~/.bashrc
```
show me the file with the details visible? It is an empty file for me.
```
gksu gedit etc/fstab
```
does show a regular fstab.

---

### Post by gregconquest on 2010-11-13
> **chaanakya_chiraag said:**
> can you type in
```
cd
cat .bashrc
```
and post the output here?


```

gregconquest@DELLmini9:~$ cat .bashrc
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

### Post by lmarmisa on 2010-11-13
You must not use super user privileges (gksu) for editing your .bashrc file.

---

### Post by gregconquest on 2010-11-13
> **lmarmisa said:**
> You must not use super user privileges (gksu) for editing your .bashrc file.

Thank you.

But using
```
gedit ~/.bashrc
```
also results in an empty file being opened.

---

### Post by lmarmisa on 2010-11-13
Hmmmm. This sounds very odd. :)

Anyway, try

```

cd
gedit .bashrc

```

---

### Post by gregconquest on 2010-11-13
> **lmarmisa said:**
> Hmmmm. This sounds very odd. :)

Anyway, try

```

cd
gedit .bashrc

```

Hmm. Both the above command, and the prior command, ```
gedit ~/.bashrc
```, bring up a full file if I enter them from terminal, but that is not where I was entering them. I was using the run command (ALT F2).

---

### Post by lmarmisa on 2010-11-13
Do not use ALT F2. Open a terminal in the graphical screen and type the commands in this terminal.

---

### Post by gregconquest on 2010-11-13
OK. Thanks, but how do you know which commands should be entered from Run Command and which from Terminal? Is editing fstab from Run Command different than editing bashrc?

---

### Post by gregconquest on 2010-11-13
And there is no PATH line in bashrc now. Were the other PATH variables set elsewhere? Can I add "PATH=" to bashrc as it exists now and add one more variable to the PATH?

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

### Post by lmarmisa on 2010-11-13
Add two new lines to the end of the file

```

PATH=$PATH:/home/your_account_name/go/bin
export PATH

```

---

### Post by gregconquest on 2010-11-13
Do this after the bottom "fi"? Do I need to add another "fi" after the two lines you suggested?

---

### Post by lmarmisa on 2010-11-13
No, simply follow the instructions.

---

### Post by gregconquest on 2010-11-13
OK. I did the above, then the following:
```

. ~/.bashrc
echo $PATH

```
and got:
```

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/gregconquest/go/bin

```

So, it is in my path now. Does this look OK, lmarmisa?

And thank you for your help.
G-)

---

### Post by lmarmisa on 2010-11-13
All seems pretty good.

But, are you able to play go?. Is the program correctly installed?.

Best regards, :)

Luis

---

### Post by gregconquest on 2010-11-13
It is not for the game "Go" / "Igo". This is for google's programming language "Go". And I can't check now to see if it is working. It all looks OK, though.

Thanks again,
Greg

PS It is 2am here, and Obama is going to be visiting the giant Buddha about 15km away tomorrow sometime. Good night.

---

### Post by VeeDubb on 2010-11-18
I'm feeling like an idiot here, but I don't have a file called .bashrc in my home folder.  The closest I have is a .bash_history

I just want /home/steve/bin added to my path.  What am i missing?

Just for the record, I've read the entire thread, and still get nothing.


```
steve@dekstop:~$ ls -l .bas*
-rw------- 1 steve steve 12473 2010-11-18 04:13 .bash_history

```

And I've tried from alt-F2, a terminal, and even switching over to VT 1, and logging into the terminal directly.  Same results across the board.

---

### Post by chaanakya_chiraag on 2010-11-18
That is really bizarre...if there is a file called /etc/environment, you can add it like this:
```
PATH=$PATH:/home/steve/bin
```
AFAIK, that should work...

---

### Post by VeeDubb on 2010-11-18
Wouldn't that make it global?  I only want to add /home/steve/bin to the path for user steve, not for everyone on the system.

---

### Post by lmarmisa on 2010-11-18
First at all, check if you are running bash in your terminal:

```

luis@UB1004ENG:~$ ps
  PID TTY          TIME CMD
 1567 pts/0    00:00:00 bash
 1610 pts/0    00:00:00 ps
luis@UB1004ENG:~$ ls -al .bash*
-rw------- 1 root root 2604 2010-09-19 21:32 .bash_history
-rw-r--r-- 1 luis luis  220 2010-07-26 05:35 .bash_logout
-rw-r--r-- 1 luis luis 3121 2010-08-28 06:23 .bashrc
luis@UB1004ENG:~$

```I copy here the contents of my file .bashrc (original file for Ubuntu 10.04):

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
#alias ll='ls -alF'
alias ll='ls -l'
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

### Post by VeeDubb on 2010-11-19
> **lmarmisa said:**
> First at all, check if you are running bash in your terminal.........


First of all, thank you!  I've been using linux for a long time, but I've never needed to creat my own .bashrc, and didn't know what to do.  Copying yours and adding /home/steve/bin to it worked just fine.

Second, I suspect that there is no .bashrc in the home folders on a clean install of 10.10.  It's probably like doing away with the xorg.conf files.  A clean install with no closed source drivers has either no xorg.conf these days, or a nearly blank one.  Once upon a time, every input and graphical device had to be manually configured in there.

---

### Post by lmarmisa on 2010-11-19
> **VeeDubb said:**
> 
...
Second, I suspect that there is no .bashrc in the home folders on a clean install of 10.10. 

The file .bashrc exists on a clean installation of 10.10 too. I don't know why this file is missing in your system:

```

luis@UB1010ENG:~$ ls -l .bash*
-rw------- 1 luis luis 4261 2010-11-19 04:37 .bash_history
-rw-r--r-- 1 luis luis  220 2010-10-10 13:40 .bash_logout
-rw-r--r-- 1 luis luis 3353 2010-10-10 13:40 .bashrc
luis@UB1010ENG:~$ 

```This is the content of the file (Ubuntu 10.10):

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

```

---

### Post by piquat on 2010-11-19
Just to add to this:

I think the key was hit on, on page 2.  The /etc/environment file.

I have a two week old install of 10.10.  I have no PATH variable listed in my .bashrc file.  I DO, however, have the file, and it's got a lot in it, but no PATH definition.

If I:
```
echo $PATH
```I get back:
```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```Oddly enough, this matches EXACTLY what's laid out in /etc/environment.

So to me it appears that I'm getting my current path from the /etc/environment file, and that's global.  If I want to add to that path for only my user, I need to add it to .bashrc or maybe .profile.

That sound correct?

---

