---
title: "Help.. my terminal is stuck in a foreign language!!!"
date: 2011-02-16
forum: General Help
---

### Post by oxf on 2011-02-16
OK here's the problem...

Some time back I posted a question about using a Greek keyboard since I'm trying to improve my limited Greek. Someone suggested a way of switching between the English and Greek desktop for Ubuntu. I tried that but it didn't work so well so I removed it. 

But I just tried to use the Terminal to install something and it's all in Greek!!! Now while I can read some of it my skills are not that good and I need it back in English again... Quickly actually! How do I go about removing the Greek from my terminal? Everything else on my system is in English so I can't figure why the terminal is stuck there.

Thanks

---

### Post by oxf on 2011-02-16
Update..
Synaptic is also partially stuck in Greek as well!!

---

### Post by Vaphell on 2011-02-16
have you set english in administration menu in Languages? at login window when you click at your user to type password in, what language is shown at the bottom toolbar?

---

### Post by oxf on 2011-02-16
> **Vaphell said:**
> have you set english in administration menu in Languages? at login window when you click at your user to type password in, what language is shown at the bottom toolbar?

Yes System>Administration>Language Support is set to English UK as the first choice. In fact I removed Greek from the list several weeks back.

English is on the toolbar...BUT.. it's in Greek characters. i.e it says "Anglika" in Greek that is!

Almost everything is in English. It's just in the terminal and synaptic etc where Greek remains.
Strange!!!

---

### Post by tredegar on 2011-02-16
I am no expert at this, but I think you should check your "environment" like this (please compare & contrast your output from the same command):```
[COLOR="SeaGreen"]tred@vaio2:~$ env[/COLOR]
ORBIT_SOCKETDIR=/tmp/orbit-tred
SSH_AGENT_PID=1727
TERM=xterm
SHELL=/bin/bash
XDG_SESSION_COOKIE=9d9c809d8aed5710f0515d5c4c8cf7fb-1297892708.176486-1092997098
WINDOWID=75497476
GNOME_KEYRING_CONTROL=/tmp/keyring-x9nkuj
GTK_MODULES=canberra-gtk-module
USER=tred
LS_COLORS=rs=0:di=01;34:ln=01;36:hl=44;37:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.axa=00;36:*.oga=00;36:*.spx=00;36:*.xspf=00;36:
SSH_AUTH_SOCK=/tmp/keyring-x9nkuj/ssh
DEFAULTS_PATH=/usr/share/gconf/gnome.default.path
SESSION_MANAGER=local/vaio2:@/tmp/.ICE-unix/1689,unix/vaio2:/tmp/.ICE-unix/1689
USERNAME=tred
XDG_CONFIG_DIRS=/etc/xdg/xdg-gnome:/etc/xdg
DESKTOP_SESSION=gnome
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
PWD=/home/tred
[COLOR="Red"]GDM_KEYBOARD_LAYOUT=gb[/COLOR]
[COLOR="Red"]LANG=en_GB.utf8[/COLOR]
GNOME_KEYRING_PID=1671
MANDATORY_PATH=/usr/share/gconf/gnome.mandatory.path
[COLOR="Red"]GDM_LANG=en_GB.utf8[/COLOR]
GDMSESSION=gnome
SPEECHD_PORT=7565
SHLVL=1
HOME=/home/tred
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
LOGNAME=tred
XDG_DATA_DIRS=/usr/share/gnome:/usr/local/share/:/usr/share/
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-ywLgwYEaBE,guid=ed8950b4c6fd750f271cd0994d5c4564
LESSOPEN=| /usr/bin/lesspipe %s
DISPLAY=:0.0
LESSCLOSE=/usr/bin/lesspipe %s %s
XAUTHORITY=/var/run/gdm/auth-for-tred-qMKmsv/database
COLORTERM=gnome-terminal
_=/usr/bin/env
[COLOR="SeaGreen"]tred@vaio2:~$[/COLOR] 

```

The above might give you some pointers to what is mis-configured.

---

### Post by oxf on 2011-02-16
Thanks Tredegar..

