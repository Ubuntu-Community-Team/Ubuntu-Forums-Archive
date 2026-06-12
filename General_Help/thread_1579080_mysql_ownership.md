---
title: "mysql ownership?"
date: 2010-09-21
forum: General Help
---

### Post by garyed on 2010-09-21
I transfered some mysql databases from an 8.04 partition to a 10.04 partition. They wouldn't open because the ownership & group was root:root since I transfered them as root. I looked at the original ownership of the files on 8.04 & found they were all "sane:124 ".
I changed everything to mysql:mysql on the 10.04 partition & everything works O.K. now but I have no idea where that owner & group came from. 
Two things I don't understand:
1 -Why I had to change ownership from root:root when I was logged in as    root in mysql & the databases didn't show up?
2 - Where did the original "sane:124" ownership come from?  
Does anyone have a clue?

---

### Post by spjackson on 2010-09-21
1. The mysql server program mysqld runs as user mysql and this user does not have access to files owned by root, even if you log in via a mysql client as root.
2. File ownership and group are numeric ids (stored in the inode). Your 8.04 system and your 10.04 system will probably have different id mappings in /etc/passwd and /etc/group. When running your 8.04 system the files will probably show as mysql:mysql but your 10.04 system is mapping the same numeric owner and group to a different owner name and group name.

---

