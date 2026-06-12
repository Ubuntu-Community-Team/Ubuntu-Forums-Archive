---
title: "how to convert rpm to sh file"
date: 2009-07-11
forum: General Help
---

### Post by suresh_vandiyur on 2009-07-11
Am using two linux os. ubuntu and zenwalk. t****he rpm and deb packages not supporting to zenwalk. i need to convert rpm to sh or deb to sh. please help me.

---

### Post by Jebtrix on 2009-07-11
I dont know of any direct way, but you can use right click on a .deb file and Extract Here. Then look for the control.tar.gz which holds any scripts that were to be run. Data.tar.bz2 contains all the files.

Most apps have a generic binary xxx.tar.gz package or you could compile from source which almost usually has a install script included to get you started. Good luck...

---

### Post by suresh_vandiyur on 2009-07-13
> **Jebtrix said:**
> I dont know of any direct way, but you can use right click on a .deb file and Extract Here. Then look for the control.tar.gz which holds any scripts that were to be run. Data.tar.bz2 contains all the files.

Most apps have a generic binary xxx.tar.gz package or you could compile from source which almost usually has a install script included to get you started. Good luck...ok
why we dont use the /boot partition in zenwalk? please help me

---

### Post by bodhi.zazen on 2009-07-13
Zenwalk is based on Slackware and one advantage of slackware is it is easy to install from source.

I suggest you try to find a Slackware package first, and if that is not possible, install directly from source.

I would install from a .deb or .rpm only as a last resort.

---

