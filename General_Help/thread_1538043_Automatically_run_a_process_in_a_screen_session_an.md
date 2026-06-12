---
title: "Automatically run a process in a screen session and then detach and quit terminal"
date: 2010-07-24
forum: General Help
---

### Post by Zorgoth on 2010-07-24
There are often times when the best way to launch an application is from the terminal, but it is a graphical application and after it is launched the terminal is useless.  

Examples of places where a terminal is convenient are when a process starts lots of child processes and is also unstable; you can be sure to kill all of its children simply by using Ctrl-C at the terminal.  Also it allows me to read program output and to set up the terminal environment to be optimal for the application (for example "unset LIBGL_ALWAYS_INDIRECT")

With GNU screen, I can get around the hassle of having a terminal window open by using something like the following in a terminal window:

```

screen
my_command
Ctrl-A d

```

and then I can close the terminal and the program will keep running.  Then I just type "screen -r <Tab>" (the tab will get me my screen session if there is only one such session) in any terminal window, even a tty, and I can get the screen session back and use Ctrl-c or something.

So my question is, is there a way to do this automatically so that a launcher or script will start a screen session, inside that screen session start a process, and then detach from that screen session without me having to manually open and close a terminal and type the commands?

---

### Post by DaithiF on 2010-07-24
Hi
screen -d -m starts screen in detached mode.  so you would do:
```
screen -d -m yourcommand

```

---

### Post by Zorgoth on 2010-07-24
Thank you!  That was very helpful and solved my problem completely.

For my example, I actually because of various syntax issues ended up using the following command:

```

screen -d -m bash -c "unset LIBGL_ALWAYS_INDIRECT && env WINEPREFIX='/home/jonathan/.wine' && wine C:\\\Program\ Files\\\Steam\\\Steam.exe"

```

---

