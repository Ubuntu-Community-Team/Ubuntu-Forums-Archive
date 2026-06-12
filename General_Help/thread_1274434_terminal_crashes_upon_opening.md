---
title: "terminal crashes upon opening"
date: 2009-09-24
forum: General Help
---

### Post by blue_flame on 2009-09-24
[Solved ~Look near bottom of post]
I have Ubuntu 9.04 (Jaunty).

I edited a terminal profile to start up with the command, "/bin/sh | cd Desktop". I was just messing around with what commands I could enter. Before I restarted terminal I noticed that the default shell is /bin/bash, but re-opened terminal anyway.

I understand why it crashes, but I don't understand why I can't fix it.
(it executes /bin/sh with the pipe operator which tells it to execute cd Desktop with /bin/sh)

I tried using "gnome-terminal --window-with-profile=default" to open the default profile, but that doesn't work.
I went into the "/home/user/.gconf/apps/gnome-terminal/profiles/Profile0" folder and edited the "%gconf.xml" file to match the "/home/user/.gconf/apps/gnome-terminal/profiles/Default/%gconf.xml" file.
I tried cold and warm booting, and I tried to open the terminal each time..

I searched google and I couldn't find anything.

I can access root terminal, but it doesn't let me change the profiles of the gnome-terminal.
I'm totally lost.
Please help me.
:confused:

[Edit]
I found more information.
I can login to the rootshell, and use "su user" to become my user. The gnome-terminal still doesn't work.
I also figured out why "--window-with-profile=default" doesn't work. It doesn't work, because I have two terminal windows called "machine", and "Default". When I use "--window-with-profile=default" it thinks I want to open the default which is "machine".

[Solved]
I wish someone would've noticed or told me that the argument "--window-with-profile=" is case-sensitive. I guess it's better I learn that on my own. The solution was to start up gnome-terminal with "gnome-terminal --window-with-profile=*Default*" not "default".
I thought about it when I was typing the the default terminal name is "Default" with a capital.

---

### Post by dcstar on 2009-09-25
> **blue_flame said:**
> [Solved ~Look near bottom of post]
........
[Solved]
I wish someone would've noticed or told me that the argument "--window-with-profile=" is case-sensitive. I guess it's better I learn that on my own. The solution was to start up gnome-terminal with "gnome-terminal --window-with-profile=*Default*" not "default".
I thought about it when I was typing the the default terminal name is "Default" with a capital.

Then mark the thread as Solved.

---

