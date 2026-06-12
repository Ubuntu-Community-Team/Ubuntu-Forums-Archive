---
title: "What have I done to my path?"
date: 2009-06-30
forum: General Help
---

### Post by aaron424 on 2009-06-30
I was working with my path to compile rockbox, and I made a mistake. Now when I open the terminal it says:

bash: /home/aaron/.bashrc: line 98: syntax error near unexpected token `then'
bash: /home/aaron/.bashrc: line 98: `export PATH=$PATH:/usr/local/arm-elf/bin:/usr/local/m68k-elf/bin:/usr/local/sh-elf/binif [ -f /etc/bash_completion ]; then'

What does this mean and how can I fix it?

Thanks

---

### Post by t0p on 2009-06-30
Show us your .bashrc file

---

### Post by aaron424 on 2009-06-30
I would assume from the terminal message that the file would be in /home/aaron/.bashrc but its not there. and I do have view hidden files enabled

---

### Post by frenkel on 2009-06-30
What's the output of```
ls -al ~
```?

---

### Post by aaron424 on 2009-06-30
```
aaron@aaron-desktop:~$ ls -al ~
total 632
drwxr-xr-x 58 aaron aaron   4096 2009-06-30 16:04 .
drwxr-xr-x  3 root  root    4096 2009-06-07 04:51 ..
drwx------  3 aaron aaron   4096 2009-06-08 11:33 .adobe
drwxr-xr-x  4 aaron aaron   4096 2009-06-08 12:24 .alien-arena
drwxr-xr-x 11 aaron aaron   4096 2009-06-26 23:08 .azureus
-rw-------  1 aaron aaron   3790 2009-06-30 14:44 .bash_history
-rw-r--r--  1 aaron aaron    220 2009-06-07 04:51 .bash_logout
-rw-r--r--  1 aaron aaron   3465 2009-06-12 11:58 .bashrc
drwxr-xr-x  6 aaron aaron   4096 2009-06-30 15:33 .cache
-rw-r--r--  1 aaron aaron     47 2009-06-08 14:04 .cdcdrc
-rw-r--r--  1 aaron aaron    115 2009-06-08 14:04 .cdserverrc
drwxr-xr-x  2 aaron aaron   4096 2009-06-30 13:46 .checkbox
drwx------  3 aaron aaron   4096 2009-06-08 14:52 .compiz
drwxr-xr-x 11 aaron aaron   4096 2009-06-30 11:56 .config
drwx------  3 aaron aaron   4096 2009-06-07 00:55 .dbus
drwxr-xr-x  3 aaron aaron  12288 2009-06-30 15:51 Desktop
-rw-------  1 aaron aaron     28 2009-06-30 08:29 .dmrc
drwxr-xr-x  4 aaron aaron   4096 2009-06-30 14:53 Documents
-rw-------  1 aaron aaron     16 2009-06-07 00:55 .esd_auth
drwxr-xr-x  7 aaron aaron   4096 2009-06-11 09:03 .evolution
drwxr-xr-x  2 aaron aaron   4096 2009-06-17 17:49 .fontconfig
drwx------  5 aaron aaron   4096 2009-06-30 08:46 .gconf
drwx------  2 aaron aaron   4096 2009-06-30 16:40 .gconfd
drwx------  4 aaron aaron   4096 2009-06-13 14:53 .gegl-0.0
drwxr-xr-x 22 aaron aaron   4096 2009-06-26 11:16 .gimp-2.6
-rw-r-----  1 aaron aaron      0 2009-06-30 15:58 .gksu.lock
drwxr-xr-x  4 aaron aaron   4096 2009-06-09 17:03 .gnome
drwx------ 12 aaron aaron   4096 2009-06-30 14:58 .gnome2
drwx------  2 aaron aaron   4096 2009-06-07 00:55 .gnome2_private
drwx------  2 aaron aaron   4096 2009-06-07 00:55 .gnupg
drwxr-xr-x  3 aaron aaron   4096 2009-06-08 11:33 .google
drwxr-xr-x 11 aaron aaron   4096 2009-06-30 16:20 gpodder-downloads
drwxr-xr-x  2 aaron aaron   4096 2009-06-22 16:20 .gstreamer-0.10
-rw-r--r--  1 aaron aaron    108 2009-06-30 08:37 .gtk-bookmarks
dr-x------  3 aaron aaron      0 2009-06-30 08:29 .gvfs
-rw-------  1 aaron aaron   7797 2009-06-30 08:29 .ICEauthority
drwxr-xr-x  2 aaron aaron   4096 2009-06-30 11:55 .icepodder
drwxr-xr-x  2 aaron aaron   4096 2009-06-08 11:14 .icons
drwxr-xr-x  4 aaron aaron   4096 2009-06-09 20:00 .java
drwx------  3 aaron aaron   4096 2009-06-09 09:09 .kde
-rw-r--r--  1 aaron aaron    150 2009-06-27 21:23 .lightyears.cfg
-rw-r--r--  1 aaron aaron 107198 2009-06-15 18:44 .lightyears.save0.dat
drwxr-xr-x  7 aaron aaron   4096 2009-06-30 13:35 .limewire
drwxr-xr-x  4 aaron aaron   4096 2009-06-30 13:34 LimeWire
drwx------  3 aaron aaron   4096 2009-06-08 11:52 .local
drwx------  3 aaron aaron   4096 2009-06-08 11:33 .macromedia
drwx------  5 aaron aaron   4096 2009-06-25 15:52 .mozilla
drwxr-xr-x  3 aaron aaron   4096 2009-06-27 21:19 Music
drwxr-xr-x  3 aaron aaron   4096 2009-06-09 10:11 My Games
drwxr-xr-x  4 aaron aaron   4096 2009-06-13 15:43 .nautilus
drwx------  3 aaron aaron   4096 2009-06-09 09:59 .netx
-rw-r--r--  1 aaron aaron   1144 2009-06-30 15:02 .nvidia-settings-rc
drwxr-xr-x  3 aaron aaron   4096 2009-06-13 14:45 .openoffice.org
drwxr-xr-x  2 aaron aaron   4096 2009-06-30 13:52 Pictures
drwxr-xr-x  2 aaron aaron   4096 2009-06-30 11:55 podcasts
drwxr-xr-x  2 aaron aaron   4096 2009-06-09 20:02 .PowerFolder
-rw-r--r--  1 aaron aaron    675 2009-06-07 04:51 .profile
drwx------  2 aaron aaron   4096 2009-06-30 08:29 .pulse
-rw-------  1 aaron aaron    256 2009-06-07 00:55 .pulse-cookie
drwxr-xr-x  2 aaron aaron   4096 2009-06-16 16:30 .pychess
-rw-------  1 aaron aaron   2990 2009-06-17 17:21 .recently-used
-rw-------  1 aaron aaron  91686 2009-06-30 16:04 .recently-used.xbel
drwxr-xr-x 19 aaron aaron   4096 2009-06-27 11:56 rockbox
drwx------  4 aaron aaron   4096 2009-06-12 13:12 .songbird2
drwxr-xr-x  3 aaron aaron   4096 2009-06-09 15:47 .subversion
-rw-r--r--  1 aaron aaron      0 2009-06-08 08:58 .sudo_as_admin_successful
-rw-r--r--  1 aaron aaron  11264 2009-06-16 14:06 .synchrorep.db
-rw-r--r--  1 aaron aaron      5 2009-06-30 08:29 .synchrorep.display
drwxr-xr-x  2 aaron aaron   4096 2009-06-16 14:06 .synchrorep_work
drwxr-xr-x  2 aaron aaron   4096 2009-06-08 11:14 .themes
drwx------  4 aaron aaron   4096 2009-06-09 09:07 .thumbnails
drwx------  2 aaron aaron   4096 2009-06-09 19:40 .unison
drwxr-xr-x  2 aaron aaron   4096 2009-06-08 09:00 .update-manager-core
drwx------  2 aaron aaron   4096 2009-06-08 11:47 .update-notifier
drwxr-xr-x  4 aaron aaron   4096 2009-06-30 14:53 Videos
-rw-r--r--  1 aaron aaron      4 2009-06-09 16:48 .windows-label
drwxr-xr-x  4 aaron aaron   4096 2009-06-30 15:33 .wine
drwxr-xr-x  2 aaron aaron   4096 2009-06-30 16:30 .winff
-rw-------  1 aaron aaron    124 2009-06-30 08:29 .Xauthority
drwxr-xr-x  2 aaron aaron   4096 2009-06-09 09:09 .xine
-rw-r--r--  1 aaron aaron    129 2009-06-08 09:06 .xscreensaver-getimage.cache
-rw-r--r--  1 aaron aaron  96598 2009-06-30 16:41 .xsession-errors

