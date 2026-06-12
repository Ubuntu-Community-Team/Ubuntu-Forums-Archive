---
title: "Error with &quot;top&quot; command in output screenlet"
date: 2010-04-07
forum: General Help
---

### Post by Talys on 2010-04-07
Greetings all -
I'm attempting to use the output screenlet to always show the output of the "top" command.  However, the screenlet will only display "TERM environment variable not set".  Opening a terminal and running a "env | grep TERM" shows me that the variable is actually set, so I think that the screenlet may not be reading my environment correctly.  Any ideas on how I can fix this?  Thanks!

---

### Post by dargaud on 2010-04-07
I don't know what an output screenlet is, but I guess you give it the command 'top' somewhere ? Replace it with "TERM=xterm top" for instance.

---

### Post by Talys on 2010-04-08
Thanks for the suggestion.  I tried that, and then got a "top:  failed tty get" error.  Some googling told me to try adding the -b flag to the top command, but that just caused the program to hang.

Some info about the screenlet:  it's one of the gnome screenlets coded in python.  This specific screenlet displays the output of a single command.  In this case, I'm trying to get it to work with the top command.

---

### Post by bobcollard on 2010-04-08
Try  Conky, it may fit the bill.  Find it under Synaptic Package Manager.

---

### Post by crazy ivan on 2011-03-13
Same problem here.. Conky is a nice monitor, though painful to configure and i search something for such a simple task as displaying output of a command.

I get the same error with top. Even worse:
"top -b" and "tail -f" kills the poor output screenlet. It just hangs entirely.. They include "top" as a preconfigured command with the screenlet, so in principle the output screenlet should be capable of doing it!

Also when I enter "tty" I get "not a tty", but that is not the problem. Even such a script as "sleep 2; echo 2" kills it.

---

### Post by bobcollard on 2011-03-13
> **crazy ivan said:**
> Same problem here.. Conky is a nice monitor, though painful to configure and i search something for such a simple task as displaying output of a command.

I get the same error with top. Even worse:
"top -b" and "tail -f" kills the poor output screenlet. It just hangs entirely.. They include "top" as a preconfigured command with the screenlet, so in principle the output screenlet should be capable of doing it!

Also when I enter "tty" I get "not a tty", but that is not the problem. Even such a script as "sleep 2; echo 2" kills it.
Monitoring Command output, there are hints here about three items down.
[http://www.ibm.com/developerworks/aix/library/au-monitorlogs/](http://www.ibm.com/developerworks/aix/library/au-monitorlogs/)

---

### Post by crazy ivan on 2011-03-13
Thanks for the link, but the problem is that the screenlet hangs until the command returns an exit code. I circumvented the problem using "since" as shown here:
[https://bugs.launchpad.net/screenlets/+bug/734469]("https://bugs.launchpad.net/screenlets/+bug/734469")

---

