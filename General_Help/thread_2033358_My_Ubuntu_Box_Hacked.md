---
title: "My Ubuntu Box Hacked?"
date: 2012-07-26
forum: General Help
---

### Post by ewe on 2012-07-26
Couldn't get on the internet because there was only 74kb of space left on my hard drive. It appears something strange has happened. Any help is appreciated.

---

### Post by elliotn on 2012-07-26
did u empty trash both as normal and as sudo?

launch Nautilus with sudo and navigate to trash if there are files there, they must be the ones eating your space

---

### Post by ewe on 2012-07-26
Thanks, I appreciate the help. Unfortunately, I'm not sure how to open Nautilius with sudo.

---

### Post by ewe on 2012-07-26
```
rob@rob-GN561AA-ABA-a6230n:~$ gksudo nautilus
Error copying '/home/rob/.Xauthority' to '/tmp/libgksu-6lFZ7p': No space left on devicerob@rob-GN561AA-ABA-a6230n:~$ 

```

---

### Post by hakermania on 2012-07-26
> **ewe said:**
> Thanks, I appreciate the help. Unfortunately, I'm not sure how to open Nautilius with sudo.

Press Alt+F2, type in 
```

gksudo nautilus

```
press [Enter], type in your password, and then Nautilus will open with Super User permissions!


(BTW, you can use the Disk Usage Analyzer program that comes along with ubuntu so as to see what's going on in your disk)

---

### Post by ewe on 2012-07-26
> **hakermania said:**
> Press Alt+F2, type in 
```

gksudo nautilus

```
press [Enter], type in your password, and then Nautilus will open with Super User permissions!


(BTW, you can use the Disk Usage Analyzer program that comes along with ubuntu so as to see what's going on in your disk)

```
rob@rob-GN561AA-ABA-a6230n:~$ gksudo nautilus
Error copying '/home/rob/.Xauthority' to '/tmp/libgksu-6lFZ7p': No space left on devicerob@rob-GN561AA-ABA-a6230n:~$ 

```

---

### Post by hal8000 on 2012-07-26
You can try clearing firefox cache and all tmp files.
Normally this is firefox, tools menu, then clear history.

However in your case firefox may not even start, so you may have to open a terminal and clear some space.

I would start with
```
sudo du -sh /tmp
```

See how much space is used by /tmp then commands

```
cd /tmp
sudo -rf *
```

WARNING: Last commands are pretty dangerous and will remove ALL file inside /tmp. You must make sure that you have changed into /tmp so lsit all files if unsure..

Hacked?  I doubt it very much. You are immune to viruses, malware and trojans on Ubuntu and linux.
You didn't give any info on how much space you allocated to your partitions. Most likely reason isyou've run out of disk space.

Hope that helps.

---

### Post by elliotn on 2012-07-26
> **hal8000 said:**
> You can try clearing firefox cache and all tmp files.
Normally this is firefox, tools menu, then clear history.

However in your case firefox may not even start, so you may have to open a terminal and clear some space.

I would start with
```
sudo du -sh /tmp
```

See how much space is used by /tmp then commands

```
cd /tmp
sudo -rf *
```

WARNING: Last commands are pretty dangerous and will remove ALL file inside /tmp. You must make sure that you have changed into /tmp so lsit all files if unsure..

Hacked?  I doubt it very much. You are immune to viruses, malware and trojans on Ubuntu and linux.
You didn't give any info on how much space you allocated to your partitions. Most likely reason isyou've run out of disk space.

Hope that helps.

try cleaning your apt cache too
```
 apt-get aptitude clean 
```

---

### Post by Grenage on 2012-07-26
While it could be an errant log file of the like, you can search for large files with something like:

```
find . -size +20000k -exec du -h {} \;
```

There is probably a more elegant method.

---

### Post by Scott Harrison on 2012-07-26
What sort of disk size are we talking about?

---

### Post by ewe on 2012-07-26
> **scott harrison said:**
> what sort of disk size are we talking about?300gb

---

### Post by ewe on 2012-07-26
I think it was Dropbox which I installed last week for my smartphone. I uninstalled it and everything seems good now.

Thanks for the help!

---

