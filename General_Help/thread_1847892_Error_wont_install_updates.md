---
title: "Error wont install updates??"
date: 2011-09-21
forum: General Help
---

### Post by blackone86 on 2011-09-21
So my update manager keeps popping up and asking me to install updates. Everytime i click install updates this comes up.

Note: After doing an upgrade i was able to knock down 47 updates to about 7 or so but this is till coming up for the last 7. 

**The action would require the installation of packages from not authenticated sources**. and the only option is to click close. 

So i tried sudo apt-get update and it comes up with this
[B]W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 61E091672E206FF0
[/B]
Thanks

---

### Post by josephmills on 2011-09-21
seems like the server is not responding to you open terminal and type in ```
sudo apt-get update --fix-broken --fix-missing
```
and paste here thanks 
joseph

---

### Post by blackone86 on 2011-09-21
ran it and same exact error came up.
[B]W: GPG error: [http://ppa.launchpad.net]("http://ppa.launchpad.net/")  natty Release: The following signatures couldn't be verified because  the public key is not available: NO_PUBKEY 61E091672E206FF0
[/B]

---

### Post by josephmills on 2011-09-21
take that out of your /ect/apt/sourcelist file or comment it out with ##

---

### Post by blackone86 on 2011-10-04
> **josephmills said:**
> take that out of your /ect/apt/sourcelist file or comment it out with ##

Sorry for being a noob, but im not that familiar with this stuff. What exactly do u mean by that??

---

### Post by wildmanne39 on 2011-10-04
Hi, open synaptic then click on settings, repositories, in the window that opens under other software you will see ppa's find the one that you have listed with the error in this thread and uncheck it in synaptic, then run:
```
sudo apt-get update && sudo apt-get upgrade
```
Thank you

---

### Post by blackone86 on 2011-10-04
Ok, i did what you suggested, but theres a problem. In repositories theres around 15 items with check boxes. 8 of those 15 all start with [http://ppa.launchpad.net/](http://ppa.launchpad.net/) and then continue on differently after the fw slash?

---

### Post by wildmanne39 on 2011-10-04
Hi, it is most likely one you added recently, have you added one since the last time you tried to update?

Also you could uncheck them one at a time until you do not get errors running that command.

When you uncheck them you have to close synaptic completely so you can run that command.
Thank you

---

### Post by pr3zident on 2011-10-04
> **blackone86 said:**
> Ok, i did what you suggested, but theres a problem. In repositories theres around 15 items with check boxes. 8 of those 15 all start with [http://ppa.launchpad.net/](http://ppa.launchpad.net/) and then continue on differently after the fw slash?

Try this : [http://www.liberiangeek.net/2010/10/fix-requires-installation-untrusted-packages-error-ubuntu-10-10-maverick-meerkat/](http://www.liberiangeek.net/2010/10/fix-requires-installation-untrusted-packages-error-ubuntu-10-10-maverick-meerkat/)

---

### Post by blackone86 on 2011-10-04
> **pr3zident said:**
> Try this : [http://www.liberiangeek.net/2010/10/fix-requires-installation-untrusted-packages-error-ubuntu-10-10-maverick-meerkat/](http://www.liberiangeek.net/2010/10/fix-requires-installation-untrusted-packages-error-ubuntu-10-10-maverick-meerkat/)

This worked. Very Simple fix just didnt know where to look. 

Thank You

---

