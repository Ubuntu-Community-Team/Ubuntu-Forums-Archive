---
title: "VT100/VT220/KCML Terminal Emulator"
date: 2009-09-01
forum: General Help
---

### Post by tom.randall on 2009-09-01
Hey, sorry if this has already been covered many times before but..... 
I'm looking to move away from Win XP to Ubuntu, however my main problem is getting our legacy sofware to work. we currently use a program called k-open which runs under a VT100/KCML emulator called WDW or K-Client (by kerridge) as far as I can tell the KCML emulator part of the program interacts with windows to allow data to be outputted to windows programs (we don't use this so thats one problem solved) I have managed to use the Gnome Terminal and screen (screen works the best) ie "screen telnet ##.##.##.##" and this opens up ok, however I havn't worked out how to print.

When k-open is used in an old "dum-terminal" or via the windows emulators you can direct print to lpt1. is this possible? if so how?

Thanks to any one who can help out a total novice.

---

### Post by lensman3 on 2009-09-01
Doesn't the environment variable in an xterm work

export TERM=vt100

turn the xterm into a vt100 terminal.  Take a look at the termcap file.  I think TERM=ansi makes a better text terminal.

As for the printer problem, have you tried searching on google groups and limiting the search parameters to pre-1995?

---

### Post by tom.randall on 2009-09-02
Thanks for the tips, I can access our old Unix server fine using Xterm and other similar programs. But my printer problem is that I need to print from the old legacy program, when we used to use dum-terminals (15+ years ago) we had epson dot-matrix printers plugged in to them, and our current Windows emulator copys this function by direct printing to lpt1. Unfortunately this function doesn't seam to exist in any of the Linux emulators I have tested, (eg when I tell the legacy software to print it prints to screen)

PS apologies if I'm missing something very simple.

Thanks again.

---

