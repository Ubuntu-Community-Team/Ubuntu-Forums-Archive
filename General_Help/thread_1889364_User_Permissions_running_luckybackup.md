---
title: "User Permissions running luckybackup"
date: 2011-12-01
forum: General Help
---

### Post by GSD4ME on 2011-12-01
Perhaps one of the experts here can help me with a problem I am having re: access permissions. Bear with me as I am still relatively new to Linux/Ubuntu, having been a Windows man all my working life (and DOS for those of you old enough to remember that ...)

I am using Ubuntu 11.10 on a laptop.

I am trying to run a backup using LuckyBackup which does work for *some* of the users on my home laptop. (Luckybackup - which I am very impressed with - comes in two flavours, 'ordinary' and 'super user'. I am using the latter as I want to backup all users on the laptop. It does ask me for the authentication password when I run it, so no problems there. Everything seems to run OK in the package, but am open to being corrected here, dependent upon the results of the discussion below)

On the laptop there are 3 user accounts - mine, wife's and a business account.

When I run the backup, my files are copied to the external drive with no problems.
Same with the business account.
However, my wife's will not copy at all - the backup basically says that it cannot access her files, despite being run in 'super user' mode.

I have logged in to her account and looked at the access permissions for her home directory (Home with a capital H). She can "create and delete", her 'group' can "access" files and "others" can "access" as well. the file access type is set to blank (actually says "-")
I  changed the  permissions for group and others to "read only" and applied the "set permissions to enclosed files". The acknowledgement box came up and worked away applying the permissions. (BTW the main control box altered the permissions back to blank ("-") whilst this was happening)
Came out of this and went to /home (small h) where the three user directories are listed. Here, she can see her files (as would be expected), she can see the business directory files but not mine. No problem here as I am an administrator' she and the business account are both 'standard' accounts.

I then logged in to me (administrator remember) went to /home (small h). I can see my files (as to be expected), I can see the business account files, but I still can't see my wife's files - which I would expect.

I have compared the file access permissions and user account modes for both by wife's account and the business account and I cannot see anything that marks them as being different from each other.

So my question is: how do I change the access permissions of her files (all of them) and her Home folder to be 'see-able' by me and the backup program. The account folders are owned by 'root' but Ubuntu doesn't have a 'root' user (or so my Ubuntu bible book tells me).
Any help would be most appreciated as I am one of these people who likes to have things backed up in case some shady character decides to walk off with my machine.

---

### Post by nothingspecial on 2011-12-01
Hi,

Please don't post your question in someone else's thread. Make a thread of your own in future.

I have done this for you.

Thanks :)

---

