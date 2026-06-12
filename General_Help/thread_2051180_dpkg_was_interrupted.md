---
title: "dpkg was interrupted"
date: 2012-09-01
forum: General Help
---

### Post by sapiiterbang on 2012-09-01
hi,
i'm fairly new to ubuntu so hears the problem.
firstly i'm running ubuntu 11.04
i tried install konsole from terminal
i type 'sudo apt-get install konsole'
so it's start downloading the file, but in middle of the time, maybe it's half of the downloaded, my friend actually close the terminal
when i'm trying to download it again, then it says:
"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. "
even i'm trying to install youtube-dl, it's just the same
and when i'm trying to open synaptic package manager, it says:
"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

How do i fix the problem ??
sorry for my bad english :lol:

---

### Post by sisco311 on 2012-09-01
Hi and welcome to the forums!

Do what the error message says. Run the following command in the terminal:
```
sudo dpkg --configure -a
```

---

### Post by sapiiterbang on 2012-09-01
ah yes, it solved the problem \\:D/
thanks :)

---

### Post by sisco311 on 2012-09-01
You are welcome!

---

