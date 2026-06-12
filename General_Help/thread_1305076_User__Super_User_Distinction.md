---
title: "User / Super User Distinction"
date: 2009-10-29
forum: General Help
---

### Post by Voxan on 2009-10-29
Hello!

I installed Karmic today and I noticed a change from Jaunty that I would like to revert.
I'm using a desktop PC that I configure for several users with their own user accounts.

I set up **one** user as the sudo user and every other user as normal user. If I need to install a package, I log in as the sudo user. The sudo account is only used for administrative purposes, I log out afterwards into the normal user account.

In **Jaunty**, when I was logged in as a normal user and I tried to open the package manager, it asked me for **my user password** and then failed to grant me access as I was not in the sudoer file.
In **Karmic**, as I open the new Software Center and attempt to install a package, it prompts me to provide the password **of the super user** and then successfully allows me to perform this task.

How can I make sure that administrative tasks are **only performed from the sudo account**, or at least from "su sudoer" in the terminal? I understand many users of 9.10 will welcome this change however this is not ideal in my situation.

Note: I set up all home folders (including the sudo account) as encrypted home folders, however I doubt this has an impact on my problem here.

*Thank you for your kind help!* :D

---

