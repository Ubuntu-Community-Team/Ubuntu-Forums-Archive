---
title: "Permissions problem"
date: 2010-03-07
forum: General Help
---

### Post by dulac on 2010-03-07
Hey guys,

i have a weird problem. I have 4 users on my server. To be precise, i am admin user and there are 3 other users.

In my home directory, i have 5 folders. One is mine, 3 for the other users and a fifth named 'admin' which i created for a place to store system things. Typically i run my scripts from there.
In this admin folder there is a folder named 'msgs'. As guessed, it means messages. I use it to allow my users to leave a message for me or others for whatever reason. They each have a symlink to their respective home directories to get to this folder.

I would like to make the folder rw for all users on the server. I was told to create the folder and a group, add users to the group, chgrp of the folder and the everything would be ok.

This is problematic since it did not work properly(users still seem to have to sudo -not permitted- to write to the folder) and the default write is still rw-r----- which i need it to be write by all users.

Any clarifications let me know,

Thanks.

---

### Post by asmoore82 on 2010-03-07
it sounds like you've got the ownership right with `chgrp`
now you need to `chmod` the actual permissions:
```
chmod 1770 msgs/
```
^this sets read/write for owner and group and the "sticky" bit,
so that users can't delete each other's messages.

---

### Post by dulac on 2010-03-07
Thanks. But it is a message folder for all users so they should be able to edit each other's messages including deletion. Is this still the same?

---

### Post by cjhabs on 2010-03-07
> **dulac said:**
> Thanks. But it is a message folder for all users so they should be able to edit each other's messages including deletion. Is this still the same?

In that case just drop the sticky bit, so the perms will be 770.

---

### Post by dulac on 2010-03-07
Thanks for the great help.

as a recap i should:

create a folder, call it msgs

chgrp {group name} msgs

ensure all users i want are in {group name}

chmod 770 msgs


All of this should ensure what i want to do?

I'll get back here if something goes wrong.

---

