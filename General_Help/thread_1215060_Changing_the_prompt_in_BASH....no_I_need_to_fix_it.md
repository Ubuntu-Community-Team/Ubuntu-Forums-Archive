---
title: "Changing the prompt in BASH....no I need to fix it"
date: 2009-07-16
forum: General Help
---

### Post by jus71n742 on 2009-07-16
First thing I need to know is how to or what the default is for the prompt option in ~/.bashrc

I did the following
```

sudo vi .bashrc

```
then on line 56 you see the following:
```

case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='[COLOR="Red"]$[/COLOR]'
    ;;
*)
    ;;
esac

```
and as one might assume I need what goes in place of the red "$".

also I know I read a way to change the look of the prompt and I never edited a file as best I can remember (could be wrong and prob am) but I remember it being a command then if it was a file it was a small file and then my prompt was changed.  

any help is appreciated.

---

### Post by wojox on 2009-07-16
# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac
#
#

---

### Post by jus71n742 on 2009-07-16
```
bash: [e]0: command not found
bash: u@h:: command not found

```

is what I get when I place anything in that line.  
I did however find that command I was thinking of
```

declare -x PS1="prompt"
```

but I still recieve the error about the above mentioned when I restart everything.

thanks for the help and quick reply though

---

### Post by redmk2 on 2009-07-16
I think you are better served by reading what you have regarding all prompt settings in the .bashrc file.

The first part is for setting the colors in the prompt if you want to.  The second part is an if statement for either color or not prompts.  See below:```
#[COLOR="Red"]do we want colors[/COLOR]
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

[COLOR="Blue"]#set the prompt either with or without colors[/COLOR]

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\>' [COLOR="Green"]<---set the non color here[/COLOR]
fi

```

---

### Post by jus71n742 on 2009-07-16
I already have that set up, and looks pretty much identical to what you have ...I just want to change it where there is a "$" as opposed to hostname@uid-desktop:pwd etc etc and then I have this huge long prompt which distracts me
but I edited the .bashrc on the above mentioned line and receive the error message listed above as well.

on my file the line I am looking at is literally the next case below what you put up redmk

```

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND=';${debian_chroot:+($debian_chroot)}\u \h:\w\a\]$PS1'
    ;;
*)
    ;;
esac

```

the bottom half of that output

---

### Post by redmk2 on 2009-07-16
Quoting from [[COLOR="DarkSlateGray"]http://tldp.org/HOWTO/Bash-Prompt-HOWTO/x264.html[/COLOR]]("http://tldp.org/HOWTO/Bash-Prompt-HOWTO/x264.html")
"Bash provides an environment variable called PROMPT_COMMAND. The contents of this variable **are executed as a regular Bash command just before Bash displays a prompt.**  

In other words $BASH_PROMPT does NOT set the prompt.  It mearly executes a command stored in the bash variable $BASH_COMMAND.

The primary prompt is held in PS1.

This is wy you have the errors.

---

### Post by jus71n742 on 2009-07-16
thank you that cleared it up...so if I want nothing displayed or executed I should just leave it blank....or find someone with an untouched .bashrc and copy theirs to restore the default since reset didn't work.  
thanks again redmk

---

### Post by redmk2 on 2009-07-16
Here is the unmolested code ```
# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
    ;;
*)
    ;;
esac


```

Edit:  As a best practice you should make copies of files BEFORE you modify them so you can recover from errors.

Edit 2:  I just realized something.  This sets the title in the X terminal window bar!

---

### Post by Brandon Williams on 2009-07-16
The default .bashrc file installed in a new user account is /etc/skel/.bashrc. You'll also find the default .profile and .bash_logout file in /etc/skel/.

---

