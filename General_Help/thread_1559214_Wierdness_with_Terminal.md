---
title: "Wierdness with Terminal"
date: 2010-08-23
forum: General Help
---

### Post by jeddycakes on 2010-08-23
Hi

I was wondering if anyone could figure this one out. I've never seen it before and its entirely possible that I may have done something to my system to cause it.
Basically, when I open any new terminal window I have a '$' sign instead of the usual blah@blah etc. Also, the cursor keys don't work :S

Attached is a screenshot of what I mean. Any help would be greatly appreciated.

---

### Post by WorMzy on 2010-08-23
Can you enter commands into it? If so, can you post the output of ```
echo $SHELL
```

---

### Post by jeddycakes on 2010-08-23
/bin/bash

This is the only output I got.

I recently added the application Celtx straight to the bin folder (seemed unusual  at the time as I've never added an app this way before)

Could this be doing funky things that I don't understand?

Thanks for the quick reply, got to love the linux community; if this were a Windows site I dare say people would smirk and be all elitist at my newb ***. lol

EDIT: have been able to input commands also; installed audicity earlier from command line no probs.

---

### Post by Grenage on 2010-08-23
Off topic: Nice desktop!

---

### Post by jeddycakes on 2010-08-23
Lol Thanks dude

---

### Post by WorMzy on 2010-08-23
I'd never heard of Celtx, but I doubt it'd have caused this.

That output was all I was expecting, so don't worry about that; it just confirmed that you're running bash, and not dash or zsh or some other shell.

Can you post the output of these commands now:
```
cat /etc/bash.bashrc
```
```
cat ~/.bashrc
```
```
cat /etc/profile
```
```
cat ~/.bash_profile
```
```
cat /etc/inputrc
```
```
cat ~/.inputrc
```

Also, could you put [CODE[COLOR="Black"]][[/COLOR]/CODE] tags around each command's output so that it's easier to read, please. Oh, and don't worry if it tells you "File not found", just be sure to include that in your reply. :)

---

### Post by Grenage on 2010-08-23
I was curious about .bashrc perhaps missing the flag for current directory and user?

Under my ~/.bashrc I have:

PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '

are you missing the '\w' (amongst others)?

---

### Post by jeddycakes on 2010-08-23
Ok then here we go:

for cat /etc/bash.bashrc -
```

$ cat /etc/bash.bashrc
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
for cat ~/.bashrc - 
```

$ cat ~/.bashrc
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
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

```

for cat /etc/profile - 
```

$ cat /etc/profile
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

for cat ~/.bash_profile - 
```

$ cat ~/.bash_profile
cat: /home/jed/.bash_profile: No such file or directory

```

for cat /etc/inputrc - 
```

$ cat /etc/inputrc
# /etc/inputrc - global inputrc for libreadline
# See readline(3readline) and `info rluserman' for more information.

# Be 8 bit clean.
set input-meta on
set output-meta on

# To allow the use of 8bit-characters like the german umlauts, comment out
# the line below. However this makes the meta key not work as a meta key,
# which is annoying to those which don't need to type in 8-bit characters.

# set convert-meta off

# try to enable the application keypad when it is called.  Some systems
# need this to enable the arrow keys.
# set enable-keypad on

# see /usr/share/doc/bash/inputrc.arrows for other codes of arrow keys

# do not bell on tab-completion
# set bell-style none
# set bell-style visible

# some defaults / modifications for the emacs mode
$if mode=emacs

# allow the use of the Home/End keys
"\e[1~": beginning-of-line
"\e[4~": end-of-line

# allow the use of the Delete/Insert keys
"\e[3~": delete-char
"\e[2~": quoted-insert

# mappings for "page up" and "page down" to step to the beginning/end
# of the history
# "\e[5~": beginning-of-history
# "\e[6~": end-of-history

# alternate mappings for "page up" and "page down" to search the history
# "\e[5~": history-search-backward
# "\e[6~": history-search-forward

# mappings for Ctrl-left-arrow and Ctrl-right-arrow for word moving
"\e[1;5C": forward-word
"\e[1;5D": backward-word
"\e[5C": forward-word
"\e[5D": backward-word
"\e\e[C": forward-word
"\e\e[D": backward-word

$if term=rxvt
"\e[8~": end-of-line
"\eOc": forward-word
"\eOd": backward-word
$endif

# for non RH/Debian xterm, can't hurt for RH/Debian xterm
# "\eOH": beginning-of-line
# "\eOF": end-of-line

# for freebsd console
# "\e[H": beginning-of-line
# "\e[F": end-of-line

$endif

```

for cat ~/.inputrc - 
```

$ cat ~/.inputrc
cat: /home/jed/.inputrc: No such file or directory

```

Hope from this you can glean some information that will be useful. TY for your time and effort!

---

### Post by jeddycakes on 2010-08-23
@Grenage

I have:

```

PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '

```

Pretty much the same as yours.

---

### Post by WorMzy on 2010-08-23
There's a few differences between your .bashrc file and mine, most of them are negligible, but there's a couple that might be causing a problem.

I'm going to post mine for you to try out and see if it makes any difference, but I recommend you rename, or make a backup of your existing one, just incase mine doesn't fix the problem and/or makes more problems crop up. (Press Ctrl+H in nautilus to show hidden files btw)

Here's mine:

```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

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
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi
```

If that doesn't help at all, then I'm not sure what the problem is; the rest of your config matches my own.

You haven't edited gnome-terminal's settings have you? Check in it's preferences (Edit -> Profile Preferences) that "run a custom command instead of my shell" isn't checked.

---

### Post by jeddycakes on 2010-08-23
I copied your config over and.....nowt. :/

I had a look in my terminal profile preferences and that box is unchecked, so the default command should be present. Totally flummoxed!

Thanks for your help. I can still run commands from terminal so hopefully everything will be fine.

If anyone else has an idea, I would be grateful; like I said it still seems to work it just feels...wierd lol.

EDIT: I'll try and remove all the Celtx stuff I added to bin, that may work. Mebbe.

---

### Post by WorMzy on 2010-08-23
Just checking, but you did close the terminal and open a new one, right? 

If so, try adding this to the end of .bash_profile:

```
PS1='\u@\h \W\$ '
```

---

### Post by jeddycakes on 2010-08-23
Where in the file should i place it? 

To answer your question, I did restart terminal; I even restarted my session in the hope that that may help. 

Bloomin strange, no?

---

### Post by WorMzy on 2010-08-23
Add it right at the bottom, on a new line.

---

### Post by jeddycakes on 2010-08-23
Still nada.

---

### Post by iponeverything on 2010-08-23
to be honest, I have not read through the thread to see if you have already tried this.. so my apologies if you have. 

try:

```
cp /etc/skel/.bashrc ~ 
```

---

### Post by WorMzy on 2010-08-23
Okay, it seems like it's not reading your profile at all. At this point I'd first suggest reinstalling bash:

```
sudo apt-get install --reinstall bash
```

If that doesn't fix the problem, then look into using a different shell. I can personally recommend zsh.

```
sudo apt-get install zsh
```

But you should already have dash installed, so give that a whirl. To try out a shell, just open a terminal and enter the shell's name.

e.g.
```
dash
```

Of course, each shell is different, and if you're content with a promptless bash, there's no real reason to switch.

I can send you a config file for zsh that'll make the prompt look like the one bash should have. It'll be like you're using bash, but with all the features of zsh.

---

### Post by jeddycakes on 2010-08-24
Tried to install zsh, but got this instead:-

```

$ sudo apt-get install zsh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  wwwconfig-common libjs-mootools javascript-common
Use 'apt-get autoremove' to remove them.
Suggested packages:
  zsh-doc
The following NEW packages will be installed
  zsh
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 4,325kB/4,971kB of archives.
After this operation, 13.0MB of additional disk space will be used.
Get: 1 http://gb.archive.ubuntu.com/ubuntu/ lucid/main zsh 4.3.10-5ubuntu3 [4,325kB]
Fetched 4,325kB in 20s (207kB/s)                                               
(Reading database ... 192935 files and directories currently installed.)
Preparing to replace bash 4.1-2ubuntu3 (using .../bash_4.1-2ubuntu3_i386.deb) ...
dpkg (subprocess): unable to execute old pre-removal script: No such file or directory
dpkg: warning: old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg (subprocess): unable to execute new pre-removal script: No such file or directory
dpkg: error processing /var/cache/apt/archives/bash_4.1-2ubuntu3_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: No such file or directory
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/bash_4.1-2ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
$ 

```

its like my system doesn't want to be fixed. Wierd.
Reinstalling bash came up with a pretty much identical error message:-

```

$ sudo apt-get install --reinstall bash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  wwwconfig-common libjs-mootools javascript-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/646kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 192935 files and directories currently installed.)
Preparing to replace bash 4.1-2ubuntu3 (using .../bash_4.1-2ubuntu3_i386.deb) ...
dpkg (subprocess): unable to execute old pre-removal script: No such file or directory
dpkg: warning: old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg (subprocess): unable to execute new pre-removal script: No such file or directory
dpkg: error processing /var/cache/apt/archives/bash_4.1-2ubuntu3_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: No such file or directory
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/bash_4.1-2ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It still works so I guess I'll just have to live with it. Or just reinstall ubuntu :/

