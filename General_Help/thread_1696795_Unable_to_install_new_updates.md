---
title: "Unable to install new updates"
date: 2011-02-27
forum: General Help
---

### Post by ksihawk7 on 2011-02-27
Whenever I try to check for updates, it will say updating cache, but then it will say Failed to download repository information Check your internet connection.

I'm connected to the internet fine, so I don't know what to do. Also, at the top right corner next to the power button on the top panel, there is a message thing saying "The update information is outdated"

---

### Post by cain071546 on 2011-02-27
what version of Ubuntu are you running?

check your software sources list make sure its up-to-date

---

### Post by Frogs Hair on 2011-02-27
Try running these in the terminal , if you don't connect right away keep trying first command until you connect to your sources. then run the second and then run the update manager. ```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

