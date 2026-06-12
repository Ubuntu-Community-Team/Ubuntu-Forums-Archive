---
title: "Can't open Synaptic Package Manager and can't play mp4 vids with video player"
date: 2011-06-10
forum: General Help
---

### Post by S Man on 2011-06-10
When I try to open SPM I enter my password and I get this message: Unable to get exclusive lock. This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first.

I don't understand because I will have no other program running and I make sure of it.

Then when I try playing mp4 with video player I get this message: The required software to play this file is not installed. You need to install suitable plugins to play media files. Do you want to search for a plugin that supports the selected file?

The search will also include software which is not officially supported.

So I happily click search, it finds the required software and asks if i want to install, I click to install, put in my password, but nothing ever gets installed. It's just idle. 

Any help? I'm using Ubuntu 11.04

---

### Post by plucky on 2011-06-11
> **S Man said:**
> When I try to open SPM I enter my password and I get this message: Unable to get exclusive lock. This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first.

I don't understand because I will have no other program running and I make sure of it.

Then when I try playing mp4 with video player I get this message: The required software to play this file is not installed. You need to install suitable plugins to play media files. Do you want to search for a plugin that supports the selected file?

The search will also include software which is not officially supported.

So I happily click search, it finds the required software and asks if i want to install, I click to install, put in my password, but nothing ever gets installed. It's just idle. 

Any help? I'm using Ubuntu 11.04

You could try deleting the "lock" file with ```
sudo rm /var/lib/dpkg/lock
``` and then see if you can now open Synaptic Package Manager.

Have you installed "Ubuntu-restricted-extras"?

Good Luck

---

### Post by wildmanne39 on 2011-06-11
> **S Man said:**
> When I try to open SPM I enter my password and I get this message: Unable to get exclusive lock. This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first.

I don't understand because I will have no other program running and I make sure of it.

Then when I try playing mp4 with video player I get this message: The required software to play this file is not installed. You need to install suitable plugins to play media files. Do you want to search for a plugin that supports the selected file?

The search will also include software which is not officially supported.

So I happily click search, it finds the required software and asks if i want to install, I click to install, put in my password, but nothing ever gets installed. It's just idle. 

Any help? I'm using Ubuntu 11.04
Hi, it sounds like you may have a broken package since that package did not finish installing. Sometime you have to restart the system to get it to get rid of the other application that is running that is preventing synaptic from working, restart
and then try these commands.
```
sudo rm -r /var/lib/apt/lists/* -vf
```
```
sudo apt-get update && sudo apt-get upgrade
```

---

