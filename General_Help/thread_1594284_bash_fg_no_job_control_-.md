---
title: "bash: fg: no job control - ?"
date: 2010-10-12
forum: General Help
---

### Post by Bucky Ball on 2010-10-12
Hi all,

Every time I open a terminal I get this in the first line of the screen:

```
bash: fg: no job control
```How do I stop this happening? I did something but can't remember what. ;)

---

### Post by Diametric on 2010-10-12
Not exactly sure, but I'd check your environment variables.  You may have exported something and now bash displays this message every time you open a terminal.  Check with someone, but I think the "env" command without arguments shows all environment variables set in bash...

---

### Post by Bucky Ball on 2010-10-12
Thanks for that. I entered 'env' and got this:

```
anna@katie:~$ env
GPG_AGENT_INFO=/tmp/seahorse-m37T7o/S.gpg-agent:7637:1
SHELL=/bin/bash
TERM=xterm
XDG_SESSION_COOKIE=1e486c1b2f0b3657433d29394b459cdb-1286926253.510133-1232389287
GTK_RC_FILES=/etc/gtk/gtkrc:/home/anna/.gtkrc-1.2-gnome2
WINDOWID=50331741
USER=anna
LS_COLORS=no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.svgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:
LIBGL_DRIVERS_PATH=/usr/lib32/dri:/usr/lib64/dri
SSH_AUTH_SOCK=/tmp/keyring-vFu0bC/ssh
GNOME_KEYRING_SOCKET=/tmp/keyring-vFu0bC/socket
SESSION_MANAGER=local/katie:/tmp/.ICE-unix/7566
USERNAME=anna
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
DESKTOP_SESSION=default
GDM_XSERVER_LOCATION=local
PWD=/home/anna
LANG=en_AU.UTF-8
GNOME_KEYRING_PID=7565
GDM_LANG=en_AU.UTF-8
GDMSESSION=default
HISTCONTROL=ignoreboth
SHLVL=1
HOME=/home/anna
GNOME_DESKTOP_SESSION_ID=Default
LOGNAME=anna
XDG_DATA_DIRS=/usr/local/share/:/usr/share/:/usr/share/gdm/
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-uLDRKvAlvD,guid=6f32948a7f9f207abc78fb354cb4efae
LESSOPEN=| /usr/bin/lesspipe %s
WINDOWPATH=7
DISPLAY=:0.0
LESSCLOSE=/usr/bin/lesspipe %s %s
COLORTERM=gnome-terminal
XAUTHORITY=/tmp/.gdm3W7EKV
_=/usr/bin/env
```All very interesting but means not much to me and no idea what to do next. I did just get up so that might have something to do with the brain atrophy! This is what I get when I open a terminal:

```
bash: fg: no job control
anna@katie:~$ 
```

---

### Post by Bucky Ball on 2010-11-03
Just had time to have a brief look at this again. I'm wondering if it is the last line of code which I have in bold in the output of the 'env' command:

```

anna@katie:~$ env
GPG_AGENT_INFO=/tmp/seahorse-m37T7o/S.gpg-agent:7637:1
SHELL=/bin/bash
TERM=xterm
XDG_SESSION_COOKIE=1e486c1b2f0b3657433d29394b459cdb-1286926253.510133-1232389287
GTK_RC_FILES=/etc/gtk/gtkrc:/home/anna/.gtkrc-1.2-gnome2
WINDOWID=50331741
USER=anna
LS_COLORS=no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.svgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:
LIBGL_DRIVERS_PATH=/usr/lib32/dri:/usr/lib64/dri
SSH_AUTH_SOCK=/tmp/keyring-vFu0bC/ssh
GNOME_KEYRING_SOCKET=/tmp/keyring-vFu0bC/socket
SESSION_MANAGER=local/katie:/tmp/.ICE-unix/7566
USERNAME=anna
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
DESKTOP_SESSION=default
GDM_XSERVER_LOCATION=local
PWD=/home/anna
LANG=en_AU.UTF-8
GNOME_KEYRING_PID=7565
GDM_LANG=en_AU.UTF-8
GDMSESSION=default
HISTCONTROL=ignoreboth
SHLVL=1
HOME=/home/anna
GNOME_DESKTOP_SESSION_ID=Default
LOGNAME=anna
XDG_DATA_DIRS=/usr/local/share/:/usr/share/:/usr/share/gdm/
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-uLDRKvAlvD,guid=6f32948a7f9f207abc78fb354cb4efae
LESSOPEN=| /usr/bin/lesspipe %s
WINDOWPATH=7
DISPLAY=:0.0
LESSCLOSE=/usr/bin/lesspipe %s %s
COLORTERM=gnome-terminal
[B]XAUTHORITY=/tmp/.gdm3W7EKV
_=/usr/bin/env[/B]
```

