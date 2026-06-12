---
title: "autorun a shell at/before startup?"
date: 2010-11-20
forum: General Help
---

### Post by WilsonMESS on 2010-11-20
I need to run a shell to enable pseudo-multitouch on my touchpad using a shell which automatically configs synclient.
```
#!/bin/bash
export DISPLAY=:0.0

synclient \
EmulateTwoFingerMinZ=50 \
EmulateTwoFingerMinW=6 \
VertTwoFingerScroll=1 \
HorizTwoFingerScroll=1 \
VertScrollDelta=75 \
HorizScrollDelta=100 \
RTCornerButton=2 \
RBCornerButton=0 \
LTCornerButton=0 \
LBCornerButton=0 \
TapButton1=1 \
TapButton2=3 \
TapButton3=0 \
;
```
I put this file under /home/<username>/, and also put this to the Session manager under system menu. But it doesn't work. I've already used chmod command to make sure that the file is executable, and, I also put this: ```
PATH="/bin:/usr/bin:/sbin:/usr/sbin:/usr/include:/usr/local/bin:$HOME/bin"
```
in $HOME/.bashrc. Now this file looks like this:
```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

PATH="/bin:/usr/bin:/sbin:/usr/sbin:/usr/include:/usr/local/bin:$HOME/bin"

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
if [ -f /etc/bash_copletion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi
```
But still no works. I'm using ASUS Eee PC 1005PE, ubuntu 10.10 Desktop version(32-bit), what shall I do?

---

### Post by CharlesA on 2010-11-20
Did you add it to start up applications?

---

### Post by James78 on 2010-11-20
Gnome and KDE have some startup folders you could try. Just drop whatever scripts into them.

Gnome: ~/.config/autostart
KDE: Only for .desktop files I think: ~/.kde/Autostart
       And for other scripts, like .sh: ~/.kde/env

Note: The Gnome startup folder might require .desktop files instead of scripts. So you should try both ways. Also, I think the ~/.config/autostart folder works for both Gnome and KDE at the same time, but I'm not 100% sure.

If you don't want to do all this manually, you can just go to the respective application/system area in both desktop environments.
Gnome: Desktop Preferences -> Sessions
KDE: System Settings -> Startup and Shutdown

---

### Post by WilsonMESS on 2010-11-20
> **CharlesA said:**
> Did you add it to start up applications?

Yes I did, isn't that located in System-Preferences-Session(or autorun application, whatever) Manager? (Well I don't know the exact name since I'm using the Chinese version, sorry)

---

### Post by WilsonMESS on 2010-11-20
> **James78 said:**
> Gnome and KDE have some startup folders you could try. Just drop whatever scripts into them.

Gnome: ~/.config/autostart
KDE: Only for .desktop files I think: ~/.kde/Autostart
       And for other scripts, like .sh: ~/.kde/env

Note: The Gnome startup folder might require .desktop files instead of scripts. So you should try both ways. Also, I think the ~/.config/autostart folder works for both Gnome and KDE at the same time, but I'm not 100% sure.

If you don't want to do all this manually, you can just go to the respective application/system area in both desktop environments.
Gnome: Desktop Preferences -> Sessions
KDE: System Settings -> Startup and Shutdown

Yeah, it seems that I already have a file named "touchpad.sh.desktop" in this directory, and it goes like this:
```

[Desktop Entry]
Type=Application
Exec=/home/wilsonmess/touchpad.sh
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[zh_CN]=&#35302;&#25511;&#26495;&#35774;&#32622;
Name=&#35302;&#25511;&#26495;&#35774;&#32622; ##touchpad configurations
Comment[zh_CN]=&#20351;&#35302;&#25511;&#26495;&#25903;&#25345;&#22810;&#28857;&#35302;&#25511;
Comment=&#20351;&#35302;&#25511;&#26495;&#25903;&#25345;&#22810;&#28857;&#35302;&#25511; ##enable pseudo-multitouch on the touchpad
```
So... Is there anything wrong in this file? Thanks!

---

### Post by CharlesA on 2010-11-20
Does the script work if you run it manually?

I'm curious as to what the "\" characters are used for.

---

### Post by efflandt on 2010-11-20
Note that if you add a **bin** directory to your home directory, that should "automatically" be included in your path the next time you login into X.

