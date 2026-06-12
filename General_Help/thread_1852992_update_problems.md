---
title: "update problems"
date: 2011-10-01
forum: General Help
---

### Post by tobydog on 2011-10-01
hi i was updating my pc and the power failed half way through an update i know cannot get the update to work , it says i can only attempt a partial update , when i try i get a file error broken file . how can i get this to work again please.

---

### Post by ajgreeny on 2011-10-01
Try ```
sudo dpkg-reconfigure -a
``` in terminal, possibly followed by ```
sudo apt-get install -f
```  If it does not make any sense, come back here with error messages showing.

---

### Post by tobydog on 2011-10-02
this is what i get when i try your suggestion .
dpkg-query: parse error, in file '/var/lib/dpkg/updates/0051' near line 0:
 field name `<?xml' must be followed by colon
/usr/sbin/dpkg-reconfigure: a2ps is not installed.
andrew@andrew-desktop-workshop-packard-bell:~$

---

### Post by dino99 on 2011-10-02
reboot in recovery mode ( shift key down at bios end process) and select "repair packages"

---

### Post by philinux on 2011-10-02
The command is.

sudo dpkg --configure -a

Note the spaces.

---

### Post by tobydog on 2011-10-02
still same problem , dont seem to be able to get recovery mode , how do i do this please

---

### Post by philinux on 2011-10-02
> **tobydog said:**
> still same problem , dont seem to be able to get recovery mode , how do i do this please

Post back what errors these commands give.

```
sudo apt-get update
```

then

```
sudo apt-get upgrade
```

---

