---
title: "help"
date: 2010-10-27
forum: General Help
---

### Post by hotshot247 on 2010-10-27
hey, actually i have a couple of questions about ubuntu. i'm using ubuntu 10.10. 

1. why is it that when i add a ppa to the repository and then i type sudo apt-get update, it has an error for that ppa but i can still install it? deluge is the main one that does that. 

2. when i install apps, it tells me to use apt-get autoremove to remove unused packages but i need some of them like java etc. how do i take some apps off of the autoremove list?

thanks for all your help.

---

### Post by WorMzy on 2010-10-27
1. Have you added the pgp key for the repository? You will continue to get a warning that the key cannot be found if you don't add the key to your keyring; the key is used to make sure that the files you're downloading have been added by who should have added them. It's a security feature to help prevent someone pretending to be someone else and uploading malicious packages to a repository.

2. Manually install them. Autoremove should only list packages which were dragged in as dependencies, but are no longer required. Do a ```
sudo apt-get install <package name>
``` and Ubuntu will stop seeing it as an unneeded dependency.

---

### Post by hotshot247 on 2010-10-27
> **WorMzy said:**
> 1. Have you added the pgp key for the repository? You will continue to get a warning that the key cannot be found if you don't add the key to your keyring; the key is used to make sure that the files you're downloading have been added by who should have added them. It's a security feature to help prevent someone pretending to be someone else and uploading malicious packages to a repository.

2. Manually install them. Autoremove should only list packages which were dragged in as dependencies, but are no longer required. Do a ```
sudo apt-get install <package name>
``` and Ubuntu will stop seeing it as an unneeded dependency.


on #1, i was adding deluge in the terminal by typing: ppa:deluge-team/ppa and that would add it and add the key as well, but i found out that deluge don't have a program for 10.10 yet so i just went to launchpad and found out how to add deluge from lucid and it works. 

on #2, for some reason, i tried to install them but it said that i already had the newest version of them all. should i uninstall them with autoremove and reinstall them, do you think that will fix it?

---

### Post by sikander3786 on 2010-10-27
#1 is already solved.

#2 You don't need the dependencies of programs you already uninstalled. I safely use autoremove to remove all un-needed packages and never had any problems.

---

### Post by WorMzy on 2010-10-27
> **hotshot247 said:**
> on #1, i was adding deluge in the terminal by typing: ppa:deluge-team/ppa
Was the the whole of the command? Because that wouldn't add the key. If you did, then what message are you getting when updating?

> **hotshot247 said:**
> on #2, for some reason, i tried to install them but it said that i already had the newest version of them all. should i uninstall them with autoremove and reinstall them, do you think that will fix it?

It should have said that it was flagging them as "manually installed" or something similar; if it didn't do this then you can try the autoremove/reinstall method.

---

