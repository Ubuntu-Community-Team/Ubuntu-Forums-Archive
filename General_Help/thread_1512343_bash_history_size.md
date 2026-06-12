---
title: "bash_history size"
date: 2010-06-18
forum: General Help
---

### Post by COKEDUDE on 2010-06-18
How do you set the bash_history size when using the .bashrc file and setting the "HISTSIZE=9000" doesn't work?

---

### Post by arrange on 2010-06-18
How doesn't it work? It cuts the history at the default 500 lines? Do you happen to have conflicting variables in *.bashrc*?

---

### Post by dino99 on 2010-06-18
By default, when a command is used in a console, that one is saved in bash history.
The problem is that each new command is saved again even if that command exist in history. bash history become fatty & it's a pain to recall a previous command using arrows.

The solution is to modify the .bashrc file by adding:
export HISTCONTROL=ignoredups:erasedups

to prevent duplicates

[https://bugs.launchpad.net/ubuntu/+source/bash/+bug/189881](https://bugs.launchpad.net/ubuntu/+source/bash/+bug/189881)

---

### Post by COKEDUDE on 2010-06-18
> **arrange said:**
> How doesn't it work? It cuts the history at the default 500 lines? Do you happen to have conflicting variables in *.bashrc*?

This is the only line I have in my *.bashrc*. I don't have any other lines. 
```
HISTSIZE=1000
```

---

### Post by COKEDUDE on 2010-06-18
> **dino99 said:**
> By default, when a command is used in a console, that one is saved in bash history.
The problem is that each new command is saved again even if that command exist in history. bash history become fatty & it's a pain to recall a previous command using arrows.

The solution is to modify the .bashrc file by adding:
export HISTCONTROL=ignoredups:erasedups

to prevent duplicates

[https://bugs.launchpad.net/ubuntu/+source/bash/+bug/189881](https://bugs.launchpad.net/ubuntu/+source/bash/+bug/189881)

I'm not worried about duplicates right now. I just wanna save more than 500 lines in my .bash_history file.

---

### Post by COKEDUDE on 2010-06-19
> **COKEDUDE said:**
> This is the only line I have in my *.bashrc*. I don't have any other lines. 
```
HISTSIZE=1000
```

Does anyone know if this is wrong?

---

### Post by arrange on 2010-06-19
[COLOR="DimGray"]This is the only line I have in my .bashrc. I don't have any other lines. [/COLOR]
Is it deliberate?

What is the contents of */etc/skel/.bashrc* and */etc/bash.bashrc*? (If they are long, use [Ubuntu pastebin]("http://paste.ubuntu.com/") or something like that.)

---

### Post by mc4man on 2010-06-19
This is what I'm using on lucid
> # don't put duplicate lines in the history. See bash(1) for more options
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoredups:ignorespace

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=2000
HISTFILESIZE=2000

You should also increase the scrollback in the profile preferences of the terminal

I also use this file in home - alllows starting a command and then page up, page down to retrieve like commands from the history

.inputrc

```
"\e[5~": history-search-backward
"\e[6~": history-search-forward

```

---

### Post by COKEDUDE on 2010-06-21
> **arrange said:**
> [COLOR="DimGray"]This is the only line I have in my .bashrc. I don't have any other lines. [/COLOR]
Is it deliberate?

What is the contents of */etc/skel/.bashrc* and */etc/bash.bashrc*? (If they are long, use [Ubuntu pastebin]("http://paste.ubuntu.com/") or something like that.)

I had no .bashrc file to start off with so I created one in my home directory added the line I wanted. 

I do not have this file /etc/skel/.bashrc. 

Here is my /etc/bash.bashrc. 
```
# System-wide .bashrc file for interactive bash(1) shells.

# To enable the settings / commands in this file for login shells as well,
# this file has to be sourced in /etc/profile.

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

use_color=false

# Set colorful PS1 only on colorful terminals.
# dircolors --print-database uses its own built-in database
# instead of using /etc/DIR_COLORS.  Try to use the external file
# first to take advantage of user additions.  Use internal bash
# globbing instead of external grep binary.
safe_term=${TERM//[^[:alnum:]]/?}   # sanitize TERM
match_lhs=""
[[ -f ~/.dir_colors   ]] && match_lhs="${match_lhs}$(<~/.dir_colors)"
[[ -f /etc/DIR_COLORS ]] && match_lhs="${match_lhs}$(</etc/DIR_COLORS)"
[[ -z ${match_lhs}    ]] \
        && type -P dircolors >/dev/null \
        && match_lhs=$(dircolors --print-database)
[[ $'\n'${match_lhs} == *$'\n'"TERM "${safe_term}* ]] && use_color=true

if ${use_color} ; then
        # Enable colors for ls, etc.  Prefer ~/.dir_colors #64489
        if type -P dircolors >/dev/null ; then
                if [[ -f ~/.dir_colors ]] ; then
                        eval $(dircolors -b ~/.dir_colors)
                elif [[ -f /etc/DIR_COLORS ]] ; then
                        eval $(dircolors -b /etc/DIR_COLORS)
                fi
        fi

        if [[ ${EUID} == 0 ]] ; then
                PS1='${debian_chroot:+($debian_chroot)}\[\033[01;31m\]\h\[\033[01;34m\] \W \$\[\033[00m\] '
        else
                PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[01;34m\] \w \$\[\033[00m\] '
        fi

        alias ls='ls --color=auto'
        alias grep='grep --colour=auto'
else
        if [[ ${EUID} == 0 ]] ; then
                # show root@ when we don't have colors
                PS1='\u@\h \W \$ '
        else
                PS1='\u@\h \w \$ '
        fi
fi

# Try to keep environment pollution down, EPA loves us.
unset use_color safe_term match_lhs

# Commented out, don't overwrite xterm -T "title" -n "icontitle" by default.
# If this is an xterm set the title to user@host:dir
#case "$TERM" in
#xterm*|rxvt*)
#    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD}\007"'
#    ;;
#*)
#    ;;
#esac

# enable bash completion in interactive shells
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

# if the command-not-found package is installed, use it
if [ -x /usr/lib/command-not-found ]; then
	function command_not_found_handle {
	        # check because c-n-f could've been removed in the meantime
                if [ -x /usr/lib/command-not-found ]; then
		   /usr/bin/python /usr/lib/command-not-found -- $1
                   return $?
		else
		   return 127
		fi
	}
fi

/usr/bin/mint-fortune
```

> **mc4man said:**
> This is what I'm using on lucid


You should also increase the scrollback in the profile preferences of the terminal

I also use this file in home - alllows starting a command and then page up, page down to retrieve like commands from the history

.inputrc

```
"\e[5~": history-search-backward
"\e[6~": history-search-forward

```

Which line increases the scrollback?

---

### Post by mc4man on 2010-06-21
> Which line increases the scrollback?
Easiest is just to open a terminal -> edit -> Profile Preferences -> scrolling.
You can set a number or choose unlimited (though I think there still may be a limit

> doug@doug-laptop:~$ history
    1  svn checkout [http://abcde.googlecode.com/svn/trunk/](http://abcde.googlecode.com/svn/trunk/) abcde-read-only
.............clipped
1990 gksudo gedit /etc/initramfs-tools/modules 
1991  history


Edit:
> though I think there still may be a limit
the unlimited actually works as it says - just did a quick mplayer build and could scroll back thru the whole build - 3208 lines

The .inputrc thing I mentioned isn't affected by your scrollback setting - it reads from your .bash_history file
scrollback is only for viewing in the terminal itself.

---

### Post by yetiman64 on 2010-06-22
> I do not have this file /etc/skel/.bashrc.  The file .bashrc is a hidden file and you will have to use CTRL + H from the keyboard or tick View > Show Hidden Files in the nautilus menus to see it.

Is it still not there ?

> Easiest is just to open a terminal -> edit -> Profile Preferences  -> scrolling.
You can set a number or choose unlimited (though I think there still may  be a limit+1 here, I think the actual limit is 100 000 lines or ~64 MB (or at least it was on older Ubuntus)

---

### Post by COKEDUDE on 2010-06-24
> **yetiman64 said:**
> **The file .bashrc is a hidden file** and you will have to use CTRL + H from the keyboard or tick View > Show Hidden Files in the nautilus menus to see it.

Is it still not there ?

+1 here, I think the actual limit is 100 000 lines or ~64 MB (or at least it was on older Ubuntus)

Thats the reason I use a terminal whenever possible. I did this in the terminal and it created a new file. 
```
sudo vi /etc/skel/.bashrc
```

I also did this to double check. 
```
ls -l  /etc/skel/.bashrc
ls: cannot access /etc/skel/.bashrc: No such file or directory
```

I just want 1000 lines. I would hope 1000 would be easy.

---

### Post by arrange on 2010-06-24
This is strange, because in Ubuntu */etc/skel/.bashrc* is included in the *bash* package```
arrange@lucid-lean:~$ dpkg -S /etc/skel/.bashrc
bash: /etc/skel/.bashrc
arrange@lucid-lean:~$ dpkg -l | grep bash
ii  bash   4.1-2ubuntu3        The GNU Bourne Again SHell

```

---

### Post by COKEDUDE on 2010-06-24
> **arrange said:**
> This is strange, because in Ubuntu */etc/skel/.bashrc* is included in the *bash* package```
arrange@lucid-lean:~$ dpkg -S /etc/skel/.bashrc
bash: /etc/skel/.bashrc
arrange@lucid-lean:~$ dpkg -l | grep bash
ii  bash   4.1-2ubuntu3        The GNU Bourne Again SHell

```

I'm using Mint :). The forums here are way more helpful than Mint's forums. I know that Mint is derived from ubuntu so they are really similar.

---

