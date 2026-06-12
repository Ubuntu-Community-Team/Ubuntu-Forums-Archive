---
title: "console colors-&gt; blink login screen"
date: 2009-09-10
forum: General Help
---

### Post by mefiiik on 2009-09-10
Hello i tryed to color my console with this guide [http://ubuntuforums.org/showthread.php?t=192675](http://ubuntuforums.org/showthread.php?t=192675) i did everything, but when i restart my pc i saw login screen for a second and it startedt blink black and again login screen... so i cant login... i tryed ti revert it to original settings but it didnt work:(... i tryed 
```
sudo dpkg-reconfigure -phigh xserver-xorg

```
but it didn't work:(... somebody know how to repair it?:((

i have Ubuntu 9.04 and graphic card NVIDIA GeForce 8200 M

PS: sorry for my english

---

### Post by PriceChild on 2009-09-10
> **mefiiik said:**
>  i have Ubuntu 9.04 and graphic card NVIDIA GeForce 8200 MThat guide is meant for The Dapper Drake, Ubuntu 6.06. It is **severely** out of date.

Despite that... throughout that guide you made lots of backups of your critical configuration files.

Things like ```
sudo cp /etc/lsb-base-logging.sh /etc/lsb-base-logging.sh_bak
```

You should boot in single user mode, or onto a live cd and mount the hard drive, then reverse all of these changes.

---

### Post by mefiiik on 2009-09-10
> **PriceChild said:**
> That guide is meant for The Dapper Drake, Ubuntu 6.06. It is **severely** out of date.

Despite that... throughout that guide you made lots of backups of your critical configuration files.

Things like ```
sudo cp /etc/lsb-base-logging.sh /etc/lsb-base-logging.sh_bak
```You should boot in single user mode, or onto a live cd and mount the hard drive, then reverse all of these changes.

Ok thanks, but i am begginer with ubuntu, can you please write some simple guide how to do it please:(

---

### Post by nothingspecial on 2009-09-10
Boot into recovery mode and
```

sudo cp /boot/grub/menu.lst_bak /boot/grub/menu.lst
```
```
sudo cp /etc/lsb-base-logging.sh_bak /etc/lsb-base-logging.sh
```
```
cp ~/.bashrc_bak ~/.bashrc 
```

---

### Post by mefiiik on 2009-09-10
when i am trying to do ```
cp ~/.bashrc_bak ~/.bashrc
```
it write me ```
cp: cannot stat '/root/.bashrc_bak': No such file or directory
```

but when i wrote it in console when i boot normaly it didn't write this...

---

### Post by nothingspecial on 2009-09-10
Sorry, you need to ```
cd /home/*[COLOR="Red"]username[/COLOR]*
``` first.

Type your username instead of *[COLOR="Red"]username[/COLOR]*

---

### Post by mefiiik on 2009-09-10
> **nothingspecial said:**
> Sorry, you need to ```
cd /home/*[COLOR=Red]username[/COLOR]*
``` first.

Type your username instead of *[COLOR=Red]username[/COLOR]* still write the same error

---

### Post by nothingspecial on 2009-09-10
Post the output of ```
ls -a
```

after ```
cd /home/username
```

---

### Post by mefiiik on 2009-09-10
> **nothingspecial said:**
> Post the output of ```
ls -a
```after ```
cd /home/username
``` how i can copy it all and put it to txt or something like thath.. or i have to rewrite all the folders?

---

### Post by nothingspecial on 2009-09-10
Do you see anything that looks like .bashrc_bak

---

### Post by mefiiik on 2009-09-10
> **nothingspecial said:**
> Do you see anything that looks like .bashrc_bak no i even cant see .bashrc

---

### Post by nothingspecial on 2009-09-10
Actually, as long as you did the first 2 commands, you may already be fixed.

---

### Post by mefiiik on 2009-09-10
> **nothingspecial said:**
> Actually, as long as you did the first 2 commands, you may already be fixed.
maybe if i can move somehow up.. because i cant see everything what it show me... just some of folders... i see folder from .bitrock.. what is up it i cant see.. i wil try reboot it and i will tell you

---

### Post by mefiiik on 2009-09-10
so it's still same.. it's still blink

---

### Post by nothingspecial on 2009-09-10
I`m out of ideas and I have to go.

Will post back if I think of something.

---

### Post by mefiiik on 2009-09-10
> **nothingspecial said:**
> I`m out of ideas and I have to go.

Will post back if I think of something.
ok even so thank you:)

---

### Post by mefiiik on 2009-09-10
maybe i found where is problem vut i still dont know how to resolve it... in home is no .bashrc.. but i found on pc bash.bashrc which look exactly the same like the fille which i changed.. so maybe 9.04 dont have .bashrc but have bash.bashrc... I didn't made backup of bash.bashrc... here is how that file look

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
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '

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
#if [ -f /etc/bash_completion ]; then
#    . /etc/bash_completion
#fi

# sudo hint
if [ ! -e $HOME/.sudo_as_admin_successful ]; then
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

```

---

### Post by mefiiik on 2009-09-10
or it can be dot.bashrc in this file i found the things which i copy from guide here is how it look```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
#export HISTCONTROL=ignoredups

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" -a -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
xterm-color)
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;
*)
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    ;;
esac

