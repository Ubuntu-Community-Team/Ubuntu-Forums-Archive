---
title: "how to startup program as root, or in terminal?"
date: 2010-07-06
forum: General Help
---

### Post by rado3105 on 2010-07-06
I have program: pinger for pinging ips. There are two way how to start it - in terminal window: writing pinger in terminal or in gtk windows: writing in terminal sudo pinger --gtk.
Can you help me how to start it after startup?

program info:
[http://ubuntuforums.org/showthread.php?t=311813](http://ubuntuforums.org/showthread.php?t=311813)

---

### Post by sisco311 on 2010-07-06
According to the README file `make install` creates a [suid]("http://en.wikipedia.org/wiki/Setuid") application. So you don't need sudo to run it as root.

---

### Post by fetuspuppet on 2010-07-06
Maybe add it to your .xinitrc file at the bottom


pinger &


Btw if you're doing network monitoring have you checked out OpenNMS ZenOSS Nagios or Syslog-ng?

---

### Post by rado3105 on 2010-07-06
I installed it using debian package.

from terminal:
> r-c@r-c-desktop:~$ pinger --gtk
Available modes: ncurses GTK
Using mode: GTK
Reading configuration file /home/r-c/.pingerrc
Using file /home/r-c/.pingerrc
### found options section
Name: title, value: standard set
Setting title to new value: standard set
------------------

Pinger version 0.32c, Petr Koloros, <silk@sinus.cz>

Successfuly removed root privileges.

(process:1940): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

---

### Post by rado3105 on 2010-07-06
I have no idea how to do this:
> Maybe add it to your .xinitrc file at the bottom


pinger &

i cant find .xinitrc file, i have ubuntu.

---

### Post by sisco311 on 2010-07-06
Add *gksu pinger --gtk* to the startup applications and move the config file from your home directory to /root.

To allow your user to run the application without a password, edit the sudoers file:
[thread=1132821]HowTO: Sudoers Configuration[/thread]

---

### Post by rado3105 on 2010-07-06
I put it in startup, also moved config file to /root. Nothning happens after restart. Am I also supposed to change privileges for other users?

---

### Post by Zorgoth on 2010-07-06
Isn't this something that should go in rc.local?

Or if you want it to boot after login, you can put in in /etc/gdm/PreSession or /etc/gdm/PostLogin in the Default file (you may need to uncomment something, I don't remember)

---

### Post by rado3105 on 2010-07-07
I have no idea how to do it in ubuntu. It is easy to do it in gentoo, but in ubuntu I dont know the way.

---

### Post by Zorgoth on 2010-07-09
Do what I said; it works.  I have scripts to run Truecrypt as root when I log in in /etc/gdm/PreSession.  You could do the same thing.  You have to put it in the file called "Default"

---

### Post by rado3105 on 2010-07-16
I tryed to put gksu ping --gtk in /etc/gdm/PreSession/Default or /etc/gdm/PostLogin/Default, but none way was working. Maybe it runs in backgroun, but it doesnt shows in screen, and I need it to be shown in screen.

---

