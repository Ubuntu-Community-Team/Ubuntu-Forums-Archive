---
title: "Disabling user the perimission to sudo and to become root"
date: 2006-03-13
forum: General Help
---

### Post by chimera on 2006-03-13
I really need to know how to disable a certain user the perimission to sudo and to become root. Any help here would be appretiated.

---

### Post by NicePics13 on 2006-03-13
Go to **System - Administration - Users and Groups**

Then edit that user's properties, go to the *user privileges* tab and disable "*executing system adm. tasks*" and whatnot.
Hope this helps.

---

### Post by frodon on 2006-03-13
Using the user & group window under System > administration. Click on the user you want to edit and then use the preference button, there's a tab that allow you to set a lot of option like "allow user to use sudo".
But don't worry, when you create a new user he don't have sudo rights by default.

---

### Post by chimera on 2006-03-13
Well, I followed your advices and now he can't use sudo, but he can still just type su in the terminal and become root! :shock:

---

### Post by Dzs on 2006-03-13
well, i think you can not set some for user, that he can not use su. Its normal bash command, but set password for root, and dont tell it to user.. \\:D/

---

### Post by chimera on 2006-03-13
Thanks, that worked :P

---

