---
title: "boot w/o X"
date: 2009-08-03
forum: General Help
---

### Post by Qvintvs on 2009-08-03
I just installed Ubuntu and I tried to install ATI's fglrx drivers. I probably should have known better by now considering fglrx has messed up X on two other distros (Arch and Gentoo), but I figured I'd give it a try on Ubuntu. Anyway, right now, when I try booting into Ubuntu I get to this messed up screen that seems to be a failed attempt at rendering an X session. I can't switch to any termials with Ctrl+alt+F{1-6}, nor can I kill X with ctrl+alt+backspace. I tried booting with runlevel 3 but that didn't seem to help.

So, is there some other runlevel I can boot with that won't start x, or anything else I can do? I have access to another linux environment if that's neccesary to edit some files on my ubuntu partition or something.

---

### Post by jocampo on 2009-08-03
> **Qvintvs said:**
> I just installed Ubuntu and I tried to install ATI's fglrx drivers. I probably should have known better by now considering fglrx has messed up X on two other distros (Arch and Gentoo), but I figured I'd give it a try on Ubuntu. Anyway, right now, when I try booting into Ubuntu I get to this messed up screen that seems to be a failed attempt at rendering an X session. I can't switch to any termials with Ctrl+alt+F{1-6}, nor can I kill X with ctrl+alt+backspace. I tried booting with runlevel 3 but that didn't seem to help.

So, is there some other runlevel I can boot with that won't start x, or anything else I can do? I have access to another linux environment if that's neccesary to edit some files on my ubuntu partition or something.

Go to recovery mode. You'll find that option when machine is booting up. Then... edit your X11 as needed using vi. You can also boot via Live CD and you'll have GUI so you can edit and play a bit with your configuration.

---

### Post by djurny on 2009-08-03
get the grub menu during boot, add the following to the kernel commandline

```
single
```

or:

boot a live cd and 
```
chmod -x /etc/init.d/[gk]dm
```
to prevent the display manager from starting up..

after that, revert your xorg.conf by
```
dpkg --reconfigure xorg-server
```

recovery mode should behave the same as adding 'single' to the kernel commandline..

preferred way is to choose the 'recovery mode' from startup menu like jocampo mentioned :)

---

### Post by Qvintvs on 2009-08-03
Using single on the kernel line worked. (I didn't have Ubuntu configure grub for me so I don't have a recovery mode option). I removed the fglrx drivers and now I'm running vesa (:().

I guess that pretty much answers this thread.

---