**echo $PATH**
/home/efflandt/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

But the question is whether you put that script in your /home/<username>/bin/, because you said "I put this file under /home/<username>/", which is NOT in your PATH (and probably should not be).

---

### Post by WilsonMESS on 2010-11-20
> **CharlesA said:**
> Does the script work if you run it manually?

I'm curious as to what the "\" characters are used for.

Yes it prompts me to choose whether to open the file or to execute it.
Actually I didn't write the shell, I found this when I was troubleshooting the touchpad (which can be found here: [http://apt-blog.net/configuring_laptop_synaptics_touchpad_in_linux](http://apt-blog.net/configuring_laptop_synaptics_touchpad_in_linux) , in Chinese). The stuff actually worked automatically for a while, so I don't think it's about the slash. But yesterday, I didn't know how, it just can't work properly, and when I open the file, it didn't prompt me what to do. The gedit simply pop out and I thought it might be solved by using the chmod +x command. Though now it can work manually, I'm still trying to figure out how to make it automatially...

---

### Post by WilsonMESS on 2010-11-20
> **efflandt said:**
> Note that if you add a **bin** directory to your home directory, that should "automatically" be included in your path the next time you login into X.

**echo $PATH**
/home/efflandt/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

But the question is whether you put that script in your /home/<username>/bin/, because you said "I put this file under /home/<username>/", which is NOT in your PATH (and probably should not be).

Well, I can't find directory "bin" under my home directory (and yes, I did press CTRL+H), but I found one under /usr/ , so I put it there, with no effect after reboot...

---

### Post by WilsonMESS on 2010-11-20
> **efflandt said:**
> Note that if you add a **bin** directory to your home directory, that should "automatically" be included in your path the next time you login into X.

**echo $PATH**
/home/efflandt/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

But the question is whether you put that script in your /home/<username>/bin/, because you said "I put this file under /home/<username>/", which is NOT in your PATH (and probably should not be).

Well, I can't find directory "bin" under my home directory (and yes, I did press CTRL+H), but I found one under /usr/ , so I put it there, with no effect after reboot...

---

### Post by WilsonMESS on 2010-11-20
> **efflandt said:**
> Note that if you add a **bin** directory to your home directory, that should "automatically" be included in your path the next time you login into X.

**echo $PATH**
/home/efflandt/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

But the question is whether you put that script in your /home/<username>/bin/, because you said "I put this file under /home/<username>/", which is NOT in your PATH (and probably should not be).

Well, I can't find directory "bin" under my home directory (and yes, I did press CTRL+H), but I found one under /usr/ , so I put it there, with no effect after reboot...

---

### Post by WilsonMESS on 2010-11-20
> **efflandt said:**
> Note that if you add a **bin** directory to your home directory, that should "automatically" be included in your path the next time you login into X.

**echo $PATH**
/home/efflandt/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

But the question is whether you put that script in your /home/<username>/bin/, because you said "I put this file under /home/<username>/", which is NOT in your PATH (and probably should not be).

Well, I can't find directory "bin" under my home directory (and yes, I did press CTRL+H), but I found one under /usr/ , so I put it there, with no effect after reboot...

---

### Post by matt_symes on 2010-11-20
Hi

What about running the script using update-rc.d with a run level

