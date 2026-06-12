---
title: "Lock screen not working after 10.10 -&gt; 11.04 upgrade"
date: 2011-08-11
forum: General Help
---

### Post by rts on 2011-08-11
So, finally, after getting my keyboard and mouse working ([http://ubuntuforums.org/showthread.php?t=1822748](http://ubuntuforums.org/showthread.php?t=1822748) not even when I was compiling kernels from floppies that came in the back of books did I have to work so hard to get the KEYBOARD working, sheesh), I have a mostly working system.

However, Lock Screen does not work in any way, shape or form:

- It doesn't work via the keyboard shortcut Ctrl+Alt+L
- It doesn't work if I select it from the Power button on the upper-right
- It doesn't work if I press the Power button to suspend (even though all the correct things are ticked/unticked in gconf-editor)
- It doesn't work if I switch users and back

Now, I do have a laptop running 11.04 and its Lock Screen *does* work.  The only difference I can find is that the laptop says gdm is running screensaver:

```

rts       1444  0.0  0.4  28516  4688 ?        Sl   Aug07   0:04 /usr/bin/gnome-screensaver --no-daemon
gdm       6248  0.0  0.2  27948  2224 ?        Sl   Aug08   0:00 /usr/bin/gnome-screensaver --no-daemon
gdm       6575  0.0  0.1  19188  1256 ?        S    Aug08   0:00 /usr/lib/gnome-screensaver/gnome-screensaver-gl-helper

```

but on this desktop machine:

```

rts       2170  0.0  0.1  29420  2760 ?        Ss   20:43   0:00 gnome-screensaver
rts       2372  0.0  0.0   5308   884 pts/0    S+   20:55   0:00 grep --color=auto screen

```

So, should gdm be running gnome-screensaver?  Why isn't it?  How do I get it to?

If it shouldn't be running, why else might Lock Screen not be working?

---

### Post by rts on 2011-08-11
I found this output when running gnome-screensaver --no-daemon --debug and then locking the screen:

```

[lock_command_watch] gs-window-x11.c:1598 (19:17:51):	 command output: ** (gnome-screensaver-dialog:4923): DEBUG: Screen locking disabled: running under GDM

```

Googling for that phrase turned up this unanswered question: [https://answers.launchpad.net/ubuntu/+question/33866](https://answers.launchpad.net/ubuntu/+question/33866)

So... anyone know what this means and how to fix it?

---

### Post by rts on 2011-08-11
Somehow the line RUNNING_UNDER_GDM=yes was put into /etc/environment.

Deleting that line and rebooting has solved this problem.

---

