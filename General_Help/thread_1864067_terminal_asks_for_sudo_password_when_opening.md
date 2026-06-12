---
title: "terminal asks for sudo password when opening"
date: 2011-10-18
forum: General Help
---

### Post by riseringseeker on 2011-10-18
In the last few days whenever I open the terminal, it immediately asks for my password. IOW, opening a terminal, instead of seeing
```

<user>@<computername>:~$
```

I see

```
[sudo] password for <user>:
```

This is the first thing I see when opening a terminal window.  I have not (intentionally at least) made any changes to the terminal of late (I do have some aliases, but those were put in long ago.)

When I do enter my sudo password it takes me to a user terminal rather than a root terminal.

It's an annoyance, and one that might well go away when I get around to doing an upgrade to 11.10, but if anyone can point me in the right direction, would appreciate it.

This only seems to have changed on my user account, my wife's desktop does not show this behavior.

---

### Post by matt_symes on 2011-10-18
Hi

Is it something in your configuration files ? Please post the output of ~/.bashrc and other config files. That may give some clues.

Kind regards

---

### Post by riseringseeker on 2011-10-18
> **matt_symes said:**
> Hi

Is it something in your configuration files ? Please post the output of ~/.bashrc and other config files. That may give some clues.

Kind regards

Here's my .bashrc file, with an alias modified to prevent unauthorized log-ins from afar:

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
alias vi='vim'
alias cd..='cd ..'
alias rm='rm -i'
alias md='mkdir'
alias la='ls -a'
alias ll='ls -l'
alias ln='ls -ln'
alias !='sudo'
alias add='sudo apt-get install'
alias update='sudo apt-get update'
alias home='ssh -YC 192.168.2.2'
alias <severnamealias>='ssh -YC <servername>'


# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi
```

---

### Post by matt_symes on 2011-10-18
Hi

> When I do enter my sudo password it takes me to a user terminal rather than a root terminal.I have generally seen this when there is a command requiring sudo in one of the startup config files. 

I could not see much wrong with your ~/.bashrc file though.

Can you post your  /etc/bash.bashrc file.

Kind regards

---

### Post by riseringseeker on 2011-10-18
> **matt_symes said:**
> Hi

I have generally seen this when there is a command requiring sudo in one of the startup config files. 

I could not see much wrong with your ~/.bashrc file though.

Can you post your  /etc/bash.bashrc file.

Kind regards

Thanks for the quick reply.

Correct me if I'm wrong, but the file you want me to post is global in nature, isn't it?  IOW, it would effect all users.  Since this is only happening in my account, and not the wife's can't see how it would be relevant, or is it?

You say you can't see ***much*** wrong, do you see anything that is?

---

### Post by mcduck on 2011-10-18
What about ~/.profile? And of course any other bash-related config file you might have in your home directory....

And also, does this happen when opening any terminal (including the TTY's) or just with Gnome-terminal? (if it's just with Gnome-terminal you should check your terminal profile)

---

### Post by matt_symes on 2011-10-18
Hi

> **riseringseeker said:**
> Thanks for the quick reply.

Correct me if I'm wrong, but the file you want me to post is global in nature, isn't it?  IOW, it would effect all users.  Since this is only happening in my account, and not the wife's can't see how it would be relevant, or is it?

You say you can't see ***much*** wrong, do you see anything that is?

 /etc/bash.bashrc is global yes. It's a system interactive bash session login file. I have learnt always to double check everything though when it comes to computers.

I could see nothing wrong with your .bashrc file. As mcduck stated, it would be good to see all your bash files just to eliminate them.

After all there is a problem somewhere on your system.

Kind regards

---

### Post by riseringseeker on 2011-10-19
> **mcduck said:**
> What about ~/.profile? And of course any other bash-related config file you might have in your home directory....

And also, does this happen when opening any terminal (including the TTY's) or just with Gnome-terminal? (if it's just with Gnome-terminal you should check your terminal profile)

TTY works normally, as does running an executable script in a terminal.

~/.profile:

```

# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022
umask 002

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