[http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

Kind regards

---

### Post by CharlesA on 2010-11-20
> **WilsonMESS said:**
> Yes it prompts me to choose whether to open the file or to execute it.
Actually I didn't write the shell, I found this when I was troubleshooting the touchpad (which can be found here: [http://apt-blog.net/configuring_laptop_synaptics_touchpad_in_linux](http://apt-blog.net/configuring_laptop_synaptics_touchpad_in_linux) , in Chinese). The stuff actually worked automatically for a while, so I don't think it's about the slash. But yesterday, I didn't know how, it just can't work properly, and when I open the file, it didn't prompt me what to do. The gedit simply pop out and I thought it might be solved by using the chmod +x command. Though now it can work manually, I'm still trying to figure out how to make it automatially...

That's because it's set as executable.

You'd have to run it in a Terminal.

@matt_symes: That might work.

---

### Post by James78 on 2010-11-20
> **matt_symes said:**
> Hi

What about running the script using update-rc.d with a run level

[http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

Kind regards
Better yet, just run it via /etc/rc.local (chmod +x afterward!). I'm sure either will work just as well though, so it's up to the OP which one to do.

---

### Post by WilsonMESS on 2010-11-20
> **CharlesA said:**
> That's because it's set as executable.

You'd have to run it in a Terminal.

@matt_symes: That might work.

> **James78 said:**
> Better yet, just run it via /etc/rc.local (chmod +x afterward!). I'm sure either will work just as well though, so it's up to the OP which one to do.

Still no work, sigh... Dumbfounded...

---

### Post by CharlesA on 2010-11-20
What happens if you run it in a terminal?

Open a terminal, cd to where that file is and execute it by running:

```
/path/to/script.sh
```

---

### Post by WilsonMESS on 2010-11-21
> **CharlesA said:**
> What happens if you run it in a terminal?

Open a terminal, cd to where that file is and execute it by running:

```
/path/to/script.sh
```

No message echo back, just show another command indicator.

---

### Post by James78 on 2010-11-21
> **WilsonMESS said:**
> Still no work, sigh... Dumbfounded...
Maybe you will have luck with this? I'm guessing it won't work for you however, given your previous luck with all the other methods mentioned.
> After some playing around, I found the best way to run my startup script was to add it at the end of:

/etc/init.d/rcS.sh

The other menthods mentioned did not work for me.

---

### Post by CharlesA on 2010-11-21
> **WilsonMESS said:**
> No message echo back, just show another command indicator.
Ok, so it didn't spit back any errors. Try using the full path to synclient and throwing it in yer user's crontab like so:

```
crontab -e
```

Add:

```
@reboot /path/to/script
```

Reboot and see if it ran the script. If it did, you'd have two-finger scrolling enabled.

---

### Post by WilsonMESS on 2010-11-23
> **James78 said:**
> Maybe you will have luck with this? I'm guessing it won't work for you however, given your previous luck with all the other methods mentioned.

No result, ahhhhhhh... Ubuntu is driven me crazy...

---

### Post by CharlesA on 2010-11-23
Does anything happen if you run each command seperately from a terminal?

```
synclient EmulateTwoFingerMinZ=50
synclient EmulateTwoFingerMinW=6
synclient VertTwoFingerScroll=1
synclient HorizTwoFingerScroll=1
synclient VertScrollDelta=75
synclient HorizScrollDelta=100
synclient RTCornerButton=2
synclient RBCornerButton=0
synclient LTCornerButton=0
synclient LBCornerButton=0
synclient TapButton1=1
synclient TapButton2=3
synclient TapButton3=0
```

---

### Post by WilsonMESS on 2010-11-24
> **CharlesA said:**
> Does anything happen if you run each command seperately from a terminal?

```
synclient EmulateTwoFingerMinZ=50
synclient EmulateTwoFingerMinW=6
synclient VertTwoFingerScroll=1
synclient HorizTwoFingerScroll=1
synclient VertScrollDelta=75
synclient HorizScrollDelta=100
synclient RTCornerButton=2
synclient RBCornerButton=0
synclient LTCornerButton=0
synclient LBCornerButton=0
synclient TapButton1=1
synclient TapButton2=3
synclient TapButton3=0
```

It works, so I just put these commands separately in the session manager and it works! Thank you soooooo much :D~

---

### Post by CharlesA on 2010-11-25
Ok. Since that works, then try adding it to start up applications and see if it'll work there.

You may have to add the full path to synclient, but it should work.

Oh, and don't forget the shebang at the top. :)

---

### Post by WilsonMESS on 2010-11-27
> **CharlesA said:**
> Ok. Since that works, then try adding it to start up applications and see if it'll work there.

You may have to add the full path to synclient, but it should work.

Oh, and don't forget the shebang at the top. :)

Yep, succeeded with some effort. Seems that the spaces in the end of each line aren't regular and ubuntu can't figure that out. (But thats a weird explanation, since I can execute that after login)
And thanks for the tip, really appreciate your help :p

---

### Post by CharlesA on 2010-11-27
Don't forget to mark the thread as solved from thread tools. :)

---

