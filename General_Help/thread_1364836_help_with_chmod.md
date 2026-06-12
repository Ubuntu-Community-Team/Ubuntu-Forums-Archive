---
title: "help with chmod"
date: 2009-12-26
forum: General Help
---

### Post by spiky001 on 2009-12-26
Hi I have a bash script i need to run, I have placed it in usr/local/bin  how do i get it to execute from terminal, i have read i need to change permission 1st would like to know how, Do i have to cd to directory then chmod x filename . If not some help plz

---

### Post by falconindy on 2009-12-26
You can always specify the full path rather than changing to the file's directory first.

sudo chmod +x /usr/local/bin/filename
  is the same as
cd /usr/local/bin; sudo chmod +x filename

If you're writing your own scripts, I suggest you maintain a bin directory in your home rather than using /usr/local.

---

### Post by spiky001 on 2009-12-26
thks for your advice, i need the script to run with the least amout of typing so i would like to just type sudo filename   then script runs, am i right in thinking it should be in /bin folder  once i have changed permissions or can i point the command to look in another folder without typing in the path? hope that made sense

---

### Post by falconindy on 2009-12-26
Type 'echo $PATH'. This will give you a list of locations separated by a colon (:). An executable in any of these directories will not need the full path to be specified in order to be run. The difference between the locations is purely semantic.

Typically, user written scripts that don't need to be system wide are kept in that user's ~/bin folder. Executables that are associated with user-compiled software (that is, not maintained by the package manager) should end up in /usr/local/bin.

So, depending on what the script is, you should put it in a place that would be apropos to its source/use.

---

### Post by spiky001 on 2009-12-26
ok the script is for turning eth0 off then back on again thats all, so do i have it in the correct folder

---

### Post by Barriehie on 2009-12-26
> **spiky001 said:**
> ok the script is for turning eth0 off then back on again thats all, so do i have it in the correct folder

I'ld go with ~/bin

Barrie

---

### Post by falconindy on 2009-12-26
> **barriehie said:**
> i'ld go with ~/bin

barrie

+1

---

### Post by spiky001 on 2009-12-26
Thks for your help hope all gose well wil let u know :)

---

### Post by bhuvi on 2009-12-26
do not place user created scripts in system directories such as /usr/bin/

create a bin folder in your home directory and place your scripts there and make it executable.then you dont have to type the path name you can use just the script name.This is because ~/bin directory is also an executable path if it exists.

---

### Post by spiky001 on 2009-12-26
hi i,m having problems getting my script to run from terminal, I have made a folder in home directory called bin hopefully made it executable with chmod 777 then put script in folder, it wont execute with command (sudo filename) in terminal. Any ideas where i hav gone wrong plz

---

### Post by spiky001 on 2009-12-26
any1 any ideas plz

---

### Post by spiky001 on 2009-12-26
hi again I have done echo $PATH and found my folder (home/bin) not in there is this why it wont execute?

---

### Post by Barriehie on 2009-12-26
> **spiky001 said:**
> hi again I have done echo $PATH and found my folder (home/bin) not in there is this why it wont execute?

Probably, definitely if you're getting a command not found error!  Try logging out and then back in.  Did you make the permissions on the folder or the file???  To make them on the file you can use chmod +x *filename*.  If logging out and then back in doesn't work you can add to the $PATH variable in your ~/.bashrc file.
```

export PATH=$PATH:/home/*user*/bin
```

HTH,
Barrie

Edit: My folder permissions for ~/bin are 755

Permissions are granted via owner-group-others with the bit order being read, write, execucte.  So 755 would be 111 101 101 = 421 401 401 = 755.

---

### Post by spiky001 on 2009-12-26
Hi Barrie yes have been at it al day this is all new to me only been off windows since sep ish so am struggerling, as u can see i was advised to make bin folder in home dir which i did have just tried all that you said but still no luck although i did change export to home/bin as i thought that would be correct as that was where the script is i did make the file executable & it works just not from command line

this is what i get from echo

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

i think i need to add home/bin to list?

---

