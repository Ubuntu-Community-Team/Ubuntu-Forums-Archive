---
title: "which repo am I apt-getting from?"
date: 2009-07-17
forum: General Help
---

### Post by PGScooter on 2009-07-17
Hi, how can I tell which repository I am installing a piece of software from when I use the command ```
apt-get install packagename
``` ?

When there is the same packagename in two different repositories, how do I search so I can see them both and how do I specify which one I want to get?

Thank you!

---

### Post by vinutux on 2009-07-17
> **PGScooter said:**
> Hi, how can I tell which repository I am installing a piece of software from when I use the command ```
apt-get install packagename
``` ?

When there is the same packagename in two different repositories, how do I search so I can see them both and how do I specify which one I want to get?

Thank you!

simple **[COLOR="DarkGreen"]System>administration>synaptic[/COLOR]** select pakage ctrl+o or **pakage menu>properties**

if you have same pakage from two repos choose in synaptic **[COLOR="DarkGreen"]pakage menu>Foce version[/COLOR]**

.

---

### Post by PGScooter on 2009-07-17
thank you, that is very useful to know.

Is there anyway to do this from the commandline?

---

### Post by darolu on 2009-07-17
> **PGScooter said:**
> thank you, that is very useful to know.

Is there anyway to do this from the commandline?

```
man apt-get
```

---

### Post by VCoolio on 2009-07-17
```
apt-cache policy <package>
```

Returns for me with dillo (for which I have a repository added):
```
dillo:
  Installed: 2.1-0+dillo1
  Candidate: 2.1.1-0+dillo1~jaunty1
  Version table:
     2.1.1-0+dillo1~jaunty1 0
        500 http://ppa.launchpad.net jaunty/main Packages
 *** 2.1-0+dillo1 0
        100 /var/lib/dpkg/status
     0.8.6-3 0
        500 http://nl.archive.ubuntu.com jaunty/universe Packages
```

---

### Post by vinutux on 2009-07-17
> **VCoolio said:**
> ```
apt-cache policy <package>
```

Returns for me with dillo (for which I have a repository added):
```
dillo:
  Installed: 2.1-0+dillo1
  Candidate: 2.1.1-0+dillo1~jaunty1
  Version table:
     2.1.1-0+dillo1~jaunty1 0
        500 http://ppa.launchpad.net jaunty/main Packages
 *** 2.1-0+dillo1 0
        100 /var/lib/dpkg/status
     0.8.6-3 0
        500 http://nl.archive.ubuntu.com jaunty/universe Packages
```

Thaks.........

---

### Post by PGScooter on 2009-07-17
> **darolu said:**
> ```
man apt-get
```
I read through it and couldn't find anything. A search for "repo" in the man page brings up few and irrelevant results.

> **VCoolio said:**
> ```
apt-cache policy <package>
```

Returns for me with dillo (for which I have a repository added):
```
dillo:
  Installed: 2.1-0+dillo1
  Candidate: 2.1.1-0+dillo1~jaunty1
  Version table:
     2.1.1-0+dillo1~jaunty1 0
        500 http://ppa.launchpad.net jaunty/main Packages
 *** 2.1-0+dillo1 0
        100 /var/lib/dpkg/status
     0.8.6-3 0
        500 http://nl.archive.ubuntu.com jaunty/universe Packages
```

Ah! I use that command all the time to quickly see which version I have installed, but I guess I never paid attention to the ppa line. Thank you.

---

