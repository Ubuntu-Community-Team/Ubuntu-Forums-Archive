---
title: "Run script as specific user"
date: 2009-12-11
forum: General Help
---

### Post by Zilioum on 2009-12-11
Hi,

I want Vuze to start in console mode when my server starts. For this I wrote the following script, which starts Vuze in console mode:```
 
#!/bin/sh

cd /opt/vuze
java -jar Azureus2.jar --ui=console

```

If I run the script in the terminal, everything works fine. But as soon as I start it from /etc/rc.local when booting up, it loads Vuze in console mode, but it uses the settings from something like root/.azureus and not myusername/.azureus. 
Thats a problem, because it doesn't load the correct plugins and settings.
Is there a way to make the script run as a specific user?

Thanks for your help.

---

### Post by bobb0009 on 2010-06-28
To run the script as a specific user just add 

sudo -u {username} {scriptname}

I load azureus from /etc/rc.local and the user I start it from is called bob9

My /etc/rc.local looks like this..

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
sudo -u bob9 /usr/bin/setsid /usr/bin/java -jar /usr/share/java/Azureus2.jar --ui=console >/dev/null 2>&1 </dev/null &
exit 0

---