### Post by Barriehie on 2009-12-26
> **spiky001 said:**
> Hi Barrie yes have been at it al day this is all new to me only been off windows since sep ish so am struggerling, as u can see i was advised to make bin folder in home dir which i did have just tried all that you said but still no luck although i did change export to home/bin as i thought that would be correct as that was where the script is i did make the file executable & it works just not from command line

this is what i get from echo

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

i think i need to add home/bin to list?

It can't hurt!  From the terminal you can do this:```
gedit ./.bashrc
``` and it will run gedit, editor, and load your .bashrc file.  Add to your PATH as indicated prior and then save the file, CTRL-s, close the file, CTRL-w, and quit, CTRL-q.  This will pop you back into the terminal and then enter:```
source ./.bashrc
``` This SHOULD amend your path information.

Barrie

Edit: Note where it says user to use YOUR login name!!!

---

### Post by spiky001 on 2009-12-26
not sure about this cant see any of the results from the echo in there so not sure where to edit ( add what i need )  or should i just add it at end just b4 (fi) ?

---

### Post by Barriehie on 2009-12-26
> **spiky001 said:**
> not sure about this cant see any of the results from the echo in there so not sure where to edit ( add what i need )  or should i just add it at end just b4 (fi) ?

You can just add it to the last line of the file or the first, I don't think it matters!  Here's some of my .bashrc

```

#
#   Set the prompt(s)
#   Bright green /path/ >
#
export PS1='\033[1;32m\T $PWD \$ \033[1;36m>>\033[1;37m '

case $TERM in
dumb)                             # Keeps emacs shell 'normal'
export PS1='\u@\h \W\$ '
esac

#
#    HISTSIZE=1000 lines
#
HISTSIZE=1000
HISTFILESIZE=1000

#
#   Set my default editor to Emacs
#
#export EDITOR='emacs22-gtk'
export EDITOR='emacsclient'
export VISUAL=emacsclient
set -o emacs

#
#   Alias'
#
source $HOME/.bash_alias


#
#   Edit $PATH environment variable
#
export PATH=$PATH:/home/barrie/programming/python/:/home/barrie/programming/python/projects/:/home/barrie/programming/modules/:/home/barrie/programming/python/scraps/:/home/barrie/temp/:/home/barrie/bin/daemons/:/home/barrie:/home/barrie/bin

```

Barrie

Edit: And if you decide you like emacs for an editor I've got a pretty cool .emacs file.... :)

---

### Post by Barriehie on 2009-12-26
Let us know how this is working!

Barrie

---

### Post by spiky001 on 2009-12-26
this is my bashrc from gedit

```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# don't overwrite GNU Midnight Commander's setting of `ignorespace'.
HISTCONTROL=$HISTCONTROL${HISTCONTROL+,}ignoredups
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoreboth

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
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

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
```not looking anything like your 1 ?

---

### Post by Barriehie on 2009-12-26
> **spiky001 said:**
> this is my bashrc from gedit

```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# don't overwrite GNU Midnight Commander's setting of `ignorespace'.
HISTCONTROL=$HISTCONTROL${HISTCONTROL+,}ignoredups
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoreboth

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
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

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
```not looking anything like your 1 ?

True, I oopsed and blew mine away at some point. No big deal.  Now you can just add:
```