All my output is the same as yours (except personal settings) except I have an extra language line.

```
GDM_KEYBOARD_LAYOUT=gb
LANG=en_GB.utf8
MANDATORY_PATH=/usr/share/gconf/gnome.mandatory.path
GDM_LANG=en_GB.utf8
GDMSESSION=gnome
SHLVL=1
HOME=/home/mbdb
[COLOR=Blue]LANGUAGE=en_GB:el:en[/COLOR]
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
LOGNAME=mbdb
XDG_DATA_DIRS=/usr/share/gnome:/usr/local/share/:/usr/share/
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-MKhTCYNBVE,guid=a595b947932f4a09ecc3f15c0000001a
LESSOPEN=| /usr/bin/lesspipe %s
WINDOWPATH=7
DISPLAY=:0.0
LESSCLOSE=/usr/bin/lesspipe %s %s
XAUTHORITY=/var/run/gdm/auth-for-mbdb-36tBj9/database
COLORTERM=gnome-terminal
_=/usr/bin/env
mbdb@M2000:~$ 

```

I don't understand this extra line?
I assume that in "[COLOR=Blue]LANGUAGE=en_GB:el:en" [COLOR=Black]the[/COLOR] "el"[COLOR=Black]refers to Elinikos i.e. greek
Where do iI change it?

Thanks
[/COLOR][/COLOR]

---

### Post by Vaphell on 2011-02-16
internet says that LANGUAGE variable can be set to control gettext (thingie responsible for translation), otherwise default english is used. 

