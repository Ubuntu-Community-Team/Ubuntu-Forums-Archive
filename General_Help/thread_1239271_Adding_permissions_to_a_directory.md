---
title: "Adding permissions to a directory"
date: 2009-08-13
forum: General Help
---

### Post by DesignerX on 2009-08-13
I have a directory which is owned by root only. I want to add my user to the ownership so I wont need to sudo all the time when accessing it. 

How can I add my self to a directory ownership without removing root as an owner ?

thx.

---

### Post by DaithiF on 2009-08-13
Hi,
first a question -- why do you want to keep root as the owner?  if it is because you want root to still be able to access it then there is no need, root can access everything whether it is the owner or not.  So you could set the owner to yourself and both you and root would have access.

But assuming you have a good reason for root remaining the owner, another way would be to assign group ownership of the directory to a group which you are a member of, either an existing group, or one you create specifically for this purpose.
```
sudo chgrp -R somegroup thedirectory
```

You can then set the permissions on the directory to allow its group owner to read, write, execute, etc.

---

### Post by prem1er on 2009-08-13
Beat me to it..

---

### Post by michy99 on 2009-08-13
If this is a system directory, it is owned by root for a reason. If you go around changes permissions without knowing what you are doing, you can mess up your system.

---

