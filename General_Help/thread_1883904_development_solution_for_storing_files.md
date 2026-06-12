---
title: "development solution for storing files"
date: 2011-11-20
forum: General Help
---

### Post by alain.roger on 2011-11-20
Hi,

i'm looking for the best way to store and secure my development files (web site / components and so on...) 

basically i will develop everything under ubuntu and i would like to have a backup but available (like a shared folder) for windows. maybe on external USB disk.

so basically i was thinking to use a cron that will backup my files on a shared network HDD on my other computer (Windows OS based)

i do not think it's the best way but t is very similar to what i have under Windows OS...basically i have a synchronization SW that do even shadow copy to another external USB disk.

if something like that exists under ubuntu i would be glad.
what do you think about that ?
A.

---

### Post by roger_1960 on 2011-11-20
Hi

Why not use Ubuntu One or Dropbox to sync with your windows PC?

---

### Post by alain.roger on 2011-11-20
AFAIK Dropbox shared also file on internet and i won't let external company to store my files.

In which way Ubuntu One can help me to automatically synchronize files after i made changes to them ?

---

### Post by roger_1960 on 2011-11-20
Hi again

Ubuntu One is much like dropbox.

To keep it local I suggest you install backintime from the software center and set it to backup the specific folders you are using to a local USB drive regularly (backup interval can be as short as 5 mins if you like).  Make sure the USB drive is formatted in something windows can use - FAT32, NTFS etc.

---