[http://ubuntuforums.org/showthread.php?t=1653704](http://ubuntuforums.org/showthread.php?t=1653704)
according to this thread offending line is located in .profile
comment it or fix it to suit your needs and see what happens after re-logging in.

---

### Post by oxf on 2011-02-17
Can someone please tell me where .profile is located?
I've looked for ~/.profile and doesn't seem to exist
Thanks

---

### Post by TeoBigusGeekus on 2011-02-17
Can you post us the contents of your .bashrc file?

---

### Post by oxf on 2011-02-17
> **TeoBigusGeekus said:**
> Can you post us the contents of your .bashrc file?

Thanks..

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
if [ -x /usr/lib/command-not-found -o -x /usr/share/command-not-found ]; then
    function command_not_found_handle {
            # check because c-n-f could've been removed in the meantime
                if [ -x /usr/lib/command-not-found ]; then
           /usr/bin/python /usr/lib/command-not-found -- $1
                   return $?
                elif [ -x /usr/share/command-not-found ]; then
           /usr/bin/python /usr/share/command-not-found -- $1
                   return $?
        else
           return 127
        fi
    }
fi
```

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
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

umask 022
```

---

### Post by TeoBigusGeekus on 2011-02-17
Hmm, nothing very useful in there.
Can you also post us the contents of the .gnomerc file?

---

### Post by oxf on 2011-02-17
> **TeoBigusGeekus said:**
> Hmm, nothing very useful in there.
Can you also post us the contents of the .gnomerc file?

OK..presume you mean this?

```
# If we are running the GNOME session, source ~/.gnomerc

BASESTARTUP=${STARTUP% *}
BASESTARTUP=${BASESTARTUP##*/}
if [ "$BASESTARTUP" = x-session-manager ]; then
    BASESTARTUP=$(basename $(readlink /etc/alternatives/x-session-manager))
fi
case "$BASESTARTUP" in
  gnome-session|gnome3-session)
    GNOMERC=$HOME/.gnomerc
    if [ -r "$GNOMERC" ]; then
      . "$GNOMERC"
    fi
    # We prepend /usr/share/gnome since its defaults.list actually points 
    # to /etc so it is configurable.
    if [ -z "$XDG_DATA_DIRS" ]; then
      XDG_DATA_DIRS=/usr/share/gnome:/usr/local/share/:/usr/share/
    else
      XDG_DATA_DIRS=/usr/share/gnome:"$XDG_DATA_DIRS"
    fi
    export XDG_DATA_DIRS
    ;;
esac
```

---

### Post by TeoBigusGeekus on 2011-02-17
Add this line to .gnomerc
```
export LANG=en_US.UTF-8
```
log out and in again.

---

### Post by oxf on 2011-02-17
> **TeoBigusGeekus said:**
> Add this line to .gnomerc
```
export LANG=en_US.UTF-8
```log out and in again.

unfortunately no change! :frown:

---

### Post by Vaphell on 2011-02-17
maybe grep will find it?
```
grep -r 'LANGUAGE=en_GB:el:en' ~
```
or something like that?
it can take a while

---

### Post by oxf on 2011-02-17
> **Vaphell said:**
> maybe grep will find it?
```
grep -r 'LANGUAGE=en_GB:el:en' ~
```or something like that?
it can take a while

Thanks
well it's taking ages but maybe this tells us something?
Will report back after work. 

```
mbdb@M2000:~$ grep -r 'LANGUAGE=en_GB:el:en' ~
grep: /home/mbdb/.pulse/9ed4a182068665727b0e6a2d00000009-runtime/native: No such device or address
grep: /home/mbdb/.local/share/ubuntuone/Purchased from Ubuntu One: No such file or directory
 sudo grep -r 'LANGUAGE=en_GB/home/mbdb/.mozilla/firefox/0hhf6omt.default/Cache/D38FBED3d01:<font color="Blue">LANGUAGE=en_GB:el:en</font>
/home/mbdb/.mozilla/firefox/0hhf6omt.default/Cache/D38FBED3d01:I assume that in &quot;<font color="Blue">LANGUAGE=en_GB:el:en&quot; <font color="Black">the</font> &quot;el&quot;<font color="Black">refers to Elinikos i.e. greek<br />
/home/mbdb/.mozilla/firefox/0hhf6omt.default/Cache/E78AA29Cd01:<font color="Blue">LANGUAGE=en_GB:el:en</font>
/home/mbdb/.mozilla/firefox/0hhf6omt.default/Cache/E78AA29Cd01:I assume that in &quot;<font color="Blue">LANGUAGE=en_GB:el:en&quot; <font color="Black">the</font> &quot;el&quot;<font color="Black">refers to Elinikos i.e. greek<br />
/home/mbdb/.mozilla/firefox/0hhf6omt.default/Cache/78B9B3CFd01:        overflow: auto">grep -r 'LANGUAGE=en_GB:el:en' ~</pre>
grep: /home/mbdb/.mozilla/firefox/0hhf6omt.default/lock: No such file or directory
mbdb@M2000:~$  sudo grep -r 'LANGUAGE=en_GB
> 
> sudo grep -r  'LANGUAGE=en_GB:el:en' ~
> grep -r 'LANGUAGE=en_GB:el:en' ~
>
```

---

### Post by cascade9 on 2011-02-17
This probably wotn work, but have you tried bleachbit? System-> localizations might just do the trick ;)

---

### Post by Vaphell on 2011-02-17
so yor home dir most likely doesn't have that line anywhere. When you think about it, it sorta does make sense. Login screen is independent of your own settings so it must be system wide setting
You could create new user account and log in to it to make sure that this problem is in fact caused by a system wide configuration. 

try grepping in /etc
```
grep -r 'LANGUAGE' /etc
```

---

### Post by oxf on 2011-02-17
> **Vaphell said:**
> so yor home dir most likely doesn't have that line anywhere. When you think about it, it sorta does make sense. Login screen is independent of your own settings so it must be system wide setting
You could create new user account and log in to it to make sure that this problem is in fact caused by a system wide configuration. 

try grepping in /etc
```
grep -r 'LANGUAGE' /etc
```

I'll maybe try that tomorrow when I'm awake!

