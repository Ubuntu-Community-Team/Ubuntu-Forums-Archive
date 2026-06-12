---
title: "Backup snapshots show up on the desktop as mounted files"
date: 2011-01-20
forum: General Help
---

### Post by zombiezparadize on 2011-01-20
I am using Ubuntu 10.04 x86_64. I log in to the machine using nfs. For a problem with mounting my home directory, I had to copy all the contents of my home directory (including all configuration files) from a recent snapshot on to itself. That is, I did something like,
```
cp -r /home/user/user /home/user 
```

All of my recent data and program configurations were in /home/user/user. So after the copy operation, I logged out and logged back in again to see that all my configuration and data was restored to what I wanted. But the problem is that now on my desktop I see hundreds of mounted volumes. These are coming from an hourly/weekly snapshot program. The tech support guys for my lab have suggested copying all relevant data to a backup and then deleting the home directory altogether. But I don't want to configure all programs all over again. I think I should be able to get rid of the problem by editing/deleting one or more desktop configuration files. I just don't know which ones. I tried looking around the gconf-editor but was overwhelmed at the amount of information on  there. Does anyone have any idea about what I could possible do?

I am attaching a snapshot of my screen for everyone to understand what I mean.

---

### Post by zombiezparadize on 2011-01-20
Bump. Anyone?

---

### Post by dlyr on 2011-01-27
I have the same probleme when I go into my .snapshot directory,
One (not satisfesant) solution is to remove drive icons from desktop as found here : [http://tombuntu.com/index.php/2007/10/25/hide-partition-icons-from-your-ubuntu-desktop/](http://tombuntu.com/index.php/2007/10/25/hide-partition-icons-from-your-ubuntu-desktop/)

in gconf-editor, key apps->nautilus->desktop, uncheck visible_drive

If anyone has a better solution (and can explain what happens) it would be better.
++ dlyr

---

### Post by zombiezparadize on 2011-01-28
My problem was solved upon rebooting. I didn't really do anything other than writing a script to backup all my data but I never ended up executing it. Unfortunately, this does not provide a solution for those who may/do face this problem.

---

