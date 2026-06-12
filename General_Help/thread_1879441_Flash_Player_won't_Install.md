---
title: "Flash Player won't Install"
date: 2011-11-11
forum: General Help
---

### Post by Orcris on 2011-11-11
I was upgdating applications using Muon, and it got stuck configuring flashplugin-installer. I quit it using ```
killall muon
``` and ran ```
sudo dpkg --configure -a
```
After that, I got an error saying that flashplugin-installer and flashplugin-downloader didn't install correctly, so I ran ```
sudo apt-get purge flashplugin-installer flashplugin-downloader
``` and ```
sudo apt-get install flashplugin-installer flashplugin-downloader
``` and got the same error as before. How do I fix this?

---

### Post by BillyBoa on 2011-11-11
Try to install it through Synaptic

---

### Post by dniMretsaM on 2011-11-11
Try this:
```
sudo rm /var/libs/dpkg/lock
sudo dpkg --configure -a
```

If it doesn't work, post the output of both commands.

> **BillyBoa said:**
> Try to install it through Synaptic

No don't, this wont help. You wont be able to install Synaptic anyway if you can't install any packages.

---

### Post by mister_playboy on 2011-11-16
> **Orcris said:**
> I was upgdating applications using Muon, and it got stuck configuring flashplugin-installer.

My computer hung on "configuring flashplugin-installer" for several minutes but eventually moved on, whereas my housemate's got stuck like yours did.

Out of curiousity, did you have the Flash-Aid Firefox add-on installed?

> **dniMretsaM said:**
> Try this:
```
sudo rm /var/libs/dpkg/lock
sudo dpkg --configure -a
```

Used these commands before but couldn't remember what they were... thanks for the refresher. :D

---

