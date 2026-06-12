---
title: "sudo is broken"
date: 2010-03-15
forum: General Help
---

### Post by willc0de4food on 2010-03-15
Hello,

In Ubuntu 9.10, sudo was working properly except it would not let me run speedy as sudo. I would get an error message, which I believe stated "No such file or directory. However, I could run the command as my regular user (being prompted it needed escalated privileges), and I could run the user as root. So I tried to "fix" it so that I could run it via the sudo command. My fix, in turn, ended up breaking sudo. I edited a file which contained the directories for PATH (I made a backup of said file), and that didn't work. It further broke sudo. So I attempted to restore the backup file, however, sudo was still just as broken.
Now, whenever I try to execute any command with sudo I get:
> tim@linux-hp:~$ sudo -i
[sudo] password for tim: 
env: -i: No such file or directory
tim@linux-hp:~$ sudo gedit
env: gedit: No such file or directory
tim@linux-hp:~$ sudo apt-get update
env: apt-get: No such file or directory
tim@linux-hp:~$ sudo nautilus
env: nautilus: No such file or directory
tim@linux-hp:~$ sudo update-manager
env: update-manager: No such file or directory
tim@linux-hp:~$ sudo speedy deploy
env: speedy: No such file or directory
:(
I have since upgraded to Ubuntu 10.04 Alpha 3, with mild hopes that the upgrade would remedy my problem, but alas - it did not. Does anyone have any suggestions on how to get sudo back to a working condition?

Thanks

---

### Post by cgb on 2010-03-15
Just to make sure we understand the full problem, can you run one of the programs like gedit without sudo and it does not give this error?  From what you are showing it sounds like sudo is working and prompts for the password.  Its just the path is now messed up.  Let us know if you can still open gedit without sudo from terminal.

---

### Post by willc0de4food on 2010-03-15
Yes - I can run each of the aforementioned programs without sudo. Each acts exactly as it should taking into account the normal user privileges. The only time I get those errors is when pre-empting the program name with the sudo command.

---

### Post by cgb on 2010-03-15
So do you recall which file you had edited that created this issue?  Was it .bashrc or another system file?


Now that I think about it you probably edited another file like /etc/environment.  This file would effect all user accounts such as sudo but then .bashrc would be for individual users and would allow you to run commands listed in its path file.  Basically whatever file you changed is still messed up and you will need to correct this.  Let me know if you have any idea on which file and we should be able to help get it corrected..

---

### Post by prodigy_ on 2010-03-15
Try this command:
```
/usr/bin/sudo /usr/bin/apt-get -s update
```
If you won't get an error, it's definitely a problem with /etc/environment. The contents of this file should look like this: ```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```

---

### Post by willc0de4food on 2010-03-17
The file that I edited was /etc/environment

> **prodigy_ said:**
> Try this command:
```
/usr/bin/sudo /usr/bin/apt-get -s update
```
This command did work without producing an error.

> **prodigy_ said:**
> 
If you won't get an error, it's definitely a problem with /etc/environment. The contents of this file should look like this: ```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```
The above code matches the contents of my /etc/environment exactly. :(

---

### Post by cgb on 2010-03-18
That is strange if that is exactly what is in your environment file.  You may even want to copy and paste the contents prodigy_ provided to ensure that something isn't in your environment file that shouldn't be there.  Other then that hopefully someone else has some ideas since I'm not sure what else it could be.

---

### Post by lavinog on 2010-03-18
post the output of ```

ls -l /etc/environment
```

you should get 
```

-rw-r--r-- 1 root root  ...

```

---

### Post by willc0de4food on 2010-03-19
> **lavinog said:**
> post the output of ```

ls -l /etc/environment
```

you should get 
```

-rw-r--r-- 1 root root  ...

```
that is correct.
> tim@linux-hp:/usr/bin$ ls -l /etc/environment
-rw-r--r-- 1 root root 79 2010-03-17 13:11 /etc/environment

also, this is an odd error i received today. I'm not sure if it's related, but I feel like it is..
> ...
Fetched 4,204kB in 13s (300kB/s)                                                                                     
E: Sub-process gzip returned an error code (100)
E: Prior errors apply to /var/cache/apt/archives/plymouth-x11_0.8.0~-17_i386.deb
E: Prior errors apply to /var/cache/apt/archives/upstart_0.6.5-5_i386.deb
E: Prior errors apply to /var/cache/apt/archives/plymouth_0.8.0~-17_i386.deb
E: Prior errors apply to /var/cache/apt/archives/libplymouth2_0.8.0~-17_i386.deb
E: Prior errors apply to /var/cache/apt/archives/mplayer_2%3a1.0~rc3+svn20090426-1ubuntu15_i386.deb
E: Prior errors apply to /var/cache/apt/archives/mplayer-nogui_2%3a1.0~rc3+svn20090426-1ubuntu15_all.deb
debconf: apt-extracttemplates failed: 
dpkg: warning: 'sh' not found on PATH.
dpkg: warning: 'rm' not found on PATH.
dpkg: warning: 'tar' not found on PATH.
dpkg: warning: 'find' not found on PATH.
dpkg: warning: 'dpkg-deb' not found on PATH.
dpkg: warning: 'ldconfig' not found on PATH.
dpkg: warning: 'start-stop-daemon' not found on PATH.
dpkg: warning: 'update-rc.d' not found on PATH.
dpkg: 8 expected program(s) not found on PATH.
NB: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
sh: touch: not found
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by rnerwein on 2010-03-19
hi
you are shure that you only touched the /etc/environment - then try following ( i am running karmic koala 9.10 ) 
wc /etc/environment   --> should be:  1  1 79 /etc/environment
why - may be you have a space line in there or some unprintable characters.
to verfy if there are unprintable characters inside you can use "vi" ( set list ) but only if you know vi !
ciao

---

### Post by willc0de4food on 2010-03-19
> tim@linux-hp:~$ wc /etc/environment
 1  1 79 /etc/environment
:(
I did copy and paste the info posted by prodigy_ though it didn't appear to alter anything, and the problem persists. Sigh

---

### Post by Ancanus on 2010-03-19
Could you post the output of: 
# echo $PATH

Thanks.

---

### Post by willc0de4food on 2010-03-19
That's what I was just curious about as well. I'm not sure where my user's PATH is being set, but here's the output:
> tim@linux-hp:~$ echo $PATH
/var/lib/gems/1.8/bin:/home/tim/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
tim@linux-hp:~$ su
Password: 
root@linux-hp:/home/tim# echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

---

### Post by sandyd on 2010-03-19
nvm.

---

### Post by sandyd on 2010-03-19
> **willc0de4food said:**
> That's what I was just curious about as well. I'm not sure where my user's PATH is being set, but here's the output:
your user's path is set in the ~/.bashrc

what about
```

sudo echo $PATH
```

---

### Post by willc0de4food on 2010-03-19
That's what I thought but upon doing a search in my ~/.bashrc , there is no such term as 'gems'
```
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

alias sudo='sudo env PATH=$path'
```

---

### Post by Ancanus on 2010-03-19
alias sudo='sudo env PATH=$path'

^- Delete

---

### Post by willc0de4food on 2010-03-23
that did it :D thanks

---

