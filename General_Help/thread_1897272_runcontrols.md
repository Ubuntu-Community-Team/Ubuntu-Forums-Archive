---
title: "runcontrols"
date: 2011-12-18
forum: General Help
---

### Post by Synoc on 2011-12-18
I widely accept that Ubuntu has three run levels off, GUI, and Reboot. 2-5 are all the same. that said:
I want to be able to disable the SSH service on startup, I cannot find anything about ssh in /etc/rc2.d (default run level for Ubnutu) what tells Ubuntu to start it in the first place?

BTW "service ssh stop" and "service ssh start" as well as "service sshd start" and service sshd stop" return the same error "unrecognized service"
yet I CAN ssh out...

---

### Post by MartijnNL on 2011-12-19
Are you talking about an SSH server (sshd) running on the computer allowing you to ssh into the computer from another one?
Or do you mean the SSH client (ssh) which allows you to login to another computer from the one you are referring too. (I asume the latter as you are talking about ssh-ing out.)

The client doesn't run as a service. It just runs when you call ssh on the commandline. If you want to be unable to use ssh on the system, you should uninstall it.

If you mean the server, you will need to edit /etc/init/ssh.conf (the file for the upstart system Ubuntu uses.
Edit the line:

```
stop on runlevel [!2345]
```

and remove the '2'.

---

### Post by Synoc on 2011-12-19
I did in fact mean the server. Thank you, I have 10.10 and the server runs be default. on my 10.04 PC it does not. so I had no idea how to fix the problem. I want it to be stopped by default but I want to be able to start it so I can ssh into the 10.04 PC to fix things, admin into it, etc.

if I remove stop on run level 2, it will start it then? and if so how do I stop it again, if Ubuntu doesn't seem to recognize sshd as a service and does that really say "Stop on NOT 2, 3, 4, and 5?" if so that's just wierd.

The other question is... is server even installed on 10.04 by default? since I don't have /etc/init/ssh.conf on my 10.04 machine

---

### Post by MartijnNL on 2011-12-20
Assuming you have a desktop Ubuntu then no, the OpenSSH server is not installed by default. And if I remember correctly on Ubuntu Server installs you still have to select it manually.

sshd is a service, by the way, but ssh isn't. But I guess it isn't installed on your system.

Yes it does mean "Stop on NOT 2, 3, 4, and 5". It stops the server on runlevels 0,1 en 6. (Halt, single user mode and reboot). It also says 'start on filesystem' which means it gets started when the last filesystem is mounted during boot. (Except when the system goes into runlevel 1. There is no boot in 0 and 6 obviously.)

By removing the 2 it's also not started in the default runlevel.

---

### Post by Synoc on 2011-12-20
Thank you

---

