---
title: "how to re-install plymouth"
date: 2011-10-24
forum: General Help
---

### Post by Spyderkid on 2011-10-24
my computer literally just spontaneously combusted, so i had to do a bunch of "fsck"'s and other stuff to get it working again, all the inodes were screwed, and many other stuff. In the process plymouth has been damaged

so on boot it only shows text, not the splash. how do i re-install it?

(Ubuntu 11.10)

---

### Post by jonkiribati on 2011-10-24
did you try to use the apt-get commande ? or dpkg-reconfigure ?

---

### Post by Spyderkid on 2011-10-24
i know what commands to use, i just don't know what the package is called... :S

---

### Post by mikejonesey on 2011-10-24
obviously a dangerous command lol :P
```
sudo apt-cache search plymouth | cut -d " " -f 1 | sort | xargs apt-get install --reinstall
```

in your case
```
sudo apt-get install --reinstall plymouth
```

---