/etc/bash.bashrc:

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

/etc/profile:

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

### Post by mcduck on 2011-10-19
> **riseringseeker said:**
> TTY works normally, as does running an executable script in a terminal.


In that case the problem is specific to Gnome-terminal, which means the most likely reason would be something set in the terminal's profile preferences.

Open a terminal, and go to Edit->Profile Preferences (or right-click on the terminal window and select Profiles->Profile Preferences). Then on the "Title and Command"-tab make sure that "Run command as a login shell" and "Run a custom command instead of my shell" are both disabled.

If even that fails to solve the problem, the run "*cat /usr/share/applications/gnome-terminal.desktop*" and make sure the "Exec"-fields are set to "gnome-terminal" and nothing else.

---

### Post by riseringseeker on 2011-10-19
> **mcduck said:**
> In that case the problem is specific to Gnome-terminal, which means the most likely reason would be something set in the terminal's profile preferences.

Open a terminal, and go to Edit->Profile Preferences (or right-click on the terminal window and select Profiles->Profile Preferences). Then on the "Title and Command"-tab make sure that "Run command as a login shell" and "Run a custom command instead of my shell" are both disabled.

I had already looked at that, but looked again (can't hurt, right?) and both are indeed unchecked.

> If even that fails to solve the problem, the run "*cat /usr/share/applications/gnome-terminal.desktop*" and make sure the "Exec"-fields are set to "gnome-terminal" and nothing else.

Only two entries with "exec" in them, and both =gnome-terminal, here's the result of the above command:

```
[Desktop Entry]
Name=Terminal
Comment=Use the command line
TryExec=gnome-terminal
Exec=gnome-terminal
Icon=utilities-terminal
Type=Application
X-GNOME-DocPath=gnome-terminal/index.html
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-terminal
X-GNOME-Bugzilla-Component=BugBuddyBugs
X-GNOME-Bugzilla-Version=2.32.0
Categories=GNOME;GTK;Utility;TerminalEmulator;
StartupNotify=true
OnlyShowIn=GNOME;
X-Ubuntu-Gettext-Domain=gnome-terminal

```

Just to double check, tried tty terminals again.  First time I tried it, only tried tty1, and it worked as I expected it to.  This time, trying each in turn, starting with tty6 and working down, they now all exhibit the errant behavior, including tty1!

---

### Post by matt_symes on 2011-10-19
Hi

Open a terminal and enter you password as you are currently having to.

Then type

```
bash
```to create a new shell. Do you have to enter your sudo password again ?

Type ```
exit
``` to exit the shell. Then type

```
bash --noprofile 
```Do you have to enter your password ?

type ```
exit
``` to exit the shell. Then type

```
bash --norc
```Do you have to enter your password?

type ```
exit
``` to exit the shell.

Just to make sure there is nothing going on with gnome terminal run these commands and post the output back.

```

gconftool-2 -g /apps/gnome-terminal/global/default_profile

What ever this one returns use in place of Default below.

gconftool-2 -g /apps/gnome-terminal/profiles/Default/use_custom_command
gconftool-2 -g /apps/gnome-terminal/profiles/Default/login_shell
gconftool-2 -g /apps/gnome-terminal/profiles/Default/custom_command
```

Kind regards

---

### Post by riseringseeker on 2011-10-20
> **matt_symes said:**
> Hi

Open a terminal and enter you password as you are currently having to.

Actually, I can also hit ^C three times and it drops asking me for the sudo password, but will do as you ask.

> 
Then type

```
bash
```to create a new shell. Do you have to enter your sudo password again ?

No, I do not.  In fact, if I type exit again, and close the terminal, it does not require me to enter the sudo password when I open new copy, even if I kill bash from system monitor.  This seems to stay this way until/unless I reboot.  If I open a ***second*** copy however, it asked for the sudo password again.

If I close all terminal windows, then start any number of them up again it doesn't ask.  This is **so** weird! (I found this out after trying all you asked.)

> Type ```
exit
``` to exit the shell.  Then type

```
bash --noprofile 
```Do you have to enter your password ?

Nope, not in a terminal that did not ask for the sudo password, or a second copy that did.

> 
type ```
exit
``` to exit the shell. Then type

```
bash --norc
```Do you have to enter your password?

type ```
exit
``` to exit the shell.

Again no, in either instance.

> Just to make sure there is nothing going on with gnome terminal run these commands and post the output back.

```

gconftool-2 -g /apps/gnome-terminal/global/default_profile
```

Default

> ```
What ever this one returns use in place of Default below.

gconftool-2 -g /apps/gnome-terminal/profiles/Default/use_custom_command
```

Not quite sure what you mean here, as it does return "Default", but the above command returns "false", as does the command below.  This again works in either instance of the terminal, whether or not it asked for a sudo password when opening or not.

> ```
gconftool-2 -g /apps/gnome-terminal/profiles/Default/login_shell
```

```
gconftool-2 -g /apps/gnome-terminal/profiles/Default/custom_command
```

The last one returns a blank line.

> Kind regards

Thanks for your patience as this is tracked down.

---

### Post by matt_symes on 2011-10-20
Hi

> No, I do not.  In fact, if I type exit again, and close the terminal, it  does not require me to enter the sudo password when I open new copy,  even if I kill bash from system monitor.  This seems to stay this way  until/unless I reboot.  If I open a ***second*** copy however, it asked for the sudo password again.

If I close all terminal windows, then start any number of them up again it doesn't ask.  This is **so** weird! (I found this out after trying all you asked.) > This is **so** weird!It is rather odd !!! Although i would not totally rule it out, i think we can start to think about eliminating the configuration files and gnome terminal profiles.

Typing bash in the terminal will create a new instance of a shell and bash --norc will not use .*rc files and bash --noprofile will not use any .*profile files. gconftool-2 results suggest that there is no bug in gnome-terminal profiles.

I will have a think during lunch. 

Anybody else with some ideas are welcome to add them.

Kind regards

---

### Post by riseringseeker on 2011-10-20
> **matt_symes said:**
> Hi

 It is rather odd !!! Although i would not totally rule it out, i think we can start to think about eliminating the configuration files and gnome terminal profiles.

Typing bash in the terminal will create a new instance of a shell and bash --norc will not use .*rc files and bash --noprofile will not use any .*profile files. gconftool-2 results suggest that there is no bug in gnome-terminal profiles.

OK, let me ask you a question here.  Should typing "bash" in an open terminal just start a new instance in the ***same*** window, or should a ***new*** window appear?  

When I type bash into an existing terminal, it ***was*** just returning the prompt, now when I do it, it does indeed ask for a sudo password curiouser and curiouser...

Let me try the commands you gave again now that it's exhibiting different behavior.

---

### Post by riseringseeker on 2011-10-20
OK, it's no showing new behavior.  All the commands you gave earlier do the same thing except for 

```
bash --norc
```

Now, that returns:

```
bash-4.1$
```

as the prompt instead of <user>@<computername>:~$, and stays that way until I exit that window.

---

### Post by riseringseeker on 2011-10-20
OK, it's no showing new behavior.  All the commands you gave earlier do the same thing except for 

```
bash --norc
```

Now, that returns:

```
bash-4.1$
```

as the prompt instead of <user>@<computername>:~$, and stays that way until I type exit, whereupon it returns to the normal prompt.

---

### Post by matt_symes on 2011-10-20
Hi

That behaviour looks correct for those commands you typed. Bash --norc output looks good.

They should not start a new gnome-terminal window but create new shells in the existing window. You can test this by opening a new gnome-terminal and typing

```
ps aux | grep -c bash
```then type

```
bash
```and again type

```
ps aux | grep -c bash
```You'll see the count increase.

Typing exit and ps aux | grep -c bash again will lower the count once more.

I'm still thinking about what your problem may be but it's late here so i'll post tomorrow.

**EDIT: **I have just noticed this.

> When I type bash into an existing terminal, it ***was*** just returning the prompt, now when I do it, it does indeed ask for a sudo password curiouser and curiouser...

Try to play around with using bash, bash --noprofile and bash --norc. This is really odd as there seems to be no pattern here and that makes it very difficult to diagnose. Try to find a consistent pattern. Make sure your testing is consistent (for each test make sure you type in the same things). Post back your results.

Kind regards

---

### Post by riseringseeker on 2011-11-01
> **matt_symes said:**
> Hi

That behaviour looks correct for those commands you typed. Bash --norc output looks good.

They should not start a new gnome-terminal window but create new shells in the existing window. You can test this by opening a new gnome-terminal and typing

```
ps aux | grep -c bash
```then type

```
bash
```and again type

```
ps aux | grep -c bash
```You'll see the count increase.

Typing exit and ps aux | grep -c bash again will lower the count once more.

I'm still thinking about what your problem may be but it's late here so i'll post tomorrow.

**EDIT: **I have just noticed this.



Try to play around with using bash, bash --noprofile and bash --norc. This is really odd as there seems to be no pattern here and that makes it very difficult to diagnose. Try to find a consistent pattern. Make sure your testing is consistent (for each test make sure you type in the same things). Post back your results.

Kind regards

The terminal now *almost* always asks for the sudo password regardless of how I open one with a single exception.  I have a few bash scripts that I often run.  When I double click on these, and instruct it to 'run in terminal', it runs normally without asking for the sudo password.

I also have some bash aliases that I frequently use in a terminal.  One of these aliases is:
```
alias update='sudo apt-get update'
```

Before this errant behavior showed up it would ask me for the sudo password before running.  Now when I type 'update' in the terminal, it runs without a password (if I have not by-passed the request for the sudo password by hitting CTRL-C twice).  It will not run 
```
apt-get update
``` 
asking me if I am root, but it will run 
```
sudo apt-get update
```
without asking for the password.

After I began answering this post, I once again tried opening a terminal normally (Applications->Accessories->Terminal) and it would open without asking for a sudo password - no idea why it changed.

If I then, in the terminal that opened normally, type 
```
gnome-terminal
```
it again asks for the sudo password.  

Closing then opening the terminal again I try 'File->Open Terminal', or "File->Open Tab' the first time I do either one I again get my normal user prompt, however, if I try it a second time, whether or not I have closed the new instance, I return to it asking for the sudo password.

I've had some weird behavior over my years of using Ubuntu, but this has to be the weirdest, and one I simply cannot figure out.

---

### Post by nothingspecial on 2011-11-01
> alias !='sudo'

That line in your .bashrc is the problem.

Either put a # infront of it or remove it.

---

### Post by riseringseeker on 2011-11-01
> **nothingspecial said:**
> That line in your .bashrc is the problem.

Either put a # infront of it or remove it.

I'll try that to see if it has any effect, but it's been working flawlessly for literally years.  Don't understand why it would suddenly become a problem when it's been working with this release, as well as at least the previous three releases since I put it in.

---

### Post by riseringseeker on 2011-11-01
It *seems* to have worked, but will hold off on marking this solved for a few days at least as the terminal behavior has been anything but consistent.  (It started as an occassional thing, then became more and more prevelant, but *sometimes* would revert to normal behavior)

It also begs the question since I have had that alias in .bashrc since at least 8.04 and it had not caused any problems before, why did it start now?

---

### Post by matt_symes on 2011-11-01
Hi

> **riseringseeker said:**
> It *seems* to have worked, but will hold off on marking this solved for a few days at least as the terminal behavior has been anything but consistent.  (It started as an occassional thing, then became more and more prevelant, but *sometimes* would revert to normal behavior)

It also begs the question since I have had that alias in .bashrc since at least 8.04 and it had not caused any problems before, why did it start now?

That may have been a great call by nothingspecial. I hope so as this has been bugging me for a week :D

I also put that alias in my .bashrc on Ubuntu and Arch installs and have not noticed the problems you have described.

Any ideas why this behaviour appeared on your machine would be most welcome.

Kind regards

---

