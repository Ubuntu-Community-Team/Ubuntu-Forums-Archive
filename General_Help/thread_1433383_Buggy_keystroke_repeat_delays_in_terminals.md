---
title: "Buggy keystroke repeat delays in terminals"
date: 2010-03-19
forum: General Help
---

### Post by zaadjis on 2010-03-19
I'm experiencing the same very annoying problem described [here]("http://www.linuxquestions.org/questions/linux-kernel-70/keyboard-delay-in-ttys-from-2.6.28-16-generic-to-2.6.31.6-on-ubuntu-9.04-jaunty-769290/").
> If I open a terminal and start writing, my keyboard input hangs for exactly for 1/4 of second every two seconds, and then everything I typed in that 1/4 second shows up all at once.

As a clarifying example: if I keep the `T` key pressed, it repeats as normal, but every 2 seconds it seems to stop for a 1/4 second, after which all the `T`s which would have been printed in that time are printed all at once.

I have this problem every time I type into a terminal, be it gnome-terminal, xterm, or even the CTRL+ALT+F1 console. But this does NOT happen if I type in GUI applications. For example, if I type in Firefox or gedit, everything works ok. It's just ttys that have this problem.

Also, the lag happens for output (not just input/keystrokes) when running this in gnome-terminal (the delay is significantly shorter though):
```

while true; do echo -n t; sleep .1; done

```

```

$ uname -a
Linux as5520g 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux
$ cat /etc/*release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"
```

Any ideas on how to attack/debug this?

---

### Post by zaadjis on 2010-03-19
Same bug described also here: [http://ubuntuforums.org/showthread.php?t=1340072](http://ubuntuforums.org/showthread.php?t=1340072)

---

### Post by zaadjis on 2010-03-22
[https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/544703](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/544703)

---

