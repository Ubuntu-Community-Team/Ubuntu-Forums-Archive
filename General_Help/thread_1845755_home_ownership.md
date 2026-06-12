---
title: "/home ownership"
date: 2011-09-17
forum: General Help
---

### Post by Sidney232 on 2011-09-17
I somehow made all files in my /home/USER owned by root while attempting to copy /home from a previous machine's hdd to my new installation.
How do I change them back to my ownership?
Help!

---

### Post by DukeBoxer on 2011-09-17
sudo chown -R "USER" /home/"USER"

sudo chgrp -R "USER" /home/"USER"

---

### Post by Sidney232 on 2011-09-17
Thanks! That worked a treat - although there was a refusal to change a .gvfs although not sure what that meant.

---

### Post by DukeBoxer on 2011-09-17
not sure about that either....someone else with more experience would know that one

---

### Post by bapoumba on 2011-09-17
It is a mount point for gnome desktop. 
[https://lists.ubuntu.com/archives/edubuntu-devel/2008-August/002627.html](https://lists.ubuntu.com/archives/edubuntu-devel/2008-August/002627.html)

---

### Post by EgoGratis on 2011-09-22
I see. If i make backup of my home folder (/home/"USER")and later restore it on new installation:

Step 1.) 

I have to make new "USER" with the same name as /home/"USER" name was if i don't want to use step 2? Is that correct?


Or i can make user with different name and copy content of backup "USER" folder in this new "USER2" folder and use step 2 to change owner and group?

Step 2.)

sudo chown -R "USER" /home/"USER"

sudo chgrp -R "USER" /home/"USER"     


Is there anything more i should know?


Step 3.)

If i can't change .gvfs permissions then i can unmount it and i can safely delete it?

umount -fl /home/"USER"/.gvfs

What is .gvfs for and can i lose some data if i unmount it and delete it? Will there be new .gvfs on next reboot or how do i make new one?

Thanks.

---

### Post by Lars Noodén on 2011-09-22
You can have /home as a separate partition.  That makes it easy to save when you do a fresh installation or upgrade.

---

### Post by drmrgd on 2011-09-22
When copying, you could also add the '-p' option to the cp command so that it preserves the permissions and ownership of the folders / files you're copying.

---

### Post by EgoGratis on 2011-09-22
Thanks for the answers but they do not answer my questions. But i do have one more question now that you mentioned it:

> You can have /home as a separate partition.  That makes it easy to save when you do a fresh installation or upgrade.

If i do have separate /home and for example 10 users and do fresh installation!

Must i add new users manually after installation or does Ubuntu installation "scan" /home folder and add them automatically?

---

### Post by Lars Noodén on 2011-09-22
Yes, you must add the users manually. You might have to [chown](http://manpages.ubuntu.com/manpages/oneiric/en/man1/chown.1posix.html) the directories and their contents to match the new UIDs.

---

### Post by patryk77 on 2011-09-22
> **Lars Noodén said:**
> Yes, you must add the users manually. You might have to [chown](http://manpages.ubuntu.com/manpages/oneiric/en/man1/chown.1posix.html) the directories and their contents to match the new UIDs.

You could just copy over your /etc/passwd, /etc/group and /etc/shadow files to the new partition.

Then you don't need to worry about UIDs/GIDs, or adding the same users, or changing all their passwords.

---

