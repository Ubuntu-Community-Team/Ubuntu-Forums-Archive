---
title: "help need to write a script.... to save lot of trouble !!"
date: 2010-02-18
forum: General Help
---

### Post by jee_bee on 2010-02-18
this thread is an option to solve the probleme of the folowing thread:
[http://ubuntuforums.org/showthread.php?t=1409517]("http://ubuntuforums.org/showthread.php?t=1409517")

i need a script than to put in the startup to kill compiz.real
and execute compiz.real --replace, but i dont want the terminal with compiz.real process to stay visible. i want compiz.real
to be run in background



that's where i im lllolll


> kill compiz.real
exec compiz.real --replace 

---

### Post by ubudog on 2010-02-18
Open a terminal and type ```
gksu gedit /etc/rc.local
```  Gedit, the text editor for ubuntu, will come up.  At the bottom of that file, just above the exit0 type any command you want to be run on startup in the background.  So your /etc/rc.local should look like: 
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
kill compiz.real
exec compiz.real --replace 
exit 0



That should do it.  Hope that helps. :p

---

### Post by Girya on 2010-02-18
> **jee_bee said:**
> this thread is an option to solve the probleme of the folowing thread:
[http://ubuntuforums.org/showthread.php?t=1409517]("http://ubuntuforums.org/showthread.php?t=1409517")

i need a script than to put in the startup to kill compiz.real
and execute compiz.real --replace, but i dont want the terminal with compiz.real process to stay visible. i want compiz.real
to be run in background



that's where i im lllolll

```
compiz.real --replace &
```
will run compiz.real --replace in the background

---

### Post by ubudog on 2010-02-18
> **Girya said:**
> ```
compiz.real --replace &
```
will run compiz.real --replace in the background

Yeah, just put that above the exit 0 in /etc/rc.local and it will be run automagically on startup.

---

### Post by jee_bee on 2010-02-18
whit both solution the terminal stay open ...........

---

### Post by jamesisin on 2010-02-18
If you typed that into a terminal that terminal won't close on its own.  Do you get your command prompt back after running that command?

---

### Post by jee_bee on 2010-02-18
no i dont get it back

---

### Post by ubudog on 2010-02-18
> **jee_bee said:**
> whit both solution the terminal stay open ...........

Add the line I mentioned before to the end of /etc/rc.local just above the exit 0, and reboot.  No terminal will come up.

---

### Post by jamesisin on 2010-02-18
The structure [command] [--argument] & ought to run that command in the background.  Regardless, I would recommend you follow ubudog's instructions above to include this at boot time.

I would also recommend including some documentation in your changes in case you have to look at that file later:

```
# the following two lines I added to restart compiz at boot
```

---

### Post by jee_bee on 2010-02-18
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
kill compiz.real
exec compiz.real --replace
exit 0

IT'S NOT DOING ANYTHING...  EVEN AFTER REBOOT

---

### Post by ubudog on 2010-02-18
Maybe you should create a script in /usr/local/bin and then add it to /etc/rc.local.

---

### Post by jamesisin on 2010-02-18
I suppose we could add a line to route standard error to a log file.

---

### Post by jee_bee on 2010-02-18
english please.....

---

### Post by jamesisin on 2010-02-18
Maybe something like this:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# the following section I added to restart compiz at boot and log results

kill compiz.real 2 >> /var/log/MyFancyKillLog.err
exec compiz.real --replace 2 >> /var/log/MyFancyReplaceLog.err

exit 0
```

---

### Post by jee_bee on 2010-02-19
solution is here....
[http://ubuntuforums.org/showthread.php?t=1409517]("http://ubuntuforums.org/showthread.php?t=1409517")

---

