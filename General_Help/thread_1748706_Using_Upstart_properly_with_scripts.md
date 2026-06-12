---
title: "Using Upstart properly with scripts"
date: 2011-05-03
forum: General Help
---

### Post by goblinlord on 2011-05-03
I seem to be having some issues.  I want to do the following.  I want a script to run prior to any GUI starting (so that if it does crash close or whatever it is not effected).  I am able to run the script after the system is booted and it works exactly as I want it to.  Once the GUI opens I have a window open and maximize with no decoraction via devilspie.  This way I have a desktop that can monitor the logs but not interact directly interact with the shell which is actually recording the logs.
  The problem is, when I try and use a simple Upstart script to start it the script does not seem to be working.  If I do a ps -A it seems to be still running.  What it should be doing is recording what the serial input to the log file I am using.  In fact... it doesn't seem to be capturing anything.  If I try and run the script manually after the computer has booted (with the Upstart script run) to a GUI it crashes the system.

The script I am running is simply to record any incoming data from a Serial connection.  It sets up the serial port then starts recording.

The shell script is as follows:

```
#!/bin/bash
stty -F /dev/ttyS0 9600 -crtscts cs8 -parenb -cstopb -clocal ixoff ixon
grep --line-buffered -v "^$" /dev/ttyS0 >> /home/user/log/current.log
```

The Upstart script is as follows:

```
start on local-filesystems
stop on runlevel [!2345]

exec /usr/bin/script
respawn
```

UPDATE:  Tried something slightly different.  Attempted combining them and just putting the script in script tags in the upstart script.

```
start on local-filesystems
stop on runlevel [!2345]
script
 stty -F /dev/ttyS0 9600 -crtscts cs8 -parenb -cstopb -clocal ixoff ixon
 grep --line-buffered -v "^$" /dev/ttyS0 >> /home/user/log/current.log
end script
respawn
```

Still not working though... any help or direction would be greatly appreciated.

---

### Post by goblinlord on 2011-05-04
Seeing as this is already 20+ pages deep... giving it a bump in hope of making help more likely.

---

### Post by goblinlord on 2011-05-09
Still looking for some help on this one... made upstart script according to what seems to be right.  Still... does not stream input to file.  The purpose of this is to have it running regardless of the Desktop Environment therefore I can't use session autorun settings.

---

### Post by goblinlord on 2011-05-17
Still looking for help with this.  As far as I can tell the script starts up but will not record anything.  If I run the script after it has been started via Upstart... the system crashes.  Starting the script manually after boot without the Upstart script and it works perfectly.  Is there anyone who can at the least give me some kind of direction for this?

---

### Post by goblinlord on 2011-05-22
Still looking for some direction =/

---

