---
title: "places not open, desktop blank after i installed the second radeon 6990.. pls help"
date: 2011-11-11
forum: General Help
---

### Post by nokia2mon2 on 2011-11-11
i have 2 radeon 6990 and this what i did


1-
 -- install ATI proprietary driver
> cd; mkdir tmp; cd tmp
wget [http://www2.ati.com/drivers/linux/ati-driver-installer-11-9-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-11-9-x86.x86_64.run)
sh ati-driver-installer-11-9-x86.x86_64.run
follow installer; reboot
apt-get install cmake libroot-python-dev libboost1.40-all-dev 
cd ~/tmp
wget [http://download2-developer.amd.com/amd/APPSDK/AMD-APP-SDK-v2.5-lnx64.tgz](http://download2-developer.amd.com/amd/APPSDK/AMD-APP-SDK-v2.5-lnx64.tgz)
tar xvzf AMD-APP-SDK-v2.5-lnx64.tgz
tar xvzf AMD-APP-SDK-v2.5-RC2-lnx64.tgz
mv AMD-APP-SDK-v2.5-RC2-lnx64/ /opt
cd /
tar xvxf ~/tmp/icd-registration.tgz
edit .bashrc
vi ~/.bashrc
add the following to the end of .bashrc

> export AMDAPPSDKROOT=/opt/AMD-APP-SDK-v2.5-RC2-lnx64/
export AMDAPPSDKSAMPLESROOT=/opt/AMD-APP-SDK-v2.5-RC2-lnx64/
export LD_LIBRARY_PATH=${AMDAPPSDKROOT}lib/x86_64:${LD_LIBRARY_PATH}
export ATISTREAMSDKROOT=$AMDAPPSDKROOTsave; quit

> cd ~/tmp
svn co [https://calpp.svn.sourceforge.net/svnroot/calpp](https://calpp.svn.sourceforge.net/svnroot/calpp) calpp
cd calpp/trunk/
cmake .
make
make install

cd ~/tmp
svn checkout [http://pyrit.googlecode.com/svn/trunk/](http://pyrit.googlecode.com/svn/trunk/) pyrit_svn
> cd pyrit_svn/pyrit/
python setup.py build
python setup.py install

cd ~/tmp/pyrit_svn/cpyrit_calpp/

vi setup.py
i changed
VERSION = '0.4.0-dev'
to
VERSION = '0.4.1-dev'
( why i did that ? because: this is to match Pyrit version; otherwise will see version mismatch while running)

then i change
CALPP_INC_DIRS.append(os.path.join(CALPP_INC_DIR, 'include'))
to
CALPP_INC_DIRS.append(os.path.join(CALPP_INC_DIR, 'include/CAL'))

> python setup.py build
python setup.py install
 
pyrit list_cores

image :
[http://sites.google.com/site/nozyczek/_/rsrc/1319764590162/config/pagetemplates/how-to-install-pyrit-with-ati-cal-support-under/pyrit_list_cores.png](http://sites.google.com/site/nozyczek/_/rsrc/1319764590162/config/pagetemplates/how-to-install-pyrit-with-ati-cal-support-under/pyrit_list_cores.png)

--------
--------

2- made the second radeon shown: 
A- Open up /root/.bashrc and add export DISPLAY=:0 in the end line, i must did that in /home/username/.bashrc , but there is no files there si so i did it from the root dir
here is the file after the edit:
```

# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
if [[ -n "$PS1" ]]; then

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
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;31m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
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
fi

# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

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
#if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
#    . /etc/bash_completion
 export HISTCONTROL=ignoreboth
fi
export PATH=$PATH:/etc/alternatives/gem-bin
# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

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
#if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
#    . /etc/bash_completion
#fi
  export HISTCONTROL=ignoreboth
fi
export PATH=$PATH:/etc/alternatives/gem-bin
export AMDAPPSDKROOT=/opt/AMD-APP-SDK-v2.5-RC2-lnx64/
export AMDAPPSDKSAMPLESROOT=/opt/AMD-APP-SDK-v2.5-RC2-lnx64/
export LD_LIBRARY_PATH=${AMDAPPSDKROOT}lib/x86_64:${LD_LIBRARY_PATH}
export ATISTREAMSDKROOT=$AMDAPPSDKROOT
export DISPLAY=:0




```B- sudo aticonfig --adapter=all --initial -f

c- Log off and login

d- now the problems  started:
1- all files and folder not shown in the desktop, the right mouse not work in the desktop
2- all folders in places cant be open
3- after 2-3 reboot the desktop came blank and the background of the desktop came blank and all files and folder not shown in the desktop, the right mouse not work in the desktop and all folders in places cant be open.
4- i can open terminal and work normal , in the panel: application and system works
5- the only good thing that this is the result aticonfig --list-adapters

> root@bt:~# aticonfig --list-adapters
* 0. 03:00.0 AMD Radeon HD 6900 Series
  1. 04:00.0 AMD Radeon HD 6900 Series
  2. 07:00.0 AMD Radeon HD 6900 Series
  3. 08:00.0 AMD Radeon HD 6900 Series

* - Default adapter
----------------------------

i think i need to make change in /etc/X11/xorg.conf to make every thing smooth, here is what in the file:


```
Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
        Screen         "aticonfig-Screen[1]-0" RightOf "aticonfig-Screen[0]-0"
        Screen         "aticonfig-Screen[2]-0" RightOf "aticonfig-Screen[1]-0"
        Screen         "aticonfig-Screen[3]-0" RightOf "aticonfig-Screen[2]-0"
EndSection

Section "Module"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[1]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[2]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[3]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:3:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[1]-0"
        Driver      "fglrx"
        BusID       "PCI:4:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[2]-0"
        Driver      "fglrx"
BusID       "PCI:7:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[3]-0"
        Driver      "fglrx"
        BusID       "PCI:8:0:0"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[1]-0"
        Device     "aticonfig-Device[1]-0"
        Monitor    "aticonfig-Monitor[1]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[2]-0"
        Device     "aticonfig-Device[2]-0"
        Monitor    "aticonfig-Monitor[2]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[3]-0"
        Device     "aticonfig-Device[3]-0"
        Monitor    "aticonfig-Monitor[3]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

```------------------
Note: 
1- when i uninstall ATI proprietary driver:
```
cd /usr/share/ati
sh fglrx-uninstall.sh
reboot
```every thing come back to work, so ithink there is something wrong on my setting.
2- every time i make reboot now its show me message the file manager not respond
3- when i type nautilus, this is the results 
> (nautilus:8946): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(nautilus:8946): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
4- when i type gksudo nautilus:
> (nautilus:9143): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(nautilus:9143): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

5- im using backtrack 5 r2 

6- im using 1 monitor only



please help me

Regards

---

### Post by nokia2mon2 on 2011-11-12
i try do the same steps in other machine and i face the same issue!

any idea ?

---

