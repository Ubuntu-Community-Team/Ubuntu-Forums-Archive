---
title: "dpkg unrecoverable error"
date: 2012-08-26
forum: General Help
---

### Post by achim_59 on 2012-08-26
When I run update manager to install updates (and similarly with synaptic package manager) I get the following message:

> Not all changes and updates succeded.

When I check the details I see the following:

```
Reading database 55% dpkg: unrecoverable error, aborting:
 failed in buffer read(rd): files list for package "linux-headers-2.6.32-32-generic: Input/output error
E: sub-process /usr/bin/dpkg returned error code (2)
A package failed to install. Trying to recover....
```

At that point it hangs. I have tried this a couple of times times with update manager and synaptic. The message is always exactly the same. Anybody have any ideas how to get around this problem?

Thanks in advance.

Achim Schmitz

---

### Post by achim_59 on 2012-12-20
I'm underwhelmed by the responses to my query, though not overly surprised.

Anyway, the problem in this case turned out to be hardware. My hard drive was slowly but surely dying and dpkg couln't read the package data anymore. I'd been having trouble with dpkg on and off for a couple of months. This latest problem was apparently the terminal stage.

I have now reinstalled on a new HD... 

Achim

---

