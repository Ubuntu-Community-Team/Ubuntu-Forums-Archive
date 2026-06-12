---
title: "remove proxy via terminal"
date: 2012-10-02
forum: General Help
---

### Post by teuma86 on 2012-10-02
Hi all

I have a ubuntu box and I installed privoxy to use my machine as a proxy to test websites from different regions.

Decided against this and removed via purge but remembered the global proxy settings are still set.

Problem: I am SSHed into the box as i am not near the box and I need to install some things but cant as its looking at localhost (via proxy)

I have tried the following

export http_proxy=""

removing the lines in
/etc/environment

and finally
gsettings set org.gnome.system.proxy.mode 'none'

I get the following error on the last line

WARNING **: Command line `dbus-launch --autolaunch=e1614808267a12940aef87360000000e --binary-syntax --close-stderr' exited with non-zero exit status 1: Autolaunch error: X11 initialization failed.\n


Still looking at localhost
How do I remove the damn proxy via terminal

---

### Post by lechien73 on 2012-10-02
Hi and welcome to the forums,

I presume that you have a GUI running on the box, but you're using an ssh terminal to access it?

If so, you could try the following before running gsettings:

```
sessionfile=`find "${HOME}/.dbus/session-bus/" -type f`
export `grep "DBUS_SESSION_BUS_ADDRESS" "${sessionfile}" | sed '/^#/d'`
```

Then try:

```
gsettings set org.gnome.system.proxy.mode 'none'
```

again.

---

### Post by teuma86 on 2012-10-02
Cheers

DOne and I get the following error

webserver@Jamie-WebServer:~$ sessionfile=`find "${HOME}/.dbus/session-bus/" -type f export `grep "DBUS_SESSION_BUS_ADDRESS" "${sessionfile}" | sed '/^#/d'


find: paths must precede expression: export
Usage: find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]
DBUS_SESSION_BUS_ADDRESS: command not found

---

### Post by lechien73 on 2012-10-02
Sorry, I should have made it clear that those are two lines of code.

So, firstly:

```
sessionfile=`find "${HOME}/.dbus/session-bus/" -type f`
```

Then:

```

export `grep "DBUS_SESSION_BUS_ADDRESS" "${sessionfile}" | sed '/^#/d'`
```

Make sure to include the backquote ` at the end of each line as well :)

---

### Post by teuma86 on 2012-10-02
Got the following

gsettings set org.gnome.system.proxy mode 'none'

** (process:2586): WARNING **: Could not connect: Connection refused

** (process:2586): WARNING **: Could not connect: Connection refused

---

### Post by lechien73 on 2012-10-02
Ok, if you're accessing from an Ubuntu machine, then try this instead. On the remote machine, type:

```
nano ~/proxychange.sh
```

In the new file, paste the following:

```
#!/bin/bash

sessionfile=`find "${HOME}/.dbus/session-bus/" -type f`

export `grep "DBUS_SESSION_BUS_ADDRESS" "${sessionfile}" | sed '/^#/d'`

gsettings set org.gnome.system.proxy.mode 'none'
```

Close and save the file. Then:

```
chmod +x ~/proxychange.sh
```

Now disconnect your ssh session and, from your local Ubuntu machine, issue the command:

```
ssh -X username@ip-address ~/proxychange.sh
```

This will attach your remote machine to a local X server and run the command. Hopefully that will change the proxy settings for you.

---

### Post by teuma86 on 2012-10-02
No, im using windows with putty.

Dont worry, something else has come up, so I will be home by the time I can look at my box again, so then I can go via the gui not SSH Terminal

Thanks for your help tho

---

### Post by teuma86 on 2012-10-03
Got home, logged straight onto the box itself. Settings ->proxy ->none.

All working now

Cheers for your help tho lechien73

---

### Post by alluremedspa123 on 2012-10-03
The configuration information is saved  under .gconf (front end GconfEdior), which is a system for storing  application preference in Gnome (think Registry for Windows PC).

---

### Post by Prospero2006 on 2012-10-03
Hello,
Glad to hear you solved it. 
I believe the command is:
```
export http_proxy=none
```

---

