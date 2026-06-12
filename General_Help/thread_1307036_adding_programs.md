---
title: "adding programs"
date: 2009-10-30
forum: General Help
---

### Post by frank_zito on 2009-10-30
i'm a totally new user and i'm having some issues with adding files. when i go to the add/remove tab, i get this error:

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.


when i go to the synaptic package manager it just shuts down on me. what can i do to fix this?

---

### Post by mac9416 on 2009-10-30
Hello, and welcome to Ubuntu!

Try going to System > Administration > Synaptic Package Manager and clicking Edit > Fix Broken Packages.
Then close Synaptic and go to Applications > Accessories > Terminal. Copy and paste the following commands into the terminal (minus the "$ "):

```
$ sudo apt-get update
$ sudo apt-get install -f
```

That should do the trick.

---

