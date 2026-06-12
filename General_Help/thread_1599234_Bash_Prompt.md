---
title: "Bash Prompt"
date: 2010-10-17
forum: General Help
---

### Post by hewjr1000 on 2010-10-17
I can temporarily change Bash prompt, but cannot save permanently.

I googled and tried some examples, but I messed up .bashrc

Fixed .bashrc now can anyone correclty tell me hw to do this.

Also would like to change root prompt to match, major OCD

Henry

Ps see attached

Pss Would like bash prompt to read: Henry E Wyatt Jr >

and root to read: Root Henry E Wyatt Jr >

---

### Post by papibe on 2010-10-20
First backup your file:
```
$ cp .bashrc .bashrc.old
```
Then open the file and go to this line:
```
# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

```
and do the following change: comment the line that starts with PS1, and add a new one like this:
```
# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    # PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    PS1="Henry E Wyatt Jr >"
    ;;
*)
    ;;
esac

```

Good Luck!

---

