---
title: "Give MySQL users limited permissions"
date: 2010-11-08
forum: General Help
---

### Post by Isamtron on 2010-11-08
Hello,

At our company, we give PHP developers Desktop User accounts... so we don't give MySQL root password for them as well. What I want to accomplish is letting the users create, see and control the databases they created only.

I checked this thread but the thing through phpMyAdmin didn't work for me at all:  

[http://ubuntuforums.org/showthread.php?t=323021](http://ubuntuforums.org/showthread.php?t=323021)

Getting 3 problems:

1. The databases created by the users are not automatically prefixed with their username.

2. The user is able to delete other users' databases (I unchecked all admin column permissions.)

3. The users see all the databases where it should be hidden if they don't have their username as prefix.

Please help.

---

