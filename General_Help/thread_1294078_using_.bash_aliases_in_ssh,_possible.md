---
title: "using .bash_aliases in ssh, possible ?"
date: 2009-10-17
forum: General Help
---

### Post by iMisspell on 2009-10-17
Hello all...

When accessing a ubuntu-server (9.04) via SSH (putty v0.60) is it possible to use alias's from the .bash_aliases file ?

apt-cache policy ssh says... 1:5.1p1-5ubuntu1

.bash_aliases works fine when sitting in front of the computer, but not while using SSH.

Thanks for any help.

[edit]
Note:
I have tried to access the remote machine with both windows xp and standard ubuntu 9.04, both running putty and with the same username (which works fine at the servers terminal), and still no .bash_aliases functionality.



_

---

### Post by falconindy on 2009-10-17
You'll have access to the .bash_aliases file on the remote host, not your own.

---

### Post by iMisspell on 2009-10-17
Sorry i should have been more clear and included that.

The first (and only) test i ran was using a windows box (xp) to access the remote ubuntu server.

I'll give a shot at accessing the server from a different ubuntu client and see if it makes a difference.

_So to be clear..._
While using SSH (putty on a win-xp box) i do not have access to the remote machines .bash_aliases file. None of the remotes alias's are working in putty installed in windows.



Thanks for the feed back.

_

---

### Post by falconindy on 2009-10-17
Odd... I just tried SSH from Ubuntu to Ubuntu, and then from PuTTY to Ubuntu and got the same results... my .bash_aliases is available. What's the output of `alias` from PuTTY? And what's the expected output?

---

### Post by iMisspell on 2009-10-17
.bash_aliases
alias firewall='sudo ufw'


While at servers terminal:
$ firewall status
$ [sudo] password...
$ .... then, list off correct info....


While at putty on XP:
$ firewall status
$ -bash: firewall: command not found

While at putty on Ubuntu (standard - non-server - different machine):
$ firewall status
$ -bash: firewall: command not found

On both client machines, im logging in with the same username as i did while logging into the server itself.

I also created a symlink of the .bash_aliases file from the 'nomral_user@server' dir to the root/ dir

Im new to all of this...
Do you have to configure SSH for this to work ?

would openssh be better ?


[edit]
While at ubuntu's putty i tried:
$ sudo vi .bash_aliases

and it brought up the file on the remote machine with the correct info in it.

_

---

### Post by falconindy on 2009-10-18
Wait, so you're using PuTTY even from Ubuntu? That seems like a mistake. PuTTY actually does a great job of mimicking the functionality provided by the included SSH client -- but why use a knockoff when you've got the real thing already?

The only "config" I've done with SSH is:
1) Established an RSA key for authentication
2) Changed the connect port in sshd_config

I suspect the problem here isn't your SSH connection, but rather your .bashrc file. When you connect remotely, what is in the .bash_aliases and .bashrc in the home directory? Does it look familiar?

---

### Post by iMisspell on 2009-10-18
> **falconindy said:**
> Wait, so you're using PuTTY even from Ubuntu? That seems like a mistake. PuTTY actually does a great job of mimicking the functionality provided by the included SSH client -- but why use a knockoff when you've got the real thing already?
Not knowing my way around any linux based system yet :) and consistency.
Figured i would run the same test on a ubuntu client as i was in windows.

With ubuntu client, just tried ('username' was changed for posting here):
$ ssh username@ip
$ username@192.168.0.80's password:
.....
username@promt_changed_ip_to_machine_name:~$

logged in fine, read both the '.bash_aliases' and '.bashrc' files off the remote computer and they are fine, same content as if i was sitting in front of the server itself.

The only change to the .bashrc which i did was un-comment (so it would work while sitting at the machine):
```

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

```



> **falconindy said:**
> The only "config" I've done with SSH is:
2) Changed the connect port in sshd_config
Security reasons ? - make it more of a guessing game for an out-sider to gain access ?

