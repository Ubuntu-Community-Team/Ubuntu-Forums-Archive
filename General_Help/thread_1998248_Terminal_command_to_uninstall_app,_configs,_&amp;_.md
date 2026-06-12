---
title: "Terminal command to uninstall app, configs, &amp; unneeded dependencies?"
date: 2012-06-06
forum: General Help
---

### Post by nrundy on 2012-06-06
Is there a command like so:  **apt-get autopurge <packagename>**?  (I can't find it in MAN APT-GET so I assume there isn't)

Running:   **apt-get autoremove <packagename>**   will uninstall the program and remove unneeded dependencies. But does it also uninstall the config files?

Is there a command that does the following: 1) uninstalls the program 2) uninstalls the config files and 3) uninstalls unneeded dependencies?

---

### Post by wheeze on 2012-06-06
I would try:

```
sudo apt-get purge appname && sudo apt-get autoremove
```

---

### Post by philinux on 2012-06-06
> **nrundy said:**
> Is there a command like so:  **apt-get autopurge <packagename>**?  (I can't find it in MAN APT-GET so I assume there isn't)

Running:   **apt-get autoremove <packagename>**   will uninstall the program and remove unneeded dependencies. But does it also uninstall the config files?

Is there a command that does the following: 1) uninstalls the program 2) uninstalls the config files and 3) uninstalls unneeded dependencies?

Even with sudo apt-get purge appname config files will remain in your home folder. 

> purge
           purge is identical to remove except that packages are removed and purged (any configuration files are
           deleted too).

---

### Post by nrundy on 2012-06-06
> **philinux said:**
> Even with sudo apt-get purge appname config files will remain in your home folder.

what config files are being removed if config files remain in my home folder. I don't understand this, could you say more please?

---

### Post by wheeze on 2012-06-06
> **nrundy said:**
> what config files are being removed if config files remain in my home folder. I don't understand this, could you say more please?

Purge removes system config files, like smb.conf for samba and so forth.

No apt commands will remove config files from your home directory, you'll need to manually delete these.

---

### Post by nrundy on 2012-06-06
> **wheeze said:**
> Purge removes system config files, like smb.conf for samba and so forth.

No apt commands will remove config files from your home directory, you'll need to manually delete these.

So just delete the .conf folder associated with the removed app in my home directory, right? Nothing else is needed to remove config files from home directory?

---

### Post by wheeze on 2012-06-06
> **nrundy said:**
> So just delete the .conf folder associated with the removed app in my home directory, right? Nothing else is needed to remove config files from home directory?

Yeah, set your home directory to show hidden files and look for folders or other files with the application name you deleted. Sometimes you have to look inside other folders, but it takes no more than 2 minutes to peruse the folders and delete remaining  configs.

---

### Post by wilee-nilee on 2012-06-06
> **nrundy said:**
> So just delete the .conf folder associated with the removed app in my home directory, right? Nothing else is needed to remove config files from home directory?

Crtl-h to show hidden, remove associated file in .config.

Look in synaptic with the original app removed for dependencies not removed, and last of all run a search in the files set up to look for what is left.

You may need to run in the terminal to have root to remove some.
```
gksudo nautilus
```

I had to do this with vlc as it turned into a big blue box in the development lately. the dependencies were still hanging around. vlc still played stuff but no controls.

---

### Post by wheeze on 2012-06-06
I'll let on to one of my secret weapons for cleaning up an installation, a package called **upgrade-system**. It's in the repos.

Install it, it brings in a few small dependencies, then run it from a terminal:
```
sudo upgrade-system
```It will do apt-get update, then apt-get dist-upgrade, then runs deborphan to look for unused dependencies. It cycles through the deborphan part until it can't find any more unused deps, since often times removing a package will make  other packages unneeded.

I've had it remove over 150 packages from a fresh install. Never broken a system yet.

---

### Post by ranger1021994 on 2012-08-02
Ubuntu Tweak (mine is 0.7.2)
It will do the dirty work of deleting config files.

---

