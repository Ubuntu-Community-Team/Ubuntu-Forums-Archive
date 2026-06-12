---
title: "apt problems"
date: 2010-02-08
forum: General Help
---

### Post by ionray on 2010-02-08
Hi,
 I've just started using ubuntu (version 9.1) installed it about 4 days ago.    
 

 I cant get apt to update or apt seems not to be working properly in the terminal. I have gone through the net finding people with similar problems but still what has been recommended does not work.
 

 

 e.g.  
 when type into terminal “apt-get update” it says “E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied) 
 E: Unable to lock the list directory ”
 

 but when I add sudo to apt-get update it works up to “connecting to au.archive.ubuntu.com” which it gets to 62% and stops.
 

 when type into terminal ”apt-get clean” says “E: Could not open lock file /var/cache/apt/archives/lock - open (13: Permission denied) 
 E: Unable to lock the download directory ”  
 

 

 Any help is appreciated.

---

### Post by i.r.id10t on 2010-02-08
You doing this as the root user or with sudo? Regular users can't do apt ...

---

### Post by ionray on 2010-02-08
I just got in as a root user and still having the same problems...

---

### Post by janidotux on 2010-02-08
Apt always must be run as root. You can also upgrade via Synaptic: System -> Administration -> Synaptic Package Manager
If your upgrade still fails at 62%, you may change your repositories location, maybe if you try another location you have luck. In Synaptic: Settings -> Repositories -> Download From, and change server location in this box.

---

### Post by ionray on 2010-02-09
after figuring out how to change the repositories it was able to download :D. thanks for your help.

---

