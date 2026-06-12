---
title: "update manager application list"
date: 2010-06-18
forum: General Help
---

### Post by emanresu on 2010-06-18
i previously had Mendeley Desktop installed. i uninstalled it a few weeks ago since i don't use it much. however, when update manager ran an hour ago, it included security updates for Mendeley. is there a way to keep the update manager from trying to update apps that i've uninstalled?

---

### Post by dcstar on 2010-06-18
> **emanresu said:**
> i previously had Mendeley Desktop installed. i uninstalled it a few weeks ago since i don't use it much. however, when update manager ran an hour ago, it included security updates for Mendeley. is there a way to keep the update manager from trying to update apps that i've uninstalled?

Remove the repository.

---

### Post by Barafu Albino Cheetah on 2010-06-18
Don't know exactly this app, but it may be possible that you have deleted frontend, leaving backend, or deleted binaries, leaving data. Because that may lie in differen packages. Start Synaptic and do search to assure you have deleted everything of the app. 
Just a repository by itself will not make you to install updates if you have no packages from that repo. It is however possible, that repo has the update to the package in main repo, and this update has additional dependecies. In this case Ubuntu will try to install them all.

---

### Post by emanresu on 2010-06-18
i used Places>Search for files...   and got a list of files with mendeley in the name. i'm assuming one of these is the culprit for my current issue. should i just go through and delete all of these? if so, i only know how to do this manually, such as "sudo rm /..." if there is a better way, please let me know how.

---

