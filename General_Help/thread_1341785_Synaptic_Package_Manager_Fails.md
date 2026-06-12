---
title: "Synaptic Package Manager Fails"
date: 2009-11-30
forum: General Help
---

### Post by SNYP40A1 on 2009-11-30
An Error Occured:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I tried installing Ark last night and it froze around 73%.  Was still at that point when I restarted the computer.  I think the process is still running in the background.  Looked, but didn't see anything that looked like it.  What should I do?

---

### Post by pedro_orange on 2009-11-30
Yeh this happens if you restart while using the package manager.

You need to open a terminal and run the 

```
sudo dpkg --configure -a
```

command. This should fix everything. You might need to do a 

```
sudo apt-get update
```

To be sure after the first command

---

### Post by john newbuntu on 2009-11-30
Do exactly what the error message says. Run this from a terminal:
```
sudo dpkg --configure -a
```
Look into this for more details:
[http://ubuntuforums.org/showpost.php?p=7244868&postcount=12](http://ubuntuforums.org/showpost.php?p=7244868&postcount=12)

---

### Post by SNYP40A1 on 2009-11-30
Seemed to work, I must have typed it in incorrectly before.  Thanks!

---

