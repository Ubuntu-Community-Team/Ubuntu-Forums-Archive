---
title: "Xmonad not responding?"
date: 2011-05-10
forum: General Help
---

### Post by Jabrick on 2011-05-10
Hey I'm trying to run xmonad, but the hot key alt+****+enter is not giving me the terminal.
Is it because I haven't installed xterm?
Right now I can't do anything on my machine because I cannot access terminal.
I always boot to SLiM, and from there enter xmonad.
By the way I'm running arch, I would post on the arch forums but I can't sign up since I need the terminal to run a verification code type thing.
Thanks in advance!

---

### Post by bodhi.zazen on 2011-05-10
Could certainly be due to the lack of xterm. could be your key mapping, what kind of keyboard do you have ?

As you are on Arch, install another window manager, say openbox.

Debug xmonad in Xephyr.

---

### Post by m_duck on 2011-05-10
If you have not customised the configuration file, the default terminal is xterm.

Default config for 0.9:
```
...
terminal = "xterm"
...
[ ((modMask .|. shiftMask, xK_Return), spawn $ XMonad.terminal conf) -- %! Launch terminal
...
```

[http://xmonad.org/xmonad-docs/xmonad/XMonad-Core.html#v%3Aterminal](http://xmonad.org/xmonad-docs/xmonad/XMonad-Core.html#v%3Aterminal)

---

### Post by Jabrick on 2011-05-10
I found my mistake, as was stated I still had to install xterm.
Also to go straight to the terminal the command is Ctrl-Alt-F6.
Thanks to the Linux community!

---

