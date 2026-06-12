---
title: "Help with own distro"
date: 2012-05-27
forum: General Help
---

### Post by z3rO88 on 2012-05-27
Hi, people I am wondering if anybody could help me with this issue that i have come across, i want to edit a desktop.iso i followed this tutorial 

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

I have done everything upto the bit customize the background, when i try putting my own background images into the directory 

/usr/share/backgrounds

comes up with error can't put file in root access error anybody got any ideas why this issue occurred and if could help.

Thanks

---

### Post by searchfgold6789 on 2012-05-27
You have to be the "root user" or "super user" to copy files to that directory, because it's owned by the root account. When a folder is owned by the root account, other accounts cannot access it without super user permissions. This is to prevent system damage.
To open the file manager as a super user, open a terminal and runs the command:```
gksu nautilus
```The command will run the file manager as root, so you can make modifications to system folders and files. 
[B]Be very careful when using the file manager in this mode, and make sure you know exactly what you are doing. If something is owned by root, it is usually for a good reason, so beware.
[/B]Anyway, I hope that suggestion helps.

---

