---
title: "Cannot start X server"
date: 2009-12-26
forum: General Help
---

### Post by cz8 on 2009-12-26
Hi there :)
Here is the technical problem I've encountered recently:
After upgrading some of the softwares on Ubuntu, i rebooted my laptop. But the weird thing is that it only takes me to the CLI every time i boot the laptop.

so I tried
*startx*
and
*sudo startx*
but neither or them worked.

Apart from startx command, I also tried 
*system-config-display*
and 
*sudo apt-get install xserver-xorg*
which didn't work either.
I suspect that installing(or reinstalling)xserver-xorg requires internet which I probably haven't connected to yet. 

Any pointers?
Thanks in advance:popcorn:

---

### Post by Ben Wright on 2009-12-26
Could you please post the output from startx. Thanks.

---

### Post by cz8 on 2009-12-28
Yes,
Here is the Blue Screen I get when I boot my computer, the message is:

> Could not start the X
server (your graphical environment)
due to some internal error.
Please contact your system administrator
or check your syslog to diagnose.
In the meantime this display will be
disabled. Please restart GDM when
the problem is corrected.
                   <OK>


here is the output from executing *startx* command:
> mktemp: cannot create temp file /tmp/serverauth.LPTBodsNYD: Read-only file system
/usr/bin/startx: line 158: cannot create temp file for here document: Read-only file system
xauth: error in locking authority file  /home/chriszeng/.Xauthority
/usr/bin/startx: line 170: cannot create temp file for here document: Read-only file system
xauth: error in locking authority file  /home/chriszeng/.Xauthority
/usr/bin/startx: line 170: cannot create temp file for here document: Read-only file system

exec: 5: /usr/bin/X11/X: not found giving up.
xinit: No such file or directory (errno 2): unable to connect to X server
xinit: No such process (errno 3): Server error.
xauth: error in locking authority file /home/chriszeng/.Xauthority


And when I entered *system-config-display*
it just says:
> -bash: system-config-display: command not found.
I also tried to put sudo in front of it, but it gave me the same thing
> sudo: system-config-display: command not found.

Thanks in advance!!:)

---

### Post by cz8 on 2009-12-31
I read some posts on the forum, which suggests:
sudo dpkg-configure xserver-xorg

I had a go with that, but I got:
command not found

---

### Post by cz8 on 2010-01-04
LOL, seems that I will have to reinstall my ubuntu.

---

