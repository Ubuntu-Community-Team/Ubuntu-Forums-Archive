---
title: "help with dapper"
date: 2006-06-01
forum: General Help
---

### Post by newhen on 2006-06-01
okay i have breezy is there a way to upgrade to dapper without downloading the huge file? cuz it takes me forever

---

### Post by rcarring on 2006-06-01
You can do a dist-upgrade. This will download several smaller files.

---

### Post by newhen on 2006-06-01
how do you do that? ps i just want it so i dont have to make a cd and everything

---

### Post by newhen on 2006-06-01
bump

---

### Post by rcarring on 2006-06-01
Look for ayisu's posts, at the bottom there is alink to his website upon which there are full details, probably better expressed than this short explanation.

1) do sudo apt-get update

2) do sudo update-manager -d

3) wait for the update manager gui to fire up and choose Dapper upgrade button.

Note: backup your data files first, and make sure you are not running any programs during the upgrade except the update-manager tool itself.

---

### Post by newhen on 2006-06-01
[QUOTE=rcarring]Look for ayisu's posts, at the bottom there is alink to his website upon which there are full details, probably better expressed than this short explanation.

1) do sudo apt-get update

2) do sudo update-manager -d

3) wait for the update manager gui to fire up and choose Dapper upgrade button.

Note: backup your data files first, and make sure you are not running any programs during the upgrade except the update-manager tool itself.[/QUOTE]
the update manger isnt wokring i might not have right version

---

### Post by rcarring on 2006-06-01
Thats the reason we were advised to run sudo apt-get update as the update manager has to be upgraded for the dist-upgrade.

Assuming you have been updating regularly you shouldn't have the disappearing xserver-xorg package, that I had to install again because during the update process to Breezy the entire package got deleted but not replaced.

Also, if you can run synaptic, it should tell you the latest version of update-manager and what version you have installed on your computer.

---

### Post by newhen on 2006-06-01
its not the right version how do i get the updated version?

---