```

Never mind, I see .bashrc. now I need to get to it.

---

### Post by renkinjutsu on 2009-06-30
according to you ls entry, .bashrc is indeed present in your home directory, it's hard looking for files in nautilus, so just```
gedit .bashrc
``` so we can have a look at it

---

### Post by aaron424 on 2009-06-30
Okay I found the .bashrc file. Here it is:

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
export PATH=$PATH:/usr/local/arm-elf/bin:/usr/local/m68k-elf/bin:/usr/local/sh-elf/bin

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
export PATH=$PATH:/usr/local/arm-elf/bin:/usr/local/m68k-elf/bin:/usr/local/sh-elf/binif [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi
export PATH=$PATH:/usr/local/arm-elf/bin:/usr/local/m68k-elf/bin:/usr/local/sh-elf/bin


export PATH=$PATH:/usr/local/arm-elf/bin:/usr/local/m68k-elf/bin:/usr/local/sh-elf/bin

```

---

### Post by renkinjutsu on 2009-06-30
ahh i see.. 
open up your .bashrc in gedit, scroll down to line 98
(gedit can display line numbers, go to preferences and check "Display line numbers")

once there, move your cursor left until you see 
```
:/usr/local/sh-elf/binif
```
change it to ```
:/usr/local/sh-elf/bin ; if
```

---

### Post by aaron424 on 2009-06-30
Worked perfectly! Thanks.

---

