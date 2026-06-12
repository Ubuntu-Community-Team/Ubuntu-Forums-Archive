---
title: "running graphical apps with 'at'"
date: 2010-01-24
forum: General Help
---

### Post by Fifoxtasy on 2010-01-24
hi there

i'm trying to run a graphical program at a specific time with the help of 'at'. i'm on kubuntu but i think this will be the same on any *buntu.

i searched a lot but it's hard to find help, because 'at' is such a common word. i found this bug [http://bugs.launchpad.net/ubuntu/+source/at/+bug/94933](http://bugs.launchpad.net/ubuntu/+source/at/+bug/94933) but the mentioned work around doesn't work.

i can make at work with command line if i enter the a tty to make the output to.
example of what i do is:
```
$ at now
warning: commands will be executed using /bin/sh
at> date > /dev/tty1
at> <EOT> (CTRL+d)
```

this will print the date to tty1. but running graphical apps (like kate for example) doesn't work at all. i tried running it on /dev/tty7 or even the terminal window /dev/pts/1. if i don't enter a tty tasks will still get executed for example ```
mkdir test
``` creates a directory in my home directory, but i don't see them happening.
whatever i enter, to launch a graphical application nothing happens.

can somebody help me with this please?

---

### Post by blueridgedog on 2010-01-24
Note that the Man page for AT states:

```
For  both  at  and  batch, commands are read from standard input or the
       file specified with the -f option and executed.  The working directory,
       the  environment (except for the variables TERM, DISPLAY and _) and the
       umask are retained from the time of invocation. 
```

What this means to you is that you need to set the DISPLAY variable in your script.

Such as:

```

:~$ at now
warning: commands will be executed using /bin/sh
at> export DISPLAY=:0.0
at> gcalctool
at> <EOT>
```

---

### Post by Fifoxtasy on 2010-01-24
it works!

nice! thanks a lot blueridgedog!

can i use 'at' to wake my computer from suspend to ram/hd (standby/hibernation)? do i need another program for that?
i know my bios supports it (it worked when i was still using windows)

---

### Post by blueridgedog on 2010-01-24
> **Fifoxtasy said:**
> can i use 'at' to wake my computer from suspend to ram/hd (standby/hibernation)? do i need another program for that?
i know my bios supports it (it worked when i was still using windows)

Sorry, I can't help you there.  I don't use suspend and haven't a clue as to how it integrates with the Linux I learned 15 years ago.

---

### Post by J-Doe on 2010-10-21
Hey guys,

I recently found this article [http://www.linuxloop.com/2009/04/21/how-to-pain-free-backups-with-grsync-and-gnome-schedule/]("http://www.linuxloop.com/2009/04/21/how-to-pain-free-backups-with-grsync-and-gnome-schedule/")

It contains a simple howto on scheduled backups using grsync. I'm no commandline wizard so I can't seem to make this work and I think it's related to this problem discussed on this thread.

According to the article the simple command would be > grsync -e “name of session”. If I input this to gnome schedule it dosen't work, but when inserted directly to command line it work just fine.

I've also tried grsync -e "name of session" export DISPLAY=0.0 but with no luck.

Could some help me out?

---

