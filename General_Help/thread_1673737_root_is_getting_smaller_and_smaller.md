---
title: "root is getting smaller and smaller"
date: 2011-01-22
forum: General Help
---

### Post by chaopoch on 2011-01-22
I am using 10.04 LTS Lucid, and I notice the free space of root is getting smaller and smaller. 

Five months ago, there was about 3.9GB free space of root, but now it is only 1.6GB. I always run sudo apt-get autoremove and sudo apt-get autoclean every time the update is finished, and also use Bleachbit to clean the system, but both are useless.

I never faced such problem with older versions of Ubuntu, is there any measure to fix it? thanks for reply.

---

### Post by nerdy_kid on 2011-01-22
did you clear the package archive out?  When Ubuntu downloads packages they are stored in /var/cache/apt/archives, so that can use up some space after awhile.
Run this to clear it out:

```

sudo rm /var/cache/apt/archives/*.deb

```

that will delete all the downloaded .debs in the cache, it will not uninstall any packages.

---

### Post by chaopoch on 2011-01-22
nerdy_kid,

Thanks for reply, I did check /var/cache/apt/archives many times before, and I just do it again, there is not any .deb inside.

---

### Post by Bitrate on 2011-01-22
Check /var/log for any large files that you can purge.

also try this command to check disk file usage:

du -sh /[!d,p]*

---

### Post by squenson on 2011-01-22
Silly idea: have you emptied the Recycle Bin?

---

### Post by chaopoch on 2011-01-23
> **Bitrate said:**
> Check /var/log for any large files that you can purge.


The total content of /var/log is only 167.6 MB, that won't be a problem.

---

### Post by Andrew.Z on 2011-01-23
Here are some suggestions in order of likeliness to help (#1 is my best suggestion)

1. Try using Disk Usage Analyzer (aka Baobab) to find where most of the space is being used.  


2. Try this command to find the largest files

du -a /var | sort -n -r | head -n 10

3. Find out which are the largest packages installed.  (This doesn't sound likely for your case)


4. For BleachBit try installing the bonus pack (currently version 0.8.2) and the latest version of BleachBit application (0.8.7, released yesterday).  In your case, the bonus pack may help if you never used it.

---

