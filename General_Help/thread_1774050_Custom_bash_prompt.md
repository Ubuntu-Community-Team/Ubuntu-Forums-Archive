---
title: "Custom bash prompt"
date: 2011-06-02
forum: General Help
---

### Post by CVGH on 2011-06-02
I'm trying to get a custom bash prompt. I thought you would edit bash.bashrc, but nothing seems to happen..

Here is my bashrc:

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

# set a fancy prompt (non-color, overwrite the one in /etc/profile)
# PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
# PS1="\[\033[36m\][\t] \[\033[1;33m\]\u\[\033[0m\]@\h:\[\033[36m\][\w]:\[\033[0m\] "

# If id command returns zero, you’ve root access.

if [ $(id -u) -eq 0 ];
then 
  PS1="\\[$(tput setaf 1)\\]\\u@\\h:\\w #\\[$(tput sgr0)\\]"
else 
  PS1="[\\u@\\h:\\w] $"
fi

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
#if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
#    . /etc/bash_completion
#fi

# sudo hint
if [ ! -e "$HOME/.sudo_as_admin_successful" ]; then
    case " $(groups) " in *\ admin\ *)
    if [ -x /usr/bin/sudo ]; then
        cat <<-EOF
        To run a command as administrator (user "root"), use "sudo <command>".
        See "man sudo_root" for details.
        
        EOF
    fi
    esac
fi

# if the command-not-found package is installed, use it

```Am I supposed to do this in etc/profile?
I'm trying a if/then to change the look if I am root.
There is a PS1 line in there I've commented out as I couldn't get that
to work either.

```
# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ -d /etc/profile.d ]; then
  for i in /etc/profile.d/*.sh; do
    if [ -r $i ]; then
      . $i
    fi
  done
  unset i
fi

if [ "$PS1" ]; then
  if [ "$BASH" ]; then
    PS1='\u@\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
    . /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='\\[$(tput setaf 1)\\]\\u@\\h:\\w #\\[$(tput sgr0)\\]'
    else
      PS1='[\\u@\\h:\\w] $'
    fi
  fi
fi

umask 022

```

---

### Post by capscrew on 2011-06-03
See [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html").

---

### Post by andrew.46 on 2011-06-03
You would be safer to experiment with $HOME/.bashrc rather than alter the system configuration files. Even safer to make a backup first:

```
cp -av $HOME/.bashrc $HOME/.bashrc_bak
```

---

### Post by CVGH on 2011-06-03
> **capscrew said:**
> See [**_[COLOR=DarkSlateGray]here[/COLOR]_**]("http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html").
That is the site that gave me the idea and also the location of bashrc....

---

### Post by CVGH on 2011-06-03
> **andrew.46 said:**
> You would be safer to experiment with $HOME/.bashrc rather than alter the system configuration files. Even safer to make a backup first:

```
cp -av $HOME/.bashrc $HOME/.bashrc_bak
```
I did make a copy of bashrc in the etc directory before I started messing around.  Did not know that there was a copy of it there. I will try that one tonight...

---

### Post by andrew.46 on 2011-06-03
> **CVGH said:**
> I did make a copy of bashrc in the etc directory before I started messing around.  Did not know that there was a copy of it there. I will try that one tonight...

Usually it is the *local* copy (in $HOME) that people modify, leaving the system copies alone.

---

### Post by CVGH on 2011-06-03
Using the local file seems to be working fine.
I'm able to add the time and change the color.
I'd like to make it so when I do "sudo su", the prompt is red
after I authenticate.
I found this code, but not sure how to integrate it:
```
# If id command returns zero, you’ve root access.

if [ $(id -u) -eq 0 ];
then 
  PS1="\\[$(tput setaf 1)\\]\\u@\\h:\\w #\\[$(tput sgr0)\\]"
else 
  PS1="[\\u@\\h:\\w] $"
fi

```This is what the prompt part of bashrc is like right now:
```

force_color_prompt=yes

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
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;35m\]\t\[\033[00m\] \[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi

```

Thanks!!

---

