---
title: "owners on a single folder?"
date: 2010-11-18
forum: General Help
---

### Post by ghostzen on 2010-11-18
Hi All,
I would like to learn if it's possible to have multiple (specified) owners on a single folder/directory?  For example, I have a folder A, and I would like to have only these specific users- userX, userY, and userZ to be the owners of folder A.  This is something that I have been wondering while I am playing with my new Ubuntu.  Thank you for your time.

---

### Post by krismatth3 on 2010-11-18
No. That's what groups are for. :) Here's a bit more about it: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

To do what you're asking, you should make a group, add the users to that group and then make that group the owner of the directory (e.g. man chgrp)

---

### Post by efflandt on 2010-11-19
If you want files in the directory to automatically use the group of the directory, set the group of the directory (chgrp) to a group only those users are in, and chmod 2775 directory.

That would give files in that directory the group of the directory.  But files would have to have group write permission for others to edit files of other users there.

---

### Post by ghostzen on 2010-11-19
Hi Krismatth3 and efflandt, thanks.  It works :).  Taking a step further, how do I make that directory prompts for username + password when user try to access it?  I had in mind that it would require a script.

---

### Post by uRock on 2010-11-19
Reading this page should be insightful on what you are looking for. [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

