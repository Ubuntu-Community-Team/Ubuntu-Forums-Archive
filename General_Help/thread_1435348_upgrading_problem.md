---
title: "upgrading problem"
date: 2010-03-21
forum: General Help
---

### Post by nischalinn on 2010-03-21
I've***openoffice.org 3.0**.* I tried to upgrade it to oog3.1 via terminal by the command 

**sudo apt-get update && sudo apt-get install openoffice.org 3.1**

my terminal shows; 

_the lines above these are not shown_
[B]
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 3.1[/B]

What could be the problem?

I got the same results when I tried the commands with firefox 3.5.

---

### Post by DawieS on 2010-03-21
Open **Update Manager** and click on **Settings**. At **Software Sources**, at **Other Software**, click on **Add**, then fill in:

Type:
Binary
Uri:
[http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu)
Distribution:
karmic
Components:
main

The next time you update, Open Office will be updated. (You may want to un-check it again after the update, or **Update Manager** will complain about something each time, I cannot remember what...):grin:

---

### Post by MelDJ on 2010-03-21
or try the link in my sig

---

