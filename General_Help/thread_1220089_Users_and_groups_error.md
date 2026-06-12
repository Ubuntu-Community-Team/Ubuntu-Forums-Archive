---
title: "Users and groups error"
date: 2009-07-22
forum: General Help
---

### Post by stoneage on 2009-07-22
I wanted to remove my user from one group and add it to another with System -> Admin -> Users and Groups. I successfully removed it from the first group, but now when I try to add it to a group clicking on Unlock in the User Settings panel results in the following error:-
Could not Authenticate An unexpected error has occurred.

This is before entering the password.
I tried usermod, and it seems to work, but I don't know how to resolve the User Settings erro. It persists even after a restart.

Anybody know what went wrong?

Ubuntu 8.10 64 bit clean install

I found this in auth.log, it seems relevant:-
> Jul 22 17:05:47 organic-desktop gdm[5569]: gnome-keyring-daemon: couldn't lookup keyring component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: Invalid MIT-MAGIC-COOKIE-1 keyAutolaunch error: X11 initialization failed.
Jul 22 17:05:48 organic-desktop gdm[5569]: )gnome-keyring-daemon: couldn't lookup ssh component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: Invalid MIT-MAGIC-COOKIE-1 keyAutolaunch error: X11 initialization failed.
Jul 22 17:05:48 organic-desktop gdm[5569]: )gnome-keyring-daemon: couldn't lookup pkcs11 component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: Invalid MIT-MAGIC-COOKIE-1 keyAutolaunch error: X11 initialization failed.
Jul 22 17:05:48 organic-desktop gdm[5569]: )
Jul 22 17:08:06 organic-desktop sudo:  organic : TTY=pts/0 ; PWD=/home/organic ; USER=root ; COMMAND=/usr/sbin/usermod admin -aG organic

---

### Post by bacil on 2009-07-22
can you post content of /etc/passwd and /etc/group ?

you can change these by manualy editing those files

---

### Post by stoneage on 2009-07-22
Hi, and thanks for the quick reply.
I was hoping there would be a text config way of doing it, but can you suggest a way to address the authentication error? Is the problem that I mistakenly removed myself from the admin group?

/etc/passwd:-
```

```



/etc/group:-
```

```

---

### Post by stoneage on 2009-07-22
ok, I'm fixed.....

Yes removing myself from the admin group was indeed a stupid thing to do :oops:

I followed this here:- [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

Boot into recovery mode
Drop to root shell prompt
enter 'adduser username admin'
Exit
Resume normal boot

Sorry to be a nuisance, but also mighty grateful for the support. If there was nowhere to go I would have been stuck.

---