# Comment in the above and uncomment this below for a color prompt
#PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
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
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
#if [ -f /etc/bash_completion ]; then
#    . /etc/bash_completion
#fi

```

---

### Post by nothingspecial on 2009-09-10
Hello again. Can`t stop, kids, tea, bath, story, bed etc.

Try renaming that file .bashrc

In home/username

```
mv bash.bashrc .bashrc
```

The mv command actually renames a file, which in linux is the same as moving it.

---

### Post by mefiiik on 2009-09-10
> **nothingspecial said:**
> Hello again. Can`t stop, kids, tea, bath, story, bed etc.

Try renaming that file .bashrc

In home/username

```
mv bash.bashrc .bashrc
```The mv command actually renames a file, which in linux is the same as moving it.
i dont know if it will work, because bash.bashrc is in /etc/ and .bashrc is in /home/mefistos

---

### Post by mefiiik on 2009-09-10
i tryed
```
cd /etc/
mv bash.bashrc /home/mefistos/.bashrc
``` and it made me .bashrc .. so i tryed
```
cp ~/.bashrc_bak ~/.bashrc
``` and it wrote me that there is no .bashrc_bak... maybe when i did the changes i changed dot.bashrc or bash.bashrc and i don't have any backup...

---

### Post by nothingspecial on 2009-09-10
Crikey. I thought you were talking about your home.

You need to copy bash.bashrc back to /etc

```
cp /home/mefistos/.bashrc /etc/bash.bashrc
```

---

### Post by nothingspecial on 2009-09-10
Not having a .bashrc should not stop you from logging in.

It will cause problems but you should still be able to log in.

---

### Post by mefiiik on 2009-09-10
done... one guy told me to do this

check rights and owner

```
ls -l /etc/lsb-base-logging.sh
-rw-r--r-- 1 root root 3820 2009-02-08 00:33 /etc/lsb-base-logging.sh
```

next copy */etc/skel/.bashrc* to your home folder


```
cp /media/ubuntu/etc/skel/.bashrc /media/ubuntu/home/user/.bashrc
```

and change owner to tou


```
sudo chown user:user /media/ubuntu/home/user/.bashrc
```

---

### Post by nothingspecial on 2009-09-10
Good stuff.

Did it work?

---

### Post by mefiiik on 2009-09-10
no because i don't have permission .. i do it from LiveCD and i cant change what is in /media/disk/...

---

### Post by mefiiik on 2009-09-10
so still don't work.. still blink login screen:(

---

### Post by nothingspecial on 2009-09-10
> **mefiiik said:**
> no because i don't have permission .. i do it from LiveCD and i cant change what is in /media/disk/...

sudo will give you permission

---

### Post by mefiiik on 2009-09-10
yes i know.. i did everything but still don't work:(:(

---

