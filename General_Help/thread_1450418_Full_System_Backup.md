---
title: "Full System Backup"
date: 2010-04-09
forum: General Help
---

### Post by Tanner2007 on 2010-04-09
Possible? I love the way my Ubuntu OS is setup but I have a habit of **** it up, anyway to do a system backup? snap shot? image? anything? 

please and thanks

---

### Post by darolu on 2010-04-09
You can back the whole hard drive/partition up with dd:
```
$ dd if=/dev/sdXX of=/path/to/your/image/backup.img
```
you can clone it to a another hard drive too:
```
$ dd if=/dev/sdXX of=/dev/sdXX
```

I usually have my /home in a different partition, that way all my personal configurations and data remain intact should I need to make a clean install.

---

### Post by Rodney9 on 2010-04-09
Clonezilla is very good -

[http://www.clonezilla.org/](http://www.clonezilla.org/)

---

### Post by e24ohm on 2010-04-10
> **darolu said:**
> You can back the whole hard drive/partition up with dd:
```
$ dd if=/dev/sdXX of=/path/to/your/image/backup.img
```
you can clone it to a another hard drive too:
```
$ dd if=/dev/sdXX of=/dev/sdXX
```

I usually have my /home in a different partition, that way all my personal configurations and data remain intact should I need to make a clean install.Is /home location, were all the configuration files saved for applications?

---

### Post by drs305 on 2010-04-10
> **e24ohm said:**
> Is /home location, were all the configuration files saved for applications?

Most of your personal settings are in your /home folder (/home/yourusername). Many system configuration files which may be important to you, such as fstab if you made many changes to it, network settings, and the default Grub 2 settings, are stored in various /etc folders. 

When I'm doing a clean install I usually make straight copies of my /home, /etc, and /boot folders for quick reference, even though I have backups in less accessible locations/formats.

---

