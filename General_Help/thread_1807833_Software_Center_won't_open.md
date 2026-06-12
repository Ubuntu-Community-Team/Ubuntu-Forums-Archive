---
title: "Software Center won't open"
date: 2011-07-19
forum: General Help
---

### Post by umwhat on 2011-07-19
Whenever I try to start of SC, nothing happens. I tried rebooting, and nothing. When I try to update from the terminal, I get: 

[INDENT]user@user-laptop:~$ sudo apt-get update
E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/bjfs-ppa-maverick.list
E: The list of sources could not be read.
[/INDENT]
And this is what I get from update manager:
[INDENT]Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/bjfs-ppa-maverick.list'[/INDENT]

Not really sure what happened. I booted up W7 for a few minutes, booted up Ubuntu again, tried to install Emesene2 and then this happened.

---

### Post by Monotoko on 2011-07-19
Hi :)

Please post the output of
```
nano /etc/apt/sources.list.d/bjfs-ppa-maverick.list
```

Basically we need to see what is in that file that is causing the package updater to fail.

---

### Post by umwhat on 2011-07-19
Hey! :D

Here it is:
deb [http://ppa.launchpad.net/bjfs/ppa/ubuntu](http://ppa.launchpad.net/bjfs/ppa/ubuntu) maverick main
deb-src [http://ppa.launchpad.net/bjfs/ppa/ubuntu](http://ppa.launchpad.net/bjfs/ppa/ubuntu) maverick main
ain

---

### Post by Monotoko on 2011-07-19
Not quite sure what that "ain" line is, mine doesn't have it. Just remove the line and then run ```
sudo apt-get update
```

It should then hopefully be as good as new :)

---

### Post by umwhat on 2011-07-19
woo, it worked! Thank you! :)

---

