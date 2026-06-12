---
title: "Generating List of Installed Packages."
date: 2010-10-29
forum: General Help
---

### Post by coffeecat on 2010-10-29
I would like to generate a list of packages I have installed on my system, but without the dependencies. This is so that I can use the list to install all my regular apps on a new install - the package manager will take care of the dependencies. But I want to weed out apps I don't need, or tried and didn't like. If I manually remove the unwanted stuff, I'll still have their dependencies as cruft and bloat in the package list - which will be a nightmare to sift through and sort out. 

The problem is that...

```
dpkg --get-selections
```...and...

```
dpkg --list
```... generate a whopping great list of everything I have installed, all their dependencies and seemingly all the stuff that comes with a default install. Trawling through the history in Synaptic is equally unrewarding. I get to see the dependencies in addition to  what I primarily selected.

Any thoughts?

---

### Post by matt_symes on 2010-10-29
Hi

That is a strange oversite. Apt-get logs to the dpkg logs and they log everything.

/root./synaptic/logs has synaptic's logs

Maybe something in this thread will help

[http://ubuntuforums.org/showthread.php?t=1600285](http://ubuntuforums.org/showthread.php?t=1600285)

Kind regards

---

### Post by coffeecat on 2010-10-29
> **matt_symes said:**
> That is a strange oversite. Apt-get logs to the dpkg logs and they log everything.

Well - perhaps an oversight, but I have sympathy for the devs who might try to get this detail to work. You'd have to log the primary apt-get install or Synaptic choice separately from the dependencies. Might be fun.

Anyway, thanks for the links. 'cat /var/log/dpkg.log | grep "\ install\ " ' gets nearest to what I want, but I'll still have to eyeball the list for recognisable apps and packages that I want. But I'm certainly a step closer.

Thanks again.

---

