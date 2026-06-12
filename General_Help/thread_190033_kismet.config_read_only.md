---
title: "kismet.config read only"
date: 2006-06-05
forum: General Help
---

### Post by notoriouslou1022 on 2006-06-05
i need to change up this file a bit, but its only read only. So i go right click properties... its says i must be in root to changes these setting. pleace help


thank you

---

### Post by mscman on 2006-06-05
Try ```
sudo gedit /path/to/file
```

---

### Post by Sutekh on 2006-06-05
You can use the Terminal (Applications-> Accessories menu) to open the file. Enter this command and then your password when prompted. You will also need to enter the folder that the file is in, as I don't spcifically know.
```
sudo gedit /<path of kismet config>/<name of kismet config file>
``` 

Or you can open the run dialog by pressing Alt+F2 and type in
```
gksudo nautilus
``` Again you your password, now you can browse your files as root (and edit them).

I will caution using the **gksudo** approach, as while Nautilus (the browser) is open you have the potential to mess things up in a bad way.  

I strongly advise changing permissions and ownerships of files that are outside your home folder.   Editing them is fine.

---

### Post by kafitz22 on 2006-06-05
Go into a terminal and enter:

```
sudo gedit /etc/kismet/kismet.conf
```

---

### Post by notoriouslou1022 on 2006-06-05
Thank you three so very much = )

---