Thanks for helping me to trouble shoot this.
Its really not that big of a deal, but now i would like to find out why its not working correctly.


heres the .bashrc file, if there something else which needs to be tweaked ?
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

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

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

```

and .bash_aliases file (none of these commands work through SSH, but all work fine in front of server)
```

alias installapp='sudo apt-get install'
alias updateapp='sudo apt-get update'
alias upgradeapp='sudo apt-get -u upgrade'
alias reinstallapp='sudo apt-get --reinstall install'
alias removeapp='sudo apt-get remove'
alias searchapp='apt-cache search'
alias vercheckapp='apt-cache policy'

alias firewall='sudo ufw'

alias adduser='sudo adduser'
alias deleteuser='sudo userdel -r'

```
_

---

### Post by falconindy on 2009-10-18
> Security reasons ? - make it more of a guessing game for an out-sider to gain access ?
Pretty much. It's not really a valid security measure, but I've still made a habit of it.

So here's a question: Given that you had to uncomment the .bash_aliases check in .bashrc, what was the trigger that gave you access to the .bash_aliases file beforehand?

---

### Post by iMisspell on 2009-10-18
> **falconindy said:**
> So here's a question: Given that you had to uncomment the .bash_aliases check in .bashrc, what was the trigger that gave you access to the .bash_aliases file beforehand?
There wasn't.

Recently did a fresh ubuntu-server install (first time using/running a gui-less server), un-commented .bashrc, created .bash_aliases, installed acouple programs - everything whent fine.

When the server was installed, the [if statement] in the .bashrc file was commented-out by default and the .bash_aliases did not exists (im sure you know this, figured i would type it out in-case another reader does not).

Tried SSH to the server and discovered the problem posted here.

_

---

### Post by iMisspell on 2009-10-21
Just got done installing 8.04 LTS Server.
Logged into SSH from ubuntu-desktop 9.04 client, edited .bashrc added .bash_aliases, saved, logged out, relogged in and its working.

Only ran one test '$ vercheckapp ssh' which is hooked to:
*alias vercheckapp='aptitude-cache policy'*

When i first created the .bash_aliases file i goofed and missed a single closing quote and when i re-logged in i was greeted with a message letting me know :)

Re-edited the file, logged out and re-logged in and its working.

Thought i would just post this "up-date".
Pretty sure im gonna be using 8.04, but the 9.04 server is sitting as a virtual so if i ever get any free time maybe ill go back and try and re-edit with a bad command and see if 9.04 alerts.

Again, thanks for the time falconindy.


_

---

### Post by Skippy le Grand Gourou on 2010-01-08
It appears that SSH sources .bash_profile and NOT .bashrc (why*?). So the solution consists in modifying or creating a $HOME/.bash_profile file so that it contains*:
```
if [ -f ~/.bashrc ]; then
    . ~/.bashrc
fi
```
The .bashrc file will then be sourced at the SSH login, and so will be .bash_aliases if .bashrc asks for it.

Edit*: Now I know why, and my knowledge and comprehension of the Linux World is highly enhanced just from that*! The .bash_profile file is used for login shells (i.e. first connexion) and .bashrc for non-login shells (e.g. new terminal in an already opened session). See for instance [this explanation](http://hacktux.com/bash/bashrc/bash_profile).

---

### Post by vol7ron on 2010-04-28
> **Skippy le Grand Gourou said:**
> 
Edit*: Now I know why, and my knowledge and comprehension of the Linux World is highly enhanced just from that*! The .bash_profile file is used for login shells (i.e. first connexion) and .bashrc for non-login shells (e.g. new terminal in an already opened session). See for instance [this explanation]("http://hacktux.com/bash/bashrc/bash_profile").

That's good to know, for newcomers like me, thank you.

I was also curious why he had to login/logoff.  Couldn't he just do ```
$> source ~/.bashrc
```

---

