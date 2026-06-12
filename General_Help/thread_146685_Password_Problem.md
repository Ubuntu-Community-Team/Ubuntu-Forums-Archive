---
title: "Password Problem"
date: 2006-03-18
forum: General Help
---

### Post by dthomp325 on 2006-03-18
I just installed 5.10, and I am having a problem with the password system. When logged in as a regular user, I try to access some of the admin features on the System->Administration menu. A dialog pops up asking for my password. If I enter the root password, it tells me I have the wrong pass. If I enter my user's password, nothing happens. If I use the 'su' command from the command line with the root password, I can run the programs I wish. Why isn't sudo working? Any ideas.

Thanks

---

### Post by jerrykenny on 2006-03-18
You need to be in the "admin" group . . . . the original user you setup during the installation should've had that by default

---

### Post by dthomp325 on 2006-03-18
My install doesn't even have an admin group. It seems like a problem with sudo.

---