The problem ain't going away I noticed when I did a little work on that machine recently.

---

### Post by gmargo on 2010-11-03
You must have an "fg" in your startup files.  Grep for it:
```

cd
grep fg .bashrc .profile

```

---

### Post by Bucky Ball on 2010-11-03
Cheers, thanks for that. This is what I get:

```
anna@katie:~$ grep fg .bashrc .profile
.bashrc:    #alias fgrep='fgrep --color=auto'
```

So something's going on there. How do I kill it?

---

### Post by Bucky Ball on 2010-12-28
Well, problem persists. Worked on that machine the other day and it reminded me. How do I find and kill the job???

---

### Post by Crusty Old Fart on 2010-12-28
> **Bucky Ball said:**
> ...How do I find and kill the job???
This is just a shot in the dark...

See [http://ss64.com/bash/fg.html](http://ss64.com/bash/fg.html) (man page for: fg)
And [http://ss64.com/bash/jobs.html](http://ss64.com/bash/jobs.html) (man page for: jobs)
Finally [http://ss64.com/bash/kill.html](http://ss64.com/bash/kill.html) (man page for: kill)

That might get you a little closer to getting rid of it.

Good Luck!

---

### Post by Crusty Old Fart on 2010-12-28
> **Bucky Ball said:**
> Cheers, thanks for that. This is what I get:

```
anna@katie:~$ grep fg .bashrc .profile
.bashrc:    #alias fgrep='fgrep --color=auto'
```So something's going on there. How do I kill it?
There's nothing going on there other than the color parameter being set for the output of your fgrep command.

The problem lies somewhere else.

---

### Post by Bucky Ball on 2010-12-28
Where I wonder? Will start digging in awhile. Thanks for the input ... ;)

---

### Post by matt_symes on 2010-12-28
Hi

Post the entire output of .bashrc .profile. The clue may be there.

Kind regards

---

### Post by Bucky Ball on 2010-12-28
The entire output is what I posted previously Matt:

```
bash: fg: no job control
anna@katie:~$ grep fg .bashrc .profile
.bashrc:    #alias fgrep='fgrep --color=auto'
```That's it. In fact, upgraded this machine from 8.04 to 10.04 recently and still the same.

---

### Post by Crusty Old Fart on 2010-12-28
> **matt_symes said:**
> Hi

Post the entire output of .bashrc .profile. The clue may be there.

Kind regards
...especially if it matches something similar in the output of the jobs command. Would be nice to see that output as well.

Howdy Matt.

---

### Post by Bucky Ball on 2010-12-28
No luck getting anything out of the jobs command. What exactly should I be putting in there to get the output you're after?

---

### Post by Crusty Old Fart on 2010-12-28
> **Bucky Ball said:**
> The entire output is what I posted previously Matt:

```
bash: fg: no job control
anna@katie:~$ grep fg .bashrc .profile
.bashrc:    #alias fgrep='fgrep --color=auto'
```That's it. In fact, upgraded this machine from 8.04 to 10.04 recently and still the same.
I think Matt is looking for something more like this:
```

cat .bashrc
cat .profile

```[s]The output from:
```

[s]jobs[/s]

```would be nice to see as well.[/s] [COLOR=Blue]Sorry Bucky, I just doubled with ya. Since you didn't get any output from the jobs command, it seems to suggest that whatever is trying to be brought to the foreground with the fg command is failing to run. Kinda makes sense given that fg is giving an error.
[/COLOR]

---

### Post by Bucky Ball on 2010-12-28
```
bash: fg: no job control
anna@katie:~$ cat .bashrc
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups
# ... and ignore same sucessive entries.
export HISTCONTROL=ignoreboth

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
if [ "$TERM" != "dumb" ] && [ -x /usr/bin/dircolors ]; then
    eval "`dircolors -b`"
   ** alias ls='ls --color=auto'**
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'

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

% export SDL_audiodriver=alsa
```Could it be this?

 ```
alias ls='ls --color=auto'
```

```
bash: fg: no job control
anna@katie:~$ cat .profile
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
    . "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
```

---

### Post by matt_symes on 2010-12-28
Hi

I can't see anything wrong with .bashrc and .profile so, unless i am missing something, the problem is not there.

> Could it be this?

Code:

alias ls='ls --color=auto'

No. It's not that.

How are you starting the terminal? Are you using the -e switch somehow?


```
NAME
       gnome-terminal &#8212; is a terminal emulation application.

SYNOPSIS
       gnome-terminal  [-e,  --command=STRING]   [-x,  --execute ]  [--window-
       with-profile=PROFILENAME]  [--tab-with-profile=PROFILENAME]  [--window-
       with-profile-internal-id=PROFILEID]       [--tab-with-profile-internal-
       id=PROFILEID]    [--role=ROLE]    [--show-menubar]     [--hide-menubar]
       [--geometry=GEOMETRY]     [--disable-factory]     [-t,   --title=TITLE]
       [--working-directory=DIRNAME]  [--usage]  [-?, --help]

...

-e, --command=STRING
                 Execute the argument to this option inside the terminal.

```

Hello Crusty. Hope your well.

Kind regarrds

---

### Post by Bucky Ball on 2010-12-28
-e switch? No.

---

### Post by Crusty Old Fart on 2010-12-29
Never mind -- See Post #21

---

### Post by Crusty Old Fart on 2010-12-29
> **matt_symes said:**
> ...Hello Crusty. Hope your well...
Doin' fine Matt. Hope you are too.

[s]How about taking a look at this: [Where is the bash log file?]("http://www.linuxquestions.org/questions/linux-general-1/where-is-the-bash-log-file-434359/") -- especially the last post, and tell us what you think.[/s] [COLOR=Blue]Never mind. See post #21.[/COLOR]

---

### Post by Crusty Old Fart on 2010-12-29
Well...well...well...

I think I found it. It's the last line in the .bashrc file:
```

% export SDL_audiodriver=alsa

```If you comment that line out, or blow it away. You won't be pestered by: **bash: fg: no job control** anymore.

That line didn't look right to me. So I added it to my .bashrc file and opened a shell. Sure enough, I got served up brand-new, shiny  **bash: fg: no job control** messages each time I opened a shell.

And then...I blew away the "% export SDL_audiodriver=alsa" line and all was ducky on the pond again. Nyuck, nyuck, nyuck, nyuck, nyuck...:cool:

It may be that you need:  % export SDL_audiodriver=alsa for something. But, when it begins with the percent sign (%), which can be used as a substitute for the fg command in some cases, it doesn't seem to be workin' right. <-- A big fat guess on my part. I have no idea what it's supposed to do, or why it's there.

Good Luck, Bucky,

Crusty

---

### Post by Bucky Ball on 2010-12-29
Crusty=LEGEND!

I commented out that line and sure enough, no more probs. I may indeed need it for something so put that line back in and took out the % and sure enough, still no problems.

Thanks a mountain you two and I'll consider this solved (although removing the % may create some odd problem in future so better remember what I did!).

Cheers ... :)

---

### Post by matt_symes on 2010-12-29
Hi

Good call. I have no idea what the % is doing there.

Maybe, in your .bashrc file, you could just add....

```
export SDL_audiodriver=alsa
```

....if you get any problems, as that's what works in bash.

Kind regards

---

### Post by Crusty Old Fart on 2010-12-29
> **Bucky Ball said:**
> Crusty=LEGEND!

I commented out that line and sure enough, no more probs. I may indeed need it for something so put that line back in and took out the % and sure enough, still no problems.

Thanks a mountain you two and I'll consider this solved (although removing the % may create some odd problem in future so better remember what I did!).

Cheers ... :)

You're mighty welcome. This was a fun nut to crack. I'm especially glad that Matt showed up. I doubt that I'd have hit paydirt without his assistance. Thanks Matt!

I've found that the easiest way for me to remember what I've done is to make a copy of the file I'm about to modify and put a suffix on its name of _original. As in:
```

cp .bashrc .bashrc_original

```Then I can safely hack the .bashrc file 'till the cows come home, knowing that I have the original file saved as .bashrc_original.

---

### Post by Crusty Old Fart on 2010-12-29
Here's a helpful reference that shed some light on what was going on here:
[http://www.faqs.org/docs/bashman/bashref_78.html](http://www.faqs.org/docs/bashman/bashref_78.html)

---

### Post by Bucky Ball on 2010-12-29
> **matt_symes said:**
> Hi

Maybe, in your .bashrc file, you could just add....

```
export SDL_audiodriver=alsa
```

Cheers, that what I tried after commenting the line out. I put it back in and removed the % and it worked fine. Sticking with it!

Crusty: Yea, for anything more elaborate I generally make a copy before splicing and dicing. Might pay here. Haven't checked audio yet!

---

