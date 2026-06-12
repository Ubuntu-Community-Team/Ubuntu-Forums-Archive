---
title: "Groups and membership"
date: 2006-01-31
forum: General Help
---

### Post by mbeach on 2006-01-31
Hi, I'm having an issue with something which has humbled me a bit (thought I was doing good)

I have a user, let's call him george.

If I type:
george@ubgx150:~$  groups

I get a list of groups which george belongs to, but it's missing a few.  If I type
george@ubgx150:~$  groups george

I get the full list that I am expecting, however, when user george tries to create file in a folder he doesn't own, but is a member of the group, and the directory has group rwx permissions, he gets a "Permission denied" error.  Also, the /etc/group file lists george as being in the groups.

One of the groups in question is the www-data group created with Apache2.

Any advice appreciated,
mb.

---

### Post by mbeach on 2006-01-31
I have a feeling
~$ newgrp group_name

is a part way solution, but cannot seem to find a good clarification.

---

