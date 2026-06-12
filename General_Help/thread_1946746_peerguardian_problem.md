---
title: "peerguardian problem"
date: 2012-03-25
forum: General Help
---

### Post by DataSpy on 2012-03-25
I have peerguardian successfully install but I get errors when starting it :(

The error message:
> 
Failed executing command(s). The following output was given:
 "* Starting PeerGuardian Linux pgld ...fail!" 

You can also check "/var/log/pgl/pgld.log" or "/var/log/pgl/pglcmd.log" for more details.


The log file /var/log/pgl/pgld.log output is:
> 
Mar 25 10:56:19 ERROR: Error requesting name Connection ":1.49" is not allowed to own the service "org.netfilter.pgl" due to security policies in the configuration file.

Mar 25 10:56:19 ERROR: Cannot initialize D-Bus
Mar 25 10:56:25 ERROR: Error requesting name Connection ":1.50" is not allowed to own the service "org.netfilter.pgl" due to security policies in the configuration file.

Mar 25 10:56:25 ERROR: Cannot initialize D-Bus


This is what I get when I run it from the command line:
> 
dataspy@laptop-ubuntu:~$ sudo pgl-gui
[sudo] password for dataspy: 
** Debug: Graphical Sudo:  "" 
** Debug: virtual void ProcessT::run() Executing command "which kdesudo" () ... 
** Debug: "/usr/bin/kdesudo" 
** Debug: virtual void ProcessT::run() Command execution finished. 
** Debug: Graphical Sudo:  "" 
** Debug: virtual void ProcessT::run() Executing command "which kdesudo" () ... 
** Debug: "/usr/bin/kdesudo" 
** Debug: virtual void ProcessT::run() Command execution finished. 
** Debug: Connection to DBus was successful. 
** Debug: virtual void ProcessT::run() Executing command "which gksudo" () ... 
** Debug: virtual void ProcessT::run() Executing command "which gksudo" () ... 
** Debug: "/usr/bin/gksudo" 
** Debug: virtual void ProcessT::run() Command execution finished. 
** Debug: "/usr/bin/gksudo" 
** Debug: virtual void ProcessT::run() Command execution finished. 
** Debug: virtual void ProcessT::run() Executing command "which kdesu" () ... 
** Debug: virtual void ProcessT::run() Executing command "which kdesu" () ... 
** Debug: "" 
** Debug: virtual void ProcessT::run() Command execution finished. 
** Debug: "" 
** Debug: virtual void ProcessT::run() Command execution finished. 
** Debug: virtual void ProcessT::run() Executing command "which gksu" () ... 
** Debug: virtual void ProcessT::run() Executing command "which gksu" () ... 
** Debug: "/usr/bin/gksu" 
** Debug: virtual void ProcessT::run() Command execution finished. 
** Debug: "/usr/bin/gksu" 
** Debug: virtual void ProcessT::run() Command execution finished.


Any help is greatly appreciated!!!!

---

### Post by jre on 2012-03-30
Hmm, the "security policy" relates to pgld trying to connect to dbus.
Did you change anything about the dbus security policy?
Do you run any security hardening software (which was not installed per default).
On which distribution have you installed pgl?

For now, I don't know how to fix that. I will look into this, but probably not before May, sorry.

I filed this as bug at our project:
[https://sourceforge.net/tracker/?func=detail&aid=3513330&group_id=131687&atid=721926](https://sourceforge.net/tracker/?func=detail&aid=3513330&group_id=131687&atid=721926)

You may disable dbus, but then you can't use the GUI (the daemon pgld and pglcmd will still be running and working though). Just set in /etc/pgl/pglcmd.conf
```
DBUS="0"
```

---

### Post by Darkblood on 2012-04-07
Hi, 

Take a look at my comment here:
[http://sourceforge.net/tracker/?func=detail&aid=3513330&group_id=131687&atid=721926](http://sourceforge.net/tracker/?func=detail&aid=3513330&group_id=131687&atid=721926)

---

### Post by whistlerspa on 2012-05-06
How do you install it the tar.gz extrasction won't run on either my desktop or netbook:(

---

### Post by jre on 2012-05-10
> **whistlerspa said:**
> How do you install it the tar.gz extrasction won't run on either my desktop or netbook:(

Have you tried the precompiled packages? See [https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock)
For now, probably try the sources.list entry from natty.

---

### Post by whistlerspa on 2012-05-13
code?

I'm sorry but i don't know what you mean by this. I was unable to add Moblock via Synaptic and the .tar.gz file resists all efforts to install it. None of the usual commands ./configure make or make install work at all.

---

### Post by jre on 2012-05-13
code? This is my signature!

If you want to continue trying the tar.gz please exactly tell what you downloaded and what you tried to unpack. But I don't recommend that you try it this way!

I think I already told you what to do [in your other thread]("http://ubuntuforums.org/showpost.php?p=11923864&postcount=5"). If you need help tell me what you did so far (don't tell long stories, but the commands or exact actions that you did). If you fail somewhere show me the error's that you get.

---

