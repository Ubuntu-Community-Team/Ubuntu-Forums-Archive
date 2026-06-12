---
title: "&quot;Continuous&quot; Script with root privileges during boot/login. HELP."
date: 2010-12-08
forum: General Help
---

### Post by DuduMoraes on 2010-12-08
Hello my friends!

I've done a very simple shell script to shutdown my computer via web browser. This can be useful, because I can shut it down via my iPhone when i'm not home and a thunder storm starts.

It works perfectly when I execute it after i've logged in. But I want it to be a "native" process. I want it to be executed during boot or login and it must have sudo privileges in order to halt the PC.

The problem is this Script "never ends": or it receives the sign to shutdown or it starts itself again after sleeping 60 seconds. Take a look:


#!/bin/sh

# First it tries to download a "shutdown.txt" file, that is created via PHP when I send the command.
wget [http://www.mydomain.com/shutdown.txt](http://www.mydomain.com/shutdown.txt)

#Then it checks if it has suceded in downloading the file. 
if [ "`find shutdown.txt`" != "shutdown.txt" ]; then

#If not.... he sleeps and starts again.
sleep 60
./shutdown.sh

#If he finds it, he accesses the server where the shutdown.txt is located via FTP, delete it, delete the shutdown.txt that was downloaded, and then shuts the PC down

else
ftp -n ftp.mydomain.com <<END_SCRIPT
quote USER xxxxxxx
quote PASS xxxxxx
cd www
delete shutdown.txt
END_SCRIPT
rm -f shutdown.txt
shutdown -h now
fi
fi


So, the problem is: if I put this script to run during the boot process my PC will never boot! It will shutdown, or try again.

Can anyone here help me to solve this problem? All I want is to make my script work without having to manually execute it every time a use the PC.

Thank you very much for reading such a big post! :)

---

### Post by Foxheadz on 2010-12-08
wait you want it to start during boot?

---

### Post by DuduMoraes on 2010-12-08
In fact, it doesn't really matter when it starts. The most important is that he starts automatically with sudo privileges.

---

### Post by Foxheadz on 2010-12-09
Well from what i know, unless you can put in some code at the beginning of your script that enters the sudo password you just need to enter it when it starts

---

### Post by DaithiF on 2010-12-09
if only there were some way of running a job at regular intervals.  what would be even better would be if each user, including root, could have a set of such jobs, where you just tell the system when or how often you want a job run, and the system would  take care of it for you.  

then you wouldn't need scripts to do silly things like sleep 60 and re-run themselves, they could just do the task they are intended to do, and allow the the system to take care of the scheduling.

oh wait, there is exactly such a system ... cron

hint: 
do 
```
sudo crontab -e

```
add this line:
```
* * * * * /path/to/your/script

```
take out the piece of your script that tries to handle sleeping / restarting itself
and bobs your uncle, your script will be run by root every minute.

---

### Post by DuduMoraes on 2010-12-09
Thank You Very Much DaithiF!

Works like a clock now! ;)

---