export PATH=$PATH:/home/***YourLoginName***/bin/
```
anywhere in the file.  As you become more adept at this OS you'll probably want to put it near the top.

Barrie

---

### Post by spiky001 on 2009-12-26
ok we are having fun here but still no joy, although now echo shows path

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/bin/

as u can i got it without the middle part you put in but did try it,

still comes up command not found, have checked folder executable, file executable, I do know that script works i can run in terminal when right click with mouse,
it must be something so simple

---

### Post by Barriehie on 2009-12-26
> **spiky001 said:**
> ok we are having fun here but still no joy, although now echo shows path

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/bin/

as u can i got it without the middle part you put in but did try it,

still comes up command not found, have checked folder executable, file executable, I do know that script works i can run in terminal when right click with mouse,
it must be something so simple

Aha! Your home dir. is /home/**your login name**/  So you must add /home/**YourLoginName**/bin to the path; i.e. /home/spiky001/bin/

/home/bin would be a home dir for a user called bin! :)

Barrie

Edit: Home dir.'s are setup like this:
/home/user1/      # Substitue user name
/home/user2/      # Substitue user name
/home/user3/      # Substitue user name
/home/user...
and so on and so forth, except for root.

---

### Post by spiky001 on 2009-12-26
the bin folder is acctually in home will this not affect it?

---

### Post by Barriehie on 2009-12-26
> **spiky001 said:**
> the bin folder is acctually in home will this not affect it?

I think you probably created that dir. in the wrong spot!  Only root will have permission in /home/bin.  Make a bin folder in YOUR home dir. i.e. /home/spiky001 or whatever you login with and put your shell script in that folder.

Barrie

---

### Post by spiky001 on 2009-12-26
ok adjusted bashrc home/spiky/bin 
have restarted system still no joy

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/spiky/bin/


i do appreciate this help

---

### Post by Barriehie on 2009-12-26
> **spiky001 said:**
> ok adjusted bashrc home/spiky/bin 
have restarted system still no joy

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/spiky/bin/


i do appreciate this help

Now put your script in /home/spiky/bin and make sure you own it. These are from the terminal: Applications > Accessories > Terminal.

```

