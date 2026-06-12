---
title: "syntax highlighting Jaunty"
date: 2009-12-18
forum: General Help
---

### Post by mudcow007 on 2009-12-18
hello all im trying to figure out why my highlighting isnt working on my jaunty box.

i want to to highlight the same way as Vi does.

this works on my feisty box.

if i uncomment the PS1 lines as per comments....

```
# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
xterm-color)
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;
*)
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    ;;
esac

# Comment in the above and uncomment this below for a color prompt
# PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
```

all i get is a lime green prompt

somebody please help!

---

### Post by mudcow007 on 2009-12-18
[IMG]http://i25.photobucket.com/albums/c81/mudcow007/Screenshot.gif[/IMG]

heres a screen dump of it working correctly on out feisty fawn box

---

