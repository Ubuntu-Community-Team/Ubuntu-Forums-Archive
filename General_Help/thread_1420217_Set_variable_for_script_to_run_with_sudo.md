---
title: "Set variable for script to run with sudo"
date: 2010-03-02
forum: General Help
---

### Post by SoftwareExplorer on 2010-03-02
I have a script that backs up my computer that must be run like this:
```
sudo /home/bjorn/script.sh
```

However, I need to be able to change the ip it backs up to. I used to do this by rewriting the script when the ip changed, but I now have like 10 different scripts. So, it would be nice to be able to set a variable and then run my script. I used $bkup_ip in the place of all the old ip s in the script. However, it seems like if I set the variable with export, and then run the script with sudo the variable is empty. How can I set the variable so that it is available for the script?

---

### Post by sisco311 on 2010-03-02
```
sudo backup_ip="whatever" ~/script.sh
```

---

### Post by SoftwareExplorer on 2010-03-02
> **sisco311 said:**
> ```
sudo backup_ip="whatever" ~/script.sh
```

Thanks. I knew there must be a simple way to do it.

---