sudo chown spiky:spiky /home/spiky/bin/**name of script**  <-- no spaces in the name!
chmod +x /home/spiky/bin/**name of script**  <-- no spaces in the name!

```

Barrie

Edit: When you make changes in .bashrc you can just type *source ./.bashrc* in a terminal, no need to restart everything!  I've got alias reload='source $HOME/.bashrc' in my alias file so I don't have to do anything except type *reload* at the prompt.

Edit-1: The terminal is your friend!

---

### Post by spiky001 on 2009-12-26
ureeka you done for get the beans u can have a coffee it now works boy have i learnt someting today thks mate

this is now solved:guitar:

---

### Post by Barriehie on 2009-12-26
> **spiky001 said:**
> ureeka you done for get the beans u can have a coffee it now works boy have i learnt someting today thks mate

this is now solved:guitar:

Cool! and your journey is just beginning!!!

Barrie

---

### Post by spiky001 on 2009-12-26
it is now i can add to the script to do more as i need it cheers

---

### Post by Barriehie on 2009-12-26
> **spiky001 said:**
> it is now i can add to the script to do more as i need it cheers

And then you'll be adding more scripts... :)

Barrie

---

### Post by spiky001 on 2009-12-26
not 2 night but maybe lol i know who to contact now

---

### Post by iMisspell on 2009-12-26
> **Barriehie said:**
> ...my alias...
Your desktop looks as bad as my _[old windows desktop did]("http://files.joescove.com/pics/misc/desktop.gif")_, bad need of a maid :)
I see an icon named, 'palmer', as in Carl Palmer ?

_

---

### Post by Barriehie on 2009-12-26
> **iMisspell said:**
> Your desktop looks as bad as my _[old windows desktop did]("http://files.joescove.com/pics/misc/desktop.gif")_, bad need of a maid :)
I see an icon named, 'palmer', as in Carl Palmer ?

_

No, don't know any Carl Palmer.  Yeah, I really need two monitors, the terminal takes up a bit of space but everything else I need handy is right there!

Barrie

---

### Post by iMisspell on 2009-12-26
> **Barriehie said:**
> No, don't know any Carl Palmer.
He's an amazing drummer from the 70's (and now).
If you like music with any sort of "rock/jazzyness" base to it, you might like his work.

_

---

### Post by Barriehie on 2009-12-26
> **iMisspell said:**
> He's an amazing drummer from the 70's (and now).
If you like music with any sort of "rock/jazzyness" base to it, you might like his work.

_

Aha, like in Brain Salad Surgery!  :)

Barrie

---

### Post by iMisspell on 2009-12-27
:popcorn:
Exactly !

For me that's the runner-up album behind Tarkus.
Those three guys have such chemistry, skills and creativity its surreal.

_

---

### Post by bhuvi on 2009-12-27
> **spiky001 said:**
> hi i,m having problems getting my script to run from terminal, I have made a folder in home directory called bin hopefully made it executable with chmod 777 then put script in folder, it wont execute with command (sudo filename) in terminal. Any ideas where i hav gone wrong plz

If you create a bin folder in your home directory it will be automatically exported as a path variable by the next time you restart your system.
As you can see from .profile file in your home directory 

> # set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
this line does it.
and you dont have to refer your bin directory as /home/<yourusername>/bin
you can simply refer to it as ~/bin
the ~ stands for /home/<yourusername>
Thus when you write bash scripts use ~ instead of /home/<yourusername> this way when distribute your script to others it can be executed without any change by them. 

you dont have to change the permissions of the directory as it is inside your home directory the default permissions of your directory will be set.

---

### Post by spiky001 on 2009-12-27
hi bhuvi have just read your post having just turned on pc  script wont run i did put it in usr/local/bin all went well there that was last night moved  it back againnot working now?

---

### Post by Barriehie on 2009-12-27
> **spiky001 said:**
> hi bhuvi have just read your post having just turned on pc  script wont run i did put it in usr/local/bin all went well there that was last night moved  it back againnot working now?

So exactly where is the script now? Please give a full path! :)

Barrie

---

### Post by spiky001 on 2009-12-28
Hi Barrihe I was out yesterday have just seen postthe route is

> spiky@dell-linux:~$ ls
Awake.iso  Desktop    Downloads         Music     Public     Ubuntu One
bin        Documents  examples.desktop  Pictures  Templates  Videos
spiky@dell-linux:~$ cd bin
spiky@dell-linux:~/bin$ ls
_**ifstart**_
spiky@dell-linux:~/bin$ 


ifstart being the file i need

---

### Post by Barriehie on 2009-12-28
> **spiky001 said:**
> Hi Barrihe I was out yesterday have just seen postthe route is



ifstart being the file i need

Okay, could you post the actual file ifstart and also the results of ls -l ifstart please?

Barrie

---

### Post by spiky001 on 2009-12-28
> spiky@dell-linux:~$ ls -I ifstart
Awake.iso  Desktop    Downloads         Music     Public     Ubuntu One
bin        Documents  examples.desktop  Pictures  Templates  Videos
spiky@dell-linux:~$ 
```
#!/bin/bash
sudo ifconfig eth0 down
sleep 5
sudo ifconfig eth0 up
```the code works just not from the location, as i said if it in usr/local/bin all is fine, I just thought get it right from the start for future sorry to be a pain

---

### Post by Barriehie on 2009-12-28
> **spiky001 said:**
> ```
#!/bin/bash
sudo ifconfig eth0 down
sleep 5
sudo ifconfig eth0 up
```the code works just not from the location, as i said if it in usr/local/bin all is fine, I just thought get it right from the start for future sorry to be a pain

Sounds like a permission thing!  From the terminal do this:
```

sudo chown spiky:spiky ~/bin/ifstart

```

You can take out the 'sudo' in each line and run it like 'sudo ifstart'

Barrie

PS:, not being a pain! :)

---

### Post by spiky001 on 2009-12-28
> [sudo] password for spiky: 
spiky@dell-linux:~$ sudo ifstart
sudo: ifstart: command not found
spiky@dell-linux:~$ 


still not right

---

### Post by Barriehie on 2009-12-28
WTH!  Okay, post the output of ```
ls -l ~/bin
```

Barrie

Edit: and while your at it post this too please!
```

find /home/spiky -iname ifstart -print
```

---

### Post by spiky001 on 2009-12-28
> spiky@dell-linux:~$ ls -l ~/bin
total 8
-rwxr-xr-x 1 spiky spiky 56 2009-12-28 08:37 ifstart
-rw-r--r-- 1 spiky spiky 66 2009-12-26 17:43 ifstart~
spiky@dell-linux:~$ 


this what i got

---

### Post by Barriehie on 2009-12-28
Hmm, might be because the file extension isn't in place? That would be a mime type thing!

Have 2 choices here:
1) ```
mv ~/bin/ifstart ~/bin/ifstart.sh
```

and

2)
Okay, put this in /home/spiky/bin and call it ifstart.sh
```

#!/bin/bash
ifconfig eth0 down
sleep 5
ifconfig eth0 up

```
Then go to a terminal and ```
chmod +x ~/bin/ifstart.sh; source ~/.bashrc
```

Run it from the terminal like this: ```
sudo ifstart.sh
```

Barrie

---

### Post by spiky001 on 2009-12-28
no still the same

> spiky@dell-linux:~$ sudo ifstart.sh
sudo: ifstart.sh: command not found
spiky@dell-linux:~$ 


dose the file ifstart.sh have to have permmision changed or is it ok just being in that folder change it

---

### Post by Barriehie on 2009-12-28
> **spiky001 said:**
> no still the same



dose the file ifstart.sh have to have permmision changed or is it ok just being in that folder change it

It has to be executable, which the chmod +x takes care of.  If the system can't find it then ~/bin isn't part of your path!  This is nuts! :) Do you have:```
export PATH=$PATH:/home/spiky/bin
``` going on in your ~/.bashrc??? 

Try using the full path; ```
sudo ~/bin/ifstart.sh
```

Post the output of: echo $PATH and the output of ls -l ~/bin again please!

Barrie

---

### Post by spiky001 on 2009-12-28
ok the full path works 

> spiky@dell-linux:~$ export PATH+$PATH:/home/spiky/bin
bash: export: `PATH+/home/spiky/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/spiky/bin/:/home/spiky/bin': not a valid identifier


---

### Post by Barriehie on 2009-12-28
> **spiky001 said:**
> ok the full path works

Okay, so it works if you specify the full path to the file.  Now, the only other error I see is your declaration of adding to your path.  It has to be:
```

export PATH=$PATH:/home/spiky/bin

```

Put that line in your ~/.bashrc file and after saving and closing your editor then type ```
source ./.bashrc
``` so that the system will reload the .bashrc file.  Note the = sign, it's not supposed to be a + as you have indicated.

At that point you should be able to type ***sudo filename.sh*** and it should run!

Barrie

Edit: Then, since that's so much to type, you can alias the whole thing with 'gointernet' and make it run. :)

---

### Post by spiky001 on 2009-12-28
ok checked bashrc code was in there

> 
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples
**export PATH=$PATH:/home/spiky/bin/**

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# don't overwrite GNU Midnight Commander's setting of `ignorespace'.
HISTCONTROL=$HISTCONTROL${HISTCONTROL+,}ignoredups
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoreboth


also ran source ./.bashrc
still not working either

---

### Post by Barriehie on 2009-12-28
> **spiky001 said:**
> ok checked bashrc code was in there



also ran source ./.bashrc
still not working either

Got me!!! Log out and then back in and see what happens when ```
sudo ifstart.sh
``` from the terminal.

Barrie

Edit: If none of that works then install 8.04 LTS...  :)

---

### Post by spiky001 on 2009-12-28
have done that sorry. Is there a reason that i shouldn't put it in usr/local/bin i know i was told not to put user scripts in there?

---

### Post by Barriehie on 2009-12-28
> **spiky001 said:**
> have done that sorry. Is there a reason that i shouldn't put it in usr/local/bin i know i was told not to put user scripts in there?

Yes there is but at this point it seems to be the only place that works...  Last shot is to actually reboot and see if it runs.  Rebooting shouldn't be necessary but then again all of the above should've worked.  Reboot and see what happens when you run it.

Barrie

---

### Post by spiky001 on 2009-12-28
yea did reboot thks for help anyway. not gonna let this stop me tho with scripts

---

### Post by Barriehie on 2009-12-28
> **spiky001 said:**
> yea did reboot thks for help anyway. not gonna let this stop me tho with scripts

Yeah, but they should be running from ~/bin!!!

Later,
Barrie

---

