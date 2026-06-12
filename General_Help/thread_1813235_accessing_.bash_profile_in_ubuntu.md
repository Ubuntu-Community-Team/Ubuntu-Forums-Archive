---
title: "accessing .bash_profile in ubuntu"
date: 2011-07-27
forum: General Help
---

### Post by itba on 2011-07-27
hi,

I need to add the following to my .bash_profile file.     
```

PATH=$PATH:/home/<username>/bin

```I couldn't find any .bash_profile file, and upon googl'ing saw that I needed to create one, so I did as follows:
```

touch ~/.bash_profile
chmod 700 ~/.bash_profile

```but I don't know how to access it and add PATH.

can you please help....thanks!

---

### Post by nothingspecial on 2011-07-27
Add it to .bashrc instead

```
echo 'PATH=$PATH:/home/<username>/bin' | tee -a ~/.bashrc
. ~/.bashrc
```

Make sure you use single quotes and don't forget the -a or you will overwrite your .bashrc

---

### Post by itba on 2011-07-27
perfect, thanks ...I did that
and had to do it per the instructions on the ActivePerl website to get ActivePerl going.
but now when I type
perl -V
I still see my original Perl v5.10 something...no sight of ActivePerl....any idea why?....this is probably an unrelated question, but I figured I'd ask anyways....

---

### Post by bodhi.zazen on 2011-07-27
Add this to .bashrc

```
if [ -d $HOME/bin ]; then
PATH=$PATH:$HOME/bin
fi
```

When you start a program, perl, it searches the path in order. If you want to use the perl in $HOME/bin, rather then the system perl, add this

```
if [ -d $HOME/bin ]; then
PATH=$HOME/bin:$PATH
fi
```

Order on the path counts and you will need to source .bashrc or start a new shell.

If you are calling the new perl from scripts, add the PATH to ~/.bash_profile rather then .bashrc

If the file does not exist, create it, lol

---

### Post by nothingspecial on 2011-07-27
Thanks bhodi.zazen, for letting me type a big long post about how the order in which bash reads things when it is called affects things etc etc and then posting it yourself just as I was about to

](*,)


:p

---

### Post by itba on 2011-07-27
ok, so I went to my /etc directory and opened the bash.bashrc file and added the following:
```

if [ -d $HOME/bin ]; then PATH=$HOME/bin:$PATH fi
```and then typed 
```

$perl - V

```still the same system perl
when I do echo $PATH
I see $HOME/bin which was not there before

was I supposed to add both the if codes that bhodi.zazen mentioned to my bashrc

---

### Post by bodhi.zazen on 2011-07-27
> **itba said:**
> ok, so I went to my /etc directory and opened the bash.bashrc file and added the following:
```

if [ -d $HOME/bin ]; then PATH=$HOME/bin:$PATH fi
```and then typed 
```

$perl - V

```still the same system perl
when I do echo $PATH
I see $HOME/bin which was not there before

was I supposed to add both the if codes that bhodi.zazen mentioned to my bashrc

Post the output of

```
echo $PATH
```

Also, check the permissions of ~/bin/perl, make sure it is executable and that $HOME is not mounted noexec

---

### Post by itba on 2011-07-27
bodhi.zazen,
here's the output of 

```

echo $PATH

``````

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/ar/bin

```when I run a simple perl program test.pl, the first line of which I have
```

#!usr/bin/perl -w

``` it executes with the system perl so I suspect the permissions of ~/bin/perl are executable
how do I figure out if $HOME is not mounted noexec?

thanks!

---

### Post by bodhi.zazen on 2011-07-27
Well, as I said earlier, it appears your problem is that $HOME/bin is listed LAST in your path.

You need to list it FIRST, see my first post

```
if [ -d $HOME/bin ]; then
PATH=$HOME/bin:$PATH
fi
```

To see your mount options , use, well, mount

```
mount
```

---

### Post by AlphaLexman on 2011-07-27
@OP: You need to put bodhi.zazen's code in /home/ar/.bashrc **NOT** /etc/bash.bashrc

*Assuming your user directory based on your $PATH posted previously.*

---

### Post by nothingspecial on 2011-07-27
You need to understand how bash reads your $PATH

which is in order.

What I told you is fine, under normal circumstances, where you want a script or piece of independent software in your $PATH

However, if you want something that is already in your $PATH to be called first, then the path to it has to be in your $PATH before the other one (if you see what I mean).

The instructions I gave you added your new stuff to your $PATH.....


.....but


...... it fails because bash finds it in the first place it searches.

```
if [ -d $HOME/bin ]; then
PATH=$HOME/bin:$PATH
fi
```

that is the important bit.

It has to search /home/$USER/bin before the other places.

---

### Post by itba on 2011-07-27
ok, so I added bodhi.zazen's code in /home/ar/.bashrc

here's the .bashrc file
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


if [ -d $HOME/bin ]; then
PATH=$HOME/bin:$PATH
fi

```when I run mount, here's what I get:
```

/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ar/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ar)
/dev/sda2 on /media/46B40E89B40E7BA5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

```and 
```

echo $PATH

```now that I removed nothingspecial's line, it returns
```

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

how do I fix it?

---

### Post by nothingspecial on 2011-07-27
I don't remember anybody telling you to remove my line.

Have you understood what people have posted?

---

