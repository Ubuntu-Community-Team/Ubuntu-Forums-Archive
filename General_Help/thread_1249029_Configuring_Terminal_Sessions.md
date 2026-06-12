---
title: "Configuring Terminal Sessions"
date: 2009-08-24
forum: General Help
---

### Post by johnDonaldson on 2009-08-24
A long time ago, I used a Unix/Linux like OS called OS9. I could run various terminal settings configured to how I wanted it to run. Back then everything was done from the command line, so each terminal session was incorporated with a script that configured it.

Now that we have these great GUI's, I want to setup some Terminal sessions, rename them to reflect what I want to do, then configure them to auto run a script.

This was a ease to do under MSWinXP but I have forgotten how to do it under this type of OS.

---

### Post by Johnny B on 2009-08-24
you can rename a terminal session by clicking edit > profile preferences > title and command or by running $gnome-terminal --title=
could you be more specific about your auto script idea?

---

### Post by kaibob on 2009-08-24
> **johnDonaldson said:**
> Now that we have these great GUI's, I want to setup some Terminal sessions, rename them to reflect what I want to do, then configure them to auto run a script.
The command-line utility, gnome-terminal, will do what you want. For example, the following command opens a terminal window of the specified geometry with the title "Test" and executes the script named scriptname. In this case, the script contained only an ls command, so the final bash command was necessary to keep the terminal window open. An alternative would be to substitute read for the second bash command. 

```
gnome-terminal --geometry=60x30 --title=Test --execute bash -c "scriptname ; bash"
```

Depending on what the script does, you may also want to try the --command option. Check the gnome-terminal man page for more information.

---

### Post by marius_vt on 2009-08-26
Hi Guys,
I have done this so far and getting my gnome-terminal to open and then start running another script.

So far I have only done this from command line.

Here is what I have so far.
_Startup.sh_
#!/bin/bash
gnome-terminal --geometry=100x65 --title=Test --execute bash -c "sh Dynamips.sh ;bash"

_Dynamips.sh_
#!/bin/bash
sudo tunctl
sleep 1 
sudo ifconfig tap4 192.168.255.1 netmask 255.255.255.0 up
sudo /home/marius/./start.lab.sh
sleep 1
sudo /home/marius/Dynamips/IE/./start_lab.sh

It is working great when I run it from command line.

It asks me for my password due to the sudo I have added,
Is there a way I can send my password to the term within the script?
To keep in mind I want the first script to run at startup.

Regards,

---

