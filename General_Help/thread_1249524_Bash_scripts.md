---
title: "Bash scripts"
date: 2009-08-25
forum: General Help
---

### Post by situz on 2009-08-25
Hello!

I'm trying to make a bash script (.sh) that is supposed to start a root terminal, do some commands, and start a program which is going to run in the terminal. It is also supposed to start another program in either a new tab in the terminal (also as root), or in a new root terminal.

these are the commands for the first terminal
```
modprobe raw1394
jackd -R -d firewire -v4
```

and the following for the second terminal tab/new terminal
```
ulimit -l unlimited
/usr/bin/ardour2
```

I'm a complete newbie with bash scripting, and I realise I'm asking a lot here. But any help would be greatly appreciated! 

All I've managed to do so far is create the .sh file and plotted in the commands for the first terminal, and made it executable. to run it I first have to log in as root in a terminal, and do 
```
./file.sh
```
but it would be awesome to integrate it all into one script somehow and make it all automated.

I hope I'm not asking too much.

thanks in advance!:guitar:

---

### Post by dmonkey on 2009-08-26
I'm a bit confused: what's the advantage of starting separate terminal windows? Do you want to be able to type in them?

---

### Post by situz on 2009-08-26
well its kinda handy to be able to monitor jack from the terminal, monitoring ardour is not really needed tho.

I don't need to be able to type in them, but, I forgot to mention that, I need to be able to terminate the jackd process using ctrl + c aswell.
when I ran jackd from the script, it seemed as if I wasn't able to terminate jack, even closing the terminal window didn't actually terminate the process (looking at my external rack sound card, which has an indicator showing when connected, and jackd connects to it)

but its really not needed to have two seperate terminal windows, if it is possible to not have it :)

---

### Post by dmonkey on 2009-08-27
Ok, see if this works for you. Put this code into a .sh file and run it (as a normal user) with bash.

```

#!/bin/bash

gnome-terminal -x sudo su -lpc modprobe raw1394; jackd -R -d firewire -v4
gnome-terminal -x sudo su -lpc ulimit -l unlimited; /usr/bin/ardour2

# exit
exit 0

```

That work?

---

