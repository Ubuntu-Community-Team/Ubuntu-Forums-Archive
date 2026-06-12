---
title: "Help with Moving Files and Permissions?"
date: 2010-08-21
forum: General Help
---

### Post by midmichmark on 2010-08-21
hello,

i'm wondering if someone can help out? we have a house computer shared by several housemates and with the new school year starting we want to delete the housemate's who have moved out and create new users for those who are moving in.

we're able to delete and create users with the users and groups cp, but one user who has moved out is still in town and we want to copy her files (we've collected them into folder) to the house guest account and drop her files into folder on the house guest desktop.

when we try to do that, we get permissions error - we tried to add our account to the user's group but that didn't help. we're kinda new to the unix thing but have had some experience. we also tried to sudo the command for mv and cp from the terminal window

sudo cp files /home/guest/Desktop/

but message said omitting files

any help would be greatly appreciated!

thanks,

m&m

---

### Post by dino99 on 2010-08-21
you should use mountmanager to deal with partitions and devices rights, set your prefs into: system admin mountmanager, after installation of course.

---

