---
title: "How to remove the shift+backspace &quot;feature&quot; of xgl"
date: 2006-06-02
forum: General Help
---

### Post by PriceChild on 2006-06-02
((only for those using xgl))

Don't know about any of you lot, but i've been constantly annoyed by my lazy little finger on the shift button causing x to reset when i press shift+backspace.

Thanks to sudomania4 on the IRC channel, he's informed me that adding

```
xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"
``` to some sort of script at each startup e.g. "thefuture" will stop the key combo from working!

Works fine for me :) thought you all may want to now.

Pricey

---

### Post by nixt on 2006-06-02
Thanks! Always wondered why my X kept restarting while typing posts...

---

### Post by PriceChild on 2006-06-02
No probs :)

Yeah i was on the irc channel last night and did it about 20 times within an hour so decided had to sort it out!

---

### Post by Xilon on 2006-06-02
I think this has been removed in the newer versions... got a clean install of Ubuntu Dapper with XGL and Compiz and the shift+backspace combination doesn't work anymore... which I don't mind a bit :)

---

### Post by nixt on 2006-06-02
Weird, my dapper was installed clean too.. and shift+bksp still restarted X..

---

### Post by leohart on 2006-06-21
[QUOTE=Xilon]I think this has been removed in the newer versions... got a clean install of Ubuntu Dapper with XGL and Compiz and the shift+backspace combination doesn't work anymore... which I don't mind a bit :)[/QUOTE]

If you are running Aiglx or something else different from Xgl, there should not be a problem with Shift+backspace. My laptop runs Aiglx and compiz-aiglx and there is no such problem. On my desktop, I have cursed and slammed the mouse like 5  times tonight already. Trying to get my essay done.

---

### Post by jeff419 on 2007-01-01
Thanks so much for this, I was ready to kill someone til I found this!!  :evil:

---

### Post by ~LoKe on 2007-01-01
That's quite the bump.  As far as I know, this no longer matters?

---

### Post by thayerw on 2007-01-03
Unfortunately, it is still valid... I'm running a fresh install of Edgy with XGL and Beryl on an ATI X1400 and after losing the same email message 5 times in a row because of this stubborn shortcut, I finally found this thread.

FYI:  You can add the command to your ~/.bashrc file if you don't want to have to run it at each start up.

This really needs a fix... or at least a well-published workaround.

~thayer

---

### Post by Cryptic1911 on 2007-01-03
I found that none of the shortcuts were working for me.. I ended up having to change my keyboard mapping. It was set to 104? key US, and I believe I changed it to 101 Key US and it fixed it.. might be worth a shot for you guys

---

### Post by sdelano on 2007-01-04
When adding this to scripts it is not working for me, but if I run this command from a console then it does work...whats the deal?

Here is my startxgl.sh:
```
#!/bin/sh
Xgl :1 -fullscreen -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4 
[COLOR="Red"]xmodmap -e "keycode 22 = BackSpace"[/COLOR]
export DISPLAY=:1 
exec gnome-session
```

Here is my ~/.bashrc
```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups

# remove Shift+BackSpace from XGL
[COLOR="Red"]xmodmap -e "keycode 22 = BackSpace"[/COLOR]

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
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
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi 
```

[COLOR="Red"]xmodmap -e "keycode 22 = BackSpace"[/COLOR] is what works when I run it from a command prompt.

Any ideas?

Am I missing something?

Thanks,
sdelano

---

### Post by bro on 2007-01-11
ah.. sorry it didn't work for you Sdelano, I only see your post now...

This is so what I needed! So to sum it up:

```

~$ gedit .bashrc

```

add the following lines at the bottom of the document:
```

# make shift+backspace NOT restart X
xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"

```

Safe the file and log out and in again.

---

### Post by Robor on 2007-01-15
I'm running Beryl + AiXGL and Shift-BackSpace kills my XServer.  I tried this fix (adding to ~/.bashrc) and it did work but I had to restart (not log off/on).  Thanks!

---

### Post by w116tjb on 2007-01-21
Yeah, I keep getting an error message when trying that command.

xmodmap:  unknown command on line commandline:1
xmodmap:  unable to open file '22' for reading
xmodmap:  unable to open file '=' for reading
xmodmap:  unable to open file 'BackSpace' for reading
xmodmap:  unable to open file 'BackSpace' for reading
xmodmap:  unable to open file 'Terminate_Server&#8221;' for reading
xmodmap:  6 errors encountered, aborting.

I'm going to try that keyboard switch now.

EDIT: I went to Menu > System > Preferences > Keyboard and selected the Layout tab. I then switched the Keyboard Model from Generic 101-key PC to Generic 105-key (Intl) PC. I no longer have the Shift + Backspace issue.

---

### Post by FuturePilot on 2007-01-21
Hey, thanks for this. I was wondering how to do that as there have been numerous times where I've accidentally hit that key combo while typing and restarted X.](*,)

---

### Post by jlc on 2007-01-31
> **PriceChild said:**
> ((only for those using xgl))

Don't know about any of you lot, but i've been constantly annoyed by my lazy little finger on the shift button causing x to reset when i press shift+backspace.

Thanks to sudomania4 on the IRC channel, he's informed me that adding

```
xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"
``` to some sort of script at each startup e.g. "thefuture" will stop the key combo from working!

Works fine for me :) thought you all may want to now.

Pricey

Thank you, this was driving me nuts as I kept writing a java program and then ZAP, back to my screen.

---

### Post by Metallinut on 2007-02-26
> **bro said:**
> ah.. sorry it didn't work for you Sdelano, I only see your post now...

This is so what I needed! So to sum it up:

```

~$ gedit .bashrc

```

add the following lines at the bottom of the document:
```

# make shift+backspace NOT restart X
xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"

```

Safe the file and log out and in again.

My keycode 22 is the '5' key.  When you reference keycode 22 do mean the shift key or the backspace key?

---

### Post by billygates on 2007-03-29
Consider me a n00b.  Can you guys please provide more detailed instruction on how to disable this "feature".  It makes me CRAZY.

I have tried the following, but it hasnt worked.  I must be missing something.

> open a terminal and type:

    $ gedit /home/username/annoymenot.sh 

Remember to replace 'username' with your username. Now, in this file type:

    $ xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server" 

Save and close the file, and make it executable:

    $ chmod 755 /home/username/annoymenot.sh 

Now go to System - Preferences - Session, Startup Programs. Click add, and type

    $ /home/username/annoymenot.sh 

Logout and back in, problem solved! 

---

### Post by jackphil on 2007-05-08
> **sdelano said:**
> When adding this to scripts it is not working for me, but if I run this command from a console then it does work...whats the deal?
...


only need this:
```
echo "keycode 22 = BackSpace BackSpace Terminate_Server" >>~/ .Xmodmap
```

---

