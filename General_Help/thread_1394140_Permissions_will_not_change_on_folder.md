---
title: "Permissions will not change on folder"
date: 2010-01-30
forum: General Help
---

### Post by daminkz on 2010-01-30
I am an Ubuntu user of about a month, and have never had trouble with permissions before this.

I am trying to set the permissions on a folder so that I can share the folder to my XP machine. I first installed samba, and set the folder to share with guests. I tried to get in from my XP machine, but am ridden by the error "Permissions denied." After searching forums I learned that I needed to change the permissions on the folder as well as sharing the folder.

I opened a terminal:

```
charles@charles-laptop:~/Desktop$ sudo chmod 777 Reason/

```This works fine. When I check the permissions, however, the revert to normal. I also tried changing the permissions from the graphical interface and after setting the permissions, they revert back to normal.

Help!!     :frown:

[edit]

Problem solved. Used the graphical Samba interface, added a windows user, and restarted both computers. Logged in via XP, and it works. :D

---

