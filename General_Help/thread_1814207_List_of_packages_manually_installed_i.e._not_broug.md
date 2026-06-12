---
title: "List of packages manually installed i.e. not brought in as dependency"
date: 2011-07-29
forum: General Help
---

### Post by danielsbrewer on 2011-07-29
Is there any way that I can get a list of packages (on the command line) that have been installed manually i.e. all those that haven't been installed as dependencies?

I think this must be possible as apt seems to know which dependency packages are no longer required i.e. apt-get autoremove

Thanks

---

### Post by ajgreeny on 2011-07-29
There are plenty of logs in verious places that tell you exactly what has been installed after the OS was first installed, but I am not sure you can separate out those that were installed because you asked for them to be, and those that the system needed to add in order to install what you asked for.

Have a look at var/log/dpkg.log though I do not think it will help with your specific needs.

---

### Post by nothingspecial on 2011-07-29
If you have used only apt-get then

```
i=$(grep "apt-get install" /var/log/apt/history.log); echo "${i//Commandline: apt-get install /}" | sed '/^-f/d'
```
 
That is a hack. It puts all the lines that start have "apt-get install" into a variable, removes the bit of the line you don't need and removes any line that is only -f (just in case you have ever apt-get install -f).

It takes no account of aptitude, synaptic or software center. It also assumes you have only ever left one space after install, and doesn't take into account anything you have subsequently removed.

Play with it, it's just off the top of my head :P

---

