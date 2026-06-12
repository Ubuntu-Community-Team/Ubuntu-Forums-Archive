---
title: "How do I disable services in 10.10?"
date: 2010-12-01
forum: General Help
---

### Post by HowlingMad on 2010-12-01
Just curious - how do I disable services that don't appear in System->Preferences->Startup Applications?

I understand that the services command can start/stop/ give status, but don't know how to disable...

Was kind of used to the old sysV init setup so if anyone wants to explain the new arrangement, please feel free.

Cheers,

HM

---

### Post by NCLI on 2010-12-01
> **HowlingMad said:**
> Just curious - how do I disable services that don't appear in System->Preferences->Startup Applications?

I understand that the services command can start/stop/ give status, but don't know how to disable...

Was kind of used to the old sysV init setup so if anyone wants to explain the new arrangement, please feel free.

Cheers,

HM

Hey HM,

All services which run at startup should be in /etc/init.d, and some of the /etc/rc*.d directories. If you find the service you want to disable in the /etc/init.d directory, you can just remove all links to it from the various rc*.d folders.

---

### Post by sisco311 on 2010-12-01
> **HowlingMad said:**
> Just curious - how do I disable services that don't appear in System->Preferences->Startup Applications?

I understand that the services command can start/stop/ give status, but don't know how to disable...

Was kind of used to the old sysV init setup so if anyone wants to explain the new arrangement, please feel free.

Cheers,

HM

Some services still use the Sys-V style scripts, you can disable them by removing their symlinks from /etc/rc*.d directories (either manually or with a tool like update-rc.d).

Upstart jobs are located in /etc/init. To disable an Upstart job simply comment out its **start on** stanza. i.e. to disable cups, edit /etc/init/cups.conf to look like this:
```

# cups - CUPS Printing spooler and server

description     "CUPS printing spooler/server"
author          "Michael Sweet <msweet@apple.com>"

**#**start on (filesystem
**#**          and (started dbus or runlevel [2345])
**#**          and stopped udevtrigger)
stop on runlevel [016]
...

```

See: [http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html)

In Ubuntu 10.10 you can use jobs-admin, a GUI tool for managing services.

---

### Post by eexpress on 2011-02-12
jobs-admin broken. bad python.

before 10.10, you can do this
```
sudo service xxxxxx stop
sudo update-rc.d -f xxxxxx remove
```

---

### Post by bhy on 2011-03-01
Do I understand it correctly, that as long as jobs-admin is broken the only way to disable system services is by editing the upstart config files? Newbie users won't be happy about this.

---

### Post by standingfire on 2011-03-01
I use bum.
sudo apt-get install bum

this will enable you to start or stop some of the major services that you may be concerned about. 

You could also use chkconfig.... not sure what the install string for that is.

---

### Post by bhy on 2011-03-02
Thank you. Correct me if I'm wrong, but as far as I know, both bum and chkconfig, just like sysv-rc-conf, only configure the SysV-based services, but not the ones that are managed by upstart.

---

### Post by dekatrion on 2011-03-10
The post by sisco is right, but I must remember that any updates to these files will conflict with newer versions when these services packages get updated, making this whole situation even more confusing or harder to maintain (how to ask an user to actually merge two service files?)

Upstart is really good, but the lack of disabling the services in a straightforward way is really annoying to me.

---

