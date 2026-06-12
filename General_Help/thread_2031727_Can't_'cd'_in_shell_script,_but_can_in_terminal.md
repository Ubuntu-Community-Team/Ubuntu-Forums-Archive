---
title: "Can't 'cd' in shell script, but can in terminal?"
date: 2012-07-22
forum: General Help
---

### Post by Ranko Kohime on 2012-07-22
I'm scratching my head at this one.

```
user@Evo-D500:~$ /media/Backup/ranko.ignorelist.com.sh 
: No such file or directoryist.com.sh: line 5: cd: /media/Backup/Downloads/
Continuing in background, pid 22820.
user@Evo-D500:~$ cd /media/Backup/Downloads/
user@Evo-D500:/media/Backup/Downloads$
```

The full script:
```
#/bin/bash
#
# Script to update Dynamic DNS @ ranko.ignorelist.com
#
cd /media/Backup/Downloads/
wget -o wget.ranko.ignorelist.com.log.txt --read-timeout=0.0 --waitretry=5 --tries=400 --background http://site
```

What could possibly cause this?

---

### Post by sandyd on 2012-07-22
> **Ranko Kohime said:**
> I'm scratching my head at this one.

```
user@Evo-D500:~$ /media/Backup/ranko.ignorelist.com.sh 
: No such file or directoryist.com.sh: line 5: cd: /media/Backup/Downloads/
Continuing in background, pid 22820.
user@Evo-D500:~$ cd /media/Backup/Downloads/
user@Evo-D500:/media/Backup/Downloads$
```The full script:
```
#**!**/bin/bash
#
# Script to update Dynamic DNS @ ranko.ignorelist.com
#
cd /media/Backup/Downloads/
wget -o wget.ranko.ignorelist.com.log.txt --read-timeout=0.0 --waitretry=5 --tries=400 --background http://site
```What could possibly cause this?
Fixed.
P.S.
Why not use
```

wget -O

```?

---

### Post by Ranko Kohime on 2012-07-22
> **sandyd said:**
> Why not use
```

wget -O

```?
A successful get produces a zero byte file for this particular service.

And is that Exclamation Point the only thing I missed?!

Excuse me while I go fix a dozen other scripts.

---

