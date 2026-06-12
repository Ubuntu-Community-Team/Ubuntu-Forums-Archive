---
title: "Does auto updating in Ubuntu update both security and software?"
date: 2012-06-08
forum: General Help
---

### Post by Rytron on 2012-06-08
In Ubuntu and its derivatives, does auto updating [as seen in image] update both security and software or just security?

---

### Post by Paqman on 2012-06-08
Those updates will automatically install any update for a package which is a security issue. What it won't update is things which are just bugfixes to ordinary packages.

---

### Post by mcduck on 2012-06-08
If you are only using Ubuntu'd official repositories, the only reasons you'll get updates are for security reasons, and to fix serious bugs. To keep things as stable as possible pAckaes in Ubuntu's repositories aren't updated just to provide latest package versions or even to fix smaller bugs after release.

So if you want normal version updates for some program you are using, you'll need to add a third-party repository which provides such updated packages.

---

### Post by Rytron on 2012-06-09
So if I install Ubuntu or a derivative on a PC belonging to someone that knows little about computers -- must I tell them to run either "sudo apt-get install update" or launch the Update Manager about once a week? I don't mind but less techy people just want the OS to run updates automatically.

---

### Post by mcduck on 2012-06-09
> **Rytron said:**
> So if I install Ubuntu or a derivative on a PC belonging to someone that knows little about computers -- must I tell them to run either "sudo apt-get install update" or launch the Update Manager about once a week? I don't mind but less techy people just want the OS to run updates automatically.

The update manager will, by default, check for available updates automatically and pop open a window giving the user an option to install them. So you don't need to do anything.

---

