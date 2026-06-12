---
title: "how to open two programs at once?"
date: 2010-12-11
forum: General Help
---

### Post by jesseafrantz on 2010-12-11
*Before you think I am trolling or this is retarded. I AM USING A VPS, UBUNTU SERVER, SO I HAVE NO GUI.*


How do you open two programs at once inside of the terminal. I need to open two programs "mangos-realmd" and "mangos-worldd". But when I run "mangos-realmd" it keeps it there and I can't do anything else until I close it. I am restricted to SSH since I am using VPS and it's a server so there is no GUI. I can't really explain this very well. :\ but I'll show an example.

```

$: mangos-realmd

MaNGOSZero/0.12.0 (* * Revision 1075 - *) for Linux_x64 (little-endian) [re
<Ctrl-C> to stop.

Using configuration file /home/root/mangoszero/etc/realmd.conf.
Database: 127.0.0.1;3306;root;mangos;realmd
MySQL client library: 5.0.51a
MySQL server ver: 5.0.51a-3ubuntu5.8
Added realm "Goldshire"

```

[I](and then there is no prompt to do more commands unless I close the program with <Ctrl-C>.)
[/I]

But I need to have another program running at the same time, as I said I don't have a GUI so I cant just minimize that terminal and open another one. :(

---

### Post by drs305 on 2010-12-11
Join the two commands on the same line with "&"

```
gedit & ls /mnt
```

---

### Post by jesseafrantz on 2010-12-11
> **drs305 said:**
> Join the two commands on the same line with "&"

```
gedit & ls /mnt
```

DOH!.. I feel dumb >.<

---

### Post by StephenDavison on 2010-12-11
The ampersand at the end of a command runs it in the background.  You don't have to put them on the same line either.  

$: mangos-realmd &
$: mangos-worldd &
$:

Once you cross that bridge into running commands in the background, you may want to read up on the shell's various job control facilities.  Depending on what shell you are using, you should look at commands like:
jobs
fg
bg

Also, let's say you accidentally run a command in the foreground (e.g. $: mangos-realmd), but wanted it in the background.  You should be able to use ctrl-z to stop the foreground process, and then put it in the background with bg %1.  That will get you back to a shell prompt with your realmd running in the background. 

UNIX command line shells are one of the reasons I love UNIX-like operating systems like Linux and OSX.

---

### Post by jesseafrantz on 2010-12-11
Thanks for the info!

---