### Post by itba on 2011-07-27
sorry nothingspecial, I actually did
but when the echo $PATH was not putting my home directory first, I removed that line....
I have again run the command you posted, I've included bodhi.zazen's code in ~/.bashrc and it still doesn't work. I don't quite understand why?
with your line back in here's what it returns
```

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/ar/bin

```
where am I making the mistake?

---

### Post by bodhi.zazen on 2011-07-27
> **itba said:**
> sorry nothingspecial, I actually did
but when the echo $PATH was not putting my home directory first, I removed that line....
I have again run the command you posted, I've included bodhi.zazen's code in ~/.bashrc and it still doesn't work. I don't quite understand why?
with your line back in here's what it returns
```

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/ar/bin

```
where am I making the mistake?

Your .bashrc with these lines:> if [ -d $HOME/bin ]; then
PATH=$HOME/bin:$PATH
fi

Looked fine. You need to start a new shell as when you echoed your path

> /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/ar/bin

"/home/ar/bin" is still at the end of the list when it needs to be as the start of the list.

---

### Post by itba on 2011-07-27
just to clarify, these are the last few lines in my .bashrc file
```

PATH=$PATH:/home/ar/bin

if [ -d $HOME/bin ]; then
PATH=$HOME/bin:$PATH
fi

```having read everybody's postings again, I understand why we are doing this and that my echo $PATH should _NOT_ read this
```

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/ar/bin
```but rather
```

/home/ar/bin: /usr/loca/sbin:.....

```and that I need to start a new shell, so I ran 
```

xterm

```and echo $PATH in the new shell
now gives me the following:
```

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/ar/bin:/home/ar/bin

```it stubbornly seems to be stuck at the end of the list...and now it's appearing twice in the new shell (is that supposed to happen, or do I just need a drink?)
how can it be that difficult.................:confused:

---

### Post by bodhi.zazen on 2011-07-27
First you do not need to set your path twice ;)

Second, I assume your syntax is off as $HOME/bin keeps ending up at the end of your line.

---

### Post by itba on 2011-07-28
bodhi.zazen,
so I should leave only your code in there, removing this line, correct?
```

PATH=$PATH:/home/ar/bin

```

---

### Post by nothingspecial on 2011-07-28
Correct.

---

### Post by itba on 2011-07-28
well, so I figured I'd test by removing the if code in addition to nothingspecial's code
and now when I run echo $PATH, it's showing:
```

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/ar/bin

```that shouldn't be the case, should it?

---

### Post by nothingspecial on 2011-07-28
Did you type ```
. ~/.bashrc
``` after you altered it.

That is needed so bash will read your .bashrc again.

---

### Post by bodhi.zazen on 2011-07-28
Post your entire .bashrc please

The default .bashrc has an if statement to add ~/bin, you need to change it, so ~/bin is added first.

---

### Post by itba on 2011-07-28
yes nothingspecial, I did

bodhi.zazen, here's the .bashrc

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

if [ -d $HOME/bin ]; then
    PATH=$HOME/bin:PATH
fi

```

---

### Post by staticd on 2011-07-28
To access any of the files starting with '.' .bashrc .bash_profile ... go to the directory where they are stored in nautilus and Press Ctrl+h. that will show your hidden files. Also works with the file open dialog box. Handy when you don't want to use the terminal.

---

### Post by bodhi.zazen on 2011-07-28
> **itba said:**
> yes nothingspecial, I did

bodhi.zazen, here's the .bashrc

Thank you for posting that. I do not see anything obviously wrong.

Here is what I would try:

1. Start a new shell. This is as simple as typing "bash" in a terminal, and again check your path.

```
bash
echo $PATH
```

2. I doubt that will solve the problem, the only way it would is if your bashrc is not up to date or was changed.

3. Check what is in /etc/bashrc, update the path there if needed.

4. Comment out this line

> # If not running interactively, don't do anything
[ -z "$PS1" ] && return

Personally, there is rarely a need to check that. If you are running interactively, you should call .bashrc, otherwise, with scripts for example, use .bash_profile.

The only reason you would need to check if you are running interactively (that I can think of) is if you are echoing a lot of text and using scp or sftp.

You can check to see if for some reason you are not running the rest of .bashrc with the command

```
alias
```

That command should print out your aliases.

---

### Post by itba on 2011-07-28
bodhi.zazen
I shall try that and write back
meanwhile, I just ran this at the prompt
```

ar@ar-VGN-FZ190E:~$ if [ -d $HOME/bin ]; then PATH=$HOME/bin:PATH; fi
ar@ar-VGN-FZ190E:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/ar/bin

```and then I ran this:
```

ar@ar-VGN-FZ190E:~$ if [ -d $HOME/bin ]; then PATH=$HOME/bin:$PATH; fi
ar@ar-VGN-FZ190E:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/ar/bin

```I am perplexed, but maybe what you have suggested will fix it.

---

### Post by itba on 2011-07-28
I commented out the line you asked me to and also ran alias....here's what it returns 
```

alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'
alias egrep='egrep --color=auto'
alias fgrep='fgrep --color=auto'
alias grep='grep --color=auto'
alias l='ls -CF'
alias la='ls -A'
alias ll='ls -alF'
alias ls='ls --color=auto'

```btw, even when I started a new shell with 
```

bash
echo $PATH

```I get the same old stuff :(

---

