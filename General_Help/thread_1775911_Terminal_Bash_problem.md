---
title: "Terminal Bash problem"
date: 2011-06-05
forum: General Help
---

### Post by Wano1997 on 2011-06-05
I got a problem with terminal, since i'm really a noob with terminal i don't know how to fix it.
Everytime i type in a command it shows for example:

-bash: ls: command not found

Even the basic commands don't work... just cd <directory> and those things works

---

### Post by JKyleOKC on 2011-06-05
Try "echo $PATH" as a command. It should show something like this:```
jk@mehitabel:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
jk@mehitabel:~$ 

```If it just gives a blank line, your problem is that for some reason the command search path is missing. If it gives you such a list but the "/usr/bin" substring isn't there, that can be fixed by editing. However the technique is a bit detailed so let's wait to see the real cause of the problem.

Can you post the content of your ".bashrc" file here? It's where the path gets set when you log in, and would be the place to make the fix.

---

### Post by Wano1997 on 2011-06-05
[IMG]http://img821.imageshack.us/img821/4985/schermafbeelding2011060q.png[/IMG]
I didn't know what you ment exactly so i just made a screenshot

---

### Post by Telengard C64 on 2011-06-05
As JKyleOKC suggested, looks like your PATH is borked. The reason **cd** works is because it is a Bash builtin, but any external commands must be found within the directories listed in PATH.

The **.bashrc** is a plain text file located in your home directory (**/home/you/.bashrc**). You can open it with any plain text editor (like **gedit** I suppose). Copy and paste the contents of **.bashrc**  into a code block in your next reply

---

### Post by nothingspecial on 2011-06-05
also post the output of ```
cat /etc/environment
```

---

### Post by Wano1997 on 2011-06-05
> **Telengard C64 said:**
> As JKyleOKC suggested, looks like your PATH is borked. The reason **cd** works is because it is a Bash builtin, but any external commands must be found within the directories listed in PATH.

The **.bashrc** is a plain text file located in your home directory (**/home/you/.bashrc**). You can open it with any plain text editor (like **gedit** I suppose). Copy and paste the contents of **.bashrc**  into a code block in your next reply
No file called .bashrc on my PC, i searched with spotlight and i did go to /home/me

---

### Post by Wano1997 on 2011-06-05
> **nothingspecial said:**
> also post the output of ```
cat /etc/environment
```
No output
Sorry double-post

---

### Post by nothingspecial on 2011-06-05
Check for sure by typing ```
ls -l ~ | grep .bashrc
```


If you have no .bashrc (nothing comes up after running previous command), you need to do this
```

cp /etc/skel/.bashrc ~/ && . ~/.bashrc
```

However, unlike most linux distros, Ubuntu's $PATH  is set in /etc/environment so you still need to post what that says.

---

### Post by Wano1997 on 2011-06-05
> **nothingspecial said:**
> Check for sure by typing ```
ls -l ~ | grep .bashrc
```If you have no .bashrc (nothing comes up after running previous command), you need to do this
```

cp /etc/skel/.bashrc ~/ && . ~/.bashrc
```However, unlike most linux distros, Ubuntu's $PATH  is set in /etc/environment so you still need to post what that says.
-bash: cp: command not found

-bash: /etc/environment: No such file or directory

Thats the output ;)
If someone has time, and wants... maybe team-viewer ?

---

### Post by nothingspecial on 2011-06-05
Of course. (to the output, not team veiwer), if we can fix this on the forum, everyone benefits 

You are going to have to fix this from a live cd, do you have one?

Have you been doing any terminal shenanigans previous to this situation?

---

### Post by Wano1997 on 2011-06-05
> **nothingspecial said:**
> Of course. (to the output, not team veiwer), if we can fix this on the forum, everyone benefits 

You are going to have to fix this from a live cd, do you have one?

Have you been doing any terminal shenanigans previous to this situation?
I didn't xD although as i said: I'm noob to all this :/

---

### Post by Wim Sturkenboom on 2011-06-05
// EDIT I haven't figured out where the original path is set so thsi is not going to help you for now :(

```

fortyfourgalena@desktop-01:~$ which vi
/usr/bin/vi
fortyfourgalena@desktop-01:~$ which nano
/usr/bin/nano

```
Use the full path to vi or nano to edit .profile and .bashrc.

**.profile**
```

# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
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

**.bashrc**
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

The above files are taken from 10.04 desktop. I guess you're running the server edition; not sure if they differ for the server.

---

### Post by nothingspecial on 2011-06-05
maybe you can fix this using the absolute path

```
/bin/cp /etc/skel/.bashrc ~/ && . ~/.bashrc
```
```

