---
title: "can't run synaptic package manager"
date: 2011-10-06
forum: General Help
---

### Post by robcul on 2011-10-06
I interrupted an install of adobe flash because it was going to take 95 minutes. Now I can't run synaptic package manager. When I try I am given this error message:
[INDENT]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/INDENT]

When I run this command nothing happens. I am the administrator. I tried it without the "sudo," and still nothing happens.

What do I need to do?

Thanks,
Rob

---

### Post by wolfen69 on 2011-10-06
Try 
```
sudo apt-get install -f
```
then 
```
sudo dpkg --configure -a
```
then 
```
sudo apt-get update
```

---

### Post by robcul on 2011-10-06
Thanks for the reply. I ran those commands and nothing visible happened. Also trying to run synaptic package manager still gets the same error message.

---

### Post by kalehrl on 2012-02-16
Have you solved your problem?
This morning I ran sudo apt-get update && sudo apt-get upgrade and it started downloading adobe flash player and I let it finish. I didn't interrupt. When I restarted my lubuntu laptop I could no longer run synaptic from the menu. I can start it with:
> synaptic
after logging as super user and it works normally.
It just wont start from Start - System Tools - Synaptic.
I tried those commands above but still the same.

---

