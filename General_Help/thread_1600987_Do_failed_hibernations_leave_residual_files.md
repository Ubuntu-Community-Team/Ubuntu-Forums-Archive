---
title: "Do failed hibernations leave residual files?"
date: 2010-10-19
forum: General Help
---

### Post by Lynx Phoenix on 2010-10-19
I was recently trying to find a way to do a [one-time hibernation]("http://ubuntuforums.org/showthread.php?p=9997555#post9997555") and during the process of finding said way, i had some failed hibernations.

i'm concerned that there might be residual data left over since the failed hibernations i mention were those i waited for until hdd activity stopped and had to hard reset, when ofcourse ubuntu booted like i had just turned the pc on. i'm guessing ubuntu doesnt know a hibernation just failed so i want to know how i can check for residue, if indeed it is necessary

also, where is the hibernation data saved and how large should i expect them to be? i ran df after these failures and it doesnt seem like there's anything extra there but i dont know enough to decide.

---

### Post by surfer on 2010-10-19
as far as i know, the contents of the memory are dumped in your swap space. there is not much of a file system there, so you will not see any files.

---

### Post by Lynx Phoenix on 2010-10-19
i'm assuming these are my swap partition:

```
Filesystem           1K-blocks      Used Available Use% Mounted on
none                   1024556       376   1024180   1% /dev
none                   1030156      5520   1024636   1% /dev/shm
none                   1030156       248   1029908   1% /var/run
none                   1030156         0   1030156   0% /var/lock
```and gparted says my swap has "-" use which obviously means its clean (or that i dont have to care :P)

so i guess everythings ok

thanks :)

---