Thanks for your help dude.

---

### Post by WorMzy on 2010-08-24
That is not a very happy system. I'm even not sure why it's complaining about bash when you're trying to install zsh.

I've looked about for similar problems to this, and a common cause is a missing sh to bash link in /bin.

So could you run

```
ls -l /bin/sh
```

If that returns "No such file or directory", then that's what's causing the apt-get error. I don't think it'd be causing the missing prompt, but we'll see.

So, if that file's missing, recreate it with
```
sudo ln -s /bin/bash /bin/sh
```

---

### Post by jeddycakes on 2010-08-24
Entered code, with this returned :

```

$ ls -l /bin/sh
lrwxrwxrwx 1 root root 4 2010-08-12 09:26 /bin/sh -> dash

```

ARgh!!!!!:lolflag:

---

### Post by WorMzy on 2010-08-24
Ok, so that idea fell flat. Boo.

It's pointing at dash, but I checked my Lucid's /bin/sh and it's point at dash too, so I guess that's correct.


What does
```
ls -l /bin/bash
```
return?

---

### Post by jeddycakes on 2010-08-24
Hmmm it returns :

```

$ ls -l /bin/bash
ls: cannot access /bin/bash: No such file or directory

```

What you were expecting?

---

### Post by WorMzy on 2010-08-24
Aha! Problem found.