/usr/bin/sudo /bin/echo 'PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"' > /etc/environment 
```

Semms like your system is pretty messed up though.

---

### Post by Telengard C64 on 2011-06-05
@nothingspecial, his PATH is borked, so he'll need to use absolute paths for those commands.

OP, please try like this:

```
/bin/ls -al ~ | /bin/grep .bashrc
```

**_Edit_**
I see nothingspecial already addressed this. Feel free to ignore this post  :P

---

### Post by nothingspecial on 2011-06-05
> **Telengard C64 said:**
> @nothingspecial, his PATH is borked, so he'll need to use absolute paths for those commands.

OP, please try like this:

```
/bin/ls -al ~ | /bin/grep .bashrc
```

See above post :P (but cheers)

---

### Post by JKyleOKC on 2011-06-05
How did you install mysql?

The screenshot you posted looks as if the installation of mysql is what destroyed your path setting.

You may be able to make the repair from the desktop without using terminal. First, though, go to "Places" on the desktop and navigate to the "etc" directory within "File System" to look for "environment" and if it's there, open it up and post us a screenshot of its content. It should be a single line that begins "PATH=" followed by a list.

The other problems may all result from absence of the "PATH" setting, since many of the system programs call other system programs to do part of their work and without a valid PATH setting cannot do their job.

---

### Post by Wano1997 on 2011-06-05
I don't know if any of this is possible, but i was messing with MySQL when i tryed to make a WoW (World of Warcraft) online private server. And i also deleted a few maps called opt, bin etc...
My dad was on my PC trying to fix it, ... but now some secs ago i've still been trying and now i can use some commands like 'which', when i type that is says: usage: which [-as] program ...

---

### Post by nothingspecial on 2011-06-05
> **Wano1997 said:**
>  And i also deleted a few maps called opt, bin etc...

:shock:

I think you may have deleted /bin, in which case your installation is toast.

If so, backup your important data with a live cd and reinstall.

Do you have the /bin directory?

---

### Post by Wano1997 on 2011-06-05
> **nothingspecial said:**
> :shock:

I think you may have deleted /bin, in which case your installation is toast.

If so, backup your important data with a live cd and reinstall.

Do you have the /bin directory?
Yes i'm in the bin directory right now with terminal

---

### Post by JKyleOKC on 2011-06-05
> **Wano1997 said:**
> And i also deleted a few maps called opt, bin etc...I suspect that this is what happened. It may be time to bite the bullet and re-install your system from scratch. You can boot with a Live CD and copy off any data that you want to keep, but if you got rid of "bin" and "etc" then you pretty well gutted the system and it's amazing that it still works at all...

---

### Post by Wano1997 on 2011-06-05
> **JKyleOKC said:**
> I suspect that this is what happened. It may be time to bite the bullet and re-install your system from scratch. You can boot with a Live CD and copy off any data that you want to keep, but if you got rid of "bin" and "etc" then you pretty well gutted the system and it's amazing that it still works at all...
I got a few maps called 'bin' so i'm not sure if those which i deleted are the ones of ... unix i guess or whatever this is ?

---

### Post by nothingspecial on 2011-06-05
> **Wano1997 said:**
> Yes i'm in the bin directory right now with terminal

/bin

/usr/bin

~/bin

which bin are you in (that sounds silly if you say it out loud)

---

### Post by Wano1997 on 2011-06-05
> **nothingspecial said:**
> /bin

/usr/bin

~/bin

which bin are you in (that sounds silly if you say it out loud)
First i did this :

cd ..
then cd bin

thats all
and yes indeed it does sound silly xD

---

### Post by nothingspecial on 2011-06-05
Well, we need to know if you have /bin, which sounds unlikely, but since ls doesn't work, it's difficult to determine.

is there anything in bin

---

### Post by Wano1997 on 2011-06-05
> **nothingspecial said:**
> Well, we need to know if you have /bin, which sounds unlikely, but since ls doesn't work, it's difficult to determine.

is there anything in bin
You can see that by typing ls -l , right ?

---

### Post by nothingspecial on 2011-06-05
> **Wano1997 said:**
> You can see that by typing ls -l , right ?

Not if ls doesn't work, but give it a go

---

### Post by Wano1997 on 2011-06-05
> **nothingspecial said:**
> Not if ls doesn't work, but give it a go
It works :/ it shows A LOT

---

### Post by nothingspecial on 2011-06-05
good, it's still there.....

did ou try

[http://ubuntuforums.org/showpost.php?p=10905247&postcount=13](http://ubuntuforums.org/showpost.php?p=10905247&postcount=13)

---

### Post by Wano1997 on 2011-06-05
> **nothingspecial said:**
> good, it's still there.....

did ou try

[http://ubuntuforums.org/showpost.php?p=10905247&postcount=13](http://ubuntuforums.org/showpost.php?p=10905247&postcount=13)
I didn't know what to do there :/

---

### Post by nothingspecial on 2011-06-05
copy and paste it into your terminal, or failing that type it, making sure you get it exactly right (hint - linux is case sensitive)

---

### Post by Wano1997 on 2011-06-05
> **nothingspecial said:**
> copy and paste it into your terminal, or failing that type it, making sure you get it exactly right (hint - linux is case sensitive)
for this it said permission denied, for the other one it said no such directory 
/usr/bin/sudo /bin/echo 'PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"' > /etc/environment

---

### Post by nothingspecial on 2011-06-05
I go to go for a while.

Something here is not right.

Hopefully someone will step in, if not, see you later

---

### Post by AlphaLexman on 2011-06-05
@ Wano1997:

As a 'noob', do you know how to use '**code**' tags? It will help us help you if you can use them please.

Do **NOT** use the 'Quick Reply', instead click 'NewReply', then click the icon on the toolbar that looks like a number sign '**#**'.

You should copy terminal commands in between the [C-O-D-E] and [/C-O-D-E] (without the dashes between the letters).

Go ahead and give it a try.

---

### Post by Telengard C64 on 2011-06-05
> **JKyleOKC said:**
> You can boot with a Live CD and copy off any data that you want to keep, but if you got rid of "bin" and "etc" then you pretty well gutted the system and it's amazing that it still works at all...

This is yet to be determined, but yeah, removing that much of the OS would be quite difficult to fix without a reinstall.

From what I've read, all I know for sure is that his PATH is borked. That is fixable.

OP, before you go for a reinstall, please remember to backup all important data to at least two external media.

It would be good to know if the absolute path commands posted earlier worked. Still waiting for that info. For example, this should work:

```
/bin/ls -al ~/.bashrc
```

If that fails, then we need to see the exact error message.

And yes, as mentioned by AlphaLexman, please remember to enclose your terminal output in a code block when you paste it into your reply. Wikipedia has a nice [BBCode quick reference](http://en.wikipedia.org/wiki/Bbcode) to help if you don't know what a code block looks like.

---

