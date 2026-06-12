---
title: "How to run my script at startup..."
date: 2006-06-19
forum: General Help
---

### Post by solarwind on 2006-06-19
Hello everyone,

I have a script called "startupscript" in my home folder "/home/ubuntu_user". I would like to have this script start up when my computer starts up, even before the gnome login screen. For example, I want this script running even before I type my username and password at the login screen. How do I do this?

---

### Post by amohanty on 2006-06-20
Take a look at this:
[http://www.tldp.org/LDP/intro-linux/html/sect_04_02.html](http://www.tldp.org/LDP/intro-linux/html/sect_04_02.html)

Basically, after the kernel is loaded the scripts in ```
/etc/init.d
``` are executed. Linux has the concept of runlevels, although there are 6 runlevels, ubuntu only uses two. 

These runlevels are encapsulated in the folders:
```

09:11 PM $ ls -d /etc/rc*
/etc/rc0.d/  /etc/rc2.d/  /etc/rc4.d/  /etc/rc6.d/
/etc/rc1.d/  /etc/rc3.d/  /etc/rc5.d/  /etc/rcS.d/

```

These folders have links to scripts in 
```

09:12 PM $ ls /etc/init.d/
acpid*              hotplug-net*                      ppp*
acpi-support*       hplip*                            pppd-dns*
alsa*               hpoj*                             procps.sh*
alsa-utils*         hwclockfirst.sh*                  rc*
anacron*            hwclock.sh*                       rcS*
apmd*               ifrename*                         readahead*
....

```

for e.g.:
Ubuntu uses runlevel 2 for multi-user graphical mode X. (for some perspective - I think fedora core 4 uses runlevel 5 for the same):
```

09:14 PM $ ls -l /etc/rc2.d/
total 0
lrwxrwxrwx  1 root root 19 2005-11-19 22:52 k01fetchmail -> ../init.d/fetchmail*lrwxrwxrwx  1 root root 19 2005-11-21 20:08 k01rmnologin -> ../init.d/rmnologin*lrwxrwxrwx  1 root root 17 2005-11-21 21:33 k01usplash -> ../init.d/usplash*
lrwxrwxrwx  1 root root 17 2005-11-19 22:52 k11anacron -> ../init.d/anacron*
lrwxrwxrwx  1 root root 15 2005-11-20 11:54 k19hplip -> ../init.d/hplip*
lrwxrwxrwx  1 root root 14 2005-11-21 22:15 k20apmd -> ../init.d/apmd*
lrwxrwxrwx  1 root root 22 2005-11-21 20:04 k20hotkey-setup -> ../init.d/hotkey-setup*
....

```

In the ```
/etc/rcX.d
``` folders some links will be marked K... and some will be marked S... If I recall correctly (please google all this info - anyway and always) the links to scripts starting with S are executed at startup and the ones named K... are executed at shutdown. The number after the S or K indicates the order in which they are executed. The lowers ones go first.

Keep in mind that runlevel 0 is for halt (shutdown) and runlevel 6 is for reboot.

Thats for starters, so to run your script at boot do the following (in a terminal):

1. create a script to do what you want called (for e.g.) ```
myscript
```
2. then set its executable bit on: ```
chmod +x [CODE]
```myscript[/CODE]
3. put it into ```
/usr/local/bin
``` (you can put it anywhere but this is a good place for user scripts) by doing ```
sudo cp myscript /usr/local/bin
```. Provide your password and press enter.
4. then create a script that sort of looks like the following in your home called something like ```
myscript.service
```
NOTE: some assumptions about your environment are made here, but this is just a template. Google and learn a bit about what I have used here.

```

#! /bin/bash

case $1 in
  start)
    /usr/local/bin/myscript 
    # this will extract your process' process id so that it can be killed at stop
    ps -o pid,command | grep myscript | awk '{print $1}' > /tmp/myscript.pid
    ;;
  stop)
    # see!! - or you could use some more nicer shutdown system
    kill -9 $(cat /tmp/myscript.pid)
    rm -f /tmp/myscript.pid
    ;;
  restart)
    stop
    start
    ;;
  *)
    echo Oops! bad options
    ;;
esac
exit 0

```
5. Put the service script in ```
/etc/init.d
``` using:
```
sudo cp myscript.service /etc/init.d
```
6. Set its executable bit on:
```
sudo chmod +x /etc/init.d/myscript.service
```
7. create a symbolic link to it in /etc/rc2.d with a high start number:
```
sudo ln -s /etc/init.d/myscript.service /etc/rc2.d/S500myscript.service
```
8. create a symbolic link for shutdown:
```
sudo ln -s /etc/init.d/myscript.service /etc/rc2.d/k001myscript.service
```
NOTE: high start # means late start, which means it should be stopped first so low stop #.
9. try it out:
```
sudo /etc/init.d/myscript.service start
```

HTH
AM

---

### Post by glotz on 2006-06-20
What kind of a script is that, if I may interject?

---

### Post by nanotube on 2006-06-20
see the third link in my sig (the faq), and go to the "how to execute things at startup" question.

---