What I was expecting, or rather, what it should have said is
```
-rwxr-xr-x 1 root root 605848 May 17 01:38 /bin/bash
```

So, it seems that you're missing bash, which is why you're not getting a prompt at terminals (I'd also expect it to not work at all, but I guess there's failsafes built into gnome-terminal to prevent that)

I'm not sure how you should go about restoring it; you could boot a Live CD and copy it's /bin/bash over to your Ubuntu partition, that might work. Use ```
gksu nautilus
``` to copy the file over easily.

Or you could download the .deb file from [here]("http://packages.ubuntu.com/lucid/bash") and try to reinstall it manually by double-clicking it (although I expect that'll give you the same error as apt-get).

Or you could create a symlink from /bin/dash and hope that apt-get will be content with that.
```
ln -s /bin/dash /bin/bash
```

It's up to you. I'm confident that this missing file is what's causing both problems, so fixing this should be all you need to do. (Of course, you can still switch shells later on if you want. :P)

---

### Post by QLee on 2010-08-24
[Quote=]Errors were encountered while processing:
 /var/cache/apt/archives/bash_4.1-2ubuntu3_i386.deb[/Quote]

This is important. Maybe there is something wrong with the package or maybe it's not the correct version. If it was my system I think I might get rid of that package and let my system download a new package file and then I would again try to install BASH or maybe I would purge then reinstall BASH and/or ZSH. That package is what is holding up the package management system.

---

### Post by jeddycakes on 2010-08-24
Whoop! 

Reinstalling from .deb worked a treat. Thank eff for that!

Thanks for all the help, seriously. Goddamn, this community rocks :)

---

### Post by jeddycakes on 2010-08-24
Just to note : Establishing a symlink to dash was a no-go; I was told I had insufficient permissions, even when I attempted the command with a sudo prefix.

Arbitrary, really, but just a heads up to people who don't wish to fix via .deb.

WorMzy is the man :)

---

### Post by WorMzy on 2010-08-24
Hurray! It took a little longer to find the problem then I'd have liked, but we got there in the end.

Remember to replace your .bashrc config file with your original one, if you haven't already. Since the problem was elsewhere, the differences in our configs are probably meant to be there.

Enjoy your prompt. :D

---

### Post by jeddycakes on 2010-08-25
> **WorMzy said:**
> Hurray! It took a little longer to find the problem then I'd have liked, but we got there in the end.

Remember to replace your .bashrc config file with your original one, if you haven't already. Since the problem was elsewhere, the differences in our configs are probably meant to be there.

Enjoy your prompt. :D

Replaced! TY

---

