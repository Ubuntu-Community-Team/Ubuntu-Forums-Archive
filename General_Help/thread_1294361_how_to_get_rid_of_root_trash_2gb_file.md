---
title: "how to get rid of root trash? 2gb file"
date: 2009-10-18
forum: General Help
---

### Post by sdowney717 on 2009-10-18
i had a 2gb log file ncidd.log in /var/log and used gksudp nautilus to put it in the trash, but i cant seem to delete this permanently
so how do i recover the space?

---

### Post by CharlesA on 2009-10-18
Check this out here: [http://ubuntuforums.org/showpost.php?p=4800640&postcount=3](http://ubuntuforums.org/showpost.php?p=4800640&postcount=3)

---

### Post by sisco311 on 2009-10-18
> **sdowney717 said:**
> i had a 2gb log file ncidd.log in /var/log and used gksudp nautilus to put it in the trash, but i cant seem to delete this permanently
so how do i recover the space?

Open your file manager as root and delete the files:
```
gksu nautilus trash://
```

Be careful!!!

---

### Post by Sam on 2009-10-18
More safe:

```
sudo apt-get install trash-cli
sudo -i empty-trash
```

---

### Post by sisco311 on 2009-10-18
> **Sam said:**
> More safe:

```
sudo apt-get install trash-cli
sudo empty-trash
```

almost :) 
```
sudo -i empty-trash
```

---

### Post by Sam on 2009-10-18
> **sisco311 said:**
> almost :)

Corrected, thanks ;)

---

