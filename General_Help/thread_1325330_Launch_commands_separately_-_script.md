---
title: "Launch commands separately - script"
date: 2009-11-13
forum: General Help
---

### Post by mocka on 2009-11-13
Hi, I am thinking about reinstalling my Ubuntu Server and upgrade to 9.10. 

There are lots of packages I want to install, therefore it would be convenient to have a script to install all packages. How do I make the script lanch commands separately (ie. install one package at the time).

As for the script, it would look like this:
```
sudo apt-get update && sudo apt-get install vsftpd && sudo wget http://garr.dl.sourceforge.net/sourceforge/webadmin/webmin_1.441_all.deb && sudo dpkg -i webmin_1.441_all.deb

```

---

### Post by diesch on 2009-11-13
What do you mean by "make the script lanch commands separately (ie. install one package at the time)"?

---

### Post by mocka on 2009-11-13
I'm very new to scripting but I have done some in the past. It has happened that a script I've written contains a command that takes a long time to finish (after execution) and thus the later commands are overlooked.

Perhaps this doesn't happen in Ubuntu?

EDIT: It will install one package at the time, not everyone at the same time.

---

### Post by Boondoklife on 2009-11-13
IIRC, I dont think a shell script will run each command at the same time, the default would be what you discribed.

```
#!/bin/bash
sudo apt-get install pkg1 pkg2
wget link-here
etc
etc
```

The above should do the trick though, let me know.

---

### Post by diesch on 2009-11-13
> **mocka said:**
> I'm very new to scripting but I have done some in the past. It has happened that a script I've written contains a command that takes a long time to finish (after execution) and thus the later commands are overlooked.


That doesn't happen in shell scripts. But if you separate the commands with *&&* like in your example then if one command terminates with an error the following commands don't get run. And running *sudo* needs you to enter your password if iot is more then 15 minutes after the last time you called sudo

I would write a script like
```
#!/bin/sh
apt-get update 
apt-get install vsftpd 
wget http://garr.dl.sourceforge.net/sourceforge/webadmin/webmin_1.441_all.deb && dpkg -i webmin_1.441_all.deb
```

and then run this script using sudo

---

### Post by mocka on 2009-11-13
Thanks a lot to you both; I'll make the script following your advices.

---

