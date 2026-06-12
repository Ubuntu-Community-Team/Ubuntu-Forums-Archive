---
title: "Apt-get keeps trying to remove a package Can I tell it to ignore it?"
date: 2009-07-24
forum: General Help
---

### Post by Redundant Username on 2009-07-24
I used the System Janitor to clean some packages. Now apt-get wants to remove brscan, my printer driver. It fails to do so. I can't install anything until it's removed, and i can't unmark it from Synaptic. I get this error: ```
E: brscan: subprocess post-removal script returned error exit status 1
	
  	
```

---

### Post by madsmeg on 2009-07-26
try ```
sudo apt-get purge brscan
```

---

