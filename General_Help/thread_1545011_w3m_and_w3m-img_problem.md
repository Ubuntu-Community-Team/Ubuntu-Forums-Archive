---
title: "w3m and w3m-img problem"
date: 2010-08-03
forum: General Help
---

### Post by syaoran87 on 2010-08-03
Hi people, 

I have a problem with w3m-img and w3m. It works fine as a text browser but I can't see any images, although I installed w3m-img. Is there any configuration that I must take note? Also, how do I input commands in w3m, I try to press 'I' to prompt a command but nothing is happening..

Many thanks to your help!

---

### Post by syaoran87 on 2010-08-03
anyone with experience on w3m, can you help me? PLEASE!

---

### Post by torrancew on 2010-08-09
Hi,

I began tinkering with this around the same time you posted, and have not had much luck in getting it to work with either terminator or gnome-terminal as my terminal emulator. I have, however, gotten it to work when using the rxvt emulator (sudo apt-get install rxvt will get it). I've only just found this out, and will be exploring other options/compatibility with other terminals.

-Tray

---

### Post by syaoran87 on 2010-08-09
thanks for the tip tray! Apparently, i have read quite a few sites that people succeeded in using w3m-img to showcase the image. Unfortunately, they didn't state which terminal that they are using.

---

### Post by dino99 on 2010-08-09
maybe try with: ‘w3m-el-snapshot’

[http://www.emacswiki.org/emacs/emacs-w3m](http://www.emacswiki.org/emacs/emacs-w3m)
[http://manpages.ubuntu.com/manpages/lucid/man1/w3m.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/w3m.1.html)

---

### Post by WorMzy on 2010-08-09
Do images work outside of a tty? They don't on Arch linux (AFAIK), but I dunno about Ubuntu.

Press Ctrl+Alt+F1 to switch to a tty, log in, and run w3m there.
Alt+F7 (or possibly F8) will bring you back to X.

---

### Post by torrancew on 2010-08-09
OK, after a bit of research and tinkering, I have w3m working for my use-case. I wanted to be able to use it with newsbeuter (an ncurses-based RSS reader, very similar to mutt). The first step for me was installing rxvt and w3m-img.

```
sudo apt-get install rxvt w3m-img
```

After this, I confirmed that launching rxvt got me a working w3m instance, and when this was confirmed, I wrote a short wrapper script to handle this for me (an alias would also suffice)

```

#! /bin/bash
# Browser script - calls w3m inside rxvt

/usr/bin/rxvt -e /usr/bin/w3m "$@"

```

At this point, sshing to the box with X11 forwarding worked for me:
```
ssh -X host.example.com
```
To take it one step farther, I wanted integration with GNU Screen, which was as simple as checking my DISPLAY variable outside of screen:

```

echo $DISPLAY

```

And then grabbing my screen session, and setting this variable to the same value

```

export DISPLAY="localhost:10.0"

```

At this point, I can call the browser discretely with my wrapper script, or from within newsbeuter/mutt. The only inconvenience I have left is that the DISPLAY variable changes when initiating a new SSH/X session. I am currently playing with a few techniques to automate the setting of this, and will keep this post updated.

-Tray

---

