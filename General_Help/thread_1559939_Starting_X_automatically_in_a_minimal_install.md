---
title: "Starting X automatically in a minimal install"
date: 2010-08-24
forum: General Help
---

### Post by subi211 on 2010-08-24
I'm moving a homebrew arcade cabinet I have in my sitting room over from Gentoo to Ubuntu.  Gentoo's served me well for a couple of years, but it refuses to recognise a touchscreen I recently installed on the cab, so I thought I'd give Ubuntu a try.

There is very little space on the SATA DOM inside the board in the cab, so I try and put as little OS on there as possible.  To that end, I installed the minimal iso, and then apt-got X.  I manually configured xorg.conf to make both monitors attached to the cab work, and I can enter X fine from the command line.

But what I need to do is have X start on powerup and automatically run my game.  In Gentoo this is as simple as putting "xinit [GAME]" into /etc/init.d/local.start (the equivalent of rc.local).  No login required, the prompt didn't even come up until I'd exited the game.

However, if I try and do this in Ubuntu, X can't find any devices, even though rc.local is at position 99.  I've tried putting the lines in rc.local as well as manually update-rc.d-ing my own files, but no luck.  X refuses to start until after the login.

So what seem to need is some way of automatically logging in as root on the command line, starting X, then running my game.  Can anyone help me out?

Thanks.

---

### Post by subi211 on 2010-08-25
I've had *some* success using rungetty.  Changing /etc/init/tty1.conf to call

```
exec /sbin/rungetty --autologin root tty1 -- xinit [GAME]
```

works, but it doesn't seem to behave like a normal X instance.  It doesn't know about any drivers I've manually loaded, fails to use TAB to autocomplete commands, and is still running as user nobody instead of root.  ;)  So clearly the login isn't being done until *after* the program is called (which makes sense, because the program you give rungetty is supposed to handle logging in, but that doesn't help me ;) )

But at least the auto login is sorted, so all I need now is a command line post-login script to run xinit [GAME].  I'll keep looking, but if some kind person can let this Linux newbie know what it is, I'd be very grateful.  :)

---

### Post by subi211 on 2010-08-25
...and for those of you (like me) who had never typed "man bash" before, the file in question is "~/.bash_profile"  ;)

Seriously, the answers to most of the Linux voodoo is in there.  the words 'Type "man bash" first' should be in big letters at the top of every Linux help board.  ;)

---

### Post by dek8 on 2010-09-10
could u write out the complete command and how its done please, im new to linux and im trying to autologin on a minimalist install as well, without a login manager, without the game thing.

---

