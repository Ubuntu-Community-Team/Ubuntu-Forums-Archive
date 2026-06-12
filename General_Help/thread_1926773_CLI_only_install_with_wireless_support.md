---
title: "CLI only install with wireless support"
date: 2012-02-16
forum: General Help
---

### Post by e24ohm on 2012-02-16
Folks:
I have older hardware, which runs very slow with the GUI; however, for what I need, I only need the CLI and wireless.

What is the easiest way to get wireless configured without a GUI? I am not sure where the wireless configuration settings are stored.

Any insight and suggestions are welcomed.

Thanks.

---

### Post by absolutezero1287 on 2012-02-16
Why not try and use WICD? The gui is wicd-gtk but there is a commandline curses client that you can use by installing the wicd-curses package.

From the WICD man page:
> 
NAME
       Wicd - Wired and Wireless Network Connection Manager

THEORY OF OPERATION
       Wicd  is  designed  to  give the user as much control over behavior of network connections as possible.  Every network, both
       wired and wireless, has its own profile with its own configuration options and connection behavior.


---

