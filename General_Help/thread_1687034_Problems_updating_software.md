---
title: "Problems updating software"
date: 2011-02-13
forum: General Help
---

### Post by maddbaron on 2011-02-13
I went to update my software and I saw the system wants to remove three programs. I googled them and they seem important but I can't update without removing them so I'm stuck.  I've included a screen shot of the items the system wants to remove. 

Also for the past month I haven't been able to update something called seahorse, the system says it's a broken package but I don't know how to fix it. Is this an essential program or can I un-install it?

I want to upgrade to 10.10 but I am reading how all updates must be done before and these issues are holding me back.

help please

---

### Post by ajgreeny on 2011-02-13
For the seahorse problem I suggest you use synaptic and go to Edit -> Fix broken packages and let the system work for you.  It may remove seahorse, but you can try re-installing it afterwards.

Then do your full system update, again using synaptic if you want, but make sure you reload (top left icon) first.

Come back again if it still tells you it is removing packages.

---

### Post by maddbaron on 2011-02-13
> **ajgreeny said:**
> For the seahorse problem I suggest you use synaptic and go to Edit -> Fix broken packages and let the system work for you.  It may remove seahorse, but you can try re-installing it afterwards.

Then do your full system update, again using synaptic if you want, but make sure you reload (top left icon) first.

Come back again if it still tells you it is removing packages.

for seahorse it says there are two version available 2.30 and 2.32 I tried forcing version 2.32 but it still won't update and is being held back.  also says I'm missing glib library that isn't listed in any of the not installed programs available.

I reloaded but the system still wants remove the 3 packages in the screen-shot.

the programs it wants to un-install deal with viewing and matching apps to the desktop as well as the appmenu-indicator if they get removed can I reinstall them?

---

### Post by ajgreeny on 2011-02-13
Seahorse 2.30 is the default version for Ubuntu 10.04, so go for that to start.

Where did the bamfdaemon and libbamf0 come from?  They are not in the repos and that is why the system is trying to remove them.

Before you do an online upgrade of distro version it is best to disable all ppa repos, and probably also remove packages that are not in repos of any kind, but that that you have installed manually, as they can upset the upgrade process.

---