```
mbdb@M2000:~$ sudo grep -r 'LANGUAGE' /etc
[sudo] password for mbdb: 
/etc/environment:LANGUAGE="en_GB:el:en"
/etc/init/mountall.conf:        export LANG LANGUAGE LC_MESSAGES LC_ALL
/etc/init/gdm.conf:    export LANG LANGUAGE
/etc/init/gdm.conf:    export LANG LANGUAGE
/etc/default/locale:LANGUAGE="en_GB:el:en"
Binary file /etc/alternatives/testparm matches
Binary file /etc/alternatives/nmblookup matches
Binary file /etc/alternatives/gnome-text-editor matches
Binary file /etc/alternatives/net matches
grep: /etc/blkid.tab: No such file or directory
/etc/speech-dispatcher/modules/swift-generic.conf:# You can use the variables $LANGUAGE, $VOICE, $PITCH and $RATE
/etc/speech-dispatcher/modules/espeak-generic.conf:# You can use the variables $LANGUAGE, $VOICE, $PITCH and $RATE
/etc/speech-dispatcher/modules/llia_phon-generic.conf:# You can use the variables $LANGUAGE, $VOICE, $PITCH and $RATE
/etc/speech-dispatcher/modules/epos-generic.conf:# You can use the variables $LANGUAGE, $VOICE, $PITCH and $RATE
/etc/speech-dispatcher/modules/epos-generic.conf:"epos-say -o --language $LANGUAGE --voice $VOICE --init_f $PITCH --init_t $RATE \
/etc/speech-dispatcher/modules/espeak-mbrola-generic.conf:# You can use the variables $LANGUAGE, $VOICE, $PITCH and $RATE
/etc/gdm/failsafeXServer:    export LANG LANGUAGE
/etc/gdm/failsafeXServer:    export LANG LANGUAGE
/etc/cron.daily/apt:    export LANG LANGUAGE LC_MESSAGES LC_ALL
mbdb@M2000:~$ 

```

Well perhaps this is what I'm looking for. How do I edit it to fix my problem?

---

### Post by Vaphell on 2011-02-18
yes, /etc/default/locale is the perpetrator here

on my box that file has only LANG=... line
open it with admin rights
```
gksu gedit /etc/default/locale
```
and comment (probably with #) or wipe that LANGUAGE line entirely.

i see that /etc/environment has that line too (my version has only PATH=...) - act accordingly

---

### Post by oxf on 2011-02-19
> **Vaphell said:**
> yes, /etc/default/locale is the perpetrator here

on my box that file has only LANG=... line
open it with admin rights
```
gksu gedit /etc/default/locale
```and comment (probably with #) or wipe that LANGUAGE line entirely.

i see that /etc/environment has that line too (my version has only PATH=...) - act accordingly

OK thank you Vaphell. That seems to have fixed the problem on the login page.  But it's still in Greek in terminal so I will keep looking..

---

### Post by oxf on 2011-02-20
OK I've resolved the problem with the login language but I've still got Greek in two places:

1. In Terminal when I use the "apt-get" command
2. In Synaptic.

This would indicate that it's the package manager that contains the problem. Any sugestions where I should look for the offending line?

Thanks

---

### Post by Vaphell on 2011-02-20
i have to admit language support is a mess. I have virtual machine with 10.10 where i do all kinds of tests, so i switched from polish (default) to english using the Language window in administration. Long story short it's half-polish half-english now - app menus are still in polish.
It's a shame that language settings are spread around in dozens of places and that they generally don't obey central configuration :/

Do you have *any* packages of greek language support installed in synaptic? If there are no greek packages there is nowhere to get greek texts from so it should fall back on english.

---

### Post by oxf on 2011-02-23
> **Vaphell said:**
> i have to admit language support is a mess. I have virtual machine with 10.10 where i do all kinds of tests, so i switched from polish (default) to english using the Language window in administration. Long story short it's half-polish half-english now - app menus are still in polish.
It's a shame that language settings are spread around in dozens of places and that they generally don't obey central configuration :/

Do you have *any* packages of greek language support installed in synaptic? If there are no greek packages there is nowhere to get greek texts from so it should fall back on english.

I don't that I can see. It's definately linked to the package manager in some way. Ultimately I guess it's not that big of a deal as I need to replace the HD soon and will have to reinstall the OS. But I've been trying to understand how it happened for future knowledge!
Hey maybe I should just learn Polish? Then I can talked to all the polish people around here! :D

---

