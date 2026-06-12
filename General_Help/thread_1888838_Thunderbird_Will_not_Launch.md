---
title: "Thunderbird Will not Launch"
date: 2011-11-30
forum: General Help
---

### Post by Quarkrad on 2011-11-30
newbie running 32bit 10.10.  I've just re-installed ubuntu 10.10 as a clean install.  Used the software centre to install Thunderbird - but it will not launch either via terminal or Apps/Internet/TB.  All I get is window saying **Thunderbird is already running, but i not responding. To open a new window, you must first close the existing Thunderbird process, or restart your system.**  There are many google entries on this including bugs but I get this on a clean install.  I've deleted TB via synaptic and re-installed after a re-boot but what ever I do TB will not launch.  I have TB running on a number of family/friends machines but this is the first time I've come across this - TB will not launch as a new install.  Any help appreciated - father-in-law is waiting to access his mail.

---

### Post by Quarkrad on 2011-11-30
Same problem if I type in terminal  **thunderbird -safe-mode**

---

### Post by Quarkrad on 2011-11-30
sorted - deleted all folder/files in home/./thunderbird   TB launches and rebuilds files.

---

### Post by ofnuts on 2011-11-30
> **Quarkrad said:**
> newbie running 32bit 10.10.  I've just re-installed ubuntu 10.10 as a clean install.  Used the software centre to install Thunderbird - but it will not launch either via terminal or Apps/Internet/TB.  All I get is window saying **Thunderbird is already running, but i not responding. To open a new window, you must first close the existing Thunderbird process, or restart your system.**  There are many google entries on this including bugs but I get this on a clean install.  I've deleted TB via synaptic and re-installed after a re-boot but what ever I do TB will not launch.  I have TB running on a number of family/friends machines but this is the first time I've come across this - TB will not launch as a new install.  Any help appreciated - father-in-law is waiting to access his mail.
You may have a lock file lingering:
```

# Go to the thunderbird profile
cd ~/.thunderbird
# find the lock
find . -name lock

```
and then erase the lock

---

